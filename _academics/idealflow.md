---
title: "Ideal Flow"
excerpt: "I use complex analysis principles to investigate potential flow, starting with elementary solutions, such as sources/sinks, doublets, and moving on to superposition of solutions. Then, I talk about the use of conformal transformations to analyze flow over airfoil shapes. "
author_profile: false
layout: splash
image: /images/jouairfoilmain.png
caption: "Photo credit: rreusser.github.io" 
header:
  overlay_color: "#2a4d8f"           
  hero_title: "Ideal Flow"
  hero_excerpt: "I use complex analysis principles to investigate potential flow, starting with elementary solutions, such as sources/sinks, doublets, and moving on to superposition of solutions. Then, I talk about the use of conformal transformations to analyze flow over airfoil shapes."
---

<style>
h2 {
  font-size: 1.6em;   /* bigger than default 1.25em */
  margin: 1.6em 0 0.4em; /* scale margins ~proportional */
  line-height: 1.25;
}
h3 {
  font-size: 1.3em;   /* bigger than default 1.0em */
  margin: 1.3em 0 0.35em;
  line-height: 1.3;
}
h4 {
  font-size: 1em;     /* bigger than default 0.75em */
  margin: 1em 0 0.3em;
  line-height: 1.35;
}
</style>

<a href="/academics/" class="button-gradient" style="display: inline-block; margin-top: 20px;">
  ← Back to Academic Works Page
</a>

<div class="sidebar-toc">
  <h3>On This Page</h3>
  <ul>
    <li><a href="#complex-differentiation-and-cauchy-riemann-equations">Complex Differentiation and Cauchy-Riemann Equations</a>
      <ul>
        <li><a href="#another-way-of-deriving-the-cauchy-riemann-conditions">Another way of deriving the Cauchy-Riemann Conditions</a></li>
        <li><a href="#conversion-to-polar-coordinates">Conversion to Polar Coordinates</a></li>
      </ul>
    </li>
    <li><a href="#potential-flow-solutions">Potential Flow Solutions</a></li>
    <li><a href="#superposition-of-potential-flow">Superposition of Potential Flow</a>
      <ul>
        <li><a href="#half-body">Half-Body</a></li>
        <li><a href="#doublet">Doublet</a></li>
        <li><a href="#cylinder-in-a-stream">Cylinder in a Stream</a></li>
        <li><a href="#cylinder-in-a-stream-with-circulation">Cylinder in a Stream with Circulation</a></li>
      </ul>
    </li>
    <li><a href="#aerodynamics">Aerodynamics</a>
      <ul>
        <li><a href="#kutta-joukowski-law">Kutta-Joukowski Law</a></li>
        <li><a href="#conformal-mapping">Conformal Mapping</a>
          <ul>
            <li><a href="#joukowski-airfoil">Joukowski Airfoil</a>
              <ul>
                <li><a href="#complex-potential-of-joukowski-airfoil-in-uniform-stream">Complex Potential of Joukowski Airfoil in Uniform Stream</a></li>
              </ul>
            </li>
          </ul>
        </li>
      </ul>
    </li>
    <li><a href="#references">References</a></li>
  </ul>
</div>

## Complex Differentiation and Cauchy-Riemann Equations

A complex function \\( F(z) \\) is said to be analytic in a domain \\(D\\) if \\( F(z) \\) is defined and differentiable at all points of \\(D\\). 

$$z=x+iy = r e^{i\theta} \notag $$

$$\begin{equation*}
    F(z) = \phi(x,y) + i\psi(x,y) 
\end{equation*}$$

What does it mean to take the derivative of this function? 

$$\begin{align}
    \dfrac{dF}{dz} &= \lim_{\Delta z \to 0} \dfrac{F(z+\Delta z) - F(z)}{\Delta z} \notag \\
    &=  \lim_{\Delta z \to 0} \dfrac{\bigg[\phi(x+\Delta x, y+\Delta y) + i \psi (x+ \Delta x, y+\Delta y) \bigg] - \bigg[ \phi(x,y) + i \psi (x,y)\bigg]}{\Delta x + i \Delta y} \label{dFdz}
\end{align}$$

Regardless of what direction we approach \\( z \\) from, the complex derivative should be the same. 

Let's approach the point \\( z \\) from the horizontal direction \\( (\Delta y=0) \\) only. The limit, Eq. \ref{dFdz}, reduces to, 

$$\begin{align*}
    \dfrac{dF}{dz} &= \lim_{\Delta z \to 0} \dfrac{\bigg[\phi(x+\Delta x, y) + i \psi (x+ \Delta x, y) \bigg] - \bigg[ \phi(x,y) + i \psi (x,y)\bigg]}{\Delta x} \\
    &= \lim_{\Delta x \to 0 }\dfrac{\phi(x + \Delta x,y)-\phi(x,y)}{\Delta x} + i\left[ \lim_{\Delta x \to 0 } \dfrac{\psi(x+\Delta x,y)-\psi(x,y)}{\Delta x} \right] 
\end{align*}
$$

$$\begin{equation}
    \boxed{\dfrac{dF}{dz}=  \dfrac{\partial \phi}{\partial x} + i \dfrac{\partial \psi}{\partial x}}
    \label{dFdz1}
\end{equation}$$

We can also approach point z from the vertical direction (\\( \Delta x =0 \\)) only. Then we have, 

 $$ \begin{align*}
        \dfrac{dF}{dz} &= \lim_{\Delta y \to 0} \dfrac{\phi(x,y+ \Delta y) - \phi(x,y) + i \bigg[ \psi(x,y + \Delta y) - \psi(x,y) \bigg]}{i \Delta y 
        } \\
        &= \dfrac{\partial \phi}{\partial y} \dfrac{1}{i} + \dfrac{\partial \psi}{\partial y} 
    \end{align*}$$

$$    \begin{equation}
        \boxed{\dfrac{dF}{dz} = \dfrac{\partial \psi}{\partial y } - i \dfrac{\partial \phi}{\partial y } } 
        \label{dFdz2}
    \end{equation}$$

Setting Eqs. \ref{dFdz1}-\ref{dFdz2} equal to each other, we obtain the **Cauchy-Riemann Conditions**.

$$\begin{equation*}
    \boxed{\dfrac{\partial \phi}{\partial x} = \dfrac{\partial \psi}{\partial y}, \quad \dfrac{\partial \psi}{\partial x} = - \dfrac{\partial \phi}{\partial y}} 
\end{equation*}$$


<details class="custom-collapse">
    <summary id="another-way-of-deriving-the-cauchy-riemann-conditions"><strong>Another way of deriving the Cauchy-Riemann Conditions</strong></summary>
  <div class="collapse-content">
    
<p align="center">
  <img src="/images/conformalmap.jpg" alt="Incremental length dz vector transformed to df vector by the function f." width="60%" style="border:1px solid #000;">
</p>

<p align="center"><strong>Figure 1:</strong> Incremental length \(dz\) vector transformed to \(df\) vector by the function \(f\).</p>


$$F(z) =\phi + i\psi \notag $$

We can imagine a vector \(dz\) in the complex plane representing a small step in the real and imaginary directions. Now, the function F transforms this vector to a new vector \(dF\). 

For an insightful interpretation, we regard a function as a warping of gridlines in the Cartesian plane, with the Jacobian describing the stretching and pulling of space. For a zoomed in region, the function seems linear, which can be described in linear algebra as a matrix vector product. 

$$\begin{align}
    dF &= J dz \notag \\ 
    \begin{bmatrix}
        dF_x \\dF_y
    \end{bmatrix} &= \begin{bmatrix}
        d\phi \\ d\psi
    \end{bmatrix} = \begin{bmatrix}
        \dfrac{\partial \phi}{\partial x} & \dfrac{\partial \phi}{\partial y} \\
        \dfrac{\partial \psi}{\partial x} & \dfrac{\partial \psi}{\partial y}
    \end{bmatrix}
    \begin{bmatrix}
        dx \\dy    
    \end{bmatrix} \label{cauchyriemannjacobian}
\end{align} $$

First, let us put together what matrix multiplication means in matrix form. 

Suppose we have an arbitrary complex number \(r=a+ib\). If we multiply by another complex number \(s=c+id\), it means that we rotate and stretch \(r\) in a certain way to yield \(s\). We view this as an operator (or function) acting on \(r=a+ib\). 

$$\begin{align*}
    \mathcal{F}(r) &= (c+id) r \\
    &= (c+id)(a+ib) \\
    &= ac-bd + i(ad+bc)
\end{align*}$$

In linear algebra terms,

$$\begin{align}
    \mathcal{F} \left(\begin{bmatrix}
        a\\b
    \end{bmatrix} \right) = \underbrace{\begin{bmatrix}
        c & -d \\ d & c
    \end{bmatrix}}_{M} \begin{bmatrix}
        a\\b
    \end{bmatrix} = \begin{bmatrix}
        ac-bd \\ ad + bc
    \end{bmatrix}
    \label{complexmultiplication}
\end{align}$$


$$\text{Therefore, multiplying a+ib by c+id corresponds to left-multiplying }  \begin{bmatrix}
    a \\ b
\end{bmatrix} \text{by the matrix } \begin{bmatrix}
    c & -d \\ d & c
\end{bmatrix}. $$

In Eq. \ref{cauchyriemannjacobian}, for \(F\) to be an analytic function, \(J\) must be a complex number, so the matrix representation of \(J\) must be the same form as \(M\) in Eq. \ref{complexmultiplication}. The main diagonal terms should be equal, and the other diagonal should have opposite signs. This results in the <strong>Cauchy-Riemann Conditions</strong> for a complex function to be complex differentiable or analytic. 

$$\begin{equation*}
    \boxed{\dfrac{\partial \phi}{\partial x} = \dfrac{\partial \psi}{\partial y}, \quad \dfrac{\partial \psi}{\partial x} = - \dfrac{\partial \phi}{\partial y}} 
\end{equation*}$$

  </div>
</details>

By the equality of mixed partial derivatives in the Cauchy-Riemann conditions, we see that both \\(\phi\\) and \\(\psi\\) satisfy Laplace's equation. Importantly, this means that we can start with any complex analytical function and be assured that it automatically satisfies Laplace's equation. 

In fluid dynamics, we use \\(\phi\\) and \\(\psi\\) to represent the velocity potential and streamfunction respectively. The complex function \\(F(z)\\), which combines the velocity potential as the real part and the streamfunction as the imaginary part, is called the **complex potential**. The derivative, \\(dF/dz\\), is known as the **complex velocity** and is denoted with \\(W\\). 

$$\begin{align*}
    \dfrac{dF}{dz} = \dfrac{\partial \phi}{\partial x} + i \dfrac{\partial \psi}{\partial x} 
\end{align*}$$

$$\begin{equation}
    \boxed{W=\dfrac{dF}{dz} = u - iv}
    \label{complexvelocityW}
\end{equation}$$

<details class="custom-collapse">
  <summary id="conversion-to-polar-coordinates"><strong>Conversion to Polar Coordinates</strong></summary>
  <div class="collapse-content">
    
$$    \begin{align*}
        \mathbf{e}_r &= \cos \theta \mathbf{i} + \sin \theta \mathbf{j} \\
        \mathbf{e}_\theta &= - \sin \theta \mathbf{i} + \cos \theta \mathbf{j}
    \end{align*}$$

In matrix form, 

$$    \begin{align}
        \begin{bmatrix}
            \mathbf{e}_r & \mathbf{e}_\theta
        \end{bmatrix} &= \begin{bmatrix}
            \mathbf{i} & \mathbf{j}
        \end{bmatrix} \underbrace{\begin{bmatrix}
            \cos \theta & - \sin \theta \\
            \sin \theta & \cos \theta
        \end{bmatrix}}_M \label{Mmatrix}\\
        \begin{bmatrix}
            \mathbf{i} & \mathbf{j}
        \end{bmatrix} &= \begin{bmatrix}
            \mathbf{e}_r & \mathbf{e}_\theta    
        \end{bmatrix} \underbrace{\begin{bmatrix}
            \cos \theta & \sin \theta \\
            -\sin \theta & \cos \theta
        \end{bmatrix}}_{M^T} \label{MTmatrix}
    \end{align}$$

$$    \begin{equation}
        \mathbf{V}= \begin{bmatrix}
            \mathbf{i} & \mathbf{j}
            \end{bmatrix} \begin{bmatrix}
                 u \\ v
            \end{bmatrix} = \begin{bmatrix}
                \mathbf{e}_r & \mathbf{e}_\theta 
            \end{bmatrix} \begin{bmatrix}
                u_r \\ u_\theta
            \end{bmatrix} \label{velocityvector}
    \end{equation}$$

We plug in Eq. \ref{Mmatrix} into the right-hand side of Eq. \ref{velocityvector}. 

$$\begin{equation}
    \begin{bmatrix}
        u \\ v
    \end{bmatrix} =  \begin{bmatrix}
        \cos \theta & -\sin \theta \\
        \sin \theta & \cos \theta
    \end{bmatrix}
    \begin{bmatrix}
        u_r \\ u_\theta
    \end{bmatrix} \label{uvmatrix}
\end{equation}
$$

Now, with the formulas for \((u,v)\) in terms of \((u_r,u_\theta)\), namely Eq. \ref{uvmatrix}, we can write the complex velocity as,

$$\begin{align*}
    W &= u-iv \\
    &= (u_r \cos \theta - u_\theta \sin \theta) - i (u_r \sin \theta + u_\theta \cos \theta  ) \\
    &= u_r (\cos \theta - i \sin \theta) - u_\theta (\sin \theta + i \cos \theta)\\
    &= u_r (\cos \theta - i \sin \theta) - u_\theta i (\cos \theta - i \sin \theta) \\
    &= (u_r - i u_\theta) (\cos \theta - i\sin\theta)
\end{align*}$$

$$\boxed{W = (u_r -i u_\theta)e^{-i \theta}} \notag $$

  </div>
</details>

## Potential Flow Solutions

Uniform Flow
$$F(z) = U e^{-i\alpha} z \notag $$

Line Source 
$$F(z)=\dfrac{m}{2 \pi} \ln z \notag $$

Line Vortex
$$F(z) = -i \dfrac{\Gamma}{2 \pi} \ln z \notag $$

## Superposition of Potential Flow
Because of the linearity of Laplace's equation, known solutions can be added together to produce new solutions. 

### Half-Body

The half-body is formed by superimposing a source and a uniform flow. 

$$\begin{align}
    F = Uz + \dfrac{m}{2 \pi}\ln z + iC \label{halfbodywithconstanteqn}\\
    W = \dfrac{dF}{dz} = U + \dfrac{m}{2\pi z} \notag
\end{align}$$

The arbitrary constant \\(C\\) is used to set \\(\psi=0\\) on the boundary streamline. Let's first find the location of the stagnation point, 

$$\begin{align*}
   W &= U + \dfrac{m}{2 \pi (x+iy)} \\
     &= U + \dfrac{m}{2 \pi} \dfrac{x-iy}{x^2+y^2} \\
     &= U + \dfrac{m}{2\pi} \dfrac{x}{x^2+y^2} -i \dfrac{m}{2 \pi} \dfrac{y}{x^2+y^2}
\end{align*}$$

Setting the real and imaginary parts equal to zero, we get,

$$ x_{\text{stag}} = -\dfrac{m}{2 \pi U}, \quad y_{stag}=0 \notag $$

The streamfunction should be equal to \\(0\\) for the streamline through the point \\((x_{stag},y_{stag})\\). What is the form of the streamfunction? Let's separate Eq. \ref{halfbodywithconstanteqn} into real and imaginary parts; the imaginary part is the streamfunction. Plug in \\(z= r e^{i\theta}\\),

$$\begin{align*}
    F(r e^{i \theta} ) &= Ur e^{i\theta} + \dfrac{m}{2 \pi} \ln ( r e^{i \theta} ) + iC \\
    &=  Ur e^{i \theta} + \dfrac{m}{2\pi} \bigg[ \ln r + i \theta \bigg] + iC \\
    &= U \bigg( x+iy \bigg) + \dfrac{m}{2\pi}\ln r + i \dfrac{m \theta}{2 \pi} + iC \\
    &= Ux + \dfrac{m}{2 \pi} \ln r + i \left[ Uy + \dfrac{m \theta}{2 \pi} + C\right]
\end{align*}$$

The streamfunction is, 

$$\psi = Uy + \dfrac{m \theta}{2 \pi} + C \notag $$

As stated before, at the point \\((x_{stag},y_{stag})\\), we know that \\(\psi=0\\), so that we may solve for the constant \\(C\\). 

$$\begin{align*}
    \psi \bigg(y_{stag}=0, \theta_{stag}=\pi \bigg) = \dfrac{m}{2} + C &= 0 \\
    C &= -\dfrac{m}{2}
\end{align*}$$

Plugging this constant into the streamfunction, 

$$\boxed{\psi=Uy - \dfrac{m}{2\pi} (\pi - \theta)} \notag $$

Defining the angle \\(\gamma\\) as measured clockwise from the negative x-axis, \\(\gamma = \pi - \theta\\), (see Fig. 2) 

<p align="center">
  <img src="/images/halfbodygamma.jpg" alt="Half-body gamma figure" width="40%" style="border:1px solid #000;">
</p>

<p align="center"><strong>Figure 2:</strong></p>


$$\boxed{\psi = Uy - \dfrac{m}{2 \pi} \gamma} \notag $$

The equation for the boundary streamline is found by setting \\(\psi = 0 \\),
$$\boxed{y_{b}= \dfrac{m}{2 \pi U} \gamma}  \notag $$

Substituting \\(y_b = R \sin \gamma\\) yields this equation in parametric polar form,

$$\begin{equation}
    \boxed{R = \dfrac{m}{2\pi U} \dfrac{\gamma}{\sin \gamma}} \label{polarparametrichalfbody}
\end{equation}$$

In order to find the velocity squared, we multiply the complex velocity by its conjugate. 

$$\begin{align}
    q^2 = W \overline{W} &= \left(U + \dfrac{m}{2 \pi z} \right) \left( U + \dfrac{m}{2 \pi \overline{z}} \right) \notag \\
    &= U^2 + \dfrac{Um}{2 \pi} \left( \dfrac{z + \overline{z}}{z \overline{z}} \right) + \dfrac{m^2}{4 \pi^2 z \overline{z}} \label{qsquaredform}
\end{align}
$$

By definition, \\(z= -r \cos \gamma + i r \sin \gamma\\) and \\(\overline{z}= -r \cos \gamma - i r \sin \gamma\\), so \\(z \overline{z}= r^2\\). Eq. \ref{qsquaredform} becomes, 

$$q^2 = U^2 - \dfrac{Um}{\pi r} \cos \gamma + \dfrac{m^2}{4 \pi^2 r^2} \notag $$

Let's evaluate this at the boundary of the half-body, \\(r=R\\) and use Eq. \ref{polarparametrichalfbody} to substitute for \\(R\\), yielding, 

$$q_b^2 = U^2 \left(1-\dfrac{2}{\gamma} \sin \gamma \cos \gamma + \dfrac{ \sin^2 \gamma}{\gamma^2} \right) \notag $$

By definition of pressure coefficient, 

$$C_p = 1 - \left( \dfrac{q_b}{U} \right) ^2 \notag $$

Substituting the equation for \\(q_b\\),

$$\begin{equation}
    \boxed{C_p = \dfrac{2}{\gamma} \sin \gamma \cos \gamma - \dfrac{\sin^2 \gamma}{\gamma^2}}
    \label{cphalfbodyeqn}
\end{equation}$$

It is better to write \\(C_p\\) in terms of the streamline coordinate system. Look at the triangle in Fig. 3.

<p align="center">
  <img src="/images/halfbodyarclength.jpg" alt="Half-body arclength figure" width="40%" style="border:1px solid #000;">
</p>

<p align="center"><strong>Figure 3:</strong></p>

Using Law of Cosines and Taylor series expansion \\(\cos (d \gamma) = 1 - (d \gamma)^2/2 + \text{H.O.T}\\),

$$\begin{align}
    (ds)^2 &= (R + dR)^2 + R^2 - 2 (R + dR)(R) \cos (d \gamma) \notag\\
    &= (R + dR)^2 + R^2 - 2 (R + dR)(R) \left( 1 - \dfrac{(d \gamma)^2}{2} \right) \notag\\
    &= (dR)^2 + (R d \gamma)^2 \label{ds=dRdgamma}
\end{align}$$

We differentiate Eq. \ref{polarparametrichalfbody} and plug into Eq. \ref{ds=dRdgamma} to obtain \\(ds\\) as a function of \\(\gamma\\). We also introduce a new variable, the half body width, \\(h=m/(2U)\\).

$$\begin{equation}
    ds = \dfrac{h}{\pi} \dfrac{d \gamma}{\sin^2 \gamma} \left[\gamma^2 + \sin^2 \gamma - 2 \gamma \cos \gamma \sin \gamma \right]^{1/2} \label{sasfunofgamma}
\end{equation}$$

If I integrate Eq. \ref{sasfunofgamma} with initial condition \\(s(0) =0\\), I obtain \\(s(\gamma)\\), which I can plot with \\(C_p(\gamma)\\) from Eq. \ref{cphalfbodyeqn}.

<p align="center">
  <img src="/images/cpgraphhalfbody.png" alt="Pressure Distribution on a Half Body" width="50%" style="border:1px solid #000;">
</p>

<p align="center"><strong>Figure 4:</strong> Pressure Distribution on a Half Body</p>


### Doublet

We can create what is known as a doublet by placing a source next to a sink. Then, we bring the source and sink closer together while increasing the strength of the source/sink. 

$$\begin{align*}
    F(z) &= \dfrac{m}{2 \pi} \ln (z + \varepsilon) - \dfrac{m}{2 \pi} \ln (z - \varepsilon) \\[3mm] 
    &= \dfrac{m}{2 \pi} \ln \left( \dfrac{z + \varepsilon}{z - \varepsilon}\right) \\[3mm]
    &= \dfrac{m}{2 \pi} \ln \left(\dfrac{1+\dfrac{\varepsilon}{z}}{1-\dfrac{\varepsilon}{z}} \right) \\[3mm]
    &= \dfrac{m}{2 \pi} \ln \left[ \left( 1 + \dfrac{\varepsilon}{z} \right) \left(1-\dfrac{\varepsilon}{z} \right)^{-1} \right]
\end{align*}$$

Recall the Taylor series expansion, 

$$\left(1-\dfrac{\varepsilon}{z} \right)^{-1} = 1 + \left( \dfrac{\varepsilon}{z} \right)+ \left( \dfrac{\varepsilon}{z} \right)^2+... \notag $$

Plug into the \\(F(z)\\) equation, 

$$F(z) = \dfrac{m}{2 \pi} \ln \left\{ 1 + 2 \dfrac{\varepsilon}{z} + O \left[\left( \dfrac{\varepsilon}{z} \right)^2 \right] \right\} \notag $$

Recall the following expansion, 

$$\ln (x) = (x-1) - \dfrac{1}{2} (x-1)^2+... \notag $$

So that the \\(F(z)\\) equation becomes,

$$F = \dfrac{m\varepsilon}{\pi z} + O \left(\dfrac{\varepsilon}{z} \right)^2 \notag $$

As the distance \\(\varepsilon \to 0\\), the source strength \\(m\to \infty\\), so that \\(\mu = m \varepsilon = \text{const}\\).

$$\boxed{F = \dfrac{\mu}{\pi z}} \notag $$

The complex potential, 

$$\boxed{W = \dfrac{dF}{dz} = - \dfrac{\mu}{\pi z^2}= -\dfrac{\mu}{\pi r^2} e^{-i2 \theta}} \notag $$

### Cylinder in a Stream 

Let's superimpose a doublet and a stream, 

$$\begin{align*}
    F = Uz + U \dfrac{r_0^2}{z} \\
    W = U -U \dfrac{r_0^2}{z^2}
\end{align*}$$

Plug in \\(z=re^{i \theta}\\), so that the complex velocity becomes

$$\begin{align*}
    W &=U \left[1- \left( \dfrac{r_0}{r}\right)^2 e^{-i 2 \theta} \right] \\
     &= U \left[e^{i \theta} - \left(\dfrac{r_0}{r} \right)^2 e^{-i \theta} \right] e^{-i \theta} \\
     &= U \left\{ \left[1- \left(\dfrac{r_0}{r} \right)^2 \right] \cos \theta  + i \left[ 1+\left( \dfrac{r_0}{r}\right)^2 \right] \sin \theta \right\} e^{-i\theta}
\end{align*}$$

Thus,

$$\boxed{\begin{aligned}
    u_r &= U \left[1- \left(\dfrac{r_0}{r} \right)^2 \right] \cos \theta \\
    u_\theta &= - U \left[ 1 + \left( \dfrac{r_0}{r}\right)^2\right] \sin \theta
\end{aligned}} \notag $$

On the surface of the cylinder, \\(r=r_0\\), \\(u_r=0\\), and \\(u_\theta=-2U \sin \theta\\),

$$\begin{align*}
    C_p = 1- \left(\dfrac{q}{U} \right)^2 = 1-4 \sin^2 \theta
\end{align*}$$

<p align="center">
  <img src="/images/pressurecoeffcylinderupgraded.png" alt="Pressure coefficient distribution over a cylinder" width="48%">
  <img src="/images/streamlinescylinder.png" alt="Streamlines around a cylinder" width="48%">
</p>

<p align="center"><strong>Figure 5:</strong> Comparison of pressure distribution and streamline pattern for flow past a cylinder.</p>

<p align="center"><em>Left:</em> Pressure coefficient distribution over a cylinder. <em>Right:</em> Streamlines around a cylinder.</p>


### Cylinder in a Stream with Circulation

Let's say we add a uniform flow, a doublet, and a vortex. With all three, the complex potential becomes, 

$$\begin{align}
    F &= Uz + U \dfrac{r_0^2}{z} - \dfrac{i \Gamma}{2 \pi} \ln \left( \dfrac{z}{r_0}\right) \label{complexpotcylinder} \\
    W &= \dfrac{dF}{dz} = U - U \dfrac{r_0^2}{z^2} - i \dfrac{\Gamma}{2 \pi z} \label{complexvelcylinder}
\end{align}$$

Let's rewrite Eq. \ref{complexvelcylinder} in a form that allows us to extract the radial and tangential velocities. 

$$\begin{align*}
    W \bigg(z=re^{i \theta} \bigg) &= U - U \left( \dfrac{r_0}{r} \right)^2 e^{-i 2 \theta} - \dfrac{i \Gamma}{2 \pi r} e^{-i \theta} \\
    &= \left[U e^{i \theta} - U \left(\dfrac{r_0}{r} \right)^2 e^{-i \theta} -\dfrac{i \Gamma}{2\pi r} \right] e^{-i \theta} \\
    &= \left\{U \left[1- \left(\dfrac{r_0}{r} \right)^2 \right] \cos \theta \right\} - i \left\{ -U \left[ 1+ \left( \dfrac{r_0}{r}\right)^2\right] \sin \theta + \dfrac{\Gamma}{2 \pi r}\right\}
\end{align*}$$

$$\boxed{\begin{aligned}
    u_r &=U \left[1- \left(\dfrac{r_0}{r} \right)^2 \right] \cos \theta \\
   u_\theta &= -U \left[ 1+ \left( \dfrac{r_0}{r}\right)^2\right] \sin \theta + \dfrac{\Gamma}{2 \pi r}
\end{aligned}} \notag $$

I locate the stagnation points by setting \\(u_\theta=0\\),

$$\begin{equation}
    \boxed{\sin \theta_0= \dfrac{\Gamma}{4U \pi r_0}=- \dfrac{\Gamma_a}{4U \pi r_0}}
    \label{stagnationpointscylinderwcirc}
\end{equation}$$

If I carefully expand the complex potential into real and imaginary parts, using polar coordinates, 

$$\boxed{F = \left\{\left[ 1 + \left( \dfrac{r_0}{r}\right)^2 \right] U r \cos \theta + \dfrac{\Gamma \theta}{2 \pi} \right\} + i \left\{ \left[1 - \left( \dfrac{r_0}{r} \right)^2 \right] Ur \sin \theta - \dfrac{\Gamma}{2 \pi} \ln \left( \dfrac{r}{r_0}\right) \right\}} \notag $$
Note: Aeronautical engineers typically define \\(\Gamma_a = -\Gamma \\) in order to make lift positive. 

<p align="center">
  <img src="/images/streamlinecylindercirculation.png" alt="Streamlines for Cylinder with Circulation" width="50%" style="border:1px solid #000;">
</p>

<p align="center"><strong>Figure 6:</strong> Streamlines for Cylinder with Circulation</p>


## Aerodynamics

### Kutta-Joukowski Law

<p align="center">
  <img src="/images/airfoilgeometry.jpg" alt="Airfoil Geometry" width="40%" style="border:1px solid #000;">
</p>

<p align="center"><strong>Figure 7:</strong> Airfoil Geometry</p>


From Fig. 7, we get, 

$$\begin{align*}
    dF_L &= p dx \\
    dF_D &= -p dy
\end{align*}$$

Forming the complex conjugate force, 

$$\begin{align*}
    d ( F_D - iF_L) &= -p dy - i  p dx \\
    &=-ip ( dx - i dy) \\
    &= -ip d \overline{z}
\end{align*}$$

From Bernoulli's equation,

$$\begin{align*}
    p &= p_0 - \dfrac{1}{2} \rho W \overline{W} \\
    &= p_0 - \dfrac{1}{2}\rho \dfrac{dF}{dz} \dfrac{d\overline{F}}{d \overline{z}}
\end{align*}$$

Plugging this into the complex conjugate force, 

$$\begin{align*}
    d(F_D - i F_L) = -ip_0 d \overline{z} + i \dfrac{1}{2}\rho \dfrac{dF}{dz} d \overline{F}
\end{align*}$$

If I integrate around the contour of the airfoil (or any shape really), 

$$\begin{align*}
    F_D -iF_L = \underbrace{\oint_C -i p_0 d \overline{z}}_{0} + \oint_C i \dfrac{\rho}{2}\dfrac{dF}{d z} d \overline{F} 
\end{align*}$$

On the streamline forming the boundary of the airfoil, \\(d\psi = 0\\), so that \\(dF = d\phi\\), which means that \\(dF = d \overline{F}\\),

$$\begin{equation}
    \boxed{F_D-iF_L = i \dfrac{\rho}{2} \oint_C \left(\dfrac{dF}{dz} \right)^2 dz=i \dfrac{\rho}{2} \oint_C W^2 dz} 
    \label{blasiustheorem}
\end{equation}$$

This is called \\( \textbf{Blasius Theorem} \\). To evaluate the integral, we employ the residue theorem, which allows us to evaluate contour integrals of analytic functions, 

$$\text{Residue Theorem: } \oint_C W^2 dz = 2 \pi i \sum_k R_k \notag $$

,where \\(R_k\\) are the residues of the function \\(W^2\\). We can use a contour at infinity because any contour of an analytic function gives the same answer as long as it loops around the same singular points of the function. 

The complex potential tends to have the form, (uniform flow + vortex + doublet) 

$$ F = Uz - i \dfrac{\Gamma}{2 \pi} \ln z + (a+ib) \dfrac{1}{z} + ...  \notag $$

Differentiating, 

$$\begin{align*}
    W &= U - \dfrac{i \Gamma}{2 \pi z} + O \left[ \dfrac{1}{z^2}\right] \\
    W^2 &= U^2 + \dfrac{i U \Gamma_a}{\pi z} + O \left[ \dfrac{1}{z^2}\right]
\end{align*}$$

The residue is \\(R= i \Gamma_a U/\pi\\), the coefficient in front of \\(1/z\\). Using Eq. \ref{blasiustheorem} and the residue theorem, 

$$F_D - i F_L = i \dfrac{\rho}{2} \left[(2\pi i) \left(\dfrac{iU \Gamma_a}{\pi} \right) \right]= -i \rho U \Gamma_a \notag $$

$$\boxed{F_L = \rho U \Gamma_a, \quad F_D =0} \notag $$

### Conformal Mapping

Consider the following complex function, 

$$\begin{equation}
    \zeta(z) = z + \dfrac{1}{z}
    \label{conformalmappingex1}
\end{equation}$$

We think of this function as "mapping" points in the z-plane to points in the \\(\zeta\text{-plane}\\)

$$\text{function} \ \zeta(z): \quad  z=x+iy \, \mapsto \,
 \zeta=\xi + i \eta  \notag $$

For example, under the transformation given by Eq. \ref{conformalmappingex1}, a circle of radius 1 maps to a line, and a circle of radius 1.1 maps to an oval shape.

<p align="center">
  <img src="/images/conformalmapex1.png" alt="Conformal map example" width="100%" style="border:1px solid #000;">
</p>

<p align="center"><strong>Figure 8:</strong> Circles \(r_0 = 1 \ \text{(blue)}\) and \(r_0 = 1.1 \ \text{(red)}\) in the \(z\)-plane mapped to corresponding shapes in the \(\zeta\)-plane under the transformation given by Eq. \ref{conformalmappingex1}.</p>

Consider the two complex potentials, 

$$\begin{align*}
    F(z) &= \phi (x,y) + i \psi (x,y) \\
    \hat{F}(\zeta) &= \hat{\phi} (\xi,\eta) + i \hat{\psi}(\xi, \eta) 
\end{align*}$$

They are related in such a way that 

$$\begin{align*}
    F(z(\zeta)) &= \hat{F}(\zeta) \\
    \hat{F}(\zeta(z)) &= F(z) 
\end{align*}$$

#### Joukowski Airfoil

For a Joukowski airfoil, let's consider the conformal mapping, 

$$\begin{equation}
    z(\zeta) = \zeta + \dfrac{c^2}{\zeta}
    \label{joukowskitransformation}
\end{equation}$$

Under this transformation, some circles in the \\(\zeta \text{-plane}\\) turn into airfoil shapes. See Fig. 9

<p align="center">
  <img src="/images/joukowski-airfoil.png" alt="Joukowski airfoil mapping" width="100%" style="border:1px solid #000;">
</p>

<p align="center"><strong>Figure 9:</strong> Mapping of a circle in the \(\zeta\)-plane centered at \(-0.023 + i0.020\) with radius \(r_0 = 0.274\) to a Joukowski airfoil under the transformation: \(z = \zeta + \frac{1/16}{\zeta}\). The \(1/16\) factor is to ensure a chord length of 1.</p>

Let's look more closely at the geometry of the circle in the \\(\zeta \text{-plane}\\) that maps to the Joukowski airfoil. Importantly, the circle is off-centered. 

<p align="center">
  <img src="/images/closerinzetaplane.jpg" alt="Off-centered Circle in zeta-plane" width="100%" style="border:1px solid #000;">
</p>

<p align="center"><strong>Figure 10:</strong> Off-centered Circle in \(\zeta\)-plane and a Zoomed-In version of the Geometry</p>

Overall, the main goal is to parameterize the path of the cirle as a function of the angle \\(\gamma\\), which is shown in Fig. 10. The circle is described by,

$$\begin{equation*}
    \zeta_c = b e^{i \gamma}
\end{equation*}$$

Divide both sides by c, 

$$\begin{equation}
    \dfrac{\zeta_c}{c} = \dfrac{b}{c} e^{i \gamma}
    \label{parameterizationofcircle}
\end{equation}$$

If we could somehow describe \\(b/c\\) as a function of \\(\gamma\\) in Eq. \ref{parameterizationofcircle}, then we will have successfully parameterized the circle. Then we can plug \\(\zeta_c\\) into Eq. \ref{joukowskitransformation} to find the corresponding airfoil shape.

To do that, we use Law of Cosines on triangles OAB and OAC, 

$$\begin{align*}
    r_0^2 &= m^2 + b^2 - 2mb \cos (\delta-\gamma) \\
    r_0^2 &= m^2 + c^2 - 2mc \cos (\delta)
\end{align*}
$$

Setting \\(r_0^2\\) equal to each other,

$$\begin{align*}
    m^2 + b^2 - 2mb \cos (\delta - \gamma) &= m^2 + c^2 - 2mc \cos (\delta) \\
    \dfrac{b^2}{c^2}-\dfrac{2 m b}{c^2} \cos (\delta - \gamma) &= 1 - \dfrac{2 m}{c} \cos (\delta)
\end{align*}$$

$$\begin{align*}
    \left( \dfrac{b}{c}\right)^2 - 2 \left(\dfrac{m}{c} \right) \left(\dfrac{b}{c} \right) \cos (\delta - \gamma) + \dfrac{2m}{c} \cos \delta -1 =0 
\end{align*}$$

Let's define \\(\varepsilon=m/c\\), 

$$\left( \dfrac{b}{c} \right)^2 + \bigg[- 2 \varepsilon \cos (\delta-\gamma) \bigg] \left(\dfrac{b}{c} \right)  + 2 \varepsilon \cos \delta - 1 = 0  \notag $$

Use the quadratic formula to solve for \\(b/c\\),

$$\begin{align*}
    \dfrac{b}{c} = g(\varepsilon) = \varepsilon \cos (\delta - \gamma) + \sqrt{\varepsilon^2 \cos^2 (\delta - \gamma) - 2 \varepsilon \cos \delta + 1} 
\end{align*}$$

We can perform a Taylor series expansion on \\(g(\varepsilon)\\), 

$$\begin{equation}
    \dfrac{b}{c} = g(\varepsilon) = 1 + B \varepsilon + O(\varepsilon^2)
    \label{bceqn}
\end{equation}$$

where

$$B= g'(0)= \cos (\delta-\gamma) - \cos \delta = \sin \delta \sin \gamma - (1-\cos \gamma) \cos \delta \notag $$

Plug Eq. \ref{bceqn} into Eq. \ref{parameterizationofcircle},

$$\begin{equation*}
    \dfrac{\zeta_c}{c} = \dfrac{b}{c} e^{i \gamma} = ( 1 + B \varepsilon) e^{i \gamma}
\end{equation*}$$

Plug this into Eq. \ref{joukowskitransformation},

$$\begin{align*}
    z_s = \zeta_c + \dfrac{c}{\zeta_c/c}= c ( 1+B \varepsilon) e^{i \gamma} + c (1+B \varepsilon)^{-1} e^{-i \gamma}
\end{align*}
$$

Use the Taylor series expansion, \\((1+ B \varepsilon)^{-1}= 1-B\varepsilon + O (\varepsilon^2)\\).

$$\begin{align*}
    \dfrac{z_s}{c} &= (1 + B \varepsilon) e^{i \gamma} + (1-B\varepsilon) e^{-i \gamma} \\
     \dfrac{z_s}{c} &= 2 \cos \gamma + 2 B \varepsilon i \sin \gamma
\end{align*}$$

$$\begin{equation*}
    \boxed{\dfrac{z_s}{4c} = \dfrac{\cos \gamma}{2} + \dfrac{B \varepsilon i \sin \gamma}{2}}
\end{equation*}$$

The chord length is \\(l= 4 c\\).

$$\dfrac{x_s}{l} = \dfrac{\cos \gamma}{2}, \quad \dfrac{y_s}{l} = \dfrac{B \varepsilon \sin \gamma}{2} \notag $$

Solve the \\(x_s/l\\) equation for \\(\cos \gamma\\),

$$\cos \gamma = \dfrac{2 x_s}{l} \notag $$

Using the trig identity, \\(\sin^2 \gamma + \cos ^2 \gamma = 1 \\), 

$$\begin{align*}
    \sin \gamma &= \pm \sqrt{1- \cos^2 \gamma} \\
    &= \pm \sqrt{1 - \left( \dfrac{2x_s}{l}\right)^2}
\end{align*}$$

Look at the \\(y_s/l\\) formula. Substitute \\(B\\) and \\(\sin \gamma\\). After some length algebra, 

$$\begin{equation}
    \dfrac{y_s}{l} = \dfrac{\varepsilon \sin \delta}{2} \left[1-4\left(\dfrac{x_s}{l} \right)^2 \right] \pm \dfrac{\varepsilon \cos \delta}{2} \left(1-2 \dfrac{x_s}{l} \right) \sqrt{1-4 \left(\dfrac{x_s}{l} \right)^2}
    \label{ys_l_formula}
\end{equation}$$

Defining \\(Y= y_s/l, \quad X = x_s/l, \quad H=h/l= (\varepsilon \sin \delta)/2, \quad T = t/l = (3 \varepsilon \sqrt{3}/4) \cos \delta\\),

$$\begin{equation}
    \boxed{Y = H(1-4X^2) \pm \dfrac{2T}{3 \sqrt{3}} (1-2X)\sqrt{1-4X^2}}
    \label{linearizedjoukowskiprofileequation}
\end{equation}
$$

This is the **linearized Joukowski profile equation** with thickness and camber parameters H and T. 

<details class="custom-collapse">
  <summary><strong>Physical Interpretation of H and T </strong></summary>
  <div class="collapse-content">
        You may wonder why H and T are defined in the way that they are defined. 

Look at Eq. \ref{ys_l_formula}, repeated below

$$   \begin{equation*}
    \dfrac{y_s}{l} = \underbrace{\dfrac{\varepsilon \sin \delta}{2} \left[1-4\left(\dfrac{x_s}{l} \right)^2 \right]}_{\text{camber line}} \pm \underbrace{\dfrac{\varepsilon \cos \delta}{2} \left(1-2 \dfrac{x_s}{l} \right) \sqrt{1-4 \left(\dfrac{x_s}{l} \right)^2}}_{\text{thickness distribution}}
    \end{equation*}$$

The equation can be divided into two parts: the camber and the thickness distribution. The equation for the camber line is just an upside down parabola shifted up, so its maximum value is \(H=h/l=\dfrac{\varepsilon}{2} \sin \delta \), which occurs at \(X=x_s/l=0\). 

For the thickness distribution, we can use calculus to determine that the maximum occurs at \( X=-1/4 \). The maximum thickness of the airfoil is then \(T=\dfrac{3 \sqrt{3}}{4} \varepsilon \cos \delta\).

  </div>
</details>

The center of the circle is given by the equation, 

$$\dfrac{\zeta_0}{c} = \varepsilon e^{\delta i } = \varepsilon \cos \delta + i \varepsilon \sin \delta = -\dfrac{4T}{3\sqrt{3}}+ i 2H \notag $$

With some rearranging, 

$$\zeta_0= -\dfrac{t}{3 \sqrt{3}} + i \dfrac{h}{2} \notag $$

#### Complex Potential of Joukowski Airfoil in Uniform Stream

<p align="center">
  <img src="/images/cylinderjoukowski.jpg" alt="Circular Cylinder off center and at angle of attack alpha" width="50%" style="border:1px solid #000;">
</p>

<p align="center"><strong>Figure 11:</strong> Circular Cylinder off center and at angle of attack \(\alpha\). <em>Source: Incompressible Flow, Ronald L. Panton</em></p>


To examine the flow around a Joukowski airfoil, we have to first examine the flow around a circular cylinder before the conformal transformation is applied. Take Eq. \ref{complexpotcylinder} but replace \\(z\\) with \\(\hat{\zeta}\\).

$$\begin{equation}
    F = U \hat{\zeta} + U \dfrac{r_0^2}{\hat{\zeta}} + \dfrac{i \Gamma_a}{2 \pi} \ln \left( \dfrac{\hat{\zeta}}{r_0}\right) 
    \label{Fzetahat}
\end{equation}$$

We introduce a \\(\hat{\zeta}=\hat{\xi} + i \hat{\eta}\\) coordinate system aligned with the flow at infinity and has its origin at the center of the circle. Look at Fig. 12. Since the coordinate system is rotated \\(\alpha\\) degrees counterclockwise, the components transform contravariantly with a rotation \\(\alpha\\) degrees clockwise. 

<p align="center">
  <img src="/images/newcoordinatesystem_joukowski.jpg" alt="New coordinate system aligned with flow at infinity" width="50%" style="border:1px solid #000;">
</p>

<p align="center"><strong>Figure 12:</strong> New coordinate system aligned with flow at infinity and has origin at center of circle</p>

Therefore, 

$$\begin{equation}
    \hat{\zeta} = (\zeta-\zeta_0) e^{-i\alpha}
    \label{zetahat}
\end{equation}$$

Eq. \ref{Fzetahat} together with Eq. \ref{zetahat} yield, 

$$\boxed{F = U (\zeta-\zeta_0) e^{-i\alpha} + U \dfrac{r_0^2}{(\zeta-\zeta_0)} e^{i \alpha} + \dfrac{i \Gamma_a}{2 \pi} \ln \left[ \dfrac{(\zeta-\zeta_0) e^{-i\alpha}}{r_0}\right]}  \notag $$

Differentiating, 

$$\hat{W}=\dfrac{dF}{d \zeta}=U e^{-i \alpha} - \dfrac{U r_0^2}{(\zeta-\zeta_0)^2} e^{i \alpha} + i \dfrac{\Gamma_a}{2 \pi} \dfrac{1}{(\zeta-\zeta_0)} \notag $$

Because of chain rule, 

$$\begin{align*}
    W=\dfrac{dF}{dz} = \dfrac{dF}{d \zeta} \dfrac{d\zeta}{dz} = \hat{W} \dfrac{d \zeta}{dz}
\end{align*}$$

Therefore,

$$\boxed{W = \left[U e^{-i \alpha} - \dfrac{U r_0^2}{(\zeta-\zeta_0)^2} e^{i \alpha} + i \dfrac{\Gamma_a}{2 \pi} \dfrac{1}{(\zeta-\zeta_0)} \right] \left[1 - \dfrac{c^2}{\zeta^2} \right]^{-1}} \notag $$

From the geometry of Fig. 11,

$$r_0 = \left( \dfrac{1}{4} + \dfrac{T}{3 \sqrt{3}}\right) l  \notag $$

$$\beta = \dfrac{h/2}{l/4} = 2H \notag $$

The location of the TE stagnation point is, (compare with Eq. \ref{stagnationpointscylinderwcirc})

$$\sin (\alpha + \beta) = \sin (\alpha + 2 H) = \dfrac{\Gamma_a}{4 U \pi r_0} \notag $$

Using Kutta's Law, 

$$F_L = 4 \pi l \rho U^2 \left( \dfrac{1}{4} + \dfrac{T}{3 \sqrt{3}} \right) \sin (\alpha + 2H)  \notag $$

$$C_L = 2 \pi ( \alpha + 2H) \notag $$

## References

**Complex Analysis (Visual Introduction)** – "What does it mean to take a complex derivative? (visually explained)" by _vcubingx_. [https://www.youtube.com/watch?v=0CHZMY02Dhk](https://www.youtube.com/watch?v=0CHZMY02Dhk).
    
**Advanced Engineering Mathematics** – Erwin Kreyszig, 10th Edition, Wiley.
    
**Incompressible Flow** – Ronald L. Panton, 4th Edition, Wiley.
    
**Fluid Mechanics** – Pijush K. Kundu, Ira M. Cohen, and David R. Dowling, 6th Edition, Academic Press.

<a href="/academics/" class="button-gradient" style="display: inline-block; margin-top: 20px;">
  ← Back to Academic Works Page
</a>

<!-- CSS -->
<style>
.page-content {
  margin-right: 270px; /* push main text to the left of sidebar */
  max-width: 700px;
  padding: 1rem;
}

.sidebar-toc {
  position: fixed;
  top: 70px;
  right: 10px;
  width: 200px;
  max-height: 80vh;
  overflow-y: auto;
  padding: 1rem;
  background: #f8f9fa;
  border: 1px solid #ddd;
  border-radius: 8px;
  font-size: 0.95rem;
  z-index: 999;
}

.sidebar-toc h3 {
  margin-top: 0;
  font-size: 1.1rem;
  border-bottom: 1px solid #ccc;
  padding-bottom: 0.5rem;
}

.sidebar-toc ul {
  list-style: none;
  padding-left: 0;
  margin: 0;
}

.sidebar-toc li {
  margin: 0.4rem 0;
}

.sidebar-toc ul ul {
  margin-left: 1rem; /* indent nested levels (for h3) */
  font-size: 0.9rem;
}

.sidebar-toc ul ul ul {
  margin-left: 1.2rem; /* indent further for h4 */
  font-size: 0.85rem;
}

.sidebar-toc a {
  text-decoration: none;
  color: #333;
}

.sidebar-toc a:hover {
  color: #007acc;
}

.sidebar-toc a.active {
  font-weight: bold;
  color: #007acc;
}

.sidebar-toc::-webkit-scrollbar {
  width: 6px;              /* scrollbar width */
}

.sidebar-toc::-webkit-scrollbar-track {
  background: transparent; /* track background */
}

.sidebar-toc::-webkit-scrollbar-thumb {
  background: #bbb;        /* scrollbar color */
  border-radius: 3px;      /* rounded edges */
}

.sidebar-toc::-webkit-scrollbar-thumb:hover {
  background: #888;        /* darker on hover */
}

/* Hide TOC on all mobile devices and tablets */
@media (max-width: 1450px) {
  .sidebar-toc {
    display: none !important;
  }
}
</style>

<script>
document.addEventListener("DOMContentLoaded", function () {
  document.addEventListener("scroll", function () {
    const links = document.querySelectorAll(".sidebar-toc a");
    let current = "";
    document.querySelectorAll("h2, h3, h4").forEach(section => {
      const sectionTop = section.getBoundingClientRect().top + window.pageYOffset - 130;
      if (window.scrollY >= sectionTop) {
        current = section.getAttribute("id");
      }
    });

    links.forEach(link => {
      link.classList.remove("active");
      if (link.getAttribute("href") === "#" + current) {
        link.classList.add("active");

        const toc = document.querySelector(".sidebar-toc");
        if (toc) {
          const linkRect = link.getBoundingClientRect();
          const tocRect = toc.getBoundingClientRect();

          if (linkRect.top < tocRect.top || linkRect.bottom > tocRect.bottom) {
            link.scrollIntoView({
              block: "center",
              behavior: "smooth"
            });
          }
        }
      }
    });
  });
});
</script>

