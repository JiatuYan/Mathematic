With the assumption of irrotational motion, a [[Basic Vector Analysis#^9c8253|velocity potential]] exists. Combining with incompressible condition, we  have
$$
\nabla\cdot\mathbf{u} = \nabla\cdot\nabla\phi = \nabla^2\phi = 0.
$$
In addition, for flows that are nondivergent and irrotational, the Laplace equation also determines the [[Basic Vector Analysis#^dd1b99| stream function]](nondivergent condition for two dimensions guarantees the existence and Laplacian equation determines the velocity). Substituting the velocity into the irrotationality condition yields the Laplacian equation for the stream function:
$$
\nabla^2\psi = \frac{\partial }{\partial x}\frac{\partial \psi}{\partial x} + \frac{\partial }{\partial z}\frac{\partial \psi}{\partial z}= \frac{\partial}{\partial x} w - \frac{\partial}{\partial z} u = 0,
$$
where the second step is from the condition for indenpendence of path of [[Basic Vector Analysis#^dd1b99| stream function]] and the last one is from irrotationality condition.
If the motion had been rotational the governing equation would be 
$$
\nabla^2\psi = \omega,
$$
where $\omega$ is the vorticity.

A few comments on the [[Basic Vector Analysis#^9c8253|velocity potential]] and the [[Basic Vector Analysis#^dd1b99|stream function]] may help in obtaining a better understanding for later applications:
1. The [[Basic Vector Analysis#^9c8253|velocity potential]] can be defined for both two and three dimensions, whereas the definition of the [[Basic Vector Analysis#^dd1b99|stream function]] is such that it can only be defined for three dimensions if the flow is symmetric about an axis(mathematically two-dimensional). It therefore follows that the stream function is of greatest use in cases where the wave motion occurs in one plane.
2. The Laplace equation is linear. Therefore, we can add and subtract solutions to build up solutions applicable for different problems of interest.