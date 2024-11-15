### DC Equivalent Circuits
- Kondensatoren $\Rightarrow$ $|Z|\rightarrow\infty$ $\Rightarrow$ offene Klemmen
- Spulen $\Rightarrow$ $|Z|\rightarrow 0$ $\Rightarrow$ Kurzschlüsse

### AC Equivalent Circuits
- Kondensatoren $\Rightarrow$ $|Z|\rightarrow 0$ $\Rightarrow$ 
- Spulen $\Rightarrow$ $|Z|\rightarrow \infty$ $\Rightarrow$ offene Klemmen
- DC-Spannungsquellen werden durch GND ersetzt, weil sie einen Innenwiderstand nahe 0 hat und weil dort keine AC-Spannung anliegen kann $\Rightarrow$ $v_{ac}=0$
- DC-Stromquellen werden durch offene Klemmen ersetzt, weil:
	- sie einen unendlich hohen Innenwiderstand hat
	- der Strom einer DC-Stromquelle sich nicht verändert, auch wenn sich die Spannung um sie herum ändert $\Rightarrow$ $i_{ac}=0$

## Kochrezept Schaltungsanalyse
1. DC-Analyse zuerst
	1. DC-Equiv.-Circuit aufstellen: Kondensatoren und Spulen ersetzen
	2. DC-Arbeitspunkt durch Großsignalmodel für Transistoren ermitteln 
2. AC-Analyse
	1. AC-Equiv.-Circuit aufstellen: Kondensatoren, Spulen, DC-Strom- und Spannungsquellen ersetzen.
	2. Transistor durch sein [Kleinsignalschaltbild](Kleinsignalschaltbild.md) ersetzen
	3. Analysiere die AC-Eigenschaften des Verstärkers mit dem Kleinsignalmodell aus 2.2
	4. Kombiniere Schritt 1.2 und 2.3 um die absoluten Werte des Netzwerks zu berechnen (machen wir fast nie)

#### Thévenin Transformation
1. Leerlaufspannung ermitteln (an gestrichelter Linie): $R_{leer}=v_s*\frac{R_B}{R_B+R_S}$
2. Innenwiderstand ermitteln: $v_s$ deaktivieren -> $R_B || R_S$
$\Rightarrow$ Seite 4-32: $v_{th}$ & $R_{th}$ 
![[Elektronik_Skript_23_24_complete.pdf#page=129]]