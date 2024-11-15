Die **mittlere Leistung** eines periodischen Signals x(t) mit der Periodendauer $T_0$ und Grundfrequenz $ω_0 = 2π / T_0$ ist:
$$P = \frac{1}{T_0} \int^{\frac{T_0}{2}}_{\frac{-T_0}{2}}|x(t)|^2dt=\frac{1}{T_0} \int^{\frac{T_0}{2}}_{\frac{-T_0}{2}}x(t)x^*(t)dt$$
Unter Verwendung der Fourierreihenentwicklung ergibt sich:
$$P=\sum^{\infty}_{n=-\infty}c^*_nc_n=\sum^{\infty}_{n=-\infty}|c_n|^2$$
>[!important] mittlere Leistung:
>$$P = \frac{1}{T_0} \int^{\frac{T_0}{2}}_{\frac{-T_0}{2}}|x(t)|^2dt=\sum^{\infty}_{n=-\infty}|c_n|^2$$

- Die mittlere Leistung eines periodischen Signals ergibt sich als Summe der Leistungen (Quadrate) seiner Fourierkoeffizienten. 
- Das Parseval Theorem gilt für alle Signaldarstellungen mittels [[1) Fourierreihe#Orthogonale Funktionen#|orthogonaler Basisfunktionen]].