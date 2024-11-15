- Spezifiziert in RFCs 1945 (HTTP/1.0) und 2616 bzw. 7230–7235 (HTTP/1.1) 
- Nachfolger: HTTP/2 in RFC 7540, mit deutlich anderer Grundstruktur
>[!linfo] Terminologie
>- Eine Webseite besteht aus Objekten (HTML-Dateien, Bildern, Audio/Video-Dateien,. . . ) 
>- Typischerweise (mindestens) ein HTML-Objekt 
>- HTML (HyperText Markup Language) ist eine Spezifikationssprache für formatierte Dokumente mit Text, eingebetteten Bildern, Links,. . .
>- Die Aufgabe eines Browsers (= HTTP-Client) ist das Herunterladen von solchen Dokumenten und das Anzeigen von HTML-Dokumenten
> ------------
>- Wie ein Web-Objekt (also z. B. eine HTML-Seite) angezeigt wird, ist unabhängig vom Protokoll – **HTTP kümmert sich nur um die Übertragung**
>- In HTTP ist jedes Objekt über eine URL (Uniform Resource Locator) adressierbar, z. B. `https://www.etit.tu-darmstadt.de/fachbereich/index.de.jsp`

>[!example]- Kurzdurchlauf Webseitenaufruf
>![[02-Anwendung.pdf#page=33]]

- Heute bestehen praktisch alle Webseiten aus mehr als einem Objekt. 
- Diese Objekte sind (möglicherweise mehrfach verschachtelt) in ein Hauptdokument eingebettet.
- Der Browser empfängt und verarbeitet zunächst dieses Hauptdokument. Dabei erfährt er, welche weiteren Objekte er laden muss. 
- Die besorgt er dann mit separaten, unabhängigen HTTP-Anfragen Das wird fortgesetzt, bis der Browser alle benötigten Objekte geladen hat.
## HTTP/1.0 -> HTTP/1.1 -> HTTP/2

| HTTP/1.0                                                                                                                                        | HTTP/1.1                                                                                                                                                                        | [[#HTTP/2]]                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| ----------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Every request requires new TCP connection                                                                                                       | establishes `connection: keep-alive` & pipelining                                                                                                                               | binary framing layer & several binary streams over one TCP connection                                                                                                                                                                                                                                                                                                                                                                                                   |
| In HTTP/1.0, the client had to break and remake the TCP connection with every new request, a costly affair in terms of both time and resources. | This allows the client to send multiple requests along the same connection without waiting for a response to each, greatly improving the performance of HTTP/1.1 over HTTP/1.0. | Problem bei HTTP/1.1: [[#Head-of-Line Blocking]]: At the most granular level, the communication channel consists of a bunch of binary-encoded frames, each tagged to a particular stream. The identifying tags allow the connection to **interleave these frames during transfer and reassemble them at the other end**. The interleaved requests and responses can **run in parallel without blocking the messages behind them**, a process called **_multiplexing_**. |


## HTTP-Anfragen
Eine HTTP-Anfrage (Request) beginnt mit einer Anfragezeile, die eine zu verwendendene Methode enthält:
- GET
	- Jede HTTP-GET-Anfrage holt genau ein Objekt
- POST
- HEAD
- PUT
- DELETE

`GET /fachbereich/index.de.jsp HTTP/1.1`

Außer der Methode gibt die Anfragezeile an, welches Dokument auf dem Server angerufen wird und welche HTTP-Protokollversion verwendet werden soll

Der Anfragezeile können noch HTTP-Header-Zeilen folgen, z. B. 
```http
Host: www.etit.tu-darmstadt.de 
User-agent: Mozilla/5.0 (X11; Linux i686; rv:99.0) \ Gecko/20100101 Firefox/99.0
Connection: keep-alive 
... 
```
Eine leere Zeile zeigt das Ende einer HTTP-Anfrage an.

## HTTP-Antworten
Eine HTTP-Antwort beginnt mit einer Statuszeile (Protokollversion + Statuscode + Beschreibung):
`HTTP/1.1 200 OK` 
Es folgen wieder Headerzeilen: 
```http
Content-Type: text/html; charset=UTF-8 
Date: Thu, 24 Oct 2021 11:14:24 GMT 
Connection: keep-alive 
... 
```
Dann eine Leerzeile.
Schließlich kommt das eigentliche angefragte Objekt. 

Parallelen zu SMTP (und vielen anderen Internet-Protokollen) sind unübersehbar. Aber einige Dinge sind anders gelöst als in SMTP so gibt es z. B. keine Einschränkung des Zeichensatzes.

## HTTP-Statuscodes
>[!example] Ein paar Beispiele für HTTP-Statuscodes: 
>- 200 OK – Alles in Ordnung 
>- 400 Bad Request – Der Server hat die Anfrage nicht verstanden 
>- 404 Not Found – Das angefragte Objekt wurde auf dem Server nicht gefunden 
>- 505 HTTP Version Not Supported

## Header-Zeilen
- `Host`: Von welchem Webserver wird etwas angefordert 
	- **der Host-Header ist Pflicht seit der HTTP-Version HTTP/1.1**
- `User-Agent`: Welcher Browser wird in welcher Version verwendet 
	- erlaubt es dem Server, evtl. speziell angepasste Versionen der Objekte auszuliefern
- `Connection: keep-alive` bedeutet, dass der Client gerne möchte, dass der Server nach dem Beantworten dieser Anfrage die TCP-Verbindung offen lässt ([[#Persistentes HTTP]])
	- Andernfalls würde der Server nach Beantworten der Anfrage die Verbindung schließen 
		- **das war das Standardverhalten im ursprünglichen HTTP**
- `Content-Type`: Welche Art von Daten ist enthalten (hier auch: welcher Zeichensatz) 7-Bit-Codierung wie in SMTP ist bei HTTP nicht nötig 
- `Content-Length`: Wie viele Bytes enthält der Datenteil? 
- `Date`: **Wann wurde die Anfrage beantwortet?** nicht wann wurde das Dokument erstellt/geändert! 
## Dynamisch erzeugte Webseiten
- Server-seitig: CGI (Common Gateway Interface)
- Client-seitig: JavaScript

## Hochladen von Formulardaten: GET vs. post
Die Daten können in einer GET-Anfrage in den angefragten Pfad hineincodiert werden:
```
GET /ein/pfad?a=irgendwas&b=wasanderes HTTP/1.1 
Host: www.meineseite.de
```

Bei der POST-Methode stehen die Formulardaten im Datenteil der HTTP-Anfrage:
```
POST /login.jsp HTTP/1.1 
Host: www.meineseite.de 
Content-Length: 28 
Content-Type: application/x-www-form-urlencoded 

userid=alice&password=geheim
```

## Zustandslosigkeit
HTTP ist ein zustandsloses Protokoll: Der Server merkt sich keine Informationen über vorherige Anfragen eines Clients.
Warum: Einfachheit
Trotzdem können sich Webseiten Zustände merken? $\downarrow$

## HTTP-Cookies
- Ein HTTP-Server kann mit einer HTTP-Antwort einen Cookie „mitliefern“ Dafür wird ein spezieller HTTP-Header verwendet: 
	- ```Set-Cookie: irgendeincookietext``` 
- Der Browser sieht diesen Header und speichert den Cookie für diese Webseite 
- Jedesmal, wenn zukünftig eine Webseite von diesem Server angefordert wird, wird der Cookie mitgeschickt Cookie: `irgendeincookietext` 
- Der HTTP-Server kann den Cookie an die Webanwendung weitergeben; sie kann so den Benutzer wiedererkennen
-> Die Informationen werden also im Client gespeichert
>[!note] Der HTTP-Server (nicht zwangsläufig die Web-Anwendung „dahinter“!) ist also weiterhin zustandslos

Typische Anwendung:
- Die Web-Anwendung wählt für jeden neuen Benutzer eine eindeutige ID als Cookie 
- Alle HTTP-Anfragen dieses Benutzers können so als zusammengehörig erkannt werden 
- Der Benutzer kann auf seinem „Weg“ durch die Webseite „verfolgt“ werden
>[!linfo]- Graphic 
>![[02-Anwendung.pdf#page=51]]


## Round Trip Times und Latenzen
Typische RTT's:
- Innerhalb Deutschlands: ca. 5–20 ms 
- Innerhalb Europas: bis ca. 50 ms 
- Nach Nordamerika: ca. 100–150 ms 
- Weltweit: bis ca. 500 ms
>[!note] Physikalisches Limit Lichtgeschwindigkeit
>Nach Nordamerika und zurück (ca. 16 000 km) sind 53 ms eine absolute untere Schranke
>>[!cite] „No matter how hard you push and no matter what the priority, you can’t increase the speed of light.“ (RFC 1925)

>[!example] Beispiel
>Wie lange dauert das Absenden eines 10 KB großen Objektes über eine VDSL-Leitung mit 80 MBit/s Übertragungsrate?
>$$\frac{10KB}{80MBit/s}=1ms$$

>[!tip] $\Rightarrow$ Das Absenden (bzw. Empfangen) des Objektes (Übertragungszeit) braucht also nur einen Bruchteil der Reisezeit durch das Netz (Latenz)! 
>>
>$\Rightarrow$ Auch Verarbeitungszeiten (in Client und Server oder auch in den Zwischenstationen bei der Paketweiterleitung) sind im Vergleich vernachlässigbar klein

Hier gibt es eine anschauliche [[02-Anwendung.pdf#page=55|Graphik]]


## HTTP-Performanz
>[!important] Interaktive Protokolle wie HTTP müssen die Zahl der notwendigen RTTs gering halten!

### Persistentes HTTP
- Als Webseiten komplexer wurden, hat man das Problem erkannt und HTTP so erweitert, dass RTT's eingespart werden können 
- Idee hinter Persistentem HTTP: 
	- nicht für jeden Request eine neue TCP-Verbindung öffnen 
	- Erfordert entsprechende Funktionen im HTTP-Protokoll <font color="#ff0000">(⇒ `Connection: keepalive`)</font> 
- Ursprüngliches HTTP: Server schließt Verbindung nach Ende des Requests, Client schließt danach ebenfalls 
- Spätere Erweiterung: Client und Server können sich darauf einigen, die Verbindung offen zu halten

>[!note]- Vergleich nicht-persistent / persistent
>![[02-Anwendung.pdf#page=59]]
>![[02-Anwendung.pdf#page=61]]

Ablauf persistente Verbindung:
1. liest einen Request von der TCP-Verbindung 
2. beantwortet ihn 
3. liest den nächsten Request 
4. usw. 

Es macht für den Server keinen Unterschied, wann die gelesenen Requests abgeschickt wurden! Das **Warten** auf die Antwort zu früheren Requests ist also per se **nicht notwendig** $\downarrow$

### Pipelining
- Der Browser kann also über dieselbe Verbindung Folge-Requests sofort absenden und dadurch weitere RTT's sparen
- Dadurch ist weitere Zeitersparnis möglich:
	1. 1 \* Verbindungsaufbau 
	2. 1 \* HTTP-Request/Response für die HTML-Seite 
	3. dann ohne Warten auf weitere Antworten direkt drei Requests zusammen: <font color="#ff0000">3 RTT's</font>

### Head-of-Line Blocking 
Potentielles Problem:
- Verzögerung durch noch nicht ausgelieferte Objekte
>[!cite] natural bottleneck
>*Since multiple data packets cannot pass each other when traveling to the same destination, there are situations in which a request at the head of the queue that cannot retrieve its required resource will block all the requests behind it. This is known as head-of-line (HOL) Blocking*
>source: [Digital Ocean](https://www.digitalocean.com/community/tutorials/http-1-1-vs-http-2-what-s-the-difference)


### Parallele TCP-Verbindungen
- Mehrere parallele TCP-Verbindungen können genutzt werden, um mehrere Objekte gleichzeitig abzurufen 
- Aber: Diese Verbindungen müssen sich natürlich die Netzwerkkapazität teilen – Gewinne sind dadurch begrenzt Zusätzliche Verbindungen erzeugen zusätzliche Last auf dem Server 
- IETF-Standards für HTTP/1.1 empfehlen: nicht mehr als zwei parallele Verbindungen (RFC 2616) 
	- Browser halten sich allerdings nicht daran 
	- Schwierige Optimierungsaufgabe für Browserprogrammierer: 
		- Wann wie viele parallele Verbindungen, und welche Objekte in welcher Reihenfolge über welche Verbindung holen?

### Content Distribution Networks (CDN)
- Wegen der wichtigen Rolle, die die Länge der RTT für die Performanz von Web-Angeboten spielt, sind Inhaltsanbieter stark an niedrigen RTT's interessiert 
- Ziel deshalb: Webserver „nahe zu den Browsern“ bringen 
	- Idee: mehrere Server mit (i. d. R.) identischen Inhalten 
	- Nutzer werden zum nächstgelegenen geleitet 
	- Das nennt man ein **Content Distribution Network (CDN)** 
	- Weit verbreitetes Konzept, mehrere kommerzielle Anbieter Akamai, Limelight, Amazon CloudFront, CDNetworks,. . .  
- Wie entscheidet man, was die „beste“ Kopie für eine gegebene Benutzer-IP-Adresse ist? 
- Hier sind viele Kriterien möglich – Geschäftsgeheimnis der CDN-Firmen 
	- erwartete RTT 
	- Netzwerk- und/oder Serverlast 
	- Kosten der jeweiligen Verbindung (Peering-/Transit-Vereinbarungen!)
	- Wenn man einen geeigneten Server identifiziert hat, leitet man den anfragenden Browser dahin um 
		- es gibt mehrere Möglichkeiten, das technisch zu realisieren
### Caching
- Eventuell lässt sich die Zeit für eine Anfrage ja manchmal vollständig vermeiden? 
- Idee: HTTP-Clients können Objekte von Webservern in einem lokalen Cache zwischenspeichern 
- Wenn der Benutzer dann dieselbe Seite noch einmal besucht, müssen sie nicht erneut übertragen werden 
>[!attention] Aber: Woher soll der Browser wissen, ob die Version des Objektes, die im Cache liegt, noch aktuell ist?$\downarrow$

### Expires-Header 
- Beim Ausliefern eines Objektes kann ein Server einen Zeitpunkt angeben, bis zu dem das Objekt gültig bleiben soll 
- Bis dahin können Anfragen nach diesem Objekt also vollständig vermieden werden 
- Der Expires-Header gibt einen Zeitpunkt an, bis zu das Objektes sicher verwendet werden kann 
>[!attention] Problem: Das erfordert, dass der Server weiß, wann sich das Objekt zum nächsten Mal ändern wird... 

 -> Um dieses Problem zu vermeiden, gibt es noch einen zweiten Mechanismus in HTTP $\downarrow$
#### Caching: Bedingtes get
- Angenommen, ein Client fragt folgendes Objekt an:
```http
GET /ein/pfad.jpg HTTP/1.1 
Host: www.einserver.de
```

- Dann kann der Server beim Beantworten einer Anfrage den „Stand“ eines Objektes mit einer speziellen Header-Zeile angeben: 
```http
HTTP/1.1 OK 
Date: Thu, 15 Nov 2021 10:56:12 
Last-Modified: Thu, 14 Nov 2012 14:44:32 
Content-Type: image/jpeg
```

- Der Client kann nun eine GET-Anfrage stellen, die das Objekt nur dann überträgt, wenn es sich gegenüber der Version im Cache geändert hat 
```http
GET /ein/pfad.jpg 
HTTP/1.1 
Host: www.einserver.de 
If-modified-since: Thu, 14 Nov 2012 14:44:32 
```
`If-modified-since` entspricht genau der Header-Zeile `Last-Modified` aus der vorangegangenen HTTP-Antwort 
- Falls sich nichts geändert hat, überträgt der Server das Objekt nicht erneut, sondern antwortet mit Statuscode 304: 
```http
HTTP/1.1 304 Not Modified 
Date: Thu, 15 Nov 2021 11:03:12
```
>[!note] `If-modified-since` kann die übertragene Datenmenge (und damit Übertragungszeiten) reduzieren. Es verringert aber nicht die Zahl notwendiger RTT's!


## HTTP/2
- Basiert auf Entwürfen von Google („SPDY“)
- Zentrale Ziele: 
	- Beschleunigung des Seitenaufbaus 
	- Reduktion der Zahl paralleler TCP-Verbindungen 
	- möglichst gute Kompatibilität zu existierenden Anwendungen
### Streams und Rahmen
- **HTTP/2 unterstützt mehrere unabhängige Streams über dieselbe TCP-Verbindung** 
- Die Daten eines Streams werden dann in Rahmen (Frames) zerlegt Rahmen unterschiedlicher Streams können abwechselnd über dieselbe TCP-Verbindung übertragen werden 
- Wann welche Rahmen für welchen Stream übertragen werden, ist flexibel 
	- so entstehen Freiheitsgrade, die für Performanzvorteile genutzt werden können 
	- insbesondere: Head-of-Line-Blocking kann vermieden werden
### Multiplexing
>[!cite] *Multiplexing resolves the head-of-line blocking issue in HTTP/1.1 by ensuring that no message has to wait for another to finish.*
>source: [Digital Ocean](https://www.digitalocean.com/community/tutorials/http-1-1-vs-http-2-what-s-the-difference#http-2-advantages-of-the-binary-framing-layer)