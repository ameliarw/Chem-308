## Vibrational Transitions

Mechanism we are focused on is the relationship between an oscillating electromagnetic field (light) and a dipole moment. 

We need to have an oscillating dipole moment (can’t get from stationary state) 
 
Electric dipole moment which oscillates at the frequency of the electromagnetic field. 
Frequency matching as energy matching → if you match the frequency, you match the energy
Polarization of light 
Horizontal or vertical (think of as basis)  
Or a combination of the two in circularly polarized light 
Circularly polarized light has angular and linear momentum, should be considered 
Horizontal and vertical together as combination
If there isn’t a 90 difference between the two components, then you get elliptically polarized light 
Polarization - in space, what is the path of the maximum as it travels across space? 
SO why is polarization important? 

Transition dipole moment is the point where the two orbitals have equal contribution - if that distribution changes with time, with phase changes, then you have an oscillating dipole moment. 

A linear combination of two eigenvectors with the same energy (degenerate energy) will yield another eigenvector of the Hamiltonian 

2px = e-ml(fi) - e

3dz2 is not a linear combination - it has well defined energy all by itself. 

Conservation laws come out of symmetry - if you bring in another atom, symmetry is broken.

The orbitals as cartoons to conceptualize the idea of selection rules, which would be allowed 

Molecular vibration case
We use the harmonic oscillator to model simple molecular vibration. 
K is the force constant. 
We use reduced mass in order to “fix” one side. This allows us to assume that we have one dimensional motion of on mass along one 


Bond strength is the Eo
R0 is the equilibrium bond length 
K is the curvature - stiffer, skinnier curve 

Morse Potential - could solve for the potential, can be solved analytically. 
But we have matlab so we will adopt an approximation of ½ kx2 as the V(x) 
So now it is the harmonic oscillator problem. 
If I am in a particular state of a harmonic oscillator, can I get to another state of a harmonic oscillator 

Each different energy level is equally separated, the spacing is hbar*omega 
The zero point energy is ½ hbar *omega 
The ground state is a Gaussian 

Integral of the initial state* transition operator acting on the final state complex conjugate from infinity over all space

How do we do this in matlab
Solve TISE for hamiltonian operator, where the V(x) is modeled by this potential 
Get vecs and vals
Plot vecs 1-6 
Displaced by their energies 
We need a potential - the potential is V(x) - the x is already linspace, just make a matrix with the solutions of ½ kx2 on the diagonal to make the potential energy matrix 
How do we get the selection rules? 
If you’re in one quantum state, what other quantum states would be allowed? 
Conceptually, 0 - 5 are the first six states (start with V = 0) 
Then you have the possible final states
Think about making a matrix/table of what transitions are allowed 
Before we make this plot, we have to find our values .
Calculate integral of psi final star  * transition operator * psi  initial 
The transition operator is simple...charge*displacement 

---------------
#### Matlab Code: 
```Matlab
function rules(n)
%remember, n refers to the number of eigenvectors generated
%here are my constants: 
%m is mass, L is length of box, barht height of barrier, w is the barrier
%width, k = spring constant, q = charge

m = 1;
L = 1;
hbarsq = 1; 
barht = 1e6;
w=3; 
pts = 250;
k = 1e3;
q = 1;
n=5;

%now account for the delta x and discritize the number of elements in the x vector 
%We say that there are some number of points within the x vector
x = linspace(-1, L, pts);
dx = x(2)-x(1);

%x is a vector that goes from 0 to 5 separated by some amount, dictated by
%the number of points. Vvec is a vector with the dimension of pts entries
%with one column
%now we have some number, points of entries in the x vector

% simple harmonic oscillator potential
Vvec = 0.5*k*(x.^2); 
V = diag(Vvec);

%making the second derivative matrix
D2 = -2*eye(pts) + diag(ones(pts-1,1), 1) + diag(ones(pts-1,1),-1);

%now account for the delta x idea by subtracting the first element from the
%second element because they will be evenly spaced, and multiply the matrix
%by the constants 
T = 1/(dx^2)*(-hbarsq/(2*m))*D2;
H=T+V; % Hamilotian operator matrix (H)

%now we want to solve for the eigenvalues of the square matrix H
[vecs, vals] = eig(H);

%now we sort the vectors and values so that they are plotted in ascending
%order of n, but the eigenvalues and eigenvectors stay together
[srtvecs,srtvals]=eigsort(vecs,vals); 

%scaling the srtvecs values
sc=100;
srtvecs=sc*srtvecs;
v=diag(srtvals);% vector of sorted eigenvalues

%now we will need to shift the graphs up so that they are on different
%levels, as determined by energy
repvals=(ones(pts,1))*v';

%defining shiftvecs so that the graphs will be shifted up
shiftvecs=srtvecs+repvals; 
srtvecs = real(srtvecs);

%is the transition allowed? 
transitions = srtvecs' * diag(x) * srtvecs;

figure (2); 
pcolor(abs(transitions(1:9, 1:9).^2));
axis square

%adjust axis 
figure(1);plot(x,shiftvecs(:,1:n),x,Vvec); 
axis([-inf inf -.5 200]); 
end
```
