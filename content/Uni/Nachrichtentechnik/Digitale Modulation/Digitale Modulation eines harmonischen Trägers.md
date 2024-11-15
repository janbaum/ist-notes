[[NT Skript 2018.pdf#page=187|Skript]]
### 9.1 Harte, binäre Umtastung eines sinusförmigen Trägers
[[NT Skript 2018.pdf#page=188|Skript]]
#### 9.1.1 Binary Amplitude Shift Keying (BASK oder 2-ASK)

#### 9.1.2 Binary Phase Shift Keying (BPSK oder 2-PSK)
>[!tldr] [[NT Skript 2018.pdf#page=196|Skript]]
>Bei Verwendung der gleichen Schaltung wie in Bild 9-1 ist die Rauschleistung die gleiche, aber die mittlere Leistung des empfangenen bipolaren Modulationssignals gm (t) ist mit $P_s=A^2 /R$ gemäß Kapitel 6.3 doppelt so groß wie die des unipolaren Modulationssignals mit $P_s=A^2 /(2×R)$ bei der BASK, d.h. die Bitfehlerwahrscheinlichkeit für BPSK ist für gleiches $E_b/N_0$ geringer als bei der BASK wie [[NT Skript 2018.pdf#page=195|Bild 9-8]] zeigt. Daher wird die BPSK der BASK in der Praxis häufig vorgezogen.

- BPSK immer besser als BASK
	- wegen [[#Harte und Weiche Abtastung|Robustheit]] (euclid distance)

#### 9.1.3 Binary Frequency Shift Keying (BFSK oder 2-FSK)
>[!note]- Orthogonalitätsbedingung
>Der für die Entkopplung nötige Frequenzhub Df = d F/dt = h / (2×T b) muss der folgenden Orthogonalitätsbedingung genügen: [[NT Skript 2018.pdf#page=198|Skript]]
- Schwellwert als Diagonale auf I/Q-Diagramm

>[!important] [[NT Skript 2018.pdf#page=198|Minimum Shift Keying (MSK)]]
>Um eine möglichst hohe spektrale Effizienz (d.h. minimale Frequenzseperation zu erreichen, muss für orthogonale Umtastung der Frequenzhub minimal, d.h. n = 1 oder der Modulationsindex h = 0.5 sein. Eine FSK mit dem so definierten minimalen Frequenzhub $\Delta f=1/(4×T_b)$ wird als Minimum Shift Keying (MSK) bezeichnet.

#### Harte und Weiche Abtastung
[[NT Skript 2018.pdf#page=200|Skript]]
Konstante Einhüllende ermöglicht viel höheren Wirkungsgrad, als lineare, (Siehe Graph $P_{out}$ über $P_{in}$) [[8.2 Intermodulation#A. Intermodulation dritter Ordnung]]
	-> MSK deutlich robuster als BPSK (constant envelope)
>[!attention] TODO
>Hier huebsch machen

