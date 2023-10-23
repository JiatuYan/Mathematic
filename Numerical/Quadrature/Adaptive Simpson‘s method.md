Adaptive Simpson's method is a [[Adaptive quadrature]] method that use composite Simpson's rule to calculate the integral in each pieces of the interval.
A criterion for determining when to stop subdividing an interval is
$$\left\lvert S(a, m) + S(m, b) - S(a, b) \right\rvert < 15\epsilon. $$
where $[a, b]$ is an interval with midpoint $m=\frac{a+b}{2}$, while $S(a, b)$, $S(a, m)$, $S(m,b)$ given by Simpson's rule are the estimates of $\int_a^b f(x)\mathrm{d}x$, $\int_a^mf(x)\mathrm{d}x$ and $\int_m^b f(x)\mathrm{d}x$ respectively, and $\epsilon$ is the desired maximum error tolerance for the interval.
To perform adaptive Simpson's method, do the following: if$\left\lvert S(a, m) + S(m, b) - S(a, b)\right\rvert < 15\epsilon_i$ ($\epsilon_{i+1}=\epsilon_i/2$), add $S(a, m)$ and $S(m, b)$ to the sum of Simpson's rules which are used to approximate the integral, otherwise, perform the same operation with 
$$
\begin{align}
&\left\lvert S(a, \frac{m-a}{2}) + S(\frac{m- a}{2},m) - S(a, m)\right\rvert< 15\epsilon_{i+1},\\
&\left\lvert S(m, \frac{b -m}{2}) + S(\frac{b - m}{2}, b) - S(m, b)\right\rvert<15\epsilon_{i+1},\\
&\left\lvert S(a, m) + S(m, b) - S(a, b)\right\rvert<15\epsilon_i.
\end{align}$$