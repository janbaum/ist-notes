- LAN – Local Area Network 
	- Lokales Netzwerk, in der Verantwortung eines Betreibers (Firma, Privathaushalt,. . . ) 
	- Ausdehnung bis max. wenige Kilometer 
	- häufigste Technologie: Ethernet 
- WAN – Wide Area Network 
	- Netzwerk über größere Strecken 
	- bis hin zum globalen Internet 
- Außerdem viele weitere Klassen (da werden gerne immer mal wieder neue erfunden): 
	- GAN – Global Area Network 
	- MAN – Metropolitan Area Network 
	- FAN – Field Area Network 
	- PAN – Personal Area Network

## Leitungsvermittlung
- Die ursprünglichen Telefonnetze waren sogenannte leitungsvermittelte Netze (engl. circuit switched networks) 
- Beim Verbindungsaufbau („Wählen“) wird ein physikalischer Pfad zwischen Teilnehmern eingerichtet Die Kommunikationspartner (und alle Zwischenstationen im übertragenden Netzwerk) einigen sich also auf die Organisation einer Verbindung 
	- → verbindungsorientiertes Netzwerk 
- Ursprünglich wirkliches „Durchschalten“ von Leitungen 
	- in späteren Systemen abgebildet auf eine Reservierung von Übertragungskapazität entlang der gesamten Übertragungsstrecke
## Paketvermittlung
- n den frühen 1960'er Jahren kamen immer mehr Computer in Gebrauch, die von mehreren Anwendern gleichzeitig genutzt werden sollten 
- Es wurden Fernzugriffsmöglichkeiten auf die (teuren und seltenen) Computer entwickelt, z. B. über Analog-Modems und die bestehenden Telekommunikationsnetze 
- Typisches Nutzungsmuster dabei war: 
	- Absenden eines Kommandos durch den entfernten Nutzer über ein Ein-Ausgabegerät (Terminal) 
	- Verarbeitung des Kommandos durch den Computer und Übertragung des Ergebnisses 
	- Verarbeitung des Ergebnisses und Vorbereitung des nächsten Befehls durch den Nu88tzer
[[01-Einfuehrung.pdf#page=10|Probleme]]:
- Diskontinuierliches Übertragungsmuster: Die Leitung ist oft ungenutzt 
- Dazwischen kurze, intensive Aktivitätsphasen („Bursts“)
- Idee in den 1960ern: Mehrere Benutzer teilen sich eine Übertragungsstrecke entsprechend ihrem kurzfristigen Bedarf und lasten sie damit besser aus

### Pakete und header
- Umgesetzt durch Paketvermittlung: Daten werden in kleine Einheiten – Pakete – zerlegt
- Die Pakete werden mit Steuerinformationen (vor allem: Adressinformationen) versehen
- Diese Steuerinformationen werden in aller Regel vor den eigentlichen Nutzdaten in einem Header übertragen 
- Über eine Leitung können dann abwechselnd Pakete unterschiedlicher Verbindungen und Kommunikationspartner übertragen werden 
- Im einfachsten Fall werden Pakete in der Reihenfolge weitergeleitet, in der sie ankamen 
	- Folge: „*stochastisches Multiplexing*“
### Verbindungsorientierung
- Paketvermittlung kann [[verbindungsorientiert]] oder [[verbindungslos]] umgesetzt werden
- Verbindungsorientierte Paketvermittlung findet man z. B.:
	- in ATM-Netzwerken (Asynchronous Transfer Mode) in den Netzen von Telekommunikationsfirmen
>[!important] Verbindungslose Paketvermittlung ist das Kernkonzept des Internet 
>Idee: Jedes Paket enthält vollständige Adressinformationen 
>- Pakete können **unabhängig voneinander** transportiert werden – ohne, dass jede Zwischenstation über jede existierende Verbindung Bescheid wissen muss (deshalb auch als „zustandslos“ bezeichnet) 
>- der Absender kann **ohne vorherige Ankündigung** Pakete an **beliebige Empfänger** übertragen $\downarrow$
#### Vorteile
- Paketvermittelnde Netzwerke können Übertragungskapazitäten effektiver ausnutzen 
	- kommunizierende Rechner können die Übertragungsstrecke nach ihren Bedürfnissen verwenden, solange andere nicht gestört werden (Fairness)
- Die Vermittlungstechnik („Paket-Switch“, „Intermediate System“, „Router“) vereinfacht sich drastisch, wenn sie zustandslos sein darf 
	- es ist nicht notwendig, in jeder Zwischenstation über jede einzelne aktive Verbindungen Buch zu führen
#### mögliche Nachteile
- Nicht vorhersehbare Übertragungsraten: 
	- nicht genau vorhersehbar, wie viele Daten in einem bestimmten Zeitraum übertragen werden können 
	- Leitungsvermittlung ist hingegen immer deterministisch 
- Nicht vorhersehbare Verzögerungszeiten: 
	- Daten können wegen der gemeinsamen Nutzung der Übertragungsstrecke nicht zu beliebigen Zeitpunkten übertragen werden 
	- Pakete werden in Warteschlangen eingereiht, bis die ausgehende Übertragungsstrecke frei wird 
	- deswegen treten Verzögerungen (Latenzen) auf, die von Paket zu Paket unterschiedlich sein können und nur unter statistischen Annahmen vorhersagbar sind 
	- Es kann zu Überlastsituationen in Routern kommen, wenn bei ihnen mehr Pakete ankommen als sie weiterleiten können

>[!important] Best-Effort-Dienst im internet
>- Im Internet sind alle diese möglichen Nachteile tatsächlich vorhanden
>- Es gibt keinerlei Garantien 
>	- wann und wie schnell ein Paket zugestellt wird 
>	- dass Pakete in derselben Reihenfolge ankommen, in der sie abgeschickt wurden 
>	- ob sie überhaupt zugestellt werden
>- Das Netz „bemüht“ sich nur, die Daten zu ihrem Ziel zu transportieren (und das geht oft schief!)

#### Overprovisioning
- Trotz dieser Nachteile ist das Internet ein extrem erfolgreiches Netz 
- Warum? Weil die Vorteile der Paketvermittlung die Nachteile in aller Regel mehr als aufwiegen 
- Der Hauptgrund: Die Technik ist billiger und flexibler! 
- Mit einem gegebenen finanziellen Aufwand kann im Vergleich zur Leitungsvermittlung ein (zu den meisten Zeitpunkten) leistungsfähigeres paketvermittelndes Netzwerk aufgebaut werden 
- Mit ausreichend Überkapazitäten wirken sich die Nachteile der Paketvermittlung weniger aus 
- Das bewusste Überdimensionieren eines Netzwerks, um z. B. Überlasteffekte zu vermeiden, wird Overprovisioning genannt

## Verschiedene "Bereiche" im Internet
>[!info]- Der Endgerätebereich: Hosts
>![[01-Einfuehrung.pdf#page=25]]

>[!info]- Der Zugangsbereich
>![[01-Einfuehrung.pdf#page=26]]

>[!info]- Der Übertragungsbereich
>![[01-Einfuehrung.pdf#page=27]]

## ISP-Hierarchien
>[!linfo]- Graphik
>![[01-Einfuehrung.pdf#page=29]]

- Eine Gruppe von ca. 10 Internet Service Providern (ISP's) ist global aktiv hat direkte Verbindungen zu jedem anderen, muss keinen anderen ISP dafür bezahlen, dass ihr Datenverkehr weitergeleitet wird (solche Verbindungen nennt man Peering). 
- Beispiele: AT&T, Sprint, NTT, Level 3, Deutsche Telekom 
- Diese werden Tier-1-ISP's genannt (ist kein offizieller Status!) 

- Tier-2-ISP's haben Verbindungen zu einem oder mehreren Tier-1-ISP's nutzen dessen Netz, um Teile des Internet zu erreichen müssen für diesen Transit-Datenverkehr bezahlen, sie sind also Kunden des Tier-1-ISP. Sie sind außerdem mit einigen anderen Tier-2-ISP's direkt verbunden (Peering) 

- Tier-3-ISP's kaufen Transit von Tier-2- und/oder Tier-1-ISP's

## Protokolle
- Ein Protokoll auf einer Schicht $n$ realisiert eine bestimmte Funktionalität (seinen Dienst), die dann von einem anderen Protokoll auf Schicht $n + 1$ benutzt werden kann
- Schicht n kommuniziert mit Schicht n des Kommunikationspartners und „spricht“ dabei ein Schicht-n-Protokoll
- Das Protokoll auf Schicht n nutzt dabei den Dienstes von Schicht $n − 1$ und realisiert auf Schicht n einen anderen, „höherwertigeren“ Dienst
- Diesen Dienst bietet sie wiederum der darüber liegenden Schicht $n + 1$ an

## Überblick
>[!linfo]- Graphic
>![[01-Einfuehrung.pdf#page=51]]
### Sicherungsschicht

### Netzwerkschicht
- Die Netzwerkschicht bietet die Ende-zu-Ende-Übertragung von Paketen durch das Internet
- Was uns die Netzwerkschicht nicht bietet ist 
	- zuverlässige Datenübertragung 
	- Reihenfolgeerhaltung

### Transportschicht
- Die Transportschicht nutzt den Dienst der Netzwerkschicht für den Transport von Daten zwischen den Anwendungsprogrammen
- Deshalb muss sie es ermöglichen, einzelne Anwendungen zu adressieren. Dafür werden sogenannte Portnummern verwendet – jeder Anwendung wird nach Bedarf (mindestens) eine Portnummer zugewiesen
- Deshalb muss sie es ermöglichen, einzelne Anwendungen zu adressieren Dafür werden sogenannte Portnummern verwendet – jeder Anwendung wird nach Bedarf (mindestens) eine Portnummer zugewiesen
- Häufigsten:
	- User Datagram Protocol (UDP)
	- Transmission Control Protocol (TCP)
		- ermöglicht die zuverlässige, reihenfolgeerhaltende Übertragung von Byteströmen von Anwendung zu Anwendung.
		- „Bytestrom“ heißt, die Anwendung muss sich nicht darum kümmern, größere Datenmengen in einzelne Pakete zu zerlegen – das erledigt TCP
- Wichtigste Infos im TCP-Header:
	- Sende- und Empfangs-Portnummer 
	- eine Sequenznummer, die die Reihenfolge des Paketes innerhalb des Bytestroms angibt (für Reihenfolgeerhaltung, Zuverlässigkeit

### Anwendungsschicht
- Anwendungsprogramme nutzen zur Kommunikation – über eine Programmierschnittstelle wie z. B. die Socket-API – direkt die Dienste der Transportschicht
- Beispiele für Anwendungsprotokolle: 
	- das HyperText Transfer Protocol (HTTP) des WWW 
	- das Simple Mail Transfer Protocol (SMTP) zur Übertragung von E-Mails 
	- das BitTorrent-Protokoll für den kooperativen Datei-Download 
	- das Session Initiation Protocol (SIP) für Internet-Telefonie 
	- und viele mehr. . .

>[!info]- Schnelldurchlauf eines Pakets durchs internet
>S. 49-50
>![[01-Einfuehrung.pdf#page=49]]

>[!info]- Enge Taille des Internets
>![[01-Einfuehrung.pdf#page=53]]
##  Ende-zu-Ende-Prinzip
>[!tip] Das bedeutet, dass so viel Funktionalität und Komplexität wie möglich an den Rand des Netzwerks verlagert wird.
>- **Sicherungs**- und **Netzwerkschicht** müssen auf einem **Router** im Inneren des Internet implementiert werden! 
>- **Transport**- und **Anwendungsschichtdaten** weitergeleiteter Pakete sind für den **Router** vollkommen **irrelevant**.

## Referenzmodelle
>[!info]- Vergleich OSI- und TCP/IP-Modell
>Diskussion S. 59
>![[01-Einfuehrung.pdf#page=58]]
## Gremien
- Telekommunikation – ITU 
- allgemeine Standardisierungsgremien – ISO, IEEE, NIST, ETSI 
- Internet-Standards – IETF
