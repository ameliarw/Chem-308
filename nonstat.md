[home](/README.md)

#### Time Evolution of Non-Stationary States
While the time evolution of stationary states proves to be periodic and predictable, non-stationary states are composed of 
eigenvectors of different energies, leading to variation in the rates of time evolution. 

Here's what the time evolution of a non-stationary state looks like in the position and energy basis. The probability density of finding the particle at a specific position is also plotted. Note how the expectation value for the position changes over time. The first, second, and fifth states are contributing to the overall quantum state in this example - as seen in the three different "lollipops" in the graph of the energy basis. 

Because these three energy states are stationary states themselves, the time and position dependence for each state may be separated. The resulting graphs are representations of the equal contributions from these three stationary state to the overall non-stationary quantum state.

![three states](/tdsenonstat.gif)

###### Matlab code 
```Matlab
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
x = linspace(0, L, pts)';
dx = x(2)-x(1);

%x is a vector that goes from 0 to L separated by some amount, dictated by the number
%of points. Vvec is a vector with the dimension of pts entries with one column
% now we have points number of entries in the x vector
Vvec = zeros(pts, 1);
Vvec([1:w, end - (w-1):end]) = barht;
%Vvec(120:130) = 75;
%this makes a barrier in the middle of the box

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

EtoX=srtvecs; % change from energy basis to position basis
XtoE=inv(srtvecs); % change from position basis to energy basis
psiE=zeros(pts,1); % vector of all zeros
psiE([1 2 5])=1; % change position 1,2 in vector to 1
psiX=EtoX*psiE;

%this output is the first eigenvector in the position basis 

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
   xexp = real(psiXt'*(x.*psiXt));
   hold on 
   plot (real(xexp), 0, 'r*')
   
% energy expectation value in energy basis
   Eexp=real(psiEt'*(srtvals*psiEt));
   plot (xexp, Eexp, 'b*')
   text(0.2,Eexp,['E= ' num2str(Eexp)])
 hold off

    
 drawnow
t = t + dt;
end


end
```

[home](/README.md)
