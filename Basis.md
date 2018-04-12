{% include mathjax.html %}

[home](/README.md)


  
### Change of Basis

In linear algebra, a basis is defined a the set of vectors which spans a certain vector space. Each vector in the basis set by definition can be written as a linear combination of the other vectors present in the basis. When operators are represented as matrices, this matrix is also defined by a certain basis. When the operation matches the basis space of the matrix, we say that the matrix is in its native basis. For example, when the position operator is represented in position space, it is in its native basis. It is often useful to be able to move between bases, like from the position basis to the energy basis for example. Therefore, a method for tranforming elements in one basis to another basis is necessary. When solving the time-dependent Schrodinger equation, it is useful to begin in one basis and then change basis to gain more information about a particle's behavior. 

In order solve the time-dependent Schrodinger equation, we will first use an "easy" basis, then change the basis such that the 
solution is in the basis we want. 

Take for example the Hamiltonian operator. As we've previously determined, using the eig function in matlab will generate a matrix consisting of eigenvectors in the position basis and a matrix with the eigenvalues (rememeber: eigenvalues have no basis). 

In order to describe a single quantum state, the matrix consisting of the eigenvectors in the position basis is multiplied by a vector in the energy basis which corresponds to the position you are trying to describe. Remember that quantum states as described in the energy basis are delta functions, so this vector will be composed of a single 1 in the position you are describing (ie, the first eigenvector) and zeros. The result of this multiplication is a single vector in the position basis which describes the desired eigenvectors. This is to say you've isolated a single quantum state and changed bases. 

$$ {\begin{bmatrix} x_1 & 0 & 0 & \cdots \\\ 0 & x_2 & 0 & \cdots \\\ 0 & 0 & x_3 & \cdots\\\ \end{bmatrix}}X * {\begin{bmatrix} 1\\\ 0\\\ 0\\\ 0 \\\ \vdots \end{bmatrix}}E  = 
{\begin{bmatrix} x_1 \\\ 0 \\\ 0 \\\ \vdots \end{bmatrix}}X $$ 
 


