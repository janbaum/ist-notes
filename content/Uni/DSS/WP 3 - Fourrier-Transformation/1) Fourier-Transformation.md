>[!summary] Inhaltsangabe
>- [[1) Fourier-Transformation|Allgemein]]
>- [[#Transformation in Frequenzbereich]]
>- [[#Rücktransformation in Zeitbereich]]
>- [[#Konvergenz der Fourier-Transformation]]
>- [[#Energiedichtefunktion und Parseval’s Theorem]]
>- [[2) Eigenschaften der Fourier-Transformation|Eigenschaften der Fourier-Transformation]]
>- [[4) Reale und ideale Filter|Reale und ideale Filter]]

Mit der Fourier-Transformation erweitern wir die Freqenzbereichsdarstellung von periodischen Signalen auf **<u>nicht-periodische Signale</u>**. 
- Wir erreichen diese Erweiterung indem wir die <u>Periodendauer sukzessive vergrößern</u> und ins „Unendliche“ laufen lassen. 
- Wir stellen fest, dass:
	- benachbarte Frequenzlinien immer näher aneinander rücken
	- Summation -> Integral 
	- Linienspektrum -> kontinuierliche Funktion
- Die Fourier-Transformierte $X(jω)$ an der Frequenz $ω$ ist ein Korrelations-Maß dafür, wie ähnlich das Zeitsignal x(t) mit der orthogonalen Basisfunktion $e^{jωt}$ an der Frequenz $ω$ ist. 
- Das Betragsspektrum $|X(jω)|$ gibt an mit welcher Intensität die Frequenz $ω$ im Signal x(t) enthalten ist. 
- Der Phasengang arg $X(j(ω)$ gibt die relative Phasenlage des Signals $x(t)$ im Bezug auf die Basisfunktion $e^{jωt}$ an.


>[!note]- Fourierreihenentwicklung für periodische Signale
>$$x(t)=\sum^{\infty}_{n=-\infty}X_n e^{j\omega_0nt}$$ 
mit $$X_n=\frac{1}{T_0} \int^{\frac{T_0}{2}}_{\frac{-T_0}{2}}x(t) e^{-j\omega_0nt}dt$$

Praktische Signale sind jedoch meist nichtperiodisch:
- Für Periodendauer $T_0 → ∞$ erweitert sich die exponentielle Fourierreihenentwicklung auf nichtperiodische Signale. 
- Der Abstand der Frequenzlinien im Linienspektrum, d.h. $ω_0 = 2π/T_0$ läuft gegen infinitesimal kleine Werte $dω$ und die Folge $nω_0$ diskreter Vielfacher der Grundfrequenz $ω_0 = 2π/T_0$ nähert sich dem kontinuierlichen Parameter $ω$ an. 
- <font color="#c0504d">Die Fourier-Transformation ergibt sich, indem man in der Fourierreihenentwicklung die diskrete Summe durch ein Integral ersetzt.</font> 
- Das Betragsspektrum (Amplitudenspektrum) der Fourier-Transformierten bildet dann quasi die Einhüllende des Betragspektrums (Linienspektrums) der Fourierreihenentwicklung.


## Transformation in Frequenzbereich
>[!important] $X(jω) = F${$x(t)$} =$$ \int_{−∞}^{∞} x(t)e^{−jωt}dt$$

## Rücktransformation in Zeitbereich
>[!important] $x(t) = F^{-1}${$x(t)$} =$$ \frac{1}{2*\pi} \int_{−∞}^{∞} x(t)e^{−jωt}dt$$ 

## Konvergenz der Fourier-Transformation
- Die Fourierreihenentwicklung eines periodischen Signals konvergiert nicht überall gleichmäßig bzw. punktweise. 
- Erfüllt das Signal die [[3) Konvergenz der Fourierreihe#Dirichlet Bedingungen|Dirichlet Bedingungen]], ist die Konvergenz der Reihe garantiert. 
	- Die [[3) Konvergenz der Fourierreihe#Dirichlet Bedingungen|Dirichlet Bedingungen]] sind hinreichend, **nicht notwendig** für die Konvergenz der Fourier-Transformation.
	1. Wenn die [[Vorlesung_Fouriertransformation_WP3.pdf#page=19|Bedingung der absoluten Integrierbarkeit]] erfüllt ist, dann ist die Fourier-Transformierte $X(jω)$ begrenzt, d.h., die Fourier-Transformation lässt sich berechnen und sie nimmt an allen Frequenzen ω endliche Werte an.
	2. Das Signal $x(t)$ erfüllt bestimmte Regularitätsbedingungen: 
		1. $x(t)$ stückweise stetig 
		2. die Anzahl aller Sprungstellen, Unstetigkeiten, Maxima und Minima von $x(t)$ ist endlich.
- Entsprechend gilt auch für Fourier-Transformation, dass diese nicht notwendigerweise für alle Signale konvergiert:
	- Die Dirichlet Bedingungen schließen per se die wichtige Klasse der sinusförmigen Signale bzw. der komplexen Exponentialfunktionen aus, da diese nicht absolut integrierbar sind.
	-> Die Fourier-Transformierten dieser Signale lassen sich jedoch mithilfe der verallgemeinerten Funktionen (z.B. der Impulsfunktion) darstellen. **Dafür erweitern wir die Definition der Fourier-Transformation um die Fourier-Transformation im Grenzbereich**:

### Fourier-Transformation im Grenzbereich
>[!example]- Am [[Vorlesung_Fouriertransformation_WP3.pdf#page=22|Beispiel]] der konstanten Funktion $x(t)= A$
>![[Vorlesung_Fouriertransformation_WP3.pdf#page=22]]

>[!example]- Am [[Vorlesung_Fouriertransformation_WP3.pdf#page=22|Beispiel]] der komplexen Exponentialfunktion 
>![[Vorlesung_Fouriertransformation_WP3.pdf#page=26]]

>[!example]- Am [[Vorlesung_Fouriertransformation_WP3.pdf#page=22|Beispiel]] der trigonometrischen Funktion 
>![[Vorlesung_Fouriertransformation_WP3.pdf#page=27]]

>[!example]- Am [[Vorlesung_Fouriertransformation_WP3.pdf#page=22|Beispiel]] der beidseitig gedämpften Exponentialfunktion 
>![[Vorlesung_Fouriertransformation_WP3.pdf#page=28]]

>[!example]- Am [[Vorlesung_Fouriertransformation_WP3.pdf#page=22|Beispiel]] der Signum Funktion 
>![[Vorlesung_Fouriertransformation_WP3.pdf#page=30]]

>[!linfo]- Zugehöriger Ausuzug aus der Korrespondenztabelle
>![[Vorlesung_Fouriertransformation_WP3.pdf#page=31]]

## Energiedichtefunktion und [[4) Parseval’s Theorem|Parsevals Theorem]]
>[!important] $$E=\frac{1}{2\pi}\int^{\infty}_{-\infty}X(j\omega)X^*(j\omega)d\omega=\frac{1}{2\pi}\int^{\infty}_{-\infty}|X(j\omega)|²$$

>[!important] $$E=\int^{\infty}_{-\infty}|x(t)|²dt=\frac{1}{2\pi}\int^{\infty}_{-\infty}|X(j\omega)|²d\omega$$
- Das Betragssignal $|X(jω)|^2$ ist die spektrale Energiedichtefunktion von $x(t)$. 
- Die **Integration** der spektralen Energiedichtefunktion über den gesamten Frequenzbereich ergibt die **Gesamtenergie**. 
- Die Signalenergie in einem **begrenzten Frequenzband**, z.B. $ω ∈ [ω1, ω2]$, berechnet sich durch Integration der Spektralen Energiedichtefunktion über das Intervall $[ω1, ω2]$. 
- Das Betragsignal $|x(t)|^2$ hingegen wird als **Momentanleistung** bezeichnet.
>[!example]- In [[Vorlesung_Fouriertransformation_WP3.pdf#page=36|diesem]] Fall ist es einfacher die Signalenergie im Zeitbereich zu berechnen.
>![[Vorlesung_Fouriertransformation_WP3.pdf#page=36]]

