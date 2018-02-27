[home](/README.md)


### Code for Three Dimensional Plot of TDSE
```Matlab
function AW_plot3(basisaxis,psi);
%% Plot complex valued vectors as 3D plots. The complex plane forms the
%% backdrop for the plot and the eigenvalue axis (defining the space)
%% projects out from that plane.
        
        s = 10; % 1/s defines the fraction of eigenvalue axis that is displayed
        
    % Begin by grabbing the real and imaginary parts of the vector psi,
    % defining the length of the "space" axis, and defining a vector of 
    % zeros that serve as the axis relative to which psi is plotted.
        realpart = real(psi);   % extract the real part of psi
        imagpart = imag(psi);   % extract the imaginary part of psi
        n = length(basisaxis);  % number of points in each vector
        bsl = zeros(n,1);       % define baseline as n zeros

    % Create a three dimensional stem plot. The bases of the stems are 
    % placed at the baseline "bsl" and the heads of the stems are displaced
    % from the baseline by the real and imaginary values of each vector
    % element
        plot3(...
          [basisaxis basisaxis]',[bsl realpart]',[bsl imagpart]','k',... % draw black stems
          basisaxis,realpart,imagpart,'b.') % draw stem heads as blue dots
        axis([min(basisaxis) max(basisaxis)/s -1 1  -1 1]); % set axis limits
        pbaspect([3,1,1])   % fix aspect ratio of 3D plot
        view([70,10])       % define the view angle
        grid on             % turn on the grid


end
```
