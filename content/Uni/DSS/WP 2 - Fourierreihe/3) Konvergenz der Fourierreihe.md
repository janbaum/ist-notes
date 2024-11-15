## Lernziele in [[Vorlesung_Fourierreihe_WP2.pdf#page=31|Skript]]:
In der fünften Lerneinheit beantworten wir die wichtige Frage, unter welchen Bedingungen sich Signale **exakt** als Fourierreihe entwickeln lassen. 
- Das führt uns auf die unterschiedlich starken Konvergenzbegriffe, d.h. der [[#Gleichmäßige Konvergenz|gleichmäßigen]] und der [[#Punktweise Konvergenz|punktweisen]] Konvergenz, 
- und die [[#Dirichlet Bedingungen]] die hinreichend (aber nicht notwendig) für die Konvergenz der Fourierreihe sind. 
- Wir lernen, dass die Fourierreihe eines „hinreichend glatten“ Signals $x(t)$ überall dort wo das Signal **stetig** ist **gleichmäßig** gegen $x(t)$ konvergiert und an den **Sprungstellen** **punktweise** gegen den Mittelwert des links- und rechtsseitigen Grenzwerts konvergiert.

Die Fourierreihenentwicklung, d.h. die unendliche Summe [[2) Fourierreihenentwicklung#Die Trigonometrische Fourierreihe|unendliche Summe]] konvergiert nicht notwendigerweise gegen $x(t)$. 
D.h., die Fourierreihe **existiert nicht für alle periodischen Signale.** Die im Folgenden beschriebenen [[Konvergenzbedingungen]] müssen erfüllt sein.

## Endliche Fourierreihe
[[Vorlesung_Fourierreihe_WP2.pdf#page=33|Skript]]
Da die Reihenentwicklung bei endlichem $N$ abgebrochen wird, stellt $x_N (t)$ in der Regel nur eine Approximation des Signals $x(t)$ dar.

## Konvergenzkriterien der Fourierreihe (Definition)
Zwei verschiedene Konvergenzarten von Funktionsfolgen:
$$x_N (t) = \frac{a_0}{2} + \sum^{N}_{n=1} a_n cos(ω_0nt)+ \sum^{N}_{n=1} b_n sin(ω_0nt)$$
[[Vorlesung_Fourierreihe_WP2.pdf#page=35|zugehörige]] Animation auf [Moodle](https://moodle.tu-darmstadt.de/mod/lti/view.php?id=1274394) at $01h : 24min$
oder hier als Video: [[gibbs'sches_phanomen-2024-07-20_13.49.25|Gibbs'sches Phänomen]]

### Punktweise Konvergenz ([[Punktweise Konvergenz|einfachere Definition]])
Die Funktionsfolge $x_N (t)$ konvergiert an der Stelle $t ∈ D$ punktweise gegen $x(t$), wenn für jedes $ϵ_t > 0$ ein $N_0$ existiert, so dass für alle $N ≥ N_0:$ $$|x_N (t) − x(t)| ≤ ϵ_t$$
### Gleichmäßige Konvergenz ([[Gleichmäßige Konvergenz|einfachere Definition]])
Die Funktionsfolge $x_N (t)$ konvergiert über einem Definitionsbereich $D$ gleichmäßig gegen $x(t$), wenn für jedes $ϵ > 0$ ein $N_0$ existiert, so dass für alle für alle $t$ in $D$ und $N ≥ N_0$: $$|x_N (t) − x(t)| ≤ ϵ$$
- Es sei $x(t)$ eine auf dem Interval $[a, b]$ **stetig und stückweise stetig differenzierbare Funktion**, dann konvergiert die Fourierreihe auf $(a, b)$ gleichmäßig gegen $x(t)$. 
- Gleichmäßige Konvergenz **gilt nicht an Sprungstellen**. 
- Gibbs’schen Phänomen: Das Gibbs’sche Phänomen beschreibt die Eigenschaft der Fourierreihe an Sprungstellen um ca. 9% überzuschwingen. ^gibbs
- An Sprungstellen gilt lediglich die **punktweise** Konvergenz aber keine gleichmäßige Konvergenz (bei geeigneter Definition der Funktionswerte an den Sprungstellen).

## Dirichlet Bedingungen
Wenn das mit $T_0$ periodische Signal $x(t)$
1. über einer Periode $T_0$ <u>absolut integrierbar</u> ist
2. innerhalb einer Periode eine <u>endliche Anzahl von Maxima und Minima</u> besitzt
3. und eine <u>endliche Anzahl von Sprungstellen</u> aufweist,
dann konvergiert die Fourierreihe:
### gleichmäßig
- überall dort wo $x(t)$ stetig und stetig differenzierbar ist, gegen $x(t)$.
### punktweise
- an den Sprungstellen und Stellen an denen $x(t)$ nicht stetig differenzierbar ist, gegen den Mittelwert des links- und rechtseitigen Grenzwerts.

D.h. punktweise Konvergenz gilt, wenn: [[Vorlesung_Fourierreihe_WP2.pdf#page=38|Skript]]
>[!info] Die Dirichlet Bedingungen sind hinreichend aber nicht notwendig.
