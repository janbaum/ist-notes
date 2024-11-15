[[06-PCM.pdf|Folien]]
- [[06-PCM.pdf#page=3|Prinzip eines PCM Senders]]
	- Datenrate: $R_b = 1/T_b = n*2f_m$
	- Bandbreite: $B_{min} = 1/(2T_b) = n*f_m$
		- $\rightarrow$ hohe Datenrate = hohe Bandbreite (mehrwertige Signale)
	- erforderliche Bandbreite zur Übertragung ausführlich in Kapitel 1 hergeleitet

- [[06-PCM.pdf#page=8|gleichmäßige Quantisierung]]

- Modulations codes
	- **Unipolarer/Bipolarer NRZ-Code**
	- **Unipolarer/Bipolarer RZ-Code**
	- HDB-3-code
	- Manchester-Code
Für Vorlesung nur Bezug auf ersten beiden, weil Geräte-intern überwiegend diese beiden benutzt werden. 
Physikalische Eigenschaften damit auch abgedeckt, die Unterschiede zu unteren Beiden sind physikalisch betrachten eher kleine. 
Oft ist es in der Praxis ein Trade-Off zwischen Bandbreite und Taktgenerierung.

### 6.2.1 Erforderliche Bandbreite zur Übertragung von NRZ-Signalen
TO DO

### 6.2.2 Verfahren zur Analog/Digital-Wandlung
_1. Zählverfahren_
_2. Iterationsverfahren_
*3. [[06-PCM.pdf#page=13|Direktverfahren (Parallelcodierer)]]*
- Sampler/Abtaster
- Quantisierer (Komparatorschaltung)
	- [[06-PCM.pdf#page=14|Komparatoren]] fragen nach aktuellen Werten grösser/kleiner als Wert $x_i$ dem entsprechen werden Werte gesendet
- [[06-PCM.pdf#page=15|Encoder]]
	- Spannungen aus Komparatoren in logischer Schaltung verknüpfen
	- [[06-PCM.pdf#page=16|Generierung von Bits]] als Codewort
		- NRZ (Non-Return to Zero):  Signalzustand bleibt über die Dauer eines Bits erhalten und geht zwischendurch nicht auf Null
- [[06-PCM.pdf#page=17|Parallel to Serial Converter]]
	- Bits, die noch parallel sind, seriell ausgeben -> **PCM Signal**
	- Zum Erkennen des Codewortanfangs wird in bestimmten Abständen ein Synchronwort mit übertragen
	- Anzahl der Quantisierungsintervalle: $N=2^n$ ^d88284
		- Anzahl der Bits pro Codewort: $n$
- Bitrate(oder auch Baudrate): $R_b=n*f_p [bits/s]$, mit:
	- Bitdauer $T_b$, Abtastintervall $T_p=n*T_b$
	- Hierbei ist $f_p=2*f_m$ die Abtastrate ($f_m$=maximale Frequenz des Nachrichtensignals)

### 6.2.3 Quantisierungsfehler und Quantisierungsrauschleistung
- [[06-PCM.pdf#page=20|Fehler zwischen tatsächlichem Wert und quantisiertem Wert]]: $\varepsilon$
	- $\varepsilon_q(i*T)= s_m(i*T_p) - s_q(i*T_p)$
		- $s_m(i*T_p)$: Wahrer Wert an der Stelle $i$
		- $s_q(i*T_p)$: Quantisierungswert an der Stelle $i$
- Wahrscheinlichkeitsdichtefunktion für das PCM-Fehlersignal:
	- $P_q = \frac{1}{R}*\int^\infty_{-\infty} p(\varepsilon_q)*\varepsilon^2_q*d\varepsilon_q$
- Signal zu Rauschquantisierungsverhältnis: 
	- Wird [[06-PCM.pdf#page=23|pro zunehmender Bit-Darstellung]] ([[#^d88284|Codewortlänge]]) um 6 dB besser
- Grey-Code: Der Gray-Code hat den Vorteil, dass sich die Codewörter benachbarter Quantisierungspegel jeweils nur in einem Bit unterscheiden. So verursachen Ein-Bit-Fehler im empfangenen Codewort minimale Fehler im zurückgewonnenen analogen Signalwert, vorausgesetzt, dass das Vorzeichen-Bit fehlerfrei ist.([[NT Skript 2018.pdf#page=104|Skript]])
- Dynamik: $D\approx6*n [dB]$ 
	_Herleitung aus $20\log((x_{max}-x_{min})/\Delta s)=20\log(2^n)$_

### 6.3 Nichtlineare Quantisierung
- gewünscht, um konstantes $SNR_q$ zu erreichen. 
	- **Warum?** Wenn in nur einem kleinen Bereich eine hohe Auflösung  gebraucht wird und in anderen Bereichen gröbere Auflösung sinnvoll
#### Formel für $SNR_Q$
$$SNR_q=1.8+6*n$  $[dB]$,  mit:  $n=\#Bits$$
- _Herleitung aus:_ 
$$SNR_q=10\log(P_S/P_Q)=10\log(6\hat{U}_0^2/\Delta s^2)$$
	 _mit:_ $P_S=\hat{U}_0^2/2R$ & $P_Q=\Delta s^2/12R$

### 6.4 PCM Übertragungssystem
[[NT Skript 2018.pdf#page=118|Skript]]
#### 6.4.1 Bitfehlerwahrscheinlichkeit
[[NT Skript 2018.pdf#page=119|Skript]]
1.  Mittlere Energie pro Bit der NRZ-Signale
2. Varianz des Empfängerrauschens
3. Bitfehlerwahrscheinlichkeit der NRZ-Signale für weißes gaußförmiges Rauschen
	- BER: Bit Error rate
#### 6.4.2 Fehlerwahrscheinlichkeit des PCM-Codewortes
[[NT Skript 2018.pdf#page=124|Skript]]

### 6.5 Zeitmultiplex
[[NT Skript 2018.pdf#page=124|Skript]]
#### 6.5.1 Getrennte Codierung
 - Vorteil: Kommt mit langsamerer Taktrate zurecht
 - Nachteil: Viele AD-Wandler haben hohen Leistungsverbrauch (~10 W)
#### 6.4.2 Zentrale Codierung
- Vorteil: Braucht weniger AD-Wandler 
- Nachteil: Braucht hohe Taktrate/Abtastrate
 [[06-PCM.pdf#page=54|Beispiel bis S. 57]]
 


## Fragen?
- Folie 7
	- x- / y-Achsen bei Quantisierung? In Beispiel 7 V von wo?
	- Was ist die Dynamik? 
	- -> Folie 8 erklärt Nutzung von Graphen
- Folie 14
	- minimale Bandbreite aus Grundwelle hergeleitet, wie?
		- evtl bei WP2-Fourier-Koeffizienten aus DSS nochmal nachschauen -> **bisher auch noch nicht dokumentiert!**
- [[#6.3 Nichtlineare Quantisierung]] Warum gewünscht?
- 