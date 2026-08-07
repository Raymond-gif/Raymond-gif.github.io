---

title: "Streamfunctions, Vector Potential, High-Re Flows, Low-Re Flows"
excerpt: "I cover high-Re-number flows, low-Re-number flows, streamfunctions, vector potential."
author_profile: false
layout: splash
image: /images/streamsurfaces.jpg
caption: 
header:
  overlay_color: "#2a4d8f"   
  hero_title: "Streamfunctions, Vector Potential, High-Re Flows, Low-Re Flows"

---

## High-Reynolds-Number Flows

Let us restate the incompressible flow momentum equation, 

$$ \begin{equation*}
    \dfrac{D \mathbf{u}}{Dt} = - \dfrac{\nabla p}{\rho} + \nu \nabla^2 \mathbf{u}
\end{equation*} $$

If we nondimensionalize this using the following change of variables,

$$ \begin{equation*}
    \mathbf{u}^* = \dfrac{\mathbf{u}}{U}, \quad p^* = \dfrac{p - p_0}{\rho U^2}, \quad t^* = \dfrac{Ut}{L}, \quad \mathbf{x}^* = \dfrac{\mathbf{x}}{L}
\end{equation*} $$

we obtain the following, 

$$ \begin{equation*}
    \dfrac{D \mathbf{u}^*}{Dt^*} = -\nabla^* p^* + \dfrac{1}{\text{Re}} \nabla^{*2} \mathbf{u}^*
\end{equation*} $$

Let Re \\( \to \infty \\),

$$ \begin{equation*}
    \boxed{\dfrac{D \mathbf{u}^*}{Dt^*} = -\nabla^* p^* }
\end{equation*} $$

Similarly, for the vorticity equation,

$$ \begin{equation*}
    \dfrac{D \boldsymbol{\omega}}{Dt} = \boldsymbol{\omega} \cdot \nabla \mathbf{u} + \nu \nabla^2 \boldsymbol{\omega}
\end{equation*} $$

For the vorticity, the proper scale is,

$$ \begin{equation*}
    \boldsymbol{\omega}^* = \dfrac{\boldsymbol{\omega}}{U/L}
\end{equation*} $$

$$ \begin{equation*}
    \dfrac{D \boldsymbol{\omega}^*}{D t^*} = \boldsymbol{\omega}^* \cdot \nabla^* \mathbf{u}^* + \dfrac{1}{\text{Re}} \nabla^{*2} \boldsymbol{\omega}^*
\end{equation*} $$

Let Re \\( \to \infty \\),

$$ \begin{equation*}
    \boxed{\dfrac{D \boldsymbol{\omega}^*}{D t^*} = \boldsymbol{\omega}^* \cdot \nabla^* \mathbf{u}^*}
\end{equation*} $$

## Stokes Flow: Low-Reynolds-Number Flows

For low Re flows, the pressure is scaled differently. Every other variable is scaled the same as in the high Reynolds Number flows.   

$$ \begin{equation*}
    p^{**} = \dfrac{p-p_0}{\mu U/L}
\end{equation*} $$

The momentum equation becomes, 

$$ \begin{equation*}
    \text{Re} \dfrac{D \mathbf{u}^*}{Dt^*} = - \nabla^* p^{**} + \nabla^{* 2} \mathbf{u}^*
\end{equation*} $$

The limit as Re \\( \to 0 \\).

$$ \begin{equation} 
    \nabla^* p^{**}  =  \nabla^{* 2} \mathbf{u}^* 
   \label{stokespressureviscous}
\end{equation} $$

If we take the divergence of Eq. \ref{stokespressureviscous}, we obtain, 

$$ \begin{equation*}
    \nabla^{* 2} p^{**} = \nabla^{* 2} \cancelto{0}{( \nabla^* \cdot \mathbf{u}^*)}
\end{equation*} $$

Finally, 

$$ \begin{equation*}
    \boxed{\nabla^{* 2} p^{**}=0}
\end{equation*} $$

The non-dimensional vorticity equation is the same as for the high Reynolds number case, except that Re \\( \to 0 \\)  

$$ \begin{equation*}
   \text{Re} \dfrac{D \boldsymbol{\omega}^*}{D t^*} =  \text{Re} \  [\boldsymbol{\omega}^* \cdot \nabla^* \mathbf{u}^* ] +  \nabla^{*2} \boldsymbol{\omega}^*
\end{equation*} $$

$$ \begin{equation} 
    \boxed{\nabla^{* 2} \boldsymbol{\omega}^*=0}
    \label{laplacianvorticitystokesflow}
\end{equation} $$

## Streamfunction in 2D-Planar Incompressible Flows

### Incompressible Momentum Equation in terms of Streamfunction

The incompressible continuity equation is,

$$ \begin{equation*}
    \dfrac{\partial u}{\partial x} + \dfrac{\partial v}{\partial y} = 0
\end{equation*} $$

The streamfunction is defined to satisfy the continuity equation automatically, so 

$$ \begin{equation} 
    u = \dfrac{\partial \psi}{\partial y}, \quad v = -\dfrac{\partial \psi}{\partial x} 
    \label{velstreamdef}
\end{equation} $$

The vorticity is,

$$ \begin{equation} 
    \omega = \omega_z = \dfrac{\partial v}{\partial x} - \dfrac{\partial u}{\partial y} = - \nabla^2 \psi
    \label{vorticitydef}
\end{equation} $$

The momentum equations are, 

$$\begin{align}
    \dfrac{\partial u }{\partial t} + u \dfrac{\partial u}{\partial x} + v \dfrac{\partial u }{\partial y} &= -\dfrac{1}{\rho} \dfrac{\partial p}{\partial x} + \nu \dfrac{\partial^2 u}{\partial x^2} + \nu \dfrac{\partial^2 u}{\partial y^2} \label{umom}\\
    \dfrac{\partial v }{\partial t} + u \dfrac{\partial v}{\partial x} + v \dfrac{\partial v }{\partial y} &= -\dfrac{1}{\rho} \dfrac{\partial p}{\partial y} + \nu \dfrac{\partial^2 v}{\partial x^2} + \nu \dfrac{\partial^2 v}{\partial y^2} \label{vmom}
\end{align}$$

Derive Eq. \ref{umom} by y and derive Eq. \ref{vmom} by x. Then, we eliminate the pressure term by subtracting the two equations. After some manipulation, we then use Eq. \ref{vorticitydef} to rewrite the two equations. The result is, 

$$ \begin{equation*}
    \dfrac{\partial \omega}{\partial t} + u \dfrac{\partial \omega}{\partial x} + v \dfrac{\partial \omega}{\partial y} = \nu \nabla^2 \omega
\end{equation*} $$

Substituting in the streamfunction,

<div class="equation-box">
  <h3>Vorticity-Streamfunction Equation</h3>
  <div>

$$ \begin{equation} 
    \dfrac{\partial (\nabla^2 \psi)}{\partial t} + \dfrac{\partial \psi}{\partial y} \dfrac{\partial (\nabla^2 \psi)}{\partial x} - \dfrac{\partial \psi}{\partial x} \dfrac{\partial (\nabla^2\psi)}{\partial y} = \nu \nabla^4 \psi
    \label{streamfunctiondifferentialequation}
\end{equation} $$

where 

$$ \begin{equation*}
    \nabla^4 \psi = \psi_{xxxx} + 2\psi_{xxyy} + \psi_{yyyy}
\end{equation*} $$

  </div>
</div>

## Vector Potential: Generalization of the Streamfunction

For flows with symmetry, where only two velocity components are nonzero, it is still possible to use the concept of the streamfunction to solve problems. However, we must generalize the above results to include axisymmetric flows. 

This is accomplished by introducing the **vector potential**, which can be thought as the higher-dimensional analogue of the streamfunction. For example, we know that the streamfunction is defined to automatically satisfy the continuity equation. In vector notation, the full continuity equation is, 

$$ \begin{equation*}
    \nabla \cdot \mathbf{u} = 0 
\end{equation*} $$

If we define a vector function \\( \mathbf{B} \\) , such that \\( \mathbf{u} = \nabla \times \mathbf{B} \\) , then continuity is automatically satisfied. Divergence of a curl is zero. 

$$ \begin{align*} 
    \nabla \cdot (\nabla \times \mathbf{B}) = 0 \quad \checkmark \text{continuity}
\end{align*} $$

How can we mathematically define a streamline? One way to do this is to consider a streamline as an intersection of two surfaces, which I'll call \\( \psi \\)  and \\( g \\) . For flows with symmetry, \\( g \\)  is often chosen as a set of coordinate planes. For example, \\( g=z \\)  in rectangular coordinates.  

<p align="center">
  <img src="/images/streamsurfaces.jpg" alt="Geometry of Streamline as an Intersection of Two Surfaces" width="40%" style="border:1px solid #000;">
</p>

<p align="center"><strong>Figure:</strong> Geometry of Streamline as an Intersection of Two Surfaces</p>

We know that the vector potential is in the form \\( \mathbf{B} = \psi \nabla g \\) . To prove this, let's compute the curl.

$$ \begin{align*} 
    \nabla \times \mathbf{B} &= \nabla \times (\psi \nabla g) \\
     &= \nabla \psi \times \nabla g + \cancel{\psi \nabla \times \nabla g} \\
     &= \nabla \psi \times \nabla g \\
     &= \mathbf{u}, \quad \text{(See figure above)}
\end{align*} $$

So we have a geometric connection between streamlines and the vector potential.

We can also connect this to the vorticity, 

$$ \begin{align*} 
    \boldsymbol{\omega} = \nabla \times \mathbf{u} = \nabla \times (\nabla \times \mathbf{B}) = -\nabla^2 \mathbf{B}
\end{align*} $$

<details class="custom-collapse" open>
<summary><strong>Vector Identity: Curl and Double Curl of One-Component Vector</strong></summary>
  <div class="collapse-content">

Suppose we know that the velocity has only one component and is a function of only two of the coordinates,

$$ \begin{equation*}
    \mathbf{A} = A_3(x_1,x_2) \mathbf{e}_3
\end{equation*} $$

Here, \( (x_1,x_2,x_3) \)  are the \textbf{generalized orthogonal coordinates}. 

Computing the curl yields the vorticity,

$$ \begin{equation} 
    \nabla \times \mathbf{A} = \dfrac{1}{h_2 h_3} \dfrac{\partial (h_3 A_3)}{\partial x_2} \mathbf{e}_1 - \dfrac{1}{h_1 h_3} \dfrac{\partial (h_3 A_3)}{\partial x_1} \mathbf{e}_2
    \label{curlofA}
\end{equation} $$

Let's curl this again,

$$ \begin{equation} 
    \nabla \times (\nabla \times \mathbf{A}) = -\dfrac{1}{h_1 h_2} \left\{ \dfrac{\partial}{\partial x_1} \left[ \dfrac{h_2}{h_1 h_3} \dfrac{\partial (h_3 A_3)}{\partial x_1}\right] +\dfrac{\partial}{\partial x_2} \left[ \dfrac{h_1}{h_2 h_3} \dfrac{\partial (h_3 A_3)}{\partial x_2} \right]\right\} \mathbf{e}_3
    \label{curlcurlofA}
\end{equation} $$

  </div>
</details>

### Velocity and Vorticity from Vector Potential

Suppose we choose \\( g=x_3 \\)  for the coordinate surface, then we have
\\( \nabla g = (1/h_3 )\mathbf{e}_3  \\) , and the vector potential is,

$$ \begin{equation*}
    \mathbf{B} = \psi \nabla g = \dfrac{\psi}{h_3} \mathbf{e}_3
\end{equation*} $$

By definition of the vector potential, we know that \\( \mathbf{u} = \nabla \times \mathbf{B} \\) . Since the vector potential has only one component, we can use Eq. \ref{curlofA} to simplify,  

$$ \begin{equation} 
    \boxed{\mathbf{u} = \nabla \times \mathbf{B} = \dfrac{1}{h_2 h_3} \dfrac{\partial \psi}{\partial x_2} \mathbf{e}_1 - \dfrac{1}{h_1 h_3} \dfrac{\partial \psi}{\partial x_1} \mathbf{e}_2}
    \label{velocityvectorpotential}
\end{equation} $$

Using Eq. \ref{curlcurlofA} to calculate vorticity, 

$$ \begin{equation} 
    \boldsymbol{\omega} = \nabla \times (\nabla \times \mathbf{B}) = -\dfrac{1}{h_1 h_2} \left\{ \dfrac{\partial}{\partial x_1} \left[ \dfrac{h_2}{h_1 h_3} \dfrac{\partial \psi}{\partial x_1} \right] + \dfrac{\partial}{\partial x_2} \left[ \dfrac{h_1}{h_2 h_3} \dfrac{\partial \psi}{\partial x_2} \right] \right\} \mathbf{e}_3
    \label{vorticitystreamfunction}
\end{equation} $$

If I define the following differential operator, 

$$ \begin{equation*}
    \boxed{E^2(\enspace) = \dfrac{h_3}{h_1 h_2} \left\{ \dfrac{\partial}{\partial x_1} \left[ \dfrac{h_2}{h_1 h_3} \dfrac{\partial ( \enspace )}{\partial x_1} \right] + \dfrac{\partial}{\partial x_2} \left[ \dfrac{h_1}{h_2 h_3} \dfrac{\partial ( \enspace)}{\partial x_2} \right] \right\}}
\end{equation*} $$

Eq. \ref{vorticitystreamfunction} reduces to,

$$ \begin{equation} 
    \boxed{\boldsymbol{\omega} = -\dfrac{E^2 (\psi)}{h_3} \mathbf{e}_3}
    \label{vorticityonecomponent}
\end{equation} $$

The divergence of the viscous stress tensor is important in the momentum equation. 

$$ \begin{align*} 
    \nabla \cdot \boldsymbol{\tau} = \mu \nabla^2 \mathbf{u} &= \mu \left[ \cancel{\nabla (\nabla \cdot \mathbf{u})} - \nabla \times (\nabla \times \mathbf{u})\right] \\
    &= -\mu \nabla \times \boldsymbol{\omega}
\end{align*} $$

To find the curl of the vorticity, we plug Eq. \ref{vorticityonecomponent} into Eq. \ref{curlofA} and obtain,

$$ \begin{equation*}
    \nabla \times \boldsymbol{\omega} = -\dfrac{1}{h_2 h_3} \dfrac{\partial}{\partial x_2} \left[  E^2 (\psi)\right] \mathbf{e}_1 + \dfrac{1}{h_1 h_3} \dfrac{\partial}{\partial x_1} \left[ E^2 (\psi)\right] \mathbf{e}_2
\end{equation*} $$

The divergence of the viscous stress tensor is thus, 

$$ \begin{equation*}
    \boxed{\nabla \cdot \boldsymbol{\tau} = \mu \left[ \dfrac{1}{h_2 h_3} \dfrac{\partial}{\partial x_2} \left[  E^2 (\psi)\right] \mathbf{e}_1 - \dfrac{1}{h_1 h_3} \dfrac{\partial}{\partial x_1} \left[ E^2 (\psi)\right] \mathbf{e}_2\right]}
\end{equation*} $$

To find the viscous term in the vorticity equation,

$$ \begin{equation*}
    \nabla^2 \boldsymbol{\omega} = - \nabla \times ( \nabla \times \boldsymbol{\omega})
\end{equation*} $$

To find the double curl of the vorticity, I plug Eq. \ref{vorticityonecomponent} into Eq. \ref{curlcurlofA}.

This results in, 

$$ \begin{equation*}
    \nabla \times (\nabla \times \boldsymbol{\omega}) = \dfrac{1}{h_1 h_2} \left\{ \dfrac{\partial }{\partial x_1} \left[ \dfrac{h_2}{h_1 h_3} \dfrac{\partial}{\partial x_1} \bigg( E^2(\psi) \bigg) \right] + \dfrac{\partial}{\partial x_2} \left[ \dfrac{h_1}{h_2 h_3} \dfrac{\partial}{\partial x_2}  \bigg( E^2 (\psi)\bigg)\right] \right\} \mathbf{e}_3 
\end{equation*} $$

Simplifying,

$$ \begin{equation*}
    \nabla \times (\nabla \times \boldsymbol{\omega})= E^2 \bigg( E^2 (\psi)\bigg) \dfrac{\mathbf{e}_3}{h_3}
\end{equation*} $$

So that the viscous term in the vorticity equation becomes,

$$ \begin{equation} 
    \boxed{\nabla^2 \boldsymbol{\omega} = - E^2 E^2 (\psi) \dfrac{\mathbf{e}_3}{h_3}}
    \label{E2E2}
\end{equation} $$

For spherical coordinates, where \\( h_1 = 1, \, h_2 = r, \, h_3 = r \sin \theta \\) , the \\( E^2 (\enspace) \\)  operator is, 

$$ \begin{equation*}
    E^2 (\enspace) = \dfrac{\partial^2}{\partial r^2} (\enspace ) + \dfrac{\sin \theta}{r^2} \dfrac{\partial}{\partial \theta} \left[ \dfrac{1}{\sin \theta} \dfrac{\partial (\enspace)}{\partial \theta}\right]
\end{equation*} $$

## Stokes Flow: Streamfunction and Vorticity

### Plane Stokes Flow: Low Re Flows

According to Eq. \ref{vorticitydef}, which is merely the definition of vorticity in terms of streamfunction (in 2D case),

$$ \begin{equation*}
    \omega_z = - \nabla^2 \psi
\end{equation*} $$

We know from Eq. \ref{laplacianvorticitystokesflow} that the laplacian of vorticity in Stokes flow is simply 0, 

$$ \begin{equation*}
    \nabla^2 \omega_z =0 
\end{equation*} $$

These two equations in tandem yield, 

$$ \begin{equation*}
    \boxed{\nabla^4 \psi = 0} 
\end{equation*} $$

### Axisymmetric Stokes Flow

For axisymmetric flows, we set Eq. \ref{E2E2} equal to 0. The following is obtained, 

$$ \begin{equation} 
    \boxed{E^2 E^2 (\psi) = 0}
    \label{E2E2axissymmetric}
\end{equation} $$

As an example, we will consider streaming motion over a sphere. 

### Stokes Flow: Streaming Motion Over Sphere

The velocity in terms of the streamfunction is, 

$$ \begin{equation*}
    \mathbf{u} = u_r \mathbf{e}_r + u_\theta \mathbf{e}_\theta + 0 \mathbf{e}_\phi =\dfrac{1}{r^2 \sin \theta} \dfrac{\partial \psi}{\partial \theta} \mathbf{e}_r - \dfrac{1}{r \sin \theta} \dfrac{\partial \psi}{\partial r} \mathbf{e}_\theta  + 0 \mathbf{e}_\phi
\end{equation*} $$

Here are the boundary conditions for this flowfield, 

At the surface of the sphere, where \\( r=R \\) , 

$$ \begin{equation*}
    u_r (R,\theta) = 0, \quad u_\theta (R,\theta) =0 
\end{equation*} $$

At infinity, the far stream, 

$$ \begin{equation*}
    \mathbf{u}(r \to \infty, \theta) = -U \mathbf{i}=-U \cos \theta \, \mathbf{e}_r + U \sin \theta \, \mathbf{e}_\theta
\end{equation*} $$

Our goal is to express these boundary conditions in terms of the streamfunction.

When \\( r=R \\) , at the surface of the sphere, 

$$ \begin{align*} 
    u_r(R,\theta) &= \dfrac{1}{R^2 \sin \theta} \dfrac{\partial \psi}{\partial \theta} \bigg|_{r=R} = 0 \\
    u_\theta(R,\theta) &= - \dfrac{1}{R \sin \theta} \dfrac{\partial \psi}{\partial r} \bigg|_{r=R} = 0 
\end{align*} $$

Therefore,

$$ \begin{equation*}
    \dfrac{\partial \psi}{\partial \theta} \bigg|_{r=R} = 0, \quad \boxed{\dfrac{\partial \psi}{\partial r} \bigg|_{r=R} = 0}
\end{equation*} $$

Leaving,

$$ \begin{equation*}
    \boxed{\psi (R,\theta) = C = 0}
\end{equation*} $$

We set the constant equal to \\( 0 \\)  for simplicity. 

For the condition at infinity, 

$$\left\{ \begin{aligned}
    \dfrac{1}{r^2 \sin \theta} \dfrac{\partial \psi}{\partial \theta} &= -U \cos \theta = u_r\\
    - \dfrac{1}{r \sin \theta} \dfrac{\partial \psi}{\partial r} &= U \sin \theta = u_\theta
\end{aligned} \right\} \enspace \longrightarrow \enspace 
\left\{ \begin{aligned}
    \dfrac{\partial \psi}{\partial \theta} &= -U r^2 \sin \theta \cos \theta \\
    \dfrac{\partial \psi}{\partial r} &= -U r \sin^2 \theta
\end{aligned} \right\} \enspace \longrightarrow \enspace \psi =- \dfrac{Ur^2 \sin^2 \theta}{2}
$$

$$ \begin{equation*}
    \boxed{\text{As } r \to \infty, \quad\psi \sim - \dfrac{r^2}{2} U \sin^2 \theta}
\end{equation*} $$

If we assume that \\( \psi \\)  is of the form,

$$ \begin{equation*}
    \psi = \bigg[R^2 U \sin^2 \theta \bigg] F\left(\dfrac{r}{R} \right) 
\end{equation*} $$

then 

$$ \begin{equation} 
    E^2 (\psi) = U \sin^2 \theta \bigg[ F''\left(\dfrac{r}{R} \right) - \dfrac{2}{(r/R)^2} F \left(\dfrac{r}{R} \right)\bigg]
    \label{E2sphere}
\end{equation} $$

and

$$ \begin{equation*}
    \boxed{E^2E^2 (\psi) = F^{(4)}\left(\dfrac{r}{R} \right) - \dfrac{4}{(r/R)^2} F''\left(\dfrac{r}{R} \right) + \dfrac{8}{(r/R)^3} F'\left(\dfrac{r}{R} \right) - \dfrac{8}{(r/R)^4} F\left(\dfrac{r}{R} \right) = 0 }
\end{equation*} $$

Plug in \\( F=C_n \left( r/R\right)^n \\)  and obtain,

$$ \begin{equation*}
    F \left( \dfrac{r}{R} \right) = C_{-1} \left( \dfrac{r}{R} \right)^{-1} +C_1 \left( \dfrac{r}{R} \right) + C_2 \left( \dfrac{r}{R} \right)^2 + C_4 \left( \dfrac{r}{R} \right)^4
\end{equation*} $$

The boundary conditions in \\( F \\)  are,

$$\boxed{
\begin{aligned}
    F(1) &= 0 \\
    F'(1)&= 0 \\
    F(\infty) & \sim - \dfrac{1}{2} \left( \dfrac{r}{R} \right)^2
\end{aligned}}$$

With these boundary conditions, we get 

$$ \begin{align*} 
    C_{-1} &= -\dfrac{1}{4} \\
    C_{1}  &= \dfrac{3}{4} \\
    C_{2}  &= -\dfrac{1}{2} \\
    C_{4}  &= 0
\end{align*} $$

$$ \begin{equation*}
    \boxed{F \left( \dfrac{r}{R} \right) = -\dfrac{1}{4} \left( \dfrac{r}{R}\right)^{-1} + \dfrac{3}{4} \left( \dfrac{r}{R} \right) - \dfrac{1}{2} \left( \dfrac{r}{R}\right)^2}
\end{equation*} $$

$$ \begin{equation*}
    \boxed{\psi = R^2U \sin^2 \theta \, \left[ -\dfrac{1}{4} \left( \dfrac{r}{R}\right)^{-1} + \dfrac{3}{4} \left( \dfrac{r}{R} \right) - \dfrac{1}{2} \left( \dfrac{r}{R}\right)^2\right]}
\end{equation*} $$

$$ \begin{align*} 
    \dfrac{u_r}{U} &= \left[ - \dfrac{1}{2} \left( \dfrac{r}{R}\right)^{-3} + \dfrac{3}{2} \left( \dfrac{r}{R}\right)^{-1} - 1\right] \cos \theta \\
    \dfrac{u_\theta}{U} &= \left[ -\dfrac{1}{4} \left( \dfrac{r}{R}\right)^{-3} - \dfrac{3}{4} \left( \dfrac{r}{R}\right)^{-1} + 1 \right] \sin \theta
\end{align*} $$

$$ \begin{align*} 
    \boldsymbol{\omega} &= - \dfrac{E^2 (\psi)}{r \sin \theta} \mathbf{e}_\phi \\
    \dfrac{\omega_\phi}{U/R} &= \dfrac{3}{2} \left( \dfrac{r}{R} \right)^{-2} \sin \theta
\end{align*} $$

In low-Re flows, the pressure exactly balances the viscous forces, 

$$ \begin{equation*}
    \nabla p = \mu \nabla^2 \mathbf{u} = -\mu \nabla \times \boldsymbol{\omega}
\end{equation*} $$

In this case, the curl of vorticity is, 

$$ \begin{equation*}
    \nabla \times \boldsymbol{\omega} = - \dfrac{1}{r^2 \sin \theta} \dfrac{\partial [E^2 (\psi)]}{\partial \theta} \mathbf{e}_r + \dfrac{1}{r \sin \theta} \dfrac{\partial [E^2 (\psi)]}{\partial r} \mathbf{e}_\theta
\end{equation*} $$

If I plug Eq. \ref{E2sphere} into this and simplify, I eventually get, 

$$ \begin{equation*}
    \nabla \times \boldsymbol{\omega} = \left[ \dfrac{3U}{R^2} \left( \dfrac{r}{R} \right)^{-3} \cos \theta \right] \, \mathbf{e}_r + \left[ \dfrac{3U}{2R^2} \left( \dfrac{r}{R}\right)^{-3} \sin \theta \right] \, \mathbf{e}_\theta
\end{equation*} $$

$$ \begin{align*} 
    (\nabla p)_r &= -\mu (\nabla \times \boldsymbol{\omega})_r =  - \dfrac{3U \mu}{R^2} \left( \dfrac{r}{R} \right)^{-3} \cos \theta = \dfrac{\partial p}{\partial r} \\
    (\nabla p)_\theta &= - \mu (\nabla \times \boldsymbol{\omega})_\theta =  -\dfrac{3U \mu}{2R^2} \left( \dfrac{r}{R}\right)^{-3} \sin \theta = \dfrac{1}{r} \dfrac{\partial p}{\partial \theta}
\end{align*} $$

$$ \begin{equation*}
    \int\limits_{p_\infty}^{p} dp = \int\limits_{\infty, \theta=0}^{r} \dfrac{\partial p}{\partial r} \, dr + \int\limits_{0,r}^{\theta} \dfrac{\partial p}{\partial \theta} \, d \theta 
\end{equation*} $$

$$ \begin{equation*}
    \boxed{p-p_\infty = \dfrac{3 \mu U}{2R} \left( \dfrac{r}{R}\right)^{-2} \cos \theta}
\end{equation*} $$

$$ \begin{align*} 
    \tau_{rr}= 2\mu \dfrac{\partial u_r}{\partial r}=3 \dfrac{\mu U}{R} \left[ \left( \dfrac{r}{R}\right)^{-4} - \left( \dfrac{r}{R}\right)^{-2}\right] \cos \theta
\end{align*} $$

## Velocity Potential

Suppose that we have a flow that is irrotational, meaning that the vorticity is zero. This means,

$$ \begin{equation*}
    \nabla \times \mathbf{u} = \mathbf{0} 
\end{equation*} $$

If this is true, then it must be that \\( \mathbf{u} \\)  is the gradient of some vector field by definition, since the curl of a gradient is 0. 

Thus,

$$ \begin{equation*}
    \mathbf{u} = \nabla \phi
\end{equation*} $$

## Bernoulli Equation

Consider the incompressible momentum equation,

$$ \begin{equation*}
    \dfrac{\partial \mathbf{u}}{\partial t } + \mathbf{u \cdot \nabla \mathbf{u}} = - \nabla \left( \dfrac{p}{\rho}\right) + \nu \nabla^2 \mathbf{u}
\end{equation*} $$

Using the following two vector identities, we can rewrite the momentum equation,

$$ \begin{align*} 
    \mathbf{u} \cdot \nabla \mathbf{u} = \dfrac{1}{2}\nabla (\mathbf{u} \cdot \mathbf{u}) - \mathbf{u}\times \boldsymbol{\omega} \\
    \nabla^2 \mathbf{u} = \nabla (\nabla \cdot \mathbf{u}) - \nabla \times \boldsymbol{\omega}
\end{align*} $$

So that the momentum equation transforms to,

$$ \begin{equation} 
    \dfrac{\partial \mathbf{u}}{\partial t} + \nabla \left( \dfrac{p}{\rho} + \dfrac{1}{2}\mathbf{u} \cdot \mathbf{u}\right) = \mathbf{u} \times \boldsymbol{\omega} - \nu \nabla \times \boldsymbol{\omega}
    \label{momintermsofvort}
\end{equation} $$

As mentioned above, for irrotational flows where the vorticity is 0, the velocity is the gradient of a scalar function, so Eq. \ref{momintermsofvort} transforms into,

$$ \begin{equation*}
    \nabla \left( \dfrac{\partial \phi}{\partial t} +\dfrac{p}{\rho}+ \dfrac{1}{2} \mathbf{u} \cdot \mathbf{u} \right) = 0
\end{equation*} $$

Let's say we have a steady flow and we define \\( H= p/\rho + (1/2) \mathbf{u}\cdot \mathbf{u} \\) , then Eq. \ref{momintermsofvort} is,

$$ \begin{equation} 
    \nabla H = \mathbf{u} \times \boldsymbol{\omega} - \nu \nabla \times \boldsymbol{\omega}
    \label{steaddybernoulli}
\end{equation} $$

We dot both sides of Eq. \ref{steaddybernoulli} with the unit tangent vector to the streamlines, 

$$ \begin{equation*}
    \mathbf{t} \cdot \nabla H =  \mathbf{t} \cdot (\mathbf{u} \times \boldsymbol{\omega}) - \nu  \mathbf{t} \cdot (\nabla \times \boldsymbol{\omega})
\end{equation*} $$

According to vector calculus, we know that the gradient of a function dotted with a unit vector is simply the directional derivative of the function. Therefore, \\( \mathbf{t} \cdot \nabla H = dH/ds \\) , where \\( s \\)  is in the streamline direction. Also, it is fairly obvious that \\( \mathbf{t} \cdot (\mathbf{u} \times \boldsymbol{\omega}) = 0 \\)  and \\( \nabla \times \boldsymbol{\omega}= - \nabla^2 \mathbf{u} \\) . With these facts in mind, 

$$ \begin{equation*}
    \boxed{\dfrac{dH}{ds} = \nu (\mathbf{t \cdot \nabla^2 \mathbf{u}} )}
\end{equation*} $$

If we now dot Eq. \ref{steaddybernoulli} by the unit normal vector and recall that \\( \mathbf{u} = V \mathbf{t} + 0 \mathbf{n} + 0 \mathbf{b} \\)  and \\( \boldsymbol{\omega}=\left[V (\mathbf{t} \cdot \nabla \times \mathbf{t}) \right] \mathbf{t} + [\partial V/\partial b] \mathbf{n} + [V/R - \partial V /\partial n] \mathbf{b} \\) , then, 

$$ \begin{align*} 
    \dfrac{dH}{dn}= \mathbf{n} \cdot \nabla H &= \mathbf{n} \cdot ( \mathbf{u} \times \boldsymbol{\omega}) - \nu \mathbf{n} \cdot (\nabla \times \boldsymbol{\omega})\\
    &= -\dfrac{V^2}{R} + \dfrac{d}{d n} \left( \dfrac{V^2}{2}\right) + \nu \mathbf{n} \cdot \nabla^2 \mathbf{u}
\end{align*} $$

$$ \begin{equation*}
    \boxed{\dfrac{d}{d n } \left( \dfrac{p}{\rho}\right) = - \dfrac{V^2}{R} + \nu \mathbf{n} \cdot \nabla^2 \mathbf{u}}
\end{equation*} $$

I will perform the same process and dot Eq. \ref{steaddybernoulli} by the unit binormal vector \\( \mathbf{b} \\) .

$$ \begin{equation*}
    \boxed{\dfrac{d}{db} \left( \dfrac{p}{\rho}\right) = \nu \mathbf{b} \cdot  \nabla^2 \mathbf{u}}
\end{equation*} $$

## Vorticity Equation

The vorticity equation is derived by taking the curl of Eq. \ref{momintermsofvort}. Note: the curl of a gradient is 0. 

By applying the two following identities, 

$$ \begin{align*} 
    \nabla \times (\nabla \times \boldsymbol{\omega} ) &= \cancel{\nabla (\nabla \cdot \boldsymbol{\omega})} - \nabla^2 \boldsymbol{\omega} \\
    \nabla \times \mathbf{u} \times \boldsymbol{\omega}&= \cancel{\mathbf{u} (\nabla \cdot \boldsymbol{\omega})} - \cancel{\boldsymbol{\omega} (\nabla \cdot \mathbf{u})} + (\boldsymbol{\omega} \cdot \nabla) \mathbf{u} - (\mathbf{u} \cdot \nabla ) \boldsymbol{\omega}
\end{align*} $$

We obtain, 

$$ \begin{equation*}
    \boxed{\dfrac{D \boldsymbol{\omega}}{Dt} = \boldsymbol{\omega} \cdot \nabla \mathbf{u} + \nu \nabla^2 \boldsymbol{\omega}}
\end{equation*} $$



