---
title: "Numerical Methods in Boundary Layer Equations"
excerpt: "Solved Falkner-Skan equation using finite difference scheme and shooting method, approximated solution to boundary layer equation by using momentum integral equation, Thwaites Method"
collection: portfolio
author_profile: false
layout: single
---

## Boundary Layer Equations + Falkner Skan

<div class="equation-box">
  <h3>Governing Equations for 2D Boundary Layer Flow over Flat Plate</h3>
  <div>
    $$ 
    \begin{align*}
        &\text{Continuity: }  \dfrac{\partial u}{\partial x} + \dfrac{\partial v}{\partial y} = 0 \\[10pt]
        &\text{Momentum: }  u \dfrac{\partial u}{\partial x} + v \dfrac{\partial u}{\partial y} = u_e \dfrac{d u_e}{d x} + \nu \dfrac{\partial^2 u}{\partial y^2} \\[10 pt]
        &\text{Boundary Conditions: } \quad u(x > 0, y = 0) = 0, \enspace v(x > 0, y = 0) = 0, \enspace u(x > 0, y \to \infty) = u_e(x)
    \end{align*}$$
  </div>
</div>

For flows with edge velocities that follow a power law, such as  \\( u_e(x) = U_0 (x/L)^m \\), similar solutions exist. This means that \\( u(x,y)/u_e(x) \\) can be expressed as a function of a single variable, \\( \eta \\).  With the help of the non-dimensional stream function, this PDE can then be converted to a nonlinear ODE. 

<div class="equation-box">
  <h3>Third-Order Nonlinear ODE for 2D Boundary Layer Flow over Flat Plate</h3>
  <div>
    $$
    \begin{align*}
        & \text{ODE: }  f'''(\eta) + \dfrac{m+1}{2} f(\eta) f''(\eta) + m \bigg[1 - f'(\eta)^2 \bigg] = 0  \\[10pt]
        & \text{Where: }  \psi(x,y) = \delta(x) u_e(x) f \bigg(\eta(x,y)\bigg), \enspace \eta(x,y) = \dfrac{y}{\delta(x)}, \enspace \delta(x) = \sqrt{\dfrac{\nu x}{u_e(x)}}, \enspace m=\dfrac{x}{u_e(x)} \dfrac{d u_e}{dx} = \dfrac{\delta^2}{\nu}\dfrac{d u_e}{dx}  \\[10pt]
        & \text{Boundary Conditions: }  f'( \eta = 0 ) = 0, \enspace f'( \eta \to \infty ) = 1, \enspace f( \eta = 0 ) = 0 
    \end{align*}$$
  </div>
</div>

In literature, another form of the equation is often presented. Recall that the similarity variable can be multiplied by any constant C and still remain the similarity variable. Intuitively, y can be scaled by any variable that is on the same order as the boundary layer thickness. For example, \\( \delta(x) =  \sqrt{C \nu x/u_e(x)} \\) is an equally valid scaling factor for y.

Let's introduce new variables to derive the other form of the Falkner Skan equation. 

$$\begin{equation*}
\xi(x,y) = \dfrac{y}{\Omega(x)}, \quad \Omega(x) = \sqrt{\dfrac{2}{m+1}} \delta(x)
\end{equation*}$$
$$\begin{equation*}
\xi = \xi(x,y) = \xi(\eta(x,y)) = \sqrt{\dfrac{m+1}{2}} \eta(x,y)
\end{equation*}$$
$$\begin{equation*}
    \boxed{\psi(x,y) = \Omega(x) u_e(x) g(\xi(x,y))}
\end{equation*}$$

If we equate the two stream functions,
$$\begin{align*}
\delta(x) f(\eta) &= \Omega(x) g(\xi) \\[8pt]
f(\eta) &= \sqrt{\dfrac{2}{m+1}} \, g(\xi), \\[8pt]
\dfrac{dg}{d\xi} &= \dfrac{df}{d\eta}, \\[8pt]
\dfrac{d^2g}{d\xi^2} &= \sqrt{\dfrac{2}{m+1}} \, \dfrac{d^2f}{d\eta^2}, \\[8pt]
\dfrac{d^3g}{d\xi^3} &= \dfrac{2}{m+1} \, \dfrac{d^3f}{d\eta^3}.
\end{align*}$$

If I make the above substitutions into the original Falkner Skan equation, the ODE is transformed into the following,

$$\begin{equation*}
\boxed{\dfrac{d^3g}{d\xi^3} + g \dfrac{d^2g}{d\xi^2} + \dfrac{2m}{m+1}\left[1 - \left(\dfrac{dg}{d\xi}\right)^2\right] = 0}
\end{equation*}$$

<p align="center">
  <img src="/images/velprof.png" width="50%">
</p>

**Figure:** Velocity profile \\( f'(\eta) \\) versus \\( \eta \\) for various values of \\( m \\). The profiles demonstrate the influence of the Falkner-Skan parameter \\( m \\) on boundary layer flow.

---

<p align="center">
  <img src="/images/falknerskanfriction.png" width="100%">
</p>

**Figure:** Falkner Skan: Friction Coefficient vs External Velocity Parameter

---

<p align="center">
  <img src="/images/blthicknessfs.png" width="100%">
</p>

**Figure:** Falkner Skan: Momentum Boundary Layer Thickness vs External Velocity Parameter

---

<p align="center">
  <img src="/images/FSMTH.png" width="100%">
</p>

**Figure:** Falkner Skan: \\( M(\lambda) = 2T - 2(H+2)\lambda, \ T(\lambda), \ \text{and } H(\lambda) \\) Plots

---

<p align="center">
  <img src="/images/fsmvslambda.png" width="50%">
</p>

**Figure:** Falkner Skan: Relationship between \\( m = \dfrac{x}{u_e} \dfrac{du_e}{dx} \\) and \\( \lambda = \dfrac{\Theta^2}{\nu} \dfrac{du_e}{dx} \\)

## Momentum Integral Equation and Its Various Forms

Solving the full partial differential equation for boundary layer is difficult due to the nonlinearity of the terms. The Von Karman momentum integral equation allows us to calculate approximate solutions for the boundary layer equations.

There are many forms of the Von Karman momentum integral equation. For the derivation, we start with the boundary layer equations.

The boundary layer equations are as follows:

$$\begin{equation}
\dfrac{\partial u}{\partial x} + \dfrac{\partial v}{\partial y} = 0
\label{eq:continuity}
\end{equation}$$

$$\begin{equation}
u \dfrac{\partial u}{\partial x} + v \dfrac{\partial u}{\partial y} = u_e \dfrac{\mathrm{d} u_e}{\mathrm{d} x} + \nu \dfrac{\partial^2 u}{\partial y^2}
\label{eq:momentum}
\end{equation}$$

We multiply the continuity equation (\ref{eq:continuity}) by \\( u \\) and add it to the momentum equation (\ref{eq:momentum}), which gives:

$$
2u \dfrac{\partial u}{\partial x} + u \dfrac{\partial v}{\partial y} + v \dfrac{\partial u}{\partial y} = u_e \dfrac{\mathrm{d} u_e}{\mathrm{d} x} + \nu \dfrac{\partial^2 u}{\partial y^2}
$$

This simplifies to:

$$
\dfrac{\partial u^2}{\partial x} + \dfrac{\partial (uv)}{\partial y} = u_e \dfrac{\partial u_e}{\partial x} + \nu \dfrac{\partial^2 u}{\partial y^2}
$$

We now integrate both sides of the equation from \\( y = 0 \\) to \\( y = \infty \\):

$$
\int_0^\infty \dfrac{\partial u^2}{\partial x} \, dy + \left[ uv \right]_{0}^{\infty} = \int_0^\infty u_e \dfrac{\mathrm{d} u_e}{\mathrm{d} x} \, dy + \nu \int_0^\infty \dfrac{\partial^2 u}{\partial y^2} \, dy
$$

$$
\dfrac{\partial}{\partial x} \left( \int_0^\infty u^2 \, dy \right) + u_e v_{\infty} = \int_0^\infty u_e \dfrac{\mathrm{d} u_e}{\mathrm{d} x} \, dy + \nu \left( \dfrac{\partial u}{\partial y} \Big|_{y=\infty} - \dfrac{\partial u}{\partial y} \Big|_{y=0} \right)
$$

We go back to continuity equation.
$$
\dfrac{\partial u}{\partial x} = - \dfrac{\partial v}{\partial y}
$$

Integrating both sides from \\( y = 0 \\) to \\( y = \infty \\):

$$
\int_0^\infty \dfrac{\partial u}{\partial x} \, dy = -v_{\infty}
$$

$$
\dfrac{\partial}{\partial x} \left( \int_0^\infty u^2 \, dy \right) - u_e \int_0^\infty \dfrac{\partial u}{\partial x} \, dy - \int_0^\infty u_e \dfrac{\mathrm{d} u_e}{\mathrm{d} x} \, dy = -\nu \dfrac{\partial u}{\partial y} \Big|_{y=0}
$$

The rest is trivial. 

$$\begin{equation*}
    \boxed{\dfrac{d}{dx} \left( u_e^2 \Theta \right) + u_e \delta^* \dfrac{d u_e}{dx}  = \dfrac{\tau_w}{\rho}}
\end{equation*}
$$

$$\begin{equation*}
\boxed{\dfrac{d\Theta}{dx} + \dfrac{\Theta}{u_e} \dfrac{d u_e}{dx} (H + 2) = \dfrac{C_f}{2} = \dfrac{\nu}{u_e^2}\dfrac{\partial u}{\partial y} \bigg|_{y=0} , \quad \text{where } H = \dfrac{\delta^*}{\Theta}}
\end{equation*}$$

$$\begin{equation*}
\boxed{\dfrac{d\Theta}{dx} + \dfrac{\delta^* + 2\Theta}{u_e} \dfrac{d u_e}{dx} = \dfrac{\tau_w}{\rho u_e^2}}
\end{equation*}$$

In approximating the boundary layer equations, it is advantageous to rewrite everything in terms of the momentum thickness.
$$\begin{equation*}
    Y = \dfrac{\Theta^2}{\nu}, \quad \lambda = \dfrac{\Theta^2}{\nu} \dfrac{d u_e}{dx} = Y \dfrac{d u_e}{dx}, \quad T = \dfrac{\tau_w \Theta}{\mu u_e}
\end{equation*}$$

$$\begin{equation*}
    u_e \dfrac{d}{dx}\bigg(\dfrac{\Theta^2}{\nu}\bigg) = 2T - 2 (H + 2) \lambda
\end{equation*}$$

$$\begin{equation}
    \boxed{u_e \dfrac{dY}{dx} = M(\lambda), \quad \text{where } M(\lambda) = 2T - 2\lambda (H + 2) }
    \label{momentumint}
\end{equation}$$

## Pohlhausen's Polynomial Approximation

Pohlhausen guessed a fourth-degree order polynomial for the velocity profile as a function of \\( \eta \\), the similarity variable. Note that this \\( \eta \\) is different from the \\( \eta \\) above in the Falkner Skan equation because we assume that the u-velocity reaches the external velocity at a finite point in the Pohlhausen approximation. 

In mathematical terms, for Pohlhausen, \\( u/u_e=1 \\) at \\( \eta=1 \\), but for Falkner Skan, we have $u/u_e=1$ as \\( \eta \rightarrow \infty \\). As such, the similarity variable and the boundary layer thickness variable defined in this section are different from the ones defined above. To make a comparison, we convert to a less arbitrary scaling for the boundary layer thickness (either using displacement thickness or momentum thickness).

The polynomial Pohlhausen guessed is, 

$$\begin{equation*}
    F(\eta) = \dfrac{u}{u_e} = A\eta^4 + B\eta^3 + C\eta^2 + D\eta + E, \quad \text{where } \eta = \dfrac{y}{\delta},
\end{equation*} $$

with the following boundary conditions, 

$$\begin{equation*}
    F(0) = 0, \quad F''(0) = -\dfrac{\delta^2}{\nu} \dfrac{d u_e}{dx} = -\Lambda, \quad F(1) = 1, \quad F'(1) = 0, \quad F''(1) = 0
\end{equation*}$$

I can solve for the coefficients with linear algebra techniques on the following matrix, 

$$\begin{equation*}
    \begin{bmatrix}
        0 & 0 & 0 & 0 & 1 \\
        0 & 0 & 2 & 0 & 0 \\
        1 & 1 & 1 & 1 & 1 \\
        4 & 3 & 2 & 1 & 0 \\
        12 & 6 & 2 & 0 & 0
    \end{bmatrix}
    \begin{bmatrix}
        A \\
        B \\
        C \\
        D \\
        E
    \end{bmatrix}
    =
    \begin{bmatrix}
        0 \\
        -\Lambda \\
        1 \\
        0 \\
        0
    \end{bmatrix}
\end{equation*}$$

$$\begin{equation*}
    \begin{bmatrix}
        A \\
        B \\
        C \\
        D \\
        E
    \end{bmatrix}
    =
    \begin{bmatrix}
        1 - \dfrac{\Lambda}{6} \\
        \dfrac{\Lambda}{2} - 2 \\
        -\dfrac{\Lambda}{2} \\
        \dfrac{\Lambda}{6} + 2 \\
        0
    \end{bmatrix}
\end{equation*}
$$

$$\begin{equation}
\boxed{F(\eta) = {\left(1-\dfrac{\Lambda }{6}\right)}\,\eta^4 +{\left(\dfrac{\Lambda }{2}-2\right)}\,\eta^3 -\dfrac{\Lambda \,\eta^2 }{2}+{\left(\dfrac{\Lambda }{6}+2\right)}\,\eta}
\label{polynomialeqn}
\end{equation}$$

$$\begin{equation}
    \boxed{F'(\eta) = \dfrac{\Lambda }{6}-\Lambda \,\eta +3\,\eta^2 \,{\left(\dfrac{\Lambda }{2}-2\right)}-4\,\eta^3 \,{\left(\dfrac{\Lambda }{6}-1\right)}+2 \longrightarrow F'(0) = \dfrac{\Lambda }{6}+2}
    \label{Fprime0eqn}
\end{equation}$$

The velocity profile is plotted in Fig. \ref{fig:pohlhausen}, varying the \\( \Lambda \\) parameter. A positive \\( \Lambda \\) means external velocity acceleration, and a negative \\( \Lambda \\) means an external velocity deceleration. 

<p align="center">
  <img src="/images/pohlhausen.png" width="50%">
</p>

**Figure:** Velocity profiles for varying \\( \Lambda \\)


Boundary layer separation occurs when the wall shear stress is zero,

$$\begin{equation*}
     \tau_w(x) = \mu \dfrac{\partial{u}}{\partial{y}} \Bigg|_{x, y = 0} = \dfrac{\mu u_e(x)}{\delta(x)} \underbrace{F'(0)}_{\text{See equation \ref{Fprime0eqn}}}
\end{equation*}$$

The wall shear stress is typically expressed as the nondimensional \\( C_f \\) by dividing by the dynamic pressure, \\( \rho u_e^2/2 \\).
$$
\begin{equation*}
    C_f(x) =\dfrac{2\nu}{\delta(x) u_e(x)} F'(0) 
\end{equation*}$$

After multiplying both sides by the known ratio \\( \delta/\Theta \\) (see equation \ref{Theta/delta} below), I obtain, 

$$\begin{equation*}
    C_f = \dfrac{2}{Re_{\Theta}} \dfrac{\Theta}{\delta} F'(0) 
\end{equation*}
$$

After substitution, 
$$\begin{equation}
    \boxed{C_f Re_{\Theta} = -{\left(\dfrac{\Lambda }{6}+2\right)}\,{\left(\dfrac{\Lambda^2 }{4536}+\dfrac{2\,\Lambda }{945}-\dfrac{74}{315}\right)}}
\end{equation}
$$

<p align="center">
  <img src="/images/phfriction.png" width="100%">
</p>

**Figure:** Pohlhausen Approximation: Friction Coefficient vs \\( \Lambda \\) and \\( \lambda \\)

According to figures \ref{fig:pohlhausen} and \ref{fig:friction}, the range is \\( -12 <\Lambda < 12 \\) and \\( -0.1567 <\lambda < 0.0948 \\). At the lower limit, the wall shear stress is zero and separation occurs. Above the higher limit, the velocity exceeds the external velocity. 

By definition, 

$$\begin{equation*}
\delta^* = \int_0^1 \left( 1 - \dfrac{u}{u_e} \right) \delta \, d\eta
\quad \Longrightarrow \quad \dfrac{\delta^*}{\delta} = \int_0^1 \left( 1 - F(\eta) \right) \, d\eta
\end{equation*}$$

$$\begin{equation*}
\dfrac{\Theta}{\delta} = \int_0^1 F(\eta) \left( 1 - F(\eta) \right) \, d\eta
\end{equation*}$$

$$\begin{equation*}
H = \dfrac{\delta^*}{\Theta} = \dfrac{\dfrac{\delta^*}{\delta}}{\dfrac{\Theta}{\delta}} = \dfrac{\int_0^1 \left( 1 - F(\eta) \right) \, d\eta}{\int_0^1 F(\eta) \left( 1 - F(\eta) \right) \, d\eta}
\end{equation*}$$

I will now substitute equation \ref{polynomialeqn} into the relations for \\( \dfrac{\delta^*}{\delta}, \, \dfrac{\Theta}{\delta}, \, H \\)

$$\begin{equation}
    \boxed{\dfrac{\delta^*}{\delta}=\dfrac{3}{10}-\dfrac{\Lambda }{120}}
\end{equation}$$

$$\begin{equation}
    \boxed{\dfrac{\Theta}{\delta}=-\dfrac{\Lambda^2 }{9072}-\dfrac{\Lambda }{945}+\dfrac{37}{315}}
    \label{Theta/delta}
\end{equation}$$

$$\begin{equation}
    H = \dfrac{\dfrac{\Lambda }{120}-\dfrac{3}{10}}{\dfrac{\Lambda^2 }{9072}+\dfrac{\Lambda }{945}-\dfrac{37}{315}}
\end{equation} $$

Solving for T is a bit trickier.
$$\begin{equation}
    \boxed{T = \dfrac{\tau_w\Theta}{\mu u_e} = F'(0) \dfrac{\Theta}{\delta} = -{\left(\dfrac{\Lambda }{6}+2\right)}\,{\left(\dfrac{\Lambda^2 }{9072}+\dfrac{\Lambda }{945}-\dfrac{37}{315}\right)}}
\end{equation}$$


Recall that \\( \lambda = \dfrac{\Theta^2}{\nu} \dfrac{d u_e}{dx} \\) and \\( \Lambda = \dfrac{\delta^2}{\nu}\dfrac{du_e}{dx} \\). Upon division, the ratio \\( \dfrac{\lambda}{\Lambda} = (\dfrac{\Theta}{\delta})^2 \\) is obtained. From equation \ref{Theta/delta}, we realize that \\( \dfrac{\lambda}{\Lambda} = f(\Lambda) \\). Thus, there is a relation between \\( \lambda \\) and \\( \Lambda \\).


$$\begin{equation}
    \boxed{\lambda=\Lambda \, \left(\dfrac{\Lambda^2 }{9072}+\dfrac{\Lambda }{945}-\dfrac{37}{315}\right)^2}
\end{equation}$$

The relation between these two variables is plotted below, 

<p align="center">
  <img src="/images/Lambdalambda.png" width="60%">
</p>

**Figure:** Pohlhausen Approximation: Relation between \\( \Lambda \\) and \\( \lambda \\)


With the relation between \\( \lambda \\) and \\( \Lambda \\), I can now solve for M. Recall that \\( M = 2T-2\lambda(H+2) \\). Since T, \\( \lambda \\), and H are all known as functions of \\( \Lambda \\), M can be found as a function of \\( \Lambda \\).

$$\begin{equation}
    \boxed{M = -2\,{\left(\dfrac{\Lambda }{6}+2\right)}\,{\left(\dfrac{\Lambda^2 }{9072}+\dfrac{\Lambda }{945}-\dfrac{37}{315}\right)}-2\,\Lambda \,{\left(\dfrac{\dfrac{\Lambda }{120}-\dfrac{3}{10}}{\dfrac{\Lambda^2 }{9072}+\dfrac{\Lambda }{945}-\dfrac{37}{315}}+2\right)}\,{\left(\dfrac{\Lambda^2 }{9072}+\dfrac{\Lambda }{945}-\dfrac{37}{315}\right)}^2}
\end{equation}$$

The main variables of note are M,T, and H. Since they are all functions of \\( \Lambda \\), and \\( \Lambda \\) is a function of \\( \lambda \\), then M, T, and H are all functions of \\( \lambda \\). 

<p align="center">
  <img src="/images/MTHvl.png" width="100%">
</p>

**Figure:** Pohlhausen Approximation: M, T, and H vs \\( \lambda \\)

Let's restate the key governing equation \ref{momentumint} now,

$$\begin{equation*}
    \boxed{u_e(x) \dfrac{dY}{dx} = M(\lambda), \quad \text{where } M(\lambda) = 2T - 2\lambda (H + 2) }
\end{equation*}$$

Writing the functional dependence explicitly,

$$\begin{equation*}
    \boxed{\dfrac{dY}{dx} (x) = \dfrac{M(\lambda(x))}{u_e(x)}}
\end{equation*}$$

The question remains: how do I pick my initial condition? At a front stagnation point, \\( u_e = 0 \\). When this happens, M should also be 0, so that \\( dY/dx \\) ends up being finite. 

$$\begin{align*}
    M(\lambda(x_0)) &= 0  \\
    \lambda(x_0) &= 0.077 
\end{align*}$$

Recalling that \\( \lambda = Y \dfrac{du_e}{dx} \\), then 

$$\begin{equation}
        \boxed{Y(x_0) = \dfrac{0.077}{u_e'(x_0)}}
\end{equation}$$

Using L'Hopital's rule, 

$$\begin{align*}
    \lim_{x \to x_0} \dfrac{M\left(\lambda(x)\right)}{u_e(x)} &= \dfrac{0}{0} \nonumber \\ 
    \lim_{x \to x_0} \dfrac{M'(\lambda(x))\lambda'(x)}{u_e'(x)} &= Y'(x_0) \\
    M'(\lambda(x_0))\lambda'(x_0) &= Y'(x_0) u_e'(x_0) \\
    M'(\lambda(x_0)) \bigg[ Y'(x_0) u_e'(x_0) + Y(x_0) u_e''(x_0) \bigg] &=  Y'(x_0) u_e'(x_0)
\end{align*}$$

$$\begin{equation*}
Y'(x_0) = \dfrac{M'(\lambda(x_0))}{1 - M'(\lambda(x_0))}  \dfrac{u_e''(x_0)}{u_e'(x_0)} Y(x_0)
\end{equation*}$$

$$\begin{equation}
\boxed{Y'(x_0) = -0.0653 \dfrac{u_e''(x_0)}{\left(u_e'(x_0)\right)^2}}
\label{IC2}
\end{equation}$$

Note that equation \ref{IC2} was simplified by using the fact that \\( M'(\lambda(x_0)) \\) is known from the graphs/equations/tables. 

With the starting conditions known, I can now numerically integrate the differential equation. I coded this in MATLAB, but I will just explain the logic. 

<div style="background:#f5f5f5; border:1px solid #ddd; padding:12px; font-family: monospace; border-radius:4px;">
  <h3 style="margin-top:0; margin-bottom:10px; font-family: monospace;">
    Matlab Code For Loop Logic
  </h3>
  
<strong>Initialization</strong>

$$\begin{equation*}
\lambda(x_0) = 0.077, \, Y(x_0) = \dfrac{0.077}{u_e'(x_0)}, \, Y'(x_0) = -\dfrac{0.0653 \, u_e''(x_0)}{(u_e'(x_0))^2}
\end{equation*}$$

<strong>Loop 1</strong>

$$\begin{equation*}
x_0 \xrightarrow {} u_e'(x_0) \xrightarrow{} \lambda(x_0) = 0.077 \xrightarrow{} Y'(x_0) = -\dfrac{0.0653 \, u_e''(x_0)}{(u_e'(x_0))^2}
\end{equation*}$$

$$\begin{equation*}
Y(x_1) = Y(x_0) + Y'(x_0) \Delta x
\end{equation*}$$

<strong>Loop 2</strong>

$$\begin{equation*}
x_1 \xrightarrow {} u_e'(x_1) \xrightarrow{} \lambda(x_1) = Y(x_1)u_e'(x_1) \xrightarrow{} Y'(x_1) = \dfrac{M(\lambda(x_1))}{u_e(x_1)}
\end{equation*}$$

$$\begin{equation*}
Y(x_2) = Y(x_1) + Y'(x_1) \Delta x
\end{equation*}$$
</div>

To recap, Pohlhausen's method involves approximating the velocity profile analytically as a polynomial that matches the boundary conditions. From this polynomial velocity profile, we can determine  \\( T(\lambda) = \dfrac{\tau_w \Theta}{\nu u_e} \\) and \\( H(\lambda)=\dfrac{\delta^*}{\Theta} \\), which we can then plug into the momentum integral equation.

<p align="center">
  <img src="/images/pohl.png" width="50%">
</p>

**Figure:** Pohlhausen Method: variance of \\( \lambda \\) and T over Circular Cylinder

## Thwaites Method

Let's return back to the governing equation, repeated below. 
$$\begin{equation*}
    \boxed{u_e(x) \dfrac{dY}{dx} = M(\lambda), \quad \text{where } M(\lambda) = 2T - 2\lambda (H + 2) }
\end{equation*}$$

Thwaites method involves assuming that M is a linear function of \\( \lambda \\) in order to simplify the governing momentum integral equation.  In reality, this may not be the case.

If we look at Fig. \ref{fig:FSMTH}, we can kinda see that M is linear in \\( \lambda \\) for the Falkner Skan velocity profiles. Thus, we assume that \\( M(\lambda) = A + B\lambda \\), which turns the ODE into a linear one that can be solved with an integrating factor.

$$\begin{align*}
    u_e \dfrac{dY}{dx} - M &= 0, \\
    \dfrac{dY}{dx} - \dfrac{A + B \lambda}{u_e} &= 0, \\
    \dfrac{dY}{dx} - \dfrac{A + B Y u_e'}{u_e} &= 0, \quad \text{note:} \quad \lambda = {Y u_e'}, \\
    \dfrac{dY}{dx} - \dfrac{B u_e'}{u_e} Y &= \dfrac{A}{u_e}.
\end{align*}$$

If we multiply both sides of the ODE by \\( u_e^{-B} \\), the integrating factor, we obtain,

$$\begin{align*}
    \dfrac{d}{dx} \big(u_e^{-B} Y \big) &= A u_e^{-(B+1)}, \\
    \int_{x_0}^{x} d\big(u_e^{-B} Y\big) &= \int_{x_0}^{x} A u_e^{-(B+1)} \, dx, \\
    Y(x) &= u_e(x)^B u_e(x_0)^{-B} Y(x_0) 
    + u_e(x)^B \int_{x_0}^{x} A u_e^{-(B+1)} \, dx.
\end{align*}$$

$$\begin{align}
    \text{Assuming } x_0 = 0 \text{ and } Y(x_0) = 0, \nonumber \\ 
    \boxed{
    \dfrac{\Theta^2}{\nu} = Y(x) = u_e(x)^B \int_{0}^{x} A u_e(x)^{-(B+1)} \, dx} \label{eq:Thwaites}
\end{align}$$

By averaging experimental data and known solutions (see Fig.~\ref{fig:thwaitesresults}), Thwaites found the following best-fit equations:

$$
M(\lambda) = 0.45 - 6.0 \lambda
$$

$$T(\lambda) = (\lambda + 0.09)^{0.62}
$$

$$H(\lambda) = 5.6071 \lambda^2 - 3.8364 \lambda + 2.6098 \quad \text{for} \ \lambda > 0
$$

$$H(\lambda) = \dfrac{2.1247 \lambda + 0.3542}{\lambda + 0.1359} \quad \text{for} \ \lambda < 0
$$

Using these numbers, equation \ref{eq:Thwaites} becomes,

$$\begin{equation*}
    \boxed{Y(x) = \dfrac{\Theta^2}{\nu} = u_e^{-6} \int_0^x 0.45 u_ e^5 \, dx}
\end{equation*}$$

With a given external velocity distribution \\( u_e(x) \\), we can then find \\( \lambda(x) =Y(x) \dfrac{du_e}{dx} \\) and \\( T(\lambda)=\dfrac{\Theta \tau_w}{\mu u_e}\\), which allows us to determine the shear stress. 

<p align="center">
  <img src="/images/thwaitesresults.png" width="50%">
</p>

**Figure:** Thwaites Fit for Various Known Solutions. Note: F corresponds to M in my notation

---

<p align="center">
  <img src="/images/comparison.png" width="100%">
</p>

**Figure:** Comparison of M, T, and H Parameters for Falkner-Skan Solution, Thwaites and Pohlhausen Approximation Plotted vs \\( \lambda \\)

## Computation for Flow Around Circular Cylinder

To calculate incompressible laminar flow around a circular cylinder, we must first compute the outer (potential flow) solution and then combine that with the approximate boundary layer equations.

Recall that an irrotational, incompressible flow satisfies Laplace's equation. 

$$\nabla^2\psi=0 \notag$$

$$
\dfrac{1}{r} \dfrac{\partial}{\partial r} \left( r \dfrac{\partial \psi}{\partial r} \right) + \dfrac{1}{r^2} \dfrac{\partial^2 \psi}{\partial \theta^2} = 0
\notag
$$

Boundary conditions:

$$
\psi(r_{\infty}, \theta) = U_0 r_{\infty} \sin \theta, \quad \psi(R, \theta) = 0 \quad \text{(at boundary)} \notag$$

Assume:

$$\psi = U_0 f(r) \sin \theta \notag$$

Partial derivatives:
$$
\dfrac{\partial \psi}{\partial \theta} = U_0 f(r) \cos \theta \notag
$$

$$
\dfrac{\partial^2 \psi}{\partial \theta^2} = - U_0 f(r) \sin \theta \notag
$$

$$
\dfrac{\partial \psi}{\partial r} = U_0 f'(r) \sin \theta \notag
$$

$$
\dfrac{\partial}{\partial r} \left( r \dfrac{\partial \psi}{\partial r} \right) = \left( U_0\sin \theta \right) \left( f'(r) + r f''(r) \right) \notag
$$

Substitute into the governing equation:
$$
\dfrac{1}{r} \left( U_0 \sin \theta \left( f' + r f'' \right) \right) - \dfrac{1}{r^2} U_0 f \sin \theta = 0 \notag
$$

Simplify:
$$ U_0 \sin \theta \left[ r^2 f'' + r f' - f \right] = 0  \notag$$

Eliminate constants:
$$
r^2 f'' + r f' - f = 0 \notag
$$

We will solve this with a series solution:

$$
f(r) = \sum_{m=0}^\infty a_m r^m \notag
$$

Derivatives:
$$
f'(r) = \sum_{m=1}^\infty m a_m r^{m-1}, \quad f''(r) = \sum_{m=2}^\infty m(m-1) a_m r^{m-2}
\notag $$

Substitute into the differential equation:
$$
a_0+a_1r + a_1+\sum_{m=2}^\infty \left[ m(m-1) + m - 1 \right] a_m r^m = 0
\notag $$

The only non-trivial solution occurs when $m = -1$ or $m = 1$.
$$ f(r) = c_1 r + c^2r^{-1} \notag $$

Skipping a couple of steps, 
$$
\boxed{
\psi = U_0 r \left[ 1 - \dfrac{R^2}{r^2} \right] \sin(\theta), \quad
u_r = U_0 \left[ 1 - \dfrac{R^2}{r^2} \right] \cos(\theta), \quad
u_\theta = -U_0 \sin(\theta) \left[ 1 + \left( \dfrac{R}{r} \right)^2 \right]
} \notag
$$

<p align="center">
  <img src="/images/prescoefcylinder.png" width="50%">
</p>

**Figure:** Pressure coefficient around a circular cylinder in potential flow: \\( C_p = 1 - 4 \sin^2(\theta) \\)

On the surface of a cylinder, we know how the edge velocity varies as a function of \\( \theta \\). To make things familiar, we convert to a boundary layer coordinate system, with the x-axis aligned with the freestream direction and the y-axis normal to that. 

$$\dfrac{u_e}{u_0} = 2\sin{(x/R)} \notag$$ 

Plugging the above into equation \ref{eq:Thwaites}, we obtain, 

$$Y(x) = \dfrac{0.225R}{u_0} \dfrac{1}{\sin^6\left(\dfrac{x}{R}\right)} \underbrace{\left[ \dfrac{2}{3} \cos^3\left(\dfrac{x}{R}\right) - \cos\left(\dfrac{x}{R}\right) - \dfrac{\cos^5\left(\dfrac{x}{R}\right)}{5} + \dfrac{8}{15} \right]}_{\text{G}\left(\dfrac{x}{R}\right)} \notag$$

$$ \boxed{Y(x) = \dfrac{0.225R}{u_0} G(x/R)} \notag $$
$$ \boxed{\lambda = 0.45  G(x/R)\cos(x/R)} \notag $$

<table>
  <tr>
    <td align="center" width="45%">
      <img src="/images/circcyl1.png" style="width:100%">
      <br>
      <b>Figure:</b> \( T \) and \( \lambda \) varying over the surface of a circular cylinder
    </td>
    <td align="center" width="45%">
      <img src="/images/circ2.png" style="width:100%">
      <br>
      <b>Figure:</b> Skin Friction Coefficient over surface of circular cylinder
    </td>
  </tr>
</table>

<p align="center"><b>Figure:</b> Thwaites Method: Analysis of a circular cylinder</p>


