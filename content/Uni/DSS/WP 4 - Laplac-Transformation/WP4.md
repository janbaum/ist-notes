![[ZusammenfassungLerneinheit11.pdf]]

Definition einseitiger-, (beidseitiger) Laplace-Transformation:

-> Für kausale Signale identisch. Bei Laplace-Transf. immer einseitige gemeint.

- Korrespondenz-Tabelle: Rationale Ausdrücke für RLC-Schaltungen, wenn DGL im Frequenz-, oder Laplacebereich ausrechnen

- Herleitung von Eigenschaften im Laplacebereich (besonders **Differentiationssatz**, auch Anfangs- und Endwertsatz) [Folie 322]; ~ 19min
	- Sofern Grenzwert für $x(t)$ existiert, kann Grenzwert auch schon im LP-Bereich berechnet werden $lim {x(t)} = lim {p*X(p)}$
	- Voraussetzung: liegt 0 im Konvergenzbereich ? Korrespondenztabelle gilt nur für Re{} > 0
	- -> gilt bspw nicht für oszillierende Signale (weil kein Grenzwert)

- Von Laplace in Zeitbereich (inverse Laplace-Transformation):  ->1. Blick in Korrespondenztabelle.
	- Sonst Kurvenintegral [Folie 324]
	- mit gebrochen-rationalen Funktionen $H(p) = \frac{Y(p)}{X(p)}$ [Folie 327] **KLAUSUR**
		- -> faktorisieren, Nullstellen im Nenner "sichtbar" machen
		- Zwei verschiedene p-Werte -> zwei Gleichungen mit zwei Variablen (c_1,c_2) -> eindeutig lösbar[Folie 328, 329]
	- mit unecht gebrochen-rationaler Funktion:
		- Ploynomdivision, [Folie 330 f] -> in echt gebrochen-rationale Funktion
		- Nenner faktorisieren:
			- Polstelle im Nenner finden (durch ausprobieren mit einfachen Werten wie -1,0,1 etc.)
				- Wieder Polynomdivision durch gefundene Nullstelle ->    : {(p-Nullst)=0}  usw. bis Faktorisierung möglich ist (mit $c_1, c_2, c_i, ...$) im Zähler [Folie 334] (hier Umgang mit doppelter Nullstelle beachten, siehe auch Hilfsblätter;  ~ 55 min
				- Kürzen
		- $c_1, ..., c_i$ bestimmen und wieder in Ausdruck einsetzen
		- Mit Korrespondenztabelle Rücktransformationen der Summanden nachschauen
		- -> [Impulsantwort] berechnen TODO

- BIBO Stabilität eines LTI-Systems im Laplace-Bereich
	-  Wichtig für RLC-Schaltungen
	- Definition BIBO-Stabilität : [Folie 341]
		- notwendige Bedingung: -----"-----
		- _Für welche Werte von Sigma gilt Integral [Folie 343 ff]_
	- Frage: Wo liegen die Polstellen im LP-Bereich ?
		 - **Fallunterscheidung** [Folie 346 f]

**Ende Vorlesung**

