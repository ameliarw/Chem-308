Particle in a Box
--

We've created a program which discritizes space and combines the potential energy and kinetic energy into a PIB hamiltonian matrix.
The eigenvalues and eigenvectors of this matrix have also been determined and sorted in two different matrices. 
One is a matrix composed of the sorted eigenvectors.
The eigenvalues of the total energy matrix are the diagonal elements of another matrix, vals. Once the eigenvalues and eigenvectors of the 
Hamiltonian matrix were found, these eigenvalues and eigenvectors were sorted so that they will be plotted in the correct order. The graphs
of each eigenvector were then shifted upwards and scaled by 0.25 so that they could be seen more easily. 





Code for the program:

function plotPIB1D( n )
%remember, n refers to the number of eigenvectors generated

%here are my constants: 

%m is mass, L is length of box, barht height of barrier, w is the barrier
%width 

m = 1;

L = 5e-9;

hbarsq = ((6.626*10^-34)/pi)^2; 

barht = 1e6;

w=3; 

pts = 250;

%now account for the delta x and discritize the number of elements in the x vector 

%We say that there are some number of points within the x vector

x = linspace(0, L, pts);

dx = x(2)-x(1);


%x is a vector that goes from 0 to 5 separated by some amount, dictated by
%the number of points. Vvec is a vector with the dimension of pts entries
%with one column
%now we have some number, points of entries in the x vector

Vvec = zeros(pts, 1);

Vvec([1:w, end - (w-1):end]) = barht;

%We created a vector of zeros, but we just set the first three and the last
%three entries (because w=3) equal to some barht (large number, using 1e6)


%plot vvec to see w

%figure(1); plot(x, Vvec)

%Now we Vvec on the diagonal of our potential matrix

V = diag(Vvec);


%making the second derivative matrix

D2 = -2*eye(pts) + diag(ones(pts-1,1), 1) + diag(ones(pts-1,1),-1);

%now account for the delta x idea by subtracting the first element from the
%second element because they will be evenly spaced, and multiply the matrix
%by the constants 

T = 1/(dx^2)*(-hbarsq/(2*m))*D2;


%here's our Hamiltonian, which accounts for both the potential energy and
%kinetic energy

H= T + V;


%now we want to solve for the eigenvalues of the square matrix H

[vecs, vals] = eig(H);

%%figure(1); plot (x, Vvec, x, vecs(:, 1:5))

%%axis([-inf inf -0.5 0.5]) 

%%arbitrarily chose 0.5 - but yay a graph


%now we sort the vectors and values so that they are plotted in ascending
%order of n, but the eigenvalues and eigenvectors stay together

[srtvecs, srtvals] = eigsort(vecs, vals);


%plot the potential and the eigenvectors 
%%all of the rows, then columns 1-5 to get the first 5 n

%%figure(1); plot (x, Vvec, x, srtvecs(:, 1:5))

%%axis([-inf inf -0.5 0.5])


%now we will need to shift the graphs up so that they are on different
%levels 

%start to make the repvals matrix

k = [1:1:pts];

l = ones(pts, 1);

%multiply by 0.25 so that the curves are more defined 

repvals = 0.25*l*k;


%defining shiftvecs so that the graphs will be shifted up

shiftvecs = repvals + srtvecs;


%we need to create a vector which has the diagonal entries of the potential
%energy matrix

v = diag(V);

figure (1); plot(x, shiftvecs(:,1:n), x, v)


%redefine shift vecs to adjust for the axis

shiftvecs = shiftvecs(:,1:n);

axis([min(x) max(x) min(v) 1.1*max(max(shiftvecs))])

%WOOHOO

%also by introducing the n values, we can now call any number of eigenfunctions by saying plotPIB1D(n)
