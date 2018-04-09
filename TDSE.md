{% include mathjax.html %}

[home](/README.md)
 
# The Time Dependent Schrodinger Equation
Now, our wavefunction or quantum state no longer only depends on space, but also time. In the Time Independent 
Schrodinger Equation, only energy eigenstates are solutions to the time-independent Schrodinger and therefore only energy 
eigenstates have well defined energy. In the TDSE, however, all physically realizable states are solutions to the 
Time-Dependent Schrodinger equation. This means that all energy eigenfunctions are solutions but not all solutions 
are energy eigenfunctions. Energy eigenfunctions have useful properties, but are not the only solutions to the TDSE. 

The time evolution of energy eigenstates is simple for the TDSE, but the time evolution of other solutions are not simple. 

#### Energy eigenstate = stationary state 
Energy eigenstates are simple and referred to as stationary states because their time evolution 
is cyclic. We can visualize this simplicity of the energy eigenstates with the plot of the energy eigenvalue in the energy basis. 
In the energy eigenstate example, this plot looked like a simple delta function, with each time corresponding to one single 
eigenvalue with a periodic movement about the complex plane. When another solution to the TDSE, but not a stationary state, 
was plotted, multiple delta functions appeared in the energy basis plot, and these energies evovled with different 
frequencies as well. The energy eigenstates have more simple time evolution compared with other possible solutions to the TDSE. 

What does this time evolution of a stationary state look like? 
[Stationary States](/TDSEmatlab.md)

We can mathematically separate the space and time dependence of our wavefunction if the wavefunction is an 
energy eigenfunction/stationary state/solution to the TDSE. 

These two variables can be separated and our wavefunction can be written as the product of two functions, 
one of which depends on space and the other depends on time. This separation of variables technique allows us to take the partial derivative of our function in respect to time and position separately. 

The time function is ${T_n(t) = \exp(−iE_nt/\hbar)}$

The complete time-dependent Schrodinger equation can be written as:
\begin{equation}\label{tdse} \mathcal{H}\Psi(x,t) = E\Psi(x,t) \end{equation}

The solutions of the TDSE do not depend on basis and therefore can be expressed in either the energy basis or the position basis. Eigenvalues do not have a specific basis. The energy basis, however, proves to be a more useful basis to use when describing the time evolution of quantum states. 

Quantum states will have faster or slower rates of rotation through the complex plane
depending on the energies of those quantum states. Therefore, solutions to the TDSE should be changed into the energy basis. 

What happens when you aren't dealing with a quantum state that is an energy eigenstate and the variables can no longer be separated? 
[Non-Stationary States](/nonstat.md)

What does this time evolution of a stationary state look like? 
[Stationary States](/TDSEmatlab.md)

[home](/README.md)
