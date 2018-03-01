{% include mathjax.html %}

[home](/README.md)

## Summary of Key Quantum Ideas
-----
A wavefunction provides the complete description of a quantum state. We will begin to use state vectors as the complete description of a quantum state in order to organize this information and manipulate it using linear algebra. In order to determine different qualities of a wavefunction, or state vector, an operation must be performed. Operating on wavefunction yields an observable, or a value specific to that quantum state. Different operators provide different information - there are operators for position, momentum, energy, etc. 


##### How can the energy of a quantum state be determined?
The Hamiltonian operator is composed of both the kinetic energy and potential energy operator. In simplified models, like the one-dimensional particle in a box model, the potential energy of the box is generally set to zero while there is infinite potential energy out of the box - this is to say that the particle exists in a well of infinite potential. 

![Particle in a Box Model](/img53.png)

##### The Hamiltonian operator operating on an eigenfunction will yield the energy of that quantum state multiplied by the original eigenfunction:

$$
\hat{H}\Psi = i \hbar\frac{\partial{\Psi}}{\partial t}
$$

The Hamiltonian operator is the combination of the kinetic energy and the potential energy and provides the total energy of a system. 
This expression is also called the Time Independent Schrodinger Equation. Note that this expression only depends on position, not time. 

- The solutions to the Schrodinger, or the set of eigenvalues can be represented by $ {E_n} $. This set is the complete list of possible total energy measurement results. 

- If two operators do not commute, then they do not share the same set of eigenfunctions. This is also to say that they do not have the same basis.


##### All operators we use are hermitian
Hermitian operators produce real eigenvalues. A hermitian matrix has a defining property where the complex conjugate is equal to the complex conjugate transpose. A complex conjugate transpose is the original matrix with the rows now serving as the columns and the columns serving as the rows, and any complex components of the matrix are replaced with $ -i = -\sqrt{-1} $. 

##### Quantum states are linear combinations of states
In the linear algebra representation of quantum states, different vectors combine to form each eigenstate. Here's a graphical representation of this concept, where vector $\vec{w}$ can be written as a linear combination of vectors $\vec{u}$ and $\vec{v}$:

![Combination](/34.gif)

This concept is depicted more generally by this equation, where the ${c}$ refers to the coefficient, or the contribution of each vector state, ${p}$, to the overall state, ${psi}$: 

$$ \eqalign{ \vec{\psi} &= \sum_{j}c_{j}\vec{p_{j}}\ &= c_{1}\vec{p_{1}} + c_{2}\vec{p_{2}}+ \ldots \ 

##### Functions as eigenfunction
An operator performs a certain operation on a function. As we've previously mentioned, this could range from multiplying a function by a variable, like the position operator, or taking the second derivative of a function, like the Hamiltonian operator. Operators can only operate on functions which are eigenfunctions for the operator. For a wavefunction to be an eigenfunction of an operator, the operation must return the original function multiplied by a scalar multiple. This scalar multiple is the eigenvalue of that operator and the observable value that we are trying to find. 

More concisely put: 
$$ {\begin{equation}\label{eig} \{omega}\{psi}=\lambda_i \{psi} \end{equation} $$

Where ${omega}$ is an operator, ${psi}$ is an eigenfunction, and ${lambda}$ is an observable. This expression can be translated into matrixes and vectors using linear algebra. 

# Linear Algebra Translation

##### Operators as Matrices
Operators now become matrices when using linear algebra to gain information about quantum states. The expression above can be modified slightly: 
$$ {\begin{equation}\label{eig} \mathbf{O}\vec{v_i}=\lambda_i \vec{v_i} \end{equation} $$

Where {O} is a matrix, {vec{v_i}} is an eigenvector, and ${lambda}$


The Hamiltonian operator combines the potential energy of a certain quantum state with the kinetic energy of a state, and this operation can be done using calculus: 
$$
\hat{H} = \frac{-hbar^2}{2m}\frac{\partial^2}{\partial x^2} + {V(x)}
$$


Using linear algebra, we can construct a matrix that will similarly take the second derivative of another matrix. We can then combine this kinetic energy matrix with the potential energy to form the Hamiltonian operator in the form of a matrix: 
```Matlab
Vvec = zeros(pts, 1
Vvec([1:w, end - (w-1):end]) = barht;
%We created a vector of zeros, but we just set the first three and the last three entries (because w=3) equal to some barht (large number, using 1e6) to model the infinite potential well

%Now we create the potential energy matrix but putting the entries of Vvec in a diagonal matrix
V = diag(Vvec);

%making the second derivative matrix
D2 = (1/(dx^2))*(-2*eye(pts) + diag(ones(pts-1,1), 1) + diag(ones(pts-1,1),-1));

%now account for the delta x idea by subtracting the first element from the second element because they will be evenly spaced, and multiply the matrix by the constants 
T = (-hbarsq/(2*m))*D2;

%here's our Hamiltonian, which accounts for both the potential energy and kinetic energy
H= T + V;
```

##### Eigenfunctions = Eigenvectors
Vectors can now be used to hold the same information that eigenfunctions hold. The basis of a vector will matter tremendously. Choosing to express a vector in a different basis has the potential to simplify it greatly. For example, if the energy of the second eigenvector of the particle in a box model is found and presented in the energy basis, the vector $$\vec{\v}$$ would be:

$|v>=\begin{bmatrix} 0 \\\ 1 \\\ \vdots \\\ 0 \end{bmatrix}


##### Inner product vs. Matrix multiplication
We will use both operations to manipulate our matrices and vectors, but the inner product of two vectors is quite different than the multiplication of two vectors. For our purposes, we are considering column or row vectors. 

The inner product is the sum of each entry in one vector multiplied by the corresponding entry of a different vector. This manipulation results in a scalar. To get the inner product, a row vector is multiplied by a column vector, and these two vectors must have the same number of entries. 

$={\begin{bmatrix} v_{1} & v_{2} & ... & v_{n} \end{bmatrix}}^* \begin{bmatrix} w_{1} \\\ w_{2} \\\ \vdots \\\ w_{n} \end{bmatrix}=\sum_{n=1}^{n}v_i ^*w_i $.

When two vectors are multplied, a new square matrix of the same dimensions (if the two vectors have the same number of entries) is generated with each entry in this new vector being the product of the corresponding entries of the two initial vectors. This outer product is generated by multiplying a column vector by a row vector. The order of this multiplication does matter. 

$\begin{bmatrix} w_{1} \\\ w_{2} \\\ \vdots \\\ w_{n} \end{bmatrix}^*{\begin{bmatrix} v_{1} & v_{2} & ... & v_{n} \end{bmatrix}}$

##### Vector Normalization
We want to work with vectors which have a length of 1 - this is to say that the vector is normalized. We can normalize a vector by dividing that vector by its own length:
\begin{equation} \vec{v_norm} = \frac{\vec{v}}{\parallel\vec{v}\parallel} \end{equation}


[home](/README.md)

