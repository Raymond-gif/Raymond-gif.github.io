---
permalink: /formula
title: "Formula Sheet"
author_profile: true

---

## Integral Equations of Motion 

$$ 
\text{Mass: }\frac{D}{Dt}\int\limits_{\text{CM}} \rho \, dV = \frac{\partial}{\partial t}
\int\limits_{\text{CV}} \rho \, dV 
+ \int\limits_{\text{CS}} \rho (\mathbf{u} \cdot \mathbf{n}) \, dS = 0 \notag
$$

$$
\text{Momentum: }\frac{D}{Dt} \int\limits_{\text{CM}}{\rho \mathbf{u} \, dV}= \frac{\partial}{\partial t}
\int\limits_{\text{CV}} { \rho \mathbf{u}} \, dV 
+ \int\limits_{\text{CS}} \rho \mathbf{u} (\mathbf{u} \cdot \mathbf{n}) \, dS 
= - \int\limits_{\text{CS}} p  \mathbf{n}\, dS + \int\limits_{\text{CS}} \boldsymbol{\underline{\underline{\tau}}} \cdot \mathbf{n} \, dS \notag
$$

$$
\text{Energy: }\frac{D}{Dt}\int\limits_{\text{CM}} \rho e_0 \, dV
= \frac{\partial}{\partial t}\int\limits_{\text{CV}} \rho e_0 \, dV 
+ \int\limits_{\text{CS}} \rho e_0 (\mathbf{u} \cdot \mathbf{n}) \, dS
= - \int\limits_{ \text{CS}} p (\mathbf{u} \cdot \mathbf{n}) \, dS 
+ \int\limits_{\text{CS}} \boldsymbol{\underline{\underline{\tau}}} \cdot \mathbf{n} \cdot \mathbf{u} \, dS 
+ \int\limits_{\text{CV}} \nabla \cdot \mathbf{q} \, dV \notag
$$

## Differential Equations of Motion 

$$
\text{Mass: }
\frac{\partial \rho}{\partial t} + \nabla \cdot (\rho {\mathbf{u}}) = 0, \quad
\frac{D \rho}{D t} = -\rho \, \nabla \cdot {\mathbf{u}} \notag
$$

$$
\text{Momentum: }
\frac{\partial (\rho {\mathbf{u}})}{\partial t} + \nabla \cdot \left( \rho {\mathbf{u}} {\mathbf{u}} \right) = -\nabla p + \nabla \cdot \underline{\underline{\boldsymbol{\tau}}}, \quad \rho\frac{D\mathbf{u}}{Dt}=-\nabla p +\nabla \cdot \boldsymbol{\underline{\underline{\tau}}} \notag
$$ 