>[!important] $$X(p)= \int^{∞}_{0} x(t)e^{-pt}dt$$
>Rücktransformation:
>$$x(t)= \frac{1}{j2\pi} \int^{\sigma+j\infty}_{\sigma-j\infty} X(p)e^{pt}dp$$
## Allgemein
Mit der Laplace-Transformation erweitern wir die Frequenzbereichsanalyse von Signale und Systemen auf **nicht-transiente** Signale für die die **Fourier-Transformation** prinzipiell nicht existiert, d.h. **nicht konvergiert**. 
- Wir lernen die ein- und die beidseitige Laplace-Transformation kennen, bei der die Fourier-Transformation (mit der zugehörigen Basisfunktion $e^{jωt}$ bei der Frequenz $ω$) um einen exponentiellen Dämpfungsterm $e^{−σt}$ erweitert wird. 
- Abhängig von der Wahl des Dämpfungsfaktors $σ$ konvergiert die Laplace- Transformation. Der Bereich von $p = σ + jω$ für den die Laplace-Transformierte existiert nennt sich Konvergenzbereich. 
- Ähnlich wie bei der Fourier-Transformation leiten wir Korrespondenz- Paare und allgemeine Eigenschaften her, die neben den jeweiligen algebraischen Ausdrücken immer auch den Konvergenzbereich beinhalten.
>[!linfo] Hintergrund
>- Wir haben die Fourier-Transformation als Instrument für die **Analyse von LTI-Systemen** kennengelernt. 
>- Die Fourieranalyse von Systemen mit **periodischen Eingängen** lässt sich nur mithilfe der verallgemeinerten Funktionen (z.B. der Impulsfunktion $δ(t)$) durchführen. 
>- Bei der Analyse von **instabilen Systemen** stößt die Fourieranalyse an ihre Grenzen, da die **Impulsantwort nicht absolut integrierbar** ist. 
>- -> In diesem Fall kann die Frequenzbereichsanalyse mithilfe der **Laplace Transformation** (LT) durchgeführt werden. 
>
>>[!info] Die Laplace-Transformation kann als Verallgemeinerung der Fourier-Transformation aufgefasst werden bei der $jω$ durch $p = σ + jω$ ersetzt wird. 
>>Die Berechnung der Laplace-Transformation ist auch in Fällen möglich, in denen die Fourier-Transformation nicht existiert.
>
>>[!tip] Vorweg-info
>>Wir unterscheiden zwischen beidseitiger- und einseitiger Laplace-Transformation, jedoch wird (nach Herleitung der beidseitigen) die **einseitige Laplace-Transformation** gemeint sein, wann immer generell von Laplace-Transformation gesprochen wird.
>>- [[2) Beidseitige Laplace-Transformation|Beidseitige Laplace-Transformation]]
>>- [[3) Einseitige Laplace-Transformation|Einseitige Laplace-Transformation]]

### Allgemeine Herleitung
Wir betrachten die ansteigende Exponentialfunktion (mit $a>0$):$$x(t)=e^{at}u(t)$$
$x(t)$ ist nicht absolut integrierbar! Die dazugehörige Fouiertransformierte existiert nicht. Die Frequenzbereichsanalyse eines LTI-Systems mit dem Eingang $x(t)$ ist daher nicht ohne Weiteres möglich.

Daher multiplizieren wir $x(t)$ mit $e^{- \sigma t}$, wobei wir annehmen, dass $σ > a$:$$y(t; σ) = e^{−σt}x(t) = e^{−(σ−a)t}u(t)$$
 $\checkmark$    $y(t; σ)$ klingt exponentiell ab und ist absolut integrierbar
$\checkmark$     Die Fouriertransfomierte $Y(ω; σ) = F\{y(t; σ)\}$ existiert
$\checkmark$     Die Frequenzbereichsanalyse kann durchgeführt werden

## Rücktransformation
$$x(t)= \frac{1}{j2\pi} \int^{\sigma+j\infty}_{\sigma-j\infty} X(p)e^{pt}dp$$
,  wobei $σ$ so gewählt wird, dass der Integrationsweg im Konvergenzbereich liegt ($Re\{p\} = σ$).
Die Berechnung der inversen Laplace-Transformation erfordert die **Auswertung eines komplexen Wegintegrales**. 
Für praktische LTI-Systeme ergibt sich eine alternative Berechnungsmethode aus bekannten Korrespondenzen mittels [[#Partialbruchzerlegung]]
$$X(P)=\frac{N(p)}{D(p)}=\frac{b_0+b_1p+...+b_mp^m}{a_0+a_1p+...+a_np^n}$$
- ist $n>m$: echt gebrochen-rationale Funktion
- ist $n<m$: unecht gebrochen-rationale Funktion
liegt eine unecht gebrochen-rationale Funktion vor, muss der Zählergrad durch [[Polynomdivision]] angepasst werden!
### Beispiel: echt gebrochen-rationale Funktion
#### Nullstellen/Polstellen berechnen
$$H(p)= \frac{5p+13}{p²+6p+5}$$
Die Nullstellen des Nenners sind $p_1 = −1$ und $p_2 = −5$. (nutze pq-Formel)
$$H(p)= \frac{5p+13}{(p + 1)(p + 5)}$$
Wir zerlegen $H(p)$ in:
$$\frac{c_1}{p+1}+\frac{c_2}{p+5}$$
Die Koeffizienten $c_1$ und $c_2$ berechnen sich wie folgt -> Wir multiplizieren beide Seiten der Gleichung mit dem Nenner: 
$$5p+13 = \frac{c_1}{p+1}(p+1)(p+5)+\frac{c_2}{p+5}(p+1)(p+5)$$
$$= c_1(p+5)+c_2(p+1)$$
Für $p=-5$ bzw $p=-1$ [[Vorlesung_Laplace_WP4.pdf#page=26|ergeben]] sich $c_2=3$ und $c_1=2$:
$$H(p)=\frac{2}{p+1}+\frac{3}{p+5}$$
$\downarrow$ ^a29a72
#### Partialbruchzerlegung
Aus der [[hilfsblaetter.pdf#page=5|Korrespondenztabelle]] kennen wir das Transformationspaar:
$$\mathcal{L}\{e^{-at}u(t)\}=\frac{1}{p+a}$$
Über die Linearitätsbeziehung der Laplace-Transformation erhalten wir:
>[!example] $$h(t) = (2e^{−t} + 3e^{−5t})u(t)$$

### Beispiel: unecht gebrochen-rationale Funktion
Wir wollen die Impulsantwort h(t) eines LTI-Systems mit der unecht gebrochen-rationalen Übertragungsfunktion berechnen
$$H(p)=\frac{p^4 + 8p^3 + 23p^2 + 34p + 19}{p^3 + 7p^2 + 15p + 9}$$
$\frac{ZÄHLERGRAD}{nennergrad}$ 
$\downarrow$ 
#### Polynomdivision
>[!example]- (schlechtes) Beispiel Polynomdivision
>![[Vorlesung_Laplace_WP4.pdf#page=29]]

TODO: Besseres/Schöneres Beispiel finden, bzw eigenen Mathe Artikel für Polynomdivision schreiben
$$H(p) = p + 1 + \frac{p^2 + 10p + 10}{p^3 + 7p^2 + 15p + 9}=p+1+G(p)$$
#### Partialbruchzerlegung
Zunächst betrachten wir die echt gebrochen rationale Funktion G(p) und führen hierzu ebenfalls eine Partialbruchzerlegung durch. Durch ausprobieren finden wir die Polstelle $p_1 = −1$.
Die übrigen Nullstellen erhalten wir wieder durch [[Vorlesung_Laplace_WP4.pdf#page=31|Polynomdivision]]:
$$G(p) = \frac{p^2 + 10p + 10}{(p + 1)(p^2 + 6p + 9)}= \frac{p^2 + 10p + 10 }{(p + 1)(p + 3)^2}$$
Die Partialbruchzerlegung von G(p) ergibt sich zu:
$$G(p)= \frac{c_1}{p+1}+\frac{c_2}{p+3}+\frac{c_3}{(p+3)^2}$$
Wir bestimmen die Koeffizienten $c_k (k = 1, . . . , 3)$ durch Ausmultiplizieren und Koeffizientenvergleich (wie [[#^a29a72|hier]]):
>[!example]- Ausmultiplizieren und Koeffizientenvergleich
>S. 32 - 34
>![[Vorlesung_Laplace_WP4.pdf#page=32]]

$$g(t) = \left\lparen \frac{1}{4} e^{−t} + \frac{3}{4} e^{−3t} + \frac{11}{2} te^{−3t} \right\rparen u(t)$$
Die Impulsantwort $h(t)$ berechnet sich zu:
$$h(t) = \mathcal{L}^{−1}\{p + 1\} + g(t)$$
>[!example] $$h(t)=\frac{d\delta (t)}{dt}+ \delta(t) + \left\lparen \frac{1}{4} e^{−t} + \frac{3}{4} e^{−3t} + \frac{11}{2} te^{−3t} \right\rparen u(t) $$

Die Korrespondenztabelle der Laplace-Transformation kann genutzt werden um die Inverse der Laplace-Transformation für $p + 1$ zu finden.
