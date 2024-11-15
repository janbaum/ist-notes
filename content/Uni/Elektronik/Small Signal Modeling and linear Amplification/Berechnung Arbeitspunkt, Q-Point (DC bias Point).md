- Durch Beschaltung der Schaltung
- Kleinsignalparameter: Eigenschaften des Transistors die AC-Verstärkung beeinflussen
1. Berechne $I_B$ 
2. Alle nicht-DC-Quellen ignorieren (hier $v_s$) 
	- Eingangskreis: 
		- DC Spannungs- / Stromquellen: $V_S$ (große Buchstaben) $\rightarrow$ hier 0.7 V
		- (zeitabhängige) Signalquellen: $v_s$ (kleine Buchstaben)
		- $\rightarrow$ Spannung über beiden Quellen: $v_S$ (klein v, groß S)
3. Schaltung neu Zeichnen
	- Collector-Strom weglassen


![[Pasted image 20240313112618.png]]
![[Elektronik_Skript_23_24_complete.pdf#page=117]]

#### Interpreting Small Signal Parameters
Hier ist auf [Seite 4-12/13](Elektronik_Skript_23_24_complete.pdf#page=119) zu erkennen, dass kleine Wechselspannungen große Auswirkungen auf den Arbeitspunkt der Schaltung haben. Daher betrachten wir hier nur **Kleinsignale** betrachtet! 
5. Dadurch können wir die Steigung der e-Kurve am Arbeitspunkt als lineare Gerade eines Ohm'schen Widerstands ersetzen.
##### Graphische Herleitung
![[Pasted image 20240313122457.png]]
$y-Achse: I_D$ 
$x-Achse: V_{BE}$
Danach ist $v_s$ AC-Quelle im [Erstazschaltbild](Elektronik_Skript_23_24_complete.pdf#page=120). Dadurch sind alle Strom- wie Spannungsgrößen Sinusförmig (kleine Buchstaben). Aber Berechnungen so, als ob es sich um DC Größen handelt.

#### Berechnung von AC-Werten
6. Mit neuer **linearen** Ersatzschaltung,  mittels Strom- Spannungsanalyse **Amplitude von Wechselspannung und Wechselstrom ermitteln!**

