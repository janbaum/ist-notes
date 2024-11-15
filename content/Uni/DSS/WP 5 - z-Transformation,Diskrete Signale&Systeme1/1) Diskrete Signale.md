Zeitkontinuierliche Signale lassen sich nicht mit Hilfe von Digitalrechnern verarbeiten.
Ein (zeit-) diskretes Signal wird durch eine **Folge reeller oder komplexer Zahlen** dargestellt:
1. von sich aus diskretes Signal, z.B. täglicher Börsenschlusskurs
2. aus analogem Signal abgeleitet: $f_n = f(nT)$
	- Zeitkontinuierliches Signal wird in eine reine Zahlendarstellung übersetzt. 
	- Dadurch wird der Einsatz digitaler Übertragungsverfahren, digitaler Signalverarbeitung, digitaler Regelungen usw. möglich. 
		- Annahmen im folgenden
		- Abtastung des zeitkontinuierlichen Signals zu äquidistanten diskreten Zeitpunkten $t=nT$ (mit $T= konstant$). $T$ heißt Abtastintervall. 
		- Einfluss der Amplitudenstufung bei Quantisierung vernachlässigbar wegen hoher Auflösung. 
		- Die Wahl des Abtastintervalls T werden wir im Abschnitt [[Abtastung]] behandeln.

>[!info]- graphische Übersicht kontinuierliche und diskrete Signale
>![[VL-ZT_1_Diskrete Signale.pdf#page=4]]
## Elementare diskrete Signale
>[!summary] Inhaltsangabe
>- [[#Impulsfolge]]
>- [[#Diskreter Deltakamm]]
>- [[#Einheitssprungfolge]]
>- [[#Exponentialfolge]]
>- [[#Sinus- Cosinusfolgen]]
### Impulsfolge
- Impuls zum Zeitpunkt $Null$
- andere Namen: diskreter Deltaimpuls, Einheitsimpuls, Kronecker – Delta
- [[VL-ZT_1_Diskrete Signale.pdf#page=6|verschobener Impuls]]
#### Abtast- und Ausblendeigenschaft
$$f_n \cdot \delta_{n-n_0}=f_{n_0} \cdot \delta_{n-n_0}$$
- Alle Werte der Folge bis auf einen werden ausgeblendet
- Daraus folgt: $$\sum^{\infty}_{n=-\infty}f_n \cdot \delta_{n-n_0}=\sum^{\infty}_{n=-\infty}f_0 \cdot \delta_{n-n_0} = f_0$$
##### Andere Interpretation: 
- Jede Folge $f_{n_0}$ lässt sich als **Summe (Überlagerung) verschobener und gewichteter Deltaimpulse** darstellen.
#### Vergleich Impulsfolge $\delta_n$ und [[Dirac-Impuls]] $\delta(t)$
>[!info]- Skript
>S.8-9
>![[VL-ZT_1_Diskrete Signale.pdf#page=8]]

### Diskreter Deltakamm
Der diskrete Deltakamm für $\mathbb{N} \in \mathbb{N}$ ist gegeben durch
$$\sum^{\infty}_{k=-\infty} \delta_{n-kN}$$
![[diskreter-deltakamm.png]]
### Einheitssprungfolge
![[einheitssprungfolge.png]]

### Exponentialfolge
$$f_n=a^n=e^{\beta n},a,\beta \in \mathbb{C}, a=e^\beta$$
abklingend für: 
- $|a| < 1$, oder
- $Re\{\beta\} < 0$
aufklingend für:
- $|a| > 1$, oder
- $Re\{\beta\} > 0$

### Sinus- Cosinusfolgen
- Sind eigentlich [[Teil2_1_Diskrete Signale.pdf#page=14|Spezialfälle]] der Exponentialfolge.
- Mit komplexen Exponentialfunktionen können Sinus- und Cosinusfolgen dargestellt werden:
>[!important] $$cos(n\omega+\phi)=\frac{1}{2}(e^{j\phi}e^{jn\omega}+e^{-j\phi}e^{-jn\omega})$$ $$sin(n\omega+\phi)=\frac{1}{2j}(e^{j\phi}e^{jn\omega}-e^{-j\phi}e^{-jn\omega})$$

#### Frequenzperiodizität
>[!important] Jede komplexe Exponentialfolge  $f_n$ ist frequenzperiodisch, d.h. sie ergibt sich nicht nur für $\omega$, sondern auch für andere Frequenzen $\omega +- m \cdot 2\pi$, mit $m \in \mathbb{Z}$, denn $$f(n)=e^{j(\omega+m2\pi)n}=e^{j\omega n}$$ 

Ein um höherfrequentes komplexes Exponentialsignal hat die gleichen Abtastwerte wie seine niederfrequente Version:
![[frequenzperiodizitaet-expofolgen.png]]

#### Zeitperiodizität komplexer Exponentialfolgen
- Komplexe Exponentialfolgen sind frequenzperiodisch, aber nicht immer zeitperiodisch.
- Bedingung für die Zeitperiodizität einer abgetasteten Exponentialfolge nach $N$ Abtastwerten:
>[!example]- Bedingung
>![[Teil2_1_Diskrete Signale.pdf#page=16]]
- Das heißt, $\frac{\omega}{2\pi}$ muss eine rationale Zahl $\frac{m}{N}$ sein

