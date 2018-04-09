{% include mathjax.html %}

[home](/README.md)


### Using the Gaussian Approximation
The ultimate goal of this modeling is to be able to say something about the localization of the particle in space. So far we have used eigenvectors to find the probability of finding a particle at a particular location over time, but we can also introduce a Gaussian wavepacket to better understand how position evolves with time. 

##### The Fourier Transform
The Gaussian is a special case where there is minimum uncertainty in both position and momentum. This allows the curve to look similarly both in the position and the momentum space. The Forier transform translates a curve from one domain to its complimentary domain. In the case of the Gaussian curve in the position domain and its complimentary momentum domain, it appears with the same bell-shape curve in both domains. 

This makes the Gaussian a good model. While the Gaussian model has the smallest uncertainty in both position and momentum, there is still a relationship between the shapes of the curve in these two domains. We can use this understanding of uncertainty to think about how the probability density of the position domain relates to the probability density of the momentum domain for the same state. If the curve is narrow in the position domain, that is there is a larger probability of finding the particle at a certain position, the curve of the Gaussian in the momentum domain will be broader - this is to say there is a wider distribution of possible momenta, as there is more uncertainty in the momentum. If there is greater uncertainy in the momentum (if the curve is broad in the momentum space), the curve in the position space will in turn also broaden, as the momenta which are faster would contribute to the particle moving faster to a new location and the slower momenta would contribute to the particle moving slower to a new location, increasing uncertainty in the location of the particle and causing a broadening in the Gaussian. 


##### What does this look like over time? 
Note the red star, the expectation value of the particle fit to this Gaussian curve and how it changes over time. 
![Gaussian](/gaus.gif)

We've set the probability density to begin slightly to the left of the barrier, and we've added in a barrier to make the behavior of the particle more interesting. 
 
The curve behaves in a less complicated fashion when the barrier is removed: 
![No barrier](/tdsenobarrier.gif)

##### Matlab Code to Include the Gaussian
```Matlab
function [x,E,psiX,psiE]=TDSE
```

First a number of different constants must be defined. Here, the mass of the particle (m), the length of the box (L), and {/hbar^2} are all defined as 1 in order to simplify the problem. The height of the barrier is defined as a large number to account for the infinite potential of the box and is set at {1 x 10^6}. A new variable w is defined as 3 in order to construct the potential wall, where w is essentially the width of the barrier. The number points used is set equal to 250.
```
%here are my constants: %m is mass, L is length of box, barht height of barrier, w is the barrier width
m = 1;
L = 1;
hbarsq = 1;
barht = 1e6;
w=3;
pts = 250;
```

The number of elements in the x vector is now defined. The linspace command is used to create a vector of x values which span from zero to the box length and are composed of pts number of elements. These x elements are evenly spaced between 0 and L. The change in x between all of these points is constant, as the points are evenly spaced and defined here as the difference between the second x element and the first x element. 
```
%now account for the delta x and discritize the number of elements in the x vector
x = linspace(0, L, pts)';
dx = x(2)-x(1);
```

%x is a vector that goes from 0 to L separated by some amount, dictated by the number
%of points. Vvec is a vector with the dimension of pts entries with one column
% now we have points number of entries in the x vector
Vvec = zeros(pts, 1);
Vvec([1:w, end - (w-1):end]) = barht;
Vvec(120:130) = 75;

%We created a vector of zeros, but we just set the first three and the last 
%three entries (because w=3) equal to some barht (large number, using 1e6)
%to model the infinite potential well

%Now we create the potential energy matrix but putting the entries of Vvec
% in a diagonal matrix
V = diag(Vvec);

%making the second derivative matrix

D2 = (1/(dx^2))*(-2*eye(pts) + diag(ones(pts-1,1), 1) + diag(ones(pts-1,1),-1));

%now account for the delta x idea by subtracting the first element from the
%second element because they will be evenly spaced, and multiply the matrix
%by the constants

T = (-hbarsq/(2*m))*D2;

%here's our Hamiltonian, which accounts for both the potential energy and
%kinetic energy
H= T + V;

%now we want to solve for the eigenvalues of the square matrix H
[vecs, vals] = eig(H);

%now we sort the vectors and values so that they are plotted in ascending
%order of n, but the eigenvalues and eigenvectors stay together
[srtvecs, srtvals] = eigsort(vecs, vals);

EtoX = srtvecs; 
XtoE = inv(srtvecs);
%defining an energy space vector which corresponds to the first energy
%eigenvector 
% psiE = zeros(pts, 1);
% psiE([1 2]) = 1;

%now set the Gaussian to take up a quarter of the box and shift it over to the left side
%psiX = EtoX*psiE;
K=4;
psiX = exp(-25*((x - .25).^2)) .* exp(i.*K.*x);
psiE = XtoE*psiX;

%get the corresponding x values corresponding to the first eigenvector
E = diag(srtvals);
%set t to get animation with time evolving
t = 0;
dt = 0.005;



for k = 1:100
    psiEt = psiE.*exp((-1i*E*t)/hbarsq);
    psiXt = EtoX*psiEt;
    
    %normalize these vectors
    psiXt = psiXt/norm(psiXt);
    psiEt = psiEt/norm(psiEt);
    
    %the probability density would be the normalized psiX * normpsiX
    %complex conjugate
    
%     prob = psiXt .* psiXt;
    prob = 5000* abs(psiXt).^2;

 figure(1)
% %clf 
 subplot (2,2,1)
    AW_plot3 (x, 5.*psiXt,1)
 subplot (2,2,2)
    AW_plot3 (E, psiEt,10)
 subplot (2,2,[3 4])
    plot(x, prob, x, Vvec)
    axis([-inf inf 0 100])
    

% expectation value for position, plotted with a red *
   xexp = psiXt' * diag(x) *psiXt;
   hold on 
   plot (real(xexp), 0, 'r*')
   
% energy expectation value
   Eexp = real(psiEt'*(srtvals*psiEt));
   plot (0, Eexp, 'b*')
   text(50, Eexp,['E= ' num2str(Eexp)])
   hold off

 drawnow
t = t + dt;
end

end


[home](/README.md)
