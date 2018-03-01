[home](/README.md)

### Change of Basis

In order solve the time-dependent Schrodinger equation, we will first use an "easy" basis, then change the basis such that the 
solution is in the basis we want. 

Take for example the Hamiltonian operator. As we've previously determined, using the eig function in matlab will generate a matrix consisting of eigenvectors in the position basis and a matrix with the eigenvalues (rememeber: eigenvalues have no basis). 

In order to describe a single quantum state, the matrix consisting of the eigenvectors in the position basis is multiplied by a vector in the energy basis which corresponds to the position you are trying to describe. Remember that quantum states as described in the energy basis are delta functions, so this vector will be composed of a single 1 in the position you are describing (ie, the first eigenvector) and zeros. The result of this multiplication is a single vector in the position basis which describes the desired eigenvectors. This is to say you've isolated a single quantum state and changed bases. 

$(\psi_n)_x=c_1{\begin{pmatrix} 1\\\ 0\\\ 0\\\ \vdots \end{pmatrix}}_x+c_2{\begin{pmatrix} 0\\\ 1\\\ 0\\\ \vdots \end{pmatrix}}_x+c_3{\begin{pmatrix} 0\\\ 0\\\ 1\\\ \vdots \end{pmatrix}}_x...+c_n{\begin{pmatrix} 0\\\ 0\\\ \vdots\\\ 1\end{pmatrix}}_x={\begin{pmatrix} c_1\\\ 0\\\ 0\\\ \vdots \end{pmatrix}}_x+{\begin{pmatrix} 0\\\ c_2\\\ 0\\\ \vdots \end{pmatrix}}_x+{\begin{pmatrix} 0\\\ 0\\\ c_3\\\ \vdots \end{pmatrix}}_x...+{\begin{pmatrix} 0\\\ 0\\\ \vdots\\\ c_n\end{pmatrix}}_x$
