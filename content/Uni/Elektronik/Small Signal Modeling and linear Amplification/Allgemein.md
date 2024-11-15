## Allgemeine Notizen zu Kleinsignalwerten
- Note that in schematic representing a small-signal representation usually only low case characters are used (unless there is no doubt about their overall linearity, as example for $R_B$)
- The small-signal representation consists of lumped elements (verteilte Bauelementen, bei denen die relevanten Wellenlängen viel größer sind, als das System selbst; braucht also keine verstreuten Bauelemente)
- The value of these elements are considered constants. Of course the values are dependent of the DC-operation point: [[Berechnung Arbeitspunkt, Q-Point (DC bias Point)]], but this choice has been made
- Independent DC-Voltage sources are considered a short-cut 
-  Independent Current sources are considered open 


![Motivation](Elektronik_Skript_23_24_complete.pdf#page=115)

## Betrieb in welchem Bereich
- BJT: Vorwärtsaktiver Bereich
- MOSFET: Gesättigter Bereich
	- Drain-Source-Spannung > (Gate-Source-Spannung - Schwellspannung $v_T oder v_t ?$)
		- Dabei natürlich in leitendem Bereich: $v_{Gate} > v_Schwell$

## Determining Voltage Gain
Normal will man Leistungsverstärkung erreichen: Dabei Amplitude von Spannung und Strom jeweils nicht relevant, solang Leistung $P=U*I$ erreicht wird. Hier aber nur Spannungsverstärkung

### [[BJT Amplifier]]

### [[MOSFET Amplifier]]
### Effizienz BJT vs MOSFET
$\Rightarrow$ Bei anzulegenden $V_{DS}= 10 V$ und $I_{DS}$ am Arbeitspunkt $\approx$ 1.5 mA -> Leistung $P=15 mW$ - Sowohl für BJT, als auch für MOSFET
$\Rightarrow$ $A_v(BJT) = 50*A_v(MOSFET)$
$\Rightarrow$ BJT vielfach effizienter, aber MOS-Transistoren für integrierte/digitale Schaltungen viel besser geeignet