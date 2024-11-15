## Allgemeinen
- Ein (zeit-) diskretes System ist eine Abbildung $\mathcal{H}$, die einem zeitdiskreten Eingangssignal (einer Eingangsfolge) ein zeitdiskretes Ausgangsignal (eine Ausgangsfolge) zuordnet.
- Mathematische Beschreibung: Differenzengleichung.
- Beispiel: digitales Filter.
- Annahme im Folgenden: Das System hat keine Anfangsenergie, befindet sich in Ruhe.
- Analogie: zeitkontinuierliches System: Eingangsfunktion $x(t)$, Ausgangsfunktion $y(t)=\mathcal{H}\{x(t)\}$ und Differentialgleichung.

## LTI-Systemeigenschaften
Siehe [[lineare und zeitinvariante Systeme]]
- Ein System, das sowohl [[#Linearität|linear]] als auch [[#Zeitinvarianz|zeitinvariant]] ist, heißt LTI-System (Linear Time-Invariant System).
- [[lineare und zeitinvariante Systeme|LTI-Systeme]] spielen in der Systemtheorie die zentrale Rolle.
- [[#Linearität]] und [[#Zeitinvarianz]] sind die Voraussetzung zum Aufbau einer einfachen, aber mächtigen Systemtheorie, die wir in dieser Vorlesung behandeln.
- Bei praktischen Anwendungen, bei denen diese Voraussetzungen nicht oder nur teilweise zutreffen, versucht man, durch Einschränkungen oder Näherungen diese Eigenschaften so weit wie möglich zu erreichen, um dann die Theorie der LTI-Systeme anwenden zu können.
	- Z.B. Nichtlinearitäten in einem Regelkreis → Linearisierung um den Arbeitspunkt mittels Taylor-Entwicklung.
	- Z.B. zeitvariantes System des Mobilfunkkanals → Betrachten von Zeiträumen, in denen das System quasi zeitinvariant ist.
### Linearität
- Bei einem linearen diskreten System ist die Antwort auf jede beliebige Linearkombination von Eingangsfolgen gleich der entsprechenden Linearkombination der einzelnen Systemantworten: $$\mathcal{H}\{a_1x_{1_n}+a_2x_{2_n}\}=a_1 \mathcal{H}\{x_{1_n}\}+a_2 \mathcal{H}\{x_{2_n}\}$$
- Das wird auch Überlagerungssatz oder Superpositionsprinzip genannt.
>[!info]- graphische Darstellung
>![[VL-ZT_2_z-Transformation.pdf#page=3]]

>[!hint] Das ist uns schon aus WP1 bekannt: 
>![[lineare und zeitinvariante Systeme#[Linearität](WP1_Lerneinheit1_Kurzzusammenfassung.pdf page=5)]]

### Zeitinvarianz
- Reagiert ein diskretes System auf jede beliebige verzögerte Eingangsfolge mit einer entsprechend verzögerten Ausgangsfolge, so bezeichnet man das diskrete System als zeitinvariant.
  $$y_{n-n_0}=\mathcal{H}\{x_{n-n_0}\}$$
- Die Antwort eines diskreten Systems auf eine bestimmte Eingangsfolge ist unabhängig vom Anregungszeitpunkt, d.h. die Systemeigenschaften ändern sich zeitlich nicht.

>[!hint] Auch das kennen wir aus WP1: 
>![[lineare und zeitinvariante Systeme#[Linearität](WP1_Lerneinheit1_Kurzzusammenfassung.pdf page=5)]]

### Impulsantwort
- Bei einem diskreten LTI-System ist die <font color="#00b050">Kenntnis der Impulsantwort</font> vollständig ausreichend, um die <font color="#00b050">Antwort des Systems</font> auf jede beliebige Eingangsfolge zu bestimmen.
- Ausgangspunkt der Herleitung: Jede beliebige Eingangsfolge kann durch eine Summe verschobener und gewichteter <font color="#00b050">Deltaimpulse</font> dargestellt werden (vgl. Kapitel „[[1) Diskrete Signale#Andere Interpretation|Diskrete Signale]]“): $$x_n=\sum^{\infty}_{k=-\infty}x_k \delta_{n-k}$$
>[!hint]- Vergleiche aus Impulsantwort aus WP1
>![[pages/Uni/DSS/WP 1 - Faltung,Signale im Zeitbereich/Systemanalyse im Zeitbereich#Impulsantwort|Impulsantwort aus WP1]]

>[!example]- Antwort eines LTI-Systems auf eine beliebige Eingangsfolge
>S.7-8 (S.8 anschaulich mit Deltaimpulsen)
>![[VL-ZT_3_DiskreteSysteme.pdf#page=7]]

#### Sprungantwort
Hier als Vergleich mit Impulsantwort:
- Systemantwort auf einen Impuls: $$x_n=\delta_n \rightarrow h_n \rightarrow y_n=\delta_n*h_n=h_n$$
- Systemantwort auf einen Sprung: $$x_n=u_n \rightarrow h_n \rightarrow y_n=u_n*h_n=\bar{h}_n$$

|  Zusammenhang  Impuls - Sprung (siehe Kapitel [[1) Diskrete Signale#Einheitssprungfolge]]) |   Zusammenhang Impulsantwort – Sprungantwort  |
| --- | --- |
|  $\delta_n = u_n-u_{n-1}$   |  $h_n=\bar{h}_n-\bar{h}_{n-1}$  |
| $u_n=\sum^{n}_{k=-\infty}\delta_k$   |  $\bar{h}_n = \sum^{n}_{k=-\infty}h_k$  |

#### Impulsantwort von Serien- Parallelschaltungen
>[!abstract]- Blockdiagramm
>![[VL-ZT_3_DiskreteSysteme.pdf#page=10]]
### Kausalität
- Hängt die Ausgangsfolge zu einem bestimmten diskreten Zeitpunkt $n_0$ für jede beliebige Eingangsfolge nur vom Verlauf der Eingangsfolge bis einschließlich zu diesem Zeitpunkt ab, so bezeichnet man das System als **kausal**: $$y_{n_0}=\mathcal{H}\{x(n\leq n_0)\}$$
- Damit ein System kausal ist, muss der Grad des Nennerpolynoms der z-Übertragungsfunktion mindestens so groß sein wie der Grad des Zählerpolynoms: $$F(z):Nennerpolynom \geq Zählerpolynom$$
### BIBO-Stabilität
- Das System G ist BIBO-stabil, falls sämtliche Polstellen der z- Übertragungsfunktion G(z) betragsmäßig kleiner als eins sind, also innerhalb des Einheitskreises liegen.
- Ein diskretes System ist stabil, wenn seine Impulsantwort absolut summierbar ist.
	- ![[Pasted image 20240303141515.png]]
	- ![[Pasted image 20240303141427.png]]
