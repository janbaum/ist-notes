## [Einheitsimpuls](WP1_Lerneinheit2_Kurzzusammenfassung.pdf#page=4)

#### [Eigenschaften der Einheitsimpulsfunktion](WP1_Lerneinheit2_Kurzzusammenfassung.pdf#page=6)
Der Einheitsimpuls dient zur Beschreibung [[Transiente – Wikipedia|transienter]], impulsartiger Vorgänge. Sie wird in der Regel als **Grenzwert einer in ε parameterisierten Folge** (Funktionsschar) klassischer Funktionen definiert -> Der Grenzwert wird bzgl. des Parameters ε gebildet:
[[Vorlesung_Signale und Systeme_WP1.pdf#page=56|Rechteckfunktionen]], [[Vorlesung_Signale und Systeme_WP1.pdf#page=57|abfallende e-Funktionen]],...
>[!important] #### Wichtig
>1. Die Impulsfunktion dient (verallgemeinert) als **Grenzwert** von [[Kurvenschar – Wikipedia|Funktionsscharen]] mit gewissen [[Vorlesung_Signale und Systeme_WP1.pdf#page=62|Bedingungen]]
>2. Die Impulsfunktion dient zur Bestimmung der [[Systemanalyse im Zeitbereich#Ansätze zur Analyse von LTI Systemen|Impulsantwort]] eines [[Systemanalyse im Zeitbereich#^lti|LTI Systems]] als Eingangssignal

>[!linfo] 1. **Normierung**: das Integral über die Impulsfunktion ist immer Eins


>[!linfo] 2. **Impuls-Character**: δ(t) hat eine Singularität an der Stelle $t = 0$
>- Das heißt, dass nicht für jeden Zeitpunkt ein definierter Funktionswert existiert
>
>[!important] ##### 3. Ausblendeigenschaft
$$x(t) \delta(t − t_0) = x(t_0) \delta(t − t_0)$$
Das bedeutet, dass die Faltung **einer Funktion** mit einem Dirac immer genau **diese Funktion** wieder zurück liefert $\rightarrow$ [[Vorlesung_Signale und Systeme_WP1.pdf#page=54|Skript]]

>[!linfo]- weitere Details
>- Der Einheitsimpuls δ(t) ist keine [(analytische) Funktion](https://de.wikipedia.org/wiki/Analytische_Funktion) im klassischen Sinne>>- Mit der Impulsfunktion lassen sich Phänomenen, die sich in extrem kurzen Zeiträumen abspielen, modellieren.
>- Die Impulsfunktion bildet nahezu augenblickliche (instantane) Änderungen der Messgröße ab.

>[!example]- Beispiel Idealisierter Funktionen
>[Einheitssprung](WP1_Lerneinheit2_Kurzzusammenfassung.pdf#page=7)
>>[!linfo]- Zusammenhang zwischen Einheitssprung und Impulsfunktion
>>Es existiert eine Unstetigkeit an der Stelle $t = 0$. Dort wird die Funktion häufig mit dem Wert $u(0) = 1/2$ definiert *(den Grund dafür sehen wir später im Zusammenhang mit der [[1) Fourier-Transformation#[Konvergenz der Fourier-Transformation](WP3_Lerneinheit7_Kurzzusammenfassung.pdf page=7)|Konvergenz der Fourier-Transformation]])*





