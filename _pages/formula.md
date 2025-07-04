---
permalink: /formula
title: "Formula Sheet"
author_profile: true

---

## Integral Equations of Motion 

$$ 
\frac{D}{Dt}\int\limits_{\text{CM}} \rho \, dV = \frac{\partial}{\partial t}
\int\limits_{\text{CV}} \rho \, dV 
+ \int\limits_{\text{CS}} \rho (\mathbf{u} \cdot \mathbf{n}) \, dS = 0 \notag
$$

$$
\frac{D}{Dt} \int\limits_{\text{CM}}{\rho \mathbf{u} \, dV}= \frac{\partial}{\partial t}
\int\limits_{\text{CV}} { \rho \mathbf{u}} \, dV 
+ \int\limits_{\text{CS}} \rho \mathbf{u} (\mathbf{u} \cdot \mathbf{n}) \, dS 
= - \int\limits_{\text{CS}} p  \mathbf{n}\, dS + \int\limits_{\text{CS}} \boldsymbol{\underline{\underline{\tau}}} \cdot \mathbf{n} \, dS \notag
$$

$$
\frac{D}{Dt}\int\limits_{\text{CM}} \rho e_0 \, dV
= \frac{\partial}{\partial t}\int\limits_{\text{CV}} \rho e_0 \, dV 
+ \int\limits_{\text{CS}} \rho e_0 (\mathbf{u} \cdot \mathbf{n}) \, dS
= - \int\limits_{ \text{CS}} p (\mathbf{u} \cdot \mathbf{n}) \, dS 
+ \int\limits_{\text{CS}} \boldsymbol{\underline{\underline{\tau}}} \cdot \mathbf{n} \cdot \mathbf{u} \, dS 
+ \int\limits_{\text{CV}} \nabla \cdot \mathbf{q} \, dV \notag
$$