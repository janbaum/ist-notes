Für $−\infty < t < \infty$:
$$y(t) = T [x(t)] = x(t) ∗ h(t) = \int^{\infty}_{-\infty} x(\tau)h(t − \tau )d\tau$$
### Berechnung des Faltungsintegrals 
Für Signale und Impulsantworten die abschnittsweise definiert sind (z.B., stückweise konstante oder stückweise lineare Funktionen) berechnet sich die Faltung durch folgende Schritte: 
1. Den Integrationsbereich in geeignete Teilstücke segmentieren. 
2. **Die Teilstücke $[t_{i−1}, t_i]$ so wählen, dass das Produkt $x(τ )h(t − τ )$ über dem jeweiligen Intervall dieselbe analytische Form als Funktion von $τ$ besitzt.
3. Die folgenden Schritte für alle Teilintervalle ausführen.

#### Schritt 1
- $x(\tau)$, 
- $h(t-\tau)$, 
- $x(\tau)h(t-\tau)$ 
als Funktionen von $\tau$ bestimmen (auch skizzieren). Hierbei ist $h(t-\tau)$ die am Ursprung $\tau=0$ gespiegelte und um $t$ verschobene Version von $h(-\tau)$

#### Schritt 2
- Das Produkt $x(\tau) h(\tau)$ bezüglich $\tau$ aufintegrieren
- Der Integrand hängt von $t$ und $τ$ ab.
- Die Integrationsvariable $τ$ verschwindet nach der Integration (Integralgrenzen einsetzen).
- Das Integral entspricht der Fläche unter der Produktfunktion $x(τ )h(t − τ )$
>[!example]- Beispiel aus WS14/15
>![[Vorlesung_Signale und Systeme_WP1.pdf#page=88]]
Kommutativität 
### Eigenschaften des Faltungsintegrals
- [[Vorlesung_Signale und Systeme_WP1.pdf#page=92|Kommutativität]]
- [[Vorlesung_Signale und Systeme_WP1.pdf#page=93|Distributivität]]
- [[Vorlesung_Signale und Systeme_WP1.pdf#page=94|Assoziativität]]
- [[Vorlesung_Signale und Systeme_WP1.pdf#page=98|Differenzierbarkeit]]
>[!example]- Beispiel "matched filter"
>![[Vorlesung_Signale und Systeme_WP1.pdf#page=96]]

#### Faltung mit Dirac-Funktion
Die Faltung einer Funktion mit einem Dirac ergibt die selbe Funktion, jeweils um die Zeitverschiebung und Gewichtung des Diracs.
>[!example] Beispiel Faltung mit Dirac
>$$y(t)=\alpha \cdot \delta(t-T)*h(t)=\alpha \cdot h(t-T)$$

