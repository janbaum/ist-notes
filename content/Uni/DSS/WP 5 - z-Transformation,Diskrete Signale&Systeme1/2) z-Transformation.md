- Die z-Transformation hat für Zahlenfolgen die gleiche Bedeutung wie die Laplace-Transformation für zeitkontinuierliche Signale. 
- Wir entwickeln die z-Transformation aus der Laplace-Transformation für ideal abgetastete Signale. 
- Anwendungsbeispiele der z-Transformation: Beschreibung diskreter linearer Filter **durch [[Nullstellen]] und [[Pole]]**.

## Entwicklung der z-Transformation aus der Laplace-Transformation
- Ausgangspunkt: <font color="#2DC26B">ideal abgetastetes</font> Signal $f_a(t)$ , d.h. Signal $f(t)$ <font color="#2DC26B">wird mit einem Dirac-Kamm multipliziert</font>: [[VL-ZT_2_z-Transformation.pdf#page=3|Skript]]
Laplace-Transformierte von $f_a(t)$: $$\int^{\infty}_{0}f_a(t)e^{-pt}dt = \int^{\infty}_{0} \sum^{\infty}_{n=0}f_n \cdot \delta(t-nT)e^{-pnT}dt = \sum^{\infty}_{n=0}f_n \cdot e^{-pnT} \int^{\infty}_{0} \delta (t-nT)dt$$
$$= \sum^{\infty}_{n=0}f_ne^{-pnT}$$
Wir ersetzen $z=e^{pT}$: 
>[!important] $$\mathcal{L\{f_a\}|_{z=e^{pT}}}=\mathcal{Z}\{f_n\}=\sum^{\infty}_{n=0} f_nz^{-n}$$
$\Rightarrow$ Die z-Transformierte ist die Laplace-Transformierte der ideal abgetasteten Funktion mit Variablensubstitution.

Die z-Transformation ordnet der reellen oder komplexen Folge $f_n$ eine Funktion $F(z)$ der komplexen Variablen $z$ zu. Die Zuordnung ist eindeutig. [[VL-ZT_2_z-Transformation.pdf#page=6|Schreibweisen]]

### Geometrische Deutung der Variablensubstitution $z=e^{pT}$
>[!info]- graphische Darstellung
>![[VL-ZT_2_z-Transformation.pdf#page=8]]

1. d.h. jeder Punkt in der linken Hälfte der p-Ebene wird abgebildet auf einen Punkt innerhalb des Einheitskreises in der z-Ebene. 
2. , d.h. jeder Punkt in der rechten Hälfte der p-Ebene wird abgebildet auf einen Punkt außerhalb des Einheitskreises in der z-Ebene. 
3. , d.h. die $j\omega$-Achse der p-Ebene wird auf den Einheitskreis in der z-Ebene abgebildet. 
4. , d.h. Ursprung der p-Ebene wird auf den Punkt $z=1$ abgebildet.
5. Punkte $p_k$, die vertikal von einem Punkt $p_0$ einen Abstand haben, der ein Vielfaches der Abtastkreisfrequenz $\omega_s=\frac{2\pi}{T}$ ist, werden auf den gleichen Punkt $z_0=e^{p_0T}$ in der z-Ebene abgebildet. 
 $$p_k=p_0+jk\omega_s; mit k=+-1,+-2,...$$
 $$z_k=e^{p_0T}e^{jk\omega_sT}=e^{p_0T}e^{jk2\pi}=e^{p_0T}=z_0; \forall k$$
- p-Ebene kann in horizontale Streifen der Breite $\omega_s$ eingeteilt werden, wovon jeder auf die gesamte z-Ebene abgebildet wird. 
	- Primärstreifen: $|\omega| <= \frac{\omega_s}{2}$ 
	- Komplementärstreifen: Die Wiederholungen nach oben und unten mit $\omega_s$

### Konvergenzgebiet
Die z-Transformierte existiert für diejenigen $z \in \mathcal{K} \subseteq \mathbb{C}$, für die Summe absolut konvergiert, für $z \in \mathcal{K}$: $$\sum^{\infty}_{n=0}|f_nz^{-n}|<\infty$$
- $\mathcal{K}$ bezeichnet man als <font color="#2DC26B">Konvergenzgebiet</font> der z-Transformierten.
- Die Werte der Folge $f_n$ sind die Koeffizienten der [[Laurent-Reihenentwicklung]] der z-Transformierten um den Punkt $z=0$ . 
- Das Gebiet, in dem die Laurent-Reihe die z-Transformierte $F(z)$ eindeutig darstellt, ist das Konvergenzgebiet $\mathcal{K}$ der z-Transformierten.
- Das Konvergenzgebiet der <font color="#2DC26B">einseitigen z-Transformierten ist die Fläche außerhalb eines Kreises</font> mit Zentrum im Ursprung.
- Der Radius des Kreises (Konvergenzradius) wird durch den betragsmäßig größten [[Pol]] bestimmt.
- Im Zeitbereich entspricht dies der am stärksten aufklingenden Exponentialfolge.
> [!example]- Beispiel Grafik
<font color="#92cddc">Konvergenzgebiet</font> $\mathcal{K}$ in türkis:
![[zT-konvergenzgebiet.png]]

$\Rightarrow$ Die z-Transformierten existieren für alle Folgen, die nicht stärker als exponentiell ansteigen.
[[VL-ZT_2_z-Transformation.pdf#page=13|Hintergrund]]: (für $a>b$) $$\sum^{\infty}_{n=0}e^{(b-a)n}<\infty$$ 

>[!summary] Fazit
>- Wählen wir also den Konvergenzradius $r=e^a$ nur groß genug, so erhalten wir für alle praktisch relevanten Folgen Konvergenz.
>- Lediglich für die stärker als exponentiell anwachsenden Folgen wie z.B. $f_n=e^{n²}$ oder $f_n = n!$ konvergiert und existiert daher die z- Transformierte nicht.
>- Den Exponentialfaktor $e^{-an}$ bezeichnet man als **Konvergenz sichernden Faktor**, da er für $n \rightarrow \infty$ die Summanden so schnell nach null drückt, dass die Summe absolut konvergiert.

>[!example]- Beispiel z-Transformierte der Impulsfolge
>![[VL-ZT_2_z-Transformation.pdf#page=15]]

>[!example]- Beispiel z-Transformierte der Sprungfolge
>![[VL-ZT_2_z-Transformation.pdf#page=16]]

>[!example]- Beispiel z-Transformierte der (kausalen) Exponentialfolge
>![[VL-ZT_2_z-Transformation.pdf#page=17]]




