
[home](/README.md)

{% include mathjax.html %}
# Selection Rules: 

This is the code used to determine which transitions are allowed in the simple harmonic oscillator. 
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
```
