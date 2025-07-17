---
title: "Method of Characteristics"
excerpt: "Developed oblique shock relations, derived Prandtl–Meyer wave behavior in the weak-shock limit, and implemented a numerical Method of Characteristics for 2D compressible flow."
collection: portfolio
author_profile: false
layout: single
---

## Oblique Shock Theory 

To find the equations of motion for flow across an oblique shock, we construct a fixed control volume around the shock and apply the conservation equations. We then decompose the velocity vectors into tangential and normal components with respect to the oblique shock. 

<figure id="fig-obliqueshock" style="width: 40%; max-width: 500px; margin: 0 auto; text-align: center; display: block;">
  <img src="/images/obliqueshock.png" alt="Oblique Shock" style="width: 100%; height: auto;">
  <figcaption style="margin-top: 0.5em;">
    <strong>Figure 1:</strong> Geometric Diagram of Oblique Shock
  </figcaption>
</figure>

<div class="equation-box">
  <h3>Governing Equations</h3>
  <div>
  $$ 
  \begin{align}
      \text{Continuity: } \quad \rho_1 u_1 &= \rho_2 u_2  \label{continuity} \\  
      \text{Momentum: } \quad p_1+ \rho_1u_1^2 &=p_2+\rho_2 u_2^2, \quad w_1=w_2 \label{momentum}\\
      \text{Energy: } \quad  h_1 + \dfrac{u_1^2}{2} &=h_2+\dfrac{u_2^2}{2} \label{energy}\\
      \text{Geometry (see fig. 1): } \quad u_1 &= V_1 \sin(\beta) , \quad u_2=V_2 \sin(\beta-\theta) \label{geometry}\\  w_1&=V_1 \cos (\beta), \quad w_2 = V_2 \cos(\beta - \theta) \notag
  \end{align}
  $$
  </div>
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

<div class= "equation-box">
  <h3><strong>Theta-Beta-M Relation: </strong></h3>
  <div>
  $$\dfrac{\tan \beta}{\tan (\beta - \theta)} = \dfrac{(\gamma+1)M_1^2 \sin^2\beta}{2+(\gamma-1)M_1^2 \sin^2\beta}
  \label{tantan sinsin} $$
  </div>
</div>

This equation is also presented equivalently in various forms in textbooks. For example, 

$$
\boxed{\tan \theta=\dfrac{2 (\cot \beta) (M_1^2 \sin^2 \beta -1)}{2+M_1^2 (\gamma + \cos 2\beta)}} \label{theta beta M}
$$

$$
\boxed{M_1^2 \sin^2 \beta -1 = \dfrac{\gamma+1}{2} M_1^2 \dfrac{\sin \beta \sin \theta}{\cos(\beta-\theta)}} \label{m1squared-1}
$$

<details class="custom-collapse">
  <summary><strong>Show Derivation for Eqs. \ref{theta beta M} and \ref{m1squared-1}</strong></summary>
  <div class = "collapse-content">
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

</div>
</details>

##  Infinitely Weak Oblique Shock Approaching Mach Line

For small deflection angles \\( \theta \\), Eq. \ref{m1squared-1} approximately becomes,

$$
\begin{equation}
M_1^2 \sin^2 \beta-1 \approx \left[\dfrac{\gamma+1}{2}M_1^2 \tan \beta \right] \theta \label{M1^2approx}
\end{equation}
$$

Plugging Eq. \ref{M1^2approx} into Eq. \ref{pressureratio}, the pressure ratio becomes, for small deflection angles,

$$\begin{equation}
\dfrac{p_2}{p_1}\approx 1 + (\gamma M_1^2 \tan \beta) \theta \label{weakpressureratio}
\end{equation}$$

As the flow deflection becomes smaller, \\( \beta \\) approaches the Mach angle, \\( \mu \\). Therefore, \\( \tan \beta \approx \tan \mu=1/\sqrt{M_1^2-1} \\). 

<div class="equation-box">
  <h3><strong>Pressure Ratio Across an Infinitely Weak Oblique Shock: </strong></h3>
  <div>
$$\begin{equation}
    \dfrac{p_2}{p_1}=1+\dfrac{\gamma M_1^2}{\sqrt{M_1^2-1}} \theta, \quad \dfrac{\Delta p}{p_1}=\dfrac{\gamma M_1^2}{\sqrt{M_1^2-1}} \theta
    \label{weakpressureratiofinal}
\end{equation}
$$

For small perturbations, so small \(\theta \)
  </div>
</div>

<figure id="fig-obliquemach" style="width: 60%; max-width: 500px; margin: 0 auto; text-align: center; display: block;">
  <img src="/images/obliquemach.png" alt="Oblique Mach" style="width: 100%; height: auto;">
  <figcaption style="margin-top: 0.5em;">
    <strong>Figure 2:</strong> Mach wave (blue) and oblique shock (red) for some given flow deflection
  </figcaption>
</figure>

<details class="custom-collapse">
  <summary><strong>Show relationship between epsilon and theta</strong></summary>
  <div class = "collapse-content">

Looking at fig. 2, we define the difference between the oblique and Mach angle as \( \epsilon \).

$$\beta = \mu + \epsilon
\notag
$$

$$
\begin{align*}
  \sin \beta = \sin (\mu + \epsilon)= \sin \mu \cos \epsilon + \cos \mu \sin \epsilon &\approx \sin \mu + \epsilon \cos \mu \\ & \approx \dfrac{1}{M_1}+\dfrac{\epsilon}{M_1} \sqrt{M_1^2-1}
\end{align*}
$$

$$
\begin{align}
    M_1 \sin \beta &\approx 1+ \epsilon \sqrt{M_1^2-1} \nonumber\\
    M_1^2 \sin^2 \beta &\approx 1+2\epsilon \sqrt{M_1^2-1} + \cancel{\epsilon^2 (M_1^2-1)} \nonumber \\
    M_1^2 \sin^2 \beta -1 &= 2 \epsilon \sqrt{M_1^2-1}, \text{ for small perturbations} \label{M1^2epsilon}
\end{align}
$$

Setting the right hand sides of Eqs. \ref{M1^2approx} and \ref{M1^2epsilon} equal to each other, I obtain 

$$
\begin{align}
    2\epsilon \sqrt{M_1^2-1}&=\dfrac{\gamma+1}{2} \dfrac{M_1^2}{\sqrt{M_1^2-1}} \theta \\
    \epsilon&= \dfrac{\gamma+1}{4}\dfrac{M_1^2}{M_1^2-1} \theta \label{epsilontheta}
\end{align}
$$

</div>
</details>

Eq. \ref{epsilontheta} leads us to conclude that \\(\epsilon\\) is proportional to (on the same order of) \\(\theta\\). That is, for an infinitely weak oblique shock, the difference in the shock and Mach angle is on the same order of the flow deflection angle. 

Recall from the geometry of oblique shock theory (Eqs. \ref{momentum}, \ref{geometry}),

$$\begin{equation}
\boxed{\dfrac{V_2^2}{V_1^2}= \dfrac{\cos^2 \beta}{\cos^2 (\beta-\theta)}} \label{v2/v1 squared relation}
\end{equation}$$

Rearranging Eq. \ref{M1^2epsilon},
$$\begin{align}
    \sin^2 \beta&=\dfrac{1+ 2\epsilon \sqrt{M_1^2-1}}{M_1^2} \nonumber \\
    \cos^2 \beta &= 1-\sin^2 \beta=1-\dfrac{1}{M_1^2} \left[1+2\epsilon\sqrt{M_1^2-1}\right] \nonumber \\
    \cos^2 \beta &= \dfrac{M_1^2-1}{M_1^2} \left[ 1- \dfrac{2 \epsilon}{\sqrt{M_1^2-1}}\right]
    \label{cos2beta}
\end{align}$$

Now, we solved for the numerator of Eq. \ref{v2/v1 squared relation}. What remains is to solve for the denominator. I follow a similar procedure in determining \\(\cos^2 (\beta-\theta)\\) as \\(\cos^2 \beta\\). 

$$\sin (\beta -\theta)= \sin[\mu + (\epsilon-\theta)]= \sin \mu \cos (\epsilon - \theta) + \cos \mu \sin (\epsilon -\theta) \notag$$

In the small angle approximation, \\(\cos (\epsilon-\theta) = 1\\) and \\(\sin (\epsilon - \theta) = \epsilon -\theta\\), 

$$\sin(\beta-\theta) = \sin \mu + (\epsilon-\theta) \cos \mu = \dfrac{1}{M_1}+(\epsilon-\theta)\dfrac{\sqrt{M_1^2-1}}{M_1} \notag
$$

Squaring and ignoring all higher order terms,

$$\begin{align}
    \sin^2 (\beta-\theta) &= \dfrac{1}{M_1^2}\left[ 1+ 2(\epsilon - \theta) \sqrt{M_1^2-1}\right] \nonumber \\
    \cos^2 (\beta -\theta) &=1-\sin^2(\beta -\theta)=1-\dfrac{1}{M_1^2} \left[ 1+ 2 (\epsilon - \theta) \sqrt{M_1^2-1}\right] \nonumber \\
    \cos ^2 (\beta - \theta) &= \dfrac{M_1^2-1}{M_1^2} \left[ 1-\dfrac{2(\epsilon - \theta)}{\sqrt{M_1^2-1}}\right]
    \label{cos^2 beta -theta}
\end{align}$$

Substituting Eqs. \ref{cos2beta} and \ref{cos^2 beta -theta} into Eq. \ref{v2/v1 squared relation}, and using Eq. \ref{epsilontheta} to express \\(\epsilon\\) in terms of \\(\theta\\), we obtain \\(V_2/V_1\\) as a function of \\(\theta\\).

$$\begin{equation}
    \boxed{\dfrac{V_2}{V_1}=\sqrt{\dfrac{1-\dfrac{\gamma+1}{2} \dfrac{M_1^2}{(M_1^2-1)^{3/2}}\theta}{1-\dfrac{2\theta}{\sqrt{M_1^2-1}} \left[ \dfrac{\gamma + 1}{4} \dfrac{M_1^2}{M_1^2-1}-1\right]}}}
    \label{V2V1functiontheta}
\end{equation}$$

Eq. \ref{V2V1functiontheta} is of the form \\(f(\theta) = \sqrt{\dfrac{1+A \theta}{1+B \theta}}\\), where \\(A= - \dfrac{\gamma+1}{2} \dfrac{M_1^2}{(M_1^2-1)^{3/2}}\\) 

and \\(B=\dfrac{-2}{\sqrt{M_1^2-1}} \left[ \dfrac{\gamma+1}{4}\dfrac{M_1^2}{M_1^2-1}-1\right]\\).

If we do a Taylor expansion and neglect all higher order terms, we obtain the velocity ratio across an infinitely weak oblique shock. 

<div class="equation-box">
  <h3><strong> Velocity Ratio Across an Infinitely Weak Oblique Shock: </strong></h3>
  <div>
  $$\begin{equation}
      \dfrac{V_2}{V_1}=1-\dfrac{\theta}{\sqrt{M_1^2-1}}, \quad \dfrac{\Delta V}{V_1}=-\dfrac{\theta}{\sqrt{M_1^2-1}}
      \label{velocityratioveryweakobliqueshock}
  \end{equation}$$
  </div>
</div>

What does this tell us? For a very small flow deflection angle \\(\theta\\), we see that the oblique shock approaches the Mach wave, and we can calculate the velocity and pressure change from Eqs. \ref{weakpressureratiofinal} and \ref{velocityratioveryweakobliqueshock}. 

It can be shown that \\(\Delta s \sim ({\Delta p}/{p_1})^3\sim\theta^3\\), but I will omit the proof here. You can derive it by doing a Taylor expansion on the entropy change across a shock. Notice that if the flow deflection is small, the change in entropy is even smaller, so the flow can be considered nearly isentropic. 

Imagine that instead of turning the flow abruptly from \\(0^\circ \\) to \\( \theta^\circ \\) via an oblique shock, we turn the flow gradually through a series of very weak, nearly isentropic Mach waves.

<figure id="fig-successive" style="width: 60%; max-width: 500px; margin: 0 auto; text-align: center; display: block;">
  <img src="/images/successive.png" alt="successive" style="width: 100%; height: auto;">
  <figcaption style="margin-top: 0.5em;">
    <strong>Figure 3:</strong> Top: Flow turning through successive isentropic compression waves, Bottom: Flow abruptly turning through oblique shock
  </figcaption>
</figure>

We can solve for the flowfield properties of an isentropic compression caused by a smooth, continuous boundary by approximating the boundary with straight line segments, with infinitely weak oblique shocks at each ``corner". 

This sensation should be familiar! Yes, this should remind you of Calculus, approximating a continuous curve with discrete line segments! As \\( n\to\infty \\), \\( \Delta \theta \to d\theta \\), and \\( \Delta \theta \to d \theta \\), so that Eq. \ref{velocityratioveryweakobliqueshock} becomes a differential equation, 

$$\begin{equation}
    \dfrac{dV}{V}=-\dfrac{d\theta}{\sqrt{M^2-1}}
    \label{diffeqn_prandtl_meyer}
\end{equation}$$

It is useful to rewrite Eq. \ref{diffeqn_prandtl_meyer} in terms of Mach number. I do this by differentiating \\( M=V/a \\) to obtain Eq. \ref{Mach number definition}. By manipulating the differential adiabatic energy equation \\( c_p dT + V dV =0 \\), I also obtain Eq. \ref{differentialadiabaticenergyeqn}.

$$\begin{equation}
    \dfrac{dV}{V}=\dfrac{dM}{M} + \dfrac{1}{2} \dfrac{dT}{T}
    \label{Mach number definition}
\end{equation}
$$

$$\begin{equation}
    \dfrac{dT}{T}+(\gamma-1)M^2 \dfrac{dV}{V}=0
    \label{differentialadiabaticenergyeqn}
\end{equation}$$

Eqs. \ref{Mach number definition}-\ref{differentialadiabaticenergyeqn} together yield, 

$$\begin{equation}
    \dfrac{dV}{V}=\dfrac{1}{1+\dfrac{\gamma-1}{2}M^2} \dfrac{dM}{M}
    \label{dVV=dMM}
\end{equation}$$

Plug Eq. \ref{dVV=dMM} into Eq. \ref{diffeqn_prandtl_meyer},

<div class="equation-box">
  <h3><strong> Differential Form of Prandtl-Meyer Function </strong></h3>
  <div>
  $$
  \begin{equation}
      d\nu =-d\theta = \dfrac{\sqrt{M^2-1}}{1+\dfrac{\gamma-1}{2}M^2 } \dfrac{dM}{M} 
      \label{PrandtlMeyerFinal}
  \end{equation}
  $$
  </div>
  </div>

## Integrating to Obtain the Prandtl-Meyer Function 

Integrating Eq. \ref{PrandtlMeyerFinal} is an arduous task, the solution of which is called the Prandtl-Meyer function. 

$$\begin{align*}
    d\nu &= \dfrac{\sqrt{M^2-1}}{1+\dfrac{\gamma-1}{2}M^2 } \dfrac{dM}{M} \\
    \int_{\nu(1)}^{\nu(M)} \, d\nu &= \int_{1}^{M} \dfrac{\sqrt{\overline{M^2}-1}}{1+\dfrac{\gamma-1}{2}\overline{M^2}} \, \dfrac{d\overline{M}}{\overline{M}}, \quad \text{where $\overline{M}$ is a dummy variable} 
\end{align*}$$

If we make the following change of variables, 
$$ z^2=\overline{M}^2-1 , \quad \dfrac{d\overline{M}}{\overline{M}}=\dfrac{z}{z^2+1} \, dz $$

$$\begin{equation}
\nu(M)-\nu(1)= \int_{0}^{\sqrt{M^2-1}}  \left[\dfrac{z^2}{1+ \dfrac{\gamma-1}{2} (z^2+1)} \right] \left[\dfrac{1}{z^2+1}\right] \, dz
\label{prandtlmeyerintegral}
\end{equation}$$

We can perform partial fraction decomposition on the integrand and then find the antiderivative, with the help of the identity \\( \int \dfrac{1}{1+(az)^2} \, dz = \dfrac{1}{a} \tan^{-1} (az) + C \\). 

$$\begin{align*}
 \int \dfrac{z^2}{1+ \dfrac{\gamma-1}{2} (z^2+1)}  \dfrac{1}{z^2+1} \, dz &= \int \left[\dfrac{1}{1+\dfrac{\gamma-1}{\gamma+1} z^2}-\dfrac{1}{z^2+1} \right] \, dz  \\
 &= \sqrt{\dfrac{\gamma+1}{\gamma-1}}\tan^{-1} \left(z \sqrt{\dfrac{\gamma-1}{\gamma+1}}\right)-\tan^{-1} (z) + C
\end{align*}$$

The limits of integration is arbitrary. To obtain a neat form, let's set \\( \nu(1) =0 \\). Eq. \ref{prandtlmeyerintegral} reduces to, 

$$\nu(M) = \left[\sqrt{\dfrac{\gamma+1}{\gamma-1}}\tan^{-1} \left(z \sqrt{\dfrac{\gamma-1}{\gamma+1}}\right)-\tan^{-1} (z) \right]_{z=0}^{z=\sqrt{M^2-1}}
$$

<div class="equation-box">
  <h3><strong> Prandtl-Meyer Function </strong></h3>
  <div>
  $$
    \begin{equation}
    \nu(M) = \sqrt{\dfrac{\gamma+1}{\gamma-1}} \tan^{-1} \left[\sqrt{\dfrac{\gamma-1}{\gamma+1} (M^2-1)} \right]- \tan^{-1} (\sqrt{M^2-1})
    \label{Prandtl-Meyer Function}
    \end{equation}
  $$
  </div>
</div>

The Prandtl-Meyer function reaches an asymptote as \\( M \to \infty \\).

$$\nu(\infty)=\dfrac{\pi}{2} \left( \sqrt{\dfrac{\gamma + 1}{\gamma - 1}}-1\right)=130.45 ^ \circ \text{ for } \gamma=1.4
$$

It is often useful to define the characteristic Mach number, \\( M_\star=V/a_\star \\), where \\( a_\star \\) is the hypothetical speed of sound when we imagine accelerating/decelerating the particle to sonic state \\( (M=1) \\). Then, we can express the Prandtl-Meyer equation as a function of the characteristic Mach number instead. See below for a derivation to relate \\( M \\) to \\( M_\star \\).

<figure id="fig-PM-comparison" style="width: 100%; max-width: 900px; margin: 0 auto; text-align: center;">

  <div style="display: flex; justify-content: space-between; flex-wrap: wrap; gap: 1em;">

    <!-- Subfigure 1 -->
    <div style="flex: 1 1 48%; text-align: center;">
      <img src="/images/PM_vs_M.png" alt="Prandtl-Meyer vs M" style="width: 100%; height: auto;">
      <figcaption style="margin-top: 0.5em;">
        <strong>Figure 4a:</strong> Prandtl-Meyer function vs Mach number \(M\)
      </figcaption>
    </div>

    <!-- Subfigure 2 -->
    <div style="flex: 1 1 48%; text-align: center;">
      <img src="/images/PM_vs_Mstar.png" alt="Prandtl-Meyer vs M*" style="width: 100%; height: auto;">
      <figcaption style="margin-top: 0.5em;">
        <strong>Figure 4b:</strong> Prandtl-Meyer function vs characteristic Mach number \(M^*\)
      </figcaption>
    </div>

  </div>

  <figcaption style="margin-top: 1em;">
    <strong>Figure 4:</strong> Prandtl-Meyer function with respect to \(M\) and \(M^*\).
  </figcaption>
</figure>

<details class="custom-collapse">
  <summary><strong> Relating \( M \) and \( M_\star \) </strong></summary>
  <div class = "collapse-content">

Start with the adiabatic energy equation, 
$$c_p T_1 + \dfrac{V_1^2}{2}=c_p T_2 + \dfrac{V_2^2}{2} \notag$$
$$\dfrac{a_1^2}{\gamma-1}+\dfrac{V_1^2}{2}=\dfrac{a_2^2}{\gamma-1}+\dfrac{V_2^2}{2} \notag $$

Let's drop the subscript for state 1 and have state 2 be the sonic state.
$$\dfrac{a^2}{\gamma-1}+\dfrac{V^2}{2}=\dfrac{a_\star^2}{\gamma-1}+\dfrac{V_\star^2}{2}, \quad (a_\star =V_\star) \notag$$
$$a_\star^2 = \dfrac{2(\gamma-1)}{\gamma+1} \left[ \dfrac{a^2}{\gamma-1}+\dfrac{V^2}{2} \right] \notag
$$

Divide by \( V^2 \) and let \( M_\star=\dfrac{V}{a_\star} \),

$$\dfrac{1}{M_\star^2}=\dfrac{2(\gamma-1)}{\gamma + 1} \left[ \dfrac{1}{\gamma-1} \dfrac{1}{M^2}+\dfrac{1}{2} \right] \notag
$$

$$\begin{equation}
    \boxed{M_\star^2 = \dfrac{(\gamma+1) M^2}{2 + (\gamma-1  )M^2}, \quad M^2 = \dfrac{2}{\gamma+1} \left[\dfrac{M_\star^2}{1-\dfrac{\gamma-1}{\gamma+1}M_\star^2} \right]}
    \label{M_vs_Mstar_relation}
\end{equation}$$

The advantage of using \( M_\star \) instead of M is because as \( M \to \infty, \ \  M_\star \to \sqrt{\dfrac{\gamma+1}{\gamma-1}} \)
</div>
</details>

## Theory of Method of Characteristics

Earlier above, I derived the Prandtl-Meyer function from the infinitely weak limiting case of an oblique shock. There is an alternative method of deriving the Prandtl-Meyer function using a more generic technique for solving hyperbolic partial differential equations -- the method of characteristics. 

We start with the governing equation of motion for steady, homentropic, homenthalpic flow. 
$${\mathbf{u} \cdot [\mathbf{u} \cdot \nabla \mathbf{u}] - a^2 \nabla \cdot \mathbf{u}=0} \notag
$$
Specializing to the 2D case,

$${(u^2 -a^2) \dfrac{\partial u}{\partial x} + (v^2-a^2) \dfrac{\partial v}{\partial y} + uv \left( \dfrac{\partial u}{\partial y} + \dfrac{\partial v}{\partial x}\right) = 0} \notag$$

Substitute in velocity potential, \\( \quad u = \phi_x, \quad v = \phi_y \\),  

$$(u^2-a^2) \phi_{xx} + (v^2-a^2) \phi_{yy} + 2uv \phi_{xy}=0 \notag$$

To make the equation simpler, let's define  \\( A=u^2-a^2, \enspace B=uv, \enspace C=v^2-a^2 \\).
$${A\phi_{xx}+2B \phi_{xy} + C \phi_{yy}=0} \notag
$$

Since \\( u=u(x,y) \\) and \\( v=v(x,y) \\), then we have by the multivariable chain rule, 

$$\begin{align*}
    du = \dfrac{\partial u}{\partial x} dx + \dfrac{\partial u}{\partial y} dy=\phi_{xx} dx + \phi_{xy} dy \\ 
    dv = \dfrac{\partial v }{\partial x} dx + \dfrac{\partial v }{\partial y} dy = \phi_{xy} dx + \phi_{yy} dy
\end{align*}$$

Putting it all together, the system of equations is formed. 

$$\left\{
\begin{aligned}
    A \phi_{xx} + 2B \phi_{xy} + C \phi_{yy} &= 0 \\
    dx \, \phi_{xx}  + dy \, \phi_{xy} + 0 \, \phi_{yy} &= du \\
    0 \, \phi_{xx} + dx \, \phi_{xy} + dy \, \phi_{yy} &= dv
\end{aligned}
\right\}$$

In matrix form, 

$$
\begin{equation}
\begin{bmatrix}
A & 2B & C \\
dx & dy & 0 \\
0 & dx & dy
\end{bmatrix}
\begin{bmatrix}
\phi_{xx} \\
\phi_{xy} \\
\phi_{yy}
\end{bmatrix}
=
\begin{bmatrix}
0 \\
du \\
dv
\end{bmatrix}
\label{methodofcharacteristicsmatrix}
\end{equation}$$

To understand the method of characteristics, let's imagine the velocity flowfield,  \\( u=u(x,y), \enspace v=v(x,y) \\). Physically, we know that the velocities must be continuous. There are no abrupt shocks or discontinuities in the velocity variables since the flow is isentropic. However, the first derivative of the velocities \\( \dfrac{\partial u}{\partial x}, \dfrac{\partial u}{\partial y}, \dfrac{\partial v}{\partial x}, \dfrac{\partial v}{\partial y} \\) can be discontinuous but finite. In the method of characteristics, the goal is to find the lines in the flowfield along which the  first derivative of the velocities is indeterminate and across which it can be discontinuous.  

As an example, we use Cramer's rule to solve for \\( \phi_{xx}= \dfrac{\partial u }{\partial x} \\) in the system of equations Eq. \ref{methodofcharacteristicsmatrix}.

$$\begin{equation}
\phi_{xx} = \dfrac{N}{D} = \dfrac{\begin{vmatrix}
    0 & 2B & C \\
    du & dy & 0 \\ 
    dv & dx & dy
\end{vmatrix}}{\begin{vmatrix}
    A & 2B & C \\
    dx & dy & 0 \\
    0 & dx &dy
\end{vmatrix}}=\dfrac{0}{0}
\label{numerator-denominator}
\end{equation}$$

First, let's focus on D = 0 in Eq. \ref{numerator-denominator}.

$$\boxed{\dfrac{dy}{dx}=\dfrac{B \pm \sqrt{B^2-AC}}{A}=\dfrac{\dfrac{uv}{a^2}\pm \sqrt{\dfrac{u^2+v^2}{a^2}-1}}{\dfrac{u^2}{a^2}-1}} \notag
$$

Using polar coordinates, \\( u = V\cos\theta, \enspace v=V \sin \theta \\), and \\( \sin \mu = 1/M \\), 

$$\begin{align}
\dfrac{dy}{dx} &=\dfrac{\cos \theta \sin \theta \pm \cos \mu \sin \mu}{\cos^2 \theta - \sin^2 \mu } \nonumber \\
&= \dfrac{\dfrac{1}{2}\left( \sin2\theta\pm \sin 2\mu\right)}{\cos^2 \theta - \sin^2 \mu} 
\label{trigintermediate}
\end{align}$$

The following trig identities are useful in transforming Eq. \ref{trigintermediate}. 

$$\begin{align*}
    \sin 2\theta &= \dfrac{2 \tan \theta}{1+ \tan^2 \theta} \\ 
    \cos^2 \theta &= \dfrac{1}{1+\tan^2 \theta} \\ 
    \sin^2 \theta &= \dfrac{\tan^2 \theta}{1+\tan^2 \theta} 
\end{align*}$$

Eq. \ref{trigintermediate} transforms to, using the shorthand notation defined above, 
$$\begin{align*}
    \dfrac{dy}{dx}=\dfrac{\dfrac{t_\theta}{1+ t_\theta^2} \pm \dfrac{t_\mu}{1+t_\mu^2}}{\dfrac{1}{1+t_\theta^2}-\dfrac{t_\mu^2}{1+t_\mu^2}} &=\dfrac{(t_\theta \pm t_\mu) + (t_\mu \pm t_\theta) t_\theta t_\mu}{(1-t_\theta t_u)(1+t_\theta t_\mu)} \\ 
    &= \dfrac{\mathcal{A}}{1-t_\theta t_\mu} + \dfrac{\mathcal{B}}{1+t_\theta t_\mu}
\end{align*}$$

After performing the partial fraction decomposition, I obtain 

$$\mathcal{A} = \dfrac{(t_\theta \pm t_\mu) + (t_\mu \pm t_\theta)}{2}, \quad \mathcal{B} = \dfrac{(t_\theta \pm t_\mu)-(t_\mu \pm t_\theta)}{2} \notag
$$

There are only two possibilities. 

$$+ : \quad \mathcal{A} = t_\mu + t_\theta, \quad \mathcal{B} =0 \notag$$
$$- : \quad \mathcal{A} =0, \quad \mathcal{B} = t_\theta - t_\mu \notag
$$

Therefore,
$$\boxed{\dfrac{dy}{dx}= \dfrac{\tan\theta\pm \tan\mu}{1\mp \tan \theta \tan\mu}=\tan(\theta \pm \mu)} \notag
$$

<div class="equation-box">
  <h3><strong> Physical Characteristic Equation </strong></h3>
  <div>
  $$
  \begin{equation}
  \dfrac{dy}{dx}=\tan(\theta \pm \mu)=\dfrac{\dfrac{uv}{a^2}\pm \sqrt{\dfrac{u^2+v^2}{a^2}-1}}{\dfrac{u^2}{a^2}-1}
  \label{characteristicequationfinal}
  \end{equation}
  $$
  $$
  \left( \dfrac{dy}{dx} \right)_{C_{+}}=\tan(\theta + \mu), \quad  \left( \dfrac{dy}{dx} \right)_{C_{-}} = \tan(\theta - \mu)
  $$
  </div>
</div>

Importantly, Eq. \ref{characteristicequationfinal} shows that the physical characteristics represent Mach lines. 

Now, let's go to N = 0 in Eq. \ref{numerator-denominator}.

$$
\begin{align}
    \dfrac{dv}{du} &=\dfrac{1}{dy/dx}-\dfrac{2B}{C} \nonumber \\ 
    &= \dfrac{\dfrac{u^2}{a^2}-1}{\dfrac{uv}{a^2}\pm \sqrt{\dfrac{u^2 + v^2}{a^2}-1}}+\dfrac{\dfrac{2uv}{a^2}}{1-\dfrac{v^2}{a^2}} = \dfrac{\left(\dfrac{u^2}{a^2}-1 \right) \left(1-\dfrac{v^2}{a^2} \right)+\dfrac{2uv}{a^2} \left( \dfrac{uv}{a^2} \pm \sqrt{\dfrac{u^2+v^2}{a^2}-1}\right)}{\left( \dfrac{uv}{a^2} \pm \sqrt{\dfrac{u^2 +v^2}{a^2}-1} \right) \left(1-\dfrac{v^2}{a^2} \right)} \nonumber \\ 
    &= \dfrac{\left(\dfrac{u v}{a^2}\right)^2 \pm \dfrac{2uv}{a^2}\sqrt{\dfrac{u^2+v^2}{a^2}-1} + \left(\dfrac{u^2 +v^2}{a^2}-1 \right)}{\left( \dfrac{uv}{a^2} \pm \sqrt{\dfrac{u^2 +v^2}{a^2}-1} \right) \left(1-\dfrac{v^2}{a^2} \right)}= \dfrac{\left[\dfrac{uv}{a^2} \pm \sqrt{\dfrac{u^2+v^2}{a^2}-1} \right]^2}{\left( \dfrac{uv}{a^2} \pm \sqrt{\dfrac{u^2 +v^2}{a^2}-1} \right) \left(1-\dfrac{v^2}{a^2} \right)} \nonumber 
\end{align}
$$

$$\begin{equation*}
\boxed{\dfrac{dv}{du} = \dfrac{-\dfrac{uv}{a^2}\mp \sqrt{\dfrac{u^2+v^2}{a^2}-1}}{\dfrac{v^2}{a^2}-1}}
\end{equation*}$$

Converting to polar coordinates, 
$$\dfrac{dv}{du}=\dfrac{d(V \sin \theta)}{d(V \cos \theta)}= \dfrac{s_\theta dV + Vc_\theta d\theta}{c_\theta dV - V s_\theta d \theta} = \dfrac{-M^2 c_\theta s_\theta \mp \sqrt{M^2-1}}{M^2 s_\theta ^2 -1 } \notag$$

After some algebraic manipulations, 
$$d\theta \mp \sqrt{M^2-1} \dfrac{dV}{V}=0 \notag
$$
Using Eq. \ref{dVV=dMM} to rewrite in terms of Mach number, 

$$\begin{equation*}
d \theta \mp \dfrac{\sqrt{M^2-1}}{1+ \dfrac{\gamma-1}{2}M^2} \dfrac{dM}{M}=0
\end{equation*}$$

Noting the similarity to the Prandtl-Meyer differential equation, we can transform the above into,
$$\boxed{d(\theta \mp \nu)=0}
$$

<div class="equation-box">
  <h3><strong> Hodograph Characteristics / Riemann Invariants</strong></h3>
  <div>

$$\begin{equation}
    \dfrac{dv}{du} = \dfrac{-\dfrac{uv}{a^2}\mp \sqrt{\dfrac{u^2+v^2}{a^2}-1}}{\dfrac{v^2}{a^2}-1}, \quad d(\theta \mp \nu) = 0
    \label{riemanninvariants}
\end{equation}
$$

$$ 
\begin{align*}
    \theta -\nu &= C_+ \\
    \theta + \nu &= C_- 
\end{align*}
$$
</div>
</div>

The Riemann invariants (Eq. \ref{riemanninvariants}) relate flow direction \\( \theta \\) to Mach number  \\( M \\). If we instead use the characteristic Mach number \\( M_\star \\), we can graph all possible hodograph characteristic curves in the \\( (u/a_\star, v/a_\star) \\) Cartesian plane, or equivalently, the \\( (M_\star,\theta) \\) polar plane. 

<figure id="fig-hodograph" style="width: 50%; max-width: 500px; margin: 0 auto; text-align: center; display: block;">
  <img src="/images/hodograph.png" alt="hodograph" style="width: 100%; height: auto;">
  <figcaption style="margin-top: 0.5em;">
    <strong>Figure 5:</strong> Hodograph Characteristics
  </figcaption>
</figure>

To graph fig. 5, we use a polar plot. The theta coordinate is given by \\( \theta=\pm \nu (M_\star) + \text{const.} \\) The radial coordinate is given by \\( r=M_\star \\). We vary the constant term to obtain different characteristic curves. In addition, \\( 1< M_\star < \sqrt{(\gamma+1)/(\gamma-1)} \\) which corresponds to \\( 1 < M < \infty \\). Below is the matlab code used, 

<details class="custom-collapse">
  <summary><strong>Click to expand MATLAB code</strong></summary>
  
    <pre><code>

    g = 1.4 ; %specific heat ratio 
    Cvec = 0:deg2rad(5):2*pi; %constant
    figure(1);
    pax = polaraxes;
    hold(pax,'on')

    for i = 1:length(Cvec)

        C = Cvec(i);
        Ms = linspace(1,sqrt( (g+1)/(g-1) )) ;
        M = sqrt( 2/(g+1) * Ms.^2 ./(1 - (g-1)/(g+1) * Ms.^2) ) ;
        nu = sqrt( (g+1)/(g-1) ) * atan( sqrt((g-1)/(g+1)*(M.^2-1)) ) - atan( sqrt(M.^2-1) ) ;

        thetaII = C + nu;
        thetaI = C - nu ;

        polarplot(thetaII,Ms,'k')
        polarplot(thetaI,Ms,'k')

    end 

    </code></pre>   
</details>

The relationship between the physical characteristics and the hodograph characteristics is important. 

$$\begin{align*}
    \left( \dfrac{dv}{du}\right)_{C_+} \left( \dfrac{dy}{dx} \right)_{C_-} &= \left[ \dfrac{-\dfrac{uv}{a^2}-\sqrt{\dfrac{u^2 +v^2}{a^2}-1}}{\dfrac{v^2}{a^2}-1}\right] \left[ \dfrac{\dfrac{uv}{a^2}-\sqrt{\dfrac{u^2+v^2}{a^2}-1}}{\dfrac{u^2}{a^2}-1}\right] \\
    &=-1
\end{align*}$$

Similarly, 
$$\left( \dfrac{dv}{du}\right)_{C_-} \left( \dfrac{dy}{dx} \right)_{C_+} = -1 \notag$$

Therefore, we conclude that the hodograph characteristics are orthogonal to the physical characteristics of the opposite family. 

## Method of Characteristics Numeric Method

<figure id="table-moc-comparison" style="width: 100%; max-width: 900px; margin: 0 auto; text-align: center;">

  <!-- Row 1 -->
  <div style="display: flex; justify-content: space-between; flex-wrap: wrap; margin-bottom: 1.5em;">
    <div style="flex: 1 1 48%; text-align: center;">
      <img src="/images/table1moca.png" alt="Table 1 MOCA" style="width: 100%; height: auto;">
      <figcaption style="margin-top: 0.5em;"><strong>Table 1a:</strong> \( 18^{\circ} \) Straight-Walled Diverging Channel: Three-Point Division</figcaption>
    </div>
    <div style="flex: 1 1 48%; text-align: center;">
      <img src="/images/table1mocb.png" alt="Table 1 MOCB" style="width: 100%; height: auto;">
      <figcaption style="margin-top: 0.5em;"><strong>Table 1b:</strong> \( 18^{\circ} \) Straight-Walled Diverging Channel: Three-Point Division </figcaption>
    </div>
  </div>

  <!-- Row 2 -->
  <div style="display: flex; justify-content: space-between; flex-wrap: wrap; margin-bottom: 1.5em;">
    <div style="flex: 1 1 48%; text-align: center;">
      <img src="/images/table2moca.png" alt="Table 2 MOCA" style="width: 100%; height: auto;">
      <figcaption style="margin-top: 0.5em;"><strong>Table 2a:</strong> \( 18^{\circ} \) Straight-Walled Diverging Channel: Four-Point Division </figcaption>
    </div>
    <div style="flex: 1 1 48%; text-align: center;">
      <img src="/images/table2mocb.png" alt="Table 2 MOCB" style="width: 100%; height: auto;">
      <figcaption style="margin-top: 0.5em;"><strong>Table 2a:</strong> \( 18^{\circ} \) Straight-Walled Diverging Channel: Four-Point Division</figcaption>
    </div>
  </div>

  <!-- Row 3 -->
  <div style="display: flex; justify-content: space-between; flex-wrap: wrap;">
    <div style="flex: 1 1 48%; text-align: center;">
      <img src="/images/table3moca.png" alt="Table 3 MOCA" style="width: 100%; height: auto;">
      <figcaption style="margin-top: 0.5em;"><strong>Table 3a: </strong> \( 18^{\circ} \) Straight-Walled Diverging Channel: Seven-Point Division </figcaption>
    </div>
    <div style="flex: 1 1 48%; text-align: center;">
      <img src="/images/table3mocb.png" alt="Table 3 MOCB" style="width: 100%; height: auto;">
      <figcaption style="margin-top: 0.5em;"><strong>Table 3b: </strong> \( 18^{\circ} \) Straight-Walled Diverging Channel: Seven-Point Division </figcaption>
    </div>
  </div>
</figure>

<br>
<br>

<figure id="fig-diverging-channel-comparison" style="width: 100%; max-width: 700px; margin: 0 auto; text-align: center;">

  <!-- Subfigure 1 -->
  <div style="margin-bottom: 1em;">
    <img src="/images/threepoint.png" alt="Three-point division" style="width: 60%; height: auto;">
    <figcaption style="margin-top: 0.5em;">
      <strong>Figure 5a:</strong> Three-point division
    </figcaption>
  </div>

  <!-- Subfigure 2 -->
  <div style="margin-bottom: 1em;">
    <img src="/images/fourpoint.png" alt="Four-point division" style="width: 60%; height: auto;">
    <figcaption style="margin-top: 0.5em;">
      <strong>Figure 5b:</strong> Four-point division
    </figcaption>
  </div>

  <!-- Subfigure 3 -->
  <div style="margin-bottom: 1em;">
    <img src="/images/sevenpoint.png" alt="Seven-point division" style="width: 60%; height: auto;">
    <figcaption style="margin-top: 0.5em;">
      <strong>Figure 5c:</strong> Seven-point division
    </figcaption>
  </div>

  <!-- Main Caption -->
  <figcaption style="margin-top: 1em;">
    <strong>Figure 5:</strong> Physical characteristic curves in \(18^\circ\) straight-walled diverging channel for various point-division schemes.
  </figcaption>
</figure>

### Comparison with Quasi-One-Dimensional Model

Let's compare the results with quasi-one-dimensional flow. Starting with three-point division,

$$\begin{align*}
    \underline{\text{Three-Point Division}} \\
    \dfrac{A_{10}}{A_1}=\dfrac{A_{10}}{A_\star} \dfrac{A_\star}{A_1} &=2.1369 \\
    \dfrac{A_{10}}{A_\star} &= 2.1369 \dfrac{A_1}{A_\star} = (2.1369)(1.1349)=2.4252 \\
    \boxed{\text{Q1D Result:} \quad M_{10} = 2.4099} \\
    \boxed{\text{MOC Result:} \quad M_{10} = 2.4104}
\end{align*}$$

We repeat this same process for the higher point divisions. 

$$\begin{align*}
    \underline{\text{Four-Point Division}} \\
    \text{Q1D Result: } \quad \boxed{M_{13} =2.0589} \\
    \text{MOC Result: } \quad \boxed{M_{13}=2.0592}
\end{align*}$$

$$\begin{align*}
    \underline{\text{Seven-Point Division}} \\
    \text{Q1D Result: } \quad \boxed{M_{18} =1.7406} \\
    \text{MOC Result: } \quad \boxed{M_{18}=1.7406}
\end{align*}$$

Therefore, we have come to the rather obvious conclusion that finer characteristic grids (more point divisions) lead to more accuracy. 

<details class="custom-collapse">
  <summary><strong> Aside: Quasi-One-Dimensional Flow </strong></summary>
  <div class = "collapse-content">

$$\begin{align}
     \quad \dfrac{d \rho}{\rho}+\dfrac{du}{u}+ \dfrac{dA}{A}&=0 \tag{mass} \label{masseqnQ1D}\\
     \quad dp + \rho u du &=0 \tag{momentum} \label{momentumeqnQ1D}\\
    \quad c_p dT + udu &=0 \tag{energy} \label{energyeqnQ1D} \\
    \dfrac{dM}{M} &=\dfrac{du}{u}-\dfrac{1}{2} \dfrac{dT}{T} \tag{mach $\#$ differential relation} \label{machdiffQ1D} \\
    a^2 &= \dfrac{dp}{d\rho} \tag{sound speed isentropic}
\end{align}$$

Let's start with the mass and momentum equation to get a relationship between the velocity and area. I replace \( dp \) in the momentum equation with \( a^2 d \rho \) and obtain, 

$$\begin{align}
    a^2 d\rho + \rho u du &= 0 \notag\\
    \dfrac{d\rho}{\rho} &=-M^2 \dfrac{du}{u} \tag{$\rho-u$ relation} \label{rhourelation}
\end{align}$$

If I then plug the \ref{rhourelation} into the mass equation and rearrange, I get, 

$$\begin{equation}
    \boxed{\dfrac{dA}{A}=(M^2-1) \dfrac{du}{u}}  \tag{A-u relation}\label{A-u relation}
\end{equation}$$

My goal is to express \( du/u \) in terms of \( dM/M \). The key to doing this is to use the energy equation combined with the differential Mach relation. Dividing the energy equation by \( a^2=\gamma R T \) and rearranging, 

$$\begin{equation}
    \dfrac{dT}{T}=-(\gamma-1) M^2  \dfrac{du}{u} \tag{T-u relation} \label{T-u relation}
\end{equation}$$

Now, I use the \ref{T-u relation} in the mach number differential relation to express \( du/u \) in terms of  \( dM/M\)

$$\begin{equation}
    \dfrac{du}{u}=\dfrac{1}{1+\dfrac{1}{2}(\gamma-1) M^2} \dfrac{dM}{M} \tag{u-M relation} \label{u-M relation}
\end{equation}$$

Plug \ref{u-M relation} into \ref{A-u relation} and simplify,
$$\begin{equation}
    \boxed{\dfrac{dA}{A}=\dfrac{M^2-1}{1+\dfrac{\gamma-1}{2}M^2} \dfrac{dM}{M}} \tag{A-M relation} \label{A-M relation}
\end{equation}$$

This equation is to be integrated. Perform partial fraction decomposition and obtain, 
$$\begin{align*}
    \dfrac{dA}{A} &= \left[ \dfrac{\dfrac{\gamma+1}{2}M}{1+ \dfrac{\gamma-1}{2}M^2} - \dfrac{1}{M} \right] dM=f(M) \ dM \\
    &= \dfrac{1}{2}\dfrac{\gamma+1}{\gamma-1} d\left[\ln \left( 1+\dfrac{\gamma-1}{2}M^2\right)\right] - d \left[ \ln (M) \right] \\
    &= d \left\{ \ln \left[ \dfrac{1}{M} \left( 1+\dfrac{\gamma-1}{2}M^2\right)^{\frac{1}{2}\frac{\gamma+1}{\gamma-1}}\right] \right\}
\end{align*}$$
I call the term in the curly braces as \( F(M) \) and note that it is an anti-derivative of \( f(M) \). 
$$\begin{align*}
    F(M) = \ln \left[ \dfrac{1}{M} \left( 1+\dfrac{\gamma-1}{2}M^2\right)^{\frac{1}{2}\frac{\gamma+1}{\gamma-1}}\right] + C 
\end{align*}$$

Integrating,
$$\begin{align}
    \int_{A_\star}^{A} \dfrac{d \bar{A}}{\bar{A}} &= \int_{1}^{M} f(\bar{M}) \ d \bar{M} = F(M)-F(1) \notag \\
    \ln \dfrac{A}{A_\star} &= \ln \left[\dfrac{1}{M} \left(1+\dfrac{\gamma-1}{2}M^2 \right)^{\frac{1}{2} \frac{\gamma+1}{\gamma-1}} \right] -\ln \left[ \left(1+\dfrac{\gamma-1}{2} \right)^{\frac{1}{2}\frac{\gamma+1}{\gamma-1}} \right] \notag \\
    \dfrac{A}{A_\star}&=\dfrac{1}{M} \left[\dfrac{2}{\gamma+1} \left( 1+\dfrac{\gamma-1}{2}M^2\right) \right]^{\frac{1}{2} \frac{\gamma+1}{\gamma-1}} \notag
\end{align}$$

</div>
</details>


