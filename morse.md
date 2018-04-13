## Modeling the Morse Potential  
  
Morse Potential - could solve for the potential, can be solved analytically. 
But we have matlab so we will adopt an approximation of ½ kx2 as the V(x) 
So now it is the harmonic oscillator problem. 
If I am in a particular state of a harmonic oscillator, can I get to another state of a harmonic oscillator 

The plot of the Morse potential with the first ten energy levels is shown below. 
![Morse](/morseplot.PNG)

Below, the likelihood of the transition is depicted below using a color scale from blue to yellow. The 
It is expected, however, that the simple harmonic oscillator selection rules would hold at lower energies. For lower energy transitions, it is expected that transitions where the change in n is equal to 1 would be allowed. This idea, however, does not appear on the graphical depiction of the likelihood of transition below. There may be a problem with the code. 
![Morse](/morseprob.PNG)

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

