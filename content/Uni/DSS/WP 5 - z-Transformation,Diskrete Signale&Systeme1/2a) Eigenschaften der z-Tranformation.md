>[!summary] Inhaltsangabe
>- [[#Linearität]]
>- [[#Verschiebung im Zeitbereich nach links]]
>- [[#Dämpfung / Modulation der Folge, Skalierung von $z$]]
>- [[#Lineare Gewichtung der Folge, Ableitung im z-Bereich]]
## Linearität
$$a\cdot f_n+b \cdot g_n \rightarrow zT \rightarrow a\cdot F(f)+ b \cdot G(z)$$
- Durch die <font color="#00b050">Skalierung</font> mit einer Konstanten <font color="#00b050">ändert </font>sich das <font color="#00b050">Konvergenzgebiet nicht.</font>
- Das resultierende Konvergenzgebiet ist in der Regel die <font color="#00b050">Schnittmenge </font>der beiden einzelnen Konvergenzgebiete.
- <font color="#00b050">Kürzen sich</font> jedoch durch die Addition <font color="#00b050">Pole weg</font>, so kann sich das <font color="#00b050">Konvergenzgebiet vergrößern</font>.
>[!example]- Beispiele: lineare Operation, Summe zweier (kausaler) Exponentialfolgen, (kausalen) Cosinus- und Sinusfolgen
>S.20-22
>![[VL-ZT_2_z-Transformation.pdf#page=20]]

## Verschiebung im Zeitbereich nach links
$$f_{n+n_0} \rightarrow zT \rightarrow z^{n_0}F(z)-\sum^{n_0-1}_{m=0}f_mz^{-(m-n_0)}$$
- Korrekturterm, da Werte der Folge aus dem Erfassungsbereich der Transformation ($n \geq 0$) herausfallen.
- Das Konvergenzgebiet ändert sich i.a. nicht.
- Beweis analog zu Verschiebung nach rechts.
>[!example]- Beispiel für $n_0=2$
>![[VL-ZT_2_z-Transformation.pdf#page=25]]

>[!example]- Beispiel zeitverschobenen Exponentialfolge
Siehe auch S.27: *nichtkausale* Exponentialfolge
>![[VL-ZT_2_z-Transformation.pdf#page=26]]


## Dämpfung / Modulation der Folge, Skalierung von $z$
	$$a^nf_n \rightarrow zT \rightarrow F \left\lparen \frac{z}{a}\right\rparen$$
mit $\mathcal{K}=|a| \cdot \mathcal{K}_f$
- Der Konvergenzradius multipliziert sich dabei um Faktor $|a|$
- Der [[VL-ZT_2_z-Transformation.pdf#page=28|Beweis]] folgt durch Einsetzen in die Definition
- Der Wert von $a$ bestimmt den „Charakter“ der Operation, wobei sich insbesondere folgende zwei praktisch relevante Fälle ergeben: 
	- Reelles $a$: $0<a<1$:  Dämpfung der Folge 
	- Komplexes $a$: mit Betrag eins, $a=e^{j\omega}$ : Modulation der Folge.
>[!example]- Beispiel gedämpften Cosinus- und Sinusfolgen
>![[VL-ZT_2_z-Transformation.pdf#page=29]]

## Lineare Gewichtung der Folge, Ableitung im z-Bereich
- Der linearen Gewichtung im Originalbereich entspricht die Ableitung im z- Bereich:
$$n \cdot f_n \rightarrow zT \rightarrow -z \frac{dF(z)}{dz}$$
, mit $\mathcal{K}=\mathcal{K}_f$
- Der [[VL-ZT_2_z-Transformation.pdf#page=30|Beweis]] erfolgt über gliedweise Differentiation der z-Transformierten, was innerhalb des Konvergenzgebiets zulässig ist.
- Das Konvergenzgebiet ändert sich nicht.
>[!example]- Beispiel z-Transformierte der Rampenfolge
>![[VL-ZT_2_z-Transformation.pdf#page=31]]


## Faltungsregel
- Eine zentrale Eigenschaft der z-Transformation ist die Überführung der Faltungsoperation im diskreten Zeitbereich in eine Multiplikation im z- Bereich: $$f_n * h_n = F(z) \cdot H(z)$$
>[!example]- Beweis & Beispiel 
>Beweis S.38
>![[VL-ZT_2_z-Transformation.pdf#page=39]]

## Anfangswertsatz
- Für den Anfangswert einer Folge gilt: $$f_0=\lim_{z \rightarrow \infty} F(z)$$
- Damit kann man den Anfangswert einer Folge direkt aus ihrer z-Transformierten **ohne Rücktransformation** ablesen.
- Der Satz folgt unmittelbar aus der [[VL-ZT_2_z-Transformation.pdf#page=40|Definitionsgleichung]]
## Endwertsatz
- Hat die z-Transformierte höchstens einen einfachen Pol bei $z=1$ und sonst nur Pole innerhalb des Einheitskreises, dann gilt: $$\lim_{n \rightarrow \infty} f_n = \lim_{z \rightarrow 1} (z-1) \cdot F(z)$$
>[!info] Anschauliche Begrüngung
>Sind die Voraussetzungen erfüllt, setzt sich die Folge $f_n$ aus <font color="#00b050">abklingenden Exponentialfolgen (Pole innerhalb des Einheitskreises)</font> und evtl. einem <font color="#00b050">konstantem Anteil (Pol bei $z=1$ )</font> zusammen. Für $n \rightarrow \infty$ verschwinden die Anteile der abklingenden Exponentialfunktionen, und nur der konstante Anteil mit Pol bei $z=1$ bleibt übrig.

