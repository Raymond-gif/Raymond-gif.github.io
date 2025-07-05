---
layout: single
title: "Formula Sheet"
permalink: /formula/
author_profile: true
---

{% include base_path %}

## Integral Equations of Motion 

### Conservation of Mass 

$$ 
\frac{D}{Dt}\int\limits_{\text{CM}} \rho \, dV = \frac{\partial}{\partial t}
\int\limits_{\text{CV}} \rho \, dV 
+ \int\limits_{\text{CS}} \rho (\mathbf{u} \cdot \mathbf{n}) \, dS = 0 \notag
$$

### Momentum Equation

$$
\frac{D}{Dt} \int\limits_{\text{CM}}{\rho \mathbf{u} \, dV}= \frac{\partial}{\partial t}
\int\limits_{\text{CV}} { \rho \mathbf{u}} \, dV 
+ \int\limits_{\text{CS}} \rho \mathbf{u} (\mathbf{u} \cdot \mathbf{n}) \, dS 
= - \int\limits_{\text{CS}} p  \mathbf{n}\, dS + \int\limits_{\text{CS}} \boldsymbol{\underline{\underline{\tau}}} \cdot \mathbf{n} \, dS \notag
$$

### Conservation of Energy

$$
\frac{D}{Dt}\int\limits_{\text{CM}} \rho e_0 \, dV
= \frac{\partial}{\partial t}\int\limits_{\text{CV}} \rho e_0 \, dV 
+ \int\limits_{\text{CS}} \rho e_0 (\mathbf{u} \cdot \mathbf{n}) \, dS
= - \int\limits_{ \text{CS}} p (\mathbf{u} \cdot \mathbf{n}) \, dS 
+ \int\limits_{\text{CS}} \boldsymbol{\underline{\underline{\tau}}} \cdot \mathbf{n} \cdot \mathbf{u} \, dS 
+ \int\limits_{\text{CV}} \nabla \cdot \mathbf{q} \, dV \notag
$$

## Differential Equations of Motion 

### Conservation of Mass

$$
\frac{\partial \rho}{\partial t} + \nabla \cdot (\rho {\mathbf{u}}) = 0, \quad
\frac{D \rho}{D t} = -\rho \, \nabla \cdot {\mathbf{u}} \notag
$$

### Momentum Equation

$$
\frac{\partial (\rho {\mathbf{u}})}{\partial t} + \nabla \cdot \left( \rho {\mathbf{u}} {\mathbf{u}} \right) = -\nabla p + \nabla \cdot \underline{\underline{\boldsymbol{\tau}}}, \quad \rho\frac{D\mathbf{u}}{Dt}=-\nabla p +\nabla \cdot \boldsymbol{\underline{\underline{\tau}}} \notag
$$ 

### Conservation of Energy

$$
\frac{\partial}{\partial t}(\rho e_0) + \nabla \cdot(\rho e_0 {\mathbf{u}}) = \nabla \cdot(\underline{\underline{\boldsymbol{\sigma}}} \cdot \mathbf{u}) - \nabla \cdot \mathbf{q}, \quad
\rho \frac{D e_0}{D t} = \nabla \cdot (\boldsymbol{\underline{\underline{\tau}}} \cdot \mathbf{u}) - \nabla \cdot (p \mathbf{u}) - \nabla \cdot \mathbf{q}
\notag
$$

$$
\rho \frac{Dh_0}{Dt} = 
\nabla \cdot (\underline{\underline{\boldsymbol{\tau}}} \cdot {\boldsymbol{u}}) - 
\nabla \cdot \boldsymbol{q} + \frac{\partial p}{\partial t}, \quad
\rho \frac{D h}{Dt} = \frac{D p}{Dt} + \boldsymbol{\underline{\underline{\tau}}} : \nabla \boldsymbol{u} - \nabla \cdot \boldsymbol{q}
\notag
$$

$$
\rho T \frac{Ds}{Dt} = \boldsymbol{\underline{\underline{\tau}}} : \nabla \boldsymbol{u}-\nabla \cdot \mathbf{q}
\notag
$$

## Thermodynamics

### 1st Law of Thermodynamics

$$
de=\delta w + \delta q \notag
$$
 
### Fundamental Thermodynamic Relations (Gibbs Equation) 

$$
h=e+pv, \quad de= Tds - pdv ,\quad dh=Tds + v dp \notag
$$

### Second Law of Thermodynamics

$$
ds=\frac{\delta q_{\text{rev}}}{T} \notag
$$

### Specific Heat Ratio Definition 

$$
c_v=\left[\frac{\partial e}{\partial T}\right]_v, \quad c_p =\left[\frac{\partial h}{\partial T}\right]_p \notag
$$


