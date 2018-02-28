{% include mathjax.html %}

[home](/README.md)

## Summary of Key Quantum Ideas
-----
A wavefunction provides the complete description of a quantum state. We will begin to use state vectors as the complete description of a quantum state in order to organize this information and manipulate it using linear algebra. In order to determine different qualities of a wavefunction, or state vector, an operation must be performed. Operating on wavefunction yields an observable, or a value specific to that quantum state. Different operators provide different information - there are operators for position, momentum, energy, etc. 


##### How can the energy of a quantum state be determined?
The Hamiltonian operator is comprised of both the kinetic energy and potential energy operator. In simplified models, like the one-dimensional particle in a box model, the potential energy of the box is generally set to zero while there is infinite potential energy out of the box - this is to say that the particle exists in a well of infinite potential. 

![Particle in a Box Model](/img53.png)

##### The Hamiltonian operator operating on an eigenfunction will yield the energy of that quantum state multiplied by the original eigenfunction:

$$
\hat{H}\Psi = i \hbar\frac{\partial{\Psi}}{\partial t}
$$

The Hamiltonian operator is the combination of the kinetic energy and the potential energy and provides the total energy of a system. 
This expression is also called the Time Independent Schr"{o}dinger Equation. Note that this expression only depends on position, not time. 

- The solutions to the Schr"{o}dinger, or the set of eigenvalues can be represented by $ {E_n} $. This set is the complete list of possible total energy measurement results. 

- If two operators do not commute, then they do not share the same set of eigenfunctions. This is also to say that they do not have the same basis.


##### All operators we use are hermitian
Hermitian operators produce real eigenvalues. A hermitian matrix has a defining property where the complex conjugate is equal to the complex conjugate transpose. A complex conjugate transpose is the original matrix with the rows now serving as the columns and the columns serving as the rows, and any complex components of the matrix are replaced with $ -i = -\sqrt{-1} $. 

##### Quantum states are linear combinations of states
In the linear algebra representation of quantum states, different vectors combine to form each eigenstate. Here's a graphical representation of this concept, where vector $\vec{w}$ can be written as a linear combination of vectors $\vec{u}$ and $\vec{v}$:

![Combination](/34.gif)

This concept is depicted more generally by this equation, where the {c} refers to the coefficient, or the contribution of each vector state, {p}: 
$$ \eqalign{ \vec{\psi} &= \sum_{j}c_{j}\vec{p_{j}}\ &= c_{1}\vec{p_{1}} + c_{2}\vec{p_{2}}+ \ldots \ &= \langle \vec{p_{1}}, \vec{\psi}\rangle \vec{p_{1}} + \langle \vec{p_{2}}, \vec{\psi}\rangle \vec{p_{2}}+ \ldots }$$






