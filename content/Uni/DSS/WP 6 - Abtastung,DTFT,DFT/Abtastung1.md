### Vorlesung DSS
$x_n=x(t) mit t=nT \rightarrow Sample$
$T \rightarrow Abtastintervall$ 
$f_a = 1/T \rightarrow Abtastrate/Abtastfrequenz$
$\omega_a=2\pi/T \rightarrow Abtastkreisfrequenz$
#### Ideale Abtastung
[original Signal mit Dirac-Kamm multiplizieren](WP6_Abtastung.pdf#page=5)
Daraus periodische, aber eineindeutige Zuordnung im Frequenzbereich $\rightarrow$ Tiefpassfilter $\rightarrow$ 
- [Voraussetzung](WP6_Abtastung.pdf#page=9) bei [[#^Abtasttheorem]]
	- Spektrum muss Bandbegrenzt sein
	- Filter muss passen $\rightarrow$ Abtastrate **T muss klein genug** sein, damit $2\pi/T$ dementsprechend groß genug wird, damit Perioden sich nicht überlappen 
Sidenote: Multiplikation mit einem Rechteck im Frequenzbereich = Faltung mit $\frac{sin(x)}{x} = si(x)$ im Zeitbereich
![](WP6_Abtastung.pdf#page=12)

![Praktische Aspekte bei der Abtastung](WP6_Abtastung.pdf#page=17)

![Nichtideale Abtastung](WP6_Abtastung.pdf#page=18)

#### [Zeitdiskrete Fourier-Transformation (DFDT)](WP6_DTFT.pdf)
- *Fourier-Transformation für stationäre Prozesse geeignet
- *LT/ZT für Ein- Auschaltvorgänge geeignet

![](WP6_DTFT.pdf#page=11)

![14 Verbindung zur Fourier-Transformierten kontinuierlicher Signale](WP6_DTFT.pdf#page=14)








### Uni Siegen
#### [Abtasttheorem](uni-siegen-signalverarbeitung.pdf#page=13): 
Es muss mindestens mit der doppelten Frequenz des original Signals abgetastet werden, damit kein [Aliasing](uni-siegen-signalverarbeitung.pdf#page=14) entsteht (Wagenrad im Film). Reale Signale bestehen aus vielen Frequenzen. Daher **bezieht sich dies auf die höchste Teilfrequenz** des realen Signals. ^Abtasttheorem

Falls die nicht gegeben ist, kommt es zu aliasing, das heißt die Frequenzkomponenten mit $f_0 < f_{max}$ werden im Bereich niedriger Frequenzen gespiegelt. Dadurch können hochfrequente Störsignale großen Schaden anrichten und niederfrequente Nutzsignale überlagern.

-> In der Praxis wählt man gerne $f_0 = 5..10*f_{max}$ 

*Note: In Realität sind die meisten Signale nicht Bandbegrenzt, haben also gar keine Komponente maximaler Frequenz, dh. $f_{max} = \infty$, daher perfekte Rekonstruierung nicht ganz möglich*

Die Trägerfrequenz $\omega_1$ wird durch das Abtasten mit  der Frequenz $\omega_0$ an folgenden Frequenzen gespiegelt:  $\omega_l =  \omega_1 +  \omega_0$  mit $l = ...-2,-1,0,1,2,...$   

#### [Quantisierung](uni-siegen-signalverarbeitung.pdf#page=20)
Durch die Quantisierung der Amplitude bei der A/D-Wandlung wird ein kontinuierlicher Zahlenbereich auf einen diskreten abgebildet. Das bedeutet, dass jeweils einem Intervall ein
fester Zahlenwert zugeordnet wird. Alle Zahlen innerhalb dieses Intervalls sind dann nach
der Quantisierung nicht mehr unterscheidbar. Wenn wir einen kontinuierlichen Zahlen-
bereich von $x_{min}$ bis $x_{max}$ auf mit n Bits quantisieren wollen, dann ergeben sich $2^n$ Intervalle
bzw. Quantisierungsstufen. Damit berechnet sich der maximale Quantisierungsfehler zu:
$e_{Q_{max}} = \frac{x_{max}-x_{min}}{2^n}$ 

denn dies entspricht der Intervallbreite. Der Quantisierungsfehler ist stets positiv, da die grüne Kurve immer über der blauen liegt.

[Zeitdiskreter Einheitssprung](uni-siegen-signalverarbeitung.pdf#page=49)
Der zeitdiskrete Einheitsimpuls (Kronecker-Delta) ist mit Höhe 1 hingegen unterschiedlich zum zeitkontinuierlichen Dirac-Impuls (Höhe ∞) definiert.

[DGL](uni-siegen-signalverarbeitung.pdf#page=53)
Für kleine Abtastzeiten $T_0$ → 0 kann jede DGL näherungsweise diskretisiert werden, indem man die Ableitungen durch Differenzenquotienten ersetzt.

