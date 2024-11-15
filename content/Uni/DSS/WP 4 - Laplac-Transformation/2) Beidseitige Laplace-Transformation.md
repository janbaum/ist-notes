
Die beidseitige Laplace-Transformation ist als Fourier-Transformation darstellbar, wenn $y(t; σ) = x(t)e^{−σt}$ gewählt wird und $Y(ω; σ) = F\{y(t; σ)\}$ gilt.
$$ Y(ω; σ) = \int^{∞}_{−∞} y(t; σ)e^{−jωt} dt = \int^{∞}_{−∞} x(t)e^{-pt}dt\left.\right\rvert_{p=\sigma+j\omega} = X(p)$$
>[!info] Die beidseitige Laplace-Transformation $X(p)$ ^beidseitige
>eines Signals $x(t)$ ist als $$X(p)= \int^{∞}_{−∞} x(t)e^{-pt}dt$$
>definiert, wobei $p=\sigma+j\omega$
>Vergleiche dazu die [[3) Einseitige Laplace-Transformation#^einseitige|einseitige]]: Integral geht von $0$ bis $\infty$



Die beidseitige Laplace-Transformierte $X(p)|_{p=σ+jω}$ des Signals $x(t)$ entspricht der Fourier-Transformierten des Signals $x(t)e^{−σt}$:

$X(p)|_{p=σ+jω}$   $\hat{=}$   $x(t)e^{−σt}$

Andererseits erhält man das Signal $X(ω)$ aus der Laplace-Transformation für $Re\{p\} = σ = 0$.

## Konvergenz  der beidseitigen Laplace-Transformation
Aus den [[1) Fourier-Transformation#Konvergenz der Fourier-Transformation|Konvergenzbedingungen der Fourier-Transformation]] ergibt sich für die beidseitige Laplace-Transformation: $$\int^{\infty}_{-\infty}|x(t)|e^{-\sigma t}dt < \infty$$, für ein beliebiges, endliches $\sigma$.

>[!info] Die beidseitige Laplace-Transformierte konvergiert somit lediglich für bestimmte Werte von $σ = Re\{p\}$. 
Der Bereich der Werte in der komplexen Ebene, für die $X(p)$ konvergiert, wird [[Konvergenzbereich]] (KB) genannt.
Für das obige Beispiel zeigt sich, dass die beidseitige Laplace-Transformation $X(p)$ des Signals $x(t) = e^{−at}u(t)$ konvergiert für $Re\{p\} = σ > −a$:
>>[!example]- Skript
>>S. 8-10
>>![[Vorlesung_Laplace_WP4.pdf#page=8]]
>
>- Für $a > 0$ ist $x(t) = e^{−at}u(t)$ exponentiell abfallend und **absolut integrierbar**. 
>	- Der Konvergenzbereich der beidseitigen Laplace-Transformation beinhaltet daher Werte von $p$ mit $σ = 0$.
>- Für $a < 0$ ist $x(t) = e^{−at}u(t)$ nicht absolut integrierbar 
>	- Der Konvergenz-Bereich beinhaltet **keine** Werte von $p$ mit $σ = 0$. 
>	- Die Fourier-Transformation von $x(t)$ existiert für $a < 0$ **nicht**. 
>	- Die beidseitige Laplace-Transformation für $σ > −a$ **existiert**.
beidseitige
>[!info] Merke
>- Die beidseitige Laplace-Transformation ist eindeutig durch den algebraischen Ausdruck und den zugehörigen Konvergenzbereich definiert. 
>- **Zwei Signale können zwar dieselbe Laplace-Transformierte haben, jedoch unterschiedliche Konvergenzbereiche besitzen.**
>>[!important] Bei der Berechnung der inversen beidseitigen Laplace-Transformation ist es daher notwendig den Konvergenzbereich **genau zu berücksichtigen**.

>[!example]- Beispiel Identischer Algebraischer Ausdruck
>![[Vorlesung_Laplace_WP4.pdf#page=13]]
