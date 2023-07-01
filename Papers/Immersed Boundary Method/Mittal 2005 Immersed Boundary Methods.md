Consider the simulation of flow past a solid body shown in figure below.
![[ImmsedBoundary 1.png]]
The model equations are
$$
\begin{equation}
\begin{split}
\frac{\partial \mathbf{u}}{\partial t} + \mathbf{u}\cdot\nabla\mathbf{u} + \frac{1}{\rho}\nabla p - \frac{\mu}{\rho}\nabla^2 \mathbf{u} = 0\\
\nabla\cdot \mathbf{u} = 0\qquad \mathrm{in}\ \Omega_f
\end{split}
\end{equation}\tag{1}
$$
$$
\mathrm{with}\ \mathbf{u} = \mathbf{u}_{\Gamma}\qquad \mathrm{on}\ \Gamma_b. \tag{2}
$$
The system above can be rewrote as
$$
\begin{equation}
\begin{split}
\mathcal{L}(\underline{U}) = 0\qquad\mathrm{in}\ \Omega_f\\
\underline{U} = \underline{U}_{\Gamma}\qquad\mathrm{on}\ \Omega_b,
\end{split}
\end{equation}\tag{3}
$$
where $\underline{U}=(\mathbf{u}, b)$ and $\mathcal{L}$ is the operator representing the Navier-Stokes equations.

In an IB method, equation(1) would be discretized on a nonbody conformal Cartesian grid and the boundary condition would be imposed indirectly through modification of Equation(3). The modification takes the form of a source term ( or forcing function) in the governing equations. The forcing function can be implemented in two different ways.
# Continuous forcing approach
In this approach, forcing function, denoted by $\underline{f}_b$ is included into the continuous governing equation(3) leading to the equation $\mathcal{L}(\underline{U})=\underline{f}_b$, which then applies to the entire domain $(\Omega_f + \Omega_g)$.
In this approach, the forcing function  is formulated independent of the underlying spatial discretization.

Among existing methods in this category, elastic and rigid boundaries require different treatments.
## Flows with elastic boundaries
The coupled simulation of blood flow and muscle contraction in a beating heart is suitable to be simulated as flows with immersed elastic boundaries.
In Peskin(1972, 1981), the fluid flow is governed by INSE and is solved on stationary Cartesian grid. The immersed boundary is represented by a set of elastic fibers and the locations of these fibers is tracked in a Lagrangian fashion by a collection of massless points that move with the local fluid velocity.

# Discrete forcing approach
In this approach the governing equations are first discretized on a Cartesian grid without regard to the immersed boundary, resulting in the set of discretized equations $[L]\{\underline{U}\} = 0$. Following this, the discretization in the cells near the IB is adjusted to account for its presence, resulting in a modified system of equations $[L]\{\underline{U}\}=\{\underline{r}\}$, which are then solved on the Cartesian grid.
**<big>Remark</big>**: PLG algorithm can be viewed as this approach
Discrete forcing approach can be categorized into those that are formulated so as to impose the boundary condition on the immersed boundary through indirect means and those that directly impose the boundary conditions on the IB.