# Modeling the Born-Oppenheimer Approximation

We can use potential energy hypersurfaces, or a two-dimensional simplification of the potential energy of a system, to better understand molecular dynamics. We've modeled a potential energy hypersurface that considers the nucleus-nucleus interactions and the nucleus-electron interactions, as previously discussed on the [Born-Approximation page](/bo.md). Initially, we begin with a LEPS potential energy surface, named for London-Erying-Polanyi-Sato, to model the dynamics of the reaction: 
$A + B_C /right arrow A-B + C$ 

![pewell](/pewell.gif)
This potential energy surface has a saddle point near the point where the reaction goes the completition, and this saddle point indicates the distance between AB and BC where the nucleus-nucleus interactions and nucleus-interactions are the most stabilizing. The well climbs steeply near r = 0 for both AB and BC because the repulsive nucleus-nucleus interactions are highly unfavorable. 

We constrain the dimensions of this reaction such that everything interacts in a co-linear fashion. The radius between A and B and B and C are plotted which allows us to understand how A is moving relative to BC. The velocity of AB can be thought of as the translational motion of BC, as BC and A approach each other, and the velocity of BC can be thought of as the initial vibrational motion of the bond between BC. Different parameters are changed in order to determine how the translational and  vibrational velocities and the starting positions of A and BC affect the reaction outcome. 

Reaction Conditions: 
- Velocity of AB  = -4.93
- Velocity of BC = -3
- AB distance = 3.75
- BC distance = 0.85
![reaction](/reaction.gif)

In the simulation above, the velocities, both translational and vibrational, are high enough and the starting points allow the reaction to have the correct phase in order to successfully overcome the activation energy needed for the reaction to occur.  The distance between BC fluctuates as the bond length oscillates, and the distance between A and B decreases as A approaches BC. The reaction does occur, and ultimately the distance between A and B fluctuates with the new bond length oscillation, and the distance between B and C increases as AB moves farther from C.   

When the velocity of A relative to B is changed, the 

-4.93 -1
![-4.93-1](/-4.93-1.png)

-4.93 -4.93
![-4.93-4.93](/-4.93-4.93.png)

-5 -3
![5.53](/5.53.gif)

-3 -3 
![-3-3](/33.gif)

-6 -3
![-6-3](/-6-3.png)

CHANGING THE INITIAL POSITION
Velocity of AB -4.93
Velocity of BC -3
AB distance 3.5
BC distance 0.85
![abcphase](/abcphase.gif)

LENNARD-JONES POTENTIAL 

Velocity of AB -1.5
Velocity of BC -0
AB distance 3.9
BC distance 1.1
![LJnorxn](/ljno.gif)

![ljwell](/ljwell.gif)
