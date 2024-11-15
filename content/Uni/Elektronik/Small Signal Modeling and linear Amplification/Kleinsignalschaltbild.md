# Allgemein
- Damit wir DC und AC Analysen von einander getrennt betrachten und mittels Superpositionsprinzip zusammen führen können, müssen die AC Spannungen und Ströme klein genug bleiben, dass die Linearität des Systems nicht beeinträchtigt wird!
- Es ist Geräte spezifisch was "klein genug" bedeutet. Wir definieren dies bei der Entwicklung des Kleinsignalmodells für jedes einzelne Gerät.

## Diode
![[Elektronik_Skript_23_24_complete.pdf#page=130]]

beachte $v_d$ und $g_d$!
$g_d=\frac{I_D+I_S}{V_T}$

> [!tip] Wichtig
> - $g_d=\frac{I_D+I_S}{V_T}$
> - 
Bis zu einer Spannungsamplitude von $\approx$ 0.05 V kann Diode als Ohm'scher Widerstand betrachtet werden. 

## BJT

[Zwei-Tor-Theorie oder y-Parameters](Elektronik_Skript_23_24_complete.pdf#page=132):
- y sind Leitwerte
- v\*y sind (gesteuerte) Stromquellen

Überführung von Zwei-Tor-Modell in lineares Kleinsignalmodell des BJT ist lösbar.

Problem: Kleinsignalparameter $y_{i,j}$ zu finden -> aus Großsignalmodell herleiten 
![[Elektronik_Skript_23_24_complete.pdf#page=133]]

>[!tip] y-Parameter finden
>- Für $y_{i,j} \rightarrow$Ableitung der Großsignalgleichungen und Arbeitspunktbetrachtung (Seite 4-40 ff)

[Weiter gucken ab 1:05](https://moodle.tu-darmstadt.de/mod/lti/view.php?id=1237376) ^b724e5









## Feldeffekttransistor