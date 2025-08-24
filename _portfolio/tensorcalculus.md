---
title: "Tensor Analysis in Fluid Mechanics"
excerpt: "I use tensor calculus to formulate the governing equations of fluid motion, generalizing the results to general coordinate systems. Christoffel symbols, Covariant derivative, Metric Tensor"
collection: portfolio
author_profile: false
layout: single
image: /images/tensorsimage.png
caption: "Photo credit: Wikipedia"
toc: true
order: 4
---
{% include toc %}

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

## Cartesian Tensors

Before delving into the general case with curvilinear coordinates, it helps to focus on the simple case: Cartesian coordinates. 

In Cartesian coordinates, the vector \\( \mathbf{a} \\) is defined as, 

$$\begin{align*}
    \bar{a}_j &= l_{ij} a_i \\
    a_i &= l_{ij} \bar{a}_j
\end{align*}$$

This is known as a first-order tensor. Here, \\( l_{ij} \\) is the cosine of the angle between \\( O_i \\) and \\( O_{\bar{j}} \\). A second order tensor transforms as,

$$\begin{align*}
    \bar{A}_{pq} &= l_{ip} l_{jq} A_{ij} \\
    A_{ij} &= l_{ip} l_{jq} \bar{A}_{pq}
\end{align*}$$

In general, a tensor \\( \mathbf{A} \\) of order n transforms as,

$$\bar{A}_{pq...t} = l_{ip} l_{jq} ...l_{nt} A_{ij...n} \notag
$$

## Eigenvalues and Eigenvectors of a Cartesian Tensor

$$\begin{align*}
    \mathbf{A} \cdot \mathbf{x} &= \lambda \mathbf{x} \\
    (\mathbf{A}-\lambda \mathbf{I}) \cdot \mathbf{x} &= \mathbf{0} \\
    (A_{ij} -\lambda \delta_{ij}) x_j &= 0
\end{align*}$$

<p>
Non-trivial solutions only exist when \( \det (\mathbf{A}-\lambda \mathbf{I})=0 \). For a symmetric tensor, where \( \mathbf{A}=\mathbf{A}^T \), we want to prove that the eigenvectors corresponding to distinct eigenvalues are orthogonal. To do that, let's consider two eigenvectors \( \mathbf{x}_{(p)} \) and \( \mathbf{x}_{(q)} \) corresponding to eigenvalues \( \lambda_{(p)} \) and \( \lambda_{(q)} \), respectively.
</p>

In dyadic notation,

$$\mathbf{A} \cdot \mathbf{x}_{(p)} = \lambda \mathbf{x}_{(p)}, \quad \text{and } \quad \mathbf{A} \cdot \mathbf{x}_{(q)} = \lambda \mathbf{x}_{(q)} \notag$$

<p> Now, we dot the first equation with \( \mathbf{x}_{(q)} \) and the second equation with \( \mathbf{x}_{(p)} \), obtaining </p>

$$
\mathbf{A} \cdot \mathbf{x}_{(p)} \cdot \mathbf{x}_{(q)} = \lambda \, \mathbf{x}_{(p)} \cdot \mathbf{x}_{(q)}, \quad \mathbf{A} \cdot \mathbf{x}_{(q)} \cdot \mathbf{x}_{(p)} = \lambda \, \mathbf{x}_{(q)} \cdot \mathbf{x}_{(p)} \notag
$$

We switch back to index notation,

$$A_{ij} x_{j(p)} x_{i(q)} = \lambda_{(p)} x_{i(p)} x_{i(q)}, \quad A_{ij} x_{j(q)} x_{i(p)} = \lambda_{(q)} x_{i(q)} x_{i(p)} \notag$$

The symmetry of \\( \mathbf{A} \\) allows us to set the left-hand sides of both equations equal to each other. Since \\( A_{ij}=A_{ji} \\), we can interchange the indices, 

$$\begin{equation*}
    \boxed{A_{ij} x_{i(p)}x_{j(q)}=\lambda_{(p)} x_{i(p)} x_{i(q)} = \lambda_{(q)} x_{i(q)} x_{i(p)}}
\end{equation*}$$

Since \\( \lambda_{(p)} \\) and \\( \lambda_{(q)} \\) are assumed to be distinct, we have that 

$$x_{i(p)} x_{i(q)}=0, \quad \text{or} \quad \mathbf{x}_{(p)} \cdot \mathbf{x}_{(q)}=0 \notag$$

Therefore, the eigenvectors are orthogonal. Let's also assume that the eigenvectors are unit length. 

$$\mathbf{x}_{(p)} \cdot \mathbf{x}_{(p)}=1, \quad \text{or} \quad x_{i(p)}x_{i(p)}=1 \notag$$

$$\mathbf{x}_{(q)} \cdot \mathbf{x}_{(q)}=1, \quad \text{or} \quad x_{i(q)}x_{i(q)}=1 \notag
$$

In other words,
$$x_{i(p)}x_{i(q)}=\delta_{pq} \notag
$$

Let's say that we change the coordinate system so that it aligns with the same direction as the eigenvectors. Then, the tensor A reduces to a diagonal form. In that case, \\( x_{i(p)} \\) and \\( x_{j(q)} \\) can be regarded as the direction cosines \\( l_{ip} \\) and \\( l_{jq} \\). To see this, note that 

$$\mathbf{x}_{(p)} = l_{ip} \mathbf{e}_i, \quad \text{and} \quad \mathbf{x}_{(q)}=l_{jq} \mathbf{e}_j \notag
$$

$$\overline{A_{pq}}=A_{ij}l_{ip}l_{jq}= \lambda_{(p)} \delta_{pq} \notag
$$

Therefore, when changing the coordinate system so that it is aligned with the normalized eigenvectors, also known as the **principal directions** of \\( \mathbf{A}\\), the tensor is in diagonal form. 

## Invariants of a Cartesian Tensor

Let's evaluate \\( \det (\mathbf{A}-\lambda \mathbf{I})=0 \\). In matrix form, this is,

$$\begin{vmatrix}
    A_{11}-\lambda & A_{12} & A_{13} \\
    A_{21} & A_{22}-\lambda & A_{33} \\
    A_{31} & A_{32} & A_{33}-\lambda
\end{vmatrix} =0 \notag$$

The evaluation of which is,
\\( \Psi  - \lambda \Phi + \lambda^2 \Theta - \lambda^3=0, \quad \text{where} \\)

$$\begin{align*}
    \Theta &= \text{tr} \ \mathbf{A} \\
    \Phi &= A_{22} A_{33} - A_{23}A_{32} + A_{33} A_{11} - A_{31} A_{13} + A_{11} A_{22} - A_{12} A_{21} \\
    \Psi &= \det \mathbf{A}
\end{align*}$$

## Kinematics

We construct two coordinate systems: the **material coordinates** of a particle and the **spatial coordinates** of a particle. The material coordinates refer to a coordinate system that is convected with the fluid particle. We denote the material coordinates with \\( \boldsymbol{\varepsilon} \\) and the spatial coordinates with \\( \mathbf{x} \\).

The velocity gradient tensor, in dyadic notation, is \\( \nabla \mathbf{V}= \dfrac{d \mathbf{V}}{d \mathbf{x}} \\). It describes two things in a flow: rate of strain and rigid body rotation of a fluid particle. This is represented by the symmetric and antisymmetric parts of the tensor, respectively. Here, \\( \mathbf{e} \\) is the rate of strain tensor, and \\( \boldsymbol{\Omega} \\) is the rigid body rotation tensor. 

$$
\nabla \mathbf{V} = \mathbf{e} + \boldsymbol{\Omega} = \dfrac{1}{2} \bigg[ \nabla \mathbf{V} + (\nabla \mathbf{V})^T \bigg] + \dfrac{1}{2} \bigg[ \nabla \mathbf{V} - (\nabla \mathbf{V})^T \bigg] \notag
$$

In index notation and in Cartesian coordinates, this is written as, 

$$\dfrac{\partial u_i}{\partial x_j}= e_{ij} + \Omega_{ij} = \dfrac{1}{2} \left( \dfrac{\partial u_i}{\partial x_j} + \dfrac{\partial u_j}{\partial x_i} \right) + \dfrac{1}{2} \left(\dfrac{\partial u_i}{\partial x_j} - \dfrac{\partial u_j}{\partial x_i} \right) \notag$$


The principal axes of strain are the directions of the eigenvectors of the tensor \\( \mathbf{e} \\), and the principal rates of strain are the eigenvalues. Therefore, we solve \\( \det (\mathbf{e}-d\mathbf{I})=0 \\)

$$\Psi  - d \Phi + d^2 \Theta - d^3=0, \quad \text{where} \notag$$

$$\begin{align*}
    \Theta &= \text{tr} \ \mathbf{e} = e_{11}+ e_{22} + e_{33}\\
    \Phi &= e_{22} e_{33} - e_{23}e_{32} + e_{33} e_{11} - e_{31} e_{13} + e_{11} e_{22} - e_{12} e_{21} \\
    \Psi &= \det \mathbf{e}
\end{align*}$$

## Stress and Constitutive Equations

We may always decompose the stress tensor into the sum of isotropic and deviatoric tensors. This amounts to separating the stress tensor into the hydrostatic pressure tensor plus the viscous stress tensor. 

$$\boldsymbol{\sigma}= -p \mathbf{I} + \boldsymbol{\tau}, \quad \text{or} \quad \sigma_{ij}=-p \delta_{ij}+\tau_{ij} \notag$$

For a Stokesian fluid, 

$$\tau_{ij}= \alpha \delta_{ij} + \beta e_{ij} + \gamma e_{ik} e_{kj} \notag$$

For a Newtonian fluid, 

$$\tau_{ij} = \lambda \Theta \delta_{ij} + 2 \mu e_{ij} \notag
$$

For our purposes, Newtonian fluid will suffice. Therefore, the stress tensor can be written as, for a Newtonian fluid,

$$\boxed{\sigma_{ij} = (-p + \lambda \Theta) \delta_{ij} + 2 \mu e_{ij}, \quad \boldsymbol{\sigma}=\bigg[-p+\lambda(\nabla \cdot \mathbf{u}) \bigg] \mathbf{I}+2\mu \mathbf{e}} \notag
$$

For the momentum equation, calculating the divergence of the stress tensor is needed. In preparation of this, I will calculate the divergence here, 

$$\begin{align*}
    (\nabla \cdot \boldsymbol{\sigma})_i = \dfrac{\partial \sigma_{ij}}{\partial x_j} &= \delta_{ij} \dfrac{\partial}{\partial x_j} (-p + \lambda \Theta) + \mu \dfrac{\partial}{\partial x_j} \left( \dfrac{\partial u_i}{\partial x_j}+\dfrac{\partial u_j}{\partial x_i} \right) \\
    &= \dfrac{\partial}{\partial x_i} (-p + \lambda \Theta) + \mu \left( \dfrac{\partial}{\partial x_j} \dfrac{\partial u_i}{\partial x_j} + \dfrac{\partial}{\partial x_i} \dfrac{\partial u_j}{\partial x_j} \right) \\
    &= \dfrac{\partial}{\partial x_i} (-p + \lambda \Theta) + \mu \left[ \nabla^2 u_i + \dfrac{\partial}{\partial x_i}(\nabla \cdot \mathbf{u})\right] \\
    & (\text{recall that } \Theta = \nabla \cdot \mathbf{u}) \\
     (\nabla \cdot \boldsymbol{\sigma})_i=\dfrac{\partial \sigma_{ij}}{\partial x_j}&= -\dfrac{\partial p}{\partial x_i} + (\lambda + \mu) \dfrac{\partial}{\partial x_i} (\nabla \cdot \mathbf{u}) + \mu \nabla^2 u_i
\end{align*}$$

Therefore, 

$$\begin{equation}
    \boxed{\nabla \cdot \boldsymbol{\sigma}= -\nabla p + (\lambda + \mu) \nabla (\nabla \cdot \mathbf{u})+\mu \nabla^2 \mathbf{u}}
    \label{divergenceofT}
\end{equation}$$

### Equations of Motion in Cartesian Coordinates

### Acceleration

$$\begin{align*}
    \mathbf{a} = \dfrac{D \mathbf{u}}{Dt} &= \dfrac{\partial \mathbf u}{\partial t} + \mathbf{u \cdot \nabla \mathbf{u}} \\
    a_i&= \dfrac{\partial u_i}{\partial t} + u_j \dfrac{\partial u_i}{\partial x_j}
\end{align*}$$

### Continuity

$$\begin{align*}
    \dfrac{\partial \rho}{\partial t} + \nabla \cdot (\rho \mathbf{u}) &= 0 \\
    \dfrac{\partial \rho}{\partial t} +  \dfrac{\partial}{\partial x_i} \bigg(\rho u_i \bigg) &=0
\end{align*}$$

### Momentum

Note: for the divergence of the stress tensor, I used the boxed formula derived above in the **Stress and Constitutive Equations** section.

$$\begin{align*}
    \rho \mathbf{a} &= \rho \mathbf{f} + \nabla \cdot \boldsymbol{\sigma} \\
    \rho a_i &= \rho f_i +\dfrac{\partial \sigma_{ij}}{\partial x_j} \\
    \rho a_i &= \rho f_i - \dfrac{\partial p }{\partial x_i} + (\lambda + \mu) \dfrac{\partial}{\partial x_i} (\nabla \cdot \mathbf{u}) + \mu \nabla^2 u_i
\end{align*}$$

$$\boxed{\rho \mathbf{a} = \rho \mathbf{f} - \nabla p + (\lambda + \mu) \nabla (\nabla \cdot \mathbf{u} ) + \mu \nabla^2 \mathbf{u}} \notag$$

<div class="equation-box">
  <h4><strong>Navier Stokes Equation for Newtonian Fluid (in Vector Form) </strong></h4>
  <div>

$$\rho \left( \dfrac{\partial \mathbf u}{\partial t} + \mathbf{u \cdot \nabla \mathbf{u}} \right) = \rho \mathbf{f} - \nabla p + (\lambda + \mu) \nabla (\nabla \cdot \mathbf{u} ) + \mu \nabla^2 \mathbf{u} \notag$$
  </div>
</div>


## Covariant and Contravariant Base Vectors

Let's define,

$$\begin{equation*}
    \mathbf{g}_{(i)}= \dfrac{\partial \mathbf{y}}{\partial x^i}
\end{equation*}$$

where \\( \mathbf{y} \\) is the position vector and \\( (x^1,x^2,x^3) \\) are the coordinates of the point in space. 

Suppose that we decide to use a different coordinate system, say \\( (\bar{x}_1, \bar{x}_2, \bar{x}_3) \\). Then, the basis vectors for those coordinates are, 

$$\mathbf{\bar{g}}_{(k)}= \dfrac{\partial \mathbf{y}}{\partial \bar{x}^k} \notag$$

I can write this in terms of the old basis vectors by using chain rule,

$$\mathbf{\bar{g}}_{(k)}= \dfrac{\partial \mathbf{y}}{\partial \bar{x}^k}=\dfrac{\partial x^i}{\partial \bar{x}^k} \dfrac{\partial \mathbf{y}}{\partial x^i}=\dfrac{\partial x^i}{\partial \bar{x}^k} \mathbf{g}_{(i)} \notag$$

Similarly, 

$$\mathbf{g}_{(i)} = \dfrac{\partial \bar{x}^k}{\partial x^i} \dfrac{\partial \mathbf{y}}{\partial \bar{x}^k}= \dfrac{\partial \bar{x}^k}{\partial x^i} \mathbf{\bar{g}}_{(k)} \notag $$

In summary.

$$\boxed{\mathbf{\bar{g}}_{(k)}=\dfrac{\partial x^i}{\partial \bar{x}^k} \mathbf{g}_{(i)}, \quad \mathbf{g}_{(i)} = \dfrac{\partial \bar{x}^k}{\partial x^i} \mathbf{\bar{g}}_{(k)}} \notag $$

Any arbitrary vector, which we call \\( \mathbf{A} \\), can be expressed in terms of the new or old basis 

$$\mathbf{A}=\bar{A}^k \bar{\mathbf{g}}_{(k)}=A^i \mathbf{g}_{(i)} \notag
$$

$$\mathbf{A} = \bar{A}^k \dfrac{\partial x^i}{\partial \bar{x}^k} \mathbf{g}_{(i)}=A^i \dfrac{\partial \bar{x}^k}{\partial x^i} \mathbf{\bar{g}}_{(k)} \notag
$$

$$\boxed{A^i = \bar{A}^k \dfrac{\partial x^i}{\partial \bar{x}^k}, \quad \bar{A}^k=A^i \dfrac{\partial \bar{x}^k}{\partial x^i}} \notag
$$

To find the length of this vector, I take the dot product of \\( \mathbf{A} \\) with itself, 

$$||\mathbf{A}||^2=\mathbf{A} \cdot \mathbf{A}= A^i \mathbf{g}_{(i)} \cdot A^j \mathbf{g}_{(j)} = A^i A^j \bigg(\mathbf{g}_{(i)} \cdot \mathbf{g}_{(j)} \bigg)=A^i A^j g_{ij} \notag $$

<p>The second order tensor \( g_{ij} = \mathbf{g}_{(i)} \cdot \mathbf{g}_{(j)} \) is known as the metric tensor. When the position vector is expressed in Cartesian components, \( \mathbf{y}=\sum y_k \mathbf{e}_{(k)} \), the metric tensor is calculated as, </p>

$$g_{ij}=\sum_{k=1}^3 \dfrac{\partial y_k}{\partial x^i} \dfrac{\partial y_k}{\partial x^j} \notag$$

The reciprocal (or dual) basis vectors \\( \mathbf{g}^{(i)} \\) are defined as 

$$\mathbf{g}^{(i)} \cdot \mathbf{g}_{(j)} = \delta^i_j \notag$$

To calculate the reciprocal basis from the original basis, we use the following formulas, 

$$
\mathbf{g}^{(1)} = \dfrac{1}{J} \bigg(\mathbf{g}_{(2)} \times \mathbf{g}_{(3)} \bigg), \quad
\mathbf{g}^{(2)} = \dfrac{1}{J} \bigg(\mathbf{g}_{(3)} \times \mathbf{g}_{(1)} \bigg), \quad
\mathbf{g}^{(3)} = \dfrac{1}{J} \bigg(\mathbf{g}_{(1)} \times \mathbf{g}_{(2)} \bigg) \notag$$

$$J = \mathbf{g}_{(1)} \cdot \bigg(\mathbf{g}_{(2)} \times \mathbf{g}_{(3)} \bigg) \notag $$

Any arbitrary vector, \\( \mathbf{A} \\), can be written in terms of the original basis or the reciprocal basis. 

$$\mathbf{A}=A^i \mathbf{g}_{(i)}=A_k \mathbf{g}^{(k)} \notag$$

If I dot by \\( \mathbf{g}_{(j)} \\) on both sides, 

$$\begin{align*}
    \mathbf{A} \cdot \mathbf{g}_{(j)}= A^i \mathbf{g}_{(i)} \cdot \mathbf{g}_{(j)} &=A_k \mathbf{g}^{(k)} \cdot \mathbf{g}_{(j)} \\
    A^i g_{ij}& = A_k \delta^k_j \\
    A^i g_{ij} &= A_j
\end{align*}$$

Thus, we have derived the fact that the metric tensor has the important property that it can lower or raise indices. 

## Differential Arc Length Element

$$\begin{equation}
    \boxed{d\mathbf{y}= dx^i \dfrac{\partial \mathbf{y}}{\partial x^i}
    = dx^i \mathbf{g}_{(i)}}
    \label{differentialarclength}
\end{equation}$$

We could have also chosen to represent to the arc length element as, 

$$\boxed{d \mathbf{y} = d \bar{x}^j \dfrac{\partial \mathbf{y}}{\partial \bar{x}^j}=d \bar{x}^j \mathbf{\bar{g}}_{(j)}} \notag$$

To find the arc length,

$$\begin{align*}
    dy^2=d \mathbf{y} \cdot d \mathbf{y} &= (dx^i \mathbf{g}_{(i)}) \cdot (dx^j \mathbf{g}_{(j)})= dx^i dx^j g_{ij} \\
    &= (d \bar{x}^i \mathbf{\bar{g}}_{(i)}) \cdot (d \bar{x}^j \mathbf{\bar{g}}_{(j)}) = d\bar{x}^i d \bar{x}^j \bar{g}_{ij}
\end{align*}$$

A important identity is obtained when you dot both sides of Eq. \ref{differentialarclength} with \\( \mathbf{g}^{(j)} \\), obtaining 

$$\begin{align}
    d \mathbf{y} &= dx^i \mathbf{g}_{(i)} \notag\\
    \mathbf{g}^{(j)} \cdot d \mathbf{y} &= dx^i \mathbf{g}^{(j)} \cdot \mathbf{g}_{(i)} \notag \\
    \mathbf{g}^{(j)} \cdot d \mathbf{y} &= dx^i \delta^j_i  \notag 
\end{align}$$

$$\begin{equation}
    \boxed{dx^j = \mathbf{g}^{(j)} \cdot d \mathbf{y}} \label{diffarclengthcomp}
\end{equation}$$

## Physical Components of Vectors

$$\mathbf{A}=A^1 \mathbf{g}_{(1)} + A^2 \mathbf{g}_{(2)}+A^3 \mathbf{g}_{(3)} \notag$$

$$\mathbf{e}_{(1)}=\dfrac{\mathbf{g}_{(1)}}{\sqrt{\mathbf{g}_{(1)} \cdot \mathbf{g}_{(1)}}}=\dfrac{\mathbf{g}_{(1)}}{\sqrt{g_{11}}}, \quad \mathbf{e}_{(2)}=\dfrac{\mathbf{g}_{(2)}}{\sqrt{\mathbf{g}_{(2)} \cdot \mathbf{g}_{(2)}}}=\dfrac{\mathbf{g}_{(2)}}{\sqrt{g_{22}}}, \quad \mathbf{e}_{(3)}=\dfrac{\mathbf{g}_{(3)}}{\sqrt{\mathbf{g}_{(3)} \cdot \mathbf{g}_{(3)}}}=\dfrac{\mathbf{g}_{(3)}}{\sqrt{g_{33}}} \notag$$

### Non-orthogonal Coordinates

$$\begin{align*}
    \mathbf{A} &=  A^1 \sqrt{g_{11}} \mathbf{e}_1+A^2 \sqrt{g_{22}} \mathbf{e}_2+A^3 \sqrt{g_{33}} \mathbf{e}_3 \\ 
    &= A(1) \mathbf{e}_1 + A(2) \mathbf{e}_2 + A(3) \mathbf{e}_3
\end{align*}$$

Therefore, the physical component \\( A(i) \\) is defined by the following rule: 

$$\begin{equation}
    \boxed{A(i) = A^i \sqrt{g_{ii}}, \quad \text{(no sum on i)}}
    \label{contravariantphysicalcomponents}
\end{equation}$$

Suppose instead that \\( \mathbf{A} \\) was expressed in terms of covariant components times contravariant basis vectors,

$$\begin{align*}
    \mathbf{A} &=A_j \mathbf{g}^{(j)} \\
    &= A_j g^{ij} \mathbf{g}_{(i)} \\
    &= \sum_iA_j g^{ij} \sqrt{g_{ii}} \mathbf{e}_{(i)}
\end{align*}$$

$$\begin{equation}
    \boxed{A(i)=A_j g^{ij}\sqrt{g_{ii}}, \quad \text{(no sum on i)}}
    \label{covariantphysicalcomponents}
\end{equation}$$

### Orthogonal Coordinates
Let us define \\( h_i=\sqrt{g_{ii}} \\) for orthogonal coordinates. In the orthogonal case, \\( g^{ii}=1/g_{jj} \\) and \\( g^{ij}=0, \ i \neq j \\), so Eqs. \ref{contravariantphysicalcomponents}-\ref{covariantphysicalcomponents} simplifies to,

$$\begin{align*}
    A(i) &= A^i h_i \quad  \text{ (no sum on i)} \\
    A(i) &= \dfrac{A_i}{h_i}
\end{align*}$$

## Examples: Cylindrical and Spherical Coordinate Systems

### Cylindrical

$$(y^1,y^2,y^3) = (x,y,z) \quad     \longrightarrow \quad (x^1,x^2,x^3) = (r, \theta, z) \notag
$$

$$\begin{align*}
    y^1 &= x^1 \cos x^2 \\
    y^2 &= x^1 \sin x^2 \\ 
    y^3 &= x^3
\end{align*}$$

$$g_{ij}=
\begin{bmatrix}
    1 & 0 & 0 \\
    0 & (x^1)^2 & 0 \\
    0 & 0 & 1 \\
\end{bmatrix} \notag$$

$$h_1=1, \quad h_2=x^1, \quad h_3=1 \notag$$

### Spherical

$$(y^1,y^2,y^3) = (x,y,z) \quad     \longrightarrow \quad (x^1,x^2,x^3) = (r, \theta, \phi) \notag$$

$$\begin{align*}
    y^1 &= x^1 \sin x^2 \cos x^3   \\
    y^2 &= x^1 \sin x^2 \sin x^3 \\
    y^3 &= x^1 \cos x^2 
\end{align*}$$

$$g_{ij}=
\begin{bmatrix}
    1 & 0 & 0 \\
    0 & (x^1)^2 & 0 \\
    0 & 0 & (x^1 \sin x^2)^2 \\
\end{bmatrix} \notag$$

$$h_1 = 1, \quad h_2 = x^1, \quad h_3 = x^1 \sin x^2 \notag$$

## Christoffel Symbols and Covariant Differentiation

<p>Suppose that we have a vector field, \( \mathbf{A}=A^i \mathbf{g}_{(i)} \). To each point \( (x^1, x^2, x^3) \) in space, we imagine a vector attached to it. As usual, we can decompose the vector into components times basis vectors. Unlikely in the Cartesian case, both \( A^i \) and \( \mathbf{g}_{(i)} \) vary in space, so taking the total derivative of \( \mathbf{A} \) requires the product rule. </p>

$$\begin{equation}
    d \mathbf{A} = dA^i \mathbf{g}_{(i)} + A^i d \mathbf{g}_{(i)}
    \label{dAformula}
\end{equation}$$

Using the chain rule and Eq. \ref{diffarclengthcomp},

$$\begin{align*}
    dA^i &= \dfrac{\partial A^i}{\partial x^j} dx^j = \dfrac{\partial A^i}{\partial x^j} \mathbf{g}^{(j)} \cdot d \mathbf{y} \\
    d \mathbf{g}_{(i)} &= \dfrac{\partial \mathbf{g}_{(i)}}{\partial x^j} dx^j = \dfrac{\partial \mathbf{g}_{(i)}}{\partial x^j} \mathbf{g}^{(j)} \cdot d \mathbf{y}
\end{align*}$$

Plugging these two equations into Eq. \ref{dAformula},

$$\begin{align*}
    d \mathbf{A} &= \dfrac{\partial A^i}{\partial x^j} \bigg(\mathbf{g}^{(j)} \cdot  d \mathbf{y} \bigg) \mathbf{g}_{(i)} + A^i \dfrac{\partial \mathbf{g}_{(i)}}{\partial x^j} \bigg(\mathbf{g}^{(j)} \cdot d\mathbf{y} \bigg) \\
   d \mathbf{A} &= \left[\dfrac{\partial A^i}{\partial x^j} \mathbf{g}_{(i)} \mathbf{g}^{(j)} + A^i \dfrac{\partial \mathbf{g}_{(i)}}{\partial x^j} \mathbf{g}^{(j)}\right] \cdot d \mathbf{y} 
\end{align*}$$

The term in brackets is known as the gradient of a vector field. 

$$\begin{equation}
    \dfrac{d \mathbf{A}}{d \mathbf{y}} = \dfrac{\partial A^i}{\partial x^j} \mathbf{g}_{(i)} \mathbf{g}^{(j)} + A^i \dfrac{\partial \mathbf{g}_{(i)}}{\partial x^j} \mathbf{g}^{(j)}
    \label{gradvectorfield}
\end{equation}$$

The variation of the base vectors is captured using what's called the Christoffel symbol. For example,

$$\begin{equation}
    \boxed{\dfrac{\partial \mathbf{g}_{(i)}}{\partial x^j}= \Gamma ^k_{ij} \mathbf{g}_{(k)}}
    \label{christoffelsymboldef}
\end{equation}$$

So, Eq. \ref{gradvectorfield} is rewritten as, 

$$\dfrac{d \mathbf{A}}{d \mathbf{y}}= \dfrac{\partial A^i}{\partial x^j} \mathbf{g}_{(i)} \mathbf{g}^{(j)} + A^i \Gamma^k_{ij} \mathbf{g}_{(k)} \mathbf{g}^{(j)} \notag
$$

We can switch the dummy indices to group terms easier. I'm going to switch \\( i \to k, \ k \to i, \ j \to j \\)

$$\boxed{\dfrac{d \mathbf{A}}{d \mathbf{y}}= \left[\dfrac{\partial A^i}{\partial x^j}+ A^k \Gamma^i_{kj} \right] \mathbf{g}_{(i)} \mathbf{g}^{(j)}=A^i_{ \ /j} \mathbf{g}_{(i)} \mathbf{g}^{(j)}} \notag$$

The bracketed term is what is known as the covariant derivative of \\( A^i \\) with respect to \\( x^j \\), and is commonly denoted as \\( A^{i}_{/j} \\).

In the beginning, we assumed that the vector field \\( \mathbf{A}=A^i \mathbf{g}_{(i)} \\) was written in terms of contravariant components. What if instead it was written in terms of covariant components? For example, \\( \mathbf{A} = A_i \mathbf{g}^{(i)} \\). Following a similar procedure, 

$$\begin{equation*}
    d \mathbf{A} = dA_i \mathbf{g}^{(i)} + A_i d \mathbf{g}^{(i)}
\end{equation*}$$

$$ \left(
\begin{aligned}
    dA_i &= \dfrac{\partial A_i}{\partial x^j} \mathbf{g}^{(j)} \cdot d \mathbf{y} \\
    d \mathbf{g}^{(i)} &= \dfrac{\partial \mathbf{g}^{(i)}}{\partial x^j} \mathbf{g}^{(j)} \cdot d \mathbf{y}
\end{aligned} \right) \notag
$$

$$\begin{align}
   d \mathbf{A} &= \left[\dfrac{\partial A_i}{\partial x^j} \mathbf{g}^{(i)} \mathbf{g}^{(j)} + A_i \dfrac{\partial \mathbf{g}^{(i)}}{\partial x^j} \mathbf{g}^{(j)}\right] \cdot d \mathbf{y} 
   \label{dA=bracketdy2}
\end{align}$$

To find the spatial variation of the contravariant base vector \\( \dfrac{\partial \mathbf{g}^{(i)}}{\partial x^j} \\) in terms of the Christoffel symbol, I first need to calculate the following, 

$$\begin{align}
    \dfrac{\partial}{\partial x^j} \bigg( \mathbf{g}^{(i)} \cdot \mathbf{g}_{(k)} \bigg) &= 0 \notag\\
    \dfrac{\partial \mathbf{g}^{(i)}}{\partial x^j} \cdot \mathbf{g}_{(k)} 
    + \mathbf{g}^{(i)} \cdot \dfrac{\partial \mathbf{g}_{(k)}}{\partial x^j} &= 0 \notag \\
    P^i_{jk} + \Gamma^{i}_{jk} = 0 \notag\\
    \dfrac{\partial \mathbf{g}^{(i)}}{\partial x^j} = P^i_{jk} \mathbf{g}^{(k)} = - \Gamma^i_{jk} \mathbf{g}^{(k)}
    \label{partialgipartialxj}
\end{align}$$

Substituting Eq. \ref{partialgipartialxj} into Eq. \ref{dA=bracketdy2},

$$d \mathbf{A} = \left[ \dfrac{\partial  A_i}{\partial x^j} \mathbf{g}^{(i)} \mathbf{g}^{(j)} - A_i \Gamma^i_{jk} \mathbf{g}^{(k)} \mathbf{g}^{(j)}\right] \cdot d \mathbf{y} \notag$$

Switching indices,

$$\boxed{\dfrac{d \mathbf{A}}{d \mathbf{y}}= \left[ \dfrac{\partial A_i}{\partial x^j} - \Gamma^k_{ij} A_k\right] \mathbf{g}^{(i)}\mathbf{g}^{(j)}=A_{i/j}\mathbf{g}^{(i)}\mathbf{g}^{(j)}} \notag$$

<div class="equation-box">
  <h3><strong>Covariant Derivative</strong></h3>
  <div>
$$
\begin{aligned}
    A^i_{ \ /j} = \dfrac{\partial A^i}{\partial x^j}+ \Gamma^i_{kj} A^k \\
    A_{i/j} =\dfrac{\partial A_i}{\partial x^j} - \Gamma^k_{ij} A_k
\end{aligned}$$
  </div>
</div>

### Christoffel Symbols in Terms of Metric Tensor

Recall from Eq. \ref{christoffelsymboldef} that,

$$\dfrac{\partial \mathbf{g}_{(i)}}{\partial x^j}= \Gamma ^k_{ij} \mathbf{g}_{(k)} \notag$$

Let's dot both sides with \\( \mathbf{g}^{(l)} \\)

$$\begin{align*}
    \dfrac{\partial \mathbf{g}_{(i)}}{\partial x^j} \cdot \mathbf{g}^{(l)}= \Gamma^l_{ij}
\end{align*}$$

<p>Since \( \partial \mathbf{g}_{(i)}/\partial x^j= \partial \mathbf{g}_{(j)}/\partial x^i \), this may be written as, </p>

$$\Gamma^l_{ij}=\dfrac{1}{2} \mathbf{g}^{(l)} \cdot \dfrac{\partial \mathbf{g}_{(i)}}{\partial x^j} + \dfrac{1}{2} \mathbf{g}^{(l)} \cdot \dfrac{\partial \mathbf{g}_{(j)}}{\partial x^i} \notag$$

Adding nothing to this (the terms in parenthesis sums to 0),

$$\begin{align*}
    \Gamma^l_{ij}= &\dfrac{1}{2} \mathbf{g}^{(l)} \cdot \dfrac{\partial \mathbf{g}_{(i)}}{\partial x^j} + \left(\dfrac{1}{2} g^{kl} \dfrac{\partial \mathbf{g}_{(k)}}{\partial x^j} \cdot \mathbf{g}_{(i)} - \dfrac{1}{2}g^{kl} \dfrac{\partial \mathbf{g}_{(j)}}{\partial x^k} \cdot \mathbf{g}_{(i)} \right) \\
    &+ \dfrac{1}{2} \mathbf{g}^{(l)} \cdot \dfrac{\partial \mathbf{g}_{(j)}}{\partial x^i}+ \left(\dfrac{1}{2} g^{kl} \dfrac{\partial \mathbf{g}_{(k)}}{\partial x^i} \cdot \mathbf{g}_{(j)} - \dfrac{1}{2}g^{kl} \dfrac{\partial \mathbf{g}_{(i)}}{\partial x^k} \cdot \mathbf{g}_{(j)} \right)
\end{align*}$$

Plugging in \\( \mathbf{g}^{(l)}=g^{kl} \mathbf{g}_{(k)} \\) followed by pulling out a common factor of \\( \dfrac{1}{2} g^{kl} \\) and grouping terms by their signs,

$$\Gamma^{l}_{ij}=\dfrac{1}{2}g^{kl} \left[ \dfrac{\partial}{\partial x^j} \bigg(\mathbf{g}_{(i)}\cdot \mathbf{g}_{(k)} \bigg) + \dfrac{\partial }{\partial x^i} \bigg(\mathbf{g}_{(j)}\cdot \mathbf{g}_{(k)} \bigg) -\dfrac{\partial}{\partial x^k} \bigg(\mathbf{g}_{(i)}\cdot \mathbf{g}_{(j)} \bigg) \right] \notag$$

And finally,

$$\begin{equation}
    \boxed{\Gamma^l_{ij}= \dfrac{1}{2}g^{kl} \left[ \dfrac{\partial g_{ik}}{\partial x^j} + \dfrac{\partial g_{jk}}{\partial x^i} - \dfrac{\partial g_{ij}}{\partial x^k}\right]}
    \label{christoffelsymbolmetrictensor}
\end{equation}$$

<details class="custom-collapse" open>
  <summary><h3>Christoffel Symbol in Orthogonal, Cylindrical, and Spherical Coordinates </h3></summary>
  <div class="collapse-content">

Using Eq. \ref{christoffelsymbolmetrictensor} and the fact that in orthogonal coordinates, the off-diagonal components of the metric tensor are zero, with \( g_{ii}=h_i^2, \enspace g^{ii}=1/h_i^2 \)
<br>
<br>
<b>Case 1:</b>

$$
\begin{array}{@{\hskip 1.5cm} l @{\hskip 1.5cm} l @{\hskip 1.5cm} l}
  \Gamma^1_{11} = \dfrac{1}{h_1} \dfrac{\partial h_1}{\partial x^1} & \Gamma^1_{21} = \dfrac{1}{h_1} \dfrac{\partial h_1}{\partial x^2} & \Gamma^1_{31} = \dfrac{1}{h_1} \dfrac{\partial h_1}{\partial x^3} \\
  \Gamma^1_{12} = \dfrac{1}{h_1} \dfrac{\partial h_1}{\partial x^2} & \Gamma^2_{21} = \dfrac{1}{h_2} \dfrac{\partial h_2}{\partial x^1} & \Gamma^3_{31} = \dfrac{1}{h_3} \dfrac{\partial h_3}{\partial x^1} \\
  \Gamma^2_{12} = \dfrac{1}{h_2} \dfrac{\partial h_2}{\partial x^1} & \Gamma^2_{22} = \dfrac{1}{h_2} \dfrac{\partial h_2}{\partial x^2} & \Gamma^2_{32} = \dfrac{1}{h_2} \dfrac{\partial h_2}{\partial x^3} \\
  \Gamma^1_{13} = \dfrac{1}{h_1} \dfrac{\partial h_1}{\partial x^3} & \Gamma^2_{23} = \dfrac{1}{h_2} \dfrac{\partial h_2}{\partial x^3} & \Gamma^3_{32} = \dfrac{1}{h_3} \dfrac{\partial h_3}{\partial x^2} \\
  \Gamma^3_{13} = \dfrac{1}{h_3} \dfrac{\partial h_3}{\partial x^1} & \Gamma^3_{23} = \dfrac{1}{h_3} \dfrac{\partial h_3}{\partial x^2} & \Gamma^3_{33} = \dfrac{1}{h_3} \dfrac{\partial h_3}{\partial x^3}
\end{array} \notag
$$

<b>Case 2:</b>

$$
\begin{array}{@{\hskip 1.5cm} l @{\hskip 1.5cm} l}
  \Gamma^2_{11} = -\dfrac{h_1}{h_2^2} \dfrac{\partial h_1}{\partial x^2} & \Gamma^1_{33} = -\dfrac{h_3}{h_1^2} \dfrac{\partial h_3}{\partial x^1} \\
  \Gamma^3_{11} = -\dfrac{h_1}{h_3^2} \dfrac{\partial h_1}{\partial x^3} & \Gamma^2_{33} = -\dfrac{h_3}{h_2^2} \dfrac{\partial h_3}{\partial x^2} \\
  \Gamma^1_{22} = -\dfrac{h_2}{h_1^2} \dfrac{\partial h_2}{\partial x^1} & \Gamma^3_{22} = -\dfrac{h_2}{h_3^2} \dfrac{\partial h_2}{\partial x^3}
\end{array} \notag
$$

<b>Case 3:</b>

$$
\begin{array}{@{\hskip 1.5cm} l @{\hskip 1.5cm} l}
  \Gamma^3_{12} = 0 & \Gamma^1_{23} = 0 \\
  \Gamma^2_{13} = 0 & \Gamma^2_{31} = 0 \\
  \Gamma^3_{21} = 0 & \Gamma^1_{32} = 0
\end{array} \notag
$$

<h4> Christoffel Symbol in Cylindrical Coordinates </h4>

The only nonvanishing components of the Christoffel symbol in cylindrical coordinates are: 

$$\begin{align*}
    \Gamma^2_{21} = \Gamma^2_{12} &= \dfrac{1}{x^1} \\
    \Gamma^1_{22} &= -x^1
\end{align*}$$

<h4>Christoffel Symbol in Spherical Coordinates</h4>

The only nonvanishing components of the Christoffel symbol in spherical coordinates are: 

$$\begin{align*}
    \Gamma^2_{21} = \Gamma^2_{12} = \Gamma^3_{31} = \Gamma^3_{13} &= \dfrac{1}{x^1} \\
    \Gamma^3_{32} =\Gamma^3_{23} &= \cot x^2 \\
    \Gamma^1_{33} &= -x^1 \sin^2(x^2) \\
    \Gamma^2_{33} &= -\sin(x^2) \cos(x^2) \\
    \Gamma^1_{22} &=-x^1
\end{align*}$$

  </div>
</details>

## Gradient, Laplacian, Divergence, Curl

Suppose we have a scalar field, \\( \phi = \phi(x^1,x^2,x^3) \\).

### Gradient 

$$\begin{align*}
        d \phi &= \dfrac{\partial \phi}{\partial x^i} dx^i= \dfrac{\partial \phi}{\partial x^i} \mathbf{g}^{(i)} \cdot d \mathbf{y} \\
        \dfrac{d \phi}{d \mathbf{y}} &= \dfrac{\partial \phi}{\partial x^i} \mathbf{g}^{(i)}= \dfrac{\partial \phi}{\partial x^i} g^{ij} \mathbf{g}_{(j)}
\end{align*}$$

In more common notation, the gradient is denoted with a \\( \nabla \\) symbol, \\( \nabla \phi = d \phi / d \mathbf{y} \\).

$$\begin{align*}
    \nabla \phi^j =g^{ij} \dfrac{\partial \phi}{\partial x^i}
\end{align*}$$

We can find the physical components of this contravariant vector (see above article),

$$    \begin{align*}
        \nabla \phi (j) &= \sqrt{g_{jj}} g^{ij} \dfrac{\partial \phi}{\partial x^i}, \quad \text{(no sum on j)} \\
        \nabla \phi (j) &= \dfrac{1}{\sqrt{g_{jj}}} \dfrac{\partial \phi}{\partial x^j}=\dfrac{1}{h_j} \dfrac{\partial \phi}{\partial x^j} \quad \text{(orthogonal coordinates, no sum on j)}
    \end{align*}$$

In cylindrical coordinates, 

$$\nabla \phi = \dfrac{\partial \phi}{\partial r} \mathbf{e}_r+ \dfrac{1}{r}\dfrac{\partial \phi}{\partial \theta} \mathbf{e}_\theta+ \dfrac{\partial \phi}{\partial z} \mathbf{e}_z \notag$$

In spherical coordinates, 

$$\nabla \Phi = \dfrac{\partial \Phi}{\partial r} \mathbf{e}_r + \dfrac{1}{r} \dfrac{\partial \Phi}{\partial \theta} \mathbf{e}_\theta + \dfrac{1}{r \sin \theta} \dfrac{\partial \Phi}{\partial \phi} \mathbf{e}_\phi \notag$$

### Divergence

$$\begin{align*}
    \nabla \cdot \mathbf{A}= A^i_{/i} &= \dfrac{\partial A^i}{\partial x^i} + \Gamma^i_{ij} A^j \\
    &= \dfrac{1}{g^{1/2}} \dfrac{\partial}{\partial x^i} \left( g^{1/2} A^i \right) 
\end{align*}$$

<div class="equation-box">
  <h4><strong>Divergence in General Curvilinear Coordinates</strong></h4>
  <div>
$$\begin{equation*}
    \nabla \cdot \mathbf{A}=\sum_i \dfrac{1}{g^{1/2}} \dfrac{\partial}{\partial x^i} \left[\sqrt{\dfrac{g}{g_{ii}} } A(i)  \right]
\end{equation*}$$
  </div>
</div>

<div class="equation-box">
  <h4><strong>Divergence in Orthogonal Coordinates</strong></h4>
  <div>

$$ \nabla \cdot \mathbf{A}=\dfrac{1}{h_1 h_2 h_3} \left[\dfrac{\partial}{\partial x^1}\biggl\{h_2 h_3 A(1) \biggr\} + \dfrac{\partial}{\partial x^2}\biggl\{h_1 h_3 A(2) \biggr\} +\dfrac{\partial}{\partial x^3}\biggl\{h_1 h_2 A(3) \biggr\}  \right] \notag 
$$
  </div>
</div>

<div class="equation-box">
  <h4><strong>Divergence in Cylindrical Coordinates</strong></h4>
  <div>

$$\mathbf{A}=A_r \mathbf{e}_r + A_\theta \mathbf{e}_\theta + A_z \mathbf{e}_z \notag
$$

$$\nabla \cdot \mathbf{A}=\dfrac{1}{r} \dfrac{\partial }{\partial r} (r A_r) + \dfrac{1}{r} \dfrac{\partial A_\theta}{\partial \theta} + \dfrac{\partial A_z}{\partial z}\notag$$

  </div>
</div>

<div class="equation-box">
  <h4><strong>Divergence in Spherical Coordinates </strong></h4>
  <div>

$$\mathbf{A}=A_r \mathbf{e}_r + A_\theta \mathbf{e}_\theta + A_\phi \mathbf{e}_\phi \notag$$

$$\nabla \cdot \mathbf{A}=\dfrac{1}{r^2} \dfrac{\partial }{\partial r} (r^2 A_r) + \dfrac{1}{r \sin \theta} \dfrac{\partial}{\partial \theta} (\sin \theta A_\theta) + \dfrac{1}{r \sin \theta} \dfrac{\partial A_\phi}{\partial \phi} \notag
$$

  </div>
</div>

### Scalar Laplacian

To find the scalar Laplacian, we take the covariant derivative of the gradient with respect to \\( x^j \\). In compact notation, we write,

$$\nabla^2 \phi = g^{ij} \phi_{/ij} \notag$$

Expanding this out, we obtain, 

$$\begin{align}
    \nabla^2\phi &= \dfrac{\partial}{\partial x^j} (\nabla \phi)^j + \Gamma^j_{kj} (\nabla \phi)^k \nonumber\\
    &= \dfrac{\partial }{\partial x^j}(g^{ij}\phi_{/i}) + \Gamma^j_{kj} g^{ik} \phi_{/i}
    \label{laplacianformulaexpanded}
\end{align}$$

To put this into a more amenable form, we use the following identity, which I shall not derive, 

$$\boxed{\Gamma^i_{ij} = \dfrac{1}{2}\dfrac{\partial \ln g}{\partial x^j}=\dfrac{1}{2 g} \dfrac{\partial g}{\partial x^j}} \quad \text{where g is the determinant of the metric tensor} \notag$$

Using the above identity, I can write Eq. \ref{laplacianformulaexpanded} in the following form, 

<div class="equation-box">
  <h4><strong>Scalar Laplacian in General Curvilinear Coordinates</strong></h4>
  <div>
$$\begin{equation}
\nabla^2 \phi = \dfrac{1}{g^{1/2}} \dfrac{\partial}{\partial x^j} \left(g^{1/2} g^{ij} \dfrac{\partial \phi}{\partial x^i} \right)
\label{laplaciansimplified}
\end{equation}$$
  </div>
</div>

The laplacian formula (eq. \ref{laplaciansimplified}) takes the following form in orthogonal coordinates. To derive this, note that \\( \sqrt{g}=h_1 h_2 h_3 \\) and \\( g^{ii}=1/g_{ii}=1/h_i^2 \\) in orthogonal coordinates, 

<div class="equation-box">
  <h4><strong>Scalar Laplacian in Orthogonal Coordinates</strong></h4>
  <div>

$$\nabla^2 \phi = \dfrac{1}{h_1 h_2 h_3} \left[\dfrac{\partial}{\partial x^1} \left( \dfrac{h_2 h_3}{h_1} \dfrac{\partial \phi}{\partial x^1}\right) + \dfrac{\partial}{\partial x^2} \left(\dfrac{h_1 h_3}{h_2} \dfrac{\partial \phi}{\partial x^2} \right)  + \dfrac{\partial}{\partial x^3} \left(\dfrac{h_1 h_2 }{h_3} \dfrac{\partial \phi}{\partial x^3} \right)\right] \notag$$

  </div>
</div>

<div class="equation-box">
  <h4><strong>Scalar Laplacian in Cylindrical Coordinates</strong></h4>
  <div>

$$\nabla^2 \phi = \dfrac{1}{r} \dfrac{\partial}{\partial r} \left(r \dfrac{\partial \phi}{\partial r} \right) + \dfrac{1}{r^2} \dfrac{\partial^2 \phi}{\partial \theta^2} + \dfrac{\partial^2 \phi}{\partial z^2} \notag$$
  </div>
</div>

<div class="equation-box">
  <h4><strong>Scalar Laplacian in Spherical Coordinates</strong></h4>
  <div>

$$\nabla^2 \Phi = \dfrac{1}{r^2} \dfrac{\partial}{\partial r} \left(r^2 \dfrac{\partial \Phi}{\partial r} \right) + \dfrac{1}{r^2 \sin \theta} \dfrac{\partial}{\partial \theta} \left(\sin \theta \dfrac{\partial \Phi}{\partial \theta} \right) + \dfrac{1}{r^2 \sin^2 \theta} \dfrac{\partial^2 \Phi}{\partial \phi^2} \notag$$

  </div>
</div>

### Vector Laplacian

The vector laplacian is defined similarly to the scalar laplacian, except it operates on a vector (obviously). 

$$\begin{equation}
    L_i=[\nabla^2 \mathbf{u}]_i=g^{jk}u_{i/jk}
    \label{vectorlaplacian}
\end{equation}$$

We should first calculate \\( u_{i/jk} \\).

$$\begin{align*}
    (u_{i/j})_{/k} &= \dfrac{\partial}{\partial x^k} (u_{i/j})-\Gamma^p_{ik} u_{p/j}-\Gamma^p_{jk} u_{i/p} \\
    &=\dfrac{\partial}{\partial x^k} \left[ \dfrac{\partial u_i}{\partial x^j}-\Gamma^m_{ij} u_m \right] - \Gamma^p_{ik} \left( \dfrac{\partial u_p}{\partial x^j}-\Gamma^m_{pj} u_m \right) - \Gamma^p_{jk} \left(\dfrac{\partial u_i}{\partial x^p}-\Gamma^m_{ip} u_m \right) \\
    &= \dfrac{\partial^2 u_i}{\partial x^k \partial x^j} - \left(\Gamma^m_{ij} \dfrac{\partial u_m}{\partial x^k} + \Gamma^p_{ik} \dfrac{\partial u_p}{\partial x^j}+\Gamma^p_{jk} \dfrac{\partial u_i}{\partial x^p} \right) - \left( \dfrac{\partial \Gamma^m_{ij}}{\partial x^k} - \Gamma^p_{ik} \Gamma^m_{pj} -\Gamma^p_{jk} \Gamma^m_{ip} \right) u_m
\end{align*}$$

Let's consider orthogonal coordinates, where \\( g^{jk} \\) is only nonzero when \\( k=j \\) and \\( g^{jj}=1/h_j^2 \\). Recall also the definition of physical components of covariant vectors, \\( u_i=h_i u(i) \\)

<div class="math-container">
In such case, 

  $$\begin{align*}
      L_i = h_i L(i) = \sum_j \dfrac{1}{h_j^2} \left[\dfrac{\partial^2 u_i}{\partial x^j \partial x^j}- \left(\Gamma^m_{ij} \dfrac{\partial u_m}{\partial x^j} + \Gamma^p_{ij} \dfrac{\partial u_p}{\partial x^j} + \Gamma^p_{jj} \dfrac{\partial u_i}{\partial x^p} \right)- \left( \dfrac{\partial \Gamma^m_{ij}}{\partial x^j}-\Gamma^m_{pj} \Gamma^p_{ij}-\Gamma^m_{ip} \Gamma^p_{jj}\right) u_m\right] 
  \end{align*}$$

  Changing dummy indices, 

  $$h_i L(i) = \sum_j \dfrac{1}{h_j^2} \left[\dfrac{\partial^2 u_i}{\partial x^j \partial x^j}- 2\Gamma^m_{ij} \dfrac{\partial u_m}{\partial x^j} - \Gamma^m_{jj} \dfrac{\partial u_i}{\partial x^m} - \left( \dfrac{\partial \Gamma^m_{ij}}{\partial x^j}-\Gamma^m_{ip} \Gamma^p_{jj}-\Gamma^m_{pj} \Gamma^p_{ij}\right) u_m\right] 
  \notag$$

</div>

And finally, using physical components, 

<div class="equation-box">
  <h4><strong>Physical Components of Vector Laplacian in Orthogonal Coordinates</strong></h4>
  <div>
    $$\begin{equation} \label{physicalcomponentsvectorlap}
    \begin{aligned}
    h_i L(i) &= \sum_j \frac{1}{h_j^2} \Bigg[ 
        \frac{\partial^2 (h_i u(i))}{\partial x^j \partial x^j}
        - 2 \sum_m \Gamma^m_{ij} \frac{\partial (h_m u(m))}{\partial x^j} \\
        &\quad - \sum_m \Gamma^m_{jj} \frac{\partial (h_i u(i))}{\partial x^m}
        - \sum_m \left( \frac{\partial \Gamma^m_{ij}}{\partial x^j}
        - \sum_p \Gamma^m_{ip} \Gamma^p_{jj}
        - \sum_p \Gamma^m_{pj} \Gamma^p_{ij} \right) u(m) h_m 
    \Bigg]
    \end{aligned}
    \end{equation}$$
  </div>
</div>

To see the **expanded form** of the physical components of the vector laplacian in orthogonal coordinates, I painstakingly expanded Eq. \ref{physicalcomponentsvectorlap} by hand (which took FOREVER),

<details class="custom-collapse">
  <summary><strong>Expanding the Physical Components of Vector Laplacian in Orthogonal Coordinates </strong></summary>
  <div class="collapse-content">
  First, I sum with respect to p.
    <br>
$$\begin{align*}
    h_i L(i) &= \sum_j \frac{1}{h_j^2} \Bigg[ 
    \frac{\partial^2 (h_i u(i))}{\partial x^j \partial x^j}
    - 2 \sum_m \Gamma^m_{ij} \frac{\partial (h_m u(m))}{\partial x^j} - \sum_m \Gamma^m_{jj} \frac{\partial (h_i u(i))}{\partial x^m} \\
     & - \sum_m \left( \frac{\partial \Gamma^m_{ij}}{\partial x^j}
    -\Gamma^m_{i1} \Gamma^1_{jj}-\Gamma^m_{i2} \Gamma^2_{jj}-\Gamma^m_{i3} \Gamma^3_{jj} 
    -\Gamma^m_{1j} \Gamma^1_{ij} - \Gamma^m_{2j} \Gamma^2_{ij}-\Gamma^m_{3j} \Gamma^3_{ij}  \right) u(m) h_m 
\Bigg] 
\end{align*}$$
<br>

Then I sum with respect to m.

$$\begin{align*}
    h_i L(i) &= \sum_j \frac{1}{h_j^2} \Bigg[ 
    \frac{\partial^2 (h_i u(i))}{\partial x^j \partial x^j}
    -2\Gamma^1_{ij} \frac{\partial (h_1 u(1))}{\partial x^j} -2 \Gamma^2_{ij} \frac{\partial (h_2 u(2))}{\partial x^j} -2\Gamma^3_{ij} \frac{\partial (h_3 u(3))}{\partial x^j}   \\ & - \Gamma^1_{jj} \frac{\partial (h_i u(i))}{\partial x^1} - \Gamma^2_{jj} \frac{\partial (h_i u(i))}{\partial x^2}-\Gamma^3_{jj} \frac{\partial (h_i u(i))}{\partial x^3}  \\
     & +  \left( -\frac{\partial \Gamma^1_{ij}}{\partial x^j}
    +\Gamma^1_{i1} \Gamma^1_{jj}+\Gamma^1_{i2} \Gamma^2_{jj}+\Gamma^1_{i3} \Gamma^3_{jj} 
    +\Gamma^1_{1j} \Gamma^1_{ij} + \Gamma^1_{2j} \Gamma^2_{ij} + \Gamma^1_{3j} \Gamma^3_{ij}  \right) u(1) h_1 \\
     & +  \left( -\frac{\partial \Gamma^2_{ij}}{\partial x^j}
    +\Gamma^2_{i1} \Gamma^1_{jj}+\Gamma^2_{i2} \Gamma^2_{jj}+\Gamma^2_{i3} \Gamma^3_{jj} 
    +\Gamma^2_{1j} \Gamma^1_{ij} + \Gamma^2_{2j} \Gamma^2_{ij} + \Gamma^2_{3j} \Gamma^3_{ij}  \right) u(2) h_2  \\
     & + \left( -\frac{\partial \Gamma^3_{ij}}{\partial x^j}
    +\Gamma^3_{i1} \Gamma^1_{jj}+\Gamma^3_{i2} \Gamma^2_{jj}+\Gamma^3_{i3} \Gamma^3_{jj} 
    +\Gamma^3_{1j} \Gamma^1_{ij} + \Gamma^3_{2j} \Gamma^2_{ij} + \Gamma^3_{3j} \Gamma^3_{ij}  \right) u(3) h_3   
\Bigg] 
\end{align*}$$
<br>

Lastly, I sum with respect to j. 

$$\begin{align*}
    h_i L(i) &=  \frac{1}{h_1^2} \Bigg[ 
    \frac{\partial^2 (h_i u(i))}{\partial x^1 \partial x^1}
    -2\Gamma^1_{i1} \frac{\partial (h_1 u(1))}{\partial x^1} -2 \Gamma^2_{i1} \frac{\partial (h_2 u(2))}{\partial x^1} -2\Gamma^3_{i1} \frac{\partial (h_3 u(3))}{\partial x^1}   \\ & - \Gamma^1_{11} \frac{\partial (h_i u(i))}{\partial x^1} - \Gamma^2_{11} \frac{\partial (h_i u(i))}{\partial x^2}-\Gamma^3_{11} \frac{\partial (h_i u(i))}{\partial x^3}  \\
     & +  \left( -\frac{\partial \Gamma^1_{i1}}{\partial x^1}
    +\Gamma^1_{i1} \Gamma^1_{11}+\Gamma^1_{i2} \Gamma^2_{11}+\Gamma^1_{i3} \Gamma^3_{11} 
    +\Gamma^1_{11} \Gamma^1_{i1} + \Gamma^1_{21} \Gamma^2_{i1} + \Gamma^1_{31} \Gamma^3_{i1}  \right) u(1) h_1 \\
     & +  \left( -\frac{\partial \Gamma^2_{i1}}{\partial x^1}
    +\Gamma^2_{i1} \Gamma^1_{11}+\Gamma^2_{i2} \Gamma^2_{11}+\Gamma^2_{i3} \Gamma^3_{11} 
    +\Gamma^2_{11} \Gamma^1_{i1} + \Gamma^2_{21} \Gamma^2_{i1} + \cancel{\Gamma^2_{31} \Gamma^3_{i1}}  \right) u(2) h_2  \\
     & + \left( -\frac{\partial \Gamma^3_{i1}}{\partial x^1}
    +\Gamma^3_{i1} \Gamma^1_{11}+\Gamma^3_{i2} \Gamma^2_{11}+\Gamma^3_{i3} \Gamma^3_{11} 
    +\Gamma^3_{11} \Gamma^1_{i1} + \cancel{\Gamma^3_{21} \Gamma^2_{i1}} + \Gamma^3_{31} \Gamma^3_{i1}  \right) u(3) h_3   
\Bigg] \\ &
 + \frac{1}{h_2^2} \Bigg[ 
    \frac{\partial^2 (h_i u(i))}{\partial x^2 \partial x^2}
    -2\Gamma^1_{i2} \frac{\partial (h_1 u(1))}{\partial x^2} -2 \Gamma^2_{i2} \frac{\partial (h_2 u(2))}{\partial x^2} -2\Gamma^3_{i2} \frac{\partial (h_3 u(3))}{\partial x^2}   \\ & - \Gamma^1_{22} \frac{\partial (h_i u(i))}{\partial x^1} - \Gamma^2_{22} \frac{\partial (h_i u(i))}{\partial x^2}-\Gamma^3_{22} \frac{\partial (h_i u(i))}{\partial x^3}  \\
     & +  \left( -\frac{\partial \Gamma^1_{i2}}{\partial x^2}
    +\Gamma^1_{i1} \Gamma^1_{22}+\Gamma^1_{i2} \Gamma^2_{22}+\Gamma^1_{i3} \Gamma^3_{22} 
    +\Gamma^1_{12} \Gamma^1_{i2} + \Gamma^1_{22} \Gamma^2_{i2} + \cancel{\Gamma^1_{32} \Gamma^3_{i2}}  \right) u(1) h_1 \\
     & +  \left( -\frac{\partial \Gamma^2_{i2}}{\partial x^2}
    +\Gamma^2_{i1} \Gamma^1_{22}+\Gamma^2_{i2} \Gamma^2_{22}+\Gamma^2_{i3} \Gamma^3_{22} 
    +\Gamma^2_{12} \Gamma^1_{i2} + \Gamma^2_{22} \Gamma^2_{i2} + \Gamma^2_{32} \Gamma^3_{i2}  \right) u(2) h_2  \\
     & + \left( -\frac{\partial \Gamma^3_{i2}}{\partial x^2}
    +\Gamma^3_{i1} \Gamma^1_{22}+\Gamma^3_{i2} \Gamma^2_{22}+\Gamma^3_{i3} \Gamma^3_{22} 
    + \cancel{\Gamma^3_{12} \Gamma^1_{i2}} + \Gamma^3_{22} \Gamma^2_{i2} + \Gamma^3_{32} \Gamma^3_{i2}  \right) u(3) h_3 \Bigg] \\ & +
 \frac{1}{h_3^2} \Bigg[ 
    \frac{\partial^2 (h_i u(i))}{\partial x^3 \partial x^3}
    -2\Gamma^1_{i3} \frac{\partial (h_1 u(1))}{\partial x^3} -2 \Gamma^2_{i3} \frac{\partial (h_2 u(2))}{\partial x^3} -2\Gamma^3_{i3} \frac{\partial (h_3 u(3))}{\partial x^3}   \\ & - \Gamma^1_{33} \frac{\partial (h_i u(i))}{\partial x^1} - \Gamma^2_{33} \frac{\partial (h_i u(i))}{\partial x^2}-\Gamma^3_{33} \frac{\partial (h_i u(i))}{\partial x^3}  \\
     & +  \left( -\frac{\partial \Gamma^1_{i3}}{\partial x^3}
    +\Gamma^1_{i1} \Gamma^1_{33}+\Gamma^1_{i2} \Gamma^2_{33}+\Gamma^1_{i3} \Gamma^3_{33} 
    +\Gamma^1_{13} \Gamma^1_{i3} + \cancel{\Gamma^1_{23} \Gamma^2_{i3}} + \Gamma^1_{33} \Gamma^3_{i3}  \right) u(1) h_1 \\
     & +  \left( -\frac{\partial \Gamma^2_{i3}}{\partial x^3}
    +\Gamma^2_{i1} \Gamma^1_{33}+\Gamma^2_{i2} \Gamma^2_{33}+\Gamma^2_{i3} \Gamma^3_{33} 
    + \cancel{\Gamma^2_{13} \Gamma^1_{i3}} + \Gamma^2_{23} \Gamma^2_{i3} + \Gamma^2_{33} \Gamma^3_{i3}  \right) u(2) h_2  \\
     & + \left( -\frac{\partial \Gamma^3_{i3}}{\partial x^3}
    +\Gamma^3_{i1} \Gamma^1_{33}+\Gamma^3_{i2} \Gamma^2_{33}+\Gamma^3_{i3} \Gamma^3_{33} 
    +\Gamma^3_{13} \Gamma^1_{i3} + \Gamma^3_{23} \Gamma^2_{i3} + \Gamma^3_{33} \Gamma^3_{i3}  \right) u(3) h_3 \Bigg]
\end{align*}$$
  </div>
</details>

<div class="equation-box">
  <h4><strong>Vector Laplacian in Cylindrical Coordinates</strong></h4>
  <div>

$$\nabla^2 \mathbf{u} \cdot \mathbf{e}_{r}=L(1)= \underbrace{\dfrac{\partial^2 u_r}{\partial r^2} + \dfrac{1}{r^2} \dfrac{\partial^2 u_r}{\partial \theta^2}+ \dfrac{\partial ^2 u_r}{\partial z^2} + \dfrac{1}{r}\dfrac{\partial u_r}{\partial r}}_{\nabla^2 u_r}-\dfrac{2}{r^2}\dfrac{\partial u_\theta}{\partial \theta} - \dfrac{u_r}{r^2} \notag$$

<br>

$$\nabla^2 \mathbf{u} \cdot \mathbf{e}_\theta=L(2)= \underbrace{\dfrac{\partial^2 u_\theta}{\partial r^2} + \dfrac{1}{r^2} \dfrac{\partial^2 u_\theta}{\partial \theta^2}+ \dfrac{\partial ^2 u_\theta}{\partial z^2} + \dfrac{1}{r}\dfrac{\partial u_\theta}{\partial r}}_{\nabla^2 u_\theta}+\dfrac{2}{r^2}\dfrac{\partial u_r}{\partial \theta} - \dfrac{u_\theta}{r^2} \notag$$

<br>

$$\nabla^2 \mathbf{u} \cdot \mathbf{e}_z=L(3)= \underbrace{\dfrac{\partial^2 u_z}{\partial r^2} + \dfrac{1}{r^2} \dfrac{\partial^2 u_z}{\partial \theta^2}+ \dfrac{\partial ^2 u_z}{\partial z^2} + \dfrac{1}{r}\dfrac{\partial u_z}{\partial r}}_{\nabla^2 u_z} \notag
$$
  </div>
</div>

<div class="equation-box">
  <h4><strong> Vector Laplacian in Spherical Coordinates</strong></h4>
  <div>

$$\nabla^2 \mathbf{u} \, \cdot \, \mathbf{e}_r =L(1) = \underbrace{\dfrac{1}{r} \dfrac{\partial^2 (r u_r)}{\partial r^2} + \dfrac{1}{r^2} \dfrac{\partial^2 u_r}{\partial \theta^2} + \dfrac{1}{r^2 \sin^2\theta} \dfrac{\partial^2 u_r}{\partial \phi^2} + \dfrac{\cot \theta}{r^2} \dfrac{\partial u_r}{\partial \theta}}_{\nabla^2 u_r} - \dfrac{2}{r^2} \dfrac{\partial u_\theta}{\partial \theta} - \dfrac{2}{r^2 \sin \theta} \dfrac{\partial u_\phi}{\partial \phi}-\dfrac{2 u_r}{r^2} - \dfrac{2 \cot \theta}{r^2} u_\theta \notag$$

<br>

$$\nabla^2 \mathbf{u} \, \cdot \, \mathbf{e}_\theta =L(2) = \underbrace{\dfrac{1}{r} \dfrac{\partial^2 (r u_\theta)}{\partial r^2} + \dfrac{1}{r^2} \dfrac{\partial^2 u_\theta}{\partial \theta^2} + \dfrac{1}{r^2 \sin^2\theta} \dfrac{\partial^2 u_\theta}{\partial \phi^2} + \dfrac{\cot \theta}{r^2} \dfrac{\partial u_\theta}{\partial \theta}}_{\nabla^2 u_\theta} - \dfrac{2 \cot \theta}{r^2 \sin \theta} \dfrac{\partial u_\phi}{\partial \phi} + \dfrac{2}{r^2} \dfrac{\partial u_r}{\partial \theta} - \dfrac{ u_\theta}{r^2 \sin^2 \theta} \notag$$

<br>

$$\nabla^2 \mathbf{u} \, \cdot \, \mathbf{e}_{\phi} =L(3) = \underbrace{\dfrac{1}{r} \dfrac{\partial^2 (r u_\phi)}{\partial r^2} + \dfrac{1}{r^2} \dfrac{\partial^2 u_\phi}{\partial \theta^2} + \dfrac{1}{r^2 \sin^2\theta} \dfrac{\partial^2 u_\phi}{\partial \phi^2} + \dfrac{\cot \theta}{r^2} \dfrac{\partial u_\phi}{\partial \theta}}_{\nabla^2 u_\phi} +\dfrac{2}{r^2 \sin \theta} \dfrac{\partial u_r}{\partial \phi} +\dfrac{2 \cot \theta}{r^2 \sin \theta} \dfrac{\partial u_\theta}{\partial \phi}  - \dfrac{ u_\phi}{r^2 \sin^2 \theta} \notag$$
  </div>
</div>

### Curl

$$(\nabla \times \mathbf{A})^i =\varepsilon^{ijk} A_{k / j} \notag$$

When expanded out, this becomes,

$$\begin{align*}
    (\nabla \times \mathbf{A})^1 &= \dfrac{1}{\sqrt{g}}\left( \dfrac{\partial A_3}{\partial x^2} -\dfrac{\partial A_2}{\partial x^3}\right)  \\
    (\nabla \times \mathbf{A})^2 &= \dfrac{1}{\sqrt{g}} \left(\dfrac{\partial A_1}{\partial x^3} -\dfrac{\partial A_3}{\partial x^1} \right)\\
    (\nabla \times \mathbf{A})^3 &= \dfrac{1}{\sqrt{g}} \left( \dfrac{\partial A_2}{\partial x^1} -\dfrac{\partial A_1}{\partial x^2}\right)
\end{align*}$$

In other words, for vector \\( \mathbf{A}=A_1 \mathbf{g}^{(1)}+A_2 \mathbf{g}^{(2)}+A_3 \mathbf{g}^{(3)} \\), curl \\( \mathbf{A} \\) is calculated as,

<div class="equation-box">
  <h4><strong>Curl in General Curvilinear Coordinates</strong></h4>
  <div>
$$\nabla \times \mathbf{A}=\epsilon^{ijk} \dfrac{1}{\sqrt{g}} \dfrac{\partial A_k}{\partial x^j} \mathbf{g}_{(i)} \notag
$$

$$\nabla \times \mathbf{A} = \dfrac{1}{\sqrt{g}}\left( \dfrac{\partial A_3}{\partial x^2} -\dfrac{\partial A_2}{\partial x^3}\right)\mathbf{g}_{(1)} + \dfrac{1}{\sqrt{g}} \left(\dfrac{\partial A_1}{\partial x^3} -\dfrac{\partial A_3}{\partial x^1} \right) \mathbf{g}_{(2)} + \dfrac{1}{\sqrt{g}} \left( \dfrac{\partial A_2}{\partial x^1} -\dfrac{\partial A_1}{\partial x^2}\right) \mathbf{g}_{(3)} \notag$$

  </div>
</div>

Important: note that \\( \varepsilon^{ijk}= g^{-1/2} \epsilon^{ijk} \\)

<p>It is usual to express this result in terms of the physical components of A and using normalized basis vectors. In orthogonal coordinates, the curl of \( \mathbf{A}=A(1) \mathbf{e}_{(1)}+A(2) \mathbf{e}_{(2)}+A(3) \mathbf{e}_{(3)} \) is, </p>

<div class="equation-box">
  <h4><strong>Curl in Orthogonal Coordinates</strong></h4>
  <div>
$$\nabla \times \mathbf{A}=\sum_i \sum_j \sum_k \epsilon^{ijk} \dfrac{h_i}{h_1h_2h_3} \dfrac{\partial}{\partial x^j} \bigg[h_k A(k) \bigg] \mathbf{e}_{(i)} \notag
$$

$$\begin{align*}
    \nabla \times \mathbf{A}= &\dfrac{1}{h_2 h_3} \left[ \dfrac{\partial \big\{h_3 A(3) \big\}}{\partial x^2}  - \dfrac{\partial\big\{h_2 A(2) \big\}}{\partial x^3}  \right] \mathbf{e}_{(1)} + \dfrac{1}{h_1 h_3} \left[ \dfrac{\partial \big\{h_1 A(1) \big\}}{\partial x^3}  - \dfrac{\partial\big\{h_3 A(3) \big\}}{\partial x^1}  \right] \mathbf{e}_{(2)} \\
    &+ \dfrac{1}{h_1 h_2} \left[ \dfrac{\partial \big\{h_2 A(2) \big\}}{\partial x^1}  - \dfrac{\partial\big\{h_1 A(1) \big\}}{\partial x^2}  \right] \mathbf{e}_{(3)}
\end{align*}$$
  </div>
</div>

<div class="equation-box">
  <h4><strong>Curl in Cylindrical Coordinates</strong></h4>
  <div>
$$\begin{equation*}
    \nabla \times \mathbf{A} = \left[\dfrac{1}{r} \dfrac{\partial A_z}{\partial \theta} - \dfrac{\partial A_\theta}{\partial z} \right] \mathbf{e}_r+ \left[\dfrac{\partial A_r}{\partial z}  - \dfrac{\partial A_z}{\partial r}  \right] \mathbf{e}_\theta +\dfrac{1}{r} \left[\dfrac{\partial}{\partial r} \left( r A_\theta \right) - \dfrac{\partial A_r}{\partial \theta} \right] \mathbf{e}_z 
\end{equation*}$$
  </div>
</div>

<div class="equation-box">
  <h4><strong>Curl in Spherical Coordinates</strong></h4>
  <div>
$$\begin{align*}
    \nabla \times \mathbf{A} = & \dfrac{1}{r \sin \theta} \left[\dfrac{\partial}{\partial \theta} \left( A_\phi\sin \theta \right) - \dfrac{\partial A_\theta}{\partial \phi} \right] \mathbf{e}_r+\dfrac{1}{r} \left[ \dfrac{1}{\sin \theta}\dfrac{\partial A_r}{\partial \phi}  - \dfrac{\partial }{\partial r} \left(r A_\phi \right) \right] \mathbf{e}_\theta \\
    &+\dfrac{1}{r} \left[\dfrac{\partial}{\partial r} \left( r A_\theta \right) - \dfrac{\partial A_r}{\partial \theta} \right] \mathbf{e}_\phi 
\end{align*}$$
  </div>
</div>

## Equations of Motion in Curvilinear Coordinates

#### Acceleration

$$\begin{align}
    \mathbf{a} = \dfrac{D \mathbf{u}}{Dt} &= \dfrac{\partial \mathbf u}{\partial t} + \mathbf{u \cdot \nabla \mathbf{u}} \notag \\
    a^i &= \dfrac{\partial u^i}{\partial t}+ u^j u^i_{/j} \notag\\
    &= \dfrac{\partial u ^i}{\partial t} + u^j \left[  \dfrac{\partial u ^i}{\partial x^j} + \Gamma ^i_{jk} u^k\right] \notag\\
    a^i &= \dfrac{\partial u^i}{\partial t}+ u^j \dfrac{\partial u^i}{\partial x^j}+ \Gamma^i_{jk} u^j u^k \label{accelerationincurvilinear}
\end{align}$$

In physical components, Eq. \ref{accelerationincurvilinear} becomes,

$$\boxed{a(i) = \dfrac{\partial u(i)}{\partial t} + \dfrac{h_i}{h_j}u(j) \dfrac{\partial}{\partial x^j}{ \left[ \dfrac{u(i)}{h_i}\right] } + \dfrac{h_i}{h_j h_k} \Gamma^i_{jk} u(j) u(k)} \notag$$

For orthogonal physical components, this simplifies to 

<div class="equation-box">
  <h4><strong>Acceleration in Orthogonal Coordinates</strong></h4>
  <div>

$$a(i)= \dfrac{\partial u(i)}{\partial t}+ \sum_j \dfrac{u(j)}{h_j} \left[ \dfrac{\partial u(i)}{\partial x^j}+ \dfrac{u(i)}{h_i} \dfrac{\partial h_i}{\partial x^j} - \dfrac{u(j)}{h_i} \dfrac{\partial h_j}{\partial x^i} \right] \notag$$
  </div>
</div>

<div class="equation-box">
  <h4><strong>Acceleration in Cylindrical Coordinates </strong></h4>
  <div>
<p>For cylindrical coordinates, \( \mathbf{a}=a_r \mathbf{e}_r + a_\theta 
\mathbf{e}_\theta + a_z \mathbf{e}_z \) </p>

$$\begin{align*}
    a_r &= \dfrac{\partial u_r}{\partial t}+ u_r \dfrac{\partial u_r}{\partial r} + \dfrac{u_\theta}{r}\dfrac{\partial u_r}{\partial \theta} + u_z \dfrac{\partial u_r}{\partial z}-\dfrac{u_\theta^2}{r} \\
    a_\theta &=\dfrac{\partial u_\theta}{\partial t}+u_r \dfrac{\partial u_\theta}{\partial r} + \dfrac{u_\theta}{r} \dfrac{\partial u_\theta}{\partial \theta} + u_z \dfrac{\partial u_\theta}{\partial z} + \dfrac{u_r u_\theta}{r} \\
    a_z &= \dfrac{\partial u_z}{\partial t} + u_r \dfrac{\partial u_z}{\partial r} + \dfrac{u_\theta}{r} \dfrac{\partial u_z}{\partial \theta} + u_z\dfrac{\partial u_z}{\partial z}
\end{align*}$$
  </div>
</div>

<div class="equation-box">
  <h4><strong>Acceleration in Spherical Coordinates</strong></h4>
  <div>
<p> For spherical coordinates, \( \mathbf{a}=a_r \mathbf{e}_r + a_\theta 
\mathbf{e}_\theta + a_\phi \mathbf{e}_\phi \) </p>

$$\begin{align*}
    a_r &= \dfrac{\partial u_r}{\partial t}+ u_r \dfrac{\partial u_r}{\partial r} + \dfrac{u_\theta}{r}\dfrac{\partial u_r}{\partial \theta} + \dfrac{u_\phi}{r \sin \theta} \dfrac{\partial u_r}{\partial \phi}-\dfrac{u_\theta^2+u_\phi^2}{r}\\
    a_\theta &=\dfrac{\partial u_\theta}{\partial t}+u_r \dfrac{\partial u_\theta}{\partial r} + \dfrac{u_\theta}{r} \dfrac{\partial u_\theta}{\partial \theta} + \dfrac{u_\phi}{r \sin \theta} \dfrac{\partial u_\theta}{\partial \phi} + \dfrac{u_r u_\theta}{r}-\dfrac{u_\phi^2}{r}\cot \theta \\
    a_\phi &= \dfrac{\partial u_\phi}{\partial t} + u_r \dfrac{\partial u_\phi}{\partial r} + \dfrac{u_\theta}{r} \dfrac{\partial u_\phi}{\partial \theta} + \dfrac{u_\phi}{r \sin \theta}\dfrac{\partial u_\phi}{\partial \phi} + \dfrac{u_r u_\phi}{r} + \dfrac{u_\theta u_\phi}{r} \cot \theta 
\end{align*}$$
  </div>
</div>

#### Continuity

$$\begin{align*}
    \dfrac{\partial \rho}{\partial t} + \nabla \cdot (\rho \mathbf{u}) &= 0 \\
    \dfrac{\partial \rho}{\partial t} + (\rho u^i)_{/i} &=0 \\ 
    \dfrac{\partial \rho}{\partial t }+ \dfrac{\partial (\rho u^i)}{\partial x^i} + \Gamma^i_{ij} \rho u^j &= 0 \\
    \dfrac{\partial \rho}{\partial t} + \dfrac{\partial (\rho u^i)}{\partial x^i} + \dfrac{1}{2g}\dfrac{\partial g}{\partial x^i} \rho u^i  &= 0 \\
    \dfrac{\partial \rho}{\partial t } + \dfrac{1}{\sqrt{g}}\dfrac{\partial}{\partial x^i} \bigg[ \sqrt{g} \ \rho u^i \bigg] &= 0
\end{align*}$$

<div class="equation-box">
  <h4><strong> Continuity Equation in Orthogonal Coordinates</strong></h4>
  <div>
$$\dfrac{\partial \rho}{\partial t} + \sum_i \dfrac{1}{h_1 h_2 h_3} \dfrac{\partial}{\partial x^i} \left[\dfrac{h_1 h_2 h_3}{h_i} \rho u(i) \right]=0
\notag$$
  </div>
</div>

<div class="equation-box">
  <h4><strong>Continuity Equation in Cylindrical Coordinates</strong></h4>
  <div>

$$\dfrac{\partial \rho}{\partial t} + \dfrac{1}{r} \dfrac{\partial}{\partial r}(r \rho u_r) + \dfrac{1}{r}\dfrac{\partial}{\partial \theta}(\rho u_\theta) + \dfrac{\partial}{\partial z}(\rho u_z)=0 \notag$$
  </div>
</div>

<div class="equation-box">
  <h4><strong>Continuity Equation in Spherical Coordinates</strong></h4>
  <div>

$$\dfrac{\partial \rho}{\partial t} + \dfrac{1}{r^2} \dfrac{\partial}{\partial r} \left(r^2 \rho u_r \right) + \dfrac{1}{r \sin \theta} \dfrac{\partial}{\partial \theta} (\sin \theta \ \rho u_\theta) + \dfrac{1}{r \sin \theta} \dfrac{\partial}{\partial \phi} (\rho u_\phi)=0 \notag$$

  </div>
</div>

#### Momentum Equation 

$$\rho \mathbf{a} = \rho \mathbf{f} - \nabla p + (\lambda + \mu) \nabla (\nabla \cdot \mathbf{u} ) + \mu \nabla^2 \mathbf{u} \notag$$

To make things simpler on me, let's just focus on the incompressible case. The above formula then reduces to, 

$$\begin{equation*}
    \boxed{\dfrac{\partial \mathbf{u}}{\partial t} + \mathbf{u} \cdot \nabla \mathbf{u} = \mathbf{f}-\dfrac{\nabla p}{\rho} + \nu \nabla^2 \mathbf{u}}
\end{equation*}$$

<div class="equation-box">
  <h3><strong>Incompressible Navier-Stokes Equation in Cylindrical Polar Coordinates</strong></h3>
  <div>
In cylindrical coordinates (with \( \mathbf{f}=0 \)),

$$\begin{align*}
    \dfrac{\partial u_r}{\partial t} &+ u_r \dfrac{\partial u_r}{\partial r} + \dfrac{u_\theta}{r}\dfrac{\partial u_r}{\partial \theta} + u_z \dfrac{\partial u_r}{\partial z}-\dfrac{u_\theta^2}{r} = -\dfrac{1}{\rho} \dfrac{\partial p}{\partial r} \\
    &+ \nu \bigg[\dfrac{\partial^2 u_r}{\partial r^2} + \dfrac{1}{r^2} \dfrac{\partial^2 u_r}{\partial \theta^2}+ \dfrac{\partial ^2 u_r}{\partial z^2} + \dfrac{1}{r}\dfrac{\partial u_r}{\partial r}-\dfrac{2}{r^2}\dfrac{\partial u_\theta}{\partial \theta} - \dfrac{u_r}{r^2}\bigg]
\end{align*}$$
<br>
$$\begin{align*}
    \dfrac{\partial u_\theta}{\partial t} &+u_r \dfrac{\partial u_\theta}{\partial r} + \dfrac{u_\theta}{r} \dfrac{\partial u_\theta}{\partial \theta} + u_z \dfrac{\partial u_\theta}{\partial z} + \dfrac{u_r u_\theta}{r} = -\dfrac{1}{\rho r} \dfrac{\partial p}{\partial \theta} \\ 
    &+ \nu \bigg[\dfrac{\partial^2 u_\theta}{\partial r^2} + \dfrac{1}{r^2} \dfrac{\partial^2 u_\theta}{\partial \theta^2}+ \dfrac{\partial ^2 u_\theta}{\partial z^2} + \dfrac{1}{r}\dfrac{\partial u_\theta}{\partial r}+\dfrac{2}{r^2}\dfrac{\partial u_r}{\partial \theta} - \dfrac{u_\theta}{r^2} \bigg]
\end{align*}$$
<br>
$$\begin{align*}
    \dfrac{\partial u_z}{\partial t} &+ u_r \dfrac{\partial u_z}{\partial r} + \dfrac{u_\theta}{r} \dfrac{\partial u_z}{\partial \theta} + u_z\dfrac{\partial u_z}{\partial z} = - \dfrac{1}{\rho} \dfrac{\partial p}{\partial z}  \\
    &+ \nu \bigg[\dfrac{\partial^2 u_z}{\partial r^2} + \dfrac{1}{r^2} \dfrac{\partial^2 u_z}{\partial \theta^2}+ \dfrac{\partial ^2 u_z}{\partial z^2} + \dfrac{1}{r}\dfrac{\partial u_z}{\partial r} \bigg]
\end{align*}$$
  </div>
</div>

<div class="equation-box">
  <h3><strong>Incompressible Navier-Stokes Equation in Spherical Polar Coordinates</strong></h3>
  <div>
In spherical coordinates (with \( \mathbf{f}=0 \)),

$$\begin{align*}
    \dfrac{\partial u_r}{\partial t} &+ u_r \dfrac{\partial u_r}{\partial r} + \dfrac{u_\theta}{r}\dfrac{\partial u_r}{\partial \theta} + \dfrac{u_\phi}{r \sin \theta} \dfrac{\partial u_r}{\partial \phi}-\dfrac{u_\theta^2+u_\phi^2}{r} = - \dfrac{1}{\rho} \dfrac{\partial p}{\partial r} \\
    &+ \nu \bigg[\dfrac{1}{r} \dfrac{\partial^2 (r u_r)}{\partial r^2} + \dfrac{1}{r^2} \dfrac{\partial^2 u_r}{\partial \theta^2} + \dfrac{1}{r^2 \sin^2\theta} \dfrac{\partial^2 u_r}{\partial \phi^2} + \dfrac{\cot \theta}{r^2} \dfrac{\partial u_r}{\partial \theta} \\
    & - \dfrac{2}{r^2} \dfrac{\partial u_\theta}{\partial \theta} - \dfrac{2}{r^2 \sin \theta} \dfrac{\partial u_\phi}{\partial \phi}-\dfrac{2 u_r}{r^2} - \dfrac{2 \cot \theta}{r^2} u_\theta \bigg]
\end{align*}$$
<br>
$$\begin{align*}
    \dfrac{\partial u_\theta}{\partial t} &+u_r \dfrac{\partial u_\theta}{\partial r} + \dfrac{u_\theta}{r} \dfrac{\partial u_\theta}{\partial \theta} + \dfrac{u_\phi}{r \sin \theta} \dfrac{\partial u_\theta}{\partial \phi} + \dfrac{u_r u_\theta}{r}-\dfrac{u_\phi^2}{r}\cot \theta = -\dfrac{1}{\rho r} \dfrac{\partial p}{\partial \theta} \\
    &+ \nu \bigg[\dfrac{1}{r} \dfrac{\partial^2 (r u_\theta)}{\partial r^2} + \dfrac{1}{r^2} \dfrac{\partial^2 u_\theta}{\partial \theta^2} + \dfrac{1}{r^2 \sin^2\theta} \dfrac{\partial^2 u_\theta}{\partial \phi^2} + \dfrac{\cot \theta}{r^2} \dfrac{\partial u_\theta}{\partial \theta} \\
    &- \dfrac{2 \cot \theta}{r^2 \sin \theta} \dfrac{\partial u_\phi}{\partial \phi} + \dfrac{2}{r^2} \dfrac{\partial u_r}{\partial \theta} - \dfrac{ u_\theta}{r^2 \sin^2 \theta} \bigg]
\end{align*}$$
<br>
$$\begin{align*}
    \dfrac{\partial u_\phi}{\partial t} &+ u_r \dfrac{\partial u_\phi}{\partial r} + \dfrac{u_\theta}{r} \dfrac{\partial u_\phi}{\partial \theta} + \dfrac{u_\phi}{r \sin \theta}\dfrac{\partial u_\phi}{\partial \phi} + \dfrac{u_r u_\phi}{r} + \dfrac{u_\theta u_\phi}{r} \cot \theta = -\dfrac{1}{\rho r \sin \theta} \dfrac{\partial p}{\partial \phi} \\
    &+ \nu \bigg[\dfrac{1}{r} \dfrac{\partial^2 (r u_\phi)}{\partial r^2} + \dfrac{1}{r^2} \dfrac{\partial^2 u_\phi}{\partial \theta^2} + \dfrac{1}{r^2 \sin^2\theta} \dfrac{\partial^2 u_\phi}{\partial \phi^2} + \dfrac{\cot \theta}{r^2} \dfrac{\partial u_\phi}{\partial \theta} \\
    &+\dfrac{2}{r^2 \sin \theta} \dfrac{\partial u_r}{\partial \phi} +\dfrac{2 \cot \theta}{r^2 \sin \theta} \dfrac{\partial u_\theta}{\partial \phi}  - \dfrac{ u_\phi}{r^2 \sin^2 \theta}\bigg]
\end{align*}$$
  </div>
</div>

## References

1. Rebecca M. Brannon, *Curvilinear Analysis in a Euclidean Space*, June 2004.  
2. Rutherford Aris, *Vectors, Tensors, and the Basic Equations of Fluid Mechanics*, Dover Publications, 1989.  
3. J. H. Heinbockel, *Introduction to Tensor Calculus and Continuum Mechanics*, 1996.  




