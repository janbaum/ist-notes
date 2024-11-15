## Komplexes Umkehrintegral
$$f_n = \mathcal{Z}^{-1} \{F(z)\}=\frac{1}{2\pi j} \oint_C F(z)z^{n-1}dz$$
>[!info]- Beschreibung
>![[VL-ZT_2_z-Transformation.pdf#page=42]]
- Berechnung des Umkehrintegrals in der Regel mit Hilfe des [[Residuensatzes]].
## Partialbruchzerlegung
- Für rationale z-Transformierte stellt die Rücktransformation über die Partialbruchzerlegung das wichtigste und einfachste Verfahren dar. 
>[!hint] Idee
>Komplizierte Funktion in einfache elementare Terme zerlegen, die jeweils getrennt einfach (z.B. mittels Korrespondenztabelle) behandelt werden können.

### Ausgangspunkt
- rationale Funktion
- Zählergrad $\leq$ Nennergrad
	- falls Zählergrad $>$ Nennergrad, muss vorher das Polynom in $z$ (antikausaler Signalanteil) mittels [[#Polynomdivision]] abgespalten und getrennt behandelt werden.
### Schritt 1
- Hilfsfunktion bilden: $\widetilde{F}(z) = \frac{F(z)}{z}$
	- Dadurch ist sichergestellt, dass Zählergrad $<$ Nennergrad, d.h. echt gebrochen rational, und damit Ansatz der Partialbruchzerlegung für $\widetilde{F}(z)$ möglich ist.
### Schritt 2
- Bestimmen der Pole $\alpha_i$ und deren Vielfachheiten $k_i$ von $\widetilde{F}(z)$ über die Nullstellen des Nennerpolynoms.
### Schritt 3
- Ansatz der Partialbruchzerlegung in der Form: ![[zT-partialbruchzerlegung.png]] mit $\alpha_i, \tilde{\alpha}_i, r_i, \tilde{r}_{i,l} \in \mathcal{C}$
- bzw. für (einfache) konjugiert komplexe Polpaare eventuell zusätzliche Terme der Form: ![[zT-konj._kompl-partialbruchzerlegung.png]]
### Schritt 4
- Bestimmen der Koeffizienten $r_i, \tilde{r}_{i,l}$ bzw $d_i, e_i$ über 
#### Koeffizientenvergleich der auf den Hauptnenner gebrachten Partialbruchsumme

oder über die 
#### Residuenformel
##### einfache Pole
$$r_i = (z-\alpha_i) \widetilde{F}(z)|_{z=\alpha_i}$$
TODO: Hä?! Schöner/verständlicher aufschreiben, gutes Beispiel verlinken
##### mehrfache Pole
TODO: Hä?! Schöner/verständlicher aufschreiben, gutes Beispiel verlinken

### Schritt 5 
- Multiplikation der Gleichung mit $z$  führt auf die Form: $$F(z)= \sum_{i} r_i \frac{z}{z-\alpha_i} + \sum_{i} \sum^{m}_{l=1} \tilde{r}_{i,l}\frac{z}{(z-\tilde{\alpha}_i)^l}$$, welche mit der Korrespondenztabelle rücktransformiert werden kann.

>[!example]- Korrespondenzen für einfache, mehrfache und konjugiert-komplexe Pole (-paare) 
>S.47-48
>![[VL-ZT_2_z-Transformation.pdf#page=47]]

## Alternativer Ansatz
- Wenn Zählergrad $<$ Nennergrad:
	- [[VL-ZT_2_z-Transformation.pdf#page=49|Direkte Partialbruchzerlegung]] von $F(z)$
	- In diesem Fall fehlt jeweils der Term $z$ im Zähler der Entwicklungsglieder, um die elementaren Korrespondenzen anzuwenden.
	- Erweitern mit $z/z$
	- *Elementare Korrespondenzen sind in einer zeitverschobenen Version anzuwenden.*
	- Man dividiert das Zählerpolynom durch das Nennerpolynom.
	- Wenn Zählergrad $≤$ Nennergrad, ergibt dies eine Form: $$f_0+f_1z^{-1}+f_2z^{-2}+...$$
	- Die Faktoren $f_n$ sind genau die gesuchte kausale Zahlenfolgen
>[!example]- Beispiel Polynomdivision
>![[VL-ZT_2_z-Transformation.pdf#page=51]]
- -> Nur sinnvoll, wenn sich der generelle Ausdruck für $f_0,f_1,f_2,...$ aus den ersten wenigen Werten ableiten lässt oder wenn nur wenige erste Werte, z.B. $f_0,f_1,f_2,f_3$ gesucht sind.