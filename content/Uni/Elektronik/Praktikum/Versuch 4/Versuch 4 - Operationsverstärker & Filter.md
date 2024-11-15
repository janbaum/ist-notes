## Operationsverstärker

Exemplarisch an Baustein LM358

- die Eingangsimpedanz des Verstärkers ist unendlich groß R_ein = ∞,
-  die Ausgangsimpedanz ist null R_aus = 0,
- die Differenzverstärkung ist unendlich groß A_D = Vdi f f = ∞.

#### Spannungfolger-Schaltung
**Einsatzgebiet** [[https://chat.openai.com/c/9cee1c0d-f797-4ba3-9077-c14bf77db0dd]]

*Angenommen, du hast eine hochohmige Signalquelle, wie beispielsweise ein Mikrofon mit einem hohen internen Widerstand. Wenn du versuchst, dieses Signal direkt in eine niederohmige Last (zum Beispiel einen Lautsprecher oder eine niederohmige Eingangsschaltung) einzuspeisen, würde eine beträchtliche Spannungsteilung am Übergang zwischen der hohen Quellenimpedanz und der niedrigen Lastimpedanz auftreten.

*Die Spannungsteilung kann dazu führen, dass nur ein Bruchteil des Signals die Last erreicht, und der Rest wird durch den hohen Widerstand der Signalquelle absorbiert. Das resultierende Signal an der Last wäre stark abgeschwächt und verzerrt.

*Hier kommt der Operationsverstärker ins Spiel. Durch seine hohe Eingangsimpedanz kann er das Signal von der hochohmigen Quelle effektiv aufnehmen, ohne dass es zu einer bedeutenden Spannungsteilung kommt. Gleichzeitig bietet der Operationsverstärker eine niedrige Ausgangsimpedanz, um das Signal mit minimalem Signalverlust an die nachgeschaltete niederohmige Last zu übertragen. So wird die hochohmige Quelle optimal an die niederohmige Last angepasst, und das Signal bleibt weitgehend unverändert.

#### Nicht-invertierender Verstärker

![[Pasted image 20231211200844.png]]


- Beim nicht-invertierenden Verstärker wird ein Gegenkopplungsnetzwerk genutzt um die Verstärkung einzustellen. Das Netzwerk besteht aus den zwei Widerständen R1 und R2.
- Für die Analyse der Schaltung wird zunächst die Spannung V− im Gegenkopplungsnetzwerkbenötigt. Das Netzwerk formt einen einfachen Spannungsteiler, die Spannung ergibt sich daher zu: ![[Pasted image 20231211200738.png]]

- Weil V_+ = V__:         ![[Pasted image 20231211201154.png]]

 - Verstärkung A:        ![[Pasted image 20231211201347.png]]
- Über die zwei Widerstände des Gegenkopplungsnetzwerks kann die Verstärkung der Schaltung einfach angepasst werden.

#### Nichtidealer Operationsverstärker
- ##### Statische Nichtidelitäten
	- Eingangoffsetspannung: ![[Pasted image 20231211202827.png]]
	- Wird der Operationsverstärker in einem nicht-invertierenden Verstärker wie in Abschnitt 1.2 beschrieben eingesetzt, so wird die Eingangsoffsetspannung mitverstärkt. Problem:
		- Bei kleinen Eingangssignalen und damit hoher Verstärkung kann eine Offsetspannung im mV-Bereich schon zu einer substantiellen Verfälschung des Ausgangssignals führen.
		- Bei *LM358* ca 2mV

- ##### Dynamische nichtidealitäten
	- Frequenzabhängig -> Immer Frage "Bei welcher Frequenz wird noch verstärkt ?"
		- Hier besonder zwei Parameter betrachtet:
			- Transifrequenz
			- Anstiegsgeschwindigkeit
		- Jeder Verstärker hat eine endliche Bandbreite, das heißt seine Differenzverstärkung fällt bei hohen Frequenzen immer weiter ab.
		- ##### Die Frequenz, bei der die Verstärkung genau eins erreicht, wird auch ( f_T ):
			- Transitfrequenz
			- Verstärkungs-Bandbreite-Produkt (*gain bandwidth product*)
			- Kleinsignalbandbreite 
			- unity-gain frequency ω_T [Skript] **genannt
				- Wird der Verstärker in Gegenkopplung und mit einer Verstärkung größer eins betrieben, kann die erzielbare Bandbreite (B) mit Hilfe der Transitfrequenz berechnet werden:                                                    ![[Pasted image 20231211204213.png]]
			- Stellt man diese Gleichung nach fT um, erhält man das Produkt aus **Bandbreite** B und Verstärkung A. Daher auch die Bezeichnung Verstärkungs-Bandbreite-Produkt.
			**Frage: Unterschied zwischen Bandbreite und Transitfrequenz ??????????**
			![[Pasted image 20231211212553.png]]
			Reine Verstärkung A ist generell höchter Wert. -> Durch SPannungsteiler in Gegenkopplung nur Bruchteil von A als Verstärkung -> kleinere Verstärkung größeres B (auf x-Achse)(siehe *Figure 3* obendrüber)
			
			- Auszüge aus Datenblättern im Versuchsskript S. 7
		##### Anstiegsgeschwindigkeit des Ausgangs
		- *slew rate, SR*
		- Betrachte Sprungantwort des Verstärkers
		![[Pasted image 20231211213257.png]]
		- Diese Beschränkung betrifft selbstverständlich nicht nur Impulse oder  Rechtecksignale. Auch sinusförmige Signale werden – abhängig von Amplitude und Frequenz – verzerrt oder gedämpft
		- Messung: OV in Gegenkopplung -> Eingangssignal anlegen, bei dem max SR am Ausgang erreicht/überschritten wird -> Am Ausgang Steigung des Ansiegs im linearen Bereich ablesen. 
		
  -> **Auswirkungen auf Bangbreite: Transitfrequenz + Ansiegsgeschwindigkeit:**
		Zusammenfassend sei gesagt, dass bei der Bestimmung der Bandbreite einer gegebenen Operationsverstärkerschaltung immer die Transitfrequenz und die Anstiegsgeschwindigkeit betrachtet werden müssen. Anderenfalls kann die Amplitude am Ausgang bei höheren Frequenzen geringer als geplant sein oder es können unerwünschte Verzerrungen des Signals auftreten.

## Filter

### Tiefpass
- lässt tiefe Frequenzen durch und Filtert hohe weg.
- meißt RC-Glied. 
- Die Amplitude des Signals am Filterausgang fällt oberhalb des Durchlassbereiches mit:
	- TP 1.Ordnung: 20dB/Dekade 
	- TP 2.Ordnung: 40dB/Dekade
- Grenzfrequenz bei 3dB (~29% Dämpfung)
	- Wird auch als Bandbreite bezeichnet

- Berechnung der Übertragungsfunktion:
	- ![[Pasted image 20231213103948.png]]
	- ![[Pasted image 20231213104004.png]]
	
- Berechnung der 3dB - Grenzfrequenz
	- Amplitude bei -3dB bestimmen ?????????????![[Pasted image 20231213104248.png]]
	- Gleichsetzen: |H(ω)| = A_−3 dB
		- ![[Pasted image 20231213104930.png]] ->![[Pasted image 20231213105003.png]]


#### Anwendungen
- -> eignen sich sehr gut um die Bandbreite von Signalen zu begrenzen:
	 - rausfiltern von Rauschen aus Signal mit bekannter Bandbreite
	 - Anti-Aliasing-Filter bei der Analog-Digital-Wandlung
	 - Frequenzweichen im Audiobereich zur Ansteuerung von Basslautsprechern


### Hochpass

- Analog zum Tiefpass:
	- aus Übertragungsfunktion H(ω) kann wieder 3dB-Grenzfrequenz ermittelt werden

#### Anwenung
- um Gleichspannungsanteile aus hochfrequenten Signalen zu filtern
	- zBsp soll kleines Wechselspannungssignal verstärkt werden, sind Gleichanteile störend, weil sonst Gleichanteil mitverstärkt und Verstärker in Sättigung geht


### Aktiver Bandpass

- Nicht nur passive Bauteile, sondern auch aktive, wie Verstärker:![[Pasted image 20231213105933.png]]
- Analyse: ![[Pasted image 20231213110006.png]]
- Übertragungsfunktion H(ω): ![[Pasted image 20231213110127.png]]
- Bei Mittenfrequenz (f_0) Verstärkung maximal
- Güte Q=f_0/B
- Bei einer Güte Q > 1/2 gilt das System als unterkritisch gedämpft. Das bedeutet, dass es auf eine Anregung mit einer gedämpften Schwingung reagiert (abklingender Sinus). Diese Schwingung weist im gegebenen Fall gerade die Mittenfrequenz f0 des Filters auf. Dieses Verhalten eignet sich gut um Instrumente elektronisch nachzubilden, da auch diese auf einen Anschlag mit einer abklingenden Schwingung reagieren.
- 