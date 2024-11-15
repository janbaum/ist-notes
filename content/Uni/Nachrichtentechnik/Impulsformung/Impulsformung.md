[[NT Skript 2018.pdf#page=131|Skript]] inklusive [[NT Skript 2018.pdf#page=132|Einordnung]] 
- [[7-Impulsformung.pdf#page=8|Symbolinterferenz]] durch $1/2f_b$ Verschiebung aller anderen Impulse vermeiden -> Problem: Jitter
	- _Nyquist-Theorem_
### 7.2.2 Realisierbare Impulsformfilter mit flacher Flanke (raised cosine (rc)-Filter)
- [[7-Impulsformung.pdf#page=9|Raised Cosine Filter ff]]
	- roll off Faktor $r$ entscheidend
#### Abtastunsicherheit (Augendiagramm, eye pattern)
[[7-Impulsformung.pdf#page=11|Augendiagramm]] zur Bewertung der Symbolfehlerwarscheinlichkeit
- Folie 23: Cosinus Filter beste, bei Kabel Einschränkungen ertragbar, weil bei Kabel nicht mehr viel andere Störung dazu kommt. 
- Nachteil Cos: doppelte Bandbreite
- In Mobilfunk kein Cosinus Filter, sonder Gauss Filter in Europa (historische Gründe)
### 7.2.3 Korrekturfilter für ISI-freie Übertragung von Nicht-Dirac-Impulsen
[[NT Skript 2018.pdf#page=144|Skript]]
[[7-Impulsformung.pdf#page=14|Kompensationsfilter]]

### 7.3 Signalangepasste Filterung (Matched Filter)
[[NT Skript 2018.pdf#page=146|Skript]]
>In der Praxis wird die Spektrumsformung meist durch **Tiefpassfilter vor dem Modulator und nach dem Demodulator** durchgeführt. 
>Der **Bandpass im Sender** dient dann lediglich zur Unterdrückung von unerwünschten Harmonischen des Trägers und des Basisbandsignals sowie der Mischprodukte höherer Ordnung und der **Eingangsbandpass des Empfängers** selektiert lediglich das gewünschte Frequenzband (mehrere RF-Kanäle bei Frequenzmultiplexsystemen) bei gleichzeitiger Unterdrückung der Spiegelfrequenzen. Die Bandbreite beider Bandpässe sollte mindestens die doppelte Bandbreite des Durchlassbereiches der Tiefpassfilter besitzen: $B_{BPF,T}>2B_{LPF,T}$ und $B_{BPF,R}>2B_{LPF,R}$


