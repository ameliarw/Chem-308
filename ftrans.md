[home](/README.md)
{% include mathjax.html %}

### Fourier Transforms Introduction
   
In the video:  
There are two graphs present. One graph is the time evolution of a wavepacket in the position space, and the other graph is the time evolution of a wavepacket in the momentum space. The plane in the middle is at x = 0 and k = 0. 
 
At a higher k values, the wavelength of the wavepacket will be decreased and the graph will appear more steep. At higher k values, or wavenumbers, the wavepacket will have more energy. 

![video](/fvid.mp4)

The Fourier transform classically refers to the idea of tranforming a function which exists in time space into a function which exists in frequency space. A function of time can be transformed into a function of frequency, using the Fourier transform. 

Generally, the Fourier transform can be expressed as: 

![fourier](/four.jpg)


The first equation allows for the transformation from the time domain to the frequency domain, while the second equation is the inverse Fourier which allows for the transformation from the frequency domain to the time domain. 

The Fourier transform can also be used to move between position and momentum space. Fourier transforms are also the link between position space and momentum space and allow for the movement from one space to another. We've introduced a similar concept with the change of basis topic. The Fourier transform can also be written with position and momentum: 

![pos and mom](/posmom.png)


The Fourier transform and inverse Fourier transform of position and momentum both yield Gaussian functions if all the values are real values. With the introduction of imaginary numbers, the Gaussian wavepacket time evolves through the complex plane when x or k do not equal zero. 

When the wavepacket moves along x, with either more positive or more negative x values, the wavepacket in the momentum space develops more kinks. The opposite relationship is also true, as when k values increase in the momentum space, the helix in the position space also gets kinkier. The handedness of the helices are based on the sign of k or x. 

Position and momentum are still defined by their uncertainties relative to each other, where $ ΔxΔp≥ℏ/2 $.

If the position of a particle is known, the momentum will be more uncertain. If the momentum is well-defined, the position will not be well-defined. This relation hold true with gaussian wavepackets in postion and momentum space as well. If the wavepacket is narrow in position space. When the wavepacket in the position space is wide, the wavepacket in the momentum space evolves more slowly. 

The Fourier transform is a linear combination of sines and cosines. The evolving combination of sines and cosines is what causes the helical shape, and with higher energy, higher k values, the helical shape will appear to evolve more quickly and display more kinks. The Fourier transform 


-----------------------

f(k) specifies how much a pure sinusoid with wavenumber of k contributes to f(x) and spans all k values

Sinusoids with wavenumber, k 
Some examples: 
	a*cos(kx) + b*sin(kx) 
	If a is zero, all sin, if b is zero, all cos.
	If cos and sin are both contributing, the sum of these, the combination of the contributions will be described by R*cos(kx-phi), where R = sqrt(a2 + b2), phi = arctan(b/a) 
	And different contributions of a and b or cos and sin will shift this left and right
	R determines the magnitude of the function, phi determines how much it is shifted
	Eikx = cos(kx) + isin(kx)
Any way we are doing it, we are choosing sinusoids as the basis
Linear combination of sinusoidal functions 
When you do the fourier transform, you’re looking at linear combinations of sines and cosines
You just want to know how much cos and sin of each frequency contributes to the overall function
Start with a function in position space and express as a linear combination of fkeikx
K is inherently continuous 

f(x) can be re-written as the sum of fkeikx where fk is like cj and eidk like phij 

If the sum is infinite then the sum of all ks equals the integral of [math] overall of k 

To be a unitary transformation - keep the same length of the original vector, scaling
f(x) = (1/sqrt(2pi)) * integral from infinity to negative infinity (fkeikxdk)
The (1/sqrt(2pi)) is to scale the transformation properly 

This is the inverse fourier transform

So I have a wavefunction in momentum space and I want to see what it is like in position space
How much of each eisk contributes to the overall function 

f(x) thought of as output, f(k) is input in the inverse fourier transform

Can also do it the opposite way - the i becomes negative because complex plane - 
f(x) = (1/sqrt(2pi)) * integral from infinity to negative infinity (f(x)e-ikxdk)

SO connection to linear algebra
<u, v> = inner product, gets a scalar 

In calc-land 
f(x) and g(x) 
This would be the integral of f(x)*g(x) = some number 
 
When we do this using linear algebra, we have to keep in mind that we have to parameters - we have both x and k as parameters 
f(x) and g(x) 
Need a row vector * a column vector 


What is the fourier transform of the first derivative of f(x)?
	- With the fourier transform, multiplication becomes a derivative and derivatives become a multiplication.

