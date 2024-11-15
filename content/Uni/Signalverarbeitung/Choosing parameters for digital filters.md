## FIR FILTERS
### Filter shape
_Rectangle, Barlett, Hanning, Hamming, Blackman_
-> control Main Lobe Width & Peak Amplitude of Side Lobe
-> controlled by parameter $\beta$
### Filter order/Window size
**controls Main Lobe Size only**
increasing N widens the filter -> order increases -> Main Lobe Width gets narrower
Peak Amplitude of Side Lobe stays the same
-> controlled by parameter $N$

>[!warning] _increase N always when your still not meeting your specifications_, but increasing $N$ results in more complicated convolution of H(z) and X(z)!

>[!info]- Properties of different windows
>![[DSP_Skript.pdf#page=37]]

1. desired Transerfunction: not realisable
	- truncate inv FT of transferfunction, because infitite impulsresponse impossible
		- -> have to convolute
	- desire: narrow main lobe, low side lobe peak
2. Design:
	- plugin numbers, get shape parameter and $N$
3. Drawback of this method:
		- method not based on optimization, because you just get parameters
			- means: find smalles N that meets specification -> **find best N**
### Optimal Filter Design
Minimizing the maximum Error (_see [[DSP_Skript.pdf#page=40|manuscript]]_)

## IIR filters
### Impuls Invariant Method
- Why design in continuous Frequency domain initially ? #frage 
- Problem: This method does not prevent from aliasing!
1. setting specs for descrete time system (ex. LPF) Folie 118
2. Map this into $\Omega$-domain:
	- means change x-axes only
3. dicede on refference filter (ex. Butterworth filter)
	1. pick the edges 
	2. $|H_c(j \Omega)|^2$ 
4. Laplace-Transformation: $H_c(s)$ 
5. z-Transformation: partial fraction expansion $H(z)$
												### Bilinear method
- non linear mapping from S -> Z
	- non linear transformtaion
- no sampling -> no aliasing
	- just transform frequency
