In der 9. Lerneinheit untersuchen wir reale LTI-Systeme, d.h. **RLC-Netzwerke**, im Frequenzbereich. 
- Wir nutzen den Faltungssatz der Fourier-Transformation um die Eingangs- /Ausgang-Beziehung in LTI-Systemen im Frequenzbereich darzustellen. 
- Wir lernen, dass die Übertragungsfunktion $H(jω)$ eines Systems als Fourier-Transformierte der Impulsantwort $h(t)$ durch die ein LTI-System vollständig charakterisiert ist. 
- Aus der Faltung mit der Impulsantwort $h(t)$ im Zeitbereich wird eine einfache Multiplikation mit der Übertragungsfunktion $H(jω)$ im Frequenzbereich. 
- Die Fourier-Transformierte des Ausgangssignals $Y(jω)$ im Frequenzbereich ergibt sich aus dem Produkt der Fourier-Transformierten des Eingangssignals $X(jω)$ und der Übertragungsfunktion $H(jω)$, d.h., $Y(jω) = H(jω) X(jω)$

## Übertragungsfunktion $H(j\omega)$
*Aus den [[2) Eigenschaften der Fourier-Transformation#Faltungstheorem|Faltungstheorem]]:* $$y(t) = x(t) ∗ h(t) \rightarrow Y(jω) = X(jω) · H(jω)$$
>[!linfo] *Da die Fourier-Transformation eine [bijektive](https://de.wikipedia.org/wiki/Bijektive_Funktion#Grafische_Veranschaulichungen) Transformation ist beinhaltet $H(jω)$ dieselbe Information wie die Impulsantwort $h(t)$.*

Dadurch ist die Berechnung der Übertragungsfunktion im Frequenzbereich um ein Vielfaches einfacher, auch für einen Computer.

$H(jω)$ wird **Übertragungsfunktion** des LTI Systems (auch Filters) genannt und entspricht der **Fourier-Transformation** der **Impulsantwort**. 
Da die Fourier-Transformation eine ein-eindeutige Transformation ist, beinhaltet $H(jω)$ dieselbe Information wie die Impulsantwort $h(t)$.
>[!linfo]- Da $H(jω)$ allgemein komplexwertig ist gilt:
>$$H(jω) = |H(jω)| e^{jΘ_H (ω)}$$
>- $|H(jω)|$ ist der Amplitudengang (das Betragsspektrum) des Systems 
>- $Θ_H(ω)$ ist die Phasenantwort (der Phasengang).

>[!linfo]- Falls $h(t)$ reell ist, dann ist:
>$$H(−jω) = H^∗(jω)$$ und 
>$$|H(jω)| = |H(−jω)|$$ 
>$$Θ_H(ω) = −Θ_H(−ω)$$



 [Berechnung der Zeitbereichsantwort über die Frequenzdarstellung](WP3_Lerneinheit10_Kurzzusammenfassung.pdf#page=10)
- Berechnung der Übertragungsfunktion mittels Fouriertransformation der Differentialgleichung und Umstellen nach $H(jω) = X(jω)/Y(jω)$
- [Fouriertransformation](WP3_Lerneinheit10_Kurzzusammenfassung.pdf#page=4) des Eingangssignals: $X(jω) = F{x(t)}$
- Berechnung der Systemantwort im Frequenzbereich: $Y(jω) = H(jω) · X(jω)$
- Rücktransformation in den Zeitbereich mittels Inverser Fouriertransformation: $y(t) = F^{−1} [Y(jω)]$
Anmerkung: Für R-, L-, C-Kreise ergeben sich im Frequenzbereich häufig gebrochenrationale Funktionen. Diese lassen sich mittels Polynomdivision und Partialbruchzerlegung in geeignete Summanden (Partialbrüche) zerlegen, die mittels Korrespondenztabelle (und Eigenschaften) rücktransformiert werden können.