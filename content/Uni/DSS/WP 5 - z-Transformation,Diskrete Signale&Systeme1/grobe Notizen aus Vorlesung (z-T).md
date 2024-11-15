Literatur für 2. Teil: Signal- und Systemtheorie, ...

Fragen: [Folie 1](VL-ZT_2_z-Transformation.pdf#page=1)

- diskrete Signale sind Folge von abgetasteten Messwerten
- Operation um von kontinuierlichem auf diskretes Signal: 
	- ideal abtasten (mit Diraque, mit **Gewicht =1**)
	- quantisieren: analoge Werte -> digitale Werten zuweisen
		- wert-kontinuierlich -> wert-diskret
	- -> A/D-Wandlung !
- Reihenfolge bei Quantisierung: 
	- Kann eine Rolle spielen, wenn vor Abtasten noch keine Werte diskretisiert wurden. Evtl gehen Informationen verloren
-> Signal $f(t)$ wir in reine Zahlendarstellung überführt, damit unabhängig von t

Frage: **Wie dicht sollten wir abtasten ?**

### Elementare diskrete Signale

##### Impulsfolge [Folie 6](VL-ZT_2_z-Transformation.pdf#page=6)
![[Pasted image 20231212183647.png]]

- Impuls zum Zeitpunkt Null
- Verschobener Impuls
- Abtast- Ausblendeigenschaft -> alle Werte ausgeblendet(=0), außer **einem** ;    
	- Herleitung: [Folie 9](VL-ZT_2_z-Transformation.pdf#page=9)

##### diskreter Deltakamm [Folie 10](VL-ZT_2_z-Transformation.pdf#page=10)
- *wie konstante Funktion*
- Werte im N-Abstand 

##### Sprungfolge [Folie 11](VL-ZT_2_z-Transformation.pdf#page=11)
- *wie Sprungfunktion*
- *integrieren*: aufsummieren
- *differenzieren*: Differenzenquotient (Steigungsdreieck)

##### Exponentialfolge [Folie 13](VL-ZT_2_z-Transformation.pdf#page=13)
- mögliche "Formen":
	- aufklingend
	- abklingend
	- alternierend
	- konstant
- komplexen Exponentialfunktionen können mit Cosinus-/Sinusfolgen dargestellt werden
- jede Exponentialfolge ist [frequenzperiodisch](Abtastung.md): -> Abtastwerte gelten für alle ganzzahlige Vielfache der anfänglichen Frequenz 
	- Außer für irrationale Abtastrate (bsp $\sqrt2$)
	**-> Bedingung: [Folie 16](VL-ZT_2_z-Transformation.pdf#page=16)**
	Damit im $sinus(\frac{n\pi}{4})$ $2\pi$ steht, muss $n=8$ sein, -> 8 mal in einer Periode abtasten
	- Wenn Abtastrate falsch gewählt wird, jedes Mal bei abtasten an gleicher Stelle in der Periode -> anderer Wert; *Phasenverschiebung ?*
	- *Quiz 5*: Ohne Kenntnis der Abtastfrequenz keine eindeutige Antwort möglich


### z- und Laplace-Transformation ![[VL-ZT_2_z-Transformation.pdf#page=2]]
##### Was ist die z-Transformierte ?
kontinuierliches Signal -> diskretisieren -> Laplace-Transformation => z-Transformierte
$U_s(s) = \sum{u(n)*e^{-p*n*T}}$ -> $z = e^{p*T}$
###### => $U_s(s) = \sum{u(k)*z^{-n}}$ 

- Entwicklung der z-Transformation aus der LP-Transformation
	- einseitige LP-Transformation -> einseitige z-Transformation
- Konvergenzgebiet [Folie 11 ff](VL-ZT_2_z-Transformation.pdf#page=11)
	- Konvergenzgebiet ist Fläche außerhalb des Kreises
	- Radius bestimmt durch größte **$Polstelle$
- -> Konvergenzbereich finden -> Z-Transformierte ?
- Unterschied: Kausalität von Systemen <-> Signalen 
- Bsp. [Folie 15](VL-ZT_2_z-Transformation.pdf#page=15): Ergebnis =1 ist eine Funktion, also eine Ebene.
- 
#### Eigenschaften der Z-Transformation [Folie 18](VL-ZT_2_z-Transformation.pdf#page=18)
- Linearität
- Konvergenzgebietsvergrößerung bei linearer Operation
- z-Transformierte der Summe zweier (kausaler) Exponentialfolge
- z-Transformierte der (kausalen) Cosinus- und Sinusfolge
- Verschiebung im Zeitbereich nach rechts
	- mittels Korrekturterm für $n_0$
	- Wenn Folge Kausal, keine Korrekturterme nötig; wieso ?
- Verschiebung im Zeitbereich nach links
- z-Transformierte der zeitverschobenen Exponentialfolge
- Dämpfung / Modulation der Folge, Skalierung von *z*
- z-Transformierte der gedämpften Cosinus- und Sinusfolge
- Lineare Gewichtung der Folge, Ableitung im z-Bereich
- z-Transformierte der Rampenfolge

-> Ergebnis (also z-Transformation) immer Polynome in z

## 13.12.23
### Fragen 

- #### Was passiert im z-Bereich, wenn Folge gedämpft wird ? [Folie 28](VL-ZT_2_z-Transformation.pdf#page=28)
	- Konvergenzradius multipliziert sich um Faktor |a|![[Pasted image 20231213114915.png]]
	- -> größerer Radius -> kleinerer Konvergenzbereich
	
- #### Was passiert bei Ableitung im z-Bereich mit diskreter Folge ?
	- Lineare Gewichtung im Originalbereich entspricht der Ableitung im z-Bereich
	- ![[Pasted image 20231213115443.png]]
	- Konvergenzgebiet ändert sich nicht
		- -> wie bei Fouriertransformation (bei Ableitungen) 
		
- #### Wie kann im Zeitdiskreten ein Faltung definiert werden ? (-> Impulsantwort)
	- ![[Pasted image 20231213120333.png]]
	- Eigenschaften der Faltung (Kommut., Distr., Assoz., Neutralelement)
	- Faltung mit $Diraque$ (verschoben um $t_0$) = gleiche Folge, ebenfalls verschoben um $t_0$
		- Impuls fällt weg, Folge bleibt stehen
	- Produkt mit zeitverschobenem $Diraque$ -> Ausblendeigenschaft -> Wert an $t_0 *\delta$, alle anderen Stellen =0
		- Impuls muss stehen bleiben
	
	- Berechnung: [Folie 33](VL-ZT_2_z-Transformation.pdf#page=33)
		- für $h_(-i) -> h_i$ an y-Achse spiegeln
		- Länge der Faltung: 
			- im Analogen $T_1 + T_2$
			- im Diskreten $T_1 + T_2 - 1$
		- Methoden zur Berechnung:
			- Papierstreifenmethode, Tabelle:[Folie 34](VL-ZT_2_z-Transformation.pdf#page=34)
			- Berechnung mit Impulsfolge: [Folie 35](VL-ZT_2_z-Transformation.pdf#page=35)
	
	- Erst abtasten, dann falten; oder erst Falten und dann abtasten ? -> 
	- Sind die Abtastwerte der kontinuierlichen Faltung gleich den Folgenwerten der diskreten Faltung ?
		- -> Im allgemeinen nicht, da bei der kontinuierlichen Faltung durch die Integration auch alle Funktionswerte und zwischen den Abtaststellen das Ergebnis beeinflussen.
				

- #### Welche Operation im z-Bereich  entspricht der Faltung zweier Folgen im Zeitdiskreten ?

	- ##### Faltungsregel
		- Eine **zentrale Eigenschaft der z-Transformation** ist die Überführung der Faltungsoperation im diskreten Zeitbereich in eine Multiplikation im z-Bereich:![[Pasted image 20231213125640.png]]
		- Beispiel auf [Folie 39](VL-ZT_2_z-Transformation.pdf#page=39)

- #### Können Anfangs und Endwerte einer Folge direkt aus der z-Transformierten bestimmt werden ?

	- Für den Anfangswert einer Folge gilt  ![[Pasted image 20231213130929.png]]
	- Damit kann man den Anfangswert einer Folge direkt aus ihrer z-Transformierten ohne Rücktransformation ablesen.
	- Anschauliche Begründung:
		- *Sind die Voraussetzungen erfüllt, setzt sich die Folge f_n aus abklingenden Exponentialfolgen (Pole innerhalb des Einheitskreises) und evtl. einem konstantem Anteil (Pol bei z=1) zusammen.*
		- *Für $n \rightarrow \infty$ verschwinden die Anteile der abklingenden Exponentialfunktionen, und nur der konstante Anteil mit Pol bei z=1 bleibt übrig.*
		- -> ?????????
		- 