---
title: "Theoretical Solutions to Fluid Flow Equations"
excerpt: "This serves as a cookbook of the various solutions to fluid flow problems that are valuable."
author_profile: false
layout: splash
image: /images/pipeflowheader.jpg
caption: "Photo credit: tec-science"
header:
  overlay_color: "#2a4d8f"   
  hero_title: "Theoretical Solutions to Fluid Flow Equations"
  hero_excerpt: "This serves as a cookbook of the various solutions to fluid flow problems that are valuable."
order: 1
---

<a href="/academics/" class="button-gradient" style="display: inline-block; margin-top: 20px;">
  ← Back to Academic Works Page
</a>

## Plane Poiseuille Flow: Pressure-Driven Flow in a Slot

<p align="center">
  <img src="/images/pressuredrivenflowslot.jpg" alt="Pressure-Driven Flow in a Slot" width="50%">
  <br>
  <em>Figure: Pressure-Driven Flow in a Slot</em>
</p>

The governing equations are, 

Continuity 

$$ \begin{equation}
    \dfrac{\partial u}{\partial x} + \cancel{\dfrac{\partial v}{\partial y}}+ \cancel{\dfrac{\partial w}{\partial z}} = 0 
    \label{contslot}
\end{equation} $$

Momentum

$$\begin{align}
    \cancel{\dfrac{\partial u}{\partial t}} + \cancel{u \dfrac{\partial u}{\partial x}} + \cancel{v \dfrac{\partial u}{\partial y}} + \cancel{w \dfrac{\partial u}{\partial z}} &= -\dfrac{1}{\rho} \dfrac{\partial p}{\partial x} + \nu \nabla ^2 u \label{momslot}\\
    \cancel{\dfrac{\partial v}{\partial t}} + \cancel{u \dfrac{\partial v}{\partial x}} + \cancel{v \dfrac{\partial v}{\partial y}} + \cancel{w \dfrac{\partial v}{\partial z}} &= -\dfrac{1}{\rho} \dfrac{\partial p}{\partial y} + \cancel{\nu \nabla ^2 v} \label{pyslot} \\
    \cancel{\dfrac{\partial w}{\partial t}} + \cancel{u \dfrac{\partial w}{\partial x}} + \cancel{v \dfrac{\partial w}{\partial y}} + \cancel{w \dfrac{\partial w}{\partial z}} &= -\dfrac{1}{\rho} \dfrac{\partial p}{\partial z} + \cancel{\nu \nabla ^2 w} \label{pzslot}
\end{align}$$

Boundary Conditions 

$$ \begin{align*}
    u (y=0) &= 0 \\
    u(y=h) &=0
\end{align*} $$

The velocity is only a function of \\( y \\) because \\( \partial u/\partial x=0 \\), and the pressure is only a function of \\( x \\).

The relevant momentum equation is therefore Eq. \ref{momslot},

$$ \begin{equation*}
    \dfrac{\partial ^2 u}{\partial y^2} = \dfrac{1}{\mu} \dfrac{\partial p}{\partial x}
\end{equation*} $$

Integrating with respect to \\( y \\) twice,

$$ \begin{align*}
    \dfrac{d u}{dy} &= \dfrac{y }{\mu} \dfrac{dp}{dx} + C_1 \\
    u &= \dfrac{y^2}{2 \mu} \dfrac{dp}{dx} + C_1 y + C_2
\end{align*} $$

Plugging in the boundary conditions yields \\( C_1 = -\dfrac{h}{2 \mu} \dfrac{dp}{dx}, \quad C_2=0 \\), resulting in,

$$ \begin{equation}
    \boxed{u=-\dfrac{h^2}{2 \mu} \dfrac{dp}{dx} \left[ \dfrac{y}{h} - \left( \dfrac{y}{h}\right)^2\right]}
    \label{velprofnotnorm}
\end{equation} $$

To calculate the volume flow rate per unit depth,

$$ \begin{align*}
    Q = \int_{0}^{h} u \, dy = - \dfrac{h^2}{2 \mu} \dfrac{dp}{dx} \int_0^h \left[  \dfrac{y}{h} - \left( \dfrac{y}{h}\right)^2\right] \, dy
\end{align*} $$

$$ \begin{equation*}
    \boxed{Q = -\dfrac{h^3}{12 \mu} \dfrac{dp}{dx} = \dfrac{h^3}{12 \mu} \dfrac{\Delta p}{L}}
\end{equation*} $$

The maximum velocity is found at \\( y/h=0.5 \\). 

$$ \begin{equation*}
    u_{\text{max}}= - \dfrac{h^2}{8 \mu} \dfrac{dp}{dx}
\end{equation*} $$

Dividing Eq. \ref{velprofnotnorm} by the max velocity, I obtain the normalized velocity profile, 

$$ \begin{equation*}
    \boxed{\dfrac{u}{u_{\text{max}}}=\dfrac{4y}{h} \left(1-\dfrac{y}{h} \right)}
\end{equation*} $$

The shear stress,

$$ \begin{equation*}
    \tau_{yx} = \mu \dfrac{\partial u}{\partial y } = \dfrac{4 \mu u_{\text{max}}}{h} \left[ 1 - 2 \dfrac{y}{h}\right]
\end{equation*} $$

<p align="center">
  <img src="/images/slotflow.png" alt="Velocity and Shear Stress Distribution for Pressure-Driven Flow in a Slot" width="70%">
  <br>
  <em>Figure: Velocity and Shear Stress Distribution for Pressure-Driven Flow in a Slot</em>
</p>


## Plane Couette Flow: Moving Wall

The governing equation is,

Momentum

$$ \begin{equation*}
    \dfrac{d^2 u}{dy^2}=0
\end{equation*} $$

Boundary Conditions 

$$ \begin{align*}
    u (y=0) &= 0 \\
    u(y=h) &= U 
\end{align*} $$

Integrating the momentum equation twice, 

$$ \begin{equation*}
    u=C_1y + C_2 
\end{equation*} $$

Applying the boundary conditions results in a simple linear relation, 

$$ \begin{equation*}
    \boxed{u = \dfrac{Uy}{h}}
\end{equation*} $$

The shear stress is constant, 

$$ \begin{equation*}
    \tau_{yx} = \mu \dfrac{du}{dy} = \mu \dfrac{U}{h} 
\end{equation*} $$

## Plane Poiseuille-Couette Flow: Superposition

Suppose that we have a flow through a slot with a pressure gradient and a moving wall. 

The equation governing the flow is, 

$$ \begin{equation*}
    -\dfrac{1}{\rho} \dfrac{\partial p}{\partial x} + \nu \dfrac{\partial^2 u}{\partial y^2} = 0 
\end{equation*} $$

 With boundary conditions,

$$ \begin{align*}
    u (y=0) &= 0 \\
    u(y=h) &= U 
\end{align*} $$

We can form the solution to the Poisueille-Couette Flow by simply adding the Poiseuille solution to the Couette solution, since the governing differential equation and boundary condition are linear. 

The solution is, 

$$ \begin{equation*}
    \boxed{\dfrac{u}{U} = \left( 1 + \mathbb{P}\right) \dfrac{y}{h} - \mathbb{P} \left( \dfrac{y}{h}\right)^2, \quad \text{where } \mathbb{P} = -\dfrac{h^2}{2U\mu} \dfrac{dp}{dx}}
\end{equation*} $$

<p align="center">
  <img src="/images/poisueillecouetteflow.png" alt="Velocity Distribution of Poiseuille-Couette Flow" width="60%">
  <br>
  <em>Figure: Velocity Distribution of Poiseuille-Couette Flow</em>
</p>

## Circular Pipe Poiseuille Flow

The momentum equation governing the flow is,

$$ \begin{equation}
    \dfrac{1}{r} \dfrac{\partial}{\partial r} \left[ r \dfrac{\partial u_z}{\partial r}\right]= \dfrac{1}{\mu} \dfrac{\partial p}{\partial z}
    \label{poiseuilleflowcircpipe}
\end{equation} $$

With boundary condition, 

$$ \begin{align*}
    u_z(r=R) &= 0 \\ 
    u_z(r=0) &= \text{finite}
\end{align*} $$

If I integrate Eq. \ref{poiseuilleflowcircpipe},

$$ \begin{align*}
    \dfrac{\partial u_z}{\partial r} &= \dfrac{r}{2 \mu} \dfrac{\partial p}{\partial z} + \dfrac{C_1}{r} \\
    u_z &= \dfrac{r^2}{4 \mu} \dfrac{\partial p }{\partial z} + C_1 \ln (r) + C_2
\end{align*} $$

In order to make sure that \\( u_z \\) remains finite, \\( C_1 =0 \\). Applying the other boundary condition, we get \\( C_2 = - \dfrac{R^2}{4 \mu} \dfrac{\partial p}{\partial z} \\).

The solution is then,

$$ \begin{equation}
    \boxed{u_z = - \dfrac{R^2}{4 \mu} \dfrac{\partial p}{\partial z} \left[ 1 - \left( \dfrac{r}{R} \right)^2\right] = \dfrac{R^2}{4 \mu} \dfrac{\Delta p}{L} \left[ 1 - \left( \dfrac{r}{R} \right)^2\right]}
    \label{poiseuilleflowvelocityeqn}
\end{equation} $$

The maximum velocity is located at \\( r=0 \\), so \\( u_{\text{max}}=- \dfrac{R^2}{4 \mu} \dfrac{\partial p}{\partial z}  \\).

The shear stress is,

$$ \begin{equation*}
    \tau = \mu \dfrac{\partial u_z}{\partial r} = \dfrac{r}{2} \dfrac{\partial p}{\partial z}
\end{equation*} $$

The volume flow rate is, 

$$ \begin{align*}
    Q = \int\limits_{A} u_z dA= \int\limits_{0}^{R} u_z 2\pi r \, dr = \dfrac{-\pi R^4}{8 \mu} \dfrac{\partial p}{\partial z}
\end{align*} $$

## Circular Couette Flow

<p align="center">
  <img src="/images/circcouetteflow.jpg" alt="Diagram for Circular Couette Flow. Credit: Fluid Mechanics Sixth Edition Kundu, Cohen, Dowling" width="40%">
  <br>
  <em>Figure: Diagram for Circular Couette Flow. Credit: <cite>Fluid Mechanics Sixth Edition Kundu, Cohen, Dowling</cite></em>
</p>

The relevant governing equations are, 

$$ \begin{align*}
    -\dfrac{1}{\rho} \dfrac{\partial p}{\partial r} + \dfrac{u_\theta^2}{r} &=0 \\
    \mu \dfrac{\partial}{\partial r} \left[ \dfrac{1}{r} \dfrac{\partial}{\partial r} (r u_\theta)\right] &= 0
\end{align*} $$

Boundary Conditions

$$ \begin{align*}
    u_\theta (r = R_1) &= \Omega_1 R_1 \\ 
    u_\theta ( r = R_2) &= \Omega_2 R_2 
\end{align*} $$

We can integrate the second equation twice to obtain an equation for \\( u_\theta \\). Once this is found, we can then solve for the pressure with the first equation. At present, our main focus is to solve for \\( u_\theta \\). 

Upon integration,

$$ \begin{equation*}
    u_\theta = Ar + \dfrac{B}{r}
\end{equation*} $$

Using the boundary conditions, we can determine \\( A \text{ and } B \\).

$$ \begin{equation*}
    A = \dfrac{\Omega_2 R_2^2 - \Omega_1 R_1^2}{R_2^2 - R_1^2}, \quad B = \dfrac{- (\Omega_2 - \Omega_1)R_1^2 R_2^2}{R_2^2 - R_1^2}
\end{equation*} $$

The answer: 

$$ \begin{equation*}
    \boxed{u_\theta = \dfrac{\Omega_2 R_2^2 - \Omega_1 R_1^2}{R_2^2 - R_1^2} r - \dfrac{1}{r} \dfrac{(\Omega_2 - \Omega_1)R_1^2 R_2^2}{R_2^2 - R_1^2}}
\end{equation*} $$

## Stokes's First Problem: Rayleigh Problem

Let's start with the governing equation, 

$$ \begin{equation*}
    \dfrac{\partial u}{\partial t} = \nu \dfrac{\partial^2 u}{\partial y^2}
\end{equation*} $$

Boundary Conditions: 

$$ \begin{align*}
    u(y,t=0) &= 0 \\
    u(y=0,t) &= U_0 \\
    u(y\to\infty,t) &=0
\end{align*} $$

Let's introduce the similarity variable, 

$$ \begin{equation*}
    \eta = \dfrac{y}{2 \sqrt{\nu t}}
\end{equation*} $$

The partial differential equation can be reduced to an ordinary differential equation by assuming,

$$ \begin{equation*}
    \dfrac{u}{U_0} = f(\eta)
\end{equation*} $$

The equation to be solved is then, 

$$ \begin{equation}
    \dfrac{\partial f}{\partial t }= \nu \dfrac{\partial ^2 f}{\partial y^2}
    \label{stokesfirstproblemf}
\end{equation} $$

By chain rule, 

$$ \begin{align*}
    \dfrac{\partial f}{\partial t} &= \dfrac{\partial \eta}{\partial t} \dfrac{df}{d \eta} = -\dfrac{1}{2} \dfrac{\eta}{t} \dfrac{df }{d \eta} \\
    \dfrac{\partial f}{\partial y} &= \dfrac{\partial \eta }{\partial y} \dfrac{df}{d \eta} = \dfrac{1}{2 \sqrt{\nu t}} \dfrac{df}{d \eta} \\
    \dfrac{\partial^2 f}{\partial y^2} &= \dfrac{\partial }{\partial y} \left(\dfrac{\partial f}{\partial y} \right) = \dfrac{\partial \eta}{\partial y} \dfrac{\partial}{\partial \eta} \left( \dfrac{\partial f}{\partial y}\right)= \dfrac{1}{ 4 \nu t} \dfrac{d^2 f}{d \eta^2}
\end{align*} $$

If I plug these derivatives into Eq. \ref{stokesfirstproblemf}, the problem becomes an ODE.

$$ \begin{equation*}
    \dfrac{d^2 f}{d \eta^2} + 2 \eta \dfrac{df}{d \eta} = 0
\end{equation*} $$

This can be solved by integrating. Let's perform a substitution of variable, \\( w = \dfrac{df}{d \eta} \\),

$$ \begin{align*}
    \dfrac{d w}{d \eta} + 2 \eta w &= 0 \\
    \int \dfrac{dw}{w} &= \int -2 \eta \, d \eta \\
    \ln (w) &= -\eta^2 + C_1 \\
    w &= C_1 e^{-\eta^2} 
\end{align*} $$

Returning back to \\( f \\) variable,

$$ \begin{equation*}
    \dfrac{df}{d \eta} = C_1 e^{-\eta^2}
\end{equation*} $$

And integrating again, 

$$ \begin{equation*}
    f(\eta)= C_1 \left[ \int\limits_{0}^{\eta} e^{-\xi^2} \, d \xi \right] + C_2
\end{equation*} $$

The integral in brackets is actually a non-elementary function known as the **error function**. 

$$ \begin{equation*}
    \text{erf} (\eta) = \dfrac{2}{\sqrt{\pi}} \int\limits_0^\eta e^{-\xi^2} d \xi
\end{equation*} $$

Plugging this in,

$$ \begin{equation*}
    f(\eta) =C_1 \dfrac{\sqrt{\pi}}{2} \text{erf}(\eta) + C_2
\end{equation*} $$

To solve for the constants, we must convert the boundary conditions in terms of \\( f \\) and \\( \eta \\). 

$$ \begin{align*}
    u(y,t=0) &= 0 \enspace \longrightarrow \enspace f(\eta=\infty) =0 \\
    u(y=0,t) &= U_0 \enspace \longrightarrow \enspace f(\eta=0)=1\\
    u(y\to\infty,t) &=0 \enspace \longrightarrow \enspace f(\eta=\infty) = 0
\end{align*} $$

Using the fact that \\( \text{erf}(0)=0 \\) and \\( \text{erf}(\infty)=1 \\), as well as the transformed boundary conditions, we get, 

$$ \begin{equation*}
    C_1 = -\dfrac{2}{\sqrt{\pi}}, \quad C_2=1
\end{equation*} $$

The solution is then,

$$ \begin{equation*}
    \boxed{f(\eta) = 1 - \text{erf}(\eta), \quad \text{or } \dfrac{u}{U_0}=1-\text{erf} \left(\dfrac{y}{2\sqrt{\nu t}} \right)}
\end{equation*} $$

The vorticity is,

$$ \begin{equation*}
    \omega_z = - \dfrac{\partial u}{\partial y} = -\dfrac{U_0}{\sqrt{\pi \nu t}} e^{- \eta^2}
\end{equation*} $$

<p align="center">
  <img src="/images/stokesfirstprob.png" alt="Velocity Profile for Stokes's First Problem" width="50%">
  <br>
  <em>Figure: Velocity Profile for Stokes's First Problem</em>
</p>

## Stokes's Second Problem: Oscillating Plate

Now, instead of moving at a constant velocity, suppose the plate is oscillating with velocity \\( u_0 \sin (\Omega t) \\). 

$$ \begin{equation}
    \dfrac{\partial u}{\partial t} = \nu \dfrac{\partial ^2 u}{\partial y^2}
    \label{stokessecondprob}
\end{equation} $$

Boundary Conditions: 

$$ \begin{align*}
    u(y,t=0) &= 0 \\
    u(y\to \infty,t) &< \infty \\
    u(y=0,t) &= u_0 \sin (\Omega t)
\end{align*} $$

To aid in solving this problem, let's recast everything in nondimensional variables. 

$$ \begin{equation*}
    U = \dfrac{u}{u_0}, \quad T = \Omega t, \quad Y = \dfrac{y}{\sqrt{\nu/\Omega}}
\end{equation*} $$

From chain rule, 

$$ \begin{align*}
    \dfrac{\partial u}{\partial t} &= u_0 \dfrac{\partial U}{\partial t} = u_0 \dfrac{\partial T}{\partial t} \dfrac{\partial U}{\partial T} = u_0 \Omega \dfrac{\partial U}{\partial T} \\
    \dfrac{\partial u}{\partial y} &= u_0 \dfrac{\partial U}{\partial y}=u_0 \dfrac{\partial Y}{\partial y} \dfrac{\partial U}{\partial Y} = u_0 \left(\dfrac{\nu}{\Omega} \right)^{-1/2} \dfrac{\partial U}{\partial Y} \\
    \dfrac{\partial ^2 u}{\partial y^2} &= \dfrac{\partial}{\partial y} \left(\dfrac{\partial u}{\partial y} \right) = \dfrac{\partial Y}{\partial y} \dfrac{\partial}{\partial Y} \left( \dfrac{\partial u}{\partial y} \right) = \dfrac{\Omega u_0}{\nu} \dfrac{\partial^2 U}{\partial Y^2}
\end{align*} $$

In terms of the nondimensional variables, Eq. \ref{stokessecondprob} becomes, 

$$ \begin{equation}
    \dfrac{\partial U}{\partial T} = \dfrac{\partial^2 U}{\partial Y^2}
    \label{stokessecondprobnondimensional}
\end{equation} $$

Boundary Conditions: 

$$ \begin{align*}
    U(Y,T=0) &= 0 \\
    U(Y \to \infty, T) &= 0 \\
    U(Y=0,T) &= \sin(T) =\text{Im} (e^{iT})
\end{align*} $$

For the steady-state solution, we assume that \\( U \\) is of the form, 

$$ \begin{equation*}
    U = f(Y) e^{iT}
\end{equation*} $$

Taking the derivatives, 

$$ \begin{align*}
    \dfrac{\partial U}{\partial T} &= f(Y) i e^{iT} \\
    \dfrac{\partial U}{\partial Y} &= f'(Y) e^{iT} \\
    \dfrac{\partial ^2 U}{\partial Y^2} &= f''(Y) e^{iT}
\end{align*} $$

And plugging this to Eq. \ref{stokessecondprobnondimensional},

$$ \begin{equation*}
    \bigg(f''(Y) - i f(Y) \bigg) e^{iT} = 0
\end{equation*} $$

$$ \begin{equation}
    f''(Y) - i f(Y) = 0
    \label{stokessecondprobODE}
\end{equation} $$

Guessing a solution of the form,

$$ \begin{align*}
    f(Y) &= A e^{aY} \\
    f'(Y) &= Aa e^{aY} \\
    f''(Y) &= Aa^2 e^{aY}
\end{align*} $$

Plugging this into Eq. \ref{stokessecondprobODE},

$$ \begin{equation*}
    Ae^{aY} (a^2-i) = 0 \ \longrightarrow \ a = \pm \sqrt{i} = \pm \dfrac{1}{\sqrt{2}} (1+i) 
\end{equation*} $$


<details class="custom-collapse">
  <summary><h3>Computing the Square Root of Imaginary Number</h3></summary>
  <div class="collapse-content">

    <p> Suppose I have a complex number, \( a = a_r + i a_{m} \). I compute its square, </p>

    $$ \begin{align*}
        a^2 = (a_r + i a_{m})(a_r + i a_{m}) = a_r^2 - a_m^2 + i 2 a_r a_m
    \end{align*} $$

    <p> Setting \( a_r^2 - a_m^2=0, \ 2a_r a_m = 1 \), we get \( a^2=i \) and by definition, \( a = \pm \sqrt{i} \). </p>

    \[
    \left\{
    \begin{aligned}
        a_r^2 - a_m^2 &= 0 \\
        2a_r a_m &= 1
    \end{aligned}
    \right\}
    \]

    Solving the above system of equations in curly braces,

    $$ \begin{equation*}
        a_r = a_m = \pm \dfrac{1}{\sqrt{2}}
    \end{equation*} $$

    So that,

    $$ \begin{equation*}
        \boxed{a = \pm \dfrac{1}{\sqrt{2}} (1+i)}
    \end{equation*} $$

  </div>
</details>

Finally,

$$ \begin{equation*}
    U = A e^{\pm \frac{1}{\sqrt{2}}(1+i)Y} e^{iT}
\end{equation*} $$

Comparing with the boundary conditions, we get that \\( A=1 \\).

$$ \begin{equation*}
    U = \text{Im} \left[ e^{-\frac{Y}{\sqrt{2}}} e^{i \left(T-\frac{Y}{\sqrt{2}} \right)}\right]
\end{equation*} $$

Finally,

$$ \begin{equation}
    \boxed{U = e^{-\frac{Y}{\sqrt{2}}} \sin \left(T- \frac{Y}{\sqrt{2}}\right)}
    \label{stokessecondproblemanswer}
\end{equation} $$

<p align="center">
  <img src="/images/stokesoscillating.png" alt="Stokes' Flow Near an Oscillating Plate. The wall oscillates as U₀ = sin T" width="70%">
  <br>
  <em>Figure: Stokes' Flow Near an Oscillating Plate. The wall oscillates as U₀ = sin T</em>
</p>

### Change of Reference Frame: Stokes's Second Problem

Suppose we have a different but similar problem. The plate is stationary, but the velocity far away sinusoidal. The problem is formulated as,

$$ \begin{equation*}
    \dfrac{\partial \overline{U}}{\partial T} = -\dfrac{d \overline{P}}{dX} + \dfrac{\partial ^2 \overline{U}}{\partial Y^2}
\end{equation*} $$

Boundary Conditions: 

$$ \begin{align*}
    \overline{U}(Y\to \infty, T) &= \sin T \\
    \overline{U} (Y = 0,T) &= 0 
\end{align*} $$

To get the answer, we take the negative of Eq. \ref{stokessecondproblemanswer} and add \\( 
\sin T \\).

$$ \begin{equation*}
    \boxed{\overline{U} = \sin T - e^{-\frac{Y}{\sqrt{2}}} \sin \left( T-\dfrac{Y}{\sqrt{2}}\right)}
\end{equation*} $$

<p align="center">
  <img src="/images/stokessecondprob2.png" alt="Oscillating stream above a wall. The free stream oscillates sin T" width="70%">
  <br>
  <em>Figure: Oscillating stream above a wall. The free stream oscillates sin T</em>
</p>

## Flow in a Slot with Oscillating Pressure Gradient

Let's try the following PDE,

$$ \begin{equation*}
    \dfrac{\partial u}{\partial t} = K \cos \Omega t + \nu \dfrac{\partial ^2 u}{\partial y^2}
\end{equation*} $$

Boundary Conditions

$$ \begin{align*}
    u(y=h) &=0 \\
    \dfrac{\partial u}{\partial y} (y=0)&=0
\end{align*} $$

Defining non-dimensional variables,

$$ \begin{equation*}
    T = \Omega t, \quad Y = \dfrac{y}{h}, \quad U = \dfrac{u}{\alpha}
\end{equation*} $$

Chain rules,

$$ \begin{align*}
    \dfrac{\partial u}{\partial t} &= \dfrac{\partial T}{\partial t} \dfrac{\partial (\alpha U)}{\partial T}= \Omega \alpha \dfrac{\partial U}{\partial T} \\
    \dfrac{\partial u}{\partial y } &= \dfrac{\partial Y}{\partial y} \dfrac{\partial (\alpha U)}{\partial Y} =\dfrac{\alpha}{h} \dfrac{\partial U}{\partial Y} \\
    \dfrac{\partial^2 u}{\partial y^2} &= \dfrac{\partial}{\partial y} \left( \dfrac{\partial u}{\partial y} \right)=\dfrac{\partial Y}{\partial y} \dfrac{\partial}{\partial Y} \left( \dfrac{\partial u}{\partial y} \right)= \dfrac{\alpha}{h^2} \dfrac{\partial^2 U}{\partial Y^2}
\end{align*} $$

Substituting these into the governing PDE and then replacing the cosine function with a complex exponential, 

$$ \begin{align*}
    \dfrac{\Omega \alpha}{K} \dfrac{\partial U}{\partial T} = e^{iT} + \dfrac{\nu \alpha}{h^2 K} \dfrac{\partial^2 U}{\partial Y^2}
\end{align*} $$

Choosing \\( \alpha = \dfrac{K}{\Omega} \\),

$$ \begin{equation*}
    \dfrac{\partial U}{\partial T} = e^{iT} + \dfrac{\nu}{h^2 \Omega} \dfrac{\partial^2 U}{\partial Y^2}
\end{equation*} $$

Defining \\( \Lambda = \dfrac{h}{\sqrt{2 \nu / \Omega }} \\),

$$ \begin{equation}
    \dfrac{\partial U}{\partial T} = e^{iT} + \dfrac{1}{2 \Lambda^2} \dfrac{\partial^2 U}{\partial Y^2}
    \label{oscpresgrad}
\end{equation} $$

The boundary conditions become,

$$ \begin{align*}
    U(Y=1,T) &= 0 \\
    \dfrac{\partial U}{\partial Y}(Y=0,T) &= 0 
\end{align*} $$

We guess a solution to Eq. \ref{oscpresgrad} in the form of,

$$ \begin{equation*}
    U = e^{iT} F(Y)
\end{equation*} $$

Its derivatives,

$$ \begin{align*}
    \dfrac{\partial U}{\partial T} &= i e^{iT}F(Y) \\ 
    \dfrac{\partial U}{\partial Y} &= e^{iT} F'(Y) \\
    \dfrac{\partial ^2 U}{\partial Y^2} &= e^{iT} F''(Y)
\end{align*} $$

Plugging this into Eq. \ref{oscpresgrad}, we get the differential equation, 

$$ \begin{equation*}
    \dfrac{1}{2 \Lambda^2} F''(Y) - i F(Y) + 1 =0 
\end{equation*} $$

Boundary Conditions: 

$$ \begin{align*}
    F (Y=1) &= 0 \\
    F'(Y=0) &= 0
\end{align*} $$

Making another change of variables yet again, \\( \widehat{F}=F + i \\)

$$ \begin{equation*}
    \widehat{F}''(Y) = i 2 \Lambda^2 \widehat{F}(Y)
\end{equation*} $$

Boundary Conditions: 

$$ \begin{align*}
    \widehat{F}(Y=1) &= i \\
    \widehat{F}'(Y=0) &= 0 
\end{align*} $$

Guessing a solution of the form, \\( \widehat{F}=e^{BY} \\),

$$ \begin{align*}
    B^2 - i 2 \Lambda^2 &= 0 \\
    B &= \pm \Lambda \sqrt{2 i} = \pm \Lambda (1+i)
\end{align*} $$

So the general form of the solution is,

$$ \begin{equation*}
    \widehat{F} = C_1 e^{\Lambda Y\sqrt{2 i}} + C_2 e^{- \Lambda Y\sqrt{2i}}
\end{equation*} $$

Applying the boundary conditions, 

$$ \begin{equation*}
    C=C_1 = C_2 = \dfrac{i}{e^{\Lambda \sqrt{2i}} + e^{-\Lambda \sqrt{2 i }}}
\end{equation*} $$

$$ \begin{align*}
    \widehat{F} &= i \dfrac{e^{\Lambda Y \sqrt{2 i}}+e^{- \Lambda Y\sqrt{2 i}}}{e^{\Lambda \sqrt{2 i}}+e^{-\Lambda \sqrt{2 i}}} \\
    &= i \dfrac{ \cosh (\Lambda Y \sqrt{2i})}{\cosh (\Lambda \sqrt{2 i })}
\end{align*} $$

Finally, we obtain 

$$ \begin{equation*}
    \boxed{U = \left[ -1 +  \dfrac{ \cosh (\Lambda Y \sqrt{2i})}{\cosh (\Lambda \sqrt{2 i })}\right] i e^{iT}}
\end{equation*} $$

More specifically, since we complexified the \\( \cos (T) \\) term earlier, the answer is actually the real part of the boxed equation above. 

## Oseen Vortex

The Oseen vortex is a vortex that, at time \\( t=0 \\), viscous effects are active. 

Governing Equation: 

$$ \begin{equation*}
    \dfrac{\partial u_\theta}{\partial t} = - \dfrac{\nu}{r^2} \dfrac{\partial}{\partial r} (r u_\theta)
    + \dfrac{\nu}{r} \dfrac{\partial^2}{\partial r^2} (r u_\theta)
\end{equation*} $$

Boundary Conditions: 

$$ \begin{align*}
    u_\theta(r=0,t) &= 0 \\
    u_\theta (r \to \infty, t) & \sim \dfrac{\Gamma}{2 \pi r} \\
    u_\theta(r,t=0) &= \dfrac{\Gamma}{ 2 \pi r}
\end{align*} $$

If I define the variable,

$$ \begin{equation*}
    \gamma^* = \dfrac{u_\theta}{\Gamma / (2 \pi r)} = \dfrac{r u_\theta}{\Gamma / (2 \pi )}
\end{equation*} $$

and its derivatives, 

$$ \begin{align*}
    \dfrac{\partial \gamma^*}{\partial t} &= \dfrac{2 \pi r}{\Gamma} \dfrac{\partial u_\theta}{\partial t} \\
    \dfrac{\partial \gamma^*}{\partial r} &= \dfrac{2 \pi}{\Gamma} \dfrac{\partial}{\partial r} (r u_\theta) \\
    \dfrac{\partial^2 \gamma^*}{\partial r^2} &= \dfrac{2 \pi}{\Gamma} \dfrac{\partial^2}{\partial r^2} (r u_\theta)
\end{align*} $$

I can rewrite the governing equation as, 

$$ \begin{equation}
    \dfrac{\partial \gamma^*}{\partial t} = -\dfrac{\nu}{r} \dfrac{\partial \gamma^*}{\partial r} + \nu \dfrac{\partial^2 \gamma^*}{\partial r^2}
    \label{oseenvortexrewrite}
\end{equation} $$

With boundary conditions: 

$$ \begin{align*}
    \gamma^*(r=0,t) &= 0 \\
    \gamma^*(r \to \infty , t) & \sim 1 \\
    \gamma^* (r,t=0) &= 1
\end{align*} $$

Now, I define the similarity variable and assume that \\( \gamma^* \\) is only a function of the similarity variable, 

$$ \begin{align*}
    \eta &= \dfrac{r}{\sqrt{\nu t}} \\
    \gamma^* &= f(\eta)
\end{align*} $$

The derivatives become, 

$$ \begin{align*}
    \dfrac{\partial \gamma^*}{\partial t} &= \dfrac{\partial \eta }{\partial t} \dfrac{df}{d \eta} = - \dfrac{r}{2 \sqrt{\nu t^3}} \dfrac{df }{d \eta} \\
    \dfrac{\partial \gamma^*}{\partial r} &= \dfrac{\partial \eta}{\partial r} \dfrac{df}{d \eta} = \dfrac{1}{\sqrt{\nu t}} \dfrac{df }{d \eta} \\
    \dfrac{\partial^2 \gamma^*}{\partial r^2} &= \dfrac{\partial}{\partial r} \left( \dfrac{\partial \gamma^*}{\partial r}\right) = \dfrac{\partial \eta}{\partial r} \dfrac{\partial }{\partial \eta} \left( \dfrac{\partial \gamma^*}{\partial r}\right) = \dfrac{1}{\nu t} \dfrac{d^2 f }{d \eta^2}
\end{align*} $$

Plugging the above derivatives into Eq. \ref{oseenvortexrewrite} and simplifying, 

$$ \begin{equation*}
    \dfrac{d^2 f}{d \eta^2} + \left[\dfrac{\eta}{2} - \dfrac{1}{\eta} \right] \dfrac{df}{d \eta} = 0 
\end{equation*} $$

Boundary Conditions: 

$$ \begin{align*}
    f ( \eta =0 ) &= 0 \\ 
    f(\eta \to \infty) & \sim 1 \\
    f(\eta \to \infty) & =1 
\end{align*} $$

Upon integration twice and plugging in the boundary conditions, 

$$ \begin{equation*}
    \boxed{f = 1 - e^{-\eta^2/4}}
\end{equation*} $$

$$ \begin{equation*}
   \boxed{ u_\theta = \dfrac{\Gamma}{2 \pi r} \left[ 1 - e^{-\frac{r^2}{4 \nu t}}\right]}
\end{equation*} $$

The vorticity, 

$$ \begin{equation*}
    \omega_z = \dfrac{1}{r} \dfrac{\partial}{\partial r} (r u_\theta) = \dfrac{\Gamma}{4 \pi \nu t} e^{- \frac{r^2}{4 \nu t}}
\end{equation*} $$

## Burgers Vortex

The Oseen vortex is an unsteady flow because of viscous diffusion, which spreads out throughout the flow. Suppose we wanted to make the flow steady. We can accomplish this by adding a radial inflow. This keeps the viscosity from diffusing outward, eliminating the time dependence. 

The radial inflow is \\( u_r = -ar \\). By continuity, \\( u_z=2az \\) (the flow has to exit somewhere). 

The governing momentum equation is, 

$$ \begin{equation*}
    u_r \dfrac{\partial u_\theta}{\partial r} + \dfrac{u_r u_\theta}{r} = \nu \dfrac{\partial}{ \partial r} \left[ \dfrac{1}{r} \dfrac{\partial}{\partial r}(r u_\theta)\right]
\end{equation*} $$


Plugging in \\( u_r = -ar \\), 

$$ \begin{equation}
    -a \left[ r \dfrac{d u_\theta}{dr} + u_\theta\right] = \nu \dfrac{d}{dr} \left[\dfrac{1}{r} \dfrac{d}{dr}(r u_\theta) \right]
    \label{burgersvortexdiffeqn}
\end{equation} $$

Boundary Conditions: 

$$ \begin{align*}
    u_\theta(r=0) &=0 \\
    u_\theta (r \to \infty) &= \dfrac{\Gamma}{2 \pi r}
\end{align*} $$

Defining the variable, 

$$ \begin{equation*}
    \gamma^* = f =\dfrac{r u_\theta}{\Gamma/(2 \pi)}
\end{equation*} $$

Eq. \ref{burgersvortexdiffeqn} becomes,

$$ \begin{equation*}
    -a \dfrac{df}{dr} = \nu \dfrac{d}{dr} \left[ \dfrac{1}{r} \dfrac{df}{dr}\right]
\end{equation*} $$

For the dependent variable, we choose, 

$$ \begin{equation*}
    \eta = \dfrac{r}{\sqrt{\nu/(2a)}}
\end{equation*} $$

So that the above equation becomes,

$$ \begin{equation*}
    -a \dfrac{df}{d \eta} \dfrac{d \eta}{dr} = \nu \dfrac{d \eta}{dr} \dfrac{d}{d \eta} \left[\dfrac{1}{r} \dfrac{d \eta}{dr} \dfrac{df}{d \eta} \right]
\end{equation*} $$

Upon simplification, 

$$ \begin{equation*}
    \dfrac{d^2 f}{d \eta^2} + \left[ \dfrac{\eta}{2} - \dfrac{1}{\eta}\right] \dfrac{df}{d \eta} = 0
\end{equation*} $$

The solution of which is the same as for the Oseen vortex (except that \\( \eta \\) is defined differently).

$$ \begin{equation*}
    \boxed{f = 1 - e^{-\eta^2/4}}
\end{equation*} $$

$$ \begin{equation*}
    \boxed{u_\theta = \dfrac{\Gamma}{2 \pi r} \left[ 1 - e^{-\frac{r^2}{2\nu/a}}\right]}
\end{equation*} $$

## Rotary Viscous Coupling

<p align="center">
  <img src="/images/rotaryviscouscoupling.jpg" alt="Diagram for Rotary Coupling" width="50%">
  <br>
  <em>Figure: Diagram for Rotary Coupling</em>
</p>

$$ \begin{equation*}
    \dfrac{\partial}{\partial r} \left[ \dfrac{1}{r} \dfrac{\partial}{\partial r} (r u_\theta)\right] + \dfrac{\partial^2 u_\theta}{\partial z^2} = 0 
\end{equation*} $$

Boundary Conditions: 

$$ \begin{align*}
    u_\theta(r,z=0) &= 0 \\
    u_\theta(r,z=h)&= r \Omega \\
    u_\theta (r=R,z)&=0
\end{align*} $$

Let's introduce nondimensional variables, 

$$ \begin{equation*}
    r^* = \dfrac{r}{R}, \quad z^*= \dfrac{z}{h}, \quad u_\theta^* = \dfrac{u_\theta}{R \Omega}, \quad \varepsilon = \dfrac{h}{R}
\end{equation*} $$

so that the governing differential equation becomes, 

$$ \begin{equation}
    \varepsilon^2 \dfrac{\partial }{\partial r^*} \left[ \dfrac{1}{r^*} \dfrac{\partial}{\partial r^*} (r^* u_\theta^*)\right] + \dfrac{\partial^2 u_\theta^*}{\partial z^{*2}}=0
    \label{rotaryviscousdiffeq}
\end{equation} $$

and the boundary conditions transform to,

$$ \begin{align*}
    u_\theta^* (r^*,z^*=0) &= 0 \\
    u_\theta^* (r^*, z^*=1) &= r^* \\
    u_\theta^* (r^*=1,z^*) &= 0 
\end{align*} $$

If the gap width is small compared to the radius, then \\( \varepsilon \to 0 \\) and the first term in Eq. \ref{rotaryviscousdiffeq} disappears, leaving 

$$ \begin{equation*}
    \dfrac{\partial^2 u_\theta^*}{\partial z^2} = 0
\end{equation*} $$

<p>This solution can only satisfy the first two boundary conditions and is not valid for the region near the wall (where \( u_\theta^*=0 \) at \( r^*=1 \)), and thus is called the <strong>outer solution</strong>. </p>

$$ \begin{equation*}
    u_{\theta, \text{outer}}^* = r^* z^*
\end{equation*} $$

For the inner solution, we scale y differently. We expect y to scale with the gap width, or \\( h \\). Basically, we are zooming in on the region near the wall. 

$$ \begin{equation*}
    y^* = \dfrac{y}{h} = \dfrac{R-r}{h} = \dfrac{1-r^*}{\varepsilon}
\end{equation*} $$

Eq. \ref{rotaryviscousdiffeq} transforms to, 

$$ \begin{equation*}
    \dfrac{\partial}{\partial y^*} \left\{ \dfrac{1}{1 - \varepsilon y^*} \dfrac{\partial}{\partial y^*} \bigg[ (1-\varepsilon y^*) u_\theta^* \bigg]\right\} + \dfrac{\partial^2 u_\theta^*}{\partial z^{*2}}=0
\end{equation*} $$

As \\( \varepsilon \to 0 \\), the differential equation for the inner solution is, 

$$ \begin{equation*}
    \dfrac{\partial^2 u_\theta^*}{\partial y^{*2}} + \dfrac{\partial^2 u_\theta^*}{\partial z^{*2}}=0
\end{equation*} $$

$$ \begin{align*}
    u_\theta^*(y^*, z^*=0) &= 0 \\
    u_\theta^*(y^*, z^*=1) &= 1 \\
    u_\theta^*(y^*=0,z^*) &= 0 \\
    u_\theta^*(y^* \to \infty,z^*) &=u^*_{\theta, \text{outer}} (r^*=1, z^*) = z^*
\end{align*} $$

Solving this involves the **separation of variables** technique.

**TO BE CONTINUED**

## Flow in a Slot with Porous Walls

<p align="center">
  <img src="/images/porouswalls.jpg" alt="Diagram of Porous Wall" width="50%">
  <br>
  <em>Figure: Diagram of Porous Wall</em>
</p>

Here are all the non-dimensional variables, 

$$
x^* = \dfrac{x}{h} \qquad 
y^* = \dfrac{y}{h} \qquad
u^* = \dfrac{u}{U_{\text{ave}}} \qquad
v^* = \dfrac{v}{U_{\text{ave}}}
\notag
$$

$$
\psi^* = \dfrac{\psi}{U_{\text{ave}}h} \qquad
v_0^* = \dfrac{v_0}{U_{\text{ave}}} \qquad
\text{Re} = \dfrac{U_{\text{ave}}h}{\nu} \qquad
\alpha = v_0^* \text{Re} = \dfrac{v_0 h}{\nu}
\notag
$$

The boundary conditions are: 

$$\begin{align*}
    u(x,0) &= 0 \longrightarrow u^*(x^*,0) = 0 \\
    u(x,h) &= 0 \longrightarrow u^*(x^*,1) = 0 \\
    v(x,0) &= v_0 \longrightarrow v^*(x^*,0) = v_0^* \\
    v(x,h) &= v_0 \longrightarrow v^*(x^*,1) = v_0^*
\end{align*}$$

One way to solve this is to use the governing streamfunction equation for 2D, steady, planar incompressible flow, derived in LINK SECTION HERE, repeated below

$$\begin{equation}
    \dfrac{\partial \psi}{\partial y} \dfrac{\partial (\nabla^2 \psi)}{\partial x} - \dfrac{\partial \psi}{\partial x} \dfrac{\partial (\nabla^2\psi)}{\partial y} = \nu \nabla^4 \psi
    \label{streamfunctiondifferentialequation}
\end{equation}$$

where 

$$\begin{equation*}
    \nabla^4 \psi = \psi_{xxxx} + 2\psi_{xxyy} + \psi_{yyyy}
\end{equation*}$$

Rewriting Eq. \ref{streamfunctiondifferentialequation} in terms of non-dimensional variables, 

$$\begin{equation}
    \text{Re} \left[ 
    \dfrac{\partial \psi^*}{\partial y^*} \dfrac{\partial (\nabla^{*2} \psi^*)}{\partial x^*} - 
    \dfrac{\partial \psi^*}{\partial x^*} \dfrac{\partial (\nabla^{*2} \psi^*)}{\partial y^*} 
    \right] = \nabla^{*4} \psi^*
    \label{nondimensionalstreamfunction}
\end{equation}$$

We assume the solution is in the form, 

$$\begin{equation*}
    \psi^* = - v_0^* x^* + F(y^*)
\end{equation*}$$

Plugging this into Eq. \ref{nondimensionalstreamfunction} and noting that \\( \alpha = v_0^*\text{Re} \\), the equation reduces to a simple fourth order ODE. 

$$\begin{equation}
    F^{(4)} = \alpha F''' 
    \label{fourthorderODEporous}
\end{equation}$$

The boundary conditions transform to,

$$\begin{align*}
    \psi^*(0,0) = 0 &= F(0) \\
    u^*(x^*,0) = 0 &= F'(0) \\
    u^*(x^*,1) = 0 &= F'(1) \\
    \psi^*(x^*,1) - \psi^*(x^*,0) = 1 &= F(1)
\end{align*}$$

Integrating Eq. \ref{fourthorderODEporous} multiple times, I end up with, 

$$\begin{equation*}
    F = C_1 \dfrac{e^{\alpha y}}{\alpha^3} + C_2 \dfrac{y^2}{2} + C_3 y + C_4
\end{equation*}$$

and the velocity,

$$\begin{equation*}
    \boxed{u^* = \dfrac{\partial \psi^*}{\partial y^*} = F' = C_1 \dfrac{e^{\alpha y }}{\alpha^2} + C_2 y + C_3}
\end{equation*}$$

With the boundary conditions, we can solve for all the constants, 

$$\begin{align*}
    C_1 &= \dfrac{2 \alpha^3}{(2-\alpha)e^\alpha-\alpha-2} \\
    C_2 &= \dfrac{1}{\alpha^2} \left[ 1 - e^\alpha \right] C_1 \\
    C_3 &= - \dfrac{C_1}{\alpha^2} \\
    C_4 &= - \dfrac{C_1}{\alpha^3}
\end{align*}$$

<p align="center">
  <img src="/images/porouswallgraph.png" alt="Velocity Distribution for Porous Wall" width="50%">
  <br>
  <em>Figure: Velocity Distribution for Porous Wall</em>
</p>

<a href="/academics/" class="button-gradient" style="display: inline-block; margin-top: 20px;">
  ← Back to Academic Works Page
</a>