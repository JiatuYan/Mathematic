
# Control Function

We use Boussinesq Equations to discribe the evalution of internal waves:
$$
\begin{align}
\nabla\cdot\tilde{\mathbf{u}} &= 0, \tag{1a}\\
\frac{\partial \tilde{u}}{\partial \tilde{t}} + (\tilde{\mathbf{u}}\cdot\nabla)\tilde{\mathbf{u}} &=
 -\frac{1}{\rho_0}\nabla\tilde{p} + \frac{\tilde{\rho}}{\rho_0}\mathbf{g} + \nu\Delta\tilde{\mathbf{u}}, \tag{1b}\\
 \frac{\partial \tilde{\rho}}{\partial \tilde{t}}  + \tilde{\mathbf{u}}\cdot\nabla\tilde{p} +
  \tilde{w}\frac{\mathrm{d}\tilde{\rho}}{\mathrm{d}\tilde{z}}&=\kappa\Delta\tilde{\rho}\tag{1c}.\\
\end{align}
$$

^e98710

Substitute the variables by
$$
\mathbf{u} = \frac{\tilde{\mathbf{u}}}{U},\quad \mathbf{x}=\frac{\tilde{\mathbf{u}}}{L},\quad t = \frac{\tilde{t}}{L/U},\quad p = \frac{\tilde{p}}{\rho_0 U^2},\quad \rho = \frac{\tilde{\rho}}{L\lvert\mathrm{d}\tilde{\rho}/\mathrm{d}\tilde{z}\rvert}, \tag{2}
$$
where $U$ and $L$ are characteristic velocity and characteristic length, respectively, $\mathrm{d}\tilde{\rho}/\mathrm{d}\tilde{z}$ is the density's gradient, and we can get the dimentionless form of the equation [[Numerial Simulation of Moving Rigid Body in a Density Stratified Liquid#^e98710|(1)]]:
$$
\begin{align}
 \nabla\cdot\mathbf{u} &= 0,\tag{3a}\\
 \frac{\partial \mathbf{u}}{\partial t} + (\mathbf{u}\cdot\nabla)\mathbf{u} &= -\nabla p - \mathrm{Ri}\rho\hat{k} + \frac{1}{\mathrm{Re}}\Delta\mathbf{u},\tag{3b}\\
\frac{\partial \rho}{\partial t} + \mathbf{u}\cdot\nabla \rho - w &= \frac{1}{\mathrm{Pe}}\Delta \rho. \tag{3c}
\end{align}
$$
where $\mathbf{u}=(u, w)^T$ and $\hat{k}$ is a unit vector whose direction is vertically upward,
$\mathrm{Ri}$, $\mathrm{Re}$ and $\mathrm{Pe}$ are dimentionless constants called Richardson, Reynolds and Peclet number respectively.
The constants are
$$\mathrm{Ri}=(\frac{NL}{U})^2,\quad
\mathrm{Re}=\frac{LU}{\nu},\quad
\mathrm{Pr} = \frac{\nu}{\kappa},\quad
 \mathrm{Pe}=\mathrm{RePr},\tag{4}
$$
where
$$
N:=\sqrt{-\frac{g}{\rho_0}\frac{\mathrm{d}\bar{\rho}}{\mathrm{d}\tilde{z}}} \tag{5}
$$
is the bouyancy frequency.

# Domain and Boundary Conditions

In the oscillating cylinder experiment, a cylinder whose radius is $1\mathrm{cm}$ is oscillating in a $150\mathrm{cm}\times 50\mathrm{cm}$ rectangular domain.
The location of the center of the cylinder can be wrote by the following equation
$$
z(t) = A\sin(\omega t), \tag{6}
$$
where $z(t)$ is the vertical coordinate, $A$ is amplitude and $\omega$ is frequency.
No-slip condition is imposed at the four walls of the domain and the boundary of the cylinder.
$$
\begin{align}
  \mathbf{u} = 0,\quad \mathrm{on}\quad \partial\Omega_r\tag{7a}\\
  \mathbf{u} = \mathbf{v},\quad\mathrm{on}\quad\partial\Omega_s\tag{7b}\\
\end{align}
$$
where $\partial\Omega_r$ is the boundary of the rectangular domain and $\partial\Omega_s$ is the boundary of the moving cylinder, $\mathbf{v}$ is the velocity of the moving cylinder.

# Boussinesq Equations with GePUP Formulation

We can write the dimentionless Boussinesq equations with GePUP formulation:
$$
\begin{align}
  \frac{\partial \mathbf{w}}{\partial t} &= -(\mathbf{u}\cdot\nabla)\mathbf{u} - \mathrm{Ri}\rho\hat{k} - \nabla q + \frac{1}{\mathrm{Re}}\Delta \mathbf{w} &\mathrm{in}\ \Omega(t),\tag{8a}\\
  \frac{\partial\rho}{\partial t} &= -\mathbf{u}\cdot\nabla\rho + w + \frac{1}{\mathrm{Pe}}\Delta\rho &\mathrm{in}\ \Omega(t),\tag{8b}\\
\mathbf{u}&=\mathbf{w}=\mathbf{v} &\mathrm{on}\ \partial\Omega(t),\tag{8c}\\
\mathbf{u}&=\mathscr{P}\mathbf{w} &\mathrm{in}\ \Omega(t),\tag{8d}\\
\Delta q &= \nabla\cdot(-(\mathbf{u}\cdot\nabla)\mathbf{u} - \mathrm{Ri}\rho\hat{k})&\mathrm{in}\ \Omega(t),\tag{8e}\\
\mathbf{n}\cdot\nabla q &= \mathbf{n}\cdot\left(-\mathrm{Ri}\rho\hat{k} + \frac{1}{\mathrm{Re}}\Delta\mathbf{u} - \frac{1}{\mathrm{Re}}\nabla\nabla\cdot\mathbf{u}\right) - \mathbf{n}\cdot\frac{\mathrm{d} \mathbf{u}}{\mathrm{d}t}&\mathrm{on}\ \partial\Omega(t).\tag{8f}\\
\end{align}
$$

^17bf18

# Spatial Discretization

We use PLG-FVM to discretize the regular and irregular spatial differential operators in equation [[#^17bf18|(8a)]] and [[#^17bf18|(8b)]].
**Remark 1:** In moving boundary problems, we use Reynolds transport theorem
$$
\begin{align}
  \frac{\mathrm{d}}{\mathrm{d}t}\int_{\mathcal{V}_j(t)} p\ \mathrm{d}V = \int_{\mathcal{V}_j(t)}\frac{\partial\ p}{\partial t}\mathrm{d}V + \oint_{\partial \mathcal{V}_i(t)}(\mathbf{v}_b\cdot\mathbf{n})p\mathrm{d}V. \tag{9}
\end{align}
$$
 to derive the governing equations on staggered grid, where cell-averaged scalar and face-averaged vectors are stored.

Imposing Reynolds transport theorem and spatial discret operators, we can write equation [[#^17bf18|(8)]] into
$$
\begin{align}
  \frac{\mathrm{d}(\lVert \mathcal{V}_i(t)\rVert)\langle \mathbf{w}\rangle}{\mathrm{d}t}
  &= \lVert \mathcal{V}_i(t)\rVert\cdot\left(-\mathrm{Ri}\langle \rho\hat{\mathbf{k}}\rangle - \mathbf{C}\langle \mathbf{uu}\rangle - \mathbf{G}\langle q\rangle + \frac{1}{\mathrm{Re}}\mathbf{L}\langle\mathbf{w}\rangle\right) + \mathbf{f}(t, \mathbf{v}_b, \mathbf{w}),\tag{10a}\\
  \frac{\mathrm{d} \lVert \mathcal{V}_i(t)\rVert \langle \rho\rangle}{\mathrm{d}t} &=
  \lVert\mathcal{V}_i(t)\rvert\left(-\mathbf{A}\langle\mathbf{u}\rho\rangle + \langle u_1\rangle + \frac{1}{\mathrm{Pe}}\mathbf{L}\langle\rho\rangle\right) + \mathbf{f}(t, \mathbf{v}_b, \rho), \tag{10b}\\
  \langle\mathbf{w}\rangle _{\partial \mathcal{V}_i\cap\partial\Omega_s(t)} &=
    \langle\mathbf{v}_b\rangle_{\partial \mathcal{V}_i\cap\partial\Omega_s(t)} \tag{10c}\\
    \langle\mathbf{w}\rangle_{\partial \mathcal{V}_i\cap\partial\Omega_r(t)}
    &= 0 \tag{10d}\\
    \langle u\rangle& = \mathbf{P}\langle \mathbf{w}\rangle\tag{10e}\\
  \langle\mathbf{n\cdot \mathbf{u}}\rangle_{\partial \mathcal{V}_i\cap\partial\Omega(t)} &= 0\tag{10f}\\
   \mathbf{L}\langle q\rangle &= \mathbf{D}(-\mathbf{C}\langle \mathbf{uu}\rangle - \mathrm{Ri}\langle \rho\hat{\mathbf{k}}\rangle), \tag{10g}\\
  \langle\frac{\partial q}{\partial \mathbf{n}}\rangle_{\partial \mathcal{V}_i\cap\partial\Omega(t)}
  &= -\langle\mathbf{n\cdot \mathrm{Ri}\rho\hat{\mathbf{k}}}\rangle_{\partial \mathcal{V}_i\cap\partial\Omega(t)} + \frac{1}{\mathrm{Re}}\mathbf{NVS}\langle \mathbf{u}\rangle - \frac{1}{\mathrm{Re}} \mathbf{NG}\left( \mathbf{D}\langle \mathbf{u}\rangle\right)
  -\langle\mathbf{n}\cdot \frac{\mathrm{d}\mathbf{v}_b}{\mathrm{d}t}\rangle_{\partial \mathcal{V}_i\cap\partial\Omega(t)}\tag{10h}\\
\end{align}
$$

^59b139

where $\mathbf{u}=(u_0, u_1)^T$, $\lVert \mathcal{V}_i(t)\rVert$ is the volume of the control volume $\mathcal{V}_i(t)$, $\langle \cdot\rangle$ means cell average
, $\mathbf{C}$, $\mathbf{D}$ $\mathbf{L}$, $\mathbf{G}$ and $\mathbf{A}$ are discrete convection, divergence laplacian, gradient and advection operators, and
$$
\mathbf{f}(t, \mathbf{v}_b, *) = \oint_{\partial \mathcal{V}_i(t)} (\mathbf{v}_b\cdot \mathbf{n})*\mathrm{d}A. \tag{11}
$$
**Remark 2:** In the equations [[#^59b139|(10a)]] and [[#^59b139|(10b)]] the the evolving variables is saved as cell-integral, while we must change the varibles into cell-averaged one to impose spatial discrete operators first, then convert them into cell-integral form back again.

**Remark 3:** The boundary conditions(no-slip condition) [[#^59b139|(10c)]], [[#^59b139|(10d)]] and [[#^59b139|(10f)]] and the last term in [[#^59b139|(10h)]] are all known as a priori.

**Remark 4:** The last term in equations [[#^59b139|(10a)]] is calculated by the function `fillNetTransportation` in class `EmFuncFiller` while the last term in [[#^59b139|(10b)]] is calculated by the function `getNetTransportation` in class `ReynoldsTransport`.

# Temporal Integration

**Remark 5:** To avoid the discontinuity caused by sweeping through the cell's corner, we must merge the cells elaborately between each time steps. Obviously, the cells are merged in the same way in each middle stage. We assme discontinuity will not appear in each stage.

Classical Runge-Kutta method is used to calculate the temporal differentiation in equations [[#^59b139|(10a)]].
For each stage $s=1,\ldots,n_s$, we have
$$
\begin{align}
 &\lVert\mathcal{V}_i(t^{(s)})\rVert\langle \mathbf w\rangle^{(1)} = \lVert\mathcal{V}_i(t^{n})\rVert\langle\mathbf{w}\rangle^{n},\tag{11a}\\
 &\lVert\mathcal{V}_i(t^{(s)})\rVert\langle \rho\rangle^{(1)}
 =\lVert\mathcal{V}_i(t^{n})\rVert\langle \rho\rangle^{n},\tag{11b}\\
 &\left\{
 \begin{array}{l}
 \lVert\mathcal{V}_i(t^{(s)})\rVert\langle \mathbf{w}\rangle^{(s)}
 = \lVert\mathcal{V}_i(t_n)\rVert \langle\mathbf{w}\rangle^n + k\sum_{j=1}^{s-1} a_{s,j}\mathbf{Y}\left(\langle\mathbf{w}\rangle^{(j)}, \langle \mathbf{u}\rangle^{(j)},\langle \rho\rangle^{(j)}, t^{(j)}\right)\\
 \lVert\mathcal{V}_i(t^{(s)})\rVert\langle \rho\rangle^{(s)}
 = \lVert\mathcal{V}_i(t^{n})\rVert\langle \rho\rangle^n + k\sum_{j=1}^{s-1} a_{s,j}\mathbf{Z}\left(\langle\mathbf{u}\rangle^{(j)}, \langle\rho\rangle^{(j)}, t^{(j)}\right),
 \end{array}
 \right. \tag{11c}\\
&\left\{
\begin{array}{l}
  \lVert\mathcal{V}_i(t^{n})\rVert\langle \mathbf{w}\rangle^{*}
 = \lVert\mathcal{V}_i(t_n)\rVert \langle\mathbf{w}\rangle^n + k\sum_{j=1}^{n_s} b_j\mathbf{Y}\left(\langle\mathbf{w}\rangle^{(j)}, \langle \mathbf{u}\rangle^{(j)},\langle \rho\rangle^{(j)}, t^{(j)}\right)\\
 \lVert\mathcal{V}_i(t^{n})\rVert\langle \rho\rangle^{n}
 = \lVert\mathcal{V}_i(t^{n})\rVert\langle \rho\rangle^n + k\sum_{j=1}^{n_s} b_j\mathbf{Z}\left(\langle\mathbf{u}\rangle^{(j)}, \langle\rho\rangle^{(j)}, t^{(j)}\right),
 \end{array}
 \right.\tag{11d}\\
 &\langle \mathbf{u}\rangle^{n+1} = \langle \mathbf{w}\rangle^{n+1},\tag{11e}\\
 &\langle \mathbf{w}\rangle^{n+1} = \langle \mathbf{u}\rangle^{n+1},\tag{11f}\\
\end{align}
$$
where
$$
\begin{align}
 \mathbf{Y}\left(\langle\mathbf{w}\rangle^{(j)}, \langle \mathbf{u}\rangle^{(j)},\langle \rho\rangle^{(j)}, t^{(j)}\right) &= \lVert \mathcal{V}_i(t^(j))\rVert\cdot\left(-\mathrm{Ri}\langle \rho^{(j)}\hat{\mathbf{k}}\rangle - \mathbf{C}\langle \mathbf{u^{(j)}u^{(j)}}\rangle - \mathbf{G}\langle q^{(j)}\rangle + \frac{1}{\mathrm{Re}}\mathbf{L}\langle\mathbf{w}^{(j)}\rangle\right) + \mathbf{f}(t^{(j)}, \mathbf{v}_b^{(j)}, \mathbf{w}^{(j)}),\tag{12a}\\
 \mathbf{Z}\left(\langle\mathbf{u}\rangle^{(j)}, \langle\rho\rangle^{(j)}, t^{(j)}\right) &= \lVert\mathcal{V}_i(t^{(j)})\rvert\left(-\mathbf{A}\langle\mathbf{u}\rho\rangle^{(j)} + \langle u_1\rangle^{(j)} + \frac{1}{\mathrm{Pe}}\mathbf{L}\langle\rho\rangle^{(j)}\right) + \mathbf{f}(t^{(j)}, \mathbf{v}_b^{(j)}, \rho^{(j)}),
 \end{align}
$$
