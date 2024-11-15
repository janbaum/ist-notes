![[Elektronik_Skript_23_24_complete.pdf#page=74]]

$R_{id} \rightarrow \infty$, $R_0=0$, $A \rightarrow \infty$
![[Elektronik_Skript_23_24_complete.pdf#page=75]]

#### 1. Annahme
If A is infinite, then the input voltage $v_{id}$ will be forced to zero for any finite output voltage: $v_{id}=0$ -> Nur für **Gegenkopplung**

#### 2. Annahme
If the input resistance $R_{ID}$ is infinite, then the two input currents $i_+$ and $i_-$ will be forced to zero: $i_+=0$ & $i_- =0$

### Mitkopplung
Bei Mitkopplung wird die Eingangsdifferenz $V{id}$ um 0° Phasenverschoben verstärkt. Das heißt:
- steigendes $V{id}$ $\Rightarrow$ steigendes $V_{out}$
- sinkendes $V{id}$ $\Rightarrow$ sinkendes $V_{out}$
Bei Mitkopplung wir der Ausgang **meistens** auf den nicht-invertierenden Eingang rückgekoppelt. Ein Gegenbeispiel ist der Spannungsfolger: [[#Spannungsfolger & Summary Inverting- Non-Inverting]] 
Die Mitkopplung erhöht die Verstärkung des Schaltkreises und **kann zur Stabilisierung der Verstärkung verwendet werden**.

### Gegenkopplung
Bei Gegenkopplung wird der Ausgang um 180° Phasenverschoben verstärkt, das heißt:
- steigendes $V{id}$ $\Rightarrow$ sinkendes $V_{out}$
- sinkendes $V{id}$ $\Rightarrow$ steigendes $V_{out}$
Bei Gegenkopplung wird der Ausgang (meistens/immer ?) auf den invertierenden Eingang rückgekoppelt. Allerdings sind nicht alle Rückkopplungen auf den invertierenden Eingang auch Gegenkopplungen (Siehe Spannungsfolger).
Die Gegenkopplung reduziert die Verstärkung des Schaltkreises und **verbessert oft die Linearität und Stabilität des Verstärkers.**
### Nicht-Invertierender 
![[Elektronik_Skript_23_24_complete.pdf#page=82]] 
### Spannungsfolger & Summary Inverting- Non-Inverting
![[Elektronik_Skript_23_24_complete.pdf#page=84]]

## Op Amp Teil 2
### Summationsverstärker 
[Schaltbild](Elektronik_Skript_23_24_complete.pdf#page=84)

### Differenzierungsverstärker

### Instrumentierungsverstärker

### Tiefpassfilter

### [Integrator](Elektronik_Skript_23_24_complete.pdf#page=89)
Kondensator als Rückkopplung am invertierenden Eingang
Wenn Kondensator mit $R_1$ getauscht, oder Kondensator durch Spule ersetzt:
-> Hochpass an Invertierendem -> Differenzierer 
### Terminology
![[Elektronik_Skript_23_24_complete.pdf#page=90]]

## Op Amp Teil 3
### Comperator & Schmitt Trigger

### Pulse width
#### Astable Multivibrator
$T_i = RCln \frac{1+\beta(\frac{V_{EE}}{V_{CC}})}{1-\beta}$
#### Monostable Multivibrator:
$T_i = RCln \frac{1+\beta(\frac{V_{D}}{V_{CC}})}{1-\beta}$
### Astable Multivibrator
Kondesator Ladespannung: $v_c=v_{out} = v_{cc}(1-e^{-t/{RC}})$$
$v_c(t)=V_{CC}-(V_{CC}+\beta V_{EE})e^{\frac{-t}{RC}}$
![[Elektronik_Skript_23_24_complete.pdf#page=96]]

### Monostable Multivibrator
[[Elektronik_Skript_23_24_complete.pdf#page=98]]
 