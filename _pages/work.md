---
title: "Method of Characteristics"
permalink: /work/
layout: single
author_profile: false
---

## Oblique Shock Theory 

To find the equations of motion for flow across an oblique shock, we construct a fixed control volume around the shock and apply the conservation equations. We then decompose the velocity vectors into tangential and normal components with respect to the oblique shock. 

<figure style="width: 40%; max-width: 500px; margin: 0 auto; text-align: center;">
  <img src="/images/obliqueshock.png" alt="Oblique Shock" style="width: 100%; height: auto;">
  <figcaption style="margin-top: 0.5em;">
   Geometric Diagram of Oblique Shock
  </figcaption>
</figure>

<div style="background-color: #e6f0ff; border: 2px solid #2a4d8f; padding: 1em; border-radius: 8px; max-width: 700px; margin: 1em auto;">
  <h3 style="color: #2a4d8f; margin-top: 0;">Governing Equations</h3>
  <p>
  $$ 
  \begin{aligned}
  \text{Continuity: } \quad \rho_1 u_1 &= \rho_2 u_2  \\  
  \text{Momentum: } \quad p_1+ \rho_1u_1^2 &=p_2+\rho_2 u_2^2, \quad w_1=w_2 \\
  \text{Energy: } \quad  h_1 + \dfrac{u_1^2}{2} &=h_2+\dfrac{u_2^2}{2} \\
  \text{Geometry (see fig.): } \quad u_1 &= V_1 \sin(\beta) , \quad u_2=V_2 \sin(\beta-\theta) \\  
  w_1&=V_1 \cos (\beta), \quad w_2 = V_2 \cos(\beta - \theta)
  \end{aligned}
  $$
  </p>
</div>

