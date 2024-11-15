#### Ursprungsfrequenz aus Signal wider heraus bekommen:

*Excursion: Energy and Power*

- Refferenz-Signal, Korrelation von Empfangenem Signal mit einer Frequenz: So kann nacheinander Spektrum aufgetragen werden. (S.73)
- Korrelation von Sinus- und Cosinus-Signalen:Orthonogal! (S.79) 
	- -> einmal mit -sin(), einmal mit cos() korrelieren
-  FFT
- DFT mit FFT: Beispiel
	- spample rate von SDR ist fix, welche sample rate benutzen ?
		- meistens 2'er Potenzen (in GNU Radio bspw )
		- auch wenn FFT gemacht wird, kommen immer genau so viel Daten raus, wie rein gekommen sind
			- -> wie viele sample auf einmal sammeln, bevor ausgegeben werden ?
			- höhere sample rate dauert länger zu "buffern" (?) 
			- man sieht evtl spike schlechter als mit geringerer samp.rate
			- Spektrum kann **höher aufgelöst** werden, sieht schärfer aus
			- Für kurze Pulse etc niedrige sample rate besser !
	- 