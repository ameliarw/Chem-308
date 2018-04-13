[home](/README.md)
{% include mathjax.html %}

## Born-Oppenheimer Approximation

The Born-Oppenheimer Approximation states that because the mass of a nucleus is so much larger than the mass of an electron, on the time-scale of the motion of an electron, the nucleus can be treated as stationary. In reality, the nucleus is not stationary, but on the electron time-scale, the electron state does not change appreciably with the changing position of the nucleus. 

While it has been established that the electron state depends parametrically on the location of the nucleus, the Born-Oppenheimer Approximation allows for a simplification of the Hamiltonian describing the energy of an electron and two nuclei. 

The Hamiltonian to describe the overall system consisting of two different nuclei and one electron, an {H_2^+} system, can be broken down into two different functions - one that depends on the separation between the two nuclei, and one that depends on the distance of the electron from the nuclei. This electronic function will also depend parametrically on the nucleus-nucleus distance. 

The Hamiltonian to describe this system can be rewritten as a series of operators that describe the potential energy and kinetic energy of the nuclei and the electron: 


The Hamiltonian must describe both the translational motion of the electron and nuclei in the system as well as the potential interactions between them. 

The electronic function parametrically depends on the radius of the nuclei. 

The separation of variables allows for an approximation. 

By diving by psi * chi the functions which don't depend on r or R can then be canceled out and the expression can be simplified. The product rule can then be used to further simplify the expression of the kinetic energy of nuclei A and B by taking the second derivative of the functions. 

When everything is simplified down as much as possible, the end result is a total potential function which depends on both the repulsion of the two nuclei as well as the attraction between the nuclei and the electron. Gives rise to the shape of the potential energy function - 

![PE Graph](/bondenergy.GIF)

In the graph above, the total potential energy of a system is depicted by changing the internuclear distance. The graph can be thought of as  a collection of electronic energy calculations made by changing the position of the reduced mass of the nuclei and then adding an electron to the system and calculating the energy of the electron. By using the reduced mass of the nuclei, one nucleus can be thought of as stationary. The minimum energy depicted on the graph is reflective of the equilibrium bond length on the r axis and the energy of the bond on the E axis. The energy of the electron at these different nucelar positions ends up determining the total potential energy of the system. 

When the electronic energy is calculated, the total potential energy ends up being calculated. 



For example, consider $H_2^+$ shown in Fig.1 bellow. It is composed of three particles: 2 protons and 1 electrons. The Hamiltonian of the system is given by the sum of the kinetic energy and potential energy of each particle.

We can write the Hamiltonian as:

$\hat{H}=\hat{T}_{nuclear}+\hat{T}_{electron}+\hat{V}_{nuc-e}+\hat{V}_{nuc-nuc}$</p>

$=(\frac{-\hbar^2 }{2M_a}\nabla^2_a + \frac{-\hbar^2 }{2M_b}\nabla^2_b) + \frac{-\hbar^2 }{2M_e}\nabla^2_e + (\frac{-q^2}{4\pi \epsilon_0 r_a} + \frac{-q^2}{4\pi \epsilon_0 r_b})+ \frac{q^2}{4\pi \epsilon_0 R_{ab}}.$</p>

Therefore, the TISE is given by

$\hat{H}\Psi(r,R)=\xi \Psi(r,R)$</p>
so
$(\hat{T}_{nuclear}+\hat{T}_{electron}+\hat{V}_{nuc-e}+\hat{V}_{nuc-nuc})\Psi(r,R)=\xi \Psi(r,R).$</p>

To solve this TISE we need to resort once again to the separation of variables trick and let

$\Psi(r,R)=\psi(r;R)\chi(R),$</p>
where $\psi(r;R)$ means that $\psi$ is a function of $r$ and has $R$ as a parameter.

So the TISE becomes

$(\hat{T}_{nuc}+\hat{T}_{e}+\hat{V}_{nuc-e}+\hat{V}_{nuc-nuc})\psi(r;R)\chi(R)=\xi \psi(r;R)\chi(R),$</p>

such that

$\hat{T}_{nuclear}(\psi \chi)+\hat{T}_{electron}(\psi \chi)+\hat{V}_{nuc-e}(\psi \chi)+\hat{V}_{nuc-nuc}(\psi \chi)$</p>
  <p align="center">$=\xi \psi \chi.$</p>

Then dividing both sides by $\psi \chi$ we have

$\frac{\hat{T}_{nuclear}(\psi \chi)}{\psi \chi}+ \frac{\hat{T}_{electron}\psi}{\psi}+ \hat{V}_{nuc-e} +\hat{V}_{nuc-nuc} =\xi.$</p>

We can see that the first term should be the most challenging to deal with, so let’s start with it. We have 

 $\hat{T}_{nuclear}(\psi \chi)= (\frac{-\hbar^2 }{2M_a}\nabla^2_a + \frac{-\hbar^2 }{2M_b}\nabla^2_b) (\psi \chi) .$</p>

 $= \frac{-\hbar^2 }{2M_a}\nabla^2_a(\psi \chi) + \frac{-\hbar^2 }{2M_b}\nabla^2_b(\psi \chi) .$</p>

The two terms in the equation above are similar, so we can solve the first term and determine the second one by analogy.


$\frac{-\hbar^2 }{2M_a}\nabla^2_a(\psi \chi) = \frac{-\hbar^2 }{2M_a} \frac{\partial}{\partial R_a} (\frac{\chi \partial \psi}{\partial R_a} + \frac{\psi \partial \chi}{\partial R_a}) $</p>

 $= \frac{-\hbar^2 }{2M_a}[(\chi \frac{\partial^2 \psi}{\partial {R_a}^2}+\frac{\partial \psi}{\partial {R_a}}\frac{\partial \chi}{\partial {R_a}}) +  (\psi \frac{\partial^2 \chi}{\partial {R_a}^2}+\frac{\partial \psi}{\partial {R_a}}\frac{\partial \chi}{\partial {R_a}})] $</p>

Now comes the Born-Oppenheimer approximation. We know that the mass of the proton is 1836 times greater than that of the electron. Therefore, as the whole system (electron + two protons) move in space, the electron also moves relative to the center of mass of the system. We can then approximate that the rate of change of $\psi$ with respect to $R_a$ is insignificant. So that

 $\frac{\partial^2 \psi}{\partial {R_a}^2}= \frac{\partial \psi}{\partial {R_a}}=0 $.</p>

We then obtain

 $\frac{-\hbar^2 }{2M_a}\nabla^2_a(\psi \chi) = \frac{-\hbar^2 }{2M_a}\psi \frac{\partial^2 \chi}{\partial {R_a}^2} $.</p>

By analogy we also have 

$\frac{-\hbar^2 }{2M_b}\nabla^2_b(\psi \chi) = \frac{-\hbar^2 }{2M_b}\psi \frac{\partial^2 \chi}{\partial {R_b}^2}$. $</p>

Therefore, the TISE become

$\frac{\frac{-\hbar^2 }{2M_a} \frac{\partial^2 \chi}{\partial {R_a}^2}}{\chi} + \frac{\frac{-\hbar^2 }{2M_b} \frac{\partial^2 \chi}{\partial {R_b}^2}}{\chi} + \frac{\hat{T}_{e} \psi}{\psi} + \hat{V}_{nuc-e}+\hat{V}_{nuc-nuc} =\xi$.</p>

The TISE can be rewritten as 

 $(\frac{\hat{T}_{nuc} \chi}{\chi} + \frac{\chi}{\chi} \hat{V}_{nuc-nuc})+ (\frac{\hat{T}_{electron} \psi}{\psi} + \frac{\psi}{\psi} \hat{V}_{nuc-e})=\xi$.</p>

Call the second term $E_e$ and factor out the $\chi$ in the first term to obtain

$(\frac{\hat{T}_{nuc}}{\chi} + \frac{1}{\chi} \hat{V}_{nuc-nuc})\chi+ E_e=\xi$.</p>

Then multiply both sides by $\chi$ to obtain

$(\hat{T}_{nuc} + \hat{V}_{nuc-nuc})\chi + E_e \chi =\xi \chi$.</p>

This can be rewritten as 

 $\hat{T}_{nuc} \chi + (\hat{V}_{nuc-nuc}+E_e) \chi =\xi \chi$.</p>

Call the terms in parenthesis $ \hat{V}_{nuclear}$ to obtain

 $\hat{T}_{nuc} \chi + \hat{V}_{nuc} \chi =\xi \chi$.</p>
