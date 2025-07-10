---
title: "Method of Characteristics"
permalink: /work/
layout: single
author_profile: false
---

## Oblique Shock Theory 

To find the equations of motion for flow across an oblique shock, we construct a fixed control volume around the shock and apply the conservation equations. We then decompose the velocity vectors into tangential and normal components with respect to the oblique shock. 

<figure id="fig-obliqueshock" style="width: 40%; max-width: 500px; margin: 0 auto; text-align: center; display: block;">
  <img src="/images/obliqueshock.png" alt="Oblique Shock" style="width: 100%; height: auto;">
  <figcaption style="margin-top: 0.5em;">
    <strong>Figure 1:</strong> Geometric Diagram of Oblique Shock
  </figcaption>
</figure>

<div style="background-color: #e6f0ff; border: 2px solid #2a4d8f; padding: 1em; border-radius: 8px; max-width: 700px; margin: 1em auto; overflow-x: auto; word-wrap: break-word;">
  <h3 style="color: #2a4d8f; margin-top: 0;">Governing Equations</h3>
  <p>
  $$ 
  \begin{align*}
      \text{Continuity: } \quad \rho_1 u_1 &= \rho_2 u_2  \label{continuity} \\  
      \text{Momentum: } \quad p_1+ \rho_1u_1^2 &=p_2+\rho_2 u_2^2, \quad w_1=w_2 \label{momentum}\\
      \text{Energy: } \quad  h_1 + \dfrac{u_1^2}{2} &=h_2+\dfrac{u_2^2}{2} \label{energy}\\
      \text{Geometry (see fig. 1): } \quad u_1 &= V_1 \sin(\beta) , \quad u_2=V_2 \sin(\beta-\theta) \label{geometry}\\  w_1&=V_1 \cos (\beta), \quad w_2 = V_2 \cos(\beta - \theta) \notag
  \end{align*}
  $$
  </p>
</div>

Do these equations look familiar? Yes! They are exactly the governing equations for the normal shock, except \\(u_1, u_2 \\) stands for the normal component of the velocity with respect to the oblique shock. 

Therefore, we can apply the normal shock relations, making sure to use the normal component of the velocity. It is then useful to define the normal Mach number. 

$$
M_{n1}=\dfrac{u_1}{a_1}=\dfrac{V_1 \sin \beta}{a_1}=M_1 \sin \beta \notag
$$

By using \\(M_{n1}\\) in place of \\(M_1\\) in the normal shock relations, we get, 

$$
\begin{align}
    \dfrac{T_2}{T_1}&=\left[\dfrac{2+(\gamma-1)M_{n1}^2}{(\gamma+1)M_{n1}^2}\right] \left[1+\dfrac{2\gamma}{\gamma+1}(M_{n1}^2-1) \right] \label{temperatureratio} \\ \dfrac{\rho_2}{\rho_1}&=\dfrac{(\gamma+1)M_{n1}^2}{2+(\gamma-1)M_{n1}^2} \label{densityratio} \\  \dfrac{p_2}{p_1}&=1+\dfrac{2\gamma}{\gamma+1}\left(M_{n1}^2-1 \right) \label{pressureratio}
\end{align}
$$

Manipulating Eqs. \ref{continuity} and \ref{geometry}, 

$$
\dfrac{\rho_2}{\rho_1}=\dfrac{u_1}{u_2}=\dfrac{V_1}{V_2} \dfrac{ \sin \beta}{\sin (\beta - \theta)}= \dfrac{\cos(\beta - \theta)}{\cos \beta} \dfrac{\sin \beta}{\sin (\beta -\theta)}=\dfrac{\tan \beta}{\tan (\beta - \theta)} 
$$

Plugging in Eq. \ref{densityratio}, I obtain, 

<div style="background-color: #ebf4ff; border: 2px solid #2c5282; padding: 12px; border-radius: 6px; max-width: 600px; margin: 1em auto;">
  <strong>Theta-Beta-M Relation: </strong>
  
  <p style="text-align: center; font-size: 1.1em; margin-top: 0.5em;">

  $$\dfrac{\tan \beta}{\tan (\beta - \theta)} = \dfrac{(\gamma+1)M_1^2 \sin^2\beta}{2+(\gamma-1)M_1^2 \sin^2\beta}
  \label{tantan sinsin} $$

  </p>
</div>

This equation is also presented equivalently in various forms in textbooks. For example, 

$$
\boxed{\tan \theta=\dfrac{2 (\cot \beta) (M_1^2 \sin^2 \beta -1)}{2+M_1^2 (\gamma + \cos 2\beta)}} \label{theta beta M}
$$

$$
\boxed{M_1^2 \sin^2 \beta -1 = \dfrac{\gamma+1}{2} M_1^2 \dfrac{\sin \beta \sin \theta}{\cos(\beta-\theta)}} \label{m1squared-1}
$$

<details>
  <summary><strong>Show Derivation for Eqs. \ref{theta beta M} and \ref{m1squared-1}</strong></summary>
  <br>

Let's define a shorthand notation, \( \{\sin \beta, \enspace \cos \beta, \enspace \tan \beta, \enspace \sin \theta, \enspace \cos \theta, \enspace \tan \theta, \enspace \cos 2 \beta\} \equiv \{s_\beta, \enspace c_\beta, \enspace t_\beta, \enspace s_\theta, \enspace c_\theta, \enspace t_\theta, \enspace c_{2\beta}\} \)

$$
\begin{align*}
  \dfrac{(\gamma+1) M_1^2 s_\beta^2}{2+ (\gamma -1 ) M_1^2 s_\beta^2 } &=\dfrac{t_\beta}{t_{\beta - \theta
  }} \\
  (\gamma+1) M_1^2 s_\beta^2 t_{\beta - \theta} &= 2 t_\beta + (\gamma-1)M_1^2 s_\beta^2 t_\beta \\
  (\gamma +1) M_1^2 s_\beta^2 (t_\beta - t_\theta) &=(1 + t_\beta t_\theta)[2 t_\beta + (\gamma -1) M_1^2 s_\beta^2 t_\beta]
\end{align*}
$$

Expand this out and divide by \( s_\beta^2 \), 

$$
\gamma M_1^2 t_\beta - \gamma M_1^2 t_\theta + M_1^2 t_\beta -M_1^2t_\theta = \dfrac{2 t_\beta}{s_\beta^2}+ \gamma M_1^2 t_\beta - M_1^2 t_\beta + 2 \dfrac{t_\beta ^2}{s_\beta^2}t_\theta + \gamma M_1^2 t_\beta^2 t_\theta - M_1^2 t_\beta^2 t_\theta \notag
$$

After some cancellation and moving all terms to one side, 

$$
\dfrac{2 c_\beta}{s_\beta}-M_1^2 s_\beta c_\beta+2t_\theta + \underbrace{\gamma M_1^2  t_\theta s_\beta ^2 + \gamma M_1^2 t_\theta c_\beta^2}_{\gamma M_1^2 t_\theta} + \underbrace{M_1^2 t_\theta c_\beta^2 -M_1^2 t_\theta s_\beta^2 }_{M_1^2 t_\theta c_{2 \beta}}-M_1^2 s_\beta c_\beta =0 \notag
$$

$$
\begin{align*}
\dfrac{2 c_\beta}{s_\beta t_\theta}-\dfrac{M_1^2 s_\beta c_\beta}{t_\theta}+2+\gamma M_1^2 +M_1^2 c_{2 \beta} -M_1^2 \dfrac{s_\beta c_\beta}{t_\theta} &=0 \\
\dfrac{M_1^2 s_\beta^2 c_\beta +M_1^2 s_\beta^2 c_\beta - 2 c_\beta}{s_\beta t_\theta} &=2+M_1^2 (\gamma + c_{2\beta}) \\
\dfrac{2 c_\beta (M_1^2 s_\beta^2 -1)}{s_\beta t_\theta} &=2 + M_1^2 (\gamma + c_{2\beta})
\end{align*}
$$

$$
\begin{equation}
t_\theta = \dfrac{2 \cot \beta (M_1^2 s_\beta^2 -1)}{2 + M_1^2 (\gamma + c_{2\beta})} \rightarrow \boxed{\tan \theta=\dfrac{2 (\cot \beta) (M_1^2 \sin^2 \beta -1)}{2+M_1^2 (\gamma + \cos 2\beta)}} 
\end{equation}
$$

Starting from Eq. \ref{tantan sinsin} and using the same shorthand notation that I used above, 

$$
\begin{align}
    (\gamma + 1) M_1^2 s_\beta^2 (s_\beta c_\theta - c_\beta s_\theta) &= t_\beta c_{\beta - \theta} [2 + (\gamma+1)M_1^2 s_\beta^2 - 2M_1^2 s_\beta^2] \nonumber \\
    (\gamma+1) M_1^2 s_\beta ^2 [s_\beta c_\theta - c_\beta s_\theta] + 2t_\beta c_{\beta -\theta} M_1^2 s_\beta^2 &=t_\beta c_{\beta-\theta} [2+ (\gamma+1)M_1^2 s_\beta^2] \nonumber \\
    (\gamma +1) M_1^2 s_\beta^2 [ s_\beta c_\theta - c_\beta s_\theta - t_\beta c_{\beta -\theta}]+2 t_\beta c_{\beta - \theta} M_1^2 s_\beta^2 &=2t_\beta c_{\beta-\theta} \nonumber \\
    (\gamma +1)M_1^2 s_\beta^2 [s_\beta c_\theta - c_\beta s_\theta - t_\beta c_{\beta - \theta}] &=2t_\beta c_{\beta - \theta}(1-M_1^2 s_\beta^2) \nonumber \\
    \dfrac{\gamma+1}{2} \dfrac{M_1^2}{c_{\beta -\theta}} s_\beta c_\beta (s_\beta c_\theta - c_\beta s_\theta - t_\beta c_{\beta-\theta}) &=1-M_1^2 s_\beta^2 \nonumber \\
    \dfrac{\gamma +1}{2} \dfrac{M_1^2}{c_{\beta-\theta}}(-s_\beta s_\theta)&=1-M_1^2 s_\beta^2 \nonumber 
\end{align}
$$

$$
\boxed{M_1^2 \sin^2 \beta -1 = \dfrac{\gamma+1}{2} M_1^2 \dfrac{\sin \beta \sin \theta}{\cos(\beta-\theta)}}
$$

</details>



