Way of taking a function, letting it propagate. 
Stationary state looks boring, at larger time steps, the stationary state starts to get wonky, the error accumulates
No eigenvectors calculated 
We are separating the potential energy and the kinetic energy 
It makes more sense to work with potential energy in position space and kinetic energy in the momentum space
So because we split these up, we do dt/2, this is the split step part 
Half step of potential, then full kinetic, then half step of potential
It would work to not split up the steps, but it makes more sense, you get faster computations 
Wait for 200 time steps before updating the graph so that it looks smoother 

