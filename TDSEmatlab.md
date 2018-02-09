[home](/README.md)

### MatLab code from class on 2/8 for time evolution of non-stationary states

function [x,E,psiX,psiE]=TDSE

% define constants, discritize , then define V and turn into matrix
% KE operator as matrix T
%H = T + V
%n refers to the number of eigenvectors generated

%here are my constants: %m is mass, L is length of box, barht height of barrier, w is the barrier width
m = 1;
L = 1;
hbarsq = 1;
barht = 1e6;
w=3;
pts = 250;

%now account for the delta x and discritize the number of elements in the x vector
x = linspace(0, L, pts);
dx = x(2)-x(1);

%x is a vector that goes from 0 to L separated by some amount, dictated by the number
%of points. Vvec is a vector with the dimension of pts entries with one column
% now we have points number of entries in the x vector
Vvec = zeros(pts, 1);
Vvec([1:w, end - (w-1):end]) = barht;

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
psiE = zeros(pts, 1);
psiE([1 2]) = 1;

%now get the first eigenvector in the positon basis
psiX = EtoX*psiE;
%this output is the first eigenvector in the position basis 

%get the corresponding x values corresponding to the first eigenvector
E = diag(srtvals);

%set t to get animation with time evolving
t = 0;
dt = 0.01;

% size(E)
% size(x')
% size(psiX)
% size(psiE)

for k = 1:100
    psiEt = psiE.*exp((-i*E*t)/hbarsq);
    psiXt = EtoX*psiEt;
figure (1)
%clf 
subplot (1,2,1)
AW_plot3 (x', psiXt)
subplot (1,2,2)
AW_plot3 (E, psiEt)
drawnow
t = t + dt;
end

end
