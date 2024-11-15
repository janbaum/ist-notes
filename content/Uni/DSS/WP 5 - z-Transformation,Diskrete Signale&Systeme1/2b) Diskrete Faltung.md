- Diskrete Faltung, Faltungsprodukt, Faltungssumme: $$y_n=f_n*h_n=\sum^{\infty}_{i=-\infty}f_i \cdot h_{n-i} = \sum^{\infty}_{i=-\infty}h_if_{n-i}$$
## Eigenschaften
- Kommutativität: $f_n*h_n = h_n*f_n$
- Assoziativität: $f_n*(g_n*h_n)=(f_n*g_n)*h_n$
- Distributivität: $f_n*(g_n+h_n)=f_n*g_n+f_n*h_n$
- Neutralelement: $\delta_n * f_n = f_n$
- **Faltung** einer Folge $f_n$ mit zeitverschobener Impulsfolge: $f_n*\delta_{n-n_0}=f_{n-n_0}$
- **Produkt** einer Folge $f_n$ mit zeitverschobener Impulsfolge: $f_n \cdot \delta_{n-n_0}=f_{n_0} \cdot \delta_{n-n_0}$

>[!info]- graphische Veranschaulichung
>![[VL-ZT_2_z-Transformation.pdf#page=33]]

>[!note]- Papierstreifenmethode
>![[VL-ZT_2_z-Transformation.pdf#page=34]]

>[!note]- Berechnung mit Impulsfolge
>![[VL-ZT_2_z-Transformation.pdf#page=36]]

>[!summary] Zusammenfassung kontinuierliche und diskrete Faltung
>>[!question] Sind die Abtastwerte der kontinuierlichen Faltung gleich den Folgenwerten der diskreten Faltung ?
>>>[!fail] Im allgemeinen nicht, da bei der kontinuierlichen Faltung durch die Integration auch alle Funktionswerte $f(t)$ und $h(t)$ zwischen den Abtaststellen $iT$ das Ergebnis $y(t=nT)$ beeinflussen.
>>
>>>[!bug] Bei der diskreten Faltung hingegen wird $y_n$ nur durch die Abtastwerte $f_i=f(iT)$ und $h_i=h(iT)$ bestimmt.
>![[VL-ZT_2_z-Transformation.pdf#page=37]]

