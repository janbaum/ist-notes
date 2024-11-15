Portnummer 25

>[!info] SMTP deckt nur die Zustellung der E-Mail bis zum Mailserver des Empfängers ab! Für die Übertragung zwischen dem Postfach und dem E-Mail-Programm des Empfängers werden andere Protokolle verwendet: 
>- POP3 („Post Office Protocol v.3“, RFC 1939) ist ein einfaches Protokoll, zur Abholung einer E-Mail, wobei sie vom Server gelöscht wird 
>- IMAP („Internet Mail Access Protocol“, RFC 3501) bietet sehr viel mehr Funktionen, kann z.B. die E-Mails auf dem Server belassen und sie so universeller zugreifbar machen

Beispiel: Client (Alice), Server (Bob)
1. Nachdem die TCP-Verbindung aufgebaut wurde, [[02-Anwendung.pdf#page=14|meldet]] sich zunächst der Server und „grüßt“
	- besteht aus:
		- Statuscode (einer dreistelligen Zahl, in diesem Fall 220) 
		- und einer optionalen (!) Fließtext- Übersetzung
2. Danach „grüßt“ der Client mit einer HELO-Nachricht, die mit Statuscode 250 (ungefähr: „alles ok“) bestätigt wird 
	- heute genutzte Erweiterung: EHLO („extended HELO“) statt HELO zur Begrüßung, aktiviert Erweiterungen
3. [[02-Anwendung.pdf#page=16|Envelope]]: Alices Mailserver gibt nun nach einander an, wer der Absender („MAIL FROM“) und wer der Empfänger („RCPT TO“) der E-Mail ist
4. Beides wird von Bobs Server jeweils mit einem Statuscode 250 bestätigt
5. Jetzt folgt die Übertragung der eigentlichen [[02-Anwendung.pdf#page=17|Mail]], eingeleitet mit „DATA“ und abgeschlossen mit einer Zeile, die nur einen Punkt enthält
6. Zum Schluss signalisiert Alices Server, dass die Verbindung geschlossen werden soll 
7. *Alternativ könnte eine weitere Mail übertragen werden*

## SMTP Kommandos und Antwort-codes
>[!info]- Kommandos
>![[02-Anwendung.pdf#page=19]]

>[!info]- Antwort-codes
>S. 20-21
>![[02-Anwendung.pdf#page=20]]

## Mail-Header
Die Kopfzeilen „From:“ und „To:“ sind Pflicht, viele weitere sind optional möglich.
Fast immer werden zumindest „Subject:“ und „Date:“ verwendet Dem Header-Teil folgt eine Leerzeile, danach dann der eigentliche Text.
```smtp
From: Alice <alice@crepes.fr> 
To: bob@hamburger.edu 
Subject: Searching for the meaning of life 


Any ideas?
```

### Received-header
Wenn ein Mailserver eine E-Mail empfängt, fügt er eine `Received:` -Kopfzeile hinzu Mit diesen Kopfzeilen kann der Empfänger den Weg der Nachricht nachvollziehen Eine E-Mail könnte dann beispielsweise so aussehen:
```smtp
Received: from crepes.fr by hamburger.edu; 12 Oct 21 15:27:39 GMT 
From: Alice <alice@crepes.fr> 
To: bob@hamburger.edu 
Subject: Hungry? 

Want to get something to eat?
```

## SMTP Erweiterungen
- Klare Trennung zwischen „Nachrichtenübertragung“ (Envelope) und „Nachrichteninhalt“ (Message) sowie die erweiterbare Header-Struktur haben dabei sehr geholfen
- Unbekannte Headerzeilen werden von (auch älterer) Mail-Software ignoriert, aber weitergeleitet
### Postel’s Law
>[!cite] „Be conservative in what you do, be liberal in what you accept from others“

### MIME (Multipurpose Internet Mail Extensions)
 - nutzt die Erweiterbarkeit durch zusätzliche Header aus; die wichtigsten: 
	 - **Content-Type**: beschreibt die Art der enthaltenen Daten (z. B. image/jpeg) 
	 - **Content-Transfer-Encoding**: gibt an, wie diese dargestellt werden (z. B. base64)
- MIME-E-Mails können aus mehreren Teilen bestehen 
	- Teile können selbst wieder (potentiell weiter verschachtelte) MIME-Nachrichten sein
```smtp
From: Alice <alice@crepes.fr> 
To: bob@hamburger.edu 
Subject: Picture of yummy crepe 
MIME-Version: 1.0 
Content-Transfer-Encoding: base64 
Content-Type: image/jpeg 

base64-codierte Daten............
```
