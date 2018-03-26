Position and momentum wave packets
Fourier transforms
Crucial to science and engineering 
Moving from one space to another
Fourier transforms are the link between position space and momentum space.
Like change of basis - 
Had a matrix of eigenvectors of one operator in one space, then multiply in energy space, then get one eigenvector in the position basis. If you want to do it opposite, use the inverse. 
Problem with the momentum eigenvectors  - they look tricky 
P = -ihbar d/dx
e^ikx, lambda = hbar*k
These eigenfunctions will be problematic (think about the infinity and negative infinity bound) 
Fft matlab command
Fast fourier transform - converts what would normally be the basis conversion matrix that you would normally see - 
It works quickly, doesn’t actually account for all values? 
Not real important to understand this, but 

Return back to video 
Key meanings: 
1. Two graphs, one is in position space and one is in momentum basis. 
The plane in the middle is at x = 0, k = 0. So at higher k, shortening the wavelength, increasing steepness, increasing energy
K is also sometimes called the wavenumber - so 
Fourier transform of time and frequency
f(t) → f(w) where f(t) is seconds, f(w) is in sec-1 , rad/sec, 2*pi*freq = ang. Freq. 
We could use position as the variable
f(x) → f(k) in m and m-1 
K = 2pi/wavelength 
So these are inversely proportional 
No real difference between the fourier transform of time and frequency, or fourier of position and k


Gaussian wavepacket in position space - if centered at zero, then the wavepacket is gaussian in momentum at zero as well - if it looks like gaussian, then it means that it is real, only had real values 

If momentum is shifted to the left, the particle has momentum to the left.
If k gets big, kinkier helix in the position space. 
As position gets bigger too, the momentum, the k gets kinkier too
If position is wide, then momentum space evolves more slowly 
Handedness of the helices are based on the sign of k 

The relationship between wide and narrow continues,  if one is wide, then the other is narrow. 
Find a way to describe all of these things on webpage.

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

Integration by parts - 
Fourier transform of a derivative
Fourier(f(x)) = f(k)

Only work with “nicely behaving functions” - insist that f(x) goes to zero in the limit of x going to +/- infinity, taper at infinity 

Given that f(x) goes to zero at infinity, what is Fourier(d/dx*f(x)) = fourier(f’(x))
What is the fourier transform of the first derivative of f(x) 

Should be 1/sqrt(2pi) integral from infinity to neg infinity f’(x) eikx dx 

With the fourier transform, multiplication becomes a derivative and derivatives become a multiplication 

