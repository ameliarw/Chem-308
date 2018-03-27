### Fourier Transforms Introduction
Fourier transforms are the link between position space and momentum space and allow for the movement from one space to another. We've introduced a similar concept with the change of basis topic. 

In the video: 
There are two graphs present. One graph is the time evolution of a wavepacket in the position space, and the other graph is the time evolution of a wavepacket in the momentum space. The plan in the middle is at x = 0 and k = 0. 

At a higher k, the wavelength of the wavepacket will be decreased and the graph will appear more steep. At higher k values, or wavenumbers, the wavepacket will have more energy. 

How can we use the Fourier transform to move from time to frequency? 

![video](/fvid.mp4)

Key Points of the Video
- When the wavepacket appears as a Gaussian, either in position or momentum space, then it means that it only has real values. 
- When the momentum is shifted to the left, then the particle has momentum to the left. 
- If the k values increase, kinkier helix in the position space. 
- As position gets bigger too, the momentum, the k gets kinkier too
- If position is wide, then momentum space evolves more slowly 
- Handedness of the helices are based on the sign of k    
- The relationship between wide and narrow continues,  if one is wide, then the other is narrow. 

Find a way to describe all of these things on webpage.

(NOTES THAT WILL BE FURTHER EXPLAINED EVENTUALLY...BEFORE THURSDAY AFTER I TURN IN THESIS)

MATH
Fourier transforms with position and momentum 

Start with f(x) 

Fourier(f(x)) = f(k) is known as the fourier transform of f(x) 

K has units of 1/distance - cycles per unit distance 
Large wavelength is small k
Small wavelength is large k
----------------------------- k = 0

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

