## [[Pasted image 20240319143046.png|Vergleich aller drei Verstärkertypen]]
- [[Pasted image 20240319170605.png|Simplified Characteristics of Single BJT Amplifiers]]
- [[Pasted image 20240319170740.png|Simplified Characteristics of Single BJT Amplifiers]]

## Invertierende Verstärkers (Common-Emitter,Common-Source)
- These amplifiers provide **moderate/high**:
	- voltage Gain
	- input resistance
	- output resistance
### [[Elektronik_Skript_23_24_complete.pdf#page=154|BJT Common-Emitter]]
- Emitter is "Ground"-potential by input signal **and** output signal
- [[Elektronik_Skript_23_24_complete.pdf#page=155|Voltage gain, output voltage, voltage divider]]
- [[Elektronik_Skript_23_24_complete.pdf#page=156|Input resistance]]
- [[Elektronik_Skript_23_24_complete.pdf#page=157|Output Resistance f]]

### [[Elektronik_Skript_23_24_complete.pdf#page=158|MOSFET Common-Source]]
- Wie Common-Emitter
- kein $r_\pi$ $\Rightarrow$ kein DC-Gate Strom! $\Rightarrow$ Bias-Widerstände deutlich höher wählbar, weil Spannungsteiler unbelastet
- $g_m$ im Vergleich zu BJT bei sehr ähnlichen Arbeitspunkten (also gleicher Collectorstrom im Vergleich zum Gate-Source-Strom) deutlich kleiner 

| Eigenschaft       | C-E(BJT) | C-S(MOS) | Advantage           |
| ----------------- | -------- | -------- | ------------------- |
| Voltage Gain      | higher   | lower    | BJT                 |
| Input Resistance  | lower    | higher   | MOS                 |
| Output Resistance | =        | =        | for similar Q-Point |


## [[Elektronik_Skript_23_24_complete.pdf#page=164|Folgeverstärker (Common-Collector, Common-Drain)]]
- Equivalent to op-amp voltage-follower:
	- Gain $\approx$ 1
	- high input resistance
	- low output resistance
- In AC-Ersatzschaltbild: negative Seite von $v_{th}$ und Collector beide auf Masse $\Rightarrow$ Common-Collector
- $|v_{gs}| < 0.2(V_{GS}-V_{TN}$
- [[Elektronik_Skript_23_24_complete.pdf#page=165|AC-Ersatzschaltbilder]]

| Eigenschaft                             | Advantage |
| --------------------------------------- | --------- |
| Voltage Unity Gain                      | BJT       |
| Achieve  $g_mR_L>>1$ -> $0.75<A{Vth}<1$ | BJT       |
- $\Rightarrow$ Bei BJT folgt die Ausgangsspannung der Eingangsspannung besser, weil eben $g_m >> 1$

- [[Elektronik_Skript_23_24_complete.pdf#page=169|Zusammenfassung und Vergleich]]





## Nicht-Invertierende Verstärker (Common-Gate, Common-Drain)
- These amplifiers provide:
	- moderate/high voltage Gain
	- low input resistance
	- high output resistance