## Vorgehensweise
- Wir betrachten zunächst die allgemeine Darstellung von Signalen mittels **gewichteter Überlagerung [[Orthogonale Funktionen|orthogonaler Basisfunktionen]] und erläutern die besondere Bedeutung der Orthogonalität.
	- Orthogonale Reihenentwicklungen sind bei der Analyse von Signalen und Systemen, aber auch in vielen technischen Anwendungen (z.B. bei der Verarbeitung von Signalen und bei der Datenkompression) von großer Bedeutung.
- Wir führen die Fourierreihenentwicklung _als den Spezialfall einer Reihenentwicklung_ für **periodischer Signale** mittels trigonometrischer (d.h. Cosinus und Sinus) und komplexer Exponential-Funktionen ein.
>[!important] Die Fourierreihenkoeffizienten sind ein Maß dafür, wie ähnlich die darzustellende Funktion zu der jeweiligen Basisfunktion (bei ganzzahligen Vielfachen der Grundfrequenz) ist.

### Die Darstellung von Funktionen als Linearkombination orthogonaler Basisfunktionen
Die ursprüngliche Funktion wird in Form eines Vektors in einem Koordinatensystem orthogonaler Basisvektoren dargestellt.
Das über dem Intervall $[a, b]$ definierte Signal $x(t)$ wird als Linearkombination (unendliche Summe) orthogonaler Basisfunktionen, d.h. einer Schar orthogonaler Funktionen dargestellt.
Der Linearkoeffizient $c_k$ ist ein Korrelationsmaß für die „Ähnlichkeit” des Signals $x(t)$ mit der Basisfunktion $ϕ_k(t)$.

#### Orthogonale Funktionen 
>[!example]- Beispiel einer endlichen Reihenentwicklung
>Werden bspw hier zwei verschiedene Funktionen miteinander multipliziert und dann über eine Periode aufintegriert, kommt immer 0 raus!
>![[Vorlesung_Fourierreihe_WP2.pdf#page=5]]

Die trigonometrischen Funktionen $cos(ω_0nt)$ und $sin(ω_0nt)$erfüllen die [[Vorlesung_Fourierreihe_WP2.pdf#page=10|Ortogonalitätseigenschaften]] 

[[2) Fourierreihenentwicklung]]
