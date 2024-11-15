[[ReadItLater]] [[StackExchange]]

# [FIR filter with linear phase, 4 types](https://dsp.stackexchange.com/questions/9408/fir-filter-with-linear-phase-4-types)

Author: [Vidak](https://dsp.stackexchange.com/users/4710/vidak)

I know there are 4 types of FIR filters with linear phase, i.e. constant group delay: (M = length of impulse response)

1.  Impulse response symmetrical, M = odd
    
2.  Imp. resp. symmetrical, M = even
    
3.  Imp. resp. anti-symmetrical, M = odd
    
4.  Imp. resp. anti-symmetrical, M = even
    

each with its traits. Which of these types is most commonly used in FIR filter with linear phase design and why? :)

***

Answered by: [Matt L.](https://dsp.stackexchange.com/users/4298/matt-l)

When choosing one of these 4 types of linear phase filters there are mainly 3 things to consider:

1.  constraints on the zeros of $H(z)$ at $z=1$ (DC) and $z=-1$ (Nyquist)
    
2.  integer/half-integer group delay
    
3.  phase shift (apart from the linear phase)
    

-   **Type I** filters (odd number of taps, even symmetry) have no constraints on the zeros at $z=1$ and $z=-1$, the phase shift is zero (apart from the linear phase), and the group delay is an integer value.
    
-   **Type II** filters (even number of taps, even symmetry) always have a zero at $z=-1$ (Nyquist), they have a zero phase shift, and their group delay is a half-integer.
    
-   **Type III** filters (odd number of taps, odd symmetry) always have zeros at $z=1$ and $z=-1$ (i.e., at DC *and* Nyquist), they have a 90 degrees phase shift and an integer group delay.
    
-   **Type IV** filters (even number of taps, odd symmetry) always have a zero at $z=1$ (DC), a phase shift of 90 degrees, and a half-integer group delay.
    

This implies (among other things) the following:

-   Type I filters are pretty universal, but they cannot be used whenever a 90 degrees phase shift is necessary, e.g. for differentiators or Hilbert transformers.
    
-   Type II filters would normally not be used for high pass or band stop filters, due to the zero at $z=-1$, i.e. at $f=f\_s/2$. Neither can they be used for applications where a 90 degrees phase shift is necessary.
    
-   Type III filters cannot be used for standard frequency selective filters because in these cases the 90 degrees phase shift is usually undesirable. For Hilbert transformers, type III filters have a relatively bad magnitude approximation at very low and very high frequencies due to the zeros at $z=1$ and $z=-1$. On the other hand, a type III Hilbert transformer can be implemented more efficiently than a type IV Hilbert transformer because for the type III Hilbert transformer every other tap is zero.
    
-   Type IV filters cannot be used for standard frequency selective filters, for the same reasons as type III filters. They are well suited for differentiators and Hilbert transformers, and their magnitude approximation is usually better because, unlike type III filters, they have no zero at $z=-1$.
    
-   In some applications an integer group delay is desirable. In these cases type I or type III filters are preferred.

***

Answered by: [Juancho](https://dsp.stackexchange.com/users/330/juancho)

The filters with anti-symmetrical impulse response all have a zero at $z=1$ (i.e. frequency 0). So if you need to implement a high-pass filter or derivative-like filter (or even band-pass), then you must go for types 3 and 4.

Similarly, if your filter is a low-pass type, then types 1 and 2 apply.

So, this depends on the type of filter you need to design, and not on which is more common.

Then, there is also a difference between types 1 and 3 vs. 2 and 4 in terms of phase response. There will be a extra $e^{j\\theta/2}$ between the two types. Even if you don't care about the actual delay introduced, this half-sample difference can be important in terms of convergence in some cases of high-pass filters (the extra phase can make your frequency response continuous at $\\theta = \\pi$, therefore providing much faster convergence and a need for fewer coefficients).

In terms of implementation, all of the 4 types can be implemented efficiently without repeating the same coefficients twice.

You need, of course, the whole M-sized delay line. But instead of multiplying each of the tap outputs by its own coefficient, you first add (or subtract) the two corresponding outputs and then multiply only once by the coefficient.

For example, if impulse response is $h\[n\] = a \\delta\[n\] + b \\delta\[n-1\] + a \\delta\[n-2\]$ (type 1 filter), instead of implementing $y\[n\] = a x\[n\] + b x\[n-1\] + a x\[n-2\]$, you make it $y\[n\] = a (x\[n\] + x\[n-2\]) + b x\[n-1\]$.

***

Answered by: [niaren](https://dsp.stackexchange.com/users/199/niaren)

Since there already are two very nice answers, I will give some very basic examples from which the properties given in the other answers can be sanity checked against. Zero locations and phase responses are directly available.

symmetrical, M=odd

$H(z) = 1\\pm2z^{-1}+z^{-2} = (1\\pm z^{-1})^2 \\\\ H(e^{j\\omega}) = (1\\pm e^{-j\\omega})^2 = (e^{-j\\omega/2}(e^{j\\omega/2}\\pm e^{-j\\omega/2}))^2 = e^{-j\\omega}(e^{j\\omega/2}\\pm e^{-j\\omega/2})^2 = 4e^{-j\\omega}\\cos^2(\\omega/2) \\quad or \\quad -4e^{-j\\omega}\\sin^2(\\omega/2) = 4e^{-j(\\omega-\\pi)}\\sin^2(\\omega/2)$

$H(z) = 1+z^{-2} = (1 + jz^{-1})(1 - jz^{-1}) \\\\ H(e^{j\\omega}) = (1 + e^{-j2\\omega}) = e^{-j\\omega}(e^{j\\omega} + e^{-j\\omega}) = 2e^{-j\\omega}\\cos(\\omega)$

symmetrical, M=even

$H(z) = 1 + z^{-1}\\\\ H(e^{j\\omega}) = (1 + e^{-j\\omega}) = e^{-j\\omega/2}(e^{j\\omega/2} + e^{-j\\omega/2}) = 2e^{-j\\omega/2}\\cos(\\omega/2)$

$H(z) = 1 + z^{-3} \\\\ H(e^{j\\omega}) = (1 + e^{-j3\\omega}) = e^{-j3\\omega/2}(e^{j3\\omega/2} + e^{-j3\\omega/2}) = 2e^{-j3\\omega/2}\\cos(3\\omega/2)$

$H(z) = 1 + 3z^{-1} + 3z^{-2} + z^{-3} = (1 + z^{-1})^3 = (1-e^{-2\\pi/3}z^{-1})(1-e^{2\\pi/3}z^{-1})(1+z^{-1})\\\\ H(e^{j\\omega}) = (1 + e^{-j\\omega})^3 = (e^{-j\\omega/2}(e^{j\\omega/2} + e^{-j\\omega/2}))^3 = 8e^{-j3\\omega/2}\\cos(\\omega/2)^3 $

antisymmetrical, M=odd (according to \[1\], $h\[N/2\] = 0$ for this case)

$H(z) = 1 - z^{-2} = (1 + z^{-1})(1 - z^{-1}) \\\\ H(e^{j\\omega}) = 1 - e^{-j2\\omega} = e^{-j\\omega}(e^{j\\omega} - e^{-j\\omega}) = 2je^{-j\\omega}\\sin(\\omega)=2e^{-j(\\omega-\\pi/2)}\\sin(\\omega)$

antisymmetrical, M=even

$H(z) = 1 - z^{-1} \\\\ H(e^{j\\omega}) = (1 - e^{-j\\omega}) = e^{-j\\omega/2}(e^{j\\omega/2} - e^{-j\\omega/2}) = 2je^{-j\\omega/2}\\sin(\\omega/2)$

\[1\] a good reference [mitrappt](http://sip.cua.edu/res/docs/courses/ee515/chapter04/ch4-4.pdf)