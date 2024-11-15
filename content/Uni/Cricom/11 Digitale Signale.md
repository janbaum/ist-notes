[Folie 46, Aufzeichnung ~min 15] : OFDM Symbole werden mit FFT erzeugt. 64 Sample im Frequenzbereich - 64 Sample in Zeit- und Frequenzbereich pro OFDM Symbol

[Folie 57, Aufzeichnung ~min 24] : Sinc-Funktion, Symbole im Frequenzbereich trennen; Orthogonale Subträger
		$delta$ f = sample rate -> die gibt uns das Spektrum
		$Bandbreite$ = 
		$\#Subcarrier$ = Größe der FFT
				$\Delta$ f= $\frac{Bandbreite}{\#FFT}$  -> Abstand zwischen Nulldurchgängen im Frequenzbereich / einzelner Subträger
			WIFI -> Bei 20 MHz Bandbreite und 64'er FFT: $\Delta$ f= $\frac{20 MHz}{64} = 312.5kHz$ , also 64 subcarrier mit jeweils 312.5 kHz Abstand
			<u>Frage</u>: Was passiert wenn \#FFT geändert wird ?
			<u>Antwort</u>: 
			- Je schneller einzelne Träger gewechselt werden, umso breiter wird das Spektrum (siehe Formel)
			-  Träger schneller wechseln -> kleinere FFT, weil dann nimmt man weniger Sample und man mit denen schnell die FFTs
			- Datenrate bleibt gleich !
			 <u>Frage</u>: Wie kann man bei OFDM den Abstand der Carrier verringern ?
			 <u>Antwort</u>: Langsamer sampeln oder größere FFT

Cyclic Prefix: 16 Sample "extra" um Interferrenz mit (eigenen) Reflexionen entgegen zu wirken (Multi-Path-Propagation) [Folie 62, ~min 40] 
	Wie viel MPP kann WLAN ab ? -> 16 Sample bei 20MHz Samplerate -> Zeit ? -> Wegunterschied bei Lichtgeschwindigkeit

Probeklausur 5.1:
	- eine FFT pro Bit(länge), genau aufs Bit alignen
