## LTI-Systeme mit periodischen Eingängen
Wir betrachten ein LTI-System mit Impulsantwort $h(t)$ und Eingangssignal $x(t)$
$$y(t)=\int^{\infty}_{-\infty}h(\tau)x(t-\tau)d\tau$$
Für $x(t)=e^{j\omega_0t}$ bedeutet das:
$$y(t)=\int^{\infty}_{-\infty}h(\tau)e^{j\omega_0(t-\tau)}d\tau=e^{j\omega_0t}\int^{\infty}_{-\infty}h(\tau)e^{-j\omega_0\tau}$$
wobei das Integral $H(j\omega_0)$ ist: 
$$y(t)=H(j\omega_0)e^{j\omega_0t}$$
	$H(jω_0)$ ist eine allgemein komplexwertige Konstante (später definieren wir $H(jω)$ als die Übertragungsfunktion (Frequenzantwort) des Systems an der Frequenz $ω$).
### Übertragungsfunktion 
$$H(j\omega)=\int^{\infty]}_{-\infty}h(t)e^{-j\omega t}dt$$
Nach Betrag und Phase aufgespalten:
#### Amplitudenantwort
- $|H(J\omega_0)|$ ist die Amplitudenantwort des Systems zur Kreisfrequenz $ω_0$
#### Phasenantwort
- $\Theta_H(\omega_0)$ ist die Phasenantwort des Systems zur Kreisfrequenz $ω_0$
#### Systemantwort
an der Frequenz $\omega_0$: [[Vorlesung_Fourierreihe_WP2.pdf#page=53|Skript]]

#### Eigenfunktion
- Die komplexe Harmonische $e^{jω_0t}$ stellt eine Eigenfunktion eines LTI- Systems dar.
- Das System wirkt sich auf die Eigenfunktion lediglich in Form einer **komplexen Skalierung** der Eigenfunktion mit $H(jω_0)$ aus.
- Die Signalform des Eingangssignals $x(t)$ wird jedoch ansonsten nicht beeinflusst (verzerrt).
[[Vorlesung_Fourierreihe_WP2.pdf#page=54|Skript]]
- Die Übertragungsfunktion $H(jω)$ an der Frequenz $ω_0$ kann als Eigen- wert des Systems für die Eigenfunktion $e^{jω_0t}$ aufgefasst werden. 
	- Der Eigenwert charakterisiert eindeutig die Antwort eines LTI-Systems auf eine komplexe Harmonische $e^{jω_0t}$.
[[Vorlesung_Fourierreihe_WP2.pdf#page=56|Beispiel]]

### Systemantwort
Die Systemantwort $y(t)$ eines LTI-Systems auf den periodischen Eingang $x(t)$ lässt sich aus der Fourierreihenentwicklung [[Vorlesung_Fourierreihe_WP2.pdf#page=57|einfach bestimmen]].
