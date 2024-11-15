[[Vorlesung_Fouriertransformation_WP3.pdf#page=100|Skript]]
## Reale Filter mit Beispiel an RC-Tiefpass
 [Übertragungsfunktion des RC Tief pass-Filters](WP3_Lerneinheit10_Kurzzusammenfassung.pdf#page=7)
- Für das Beispiel eines angeregten RC-Schwingkreises untersuchen wir das Tiefpassverhalten des Systems sowohl im Zeitbereich als auch im Frequenzbereich. 
 - Ein Tiefpass ist ein System bei dem Signalanteile bei tiefe Frequenzen das System weitgehend unverzerrt passieren können und bei dem Signalanteile bei hohen Frequenzen am Ausgang gegenüber dem Eingangssignal deutlich gedämpft auftreten. 
 >[!summary]- 
![[wp3_rc-tiefpass.png]]
$3dB$ Grenzfrequenz: $ω_0 = \frac{1}{RC}$   
Zeitkonstante: $ω_0^{-1} = RC$

Gegeben sei ein einfacher [[Vorlesung_Fouriertransformation_WP3.pdf#page=99|RC-Schwingkreis]]:
$x(t)=R*i(t)+y(t)$
$i(t)=C\frac{dy(t)}{dt}$
Daraus folgt: $$x(t)=R*C\frac{dy(t)}{dt}+y(t)$$
Das heißt, wir brauchen den [[2) Eigenschaften der Fourier-Transformation#Differentiation nach der Zeit|Differentiationssatz]] und erhalten daraus: $$X(j\omega)=(1+j\omega RC)· Y(j\omega)$$
%%where $(1+j\omega RC)= \frac{1}{H(j\omega)}$%%
>[!note] Übertragungsfunktion
Die Übertragungsfunktion ergibt sich aus:
$$H(j\omega)=\frac{1}{1+j\omega RC}=\frac{1}{1+j\frac{\omega}{\omega_0}}$$
Für Impulsantwort $y(t)$, Blick in [[hilfsblaetter.pdf#page=4]]:
$$h(t)=\omega_0e^{\omega_0t}u(t)=\frac{1}{RC}e^{-\frac{t}{RC}}u(t)$$

>[!note] Grenzfrequenz
$\omega_0=\frac{1}{RC}$ ist die $3dB$ Grenzfrequenz.
Es gilt:
$$|H(jω_0)| = \frac{1}{\sqrt{2}} |H(0)|$$
so dass: $$20 log_{10} [\frac{|H(jω_0)|}{H(0)}]=-3dB$$

>[!note] Amplitudengang
>$$|H(jω)| = \sqrt{(\frac{1}{1+j\frac{\omega}{\omega_0}})²} = [1+(\frac{\omega}{\omega_0})²] ^{-\frac{1}{2}}$$
>

^ftamplitudengang

>[!linfo]- Zeitkonstante 
>S. 104: Amplitudengang
>S. 105: Phasengang
>![[Vorlesung_Fouriertransformation_WP3.pdf#page=104]]

>[!note] Phasengang
>TODO: Formeln in Mathjax übertragen
>![[Vorlesung_Fouriertransformation_WP3.pdf#page=107]]

>[!example]- Beispiele am RC-Tiefpass
>S. 109-112 Abklingende E-Funktion am RC-Tiefpass
>S. 113-121 Rechtecksimpuls am RC-Tiefpass
>![[Vorlesung_Fouriertransformation_WP3.pdf#page=109]]


### Klassifizierung von Filtern 
Aus dem Betragsspektrums $|H(jω)|$ der Übertragungsfunktion $H(jω)$ eines LTI-Systems lässt sich sehr einfach feststellen, ob es sich bei einem System um einen Hochpass-, Bandpass-, oder Tiefpass-Filter handelt.

[[#^ftamplitudengang|Amplitudengang]]: 
Mit steigendem $ω$ nimmt der Betrag der Übertragungsfunktion ab. Für kleine Frequenzen sind die Beträge von $H(jω)$ groß. Systeme, die sich so verhalten, werden **Tiefpass-Filter** genannt. 

Signalanteile bei tiefen Frequenzen passieren den RC-Filter nahezu unverändert. 
Signalanteile bei hohen Frequenzen werden stark gedämpft.

## Ideale filter
In der 10. Lerneinheit beschäftigen wir uns mit der theoretischen Modellvorstellung der ideale Filter. 
- Wir unterscheiden vier grundlegende Filtertypen: 
	- den Allpass-Filter
	- den Tiefpass-Filter
	- den Bandpass-Filter 
	- den Hochpass-Filter
- **Ideale Filter** werden im **Frequenzbereich definiert** und haben **unendlich steile Flanken** zwischen dem Durchlass- und dem Sperrbereich.
- Wir lernen, dass die zugehörigen **Impulsantworten** von idealen Filtern in **positive wie auch negative Zeitrichtungen unendlich ausgedehnt** sind und sich daher in der Praxis nicht als kausale Systeme umsetzen lassen. 
### Warum?
Ein LTI-System kann als Filter aufgefasst werden. Bei der Modellierung, dem Entwurf und der Analyse eines praktischen Systems ist es häufig sinnvoll mit der Vorstellung von idealisierten Filtern zu arbeiten. 
Ein idealer Filter ist im Frequenzbereich wie folgt charakterisiert: 
- Im Durchlassbereich ist der Amplitudengang konstant (meistens konstant 1). 
- Im Sperrbereich ist der Amplitudengang identisch Null. 
- Der Übergang von Durchlassbereich zu Sperrbereich hat unendlich steile Flanken.
- Häufige gilt die Anforderung, dass der **Phasengang** der Filter im Durchlassbereich linear (d.h. eine lineare Funktionen der Frequenz) ist. 
	- *Linearphasigkeit garantiert, dass die Verzerrung des Eingangssignals im Durchlassbereich am Ausgang lediglich in einer Zeitverzögerung besteht (vergleiche [[2) Eigenschaften der Fourier-Transformation#Zeitverschiebung|Verschiebungssatz]]).*
	- Beim idealen linear-phasigen Tiefpass bleibt die Hüllkurve des Eingangssignals im Durchlassbereich erhalten.
### Kurzfassung
**Im Frequenzbereich**:
- Konstante Verstärkung im Durchlassbereich
- Vollständige Unterdrückung im Stoppbandbereich
- Linear Phase (entspricht konstanter Zeitverzögerung) 
- Unendlich steile Flanken am Übergang vom Durchlassbereich zum Stoppbandbereich 
**Im Zeitbereich:** 
- Nichtkausales Filter (Impulsantwort zu negativen Zeiten verschwindet nicht)
- Unendlich ausgedehnte Impulsantwort

Reale Filter mit endlicher Impulsantwort lassen sich durch Abschneiden (bei positiven und negativen Zeiten) und Verschieben der Impulsantwort generieren. ⇒ [[gibbs'sches_phanomen.25|Gibbs’sches Phänomen]].

>[!example]- Beispiele
>>[!example]- Allpass
>>![[Vorlesung_Fouriertransformation_WP3.pdf#page=126]]
>
>>[!example]- Phasengang 
>>![[Vorlesung_Fouriertransformation_WP3.pdf#page=130]]
>
>>[!example]- Tiefpass mit Rechteckimpuls am Eingang
>>inkl. Folgeseite
>>![Tief pass-Filter mit Rechtecksimpuls am Eingang f](WP3_Lerneinheit10_Kurzzusammenfassung.pdf#page=12) 

 >[!info]- Fourier-Transformierte wichtiger Funktionen
 ![Fourier-Transformierte wichtiger Funktionen](WP3_Lerneinheit10_Kurzzusammenfassung.pdf#page=11)
 

