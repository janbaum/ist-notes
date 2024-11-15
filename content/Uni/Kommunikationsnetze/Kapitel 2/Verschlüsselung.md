## Symmetrische Verschlüsselung
- Bei symmetrischen Kryptoverfahren <font color="#00b050">kennen Sender und Empfänger beide denselben Schlüssel.</font>
- Der Schlüssel ist eine **Bitfolge fester Länge** (z. B. 128 Bit) 
- Nachrichten, die <font color="#00b050">mit Schlüssel K verschlüsselt</font> wurden, können <font color="#00b050">nur mithilfe von K wieder entschlüsselt</font> werden
>[!example] Beispiele für symmetrische Verschlüsselungsalgorithmen: 
>AES, Blowfish, Serpent, Twofish; historisch: DES, RC4

## Asymmetrische Verschlüsselung
- Separate Schlüssel für alle Paare von Teilnehmern sind oft nicht möglich 
- Dann helfen asymmetrische („<font color="#00b050">Public Key</font>“) Verfahren 
	- z. B. RSA, ElGamal, verschiedene EC-Algorithmen,...
- Jeder Benutzer hat einen privaten und einen öffentlichen Schlüssel (hier mit $K^−$ und $K^+$ bezeichnet) 
- Was mit dem <font color="#00b050">öffentlichen Schlüssel verschlüsselt</font> wurde, kann <font color="#00b050">nur mit dem privaten wieder entschlüsselt</font> werden
## Digitale Unterschriften
- Public-Key-Kryptographie lässt sich „umgekehrt“ anwenden: 
	- Was mit dem privaten Schlüssel „verschlüsselt“ wurde, kann nur mit dem passenden öffentlichen Schlüssel „entschlüsselt“ werden 
- Das ermöglicht Absenderauthentifizierung und digitale Signaturen: 
	- Die Nachricht kann nur vom Besitzer des privaten Schlüssels „unterschrieben“ worden sein
## Kryptographische Hashfunktionen
- Public-Key-Kryptographie ist rechenaufwändig und deshalb langsam 
- Techniken für digitale Unterschriften werden daher oft mit kryptographischen Hashfunktionen kombiniert 
- Eine Hashfunktion ist eine Funktion, die eine Eingabe auf einen <font color="#00b050">Hashwert fester Länge</font> abbildet 
- Bei einer kryptographischen Hashfunktion ist es nicht möglich, zu einem gegebenen Hashwert $y$ eine Nachricht $x$ zu finden, für die $H(x) = y$ *(eine Kollision)* 
- Aktuelle Beispiele: SHA-3, SHA-2, Skein, Whirlpool 
- Historisch (Komplexität der besten Kollisionsattacke): SHA-1 (261,2), MD5 (221), MD4 (2)
>[!example]- Graphic
>![[02-Anwendung.pdf#page=78]]

## Schlüsselaustauschprotokolle
- Mit Schlüsselaustauschprotokollen können sich zwei Kommunikationspartnern über eine nicht abhörsichere Leitung auf einen gemeinsamen Schlüssel einigen 
- Bekanntestes Beispiel: Diffie-Hellman-Schlüsselaustausch
>[!example]- Graphic
>![[02-Anwendung.pdf#page=79]]
- Um sog. Man-in-the-Middle-Angriffe zu verhindern, wird das üblicherweise mit Public-Key-Kryptographie kombiniert
## Zertifikate und Identitäten
>[!attention] Wie findet man bei asymmetrischer Krytographie den öffentlichen Schlüssel seines Kommunikationspartners? 
- Verschlüsseln bringt nichts, wenn man nicht sicher sein kann, den richtigen Schlüssel zu benutzen! 
- Zentrales Problem daher: 
	- Vertrauenswürdige Abbildung einer Identität auf den dazugehörigen öffentlichen Schlüssel 
- Lösungsansatz: 
	- Zertifikate – vertrauenswürdige Dritte unterschreiben (digital), dass ein bestimmter öffentlicher Schlüssel zu einer bestimmten Person(/Organisation/...) gehört
>[!note]- Weitere Probleme mit der Vertrauenswürdigkeit der Zertifikate
>![[02-Anwendung.pdf#page=page=82]]

### Public Key Infrastructure (PKI)
- Die Regeln, nach denen Zertifikate ausgestellt werden, und die dafür notwendige Infrastruktur nennt man Public Key Infrastructure (PKI):
	- Häufig, unter anderem im WWW: oligopolistisch und hierarchisch (X.509/PKIX) 
	- Alternative: anarchisch (Web of Trust) 
- Zentrale Frage: Wem vertraue ich?
#### Hierarchisches Vorgehensweise
- Es gibt einige Anbieter, die sogenannte Root-Zertifikate besitzen: 
	- mit einem Root-Zertifikat zertifiziert man sich selbst („ich bestätige hiermit, dass ich ich bin“) 
	- Root-Zertifikate schaffen kein neues Vertrauen 
	- Root-Zertifikaten könnte man z. B. vertrauen, weil sie als Bestandteile von Programmen oder Betriebssystemen ausgeliefert werden 
- Jemand, der von einem solchen Anbieter ein Zertifikat erhalten hat, kann dann wieder Zertifikate für andere ausstellen

- Einem Zertifikat A in einer hierarchischen PKI kann man nur dann vertrauen, wenn: 
	- es eine Kette von Zertifikaten gibt, die von einem Root-Zertifikat zu A führt bei dieser Kette jeder Nachfolger vom Vorgänger zertifiziert wird man jedem einzelnen Element dieser Kette vertraut 
- Fazit: Je länger die Kette ist, desto schwerer fällt das Vertrauen 
- Konsequenz: Meist möchte man sein Zertifikat direkt von einem vertrauenswürdigen Inhaber eines Root-Zertifikats erhalten

- Im Internet kommen häufig PKI-Systeme zum Einsatz, die auf X.509/PKIX basieren 
- Das ist auch das Standardvorgehen im www
>[!linfo]- Details
>- X.509 ist ein allgemeiner Standard zur Darstellung von Zertifikaten 
>- PKIX ist eine IETF-Arbeitsgruppe, die X.509 auf die Bedürfnisse des Internet anpasst 
>- Zentrales Dokument: RFC 5280: Internet X.509 Public Key Infrastructure Certificate and Certificate Revocation List (CRL) Profile 
- Sehr trocken! Im Folgenden schauen wir uns einfach einmal ein Zertifikat für das Homebanking der Deutschen Bank an:
>[!example]- Beispiel Deutsche Bank
>S. 87-89
>![[02-Anwendung.pdf#page=87]]

## SSL/TLS
- SSL bzw. TLS sind (teilweise unnötig) komplexe Protokolle Prinzip: 
	- zusätzliche Protokollschicht zwischen Transport- und Anwendungsprotokoll 
	- sieht nach „oben“ aus wie TCP, nach „unten“ wie ein TCP-basiertes Anwendungsprotokoll 
	- nutzt eine darunterliegende TCP-Verbindung 
	- verlässt sich insbes. auf Zuverlässigkeit und Reihenfolgeerhaltung durch TCP 
- Variante für UDP-basierte Anwendungsprotokolle: DTLS
### HTTPS-Protokollstapel
- Durch diese Struktur unterstützt SSL/TLS prinzipiell jedes (TCP-basierte) Anwendungsprotokoll 
- HTTPS ist tatsächlich ganz „normales“ HTTP, mit der zusätzlichen SSL/TLS-Zwischenschicht 
- Ebenso wird SSL/TLS aber auch mit anderen Protokollen genutzt, z. B. mit SMTP, POP3, IMAP,... 
- Die SSL/TLS-Zwischenschicht nutzt X.509-Zertifikate für die Überprüfung von Identitäten 
- ... mit allen sich daraus ergebenden möglichen Problemen und Einschränkungen!
>[!important] Wichtig: SSL/TLS ist nicht unfehlbar – und höchstens so vertrauenswürdig wie das verwendete Zertifikat

