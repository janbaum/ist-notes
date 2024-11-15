>[!info] Die einseitige Laplace-Transformation $X(p)$ ^einseitige
>eines Signals $x(t)$ ist als $$\mathcal{L}\{x(t)\}=X(p)= \int^{∞}_{0} x(t)e^{-pt}dt$$
>definiert, wobei $p=\sigma+j\omega$. 
>Vergleiche dazu die [[2) Beidseitige Laplace-Transformation#^beidseitige|beidseitige]]: Integral geht von $-\infty$ bis $\infty$

>[!linfo]- Herleitung
>Die einseitige Laplace-Transformation eines Signals x(t) entspricht der Fourier-Transformierten des als **kausal** und **abklingend** modifizierten Signals:
>$$z(t; σ) = u(t)e^{−σt}x(t)$$
>$$Z(t; σ) = \int^{\infty}_{-\infty} z(t; σ)e^{−jωt} dt$$
>$$= \int^{\infty}_{-\infty} u(t)e^{-\sigma t}e^{−jωt} dt$$
>$$= \int^{\infty}_{0} x(t)e^{-(\sigma +j\omega) t}dt$$

Die einseitige Laplace-Transformation hat starke Ähnlichkeiten zu der [[#Beidseitige Laplace-Transformation|beidseitigen]] Laplace-Transformation. Praktische Signale haben ohnehin einen Startpunkt. 

### Konvergenz der einseitigen Laplace-Transformation
Die einseitige Laplace-Transformation hat ähnliche [[#Konvergenz der beidseitigen Laplace-Transformation|Konvergenzeigenschaften]] wie die beidseitige Laplace-Transformation.

>[!info] Die einseitige Laplace-Transformation konvergiert 
>wenn $Re\{p\} = σ$ die Bedingung: 
>$$\int^{\infty}_{0}|x(t)e^{-\sigma t}dt < \infty|$$
>erfüllt

>[!important] Im Folgenden bezeichnet wir die einseitige Laplace-Transformation kurz als Laplace-Transformation!

... Siehe im Folgenden die [[4) Grenzwertsätze]]
