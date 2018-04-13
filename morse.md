## Modeling the Morse Potential  
  
How can we visually display which transitions are allowed? 
First, the time independent Schrodinger equation will be solved using the potential energy of the harmonic oscillator. Then the eigenvectors and eigenvalues can be solved. 
We will use the dipole moment as the transition operator to determine whether or not the transition is allowed. 
Then we can visualize them with a graphic 

Also think about why the harmonic oscillators look the way they look when graphed - why are the nodes spaced closer together? - the energy, the kinetic energy is increasing between states. 

The original particle in a box code was modified such that the potential energy matrix modeled the harmonic oscillator potential energy. The eigenvectors were again shifted up by their energies. 


Using the reduced mass allows for the simple harmonic oscillator to be used. Take for example an HCl molecule. The reduced mass is 1, by 35+1/35*1 = 1. The graphs are the probability amplitude of the hydrogen atom. The chlorine is the negative side of the dipole. The charge is a fixed constant. 




Selection rules are not limited to electronic transitions - they also define which vibrational, rotational, transitions are allowed. 

The concavity of the wavefunction flips at the turning point. The behavior of the wavefunction changes between where it is classically allowed and not allowed classically. 
Oscillates where allowed
Exponentially decays after turning points


To determine the displacement for the transition dipole operator: 
We say that the transition dipole operator is the complex conjugate of the final wavevector state multiplied by the x position multiplied by the initial wavevector. 
We yield a scalar which is proportional to the likelihood of the transition from one initial state to a final state. 
We need to use some psi i from 0-9 and psi f from 0-9 
Make a diag(x) from the x linspace we have 
row* times matrix times column vector
Everything is in position basis 
X operator is in position - make a diagonal matrix of the x values
Then multiply the 

Using this matrix 

If your system is described by harmonic oscillator, you will see the selection rules we’ve found. 

Try it with the morse potential - does it move off to the side? Do we see different transitions allowed? 

Adjust the depth of the well and the x bounds to make sure that our graph fits within the new morse potential 

![Morse](/morseplot.png)
![Morse](/morseprob.png)

--------------
#### Matlab Code
```Matlab
function morse(n)
    m = 1;
    hbarsq = 1; 
    pts = 250;
    k = 1e3;
    q = 1;
    n=10;
    De = 500;
    a = 1;

%now account for the delta x and discritize the number of elements in the x vector 
%We say that there are some number of points within the x vector
x = linspace(0, 2, pts);
dx = x(2)-x(1);

 D2 = -2*eye(pts) + diag(ones(pts-1,1), 1) + diag(ones(pts-1,1),-1);   
    T = 1/(dx^2)*(-hbarsq/(2*m))*D2;
    Vvec=De*(1-exp(-a*(x-1))).^2;
    V=diag(Vvec);
    H=T+V; 

[vecs, vals] = eig(H);
[srtvecs, srtvals] = eigsort(vecs, vals);

k = diag(srtvals);
l = ones(pts, 1);
repvals = l*k';

sc = 100;
shiftvecs = repvals + sc*srtvecs;
    
    transitions=vecs'*(q*diag(x))*vecs;

    figure(1);pcolor(abs(transitions(1:n,1:n).^2))
    axis square
    figure(2);plot(x,shiftvecs(:,1:n),x,Vvec); 
axis([-inf inf 0 450]);
end
```

