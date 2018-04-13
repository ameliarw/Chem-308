[home](/README.md)
{% include mathjax.html %}

# Modeling the Born-Oppenheimer Approximation 

We can use potential energy hypersurfaces, or a two-dimensional simplification of the potential energy of a system, to better understand molecular dynamics. We've modeled a potential energy hypersurface that considers the nucleus-nucleus interactions and the nucleus-electron interactions, as previously discussed on the [Born-Approximation page](/bo.md). Initially, we begin with a LEPS potential energy surface, named for London-Erying-Polanyi-Sato, to model the dynamics of the reaction: 
$A + BC \rightarrow AB + C$ 

## Early Barrier
This is the early barrier potential energy hypersurface. The reactants are higher energy than the products, and thus the reaction is more thermodynamically favorable and is exergonic. 
![pewell](/pewell.gif)

This potential energy surface has a saddle point near the point where the reaction goes the completition, and this saddle point indicates the distance between AB and BC where the nucleus-nucleus interactions and nucleus-electron interactions are the most stabilizing. The well climbs steeply near r = 0 for both AB and BC because the repulsive nucleus-nucleus interactions are highly unfavorable. The well plateaus at increasing radii because the attractive nucleus-electron interactions become weaker at increasing distances. 

We constrain the dimensions of this reaction such that everything interacts in a co-linear fashion. The radius between A and B and B and C are plotted which allows us to understand how A is moving relative to BC. The velocity of AB can be thought of as the translational motion of BC, as BC and A approach each other, and the velocity of BC can be thought of as the initial vibrational motion of the bond between BC. Different parameters are changed in order to determine how the translational and  vibrational velocities and the starting positions of A and BC affect the reaction outcome. 

Parameters: 
- Velocity of AB  = -4.93
- Velocity of BC = -3
- AB distance = 3.75
- BC distance = 0.85

![reaction](/reaction.gif)

In the simulation above, the velocities, both translational and vibrational, are high enough and the starting points allow the reaction to have the correct phase in order to successfully overcome the activation energy needed for the reaction to occur.  The distance between BC fluctuates as the bond length oscillates, and the distance between A and B decreases as A approaches BC. The reaction does occur, and ultimately the distance between A and B fluctuates with the new bond length oscillation, and the distance between B and C increases as AB moves farther from C.   

#### Changing BC velocity 

When the velocity of B relative to C is changed, the reaction no longer occurs. A and BC get closer to each other, as depicted by the position components graph, but the energy of the system is not enough for the reaction to occur. 

Parameters: 
- Velocity of AB  = -4.93
- Velocity of BC = -1
- AB distance = 3.75
- BC distance = 0.85

![-4.93-1](/-4.93-1.png)


Increasing the velocity of B relative to C, however, changes the reaction outcome. When the vibrational energy of BC is increased, the reaction occurs. The increased energy due to this vibrational energy could explain why the reaction occurs.

Parameters: 
- Velocity of AB  = -4.93
- Velocity of BC = -4.93
- AB distance = 3.75
- BC distance = 0.85

![-4.93-4.93](/-4.93-4.93.png)

#### Changing AB velocity 
Changing the translational velocities of A in respect to BC will also affect to outcome of the reaction. Again, if A does not have enough translational energy, the reaction will not occur, as depicted in the first animation. The second animation describes the situation when the translational energy of A is increased, and the reaction does indeed occur.
Parameters: 
- Velocity of AB  = -3
- Velocity of BC = -3
- AB distance = 3.75
- BC distance = 0.85

![-3-3](/33.gif)

Parameters: 
- Velocity of AB  = -6
- Velocity of BC = -3
- AB distance = 3.75
- BC distance = 0.85

![5.53](/5.53.gif)

##### Changing Intial Position
Changing the initial position of the reactants also has an impact on the reaction dynamics. If the reactants don't reach the point of the reaction at the proper place on the potential energy hypersurface, the reaction will not continue. Changing the starting position of the reactants shifts the phase of the vibrational motion, and thus changing the starting position can affect whether or not the reaction occurs. When the AB distance is decrease, ie. BC shifts to the left, the reaction does not occur. 
Parameters:
Velocity of AB -4.93
Velocity of BC -3
AB distance 3.5
BC distance 0.85
![abcphase](/abcphase.gif)

## Late Barrier 
The late barrier conditions describe a reaction where the energy of the reactants is lower than that of the products. This is to say that the reaction is endergonic and thus requires additional energy to occur. The initial velocities of the reactants and the products must be larger in this potential energy hypersurface in order for the reaction to occur. This idea is depicted in the animation below, where the intial velocity of AB is -5.5 and the initial BC velocity is -5. Decreasing either velocity will cause the reaction to no longer occur. Increasing the distance between A and BC initially, as in shifting over the starting position of A causes no reaction. Decreasing this distance between A and BC by shifting the starting position of A to the left results in a reaction where A and BC go to AB and C. 

![Late](/late.gif)

# Lennard-Jones Potential 
A different potential energy hypersurface can also be used to model the potential energy of a system. The Lennard-Jones potential is modeled after non-reactive species like nobel gases and takes into account the atttractive long-range forces as well as the repulsive forces due to overlapping orbitals. The Lennard-Jones potential is defined by the depth of the potential well, the equilibrium bond length, and the distance between the two nuclei. No matter which parameters are chosen, this reaction will not occur due to the shape of the Lennard-Jones potential. 

Parameters: 
- Velocity of AB -1.5
- Velocity of BC -0
- AB distance 3.9
- BC distance 1.1


![LJnorxn](/ljno.gif)

![ljwell](/ljwell.gif)
