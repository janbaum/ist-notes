Die Grenzwertsätze sind, z.B., in der Regelungstechnik (beim Berechnen des Systemausgangs im eingeschwungenen Zustand ohne Lösen der Systemgleichungen), praktisch relevant.
## Anfangswertsatz
Aus dem Differentiationssatz:
$$\mathcal{L} \{ \frac{dx(t)}{dt}\} = \int^{\infty}_{0}x'(t)e^{-pt}dt= pX(p)-x(0⁻)$$
leitet sich der Anfangswertsatz ab: $$x(o⁻)= \lim_{p \rightarrow 0} pX(p)$$
wenn $x(0⁻)= \lim_{\epsilon \rightarrow 0} x(0- \epsilon)$ existiert, dh. unendlich ist.

## Endwertsatz
Ebenso leitet sich der Endwertsatz ab: $$lim_{t→∞}  x(t) = lim_{p→0}  pX(p)$$
wenn $lim_{t→∞} x(t)$ existiert, d.h. **endlich** ist bzw. **konvergiert**.

## Wichtig ist es jedoch zunächst zu untersuchen, ob die Grenzwerte überhaupt existieren!
Beispiel:
$x(t) = cos(\omega_0 t)$ -> das Signal oszilliert, d.h., es konvergiert für große $t$ nicht.
$$X(p) = L\{x(t)\} = \frac{p}{p^2+ω_0²} = \lim_{p \rightarrow 0} pX(p) = \lim_{p\rightarrow 0} \frac{p²}{p^2+ω_0²} = 0$$
>[!note] Das Problem besteht darin, dass das Signal $x(t)$ keinen Grenzwert besitzt ($\lim_{t→∞} x(t)\not= 0$!!!), da $p = 0$ nicht im Konvergenzbereich liegt.
