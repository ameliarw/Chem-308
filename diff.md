{% include mathjax.html %}

[home](/README.md)

# Difference Equation vs. Differential Equation

## A new way to time evolve 

We've so far looked at the time evolution of a quantum state by separating out the function in terms of position and time, using a differential approach, where we
multiply the x positions of a wavevector (in position space) by the time-dependence: 

$$ \begin{equation}\label{tdse} \hat{H}\Psi(x,t) = E\Psi(x,t) \end{equation} $$ 

Where the time dependence is represented as: 
$${T_n(t) = e^(\frac{−i(E_n)t}{\hbar}}$$

Instead of using a differential equation to solve the Hamiltonian and find an energy eigenvalue using this formula: 
$ \hat{H} = \frac{-hbar^2}{2m}\frac{\partial^2}{\partial x^2} + {V(x)} $, we can instead define a difference equation to better understand the time evolution of a quantum state. 

Where we have previously discritized space using some arbitrary quantity {dt}, we can now compare the wavefunctions at two different times in order to better understand time evolution. 
$$ \begin{equation}\label{woo} \hat{H}\Psi(x,t) = i{\hbar}\frac{\partial}{\partial t}\Psi(x,t) \end{equation} $$

This expression can now be expressed in the difference form by comparing the wavefunction {\psi} at two different times: 
$$ \begin{equation}\label{wowwow} \hat{H}\Psi(x,t) = i{\hbar}\frac{\Delta \Psi(x,t)}{\Delta t}\end{equation} $$

With algebraic manipulation of this expression, we can ultimately solve for what the wavefunction appears as at a later time. Because ${-i}$ and ${\hbar}$ are defined as constants, we can rearrange the equation. 

$$ \begin{equation}\label{another} \hat{H}\Psi(x,t) = i{hbar} \frac{\Psi(x, t + \Delta t) - \Psi(x,t)}{\Delta t} \end{equation} $$

$ \Psi(x, t + \Delta t) = \frac{\Delta t \hat{H} Psi(x, t)}{i hbar} + \Psi(x, t + \Delta t) $

The function which is {\psi} at the initial time can then be factored out of this expression above such that:

$  \Psi(x, t + \Delta t) = (\frac{\Delta t \hat{H}}{i \hbar} + 1) \Psi(x, t)  $ 

This form allows for a new translation into the linear algebra that we've been using so far as well. The first half of the expression can simplify to ({i \hbar}* the Hamiltonian matrix which takes the second derivative of a different matrix * the identity matrix of the same dimensions as the Hamiltonian) all then multiplied by the original wavevector. These mathematical manipulations would then yield a new wavevector of the original wavevector at a different time - $ {\Psi (x, t + \Delta t)} $.




