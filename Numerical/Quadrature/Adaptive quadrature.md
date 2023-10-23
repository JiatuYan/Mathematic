**Adaptive quadrature** is a numeric integration method in which the integral of a function $f(x)$ is approximated using static quadrature rules on adaptively refined subintervals of the region of integration. Generally, adaptive algorithms are just as efficient and effective as traditional algorithms for "well behaved" integrands, but are also effective for "badly behaved" integrands for which traditional algorithms may fail.

Adaptive quadrature follows the general scheme
1. procedure $\mathrm{integrate}(f, a, b, \tau)$
2. $Q\approx\int_a^b f(x)\mathrm{d}x$
3. $\epsilon\approx\lvert Q - \int_a^b f(x)\mathrm{d}x\rvert$
4. if $\epsilon > \xi$ then
	1. $m=(a+b)/2$
	2. $Q = \mathrm{integrate}(f, a, m, \tau/2) + \mathrm{integrate}(f, m, b, \tau/2)$
5. endif
6. return $Q$
If the estimated error is larger than the required tolerance $\tau$, the interval will be subdivied and the quature is applied on each piece of the divided intervals.

The important components are the quadrature rule itself
$$Q\approx\int_a^bf(x)\mathrm{d}x,$$
the error estimator
$$\epsilon\approx\left\lvert Q-\int_a^bf(x)\mathrm{d}x\right\rvert,$$
and the logic for deciding which interval to subdivide and when to terminate.