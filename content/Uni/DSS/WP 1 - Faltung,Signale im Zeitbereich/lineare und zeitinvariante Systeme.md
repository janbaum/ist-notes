### [Zeitinvarianz](WP1_Lerneinheit1_Kurzzusammenfassung.pdf#page=4): 
- Eingangs-Ausgangsbeziehung **nicht von der Wahl des Zeitpunktes abhängt**
- Über [[Vorlesung_Signale und Systeme_WP1.pdf#page=23|Faltungsintegral]] definiert
- Ein System ist zeitinvariant genau dann, wenn: Bei zeitverschobenem Eingang der Ausgang ebenso zeitverschoben wird.![[Pasted image 20240212113419.png]]
### [Linearität](WP1_Lerneinheit1_Kurzzusammenfassung.pdf#page=5):
- Linearität: Ein lineares System ist eines, für das das **Superpositionsprinzip** gilt:![[Pasted image 20240212113751.png]]
- Gegenbeispiel an [[Vorlesung_Signale und Systeme_WP1.pdf#page=36|Diodenschaltung]]
- Ein System aus mehreren Komponenten ist linear, wenn es nur aus linearen (zeitinvarianten?) [[Vorlesung_Signale und Systeme_WP1.pdf#page=45|Teilkomponenten]] besteht.
### [Kausalität:](WP1_Lerneinheit1_Kurzzusammenfassung.pdf#page=6)
- Die Antwort eines kausalen Systems zu Zeitpunkt $t_0$ **hängt lediglich von aktuellen und vergangenen** $(t ≤ t_0)$, nicht jedoch von zukünftigen $(t > t_0)$ Eingängen ab. Das System verhält sich nicht antizipatorisch.
- Gegenbeispiel: In der Bildverarbeitung spielt Kausalität meist keine große Rolle.

>[!detail]- Gedächtnisloses system
>Der Ausgang $y(t)$ des Systems zu einem gegebenen Zeitpunkt $t = t_0$ hängt nur von dem Eingangsignal zum Zeitpunkt $t = t_0$ ab – aber nicht von dem Eingangsignal x(t) zu vergangenen Zeitpunkten $(t < t_0)$. D.h., $y(t0) = T [x(t0)]$. Dynamisches System: Das Ausgangssignal y(t) hängt neben dem aktuellen Eingangssignal auch von vergangenen (gegebenenfalls auch von zukünftigen) Eingangswerten x(t) ab.
>Beispiel: **Widerstand**

>[!detail]- Dynamisches system
>Das Ausgangssignal $y(t)$ hängt neben dem aktuellen Eingangssignal auch von vergangenen (gegebenenfalls auch von zukünftigen) Eingangswerten $x(t)$ ab.
>Beispiel: **Spule**



