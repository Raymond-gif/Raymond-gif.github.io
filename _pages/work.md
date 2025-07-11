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
\boxed{M_1^2 \sin^2 \beta -1 = \dfrac{\gamma+1}{2} M_1^2 \dfrac{\sin \beta \sin \theta}{\cos(\beta-\theta)}} \label{m1squared-1}
$$

</div>
</details>

##  Infinitely Weak Oblique Shock Approaching Mach Line

For small deflection angles \(\theta\), Eq. \ref{m1squared-1} approximately becomes,

$$
\begin{equation}
M_1^2 \sin^2 \beta-1 \approx \left[\dfrac{\gamma+1}{2}M_1^2 \tan \beta \right] \theta \label{M1^2approx}
\end{equation}
$$

Plugging Eq. \ref{M1^2approx} into Eq. \ref{pressureratio}, the pressure ratio becomes, for small deflection angles,

$$\begin{equation}
\dfrac{p_2}{p_1}\approx 1 + (\gamma M_1^2 \tan \beta) \theta \label{weakpressureratio}
\end{equation}$$

As the flow deflection becomes smaller, \(\beta\) approaches the Mach angle, \(\mu\). Therefore, \(\tan \beta \approx \tan \mu=1/\sqrt{M_1^2-1}\). 

<div style="background-color: #ebf4ff; border: 2px solid #2c5282; padding: 12px; border-radius: 6px; max-width: 600px; margin: 1em auto;">
  <strong>Pressure Ratio Across an Infinitely Weak Oblique Shock: </strong>
  
  <p style="text-align: center; font-size: 1.1em; margin-top: 0.5em;">

$$\begin{equation}
    \boxed{\dfrac{p_2}{p_1}=1+\dfrac{\gamma M_1^2}{\sqrt{M_1^2-1}} \theta, \quad \dfrac{\Delta p}{p_1}=\dfrac{\gamma M_1^2}{\sqrt{M_1^2-1}} \theta}, \text{ for small perturbations (small \theta)}  
    \label{weakpressureratiofinal}
\end{equation}
$$
  </p>
</div>

\begin{figure}[htbp]
    \centering
    \includegraphics[width=0.5\linewidth]{obliquemach.png}
    \caption{Mach wave (blue) and oblique shock (red) for some given flow deflection}
    \label{fig:machobliqueshock}
\end{figure}

\begin{tcolorbox}[
  colback=yellow!10!white,  % Pale yellow background
  colframe=yellow!80!black, % Dark yellowish frame for contrast
  title=\raggedright{Relationship Between $\epsilon$ and $\theta$}, % Title of the section
  sharp corners,             % Sharp corners for the box
  boxrule=0.8mm,             % Thin frame
  fonttitle=\bfseries\LARGE, % Bold and large title
  coltitle=black,   
  breakable 
]
\small
Looking at fig. \ref{fig:machobliqueshock}, we define the difference between the oblique and Mach angle as $\epsilon$.
\[\beta = \mu + \epsilon\]
\begin{align*}
\sin \beta = \sin (\mu + \epsilon)= \sin \mu \cos \epsilon + \cos \mu \sin \epsilon &\approx \sin \mu + \epsilon \cos \mu \\ & \approx \dfrac{1}{M_1}+\dfrac{\epsilon}{M_1} \sqrt{M_1^2-1}
\end{align*}
\begin{align}
    M_1 \sin \beta &\approx 1+ \epsilon \sqrt{M_1^2-1} \nonumber\\
    M_1^2 \sin^2 \beta &\approx 1+2\epsilon \sqrt{M_1^2-1} + \cancel{\epsilon^2 (M_1^2-1)} \nonumber \\
    \Aboxed{M_1^2 \sin^2 \beta -1 &= 2 \epsilon \sqrt{M_1^2-1}}, \text{ for small perturbations} \label{M1^2epsilon}
\end{align}

Setting the right hand sides of Eqs. \ref{M1^2approx} and \ref{M1^2epsilon} equal to each other, I obtain 

\begin{align}
    2\epsilon \sqrt{M_1^2-1}&=\dfrac{\gamma+1}{2} \dfrac{M_1^2}{\sqrt{M_1^2-1}} \theta \\
    \Aboxed{\epsilon&= \dfrac{\gamma+1}{4}\dfrac{M_1^2}{M_1^2-1} \theta} \label{epsilontheta}
\end{align}
\end{tcolorbox}

Eq. \ref{epsilontheta} leads us to conclude that $\epsilon$ is proportional to (on the same order of) $\theta$. That is, for an infinitely weak oblique shock, the difference in the shock and Mach angle is on the same order of the flow deflection angle. 

Recall from the geometry of oblique shock theory (Eqs. \ref{momentum}, \ref{geometry}),
\begin{equation}
\boxed{\dfrac{V_2^2}{V_1^2}= \dfrac{\cos^2 \beta}{\cos^2 (\beta-\theta)}} \label{v2/v1 squared relation}
\end{equation}

Rearranging Eq. \ref{M1^2epsilon},
\begin{align}
    \sin^2 \beta&=\dfrac{1+ 2\epsilon \sqrt{M_1^2-1}}{M_1^2} \nonumber \\
    \cos^2 \beta &= 1-\sin^2 \beta=1-\dfrac{1}{M_1^2} \left[1+2\epsilon\sqrt{M_1^2-1}\right] \nonumber \\
    \cos^2 \beta &= \dfrac{M_1^2-1}{M_1^2} \left[ 1- \dfrac{2 \epsilon}{\sqrt{M_1^2-1}}\right]
    \label{cos2beta}
\end{align}

Now, we solved for the numerator of Eq. \ref{v2/v1 squared relation}. What remains is to solve for the denominator. I follow a similar procedure in determining $\cos^2 (\beta-\theta)$ as $\cos^2 \beta$. 
\[\sin (\beta -\theta)= \sin[\mu + (\epsilon-\theta)]= \sin \mu \cos (\epsilon - \theta) + \cos \mu \sin (\epsilon -\theta)\]

In the small angle approximation, $\cos (\epsilon-\theta) = 1$ and $\sin (\epsilon - \theta) = \epsilon -\theta$, 
\[\sin(\beta-\theta) = \sin \mu + (\epsilon-\theta) \cos \mu = \dfrac{1}{M_1}+(\epsilon-\theta)\dfrac{\sqrt{M_1^2-1}}{M_1}\]

Squaring and ignoring all higher order terms,
\begin{align}
    \sin^2 (\beta-\theta) &= \dfrac{1}{M_1^2}\left[ 1+ 2(\epsilon - \theta) \sqrt{M_1^2-1}\right] \nonumber \\
    \cos^2 (\beta -\theta) &=1-\sin^2(\beta -\theta)=1-\dfrac{1}{M_1^2} \left[ 1+ 2 (\epsilon - \theta) \sqrt{M_1^2-1}\right] \nonumber \\
    \cos ^2 (\beta - \theta) &= \dfrac{M_1^2-1}{M_1^2} \left[ 1-\dfrac{2(\epsilon - \theta)}{\sqrt{M_1^2-1}}\right]
    \label{cos^2 beta -theta}
\end{align}

Substituting Eqs. \ref{cos2beta} and \ref{cos^2 beta -theta} into Eq. \ref{v2/v1 squared relation}, and using Eq. \ref{epsilontheta} to express $\epsilon$ in terms of $\theta$, we obtain $V_2/V_1$ as a function of $\theta$.

\begin{equation}
    \boxed{\dfrac{V_2}{V_1}=\sqrt{\dfrac{1-\dfrac{\gamma+1}{2} \dfrac{M_1^2}{(M_1^2-1)^{3/2}}\theta}{1-\dfrac{2\theta}{\sqrt{M_1^2-1}} \left[ \dfrac{\gamma + 1}{4} \dfrac{M_1^2}{M_1^2-1}-1\right]}}}
    \label{V2V1functiontheta}
\end{equation}

Eq. \ref{V2V1functiontheta} is of the form $f(\theta) = \sqrt{\dfrac{1+A \theta}{1+B \theta}}$, where $A= - \dfrac{\gamma+1}{2} \dfrac{M_1^2}{(M_1^2-1)^{3/2}}$ 

and $B=\dfrac{-2}{\sqrt{M_1^2-1}} \left[ \dfrac{\gamma+1}{4}\dfrac{M_1^2}{M_1^2-1}-1\right]$.

If we do a Taylor expansion and neglect all higher order terms, we obtain the velocity ratio across an infinitely weak oblique shock. 

\begin{tcolorbox}[colback=blue!5!white, colframe=blue!75!black, title=Velocity Ratio Across an Infinitely Weak Oblique Shock]
\begin{equation}
    \boxed{\dfrac{V_2}{V_1}=1-\dfrac{\theta}{\sqrt{M_1^2-1}}, \quad \dfrac{\Delta V}{V_1}=-\dfrac{\theta}{\sqrt{M_1^2-1}}}
    \label{velocityratioveryweakobliqueshock}
\end{equation}
\end{tcolorbox}

What does this tell us? For a very small flow deflection angle $\theta$, we see that the oblique shock approaches the Mach wave, and we can calculate the velocity and pressure change from Eqs. \ref{weakpressureratiofinal} and \ref{velocityratioveryweakobliqueshock}. 

It can be shown that $\Delta s \sim ({\Delta p}/{p_1})^3\sim\theta^3$, but I will omit the proof here. You can derive it by doing a Taylor expansion on the entropy change across a shock. Notice that if the flow deflection is small, the change in entropy is even smaller, so the flow can be considered nearly isentropic. 

Imagine that instead of turning the flow abruptly from $0^\circ$ to $\theta^\circ$ via an oblique shock, we turn the flow gradually through a series of very weak, nearly isentropic Mach waves.

\begin{figure}[htbp]
    \centering
    \includegraphics[width=0.5\linewidth]{successive.png}
    \caption{Top: Flow turning through successive isentropic compression waves, Bottom: Flow abruptly turning through oblique shock}
    \label{fig:successive}
\end{figure}

We can solve for the flowfield properties of an isentropic compression caused by a smooth, continuous boundary by approximating the boundary with straight line segments, with infinitely weak oblique shocks at each ``corner". 

This sensation should be familiar! Yes, this should remind you of Calculus, approximating a continuous curve with discrete line segments! As $n\to\infty$, $\Delta \theta \to d\theta$, and $\Delta \theta \to d \theta$, so that Eq. \ref{velocityratioveryweakobliqueshock} becomes a differential equation, 

\begin{equation}
    \dfrac{dV}{V}=-\dfrac{d\theta}{\sqrt{M^2-1}}
    \label{diffeqn_prandtl_meyer}
\end{equation}

It is useful to rewrite Eq. \ref{diffeqn_prandtl_meyer} in terms of Mach number. I do this by differentiating $M=V/a$ to obtain Eq. \ref{Mach number definition}. By manipulating the differential adiabatic energy equation $c_p dT + V dV =0$, I also obtain Eq. \ref{differentialadiabaticenergyeqn}.

\begin{equation}
    \dfrac{dV}{V}=\dfrac{dM}{M} + \dfrac{1}{2} \dfrac{dT}{T}
    \label{Mach number definition}
\end{equation}

\begin{equation}
    \dfrac{dT}{T}+(\gamma-1)M^2 \dfrac{dV}{V}=0
    \label{differentialadiabaticenergyeqn}
\end{equation}

Eqs. \ref{Mach number definition}-\ref{differentialadiabaticenergyeqn} together yield, 

\begin{equation}
    \dfrac{dV}{V}=\dfrac{1}{1+\dfrac{\gamma-1}{2}M^2} \dfrac{dM}{M}
    \label{dVV=dMM}
\end{equation}

Plug Eq. \ref{dVV=dMM} into Eq. \ref{diffeqn_prandtl_meyer},

\begin{tcolorbox}[colback=blue!5!white, colframe=blue!75!black, title=Differential Form of Prandtl-Meyer Function]
\begin{equation}
    \boxed{d\nu =-d\theta = \dfrac{\sqrt{M^2-1}}{1+\dfrac{\gamma-1}{2}M^2 } \dfrac{dM}{M}} 
    \label{PrandtlMeyerFinal}
\end{equation}
\end{tcolorbox}



