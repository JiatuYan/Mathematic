At any boundary, whether it is fixed, 
  such as the bottom, or free, 
  such as the water surface 
  which is free to deform under the influence of forces, 
  certain physical conditions must be satisfied by the fluid velocities.
# Kinematic boundary conditions

^6b8448

The conditions on the water particle kinematics are called **kinematic boundary conditions**.
At any surface or fluid interface, 
  it is clear that there must be no flow accross the interface.

The mathematical expression
  for the kinematic boundary condition
  may be derived from
  the equation 
  which describes the surface 
  that constitutes the boundary.
Any fixed or moving surface 
  can be expressed in  terms of
   a mathematical expression of the form $F(x, y, z, y) = 0$.
If the surface varies with time, 
  as would the water surface,
  then the total derivative of  the surface
  with respect to time would be zero on the surface.
In other words, if we move with the surface, it does not change.
$$
\frac{\mathrm{D}F(x, y, z, t)}{\mathrm{D}t} = 0 = \left.\frac{\partial F}{\partial t} + u\frac{\partial F}{\partial x} + v\frac{\partial F}{\partial y} + w\frac{\partial F}{\partial z}\right\rvert_{\mathrm{on}\ F(x, y, z, t) = 0}
$$
or
$$
-\frac{\partial F}{\partial t} = \mathbf{u}\cdot \nabla F = \mathbf{u}\cdot\mathbf{n}\lvert\nabla F\rvert,
$$
where the unit vector normal to the surface has been introduced as $\mathbf{n} = \nabla F/\lvert\nabla F\rvert$.

Rearranging the kinnematic boundary condition results:
$$
\mathbf{u}\cdot\mathbf{n}=\frac{-\partial F/\partial t}{\lvert\nabla F\rvert}\qquad \mathrm{on}\ F(x, y, z, t) = 0,
$$
where
$$
\lvert \nabla F\rvert = \sqrt{\left(\frac{\partial F}{\partial x}\right)^2 + \left(\frac{\partial F}{\partial y}\right)^2 + \left(\frac{\partial F}{\partial z}\right)^2}
$$

This condition requires that
  the component of the fluid velocity normal to the surface
  be related to the local velocity of the surface.
If the surface does not change with time, then $\mathbf{u}\cdot \mathbf{n} = 0$;
  that is, the velocity component normal to the surfaceis zero.

## The Bottom Boundary Condition(BBC)

^0efc03

In general, the lower boundary of our region of interest
  is described as $z=-h(x)$ 
  for a two-domensional case
  where the origin is located at the still water level
  and $h$ represents the depth.
If the bottom is impermeable, 
  we expect that $\mathbf{u}\cdot\mathbf{n}=0$,
  as the bottom does not move with time.

The surface equation for the bottom is
  $F(x, z) = z + h(x) = 0$.
Therefore,
$$
\mathbf{u}\cdot\mathbf{n} = 0,
$$
  where 
$$
\mathbf{n} = \frac{\nabla F}{\lvert \nabla F\rvert} = \frac{\frac{\mathrm{d}h}{\mathrm{d} x}\mathbf{i} + 1\mathbf{k}} {\sqrt{\left(\mathrm{d}h/\mathrm{d}x\right)^2 + 1}}.
$$
Carrying out the dot product 
  and multiplying through by the square root,
  we have
$$
u\frac{\mathrm{d}h}{\mathrm{d}x}  + w = 0\qquad \mathrm{on}\ z = -h(x),
$$
  or 
$$
w = -u\frac{\mathrm{d}h}{\mathrm{d}x}\qquad \mathrm{on}\ z = -h(x).  
$$

## Kinematic Free Surface Boundary Condition(KFSBC). 

^ff35da

The free surface of a wave 
  can be described as $F(x, y, z, t) = z - \eta(x, y, t)=  0$,
  where $\eta(x, y, t)$ is the displacement 
  of the free surface about the horizontal plane, $z=0$.
The **kinematic boundary condition** at the free surface is
$$
\mathbf{u}\cdot\mathbf{n} 
= \frac{\partial{\eta}/\partial t}{\sqrt{\left(\partial \eta/\partial x\right)^2 + \left(\partial \eta/\partial y\right)^2+1}}
\qquad \mathrm{on}\ z=\eta(x, y, t).
$$

# Dynamic Free Surface Boundary Condition.

^bed3ed

A distinuighing feature of fixed (in space) surfaces
  is that they can support pressure variations.
However, surfaces that are "free",
  such as the air-water interface,
  cannot support variations in pressure (neglecting surface tension)
  across the interface
  and hence must respond 
  in order to maintain the pressure as uniform.
A second boundary condition,
  termed a **dynamic boundary condition**,
  is thus required on any free surface or interface,
  to describe the pressure distribution on this boundary.
An interesting effect 
  of the displacement of the free surface
  is that the position of the upper boundary
  is not know a priori in the water wave problem.
This aspect causes considerable difficulty
  in the attemp to obtain accurate solutions
  that apply for large wave heights.

As the dynamic free surface boundary condition 
  is a requirement 
  that the pressure on the free surface boundary condition
  be uniform along the wave form, 
  the Bernoulli equation with $p_{\eta}=constant$ 
  is applied on the free surface, $z=\eta(x, t)$,
$$
-\frac{\partial \phi}{\partial t} + \frac{1}{2}\left(u^2 + w^2\right) + \frac{p_{\eta}}{\rho} + gz=C(t),
$$
  where $p_{\eta}$ is a constant 
  and usually taken as gage pressure, $p_{\eta} =0$.

## Conditions at "Responsive" Boundaries.
In the case of wind blowing
  across a water surface and generating waves,
  if the pressure relationship were know,
  the Bernoulli equation would serve 
  to couple that wind field 
  with the kinematics of the wave.
1. The wave and wind field would be interdependent
      and the wave motion would be termed **"coupled"**.
2. If the wave were driven by,
      but did not affect the applied surface pressure,
      this would be a case of **"forced"** wave motion
      and again the Bernoulli equation would serve
      to express the boundary condition.
3. For the simpler case 
      that is explored in some detail in this chapter,
      the pressure will be considered to be uniform
      and hence a case of **"free"** wave motion exists.

If the wave length are very short (on the order of several centimeters),
  the surface is no longer "free".
Although the pressure is uniform above the water surface,
  as a result of the surface curvature,
  a nonuniform pressure will occur within the water
  immedirately below the surface film.

For cases in which surface tension forces are important,
  the dynamic free surface boundary condition is modified to
$$
-\frac{\partial\phi}{\partial t} + \frac{p_{\eta}}{\rho} - \frac{\sigma'}{\rho}
\frac{\partial^2\eta}{\partial x^2} + \frac{1}{2}\left[\left(\frac{\partial\phi}{\partial x}\right)^2 + \left(\frac{\partial\phi}{\partial z}\right)^2\right] + gz = C(t),\qquad z = \eta(x, t),
$$
  where $\sigma'$ is the coefficient of surface tension.
The equation above is of use 
  in examination of capillary water waves.

## Lateral Boundary Conditions
The boundary conditions for the bottom and upper surfacces have been discussed.
In order to complete specification of the boundary value problem,
  conditions must also be specified on the remaining lateral boundaries.

If the wavers are propagating in one direction (say the $x$ direction),
  conditions are two-dimensional 
  and then "no-flow" conditions are appropriate
  for the velocities in the $y$ direction.
The boundary conditions to be applied
  in the $x$ direction
  depend on the problem under consideration.
For example, in the classical wavemaker problem, 
  the wave motion results from a prescribed disturbance of
  an object at $x=0$.

Take the following figure as an example.
![[wavemaker.png]]
Consider a vertical paddle acting as a wavemaker in a wave tank.
If the displacement of the paddle
  may be described as $x=S(z, t)$, 
  the [[#^ff35da|kinematic boundary condition]] is 
$$
\mathbf{u}\cdot\mathbf{n} = \frac{\partial S(z, t)}{\partial t}\bigg/\sqrt{1 + \left(\frac{\partial S}{\partial z}\right)^2},
$$
  where
$$
\mathbf{n} = \frac{1\mathbf{i} - \frac{\partial S}{\partial z}\mathbf{k}}{\sqrt{1 + \left(\partial S/\partial z\right)^2}}.
$$
This requires that the fluid particles at the moving wall follow the wall.
Two different conditions occur
  at the other possible lateral boundaries:
  at a fixed beach as shown at the right side of the figure(a) above,
  where a [[#^0efc03|kinematic condition]] would be applied,
  or as in the figure(b),
  where a "radiation" boundary condition is applied
  which requires that only outgoing waves occur at infinity.
