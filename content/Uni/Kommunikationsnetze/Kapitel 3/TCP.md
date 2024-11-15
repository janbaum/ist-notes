- TCP überträgt in beide Richtungen je einen Bytestrom 
	- kein Problem: die beiden Richtungen sind unabhängig 
>[!summary] Zusammenfassung
>- In diesem Kapitel haben wir die Transportschicht betrachtet 
>- Wir haben uns (kurz) UDP und (lange) TCP angeschaut 
>- Wir haben uns über die unterschiedlichen Dienstmodelle der Protokolle unterhalten 
>- Wir haben gesehen, wie man Zuverlässigkeit über einen unzuverlässigen Übertragungskanal (wie z. B. die Internet-Netzwerkschicht) erreichen kann 
>- Wir haben die TCP-Zuverlässigkeitsmechanismen kennen gelernt 
>- Und wir haben erkannt, dass [[#Flusskontrolle]] und [[#Überlastkontrolle]] notwendig sind und wie sie in TCP umgesetzt werden 
>- Jetzt: Wieder ein Schritt weiter nach unten im Protokollstapel, in die Netzwerkschicht
## Transportschicht-Multiplexing TCP
- TCP darf Segmente, die von unterschiedlichen Quellen stammen **nicht** an denselben Ziel-Socket zustellen
- TCP Empfänger entscheidet, an welchen Socket ein eingehendes Segment gehen soll anhand des 4-Tupels:
	- Quell-IP-Adresse
	- Quell-Portnummer
	- Ziel-IP-Adresse
	- Ziel-Portnummer
- Eine Teilmenge des 4-Tupels ist im Allgemeinen nicht ausreichend – anders als beim verbindungslosen UDP
- Es kann mehrere gleichzeitig aktive TCP-Sockets mit derselben Portnummer geben für die selbe (lokale) IP-Adresse geben
>[!example]- Beispiel HTTP-Verbindung
>![[03-Transportprotokolle.pdf#page=23]]

## Sequenznummern
- Sequenznummern sind endliche Zahlen – bei langen Verbindungen werden sie sich irgendwann wiederholen 
	- es muss jederzeit sichergestellt sein, dass kein anderes Paket mit derselben Sequenznummer beim Empfänger ankommt 
- Die Zeit bis zu einer Wiederholung muss länger sein, als ein Paket im Netz maximal „überlebt“ haben kann 
- Gar nicht so einfach abzuschätzen (vor allem für zukünftige Netze, über die das Protokoll einmal verwendet werden könnte!) 
	- hängt auch von der Rate ab, mit der Sequenznummern „abgearbeitet“ werden 
	- also von der Übertragungsgeschwindigkeit im Netz
- Darf nicht vorhersehbar sein
- TCP nutzt 32-Bit-Sequenznummern
>[!info] Heute oft praktiziert 
>- Startsequenznummer zufällig wählen 
>- ausreichend großen Sequenznummernbereich verwenden ^sequenznummern
>- das Beste hoffen

## Stop-and-wait
>[!info]- 
>![[03-Transportprotokolle.pdf#page=38]] 

## Go-Back-n
>[!info]- 
>![[03-Transportprotokolle.pdf#page=42]]
- Sender: 
	- ACK für Paket x bedeutet, dass auch alle vorangegangenen Pakete erfolgreich angekommen sind (kumulatives ACK) 
	- Fehler werden durch einen Timeout erkannt 
	- überträgt bei einem erkannten Fehler für Paket x alle Pakete ab x erneut 
- Empfänger: 
	- quittiert bei jedem Empfang das letzte in der richtigen Reihenfolge empfangene Paket (ggf. also viele ACKs mit derselben Sequenznummer) 
	- verwirft alle Pakete, die nicht in der richtigen Reihenfolge ankommen 
		- Variante/Erweiterung: Puffern von Paketen „außer der Reihe“ kann ggf. die Effizienz steigern
## Selective repeat
>[!info]- 
>![[03-Transportprotokolle.pdf#page=44]]
- Sender: 
	- erkennt Fehler an Lücken in Quittierung 
	- wiederholt nur Übertragung nicht quittierter Pakete 
	- Erkennung fehlender ACKs durch Sende-Timeouts 
- Empfänger: 
	- speichert alle empfangenen Pakete 
	- quittiert jedes Paket 
	- 
-> Aufwändiger als Go-back-n – aber (je nach Umgebung, Einsatzzweck) evtl. auch effizienter
## ACKs in TCP
- Jedes TCP-Segment in eine Richtung kann gleichzeitig ein ACK in die andere Richtung sein (piggybacked ACKs) 
- Wenn in die Gegenrichtung gerade keine Daten zu verschicken sind, dann ist ein ACK ein leeres TCP-Segment (Nutzdatenlänge 0) mit gesetztem ACK-Feld 
- ACKs in TCP sind **kumulativ**
### kumulative ACKs
- Da ein (kumulatives!) ACK immer auch alle früheren Segmente bestätigt, können Segmente hinter einer „Lücke“ oder in falscher Reihenfolge eintreffende Segmente nicht bestätigt werden 
- TCP wiederholt dann – genau wie klassisches [[#Go-Back-n]] – jeweils einmal das vorherige ACK 
- Die TCP-Spezifikation schreibt nicht vor, ob außer der Reihe eintreffende Segmente vom Empfänger zwischengespeichert werden 
	- sie dürfen auch verworfen werden – wegen Neuübertragungen werden sie noch einmal ankommen 
	- heutige TCP-Implementationen puffern solche Daten aber praktisch immer zwischen
## Bytesequenznummern
- TCP nummeriert nicht Segmente, sondern alle Bytes im übertragenen Bytestrom durch 
- Zahl im Sequenznummern-Feld = Sequenznummer des ersten im Segment enthaltenen Bytes 
	- hat ein Segment die Sequenznummer 3217 und enthält 500 Bytes Daten, dann hat das nächste Segment die Sequenznummer 3717 
- Zahl im ACK-Feld = Sequenznummer des ersten Bytes an, das dem Sender des ACK im Bytestrom noch fehlt 
- also **nicht (!!!)** die höchste bereits empfangene Sequenznummer
>[!example]- Beispiel
>![[03-Transportprotokolle.pdf#page=49]]

## Retransmission timeout
- Timeout darf nicht zu früh stattfinden
- grobe Orientierung an RTT, früher nahm man doppelte RTT für Time-Out
	- Problem: Unterschiedliche [[03-Transportprotokolle.pdf#page=53|Warscheinlichkeiten]]
- Also: Standardabweichung (und damit „Breite“ der Verteilung) sollte mit einfließen 
- TCP misst deshalb außerdem, wie weit die RTT's typischerweise vom Mittelwert abweichen (erneut gleitender Mittelwert) 
- Der Timeout wird in TCP dann wie folgt gewählt: $RTT + 4 * Standardabweichung$
### Exponentielle Timeouts
- Wenn nach einer Übertragungswiederholung noch immer kein ACK eintrifft, wird die Wartezeit bis zum nächsten Übertragungsversuch verdoppelt
- Die Zeit zwischen aufeinanderfolgenden Übertragungsversuchen wächst also exponentiell (bis zu einer oberen Grenze, oft 60 s)
## Verzögerte ACKs (Delayed ACKs)
- Heutige TCP-Implementationen verringern die Zahl generierter ACK-Nachrichten durch einen Mechanismus namens **Delayed ACKs** (DACK); wenn ein TCP-Empfänger:
	- ein Segment in richtiger Reihenfolge mit der erwarteten Sequenznummer erhält und alle vorangegangenen Daten schon bestätigt wurden 
		- -> das ACK wird verzögert und auf das nächste Segment gewartet; erst wenn nach (max.) 500 ms immer noch kein weiteres Segment ankommt, wird das ACK verschickt 
	- ein Segment in richtiger Reihenfolge mit der erwarteten Sequenznummer ankommt und ein vorangegangenes ACK verzögert wurde 
		- -> sofort ein gemeinsames (kumulatives!) ACK für beide Segmente verschicken
	- ein Segment mit einer höheren Sequenznummer als erwartet empfängt 
		- -> eine Lücke! 
		- -> sofort das vorangegangene ACK wiederholen (mit der – noch immer – erwarteten nächsten Sequenznummer = Anfang der Lücke)
	- ein Segment erhält, das eine vorhandene Lücke (teilweise) schließt 
		- -> sofort ein ACK mit dem nächsten noch fehlenden Byte verschicken
>[!example]- Beispiel
>![[03-Transportprotokolle.pdf#page=58]]

## Fast Retransmit
- Der TCP Retransmission Timeout ist oft relativ lang
- Das bedeutet lange Verzögerungen vor einer Übertragungswiederholung
>[!caution] Was passiert, wenn ein einzelnes Segment verloren geht, nachfolgende aber ankommen? 
>- Der Sender wird mehrere ACKs mit derselben Sequenznummer bekommen 
>- Das lässt sich ausnutzen: wenn ein Sender drei Duplikate eines ACKs erhalten hat (Triple Duplicate ACK, TDACK), nimmt er an, dass das Segment verloren gegangen ist 
>- -> dann wird ein Fast Retransmit durchgeführt: das Segment wird schon vor dem Timeout wiederholt 
>- -> Neu übertragen wird nur das eine Segment

>[!example]- Beispiel
>![[03-Transportprotokolle.pdf#page=60]]

## TCP-Header, -Flags, -Options
S. 61-65 (inkl. Timestamp-Options)
![[03-Transportprotokolle.pdf#page=61]]

## TCP-Verbindungen
>[!info]- Komplette TCP-Sitzung
>![[03-Transportprotokolle.pdf#page=79]] 
### Verbindungsaufbau
Zum Aufbauen einer Verbindung verwendet TCP einen sogenannten Drei-Wege-Handshake:
1. Client schickt `SYN`-Flag
2. Der Server: 
	1. antwortet mit einem `SYN-ACK`-Segment
	2. bestätigt im ACK-Nummern-Feld die initiale Sequenznummer des Clients +1 (!) 
	3. und gibt im Sequenznummernfeld seine eigene Startsequenznummer an
3. Schließlich bestätigt der Client das SYN-ACK mit einem ACK, in dem er die initiale Sequenznummer des Servers, wieder +1,bestätigt
>[!info]- Graphic
>![[03-Transportprotokolle.pdf#page=73]]

>[!warning] Wieso ist ein Drei-Wege-Handshake notwendig? Warum genügt nicht auch ein SYN/SYNACK-Handshake?
- Es geht wiederum um „alte“ Segmente, die das Netz eventuell noch verlassen könnten 
- Angenommen, ein Zwei-Wege-Handshake würde verwendet und die paar ersten Segmente einer alten Verbindung würden (evtl. ein zweites Mal) bei einem TCP-Server ankommen
- Wenn nur ein Zwei-Wege-Handshake erfolgen müsste, dann müsste der Server die eingehenden Daten akzeptieren und an die Anwendung weitergeben 
- Das dritte Handshake-Paket (genauer: die korrekt wiedergegebene Startsequenznummer des Servers) bestätigt dem Server also, dass der Client „lebt“ und jetzt die Verbindung aufbauen möchte 
- Außerdem bietet es zusätzlichen Schutz vor einem Angreifer, der auf diese Weise keine TCP-Verbindung mit gefälschter Quelladresse vortäuschen kann, ohne die Antworten zu hören
### Verbindungsabbau
- Für den Verbindungsabbau verwendet TCP einen Vier-Wege-Handshake
- Jede Richtung der Verbindung kann mit einem gesetzten FIN-Flag signalisieren, dass sie keine weiteren Daten senden wird
- Ein FIN der Gegenseite wird mit einem ACK bestätigt 
	- **<font color="#ff0000">wie beim SYN wird die ACK-Nummer um 1 erhöht</font>**
	- dieses ACK bestätigt also, dass alle Daten dieser Richtung korrekt empfangen wurden; es werden also keine weiteren Übertragungswiederholungen notwendig
>[!example]- Graphik
>![[03-Transportprotokolle.pdf#page=76]]
- Auch nachdem die Richtung A → B geschlossen wurde, können noch Daten von B zu A fließen 
	- das nennt man „halb geschlossene Verbindung“ (nicht verwechseln mit einer „halboffenen Verbindung“ vor Abschluss des 3-Wege-Handshakes!)
>[!warning]- Problem: Wann kann ein Host die Informationen zu einer geschlossenen TCP-Verbindung „vergessen“?
>S.78-79
>![[03-Transportprotokolle.pdf#page=78]]

#### Reset (RST)
- Neben dem „geordneten“ Schließen mit FIN-Segmenten kann eine TCP-Verbindung auch abgebrochen werden 
- Der Empfang eines Segmentes mit gesetztem RST-Flag (Reset) bedeutet, dass ab sofort 
	- keine weiteren Segmente gesendet werden dürfen 
	- und alle zukünftig eintreffenden Segmente verworfen werden sollen 
- Zweck: Fehlerbehandlung, zum Beispiel nach dem Absturz von einem der Kommunikationspartner 
	- RST wird deshalb vor allem dann gesendet, wenn ein Segment für eine unbekannte TCP-Verbindung eintrifft 
- Nach einem Reset gibt es keine Garantien, ob gesendete Daten zugestellt wurden oder nicht! 
- Ein RST darf niemals als Antwort auf ein eingehendes RST gesendet werden (um sog. „Reset Wars“ zu vermeiden)
>[!example]- Zustände einer TCP-Verbindung (vereinfacht)
>![[03-Transportprotokolle.pdf#page=81]]

## Bytestrom-Segmentierung
TCP unterteilt den verschickten Bytestrom selbständig in Segmente
- Wie viele Daten sollten wir in ein Segment packen?
### Nicht volle Segmente
- Wir bekommen von der Anwendung jetzt x Byte Daten, wobei x < MSS ( Maximum Segment Size)
-> Paket "halb leer", trotzdem verschicken
- Was wenn die Anwendung danach wieder ein paar wenige (zu wenige für ein ganzes Paket) Daten in den Sendepuffer schreibt?  (Tinygram-Problem)
#### Nagle-Algorithmus (Nagle’s Algorithm)
Grundidee: 
- solange ein unbestätigtes Segment unterwegs ist 
- und noch nicht genug Daten für ein volles Segment (also weniger als eine MSS) zum Senden vorliegen
- dann verzögere das Absenden des nächsten Segments


## Flusskontrolle
Einfachste Methode bei drohendem Empfänger-Überlauf: 
- Absenden einer „Halt“-Meldung 
Bei wieder möglichem Empfang: 
- Absenden einer „Weiter“-Meldung 
>[!example]- Examples & Graphic
>![[03-Transportprotokolle.pdf#page=page=88]]

>[!warning] Problem: In Netzen wie dem Internet gibt es keine Garantie, dass/wann die „Halt“-Nachricht eintrifft

Um zu verstehen, was genau der Empfänger dem Sender mitteilen muss, schauen wir uns den Sequenznummernbereich aus Sicht beider Endpunkte genauer an: 
Ab hier, macht es Sinn sich die Slides anzuschauen, wie sich das Fenster immer eiter verschiebt. *Dann müssen wir die Graphiken nicht alle hier rein pasten*
### Sequenznummernraum bei Sender und Empfänger
S.90 - 95
![[03-Transportprotokolle.pdf#page=90]]

- Beispiel: Wenn Empfangspuffer voll läuft, in ACKs `rwin`-Flag auf Null setzen
- der Empfänger darf (muss nicht!) auch von sich aus erneut ein Fenster-Update (= wiederholtes ACK mit höherer Fenstergröße) schicken, sobald wieder Platz ist
>[!example]- Beispiel mit volllaufendem Puffer
>![[03-Transportprotokolle.pdf#page=102]]

>[!warning]- Problem: Silly Windows
>![[03-Transportprotokolle.pdf#page=103]]

Lösung: 
- Empfänger wartet, bis sinnvoll viel Puffer (z. B. halbe Puffergröße oder eine MSS) verfügbar ist 
- Erst dann wird der Sender über das wieder geöffnete Fenster informiert 
- Auch der Nagle-Algorithmus auf der anderen Seite der Verbindung, falls aktiviert, kann das Problem lösen
### Maximale Fenstergröße
- Das Fenster darf maximal den halben [[#^sequenznummern|Sequenznummernbereich]] überdecken 
- Wenn es dann um eine volle Fenstergröße verschoben wird, werden dennoch alle vorher gültigen Sequenznummern [[03-Transportprotokolle.pdf#page=108|ungültig]]
- Die Fenstergröße in TCP ist ein 16-Bit-Feld im TCP-Header 
	- Der maximale Wert ist also (ganz unabhängig vom Sequenznummernfeld) $2^{16} − 1 = 65535$
- -> Es können niemals mehr als 64 KB Daten gleichzeitig unterwegs sein
#### BDP und Fenstergrößen
- Allgemeiner können wir festhalten, dass die RTT und die erlaubte Fenstergröße W die erreichbare Datenrate R einschränken: $$R=\frac{W}{RTT}$$
- Umgekehrt ergibt sich die notwendige Fenstergröße direkt aus dem Produkt von Datenrate und RTT der Netzwerkstrecke – das Bandwidth-Delay Product (BDP): $$W = R · RTT = BDP$$
#### Window Scaling
>[!note]- Skript
>S.112-113
>[[03-Transportprotokolle.pdf#page=112]]

## Überlastkontrolle
Disclaimer: Dieser Teil ist sehr unsauber Dokumentiert
>[!important] Unterschied zwischen Fluss- und Überlastkontrolle
>- Flusskontrolle = Regulieren der Senderate zum Vermeiden von Überlastung des **Empfängers** 
>- Überlastkontrolle = Regulieren der Senderate zur Vermeidung von Überlast im **Netzwerk**

### Congestion Collapse
- Eine Situation, in der ein Netz aufgrund von Überlasteffekten praktisch vollständig zusammenbricht und kaum mehr sinnvoll Daten zustellt, nennt man Congestion Collapse 
- Im Internet trat dies Mitte der 1980'er Jahre massiv auf – zum Teil brach die erreichbare Datenrate um den Faktor 1000 ein! 
- Deshalb ist Überlastkontrolle für ein Netzwerk quasi „lebensnotwendig“

### Lösungsansätze
Es gibt zwei prinzipielle Möglichkeiten, in einem Netzwerk Überlastkontrolle zu implementieren:
1. mit Unterstützung durch das Netzwerkinnere 
	- die weiterleitenden Netzwerkknoten signalisieren auftretende Überlast 
	- dies kann in sehr unterschiedlicher Weise geschehen: von einem einzelnen durch den Router gesetzten Bit im Paket als Überlasthinweis, bis hin zur expliziten Vergabe von Senderaten 
2. Ende-zu-Ende 
	- Überlast im Netz muss von den Endsystemen durch Beobachtung des Netzwerkverhaltens erkannt werden 
	- **TCP verfolgt diesen Ansatz**
#### TCP-Überlastkontrolle
- Eigentlich ist es ein wenig seltsam, das Problem an dieser Stelle zu lösen: 
	- Überlast ist ein Problem im Inneren des Netzwerkes 
	- die Transportschicht arbeitet im Internet nur auf Endsystemen! 
- Die Systeme im Netzwerkinneren kennen jedoch keine Verbindungen
- Außerdem entspricht es dem Ende-zu-Ende-Prinzip, komplexe Funktionalität (Überlastkontrolle ist sehr komplex!) möglichst in den Endsystemen zu implementieren 
- Deshalb hat man im Internet entschieden, die Überlastkontrolle in TCP zu implementieren

- TCP erkennt Überlast anhand von Segmentverlusten 
- Annahme: Segmentverlust = Überlast 
- Deshalb: Bei Segmentverlusten wird die Rate verringert, mit der TCP Daten absendet

Wir hatten im Zusammenhang mit der [[#BDP und Fenstergrößen|Flusskontrolle]] schon gesehen, dass die Größe des eines vom Sender beachteten Schiebefenster implizit die Datenrate begrenzt: $$Datenrate = \frac{Fenstergröße}{RTT}$$
>[!info] TCP-Überlastkontrolle
>- Idee deshalb: ein zweites, unabhängiges Fenster zur Ratenbegrenzung 
>- Dieses Überlastfenster (**congestion window, congwin bzw. cwin**) wird zusätzlich zum Flusskontrollfenster beachtet 
>	- gesendet werden darf nur das, was in beide Fenster passt (also eine Datenmenge entsprechend dem Fenster, das gerade kleiner ist) 
>	- **Vorsicht: Das erhöht die Gefahr, dass Sie Flusskontrolle und Überlastkontrolle verwechseln, noch mehr!** 
>- `congwin` bestimmt deshalb die maximal mögliche Datenmenge pro RTT – und damit die Datenrate! 
>- Die Größe des Überlastfensters wird kontinuierlich angepasst, je nach wahrgenommener Überlastsituation

##### Additive Increase, Multiplicative Decrease (AIMD)
- Bis zum Auftreten eines Verlustes wächst congwin mit einer festen Rate (Additive Increase) 
- Konkret: in jeder RTT wird die erlaubte Datenmenge um so viel erhöht, wie in ein volles Segment passt (eine Maximum Segment Size, MSS)
##### Slow Start
- Zu Beginn erhöht TCP deshalb die Datenrate exponentiell 
	- meist bis zum ersten Verlustereignis 
	- oder bis zum Erreichen einer Schwelle (je nach Implementation, s. u.)
- TCP passt congwin immer beim Eintreffen eines ACK an 
- Während der Slow-Start-Phase möchte TCP die Senderate in jeder RTT [[03-Transportprotokolle.pdf#page=138|verdoppeln]]
##### Verhalten bei Verlusten
- Bei beobachteten Paketverlusten wird die Fenstergröße verkleinert 
- Das Verhalten von TCP unterscheidet sich, je nachdem, wie der Segmentverlust erkannt wurde: 
	- <font color="#ff0000">a)</font> Ein <font color="#ff0000">Triple Duplicate ACK</font> (TDACK) bedeutet, dass das Netz noch in der Lage ist, zumindest einen Teil der Segmente zuzustellen (siehe [[#Fast Retransmit]]!) 
		- TCP nimmt deshalb in diesem Fall moderate Überlast an: 
			- <font color="#ff0000">congwin wird halbiert</font> (Multiplicative Decrease) 
			- <font color="#ff0000">danach wächst es wieder linear an</font> (diese Betriebsart von TCP nennt man Congestion Avoidance)
	- <font color="#ff0000">b)</font> Ein <font color="#ff0000">Timeout</font> deutet hingegen auf schwere Überlast hin, entsprechend reagiert TCP stärker 
		- `congwin` wird deshalb in diesem Fall auf <font color="#ff0000">1 oder 2 MSS gesetzt</font>, danach erfolgt ein <font color="#ff0000">neuer Slow Start</font> 
		- Er wird bei Erreichen von <font color="#ff0000">50% der vorherigen Fenstergröße beendet</font> 
			- diese Schwelle nennt man Slow Start Threshold (<font color="#ff0000">ssthresh</font>) 
			- ssthresh wird in einer Variablen gespeichert 
			- sie wird immer beim <font color="#ff0000">Eintreten eines Verlustereignisses</font> <font color="#ff0000">auf die Hälfte der vorher erreichten Fenstergröße</font> gesetzt 
			- *manche Implementationen von TCP geben zu Beginn einer Verbindung einen ssthresh vor, sodass der erste Slow Start immer an einem bestimmten Punkt abbricht; bei anderen (z. B. Linux) endet der erste Slow Start stets mit dem ersten Verlustereignis* 
			- <font color="#ff0000">Nach Überschreiten</font> des ssthresh wächst `congwin` <font color="#ff0000">linear weiter</font> (= Übergang zu Congestion Avoidance)
>[!example]- Beispiel Graphic
>![[03-Transportprotokolle.pdf#page=142]]

### Self Clocking
- TCP benötigt für das Anpassen der Überlastfenstergröße keine Timer 
- Die RTT im Netzwerk gibt den „Takt“ vor, nach dem das Fenster zu höheren Sequenznummern hin verschoben (und gleichzeitig vergrößert) wird
	- und damit auch den Takt, in dem neue Segmente den Sender verlassen dürfen 
- Self Clocking hilft bei der Implementierung: **TCP-Sender brauchen trotz der komplexen Protokollregeln wenige Ressourcen**
### Fairness
- Das Gesamtsystem konvergiert gegen eine gleichmäßige Aufteilung der Datenrate 
- Erklärungsansatz: Die momentan schnelleren Verbindungen werden häufiger und stärker „gebremst“ 
- Warum? 
	- Verlustwahrscheinlichkeit ist für alle Pakete gleich Verbindungen mit momentan höherer Datenrate haben mehr Pakete unterwegs, sehen deshalb mit höherer Frequenz Verluste 
	- wegen des Multiplicative Decrease wird außerdem von der schnelleren Verbindung bei einem Verlust mehr „abgezogen“
>[!example]- Beispiel
>![[03-Transportprotokolle.pdf#page=151]]

## TCP-Varianten-Zoo 
- Es gibt (sehr!) viele Varianten der TCP-Überlastkontrolle (hunderte, vielleicht tausende) 
- Unterscheiden sich darin, wie Überlast erkannt und behandelt wird 
- Die „klassische“ Variante, die wir hier (mit Vereinfachungen. . . ) besprochen haben, heißt TCP Reno 
- Ziel ist immer: kompatibel sein mit anderen TCP-Varianten (jeder soll mit jedem reden können) 
- möglichst fair sein zu anderen TCP-Varianten (beim gemeinsamen Durchqueren eines Engpasses)
Wichtige und bekannte TCP-Spielarten sind z. B.: 
- TCP Tahoe: Der „Urahn“ und Vorläufer von TCP Reno; keine Sonderbehandlung von TDACKs, nach jedem Verlust ein Slow Start 
- TCP NewReno: veränderte Regeln, wie/wann/welche Segmente nach TDACKs übertragen werden 
- TCP Vegas: beobachtet zum Zweck der Überlastkontrolle Veränderungen der RTT; kann auf diese Weise wachsende Warteschlangen früh erkennen dadurch schon vor dem Entstehen von Verlusten auf bevorstehende Überlast reagieren 
- CUBIC (derzeit in Linux) und Compound TCP (zeitweise in Windows): Anpassungen für Long Fat Pipes 
- BBR („Bottleneck Bandwidth and Round-trip propagation time“): kombiniert Ideen von TCP Vegas (Beobachtung der RTT) mit „Probing“ um die Bottleneck-Rate zu ermitteln
## Grundidee hinter CUBIC 
- Standard-Variante von TCP im Linux-Kernel seit Version 2.6.19
- mit einem völlig anderen Verfahren zum Bestimmen des Congestion Window: 
	- keine Unterscheidung Slow Start / Congestion Avoidance 
	- nicht mehr self-clocking, Fensterwachstum unabhängig vom Eintreffen von ACKs (stattdessen zeitabhängig) 
- Die Größe des Fensters über die Zeit wird von einer kubischen Funktion beschrieben 
- Bei einem Verlustereignis wird die Fenstergröße reduziert 
- Wächst dann wieder entsprechend einer kubischen Funktion 
- Die Parameter der kubischen Funktion für die neue „Runde“ werden abhängig von der bis zum Verlust erreichten Fenstergröße neu bestimmt

- Die [[03-Transportprotokolle.pdf#page=163|kubische Funktion]] führt erst zu einem schnellen Wachsen des Fensters: 
	- zügiges Wiederherstellen der Höhe vor dem Verlust 
	- dann zu einem „Plateau“, während dem das Fenster weitgehend unverändert bleibt: Parameter werden so justiert, dass die Höhe dem letzten funktionierenden Fenster vor dem Verlust entspricht (in der Abbildung Wmax) 
	- und dann wieder zu einem schnellen Anstieg: Austesten, ob noch mehr geht
- Vermeidet Unfairness zwischen Verbindungen mit unterschiedlichen RTTs, da das Fensterwachstum von der RTT unabhängig ist 
- Kann Long Fat Pipes besser ausnutzen, da das Wachstum sich immer schnell dem vorherigen Fenster annähert 
- Parameter sind so justiert, dass das Teilen eines Engpasses mit „klassischen“ TCP-Varianten ebenfalls (einigermaßen) fair geschieht