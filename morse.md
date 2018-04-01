## Modeling the Morse Potential 
Feedback on the pages: 
Update the landing pages so that it feels that anyone in the chemistry department would be able to read
Give global view of the topics, shouldn’t just read like a diary
Not even necessarily specific to the course, but more about the topics covered 
  
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

![Morse](/unshiftedmorse.png)

--------------
#### Matlab Code
```Matlab
function rules(n)
%remember, n refers to the number of eigenvectors generated
%here are my constants: 
%m is mass, L is length of box, barht height of barrier, w is the barrier
%width, k = spring constant, q = charge

m = 1;
L = 3;
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

% morse potential 
Vvec = 1*(1-exp((-1*(x-1).^2)));
Vvec = Vvec.*100;
% now scaled so we can see the states within the well

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

