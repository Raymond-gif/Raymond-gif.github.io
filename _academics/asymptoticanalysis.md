---
title: "Asymptotic Analysis "
excerpt: "For certain differential equations, it can be difficult or even impossible to find an analytical solution. When this is the case, asymptotic analysis techniques can help approximate solutions."
author_profile: false
layout: splash
image: /images/friedrich1.png
caption: 
header:
  overlay_color: "#2a4d8f"   
  hero_title: "Asymptotic Analysis"
---

## Rotary Viscous Coupling

<p align="center">
  <img src="/images/rotaryviscouscoupling.jpg" alt="Diagram for Rotary Coupling" width="45%">
  <img src="/images/rotaryviscousgraph.png" alt="Rotary Coupling Graph" width="45%">
  <br>
  <em>Figure: (Left) Diagram for Rotary Coupling. (Right) Rotary Coupling Graph.</em>
</p>

### Full Governing Equation

$$\begin{equation*}
    \dfrac{\partial}{\partial r} \left[ \dfrac{1}{r} \dfrac{\partial}{\partial r} (r u_\theta)\right] + \dfrac{\partial^2 u_\theta}{\partial z^2} = 0 
\end{equation*}$$

Boundary Conditions: 

$$\begin{align*}
    u_\theta(r,z=0) &= 0 \\
    u_\theta(r,z=h)&= r \Omega \\
    u_\theta (r=R,z)&=0
\end{align*}$$

Let's introduce nondimensional variables, 

$$\begin{equation*}
    r^* = \dfrac{r}{R}, \quad z^*= \dfrac{z}{h}, \quad u_\theta^* = \dfrac{u_\theta}{R \Omega}, \quad \varepsilon = \dfrac{h}{R}
\end{equation*}$$

so that the governing differential equation becomes, 

$$\begin{equation}
    \varepsilon^2 \dfrac{\partial }{\partial r^*} \left[ \dfrac{1}{r^*} \dfrac{\partial}{\partial r^*} (r^* u_\theta^*)\right] + \dfrac{\partial^2 u_\theta^*}{\partial z^{* 2}}=0
    \label{rotaryviscousdiffeq}
\end{equation}$$

and the boundary conditions transform to,

$$\begin{align*}
    u_\theta^* (r^*,z^*=0) &= 0 \\
    u_\theta^* (r^*, z^*=1) &= r^* \\
    u_\theta^* (r^*=1,z^*) &= 0 
\end{align*}$$

### Outer Section

If the gap width is small compared to the radius, then \\( \varepsilon \to 0 \\) and the first term in Eq. \ref{rotaryviscousdiffeq} disappears, leaving 

$$\begin{equation*}
    \dfrac{\partial^2 u_\theta^*}{\partial z^2} = 0
\end{equation*}$$

<p> This solution can only satisfy the first two boundary conditions and is not valid for the region near the wall (where \( u_\theta^*=0 \) at \( r^*=1 \) ), and thus is called the <strong> outer solution </strong>. </p>

$$\begin{equation*}
    \boxed{u_{\theta, \text{outer}}^* = r^* z^*}
\end{equation*}$$

### Inner Section

For the inner solution, we scale y differently. We expect y to scale with the gap width, or \\( h \\). Basically, we are zooming in on the region near the wall. 

$$\begin{equation}
    y^* = \dfrac{y}{h} = \dfrac{R-r}{h} = \dfrac{1-r^*}{\varepsilon}
    \label{yrstarepsilon}
\end{equation}
$$

Eq. \ref{rotaryviscousdiffeq} transforms to, 

$$\begin{equation*}
    \dfrac{\partial}{\partial y^*} \left\{ \dfrac{1}{1 - \varepsilon y^*} \dfrac{\partial}{\partial y^*} \bigg[ (1-\varepsilon y^*) u_\theta^* \bigg]\right\} + \dfrac{\partial^2 u_\theta^*}{\partial z^{* 2}}=0
\end{equation*}$$

As \\( \varepsilon \to 0 \\), the differential equation for the inner solution is, 

$$\begin{equation*}
    \dfrac{\partial^2 u_\theta^*}{\partial y^{* 2}} + \dfrac{\partial^2 u_\theta^*}{\partial z^{* 2}}=0
\end{equation*}$$

$$\begin{align}
    u_\theta^*(y^*, z^*=0) &= 0 \label{utheta1}\\
    u_\theta^*(y^*, z^*=1) &= 1 \label{utheta2}\\
    u_\theta^*(y^*=0,z^*) &= 0 \label{utheta3}\\
    u_\theta^*(y^* \to \infty,z^*) &=u^*_{\theta, \text{outer}} (r^*=1, z^*) = z^* \label{utheta4}
\end{align}$$

Solving this involves the **separation of variables** technique.

$$\begin{equation*}
    u_\theta^* = F(y^*) G(z^*)     
\end{equation*}$$

Plugging this into the differential equation, 

$$\begin{align*}
    F''(y^*) G(z^*) + F(y^*) G''(z^*) & = 0 \\
    \dfrac{F''(y^*)}{F(y^*)} = - \dfrac{G''(z^*)}{G(z^*)} &= \lambda
\end{align*}
$$

The problem is now separated into two ordinary differential equations. 

Let's focus on \\( G \\) first. 

The \\( G \\) differential equation to be solved is, 

$$\begin{equation*}
    G''(z^*) + \lambda G(z^*) = 0, \quad G(0) =0, \quad G(1) = 0
\end{equation*}$$

The general solution is, 

$$\begin{equation*}
    G(z^*) = C_1 \cos \left(z^* \sqrt{\lambda} \right) + C_2 \sin \left( z^* \sqrt{\lambda }\right) 
\end{equation*}
$$

Plugging in the boundary conditions,

$$\begin{align*}
    G(0) &= C_1 =0 \\
    G(1) &= C_2 \sin \left( \sqrt{\lambda}\right) = 0 
\end{align*}$$

In order for a non-trivial solution to exist, we require that \\( \sin \left( \sqrt{\lambda} \right) =0 \\) or \\( \sqrt{\lambda} = \pi n \\).

The eigenfunctions are thus, 

$$\begin{equation*}
    \boxed{G_n(z^*) = \sin (\pi n z^*)}
\end{equation*}$$

Focusing on the \\( F \\) solution now. 

$$\begin{equation*}
    F''(y^*) - \lambda F(y^*) = 0
\end{equation*}$$

$$\begin{equation*}
    F(y^*) = \cancel{C_1 e^{y^* \sqrt{\lambda}}} + C_2 e^{-y^* \sqrt{\lambda}}
\end{equation*}$$

$$\begin{equation*}
    \boxed{F(y^*) = e^{-\pi n y^*}}
\end{equation*}$$

So right now, we have 

$$\begin{equation*}
    u_\theta^* = \sum_n^\infty C_n e^{-\pi ny^*} \sin (\pi n z^*)
\end{equation*}
$$

To satisfy boundary condition \ref{utheta2} and \ref{utheta4}, we add \\( z^* \\) to the solution. Think of it as the particular solution. 

$$\begin{equation*}
    u_\theta^* = z^* + \sum_n^\infty C_n e^{-\pi ny^*} \sin (\pi n z^*)
\end{equation*}$$

Now, it's time to plug in boundary condition Eq. \ref{utheta3}.

$$\begin{align*}
    u_\theta^*(y^*=0,z^*) = z^* + \sum_n^\infty C_n \sin (\pi n z^*) &= 0 \\
    \sum_n^\infty C_n \sin (\pi n z^*) &= -z^*
\end{align*}$$

Using Fourier analysis,

$$\begin{align*}
    C_n = 2 \int\limits_0^1 -z^* \sin (n \pi z^*) \, dz^* = \dfrac{2}{\pi} \dfrac{(-1)^n}{n}
\end{align*}$$

$$\begin{equation*}
    u_{\theta, \text{ inner}}^* = z^* + \dfrac{2}{\pi}  \sum_n^\infty \dfrac{(-1)^n}{n} e^{-\pi ny^*} \sin (\pi n z^*) 
\end{equation*}$$

Substituting the equation for \\( y^* \\), Eq. \ref{yrstarepsilon},

$$\begin{equation*}
    \boxed{    u_{\theta, \text{ inner}}^* = z^* + \dfrac{2}{\pi}  \sum_n^\infty \dfrac{(-1)^n}{n} \text{exp} \left[ -{\dfrac{\pi n (1-r^*)}{\varepsilon}} \right] \sin (\pi n z^*) }
\end{equation*}$$

Form the composite solution,

$$\begin{equation*}
    u_{\theta , \text{ composite}}^* = u_{\theta, \text{ inner}}^* + u_{\theta, \text{ outer}}^* - \underbrace{u_{\theta, \text{ common}}^*}_{z^*}
\end{equation*}$$

Substituting,

$$\begin{equation*}
    \boxed{ u_{\theta , \text{ composite}}^* = r^*  z^* + \dfrac{2}{\pi}  \sum_n^\infty \dfrac{(-1)^n}{n} \text{exp} \left[ -{\dfrac{\pi n (1-r^*)}{\varepsilon}} \right] \sin (\pi n z^*) }
\end{equation*}$$

## Wavy Wall Analysis

<p align="center">
  <img src="/images/wavywalldiagram.jpg" alt="Diagram of Wavy Wall" width="50%">
</p>
<p align="center"><strong>Figure:</strong> Diagram of Wavy Wall</p>


Consider potential flow over a wavy wall defined by the equation,

$$ \begin{equation}
    \hat{y}_w = h \sin \left( \dfrac{2 \pi}{\lambda} \hat{x} \right)
    \label{walldimension}
\end{equation} $$

We introduce the nondimensional variables, 

$$ \begin{equation*}
    \varepsilon = \dfrac{h}{\lambda}, \quad x = \dfrac{\hat{x}}{\lambda}, \quad y = \dfrac{\hat{y}}{\lambda}, \quad u=\dfrac{\hat{u}}{U_\infty}, \quad v = \dfrac{\hat{v}}{U_\infty}, \quad \phi = \dfrac{\hat{\phi}}{U_\infty \lambda}
\end{equation*} $$

Eq. \ref{walldimension} is turned into, 

$$ \begin{align*} 
    y_w &= \varepsilon \sin (2 \pi x) \\
    \dfrac{d y_w}{dx} &= 2 \pi \varepsilon \cos (2 \pi x)
\end{align*} $$

<div class="equation-box">
  <h3>Wavy Wall Governing Equation</h3>
  <div>

The wavy wall potential flow is governed by Laplace's equation, 

$$ \begin{equation*}
    \dfrac{\partial^2 \phi}{\partial x^2 } + \dfrac{\partial^2 \phi}{\partial y^2} = 0 
\end{equation*} $$

With boundary conditions,

$$ \begin{align}
    \phi_x(x,y \to \infty) &= 1 \label{BC1wavy}\\
    \dfrac{v(x,y_w)}{u(x,y_w)} = \dfrac{\phi_y (x,y_w)}{\phi_x (x,y_w)} = \dfrac{dy_w}{dx} &= 2 \pi \varepsilon \cos (2 \pi x) \label{BC2wavy}
\end{align} $$

  </div>
</div>

Now, let's begin the asymptotic analysis. We assume that \\( \phi \\) is equal to an asymptotic series, 

$$ \begin{equation*}
    \phi = \phi^0 + \varepsilon \phi^1
\end{equation*} $$

Laplace's equation becomes, 

$$ \begin{equation*}
    \boxed{\bigg[\phi^0_{xx} + \phi^0_{yy} \bigg] + \varepsilon \bigg[ \phi^1_{xx} + \phi^1_{yy} \bigg] = 0}
\end{equation*} $$

Both \\( \phi^0 \\) and \\( \phi^1 \\) must satisfy Laplace's equation.

### Transforming the Boundary Conditions

First, we transform the first boundary condition, Eq. \ref{BC1wavy}.

$$ \begin{equation*}
    \phi_x^0 (x, y \to \infty) + \varepsilon \phi_x^1 (x, y \to \infty) = 1 
\end{equation*} $$

$$ \begin{equation*}
    \boxed{\phi_x^0 (x, y \to \infty)= 1, \quad \phi_x^1 (x,y \to \infty)= 0}
\end{equation*} $$

Now, we transform boundary condition, Eq. \ref{BC2wavy}, 

$$ \begin{equation}
    \bigg[ 2 \pi \varepsilon \cos (2 \pi x)\bigg] \bigg[ \phi_x^0 (x,y_w) + \varepsilon \phi_x^1 (x,y_w)\bigg] - \bigg[ \phi_y^0 (x,y_w) + \varepsilon \phi_y^1 (x,y_w) \bigg] = 0 
    \label{rllylongBC}
\end{equation} $$

We perform a Taylor series expansion on each of the \\( \phi \\) terms around \\( y=0 \\), neglecting second-order terms. 

$$ \begin{equation*}
    \phi_x^0 (x,y_w) = \phi_x^0 (x,0) + \phi_{xy}^0 (x,0) y_w
\end{equation*} $$

Eq. \ref{rllylongBC} becomes, 

$$ \begin{align*} 
    \bigg [ 2 \pi \varepsilon \cos (2 \pi x)\bigg] \bigg[ \phi_x^0 (x,0) &+ \phi_{xy}^0 (x,0) y_w + \varepsilon \phi_x^1 (x,0) + \varepsilon \phi _{xy}^1 (x,0) y_w\bigg] \\
    &- \bigg[ \phi_y^0 (x,0) + \phi_{yy}^0 (x,0) y_w + \varepsilon \phi_y^1 (x,0) + \varepsilon \phi_{yy}^1 (x,0) y_w\bigg] = 0
\end{align*} $$

Expanding and grouping in terms of \\( \varepsilon \\),

$$ \begin{align*} 
    -\phi_y^0 (x,0) + \bigg[ 2 \pi \cos (2 \pi x) \phi_x^0 (x,0) - \phi_{yy}^0 (x,0) \sin (2 \pi x) - \phi_y^1 (x,0) \bigg] \varepsilon + O(\varepsilon^2) = 0
\end{align*} $$

Set the coefficients in front of \\( \varepsilon \\) and \\( \varepsilon^0 \\) equal to zero. The boundary conditions are, 

$$\boxed{\begin{aligned}
    \phi_y^0 (x,0) &= 0 \\
    \phi_y^1 (x,0) &= 2 \pi \cos (2 \pi x)  \phi_x^0 (x,0) - \sin (2 \pi x) \phi_{yy}^0 (x,0) 
\end{aligned}} $$

In summary, we now have two decoupled partial differential equations that we can solve, 

$$ \begin{align*} 
    \dfrac{\partial^2 \phi^0}{\partial x^2} + \dfrac{\partial^2 \phi^0}{\partial y^2} &= 0 \\
    \phi_y^0 (x,0) &= 0 \\
    \phi_x^0 (x, y\to \infty) &= 1 
\end{align*} $$

$$ \begin{align*} 
    \dfrac{\partial^2 \phi^1}{\partial x^2} + \dfrac{\partial^2 \phi^1}{\partial y^2} &= 0 \\
    \phi_x^1 (x,y \to \infty) &= 0 \\
    \phi_y^1 (x, 0) &= 2 \pi \cos (2 \pi x) 
\end{align*} $$

By inspection, the solution to the first system is, 

$$ \begin{equation*}
    \phi^0 (x,y) = x
\end{equation*} $$


And the second solution is accomplished by separation of variables,

$$ \begin{equation*}
    \phi^1 (x,y) = - e^{-2 \pi y} \cos (2 \pi x)
\end{equation*} $$

Put together, the solution is, 

$$ \begin{equation*}
    \boxed{\phi = x - \varepsilon e^{-2 \pi y} \cos (2 \pi x)}
\end{equation*} $$

The velocities: 

$$ \begin{align*} 
    u &= 1 + 2 \pi \varepsilon e^{-2 \pi y} \sin (2 \pi x) \\
    v &= 2 \pi \varepsilon e^{-2 \pi y} \cos (2 \pi x) \\
    V = \sqrt{u^2 + v^2} &= \sqrt{1 + 4 \pi \varepsilon e^{-2 \pi y} \sin (2 \pi x) + 4 \pi^2 \varepsilon^2 e^{-4 \pi y}} 
\end{align*} $$

The pressure coefficient: 

$$ \begin{equation*}
    C_p = 1 - V^2 = -4 \pi \varepsilon e^{-2 \pi y} \sin (2 \pi x) + O(\varepsilon^2)
\end{equation*} $$

At the wall, the important quantities are, 

$$ \begin{align*} 
    C_{p, \text{ wall}} &= -4 \pi \varepsilon \sin (2 \pi x) \\
    V_{\text{wall}}&= \sqrt{1 + 4 \pi \varepsilon \sin (2 \pi x) + 4 \pi^2 \varepsilon^2}
\end{align*} $$

<p align="center">
  <img src="/images/wavywallstreamlines.png" alt="Streamlines of Wavy Wall" width="45%">
  <img src="/images/velocityandpressureforwavywall.png" alt="Velocity and Pressure Distribution for Wavy Wall" width="45%">
</p>
<p align="center"><strong>Figure:</strong> Streamlines, Velocity, and Pressure Distribution for Wavy Wall</p>


## Singular Perturbation: Friedrich's Problem 1

Suppose that the differential equation that we want to solve is, 

<div class="equation-box">
  <div>

$$ \begin{align}
    \varepsilon \dfrac{d^2 u}{d y^2} + \dfrac{du}{dy} &= - \dfrac{3}{2} (1-3 \varepsilon) e^{-3y} \label{friedrichproblemgoverningeqn}\\
    u(0) & = 0 \notag \\
    u(\infty) &= 1 \notag
\end{align} $$

  </div>
</div>

### Outer Expansion

We begin by assuming an asymptotic expansion, 

$$ \begin{equation*}
    u = f(y) = f^{(0)} (y) + O[\varepsilon]
\end{equation*} $$

Let \\( \varepsilon \to 0  \\), and the governing differential equation becomes, 

$$ \begin{align*} 
    \dfrac{df^{(0)}}{dy} &= -\dfrac{3}{2} e^{-3y} \\
    f^{(0)} (0) &= 0 \\
    f^{(0)} (\infty) &= 1 
\end{align*} $$

Unfortunately, the no-slip condition \\( f^0 (0) = 0  \\) cannot be satisfied because this is a first-order ODE. Instead, we choose to satisfy the boundary condition at infinity. 

The solution: 

$$ \begin{equation*}
    \boxed{f_{\text{outer}}^{(0)} (y) = 1 + \dfrac{1}{2} e^{-3y}}
\end{equation*} $$

### Inner Expansion

We seek to define a new variable that rescales and magnifies the singular region near the wall as \\( \varepsilon \to 0 \\). Let's define, 

$$ \begin{equation*}
    Y = \dfrac{y}{g(\varepsilon)}
\end{equation*} $$

Eq. \ref{friedrichproblemgoverningeqn} transforms into, 

$$ \begin{equation*}
    \varepsilon \dfrac{d^2 u}{dY^2} + g \dfrac{du}{dY} = - \dfrac{3}{2} g^2 (1 -3\varepsilon) e^{-3gY}
\end{equation*} $$

An asymptotic expansion for the inner region is, 

$$ \begin{equation*}
    u = F(Y) = F^{(0)} (Y) + O [\varepsilon]
\end{equation*} $$

A good choice for the scaling function is \\( g(\varepsilon) = \varepsilon \\), so that the differential equation becomes, 

$$ \begin{align*} 
    \dfrac{d^2 F^{(0)}}{dY^2} + \dfrac{d F^{(0)}}{dY} &= 0 \\
    F^{(0)} (0) &= 0
\end{align*} $$

The solution, 

$$ \begin{equation*}
    F^{(0)}(Y) = C_1 \left[ 1 - e^{-Y}\right]
\end{equation*} $$

To solve for the constant, we need another boundary condition, this is done by matching the inner solution to the outer solution. 

Using, \\( f^{(0)} (0) = F^{(0)} (Y \to \infty) \\), we get \\( C_1 = 3/2 \\).

$$ \begin{equation*}
    \boxed{F_{\text{inner}}^{(0)} (Y) = \dfrac{3}{2} \bigg( 1 - e^{-Y}\bigg)}
\end{equation*} $$

### Summary

The theoretical exact solution is computed. (I omit the calculation here). 

$$\boxed{\begin{aligned}
   f_{\text{outer}}^{(0)} (y) &= 1 + \dfrac{1}{2} e^{-3y} \\
    F_{\text{inner}}^{(0)} (y) &= \dfrac{3}{2} \bigg( 1 - e^{-y/\varepsilon}\bigg) \\
    u_{\text{exact}}(y) &= \dfrac{1}{2}e^{-3y} - \dfrac{3}{2} e^{-y/\varepsilon} + 1 
\end{aligned}} $$

<p align="center">
  <img src="/images/friedrich1.png" alt="Graph of outer, inner asymptotic expansions and exact solution" width="50%">
</p>
<p align="center"><strong>Figure:</strong> Graph of outer, inner asymptotic expansions and exact solution</p>

## Friedrich's Problem 2

Suppose that the differential equation that we want to solve is, 

<div class="equation-box">
  <div>

$$ \begin{align}
    \varepsilon \dfrac{d^2 f}{dy^2} + \dfrac{df}{dy} &= - \dfrac{5}{2} + \dfrac{3}{2} y^2 \label{friedrichprob2}\\
    f(0) &= 0 \notag \\
    f(1) &= 1 \notag
\end{align} $$

  </div>
</div>

### Outer Expansion

Perform the asymptotic expansion for \\( f \\), 

$$ \begin{equation*}
    f(y) = f^{(0)}(y) + \varepsilon f^{(1)}(y) + \varepsilon^2 f^{(2)}(y)
\end{equation*} $$

Plugging this into Eq. \ref{friedrichprob2},

$$ \begin{equation*}
    \dfrac{df^{(0)}}{dy} + \varepsilon \left[ \dfrac{d^2 f^{(0)}}{dy^2} + \dfrac{df^{(1)}}{dy}\right] + \varepsilon^2 \left[ \dfrac{d^2 f^{(1)}}{dy^2} + \dfrac{df^{(2)}}{dy} \right] + \varepsilon^3 \dfrac{d^2 f^{(2)}}{dy^2} = - \dfrac{5}{2} + \dfrac{3}{2} y^2
\end{equation*} $$

$$ \begin{align*} 
    O[1] &: \quad \dfrac{df^{(0)}}{dy} = - \dfrac{5}{2} + \dfrac{3}{2} y^2 \\
    O[\varepsilon] &: \quad \dfrac{d^2 f^{(0)}}{dy^2} + \dfrac{df^{(1)}}{dy} = 0 \\
    O[\varepsilon^2] &: \quad \dfrac{d^2 f^{(1)}}{dy^2} + \dfrac{df^{(2)}}{dy} = 0
\end{align*} $$

Boundary conditions: 

$$ \begin{align*} 
    f^{(0)} (0) = f^{(1)} (0)= f^{(2)}(0) &= 0 \\
    f^{(0)} (1) &= 1 \\
    f^{(1)} (1) = f^{(2)}(1) &= 0
\end{align*} $$

The solutions,

$$ \begin{align*} 
    f^{(0)}(y) &= - \dfrac{5}{2}y + \dfrac{1}{2} y^3 + 3 \\
    f^{(1)} (y) &= \dfrac{3}{2} - \dfrac{3}{2} y^2 \\
    f^{(2)} (y) &= 3y - 3
\end{align*} $$

In total, 

$$ \begin{equation}
    \boxed{f_{\text{outer}}(y) =  \left( - \dfrac{5}{2}y + \dfrac{1}{2} y^3 + 3 \right)+ \dfrac{3}{2} \varepsilon \left( 1 -  y^2\right) + 3\varepsilon^2 (y-1)}
    \label{friedrich2outerf}
\end{equation} $$

### Inner Expansion

We define a new scaling for the independent variable, 

$$ \begin{equation*}
    f = F(Y(y)), \quad Y = \dfrac{y}{\varepsilon}
\end{equation*} $$

$$ \begin{align*} 
    \dfrac{df}{dy} &= \dfrac{dF}{dY} \dfrac{dY}{dy} = \dfrac{1}{\varepsilon} \dfrac{dF}{dY} \\
    \dfrac{d^2 f}{dy^2} &= \dfrac{dY}{dy} \dfrac{d}{dY} \left[ \dfrac{df}{dy}\right] = \dfrac{1}{\varepsilon^2} \dfrac{d^2 F}{dY^2}
\end{align*} $$

so that the differential Eq. \ref{friedrichprob2} turns into, 

$$ \begin{align}
    \dfrac{d^2 F}{dY^2} + \dfrac{dF}{dY} &= - \dfrac{5}{2} \varepsilon + O[\varepsilon^3] \label{innerexpansionfriedrichprob} \\
    F(0) &= 0 \notag
\end{align} $$

An asymptotic expansion for \\( F \\) is, 

$$ \begin{equation}
    F(Y) = F^{(0)} (Y) + \varepsilon F^{(1)}(Y) + \varepsilon^2 F^{(2)}(Y) \label{asymptoticF}
\end{equation} $$

Plugging Eq. \ref{asymptoticF} into Eq. \ref{innerexpansionfriedrichprob},

$$ \begin{align*} 
    \left( \dfrac{d^2 F^{(0)}}{dY^2}  + \dfrac{d F^{(0)}}{dY} \right) + \varepsilon \left( \dfrac{d^2 F^{(1)}}{dY^2} + \dfrac{dF^{(1)}}{dY} \right) + \varepsilon^2 \left( \dfrac{d^2 F^{(2)}}{dY^2} + \dfrac{dF^{(2)}}{dY} \right) = - \dfrac{5}{2} \varepsilon
\end{align*} $$

$$ \begin{align*} 
    O[1] &: \quad \dfrac{d^2 F^{(0)}}{dY^2} + \dfrac{dF^{(0)}}{dY} = 0, \quad F^{(0)} (0) = 0 \\
    O[\varepsilon] &: \quad \dfrac{d^2 F^{(1)}}{dY^2} + \dfrac{dF^{(1)}}{dY} = -\dfrac{5}{2}, \quad F^{(1)} (0) = 0 \\
    O[\varepsilon^2] &: \quad \dfrac{d^2 F^{(2)}}{dY^2} + \dfrac{d F^{(2)}}{dY} = 0, \quad F^{(2)} (0) = 0 
\end{align*} $$

The solutions: 

$$ \begin{align*} 
    F^{(0)}(Y) &= C_1 \bigg[ 1-e^{-Y}\bigg] \\
    F^{(1)}(Y) &= C_2 \bigg[ 1 - e^{-Y}\bigg] - \dfrac{5}{2}Y \\
    F^{(2)}(Y) &= C_3 \bigg[ 1-e^{-Y}\bigg]
\end{align*} $$

In total,

$$ \begin{equation}
     \boxed{F_{\text{inner}}(Y) = C_1 \bigg[ 1-e^{-Y}\bigg] + \varepsilon \left\{  C_2 \bigg[ 1 - e^{-Y}\bigg] - \dfrac{5}{2}Y \right\} + \varepsilon^2 C_3 \bigg[ 1-e^{-Y}\bigg]}
     \label{friedrich2innerF}
\end{equation} $$

### Matching Outer and Inner Expansions

Let's express Eq. \ref{friedrich2outerf} in terms of \\( Y = y/\varepsilon \\) and neglect all \\( O[\varepsilon^3] \\) terms. 

$$ \begin{equation*}
    f_{\text{outer}}(Y) = 3 + \left( \dfrac{3}{2} - \dfrac{5}{2} Y \right) \varepsilon - 3 \varepsilon^2
\end{equation*} $$

Conversely, let's express Eq. \ref{friedrich2innerF} in terms of \\( y = Y \varepsilon \\),

$$ \begin{equation*}
    F_{\text{inner}} (y) = C_1 - \dfrac{5}{2}y + C_2 \varepsilon + C_3 \varepsilon^2 + O[e^{-1/\varepsilon}]
\end{equation*} $$

If we set these two equal to each other and equate coefficients of \\( \varepsilon \\), we obtain, 

$$ \begin{equation*}
    C_1 = 3, \quad C_2 = \dfrac{3}{2}, \quad C_3 = -3 
\end{equation*} $$

Thus, the common function (where \\( f_\text{outer}=F_\text{inner} \\)) is, 

$$ \begin{equation*}
    \boxed{F_{\text{common}} (y)= 3- \dfrac{5}{2}y + \dfrac{3}{2} \varepsilon - 3 \varepsilon^2 }
\end{equation*} $$


<details class="custom-collapse" open>
  <summary><strong> Exact Solution of Friedrich's Problem 2</strong></summary>
  <div class="collapse-content">

Let us restate the differential equation that we want to solve, 

$$ \begin{align*} 
    \varepsilon \dfrac{d^2 f}{dy^2} + \dfrac{df}{dy} &= - \dfrac{5}{2} + \dfrac{3}{2} y^2 \\
    f(0) &= 0  \\
    f(1) &= 1 
\end{align*} $$

The homogeneous solution is easily computed as, 

$$ \begin{equation*}
    \boxed{f_h = C_1 + C_2 e^{- \frac{y}{\varepsilon}}}
\end{equation*} $$

For the particular solution, we guess a polynomial form. 

$$ \begin{equation*}
    f_p = By + \mathcal{C} y^2 + D y^3
\end{equation*} $$

Plugging this into the differential equation, 

$$ \begin{equation*}
    (2 \varepsilon \mathcal{C} + B) + (6D \varepsilon + 2 \mathcal{C}) y + 3Dy^2 = - \dfrac{5}{2} + \dfrac{3}{2} y^2
\end{equation*} $$

Equating coefficients of \( y \), we get,

$$ \begin{align*} 
    B &= - \dfrac{5}{2} + 3 \varepsilon^2 \\
    \mathcal{C} &= -\dfrac{3 \varepsilon}{2} \\
    D &= \dfrac{1}{2}
\end{align*} $$

The particular solution is,

$$ \begin{equation*}
    \boxed{f_p = \left(  - \dfrac{5}{2} + 3 \varepsilon^2  \right) y - \dfrac{3 \varepsilon}{2} y ^2 + \dfrac{y^3}{2}}
\end{equation*} $$

The full solution is \( f = f_h + f_p \). We use the boundary conditions to solve for the constants, 

$$ \begin{equation*}
    \boxed{ f_{\text{exact}}(y) = C_1 \bigg[ 1 - e^{-y/\varepsilon} \bigg] + \left(  - \dfrac{5}{2} + 3 \varepsilon^2  \right) y - \dfrac{3 \varepsilon}{2} y ^2 + \dfrac{y^3}{2}, \text{ where } \quad C_1 = \dfrac{3-3\varepsilon^2 + \dfrac{3}{2} \varepsilon}{1- e^{-1/\varepsilon}} } 
\end{equation*} $$

  </div>
</details>

### Summary

$$\boxed{\begin{aligned}
    f_{\text{outer}}(y) &=  \left( - \dfrac{5}{2}y + \dfrac{1}{2} y^3 + 3 \right)+ \dfrac{3}{2} \varepsilon \left( 1 -  y^2\right) + 3\varepsilon^2 (y-1) \\
     F_{\text{inner}}(y) &= 3 \bigg[ 1-e^{-y/\varepsilon}\bigg] + \varepsilon \left\{  \dfrac{3}{2} \bigg[ 1 - e^{-y/\varepsilon}\bigg] - \dfrac{5}{2} \dfrac{y}{\varepsilon} \right\} -3 \varepsilon^2 \bigg[ 1-e^{-y/\varepsilon}\bigg] \\
    f_{\text{exact}}(y) &= C_1 \bigg[ 1 - e^{-y/\varepsilon} \bigg] + \left(  - \dfrac{5}{2} + 3 \varepsilon^2  \right) y - \dfrac{3 \varepsilon}{2} y ^2 + \dfrac{y^3}{2}, \text{ where } \quad C_1 = \dfrac{3-3\varepsilon^2 + \dfrac{3}{2} \varepsilon}{1- e^{-1/\varepsilon}} 
\end{aligned}}$$


