{% include mathjax.html %}

[home](/README.md)

# Difference Equation vs. Differential Equation

## A new way to time evolve 

We've so far looked at the time evolution of a quantum state by separating out the function in terms of position and time, using a differential approach, where we
multiply the x positions of a wavevector (in position space) by the time-dependence: 

$$ \begin{equation}\label{tdse} \mathcal{H}\Psi(x,t) = E\Psi(x,t) \end{equation} $$ 

Where the time dependence is represented as: 
$${T_n(t) = e^(((−iEnt/hbar))}$$

Instead of using a differential equation to solve the Hamiltonian and find an energy eigenvalue using this formula: 
$ \hat{H} = \frac{-hbar^2}{2m}\frac{\partial^2}{\partial x^2} + {V(x)} $, we can instead define a difference equation to better understand the time evolution of a quantum state. 

Where we have previously discritized space using some arbitrary quantity %{dt}$, we can now compare the wavefunctions at two different times in order to better understand time evolution. 
$$ \begin{equation}\label{tdse} \mathcal{H}\Psi(x,t) = i{hbar}\frac{\partial}{\partial t}Psi(x,t) \end{equation} $$

This expression can now be expressed in the difference form by comparing the wavefunction {psi} at two different times: 
$$ \begin{equation}\label{tdse} \mathcal{H}\Psi(x,t) = i{hbar}\frac{\delta Psi(x,t)}{\delta t}\end{equation} $$

