---
layout: page-en
title: NUMERICAL CODES
permalink: /codes/en/
order: 6
---

This page summarizes numerical codes and research software that I make publicly available.

## spectral-noisy-coupled-burgers-1d

[spectral-noisy-coupled-burgers-1d](https://github.com/nakano35255/spectral-noisy-coupled-burgers-1d) is a C++ solver for one-dimensional multi-component noisy coupled Burgers equations.

The code solves conservative stochastic partial differential equations of the form

$$
\partial_t \phi^\alpha
+ \sum_\beta A_{\alpha\beta}\partial_x\phi^\beta
- \sum_\beta D_{\alpha\beta}\partial_x^2\phi^\beta
+ \sum_{\beta,\gamma}H^\alpha_{\beta\gamma}\partial_x(\phi^\beta\phi^\gamma)
=
\sum_\beta B_{\alpha\beta}\partial_x\xi^\beta .
$$

Spatial derivatives are evaluated with a Fourier spectral method, and nonlinear terms are computed by a pseudospectral method with 3/2 padding. The solver supports conservative noise, nonlinear mode coupling, restart output, and several observables designed for fluctuating hydrodynamics and KPZ universality.

A distinctive feature of the code is that simulations are controlled by a LAMMPS-like `input.script`. This makes it easy to run different one-dimensional multi-component fluctuating hydrodynamic equations within the same framework. The Fourier spectral discretization also enables high-accuracy evaluation of spatial derivatives.

In particular, the code includes measurements of height fluctuation moments, skewness, excess kurtosis, Fourier-mode correlations, and time correlations. These observables are useful for testing KPZ/NFH scaling predictions directly from numerical simulations, and the code is designed so that new observables can be added without rewriting the solver core.

The examples demonstrate, among others,

* comparison with finite-size exact results for the fluctuating advection-diffusion equation,
* demonstration that height fluctuations in the one-component noisy Burgers equation approach the GOE Tracy-Widom-type distribution of the KPZ universality class, following settings such as Oliveira, Ferreira, and Alves, [Phys. Rev. E 85, 010601 (2012)](https://doi.org/10.1103/PhysRevE.85.010601),
* reproduction of recent work on how height fluctuations in a two-component coupled Burgers equation are related to exact results for the KPZ equation, following De Nardis, Gopalakrishnan, and Vasseur, [Phys. Rev. Lett. 131, 197102 (2023)](https://doi.org/10.1103/PhysRevLett.131.197102).

The repository is intended not only as a time-evolution solver, but also as a reproducible numerical framework: it includes input scripts, analysis scripts, and representative figures for comparing simulations with theoretical predictions.

**Links**

* GitHub repository: [spectral-noisy-coupled-burgers-1d](https://github.com/nakano35255/spectral-noisy-coupled-burgers-1d)
* Documentation: [README](https://github.com/nakano35255/spectral-noisy-coupled-burgers-1d/blob/main/README.md), [WIKI](https://github.com/nakano35255/spectral-noisy-coupled-burgers-1d/blob/main/WIKI.md)
* Examples: [examples directory](https://github.com/nakano35255/spectral-noisy-coupled-burgers-1d/tree/main/examples)

## spectral-scalar-fluctuating-hydrodynamics-1d

I am planning to release another numerical code for more complex fluctuating hydrodynamic equations, restricted to one-component fields.

The target equations include conservative stochastic partial differential equations for a one-component scalar density field $\rho(x,t)$, such as

$$
\frac{\partial \rho(x,t)}{\partial t}
=
\frac{\partial}{\partial x}
\left[
D(\rho)\frac{\partial \rho}{\partial x}
\right]
-
\frac{\partial}{\partial x}
\left[
M(\rho)\frac{\partial^3 \rho}{\partial x^3}
\right]
-
\frac{\partial}{\partial x}
\left[
v(x)A(\rho)
\right]
+
\frac{\partial}{\partial x}
\left[
\sqrt{2\sigma(\rho)}\,\xi(x,t)
\right].
$$
