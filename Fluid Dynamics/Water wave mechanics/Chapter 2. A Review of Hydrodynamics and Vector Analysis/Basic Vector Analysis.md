We consider in a three-dimension Cartesian coordinate system. For example, the vector $\mathbf{a}$ can be represented as 
$$
\mathbf{a} = a_x\mathbf{i} + a_y\mathbf{j} + a_z\mathbf{k},
$$
where $a_x$, $a_y$ and $a_z$ are the projections of $\mathbf{a}$ on the $x$, $y$ and $z$ axes.

# 1. The Dot Product
The dot product is defined as
$$
\mathbf{a}\mathbf{b} = \lvert \mathbf{a}\rvert\lvert \mathbf{b}\rvert\cos(\theta) = a_xb_x+a_yb_y+a_zb_z.
$$

# 2. The Cross Product
The cross product is a **vector quantity** which is defined as $\mathbf{a}\times \mathbf{b}=\lvert\mathbf{a}\rvert\lvert\mathbf{b}\rvert\sin(\theta)$. We can write it into Einstein Summation form:
$$
\mathbf{a}\times \mathbf{b} = \epsilon_{ijk}a_jb_k\mathbf{e}_i
$$

# 3. The  Gradient
The gradient is written as $\nabla T$ and can be further broken down to
$$
\nabla T = \left(\mathbf{i}\frac{\partial}{\partial x} + \mathbf{j}\frac{\partial}{\partial y} + \mathbf{k}\frac{\partial}{\partial z}\right) T(x, y, z).
$$
The gradient always indicates the direction of maximum change of a scalar field and can be used to indicate perpendicular, or normal, vectors to a surface.

# 4. The Divergence
If the vector differential operator is applied to a vector using a dot product rather thant to a scalar, as in the gradient, we have the divergence
$$
\nabla\cdot \mathbf{a} = \frac{\partial a_x}{\partial x} + \frac{\partial a_y}{\partial y} + \frac{\partial a_z}{\partial z}.
$$

Del squared ($\nabla^2$) is known as the Laplacian operator, where 
$$
\nabla\cdot\nabla T = \nabla^2 T.
$$
# 5. The Curl
If the vector differential operator is applied to a vector using the cross product, the the **curl** of the vector results.
$$
\nabla\times \mathbf{a} = \epsilon_{ijk}\frac{\partial a_k}{\partial x_j}\mathbf{e}_i
$$
The curl of a velocity vector is a measure of the rotation in the velocity field.

The divergence of a curl of $\mathbf{a}$ is identity for any vector that has continuous first and second derivatives:
$$
\nabla\cdot\nabla\times\mathbf{a} = \frac{\partial}{\partial x_i}\epsilon_{ijk}\frac{\partial a_k}{\partial x_j}\mathbf{e}_i = 0.
$$
# 6. Line Integrals
We denote the integral from $P_0$ to $P_1$ of the projection of the vector $\mathbf{a}$ on the contour line $C_1$ as $F$:
$$
F = \int_{P_0}^{P_1}\mathbf{a}\cdot \mathrm{d}l
$$

# 7. Velocity Potential

^9c8253

Let us consider a vector velocity $\mathbf{u}$ and define the value of the line integral of $\mathbf{u}$ as $-\phi$:
$$
-\phi = \int_{C}\mathbf{u}\cdot \mathrm{d}\mathbf{l} = \int_{C}(u\mathrm{d}x + v\mathrm{d}y + w\mathrm{z}).
$$
The quantity $\mathbf{u}\cdot\mathrm{d}\mathbf{l}$ is a measure of the fluid velocity in the direction of thecontour at each point. Therefore, $-\phi$ is related to the product of the velocity and length along the path between the two point $P_0$ and $P_1$. The minus sing is a matter of definitional convenience.

For the value of $\phi$ to be independent of path, that is, for the flow rate between $P_0$ and $P_1$ to be the same no matter how the integration is carried out, the terms in the integral must be an exact differential $\mathrm{d}\phi$, and therefore
$$
\begin{align}
u &= -\frac{\partial \phi}{\partial x},\\
v &= -\frac{\partial \phi}{\partial y},\\
w &= -\frac{\partial \phi}{\partial z}.\\
\end{align}
$$
To ensure that this scalar function $\phi$ exists, the curl of the velocity vector must be zero:
$$
\nabla\times \mathbf{u} = 0.
$$
(or the equality $\nabla\times\nabla\phi = 0$ will induce a contradiction).

The velocity vector $\mathbf{u}$ can therefore be conveniently represented as
$$
\mathbf{u} = -\nabla\phi.
$$
That is, we can express the vector quantity by the gradient of a scalar function $\phi$ for a flow with no vorticity. Further $\mathbf{u}$ flows "downhill", that is, in the direction of decreasing $\phi$.

Let us examine more closely the line integral of the velocity component along the contour. If we consider the closed path from $P_0$ to $P_1$ and then back again, we know, from before, that the integral is zero.
$$
\oint \mathbf{u}\cdot\mathrm{d}\mathbf{l} = 0,
$$
which means that if, for example, the path taken from $P_0$ to $P_1$ and back agian were circular, no fluid would travel this circular path. Therefore, we expect no rotation of the fluid in circles if the curl of the velocity vector is zero.(Refer to [[Stokes Theorem|Stokes theorem]]).

For an inviscid and incompressible fluid, where the Euler equations are valid, there are only normal stresses(pressure) acting on the surface of a fluid particle; since the shear stresses are zero, there are no stresses to impart a rotation on a fluid particle. Therefore, in an inviscid fluid, a nonrotating particle remains nonrotating. However, if an initial vorticity exists in the fluid, the vorticity remains constant. To see this, we write the Euler equations in vector form:
$$
\frac{\mathrm{D}\mathbf{u}}{\mathrm{D}t} = -\frac{1}{\rho}\nabla p - g\mathbf{k}.
$$
Taking the curl of this equation and substituting $\nabla\times \mathbf{u} = \omega$ and $\nabla\times\nabla p = 0$, we have
$$
\frac{\mathrm{D}\omega}{\mathrm{D} t} = 0.
$$
Therefore, there can be no change in the vorticity or the rotation of the fluid with time.

# 8. Stream Function

^dd1b99

Let us define the line integral composed of the velocity component perpendicular to the line element in two dimensions.
$$
\psi = \int_{P_0}^{P_1}\mathbf{u}\cdot\mathbf{n}\mathrm{d}l,
$$
where $\mathrm{d}l = \lvert \mathrm{d}\mathbf{l}\rvert$. Consideration of the integrand above will demonstrate that $\psi$ represents the amount of fluid crossing the line $C$ between points $P_0$ and $P_1$.

Independence of path requires 
$$
w = \frac{\partial \psi}{\partial x}\qquad u =- \frac{\partial\psi}{\partial z}.
$$Thus the condition for it is 
$$
\frac{\partial w}{\partial z} + \frac{\partial u}{\partial x} = 0,
$$
there is the two-dimensional form of the continuity euqation.

In general, there can be no stream function for three-dimensional flows, with the exception of axisymmetric flows. However, the velocity potential exists in any three-dimensional flow that is irrotational.

# 9. Streamline
A streamline is defined as a line that is everwhere trangent to the velocity vector.

In two dimensional flows, the gradient of $\psi$ is perpendicular to the streamlines and in the direction normal to the velocity vector along a streamline.

# 10. Relationship between velocity potential and stream function
For a three-dimensional flow, the velocity field may be determined from a velocity potential $\phi$ if the fluid is irrotational. For some three-dimensional flows and all two-dimensional flows for which the fluid is incompressible, a strema function $\psi$ exists. Each is a measure of the flow rate between two points: in either the normal  or transverse direction. For two-dimensional incompressible fluid flow, which is irrotational, both the stream function and the velocity potential exist and must be related throught velocity components.

The streamline, or line of constant stream function, and the lines of constant velocity potential are perpendicular, as can be seen from the fact that their gradients are perpendicular:
$$
\nabla\phi\cdot\nabla\psi= 0.
$$

We have
$$
\begin{align}
u &= -\frac{\partial\phi}{\partial x} = -\frac{\partial\psi}{\partial z},\\
w &= -\frac{\partial\phi}{\partial x} = \frac{\partial\psi}{\partial z}.\\
\end{align}
$$
These relationships are called the Cauchy-Riemann conditions.







