>[!linfo]- Über die Eigenschaften
>- Die allgemeinen Eigenschaften der Fourier-Transformation sind für das Verständnis von Signalen und Systemen in praktischen Anwendungen fundamental wichtig. 
>- Die allgemeinen Eigenschaften ermöglichen uns in vielen Fällen eine **einfache Berechnung der Fourier-Tranformierten** durchzuführen, ohne jeweils das Transformationsintegral auswerten zu müssen. 
>- Voraussetzung ist, dass ein **geeignetes Transformationspaar** gegeben ist (z.B. in der Korrespondenztabelle) und dazu eine entsprechend geeignete Operation, sodass sich das Fourier-Transformierte des gesuchten Signals damit darstellen lässt.

>[!summary] Inhaltsangabe:
>- [[Vorlesung_Fouriertransformation_WP3.pdf#page=41|Linearität]]
>- [Zeitverschiebung](WP3_Lerneinheit8_Kurzzusammenfassung.pdf#page=6) 
>- [Zeitskalierung](WP3_Lerneinheit8_Kurzzusammenfassung.pdf#page=7)
>- [Zeitspiegelung](WP3_Lerneinheit8_Kurzzusammenfassung.pdf#page=8)
>- [Dualitätsbeziehung (Symmetriebeziehung)](WP3_Lerneinheit8_Kurzzusammenfassung.pdf#page=9)
>- [Frequenzversatz](WP3_Lerneinheit9_Kurzzusammenfassung.pdf#page=6)
>- [Differentiation nach der Zeit](WP3_Lerneinheit9_Kurzzusammenfassung.pdf#page=7)
>- [[Vorlesung_Fouriertransformation_WP3.pdf#page=75|Multiplikation im Zeitbereich]]
>- [[Vorlesung_Fouriertransformation_WP3.pdf#page=76|Integration]]
>- [[Vorlesung_Fouriertransformation_WP3.pdf#page=81|Grenzverhalten]]
>- [[Vorlesung_Fouriertransformation_WP3.pdf#page=82|Konjugiert komplexes/reelles Zeitsignal]]
>- [[Vorlesung_Fouriertransformation_WP3.pdf#page=83|gerade Zeitfunktion]]

## Auszug aus der Korrespondenztabelle
![[Vorlesung_Fouriertransformation_WP3.pdf#page=86]]

## Linearität
$a*x_1(t) + b*x_2(t) = a*X_1(j\omega) + b*X_2(j\omega)$

## Zeitverschiebung
$x(t-t_0) \rightarrow X(j\omega)e^{-j \omega t_0}$
![[wp3_zeitverschiebung.png]]
>[!example]- Zeitverschiebung der Impulsfunktion
>![[Vorlesung_Fouriertransformation_WP3.pdf#page=45]]

>[!example]- Pfadverzögerung im OFDM System
>![[Vorlesung_Fouriertransformation_WP3.pdf#page=46]]

## Zeitskalierung
$$x(at) \rightarrow \frac{1}{|a|}X(\frac{j\omega}{a})$$
![[wp3_zeitskalierung.png]]

## Zeitspiegelung
$$x(-t) \rightarrow X(-j\omega)$$
falls $x(t)$ reell: $\rightarrow X^*(j\omega)$
![[wp3_zeitspiegelung.png]]
## Dualitätsbeziehung (Symmetriebeziehung)
$X(jt) \rightarrow 2 \pi x(-\omega)$
Mithilfe der Dualitätseigenschaft lässt sich z.B. die Fourier-Transformierte für solche Signale (bzw. Zeitbereichsfunktionen) berechnen, für die in der Korrespondenztabelle lediglich ein entsprechendes Signal als Frequenzbereichsfunktion gegeben ist.
>[!example]- Beispiele
>![[Vorlesung_Fouriertransformation_WP3.pdf#page=56]]

## Frequenzversatz
$$x(t)e^{j\omega_0t} \rightarrow X(j(\omega-\omega_0)$$
Frequenzversatz Für eine Frequenzverschiebung der FT $X(jω)$ um $ω_0$ gilt die folgende Eigenschaft, $x(t)e^{jω_0t} \rightarrow X (j(ω − ω0))$ wobei $ω_0$ eine reelle Konstante darstellt. Die Multiplikation des Signals $x(t)$ mit der komplexen Harmonischen $e^{jω_0t}$ wird als Modulation im Zeitbereich bezeichnet.
![[wp3_frequenzversatz.png]]
>[!example]- Beispiel Modulation
>![[Vorlesung_Fouriertransformation_WP3.pdf#page=62]] 

>[!example]- Sinus der Grundfrequenz $ω_0$
>![[Vorlesung_Fouriertransformation_WP3.pdf#page=63]] 

## Differentiation nach der Zeit
$n$-te Ableitung des Signals $x(t)$ nach der Zeit: $$x^{(n)}(t) = \frac{d{^n(x)t}}{dt^n} \rightarrow (j \omega)X(j \omega)$$ 
Der Differentiationssatz der Fourier-Transformation spielt bei der Analyse von realen Systemen, d.h. RLC-Netzwerken, eine große Rolle, da sich in diesen Systemen die Eingang-/Ausgangsbeziehung implizit über lineare Differentialgleichungen beschreiben lässt. Wir werden diese Differentialgleichungen im [[Frequenzbereich]] untersuchen.

## Faltungstheorem
$$x_1(t)*x_2(t) \rightarrow X_1(j\omega)·X_2(j\omega)$$
Das Faltungstheorem der Fourier-Transformation ist eines der wichtigsten Eigenschaften für LTI-Systeme. Es ermöglicht eine vereinfachte Berechnung der [[Systemantwort]] aus dem Eingangssignal $x(t)$ und der Impulsantwort $h(t)$ des Systems im Frequenzbereich. -> [[Fast Fourier Transformation]]
>[!example]- Beispiele
>![[Vorlesung_Fouriertransformation_WP3.pdf#page=71]]

## Multiplikation im Zeitbereich
$$x1(t) · x2(t)\rightarrow \frac{1}{2\pi} X_1(j\omega)*X_2(j\omega)=\frac{1}{2\pi}\int^{\infty}_{-\infty}X_1(j\lambda)X_2(j(\omega-\lambda))d\lambda$$
[[Vorlesung_Fouriertransformation_WP3.pdf#page=75|Herleitung]] aus der [[#Dualitätsbeziehung (Symmetriebeziehung)]] und dem [[#Faltungstheorem]]

## Integration
$$\int^{t}_{-\infty}x(\tau)d\tau \rightarrow \frac{X(j\omega)}{j\omega}+\pi X(0)\delta (\omega)$$

- ##### [Eingangs- und Ausgangsbeziehung eines LTI-Systems im Frequenzbereich]((WP3_Lerneinheit9_Kurzzusammenfassung.pdf#page=8)
$x(t) ∗ h(t) \rightarrow X(jω) · H(jω)$

## Grenzverhalten
$$\lim_{\omega \rightarrow \infty} X(j\omega) = \lim_{\omega \rightarrow \infty} X(-j\omega) = 0$$


## Konjugiert komplexes Zeitsignal, reelles Zeitsignal
$$x^*(t) \rightarrow X^*(-j\omega)$$

## gerade/ungerade Zeitfunktionen
### gerade
$$x(t)=x(-t)=X(j\omega)=X(j\omega)$$
### ungerade
$$x(t)=\frac{2}{\pi} \int^{\infty}_{0} X(j\omega)cos(\omega t)dt$$

$$x(t)=\frac{2}{\pi}$$
