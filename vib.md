{% include mathjax.html %}
[home](/README.md)

## Simple Harmonic Oscillator
How can we visually display which transitions are allowed? 
We use the harmonic oscillator to model simple molecular vibration. We use reduced mass in order to “fix” one side. This allows us to assume that we have one dimensional motion of on mass along an axis. 
 
First, the time independent Schrodinger equation will be solved using the potential energy of the harmonic oscillator. The original particle in a box code was modified such that the potential energy matrix modeled the harmonic oscillator potential energy. Then the eigenvectors and eigenvalues can be solved. We will use the dipole moment as the transition operator to determine whether or not the transition is allowed. We say that the transition dipole operator is the complex conjugate of the final wavevector state multiplied by the x position multiplied by the initial wavevector. We yield a scalar which is proportional to the likelihood of the transition from one initial state to a final state. 

We yield a scalar which is proportional to the likelihood of the transition from one initial state to a final state. 

On the graph below, the eigenvectors are again shifted up by their energies. With increasing energy levels, the nodes of the wavevectors become spaced closer together. The kinetic energy of the states increases with increasing energy levels, so the curvature of the graphical depiction of each energy state also increases. This is why the nodes become closer together with increasing energy level. 


Each different energy level is equally separated, the spacing is hbar*omega 
The zero point energy is ½ hbar *omega 
The ground state is a Gaussian 

Integral of the initial state* transition operator acting on the final state complex conjugate from infinity over all space

Calculate integral of psi final star  * transition operator * psi  initial 
The transition operator is simple...charge*displacement 

---------------
 ## Code for Simple Harmonic Oscillator Transitions
 
 First a number of constants must be defined. Most of these constants are set to zero in order to simplify the program. M is the mass of the particle, ${/hbar^2}$ 
 ```Matlab
 function selection(n)
    m = 1;
    hbarsq = 1; 
    pts = 250;
    k = 1e3;
    q = 1;
    n=10;

%now account for the delta x and discritize the number of elements in the x vector 
%We say that there are some number of points within the x vector
x = linspace(-1, 1, pts);
dx = x(2)-x(1);

 D2 = -2*eye(pts) + diag(ones(pts-1,1), 1) + diag(ones(pts-1,1),-1);   
    T = 1/(dx^2)*(-hbarsq/(2*m))*D2;
    Vvec=.5*k*(x.^2);
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
axis([-inf inf 0 200]);
end
 
