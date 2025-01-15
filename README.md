# 2D_Dynamic_simualation of Jack in the box.

This code is the final project for ME-314 Machine Dynamics course at Northwestern University.<br>
For more details visit: [Portfolio Post](https://sayantani-bhattacharya.github.io/posts/my-second-post/)

## Dynamic modelling: 

 
### Euler-Lagrange Equation:  

Considering uniform mass distribution in both box and jack, I calculate the kinetic and potential energy at the centroid (geometric center of the two rectangles). And Lagrangian as kinetic minus the potential energy of the two bodies. Using the Euler lagrange formula to get the equations of motion, by equating it to the external force applied on both the rigid bodies. 

### External force: 

The box is supposed to vibrate and have some degree of gravity compensation, so I have given the external force in y as 4*M_box*g  [ M_box*g : is the force due to gravity, and 4 is a tunable parameter, could be any hard-set value, but its easier to reference wrt to gravitational force, so used this.] And the external force on theta is a sinusoidal function, to generate an oscillation/ vibration like motion. And there is no external force to jack (it has potential component, but that is internal). 

### Impact conditions: 

There are 16 impact conditions in this model. Which is that every 4 point of the jack coming in contact with any of the box’s walls. Which basically means that the x component of transform (between corner and wall) for Wall 1 and 3 and y coordinate for Wall 2 and 4, should be less than a threshold value. Value should not be kept 0, as in simulation, till the 0 transform is actually achieved the animation would have stepped outside the box, as it is a bit coarsely discrete system. Also, this threshold value can be tuned. And I used it to detect the impact occurrence and calling the impact update function. 

### Impact update procedure: 

To find the state of the system after impact, we solve six conservation of momentum equations and one Hamiltonian conservation equation. We have 7 variables (lambda, and six state variables [q]) and 7 equations. And I used this to generate the trajectory after every impact. 

### Simulation Behavior Analysis: 

In the attached video, it is visible that when any of the four corners of the jack comes in contact with any of the four walls of the box [ i.e. impact condition is met], the jack bounces off the wall and keeping the speed of jack same, as I am assuming elastic collision [ i.e. following the impact update rule].  

Also, the external force ensures the box does not free fall under gravity. If you uncomment the external force section, this behavior can be seen in the simulation as well. Also, as a sanity check, one may uncomment impact equations, and it would be observed that, both the bodies would have free fall decoupled from each other.

