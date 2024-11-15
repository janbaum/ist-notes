>[!important] In LTI-Systemen ist der **Ausgang** des Systems vollständig durch das **Eingangssignal** und die **Antwort** des Systemes auf einen **Impuls am Eingang** beschrieben ist. ^lti

[[Vorlesung_Signale und Systeme_WP1.pdf#page=76|Ziele WP3]]:
- [[#^lti|Ziele LTI Systeme]]
- Faltung
- BIBO-Stabilität
- Kriterium absoluter Integrierbarkeit für BIBO stabile Systeme
### Ansätze zur Analyse von LTI Systemen
1. Differentialgleichungen ("sehr kompliziert" lol)
2. Analyse im Zeitbereich mittels [[Die Faltung|Faltungsintegral]]
3. Analyse im Frequenzbereich mittels [[Fourier-]] oder [[1) Laplace-Transformation]]
### Impulsantwort
- Die Impulsantwort eines Systems ist die Antwort des Systems auf einen Einheitsimpuls zum Zeitpunkt $t = 0$ 
- (vorausgesetzt alle Anfangsbedingungen des Systems sind auf Null gesetzt, d.h. interne Speicher, wie z.B. Kapazitäten sind entladen).
>[!linfo]- Eigenschaften der Impulsantwort
>![[Vorlesung_Signale und Systeme_WP1.pdf#page=79]]

### Sprungantwort eines LTI Systems
In praktischen Anwendungen [[#^impulsantwort|Impulsantwort]] manchmal schwer messbar. Stattdessen wird die Sprungantwort, d.h. die Antwort des Systems auf eine Sprungfunktion am Eingang, gemessen.
Die Impulsantwort $h(t)$ des [[Vorlesung_Signale und Systeme_WP1.pdf#page=99|Systems]] kann man dann [[Vorlesung_Signale und Systeme_WP1.pdf#page=100|aus der Ableitung]] der Sprungantwort $a(t)$ des Systems bestimmen.


### BIBO Stabilität
engl. bounded-input, bounded-output
>[!important] in System is BIBO stabil wenn jedes begrenzte Eingangsignal zu einem begrenzten Ausgangssignal führt.

Hinreichende Bedingung für BIBO Stabilität: Die zugehörige Impulsantwort $h(t)$ ist absolut integrierbar:
$$\int^{\infty}_{- \infty}|h(t)|dt < \infty$$
$\uparrow$ [[Vorlesung_Signale und Systeme_WP1.pdf#page104|Beweis]]
>[!example]- Beispiel BIBO Stabilität
>![[Vorlesung_Signale und Systeme_WP1.pdf#page=105]]

