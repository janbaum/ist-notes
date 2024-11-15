Lernziele in [[Vorlesung_Fourierreihe_WP2.pdf#page=44|Skript]]:
In der 6. Lerneinheit nutzen wir die Fourierreihenentwicklung um Signale im Frequenzbereich darzustellen. 
- Die Fourierreihenkoeffizienten geben an mit welcher „Intensität“ das jeweilige „**ganzzahligen Vielfache** der Grundfrequenz“ im Signal enthalten ist. 
- Mithilfe der komplexen Fourierkoeffizienten lassen sich Signale als **Linienspektrum** (d.h. Betrag) und (diskreten) **Phasengang** gegen die diskreten Frequenzen darstellen. 
- Unter den zuvor betrachteten Konvergenzbedingungen ist die Frequenzbereichsdarstellung mithilfe der Fourierkoeffizienten äquivalent zu der Zeitbereichsdarstellung, d.h., bei der Transformation geht keine Information verloren.
- Wir betrachten die Frequenzbereichsdarstellung in LTI-Systemen und erkennen, dass die komplexen **Exponentialfunktionen** Eigenfunktionen von LTI-Systemen sind, die das System **ohne Verzerrung** und lediglich mit einer **komplexwertigen Dämpfung** passieren.

>[!reminder] Die Fourierreihe eines mit $T_0$ periodischen Signals x(t)
>![[2) Fourierreihenentwicklung#Fourierreihe komplexer Exponentialfunktionen]]
>Ausserdem gelten die [[Symmetriebeziehungen]]

## Beispiel an periodischem Rechtecksignale
Gesucht werden Amplitudenspektrum und Phasengang: [[Vorlesung_Fourierreihe_WP2.pdf#page=46|Beispiel]]

Das Signal x(t) ist **ungerade**, daher sind die zugehörigen Fourierkoeffizienten **rein imaginär**-wertig.
>[!error] Wie kommt [[Vorlesung_Fourierreihe_WP2.pdf#page=48|hier]] der Phasengang zustande?
>Wegen $e^{-j\omega_0nt}$, daher ist der Phasengang für positive n negativ und umgekehrt?? Aber das passt nicht mit:
>"Der Phasengang ist für n < 0 positiv (identisch π/2 ), für n > 0 negativ (identisch − π/2 )" (von [[Vorlesung_Fourierreihe_WP2.pdf#page=50|hier]])

