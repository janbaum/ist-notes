## Die Trigonometrische Fourierreihe
>[!important] $x(t) = \frac{a_0}{2}+ \sum^{\infty}_{n=1} a_n cos(ω_0nt) + \sum^{\infty}_{n=1} b_n sin(ω_0nt)$

[[Vorlesung_Fourierreihe_WP2.pdf#page=11|Skript]]
Berechnung der Fourierreihenkoeffizienten:
$$a_n=\frac{2}{T_0}\int^{\frac{T_0}{2}}_{\frac{-T_0}{2}} x(t)cos(\omega_0nt)dt$$
$$b_n=\frac{2}{T_0}\int^{\frac{T_0}{2}}_{\frac{-T_0}{2}} x(t)sin(\omega_0nt)dt$$
##  Fourierreihe komplexer Exponentialfunktionen
>[!important] $x(t) = \sum^{\infty}_{n=-\infty} c_n e^{j\omega_0nt}$

[[Vorlesung_Fourierreihe_WP2.pdf#page=17|Skript]]
Berechnung der Fourierreihenkoeffizienten (mit n $\in$ $\mathbb{N}$):
 $$c_n=\frac{1}{T_0}\int^{\frac{T_0}{2}}_{\frac{-T_0}{2}} x(t)e^{-j\omega_0nt}dt$$
## Fourierkoeffizienten im Frequenzbereich
- Das **Amplitudenspektrum**, $|c_n|$, stellt die Amplitude (bzw. den Betrag) der Fourierkoeffizienten gegen den Frequenzindex n dar.
- Der **Phasengang**, $\arg c_n$, stellt die Phase (das komplexe Argument) der Fourierkoeffizienten gegen den Frequenzindex n dar.
- Bei [[hilfsblaetter.pdf#page=3|reellwertigen Zeitsignalen]] ist das Amplitudenspektrum **gerade** und das Phasenspektrum **ungerade**.
## Zusammenhang zwischen Zeit- und Frequenzbereich 
Hier anhand des [[Vorlesung_Fourierreihe_WP2.pdf|Rechteckimpulses]]
1. Für konstantes $T_0$ nimmt die Breite der Einhüllenden des Amplitudenspektrums (d.h. die Bandbreite) mit abnehmender Pulsbreite $τ$ zu:
	- kleinere Pulsbreite $\tau$ -> höhere Bandbreite
2. Für einen konstanten Wert von $τ$ nimmt der Abstand $ω_0$ zwischen den Spektrallinien gemäß $ω_0 = \frac{2π}{T_0}$ mit steigender Periodendauer $T_0$ von $x(t)$ ab.
## Zusammenhang zwischen trigonometrischer und komplexer Fourierreihe
Das reellwertige Signal $x(t)$ lässt sich also wie folgt mittels seiner komplexen Fourierreihenkoeffizienten ausdrücken:
$$x(t) = c_0 + \sum^{\infty}_{n=1}[2 Re\{c_n\} cos (ω_0nt) − 2 Im\{c_n\} sin (ω_0nt)]$$
Daher gilt folgende Beziehung zwischen den Koeffizienten der komplexen und der trigonometrischen Fourierreihe:[[Vorlesung_Fourierreihe_WP2.pdf#page=27|Skript]]
## Fourierkoeffizienten reellwertiger Funktionen
Weitere Vereinfachungen ergeben sich, wenn $x(t)$ eine **gerade reellwertige Funktion** ist (d.h. wenn $x(t) = x(−t)$):
- In diesem Fall sind auch die Fourierkoeffizienten  **rein reellwertig**:[[Vorlesung_Fourierreihe_WP2.pdf#page=29|Beispiel]]
- Das Integral einer ungeraden Funktion verschwindet über einem um t = 0 symmetrischen Intervall.
- Ebenso ist $c_n$ **rein imaginärwertig** (d.h. $Re\{c_n\} = 0$), wenn $x(t)$ **reellwertig** und **ungerade** ist.