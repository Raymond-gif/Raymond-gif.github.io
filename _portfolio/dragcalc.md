---
title: "Drag Calculation of Airplane Project (Work in Progress)"
excerpt: "Drag is a fundamental aerodynamic force that acts on an airplane in flight. Determining this value is crucial for determining the thrust output required by the airplane engine in order to maintain steady flight. In this report, I calculate the total incompressible drag acting on an airplane, including the parasitic and induced drag. To calculate the drag of the entire airplane, it is necessary to calculate the drag of the individual components, such as the wing, fuselage, etc, and sum them up."
order: 1
layout: splash
image: /images/iso.png
header:
  overlay_color: "#2a4d8f"           
  hero_title: "Drag Calculation of Airplane Project"
  hero_excerpt: "Drag is a fundamental aerodynamic force that acts on an airplane in flight. Determining this value is crucial for determining the thrust output required by the airplane engine in order to maintain steady flight. In this report, I calculate the total incompressible drag acting on an airplane, including the parasitic and induced drag. To calculate the drag of the entire airplane, it is necessary to calculate the drag of the individual components, such as the wing, fuselage, etc, and sum them up."
---



<div class="equation-box">
  <h3>Airplane Specifications</h3>
  <div>
 $$      \begin{align*}
           b_{\text{wing}} &= 96 \text{ ft} \\ 
           c_{r_o,\text{wing}} &= 20 \text{ ft} \\ 
           \sigma_{\text{wing}} &= 0.22 \\
           \Lambda_{c/4} &= 8^{o} \\
           L_f &= 103 \text{ ft} \\
           D_f &= 13 \text{ ft} \\
           S_{\text{wet}_f} &= 3365.274 \text{ ft}^2
        \end{align*}$$
  </div>
</div>

## Introduction
###  Motivation

Drag is a fundamental aerodynamic force that acts on an airplane in flight. Determining this value is crucial for determining the thrust output required by the airplane engine in order to maintain steady flight. The total incompressible drag acting on an airplane consists of two parts, the parasitic and induced drag. To calculate the drag of the entire airplane, it is necessary to calculate the drag of the individual components, such as the wing, fuselage, etc, and sum them up.  

###  Flight Conditions
The plane is flying under the following conditions, given as density, temperature, and absolute viscosity, respectively, 

$$\begin{align*}
    \rho &= 0.0008754 \  \dfrac{\text{slugs}}{\text{ft}^3} \\
    T &= 400^{o} \ R \\
    \mu &= 3.025\times10^{-7} \ \dfrac{\text{lb} \cdot \text{s}}{\text{ft}^2} \\
    \text{Flight Velocity}: \ v &= 765 \text{ ft/s}
\end{align*}$$

###  Calculating Parasitic Drag

The parasitic drag coefficient of the total aircraft is calculated with the following equation, with the subscript i denoting each aircraft component,

$$\begin{equation} \label{parasitedragcoeff}
    \boxed{C_{D_p} = \sum_{\text{i}}{\dfrac{K_iC_{f,i} S_{\text{wet},i}}{S_{\text{ref}}}}}
\end{equation}$$

where \\(K_i\\) is the form factor accounting for pressure drag, \\(C_{f,i}\\) is the skin friction coefficient, \\(S_{\text{wet},i}\\) is the wetted area, and \\(S_{\text{ref}}\\) is the wing planform area. \\(C_{f,i}\\) is a function of Reynolds number, and the graph is digitized in Fig. \ref{fig:skinfriction} in section \ref{plotting}. For a wing, the characteristic length is the mean aerodynamic chord or m.a.c, which is computed as, 

$$\begin{equation} \label{mac}
    \text{m.a.c.} = \dfrac{2}{3}\biggl(C_R+C_T-\dfrac{C_RC_T}{C_R+C_T} \biggr)
\end{equation}$$

### Calculating Induced Drag

Induced drag is caused by trailing vortices that form at the tip of a finite wing and is a byproduct of lift. The induced drag coefficient is calculated using,

$$\begin{equation} \label{induceddragcoeff}
    \boxed{C_{D_i} = \dfrac{C_L^2}{\pi \cdot AR \cdot e} }
\end{equation},$$

where \\(C_L\\) is the lift coefficient, \\(AR \equiv \dfrac{\text{span}^2}{\text{reference area}} =  b^2/S_{\text{ref}}\\), and \\(e\\) is the Oswald's efficiency factor. 

###  Calculating Total Drag

$$\begin{equation} \label{totaldragequation}
    \boxed{C_{D_{tot}} = \underbrace{C_{D_p}}_{\text{parasite}} + \underbrace{\dfrac{C_L^2}{\pi\cdot AR\cdot e}}_{\text{induced drag, due to lift}} + \underbrace{\cancelto{0}{\Delta{C_{DC}}}}_{\text{compressibility effects}}}
\end{equation}$$

Compressibility effects are ignored for the purposes of this design report.

## Results

###  Plots \label{plotting}

Figure \ref{fig:main} and \ref{fig:l_d} were graphed based on my original constants. The MATLAB code used to graph this is shown in section \ref{MATLABCODE}. 

<div style="display: flex; justify-content: center; gap: 1rem;">

  <!-- Subfigure 1 -->
  <figure style="flex: 1; text-align: center;">
    <img src="/images/fig1.jpg" alt="Drag as a Function of Velocity" style="width:100%;">
    <figcaption>(a)</figcaption>
  </figure>

  <!-- Subfigure 2 -->
  <figure style="flex: 1; text-align: center;">
    <img src="/images/fig2.jpg" alt="Lift-To-Drag Ratio as a Function of Velocity" style="width:100%;">
    <figcaption>(b)</figcaption>
  </figure>

</div>

<figcaption style="text-align:center; margin-top: 1rem;">
(a) Drag as a Function of Velocity; (b) Lift-To-Drag Ratio as a Function of Velocity
</figcaption>

The rest of the figures were digitized from \cite{Shevell_1983}. In particular, for Fig. \ref{fig:surfaceform}, equation \ref{digitaleqn} was used.

$$\begin{equation}
\begin{split} \label{digitaleqn}
    K &= 1 + Z(t/c) + 100(t/c)^4 \\
    Z &= \dfrac{(2-M_0^2)\cos{(\Lambda_{C/4}})}{\sqrt{1-M_0^2\cos^2(\Lambda_{C/4})}}
    \end{split}
\end{equation}
$$

<!-- Figure 3 -->
<p align="center">
  <img src="/images/fig3.jpg" 
       alt="Skin Friction Coefficient as a Function of RN" 
       width="40%" style="border:1px solid #000;">
</p>

<p align="center">
  <strong>Figure 3:</strong> Skin Friction Coefficient \(C_f\) as a Function of RN. 
  Adapted from Shevell (1983).
</p>

<!-- Figure 4 -->
<p align="center">
  <img src="/images/fig4.jpg" 
       alt="K as a Function of Λc/4 and t/c for Aerodynamic Surfaces" 
       width="40%" style="border:1px solid #000;">
</p>

<p align="center">
  <strong>Figure 4:</strong> (For Aerodynamic Surfaces) K as a Function of \(\Lambda_{c/4}\) and \(t/c\). 
  Adapted from Shevell (1983).
</p>

<!-- Figure 5 -->
<p align="center">
  <img src="/images/fig5.jpg" 
       alt="K as a Function of Fineness Ratio for Bodies" 
       width="40%" style="border:1px solid #000;">
</p>

<p align="center">
  <strong>Figure 5:</strong> (For Bodies) K as a Function of Fineness Ratio. 
  Adapted from Shevell (1983).
</p>

<!-- Figure 6 -->
<p align="center">
  <img src="/images/fig6.jpg" 
       alt="Oswald Efficiency as a Function of Aspect Ratio and Parasitic Drag Coefficient" 
       width="40%" style="border:1px solid #000;">
</p>

<p align="center">
  <strong>Figure 6:</strong> Oswald Efficiency as a Function of Aspect Ratio and Parasitic Drag Coefficient. 
  Adapted from Shevell (1983).
</p>

###  Hand Calculations
Here are the aircraft constants for my specific airplane: 

$$    \begin{equation} \label{my constants}
        \boxed{    
        \begin{split}
           b_{\text{wing}} &= 96 \text{ ft} \\ 
           c_{r_o,\text{wing}} &= 20 \text{ ft} \\ 
           \sigma_{\text{wing}} &= 0.22 \\
           \Lambda_{c/4} &= 8^{o} \\
           L_f &= 103 \text{ ft} \\
           D_f &= 13 \text{ ft} \\
        \end{split} }
        \end{equation}$$

From SOLIDWORKS, the following values were also obtained for my specific aircraft. This is discussed and shown more in section \ref{solidworkssection}. 

$$\begin{equation*}
\boxed{\begin{split}
    \text{Wetted Area of Wing}& \ \ \  S_{\text{wet}_1} &= 1914.679 \ \text{ft}^2 \\
    \text{Wing Planform Area}&\ \ \ S_{\text{ref}} &= 1172.890 \ \text{ft}^2 \\
    \text{Average t/c of Wing}& \ \ \  t/c &= 0.1432 \\ 
\end{split}}
\end{equation*}$$

For my calculations, I will use the following numbers to denote the specific components of the airplane. 

__1 = Wing, 2 = Fuselage, 3 = Horizontal Tail, 4 = Vertical Tail, 5 =
Pylons, 6 = Nacelles__ 

$$\begin{align*}
    C_{T,1} &= (\sigma_{1}) \biggl(\underbrace{C_{r_o,1}}_{\text{centerline root chord}}\biggr) = (0.22)(20 \text{ ft}) = 4.4 \text{ ft} \\
     \text{m.a.c.}_{\text{exposed, 1}} &= \dfrac{2}{3}\biggl(\underbrace{C_{R1}}_{\text{exposed}}+C_T-\dfrac{C_{R1}C_T}{C_{R1}+C_T} \biggr) \\
    &= \dfrac{2}{3} \biggl(17.9196 + 4.4 - \dfrac{17.9196\cdot4.4}{17.9196+4.4} \biggr) \text{ ft} \\ &= 12.525 \text{ ft} \\ 
    RN_1 &= \dfrac{(\rho)(v)(\text{m.a.c.})}{\mu} = \dfrac{\left(0.0008754 \ \dfrac{\text{slugs}}{\text{ft}^3} \right) \left(765 \ \dfrac{\text{ft}}{s} \right) \left(12.525 \ \text{ft}\right)}{\left(3.025\times10^{-7} \dfrac{\ \text{lb} \cdot \text{s}}{\text{ft}^2} \right)} = 2.7728 \times 10^7
\end{align*}$$

Using Fig. \ref{fig:skinfriction}, it was found that \\(C_{f,1} \approx 2.8 \times 10^{-3}\\). To find the form factor K, Fig. \ref{fig:surfaceform} was used. Using SOLIDWORKS, the average thickness-to-chord ratio is \\(t/c = 0.1433\\). Thus, the form factor K can be calculated using sweep angle and t/c, resulting in  \\( K_1 = 1.32 \\). 

$$\begin{equation*}
    C_{D_{p_1}} = \dfrac{K_1 C_{f_{1}} S_{\text{wet}_1}}{S_{\text{ref}}} = \dfrac{(1.32)(2.8\times10^{-3})(1914.6789) \ \text{ft}}{1172.890 \ \text{ft}} = \underline{6.034 \times 10^{-3}}
\end{equation*}$$

Moving on to the fuselage, the length and diameter of the fuselage are obtained from my unique constants in (\ref{my constants}). The fineness ratio is then \\(L_f/D_f = 7.923\\), and from Fig. \ref{fig:bodyform}, \\(K_2 = 1.16\\).  Now, to calculate Reynolds number, 

$$\begin{equation*}
    RN_2 = \dfrac{\rho v L_f}{\mu} = \dfrac{\left(0.0008754 \ \dfrac{\text{slugs}}{\text{ft}^3} \right) \left(765 \ \dfrac{\text{ft}}{\text{s}} \right) \left(103 \ \text{ft}\right)}{3.025\times10^{-7} \ \dfrac{\text{lb} \cdot \text{s}}{\text{ft}^2}} = 2.280 \times 10^8 
\end{equation*}$$

To calculate the wetted area, the following formula is used,

$$\begin{equation*}
    S_{\text{wet}_2} = (0.8\pi)(D_f)(L_f) = (0.8\pi)(13 \text{ft})(103 \ \text{ft}) = 3365.274 \  \text{ft}^2
\end{equation*}$$

From Fig. \ref{fig:skinfriction}, \\(C_{f_{2}} = 2\times10^{-3}\\). 

$$\begin{gather*}
    C_{D_{p2}} = \dfrac{K_2 C_{f_{2}} S_{\text{wet}_2}}{S_{\text{ref}}} = \dfrac{(1.16)(2\times10^{-3})(3365.274 \ \text{ft}^2)}{1172.890 \ \text{ft}^2} = \underline{6.657 \times 10^{-3}}
\end{gather*}$$

Now, let's consider the horizontal tail. Similar to the wing, 

$$\begin{align*}
    C_{T3} &= \sigma_3 \cdot C_{R3} = (0.35)(11.1 \ \text{ft}) = 3.885 \ \text{ft} \\
   \text{m.a.c.}_{\text{exposed, 3}} &= \dfrac{2}{3}\biggl(C_{R3}+C_{T3}-\dfrac{C_{R3}C_{T3}}{C_{R3}+C_{T3}} \biggr) \\ &= \dfrac{2}{3} \biggl(11.1 + 3.885 - \dfrac{11.1\cdot3.885}{11.1+3.885} \biggr) \text{ ft} \\
    &= 8.071 \text{ ft}  
\end{align*}
$$

With the m.a.c. known, it is possible to calculate Reynolds number.

$$\begin{align*}
    RN_3 &= \dfrac{(\rho)(v)(\text{m.a.c.}_3)}{\mu} = \dfrac{\left(0.0008754 \ \dfrac{\text{slugs}}{\text{ft}^3} \right) \left(765 \ \dfrac{\text{ft}}{s} \right) \left(8.071 \ \text{ft}\right)}{\left(3.025\times10^{-7} \dfrac{\ \text{lb} \cdot \text{s}}{\text{ft}^2}\right)} = 1.7868 \times 10^7 \\
    C_{f_{3}} &= 3.1 \times 10^{-3} \\
    K_3 &= 1.16 \\ 
    S_{\text{wet}_3} &= (2)(\text{exposed planform area})(\underbrace{1.02}_{\text{curvature}}) = (2)(261 \  \text{ft}^2)(1.02) = 532.44 \ \text{ft}^2 \\
     C_{D_{p3}} &= \dfrac{K_3 C_{f_{3}} S_{\text{wet}_3}}{S_{\text{ref}}} = \dfrac{(1.16)(3.1\times10^{-3})(532.44 \ \text{ft}^2)}{1172.890 \ \text{ft}^2} = \underline{1.632 \times 10^{-3}}
\end{align*}
$$

Now, let's consider the vertical tail. 

$$\begin{equation*}
\begin{split}
    C_{T4} &= \sigma_4 \cdot C_{R4} = (0.8)(15.5 \ \text{ft}) = 12.4 \ \text{ft} \\
     \text{m.a.c.}_{\text{exposed, 4}} &= \dfrac{2}{3}\biggl(C_{R4}+C_{T4}-\dfrac{C_{R4}C_{T4}}{C_{R4}+C_{T4}} \biggr) \\ &= \dfrac{2}{3} \biggl(15.5 + 12.4 - \dfrac{15.5\cdot12.4}{15.5+12.4} \biggr) \text{ ft} \\ &= 21.011 \text{ ft} \\ 
\end{split}
\end{equation*}$$

With the m.a.c. known, it is possible to calculate Reynolds number.

$$\begin{align*}
    RN_4 &= \dfrac{(\rho)(v)(\text{m.a.c.}_4)}{\mu} = \dfrac{\left(0.0008754 \ \dfrac{\text{slugs}}{\text{ft}^3} \right) \left(765 \ \dfrac{\text{ft}}{s} \right) \left(21.011 \ \text{ft}\right)}{ \left(3.025\times10^{-7} \dfrac{\ \text{lb} \cdot \text{s}}{\text{ft}^2} \right)} = 4.651 \times 10^7 \\
    C_{f_{4}} &= 2.5 \times 10^{-3} \\
    K_4 &= 1.125 \\ 
    S_{\text{wet}_4} &= (2)(\text{exposed planform area})(\underbrace{1.02}_{\text{curvature}}) = (2)(161 \  \text{ft}^2)(1.02) = 328.44 \ \text{ft}^2 \\
     C_{D_{p4}} &= \dfrac{K_4 C_{f_{4}} S_{\text{wet}_4}}{S_{\text{ref}}} = \dfrac{(1.125)(2.5\times10^{-3})(328.44 \ \text{ft}^2)}{1172.890 \ \text{ft}^2} = \underline{7.876 \times 10^{-4}}
\end{align*}
$$

Now, for the pylons, 

$$\begin{align*}
    RN_5 &= \dfrac{(\rho)(v)(\text{m.a.c.}_5)}{\mu} = \dfrac{\left(0.0008754 \ \dfrac{\text{slugs}}{\text{ft}^3} \right) \left(765 \ \dfrac{\text{ft}}{s} \right) \left(16.2 \ \text{ft} \right)}{ \left(3.025\times10^{-7} \dfrac{\ \text{lb} \cdot \text{s}}{\text{ft}^2} \right)} = 3.586 \times 10^7 \\
    C_{f_{5}} &= 2.75 \times 10^{-3} \\
    K_5 &= 1.12 \\ 
    S_{\text{wet}_5} &= 117 \ \text{ft}^2\\
     C_{D_{p5}} &= \dfrac{K_5 C_{f_{5}} S_{\text{wet}_5}}{S_{\text{ref}}} = \dfrac{(1.12)(2.75\times10^{-3})(117 \ \text{ft}^2)}{1172.890 \ \text{ft}^2} = \underline{3.072 \times 10^{-4}}
\end{align*}$$

Now, for the nacelles. In terms of calculation, this is similar to the fuselage case. From Fig. \ref{fig:bodyform}, \\( \underline{K_6 = 1.28} \\) corresponds to a fineness ratio of 5.0. \\(S_{\text{wet}_6} = 455\\) is given.

$$\begin{align*}
    RN_6 &= \dfrac{\rho v L_n}{\mu} = \dfrac{ \left(0.0008754 \ \dfrac{\text{slugs}}{\text{ft}^3} \right) \left(765 \ \dfrac{\text{ft}}{\text{s}} \right) \left(16.8 \ \text{ft} \right)}{3.025\times10^{-7} \ \dfrac{\text{lb} \cdot \text{s}}{\text{ft}^2}} = 3.719 \times 10^7 \\
    C_{f_{6}} &= 2.75 \times 10^{-3} \\
    C_{D_{p6}} &= \dfrac{K_6 C_{f_{6}} S_{\text{wet}_6}}{S_{\text{ref}}} = \dfrac{(1.28)(2.75\times10^{-3})(455 \ \text{ft}^2)}{1172.890 \ \text{ft}^2} = \underline{1.3655\times10^{-3}} 
\end{align*}$$

For the total \textbf{parasite} coefficient of drag, all contributions to the drag from the various components are summed up,

$$\begin{align*}
        C_{D_{p}} = \sum_{i=1}^6 {C_{D_{p,i}}} = (6.034\times10^{-3} + 6.657\times10^{-3} + 1.632\times 10^{-3} + \\ 7.876\times10^{-4} + 3.072\times10^{-4} +1.3655\times10^{-3}) \\
        = {0.0167}
\end{align*}$$

From the parasitic drag coefficient, the actual parasitic drag is,

$$\begin{equation}
\boxed{
\begin{split}
    D_p = (C_{D_{p}}) \left(\dfrac{1}{2} \rho_a v^2 \right)(S_{\text{ref}}) = (0.0167)(0.5) \left(0.0008754 \  \dfrac{\text{slugs}}{\text{ft}^3} \right) \left(765 \ \dfrac{\text{ft}}{s} \right)^2(1172.890 \ \text{ft}^2) \\ = \textbf{5017.336 lb}
\end{split} } 
\end{equation}$$

Now, it is time to calculate the induced drag. For that, it is assumed that the weight of aircraft is \\(98,000\\) lbs. At steady level flight, this is equal to the lift force.

$$\begin{align*}
    C_L &= \dfrac{L}{\dfrac{1}{2}\rho_a v^2 S_{\text{ref}}} = \dfrac{98000 \ \text{lbs}}{(0.5) \left(0.0008754 \  \dfrac{\text{slugs}}{\text{ft}^3} \right) \left(765 \dfrac{\text{ft}}{\ \text{s}} \right)^2(1172.890 \ \text{ft}^2) } = {0.3262} \\
    AR &= \dfrac{b^2}{S_{\text{ref}}} = \dfrac{(96 \ \text{ft})^2}{1172.890 \ \text{ft}^2} = {7.858}
\end{align*}$$

With \\(C_L\\) and aspect ratio known, it is possible to determine the Oswald's efficiency factor, e, using Fig. \ref{fig: oswald}, which turns out to be \\(\underline{e = 0.8384}\\).

$$\begin{equation*}
    \underbrace{C_{D_{i}}}_{\text{induced drag}} = \ \dfrac{C_L^2}{\pi\cdot AR \cdot e} = \dfrac{(0.3262)^2}{(\pi)(7.858)(0.8384)} = {0.00514}
\end{equation*}
$$

The actual induced drag is, 

$$\begin{equation}
\boxed{
\begin{split}
    D_{\text{induced}} &= (C_{D_{i}}) \left(\dfrac{1}{2} \rho_a v^2 \right)(S_{\text{ref}}) \\ &= (0.00514)(0.5) \left(0.0008754 \  \dfrac{\text{slugs}}{\text{ft}^3} \right) \left(765 \ \dfrac{\text{ft}}{s} \right)^2(1172.890 \ \text{ft}^2) \\ &= \textbf{1544.258 lb}
\end{split} } 
\end{equation}$$
Now, the total drag coefficient is determined using Equation (\ref{totaldragequation}), 

$$\begin{equation*}
   {C_{\text{D,total}} = C_{D_{p}} + C_{D,\text{induced}} = 0.0167 + 0.00514 = 0.02184}
\end{equation*}
$$

$$\begin{equation}
    \boxed{D_{\text{total}} = D_{\text{p}} + D_{\text{induced}} = 5017.336 \ \text{lb} + 1544.258 \ \text{lb} = \textbf{6561.594 lb}}
\end{equation}$$

###  Comparison with MATLAB Data

Now that the hand calculations are concluded, let's compare this with the MATLAB calculations. The MATLAB calculation was done using Fig. \ref{fig:main}. To get the exact point when \\(V = 765 \  \text{ft/s}\\), a while loop was used, with the results shown below.

|                         | **Hand Calculations** | **MATLAB Calculations** |
|-------------------------|--------------------|-----------------------|
| **Parasitic Drag**      | 5017 lbs           | 5030 lbs              |
| **Induced Drag**        | 1544 lbs           | 1544 lbs              |
| **Total Drag**          | 6561 lbs           | 6574 lbs              |

*Comparison of Hand Calculations and MATLAB Calculations for Flight Condition V = 765 ft/s*

###  Optimum Operating Condition
The best operating condition for this unique airplane, according to Fig. \ref{fig:main}, is at \\( \boxed{V = 565 \ \text{ft/s}} \\), which is when drag (and thrust required) is minimum, with **a total drag of 5708 lbs**. This is also when the parasite drag and induced drag are equal. 

## Conclusion
###  Behavior of Drag
As shown in Fig. \ref{fig:main}, the behavior of total drag is approximately parabolic with increasing velocity. As such, there is an optimum velocity to fly at, which occurs when the total drag is minimum, or when the L/D is maximum as in Fig. \ref{fig:l_d}. To see why this is, let us examine the equations for total drag, where \\(q = (1/2)\rho v^2\\),

$$\begin{equation}
\begin{split} \label{totaldragexplanation}
    C_D &= C_{D_{p}} + C_{D_{i}} = \dfrac{KC_fS_{\text{wet}}}{S_{\text{ref}}} + \dfrac{C_L^2}{\pi \cdot AR \cdot e} \\ 
    D &= qS_{\text{ref}}C_{D} = \underbrace{qKC_fS_{\text{wet}}}_{\text{parasitic}} + \underbrace{qS_{\text{ref}}\dfrac{\left(\dfrac{L}{qS_{\text{ref}}} \right)^2}{\pi \cdot AR \cdot e}}_{\text{induced}}
\end{split}
\end{equation}$$

Equation (\ref{totaldragexplanation}) shows that the parasitic drag is proportional to q, and the induced drag is inversely proportional to \\(q^2\\). Since \\(q = \rho v^2 /2 \\), this is why parasitic drag increases with increasing velocity, while induced drag decreases. 

In the case of my unique airplane, it is advantageous to slow down because, at the flight speed of 765 ft/s, parasitic drag dominates. By slowing down, parasitic drag decreases. 

## Appendix
###  SOLIDWORKS 

<!-- Figure: Wing and Fuselage Views -->
<p align="center">
  <span style="display:inline-block; text-align:center; margin:0 0.5rem;">
    <img src="/images/iso.png" alt="Isometric View of Wing and Fuselage" width="45%" style="border:1px solid #000; display:block; margin:auto;">
    <br>(a)
  </span>
  <span style="display:inline-block; text-align:center; margin:0 0.5rem;">
    <img src="/images/topdownview.png" alt="Top-Down View Displaying Wing Dimensions" width="45%" style="border:1px solid #000; display:block; margin:auto;">
    <br>(b)
  </span>
</p>

<p align="center">
  <span style="display:inline-block; text-align:center; margin:0 0.5rem;">
    <img src="/images/exposedRC.png" alt="Exposed Root Chord" width="40%" style="border:1px solid #000; display:block; margin:auto;">
    <br>(c)
  </span>
  <span style="display:inline-block; text-align:center; margin:0 0.5rem;">
    <img src="/images/wetarea.png" alt="Wetted Area of Wing" width="55%" style="border:1px solid #000; display:block; margin:auto;">
    <br>(d)
  </span>
</p>

<p align="center">
  <strong>Figure 1:</strong> (a) Isometric View of Wing and Fuselage; 
  (b) Top-Down View Displaying Wing Dimensions; 
  (c) Exposed Root Chord; 
  (d) Wetted Area of Wing \(S_{\text{wet}_1}\)
</p>

<!-- Figure: Wing Planform and Fuselage Measurements -->
<p align="center">
  <span style="display:inline-block; text-align:center; margin:0 0.5rem;">
    <img src="/images/projection.png" alt="Wing Planform Area S_ref" width="65%" style="border:1px solid #000; display:block; margin:auto;">
    <br>(a)
  </span>
  <span style="display:inline-block; text-align:center; margin:0 0.5rem;">
    <img src="/images/t_c.png" alt="Average t/c ratio at m.a.c." width="45%" style="border:1px solid #000; display:block; margin:auto;">
    <br>(b)
  </span>
  <span style="display:inline-block; text-align:center; margin:0 0.5rem;">
    <img src="/images/fuselage.png" alt="Measurements of the Fuselage" width="45%" style="border:1px solid #000; display:block; margin:auto;">
    <br>(c)
  </span>
</p>

<p align="center">
  <strong>Figure 2:</strong> (a) Wing Planform Area \(S_{\text{ref}}\); 
  (b) Average t/c ratio, located at m.a.c.; 
  (c) Measurements of the Fuselage
</p>

###  MATLAB Code
For the MATLAB code, there is one function, Kwing, which was used to graph Fig. \ref{fig:surfaceform}. It is simply the equation used to plot Fig. \ref{fig:surfaceform}.

```matlab
clear, clc, close all 

load('fig11point2fit.mat') %loads fit curves 
load('fig11point4fit.mat') %loads fit curves 
load('fig11point8fit.mat') %loads fit curves 

b = 96 ; % span
g = 1.4 ; % specific heat ratio 
R = 1718 ; % gas constant 
rhoa = 0.0008754 ; %ambient pressure
Ta = 400 ; %ambient temperature
a = sqrt(g*R*Ta) ; % speed of sound
mu = 3.025E-7 ; % absolute viscosity 
Sref = 2*586.445158 ; %planform area
weight = 98000 ; % weight = lift in SLF
lift = weight ; 
AR = b^2/Sref ; % aspect ratio 
n = 500 ; % number of intervals between velocity range 
v_vec = linspace(200,900,n) ; % flight velocity

Dp = zeros(1,n) ; % initializing matrix for speed
Di = zeros(1,n) ; % initializing matrix for speed

for i=1:n %for-loop to go through every single velocity value

v = v_vec(i) ; % going through each velocity value 
q = (1/2)*rhoa*v^2 ; %dynamic pressure
Ma = v/a ; % Mach Number

%% Calculations Begin %% 
% Here is my numbering key: 
% 1 = Wing, 2 = Fuselage, 3 = Horizontal Tail, 4 = Vertical Tail, 5 =
% Pylons, 6 = Nacelles 

cr1 = 17.919574; % exposed root chord of wing (SolidWorks Calculated)
o1 = 0.22 ; % taper ratio 
ct1 = o1*cr1 ; % tip chord of wing 
mac1 = (2/3)*(cr1+ct1-(cr1*ct1)/(cr1+ct1)) ; % mean aerodynamic chord (exposed) 
RN1 = rhoa*v*mac1/mu ; %reynolds number
cf1 = fig11point2fit(RN1)/10^3 ; %using Fig 11.2 to find cf1 given reynolds number
K1 = Kwing(Ma,0.143266547,8) ; % calling on a function named Kwing, which takes in M0, t/c, and lambda and outputs K1 
Swet1 = 2*957.339439 ; % wetted area (SolidWorks Calculated)
cdp1 = K1*cf1*Swet1/Sref; %parasite drag from wing 

l2 = 103; %length of fuselage 
d2 = 13 ; %diameter of fuselage
K2 = fig11point4fit(l2/d2) ; % form factor of fuselage
RN2 = rhoa*v*l2/mu ; % reynolds number of fuselage
cf2 = fig11point2fit(RN2)/10^3 ; %using Fig 11.2 to find cf2 given reynolds number
Swet2 = 0.8*pi*d2*l2; % wetted area 
cdp2 = K2*cf2*Swet2/Sref; % parasite drag from fuselage 

cr3 = 11.1; 
o3 = 0.35;
ct3 = o3*cr3 ; 
mac3 = (2/3)*(cr3+ct3-(cr3*ct3)/(cr3+ct3)); 
RN3 = rhoa*v*mac3/mu ; 
K3 = Kwing(Ma,0.09,31.6) ; 
Swet3 = 2*261*1.02 ; 
cf3 = fig11point2fit(RN3)/10^3 ; 
cdp3 = K3*cf3*Swet3/Sref;

cr4 = 15.5;
o4 = 0.8;
ct4 = o4*cr4 ; 
mac4 = (2/3)*(cr4+ct4-(cr4*ct4)/(cr4+ct4)); 
RN4 = rhoa*v*mac4/mu ; 
K4 = Kwing(Ma,0.09,43.5) ; 
Swet4 = 2*161*1.02 ; 
cf4 = fig11point2fit(RN4)/10^3;
cdp4 = K4*cf4*Swet4/Sref;

cr5 = 16.2;
o5 = 1;
ct5 = o5*cr5 ; 
mac5 = (2/3)*(cr5+ct5-(cr5*ct5)/(cr5+ct5)); 
RN5 = rhoa*v*mac4/mu ; 
K5 = Kwing(Ma,0.06,0) ; 
Swet5 = 117; 
cf5 = fig11point2fit(RN5)/10^3;
cdp5 = K5*cf5*Swet5/Sref; 

l6 = 16.8; 
K6 = fig11point4fit(5) ; 
RN6 = rhoa*v*l6/mu ; 
cf6 = fig11point2fit(RN6)/10^3 ; 
Swet6 = 455;
cdp6 = K6*cf6*Swet6/Sref;

cdp = cdp1+cdp2+cdp3+cdp4+cdp5+cdp6 ;  % summing all parasite drag components

cl = lift/(q*Sref) ;  % lift coefficient 

e = fig11point8fit(AR,cdp); % calculating Oswald's Efficiency using Fig 11.8

cdi = cl^2/(pi*AR*e); % induced drag coeff

Dp(i) = cdp*q*Sref ; % parasitic drag
Di(i) = cdi*q*Sref ; % induced drag

end

Dtot = Dp + Di ; % total drag

j = 1; % I am finding out where the graphs intersect
while Dp(j)<Di(j)
    j = j+1;
end

L_D = lift./Dtot; % calculating L/D ratio

r = 1 ; % I am finding out where v = 765 ft/s
while v_vec(r)<765
    r = r + 1 ; 
end

Dp_765 = Dp(r) ; % parasitic drag when v = 765 
Di_765 = Di(r) ;% induced drag when v = 765 
Dtot_765 = Dp_765 + Di_765 ;% total drag when v = 765 

fprintf('Parasite Drag is: %f, \n Induced Drag is %f, \n Total Drag is %f\n',Dp_765,Di_765,Dtot_765)

figure
hold on; grid on; 
plot(v_vec,Dp,'LineWidth',2)
plot(v_vec,Di,'--','LineWidth',2)
plot(v_vec,Dtot,'-.','LineWidth',2) 
scatter(v_vec(j),Dp(j),80,'filled')
scatter(v_vec(j),Dtot(j),80,'filled','Marker','^')
xline(v_vec(j),'k:','LineWidth',2)
str = sprintf('Parasitic, Induced, and Total Drag\n vs. Flight Velocity') ;
title(str,'FontSize',20)
ylabel('Drag (lb)','FontSize',15)
xlabel('Velocity (ft/s)','FontSize',15)
str2 = sprintf('(%0.0f, %0.0f)', v_vec(j),Dp(j));
str3 = sprintf('(%0.0f, %0.0f)', v_vec(j),Dtot(j));
legend('Parasite Drag D_p','Induced Drag D_i','Total Drag D_{tot}',str2,str3,'Optimal Velocity')
hold off 
ylim([0 2E4]); xlim([200 900])

figure;
str4 = sprintf('Max L/D \n(%0.0f, %0.0f)', v_vec(j),L_D(j));
plot(v_vec,L_D,'LineWidth',2); grid on ; hold on;
xline(v_vec(j),'k:','LineWidth',2)
scatter(v_vec(j),L_D(j),80,'filled')
title('Lift to Drag Behavior as a Function of Velocity','FontSize',18)
legend('L/D Curve','Optimal Velocity',str4,'Location','southeast')
hold off;
xlabel('V (ft/s)','FontSize',15)
ylabel('L/D','FontSize',15)

figure; 
x = logspace(5,9) ; 
y = fig11point2fit(x);
loglog(x,y,'LineWidth',2); grid on 
hi = sprintf('Skin Friction Coeffficient Based on \n Length (Reynolds Number)');
title(hi,'FontSize',20)
xlabel('Reynolds number based on length, RN','FontSize',15)
ylabel('Skin Friction Coefficient, $C_f \times 10^3$','interpreter','latex','FontSize',15)
legend('Typical Transport Aircraft Roughness')
xlim([1E5 1E9])
ylim([1 20])
yticks([1 2 3 4 5 6 8 10 20])

figure
x = linspace(0,0.20) ; 
z = linspace(10,50) ; 
[X Z] = meshgrid(x,z) ; 
Y = Kwing(0.5,X,Z) ;

contour(X,Y,Z,0:5:50,'LineWidth',2);
colorbar; grid on ; 
title('Aerodynamic Surface Form Factor','FontSize',20)
xlabel('Thickness ratio, t/c','FontSize',15)
ylabel('Form Factor, K','FontSize',15) 
zlabel('hi this is just a test')
legend('Sweepback Angle \Lambda_{c/4}','Location','southeast') 

figure
x = linspace(3,11) ; 
y = fig11point4fit(x) ; 
plot(x,y,'LineWidth',2)
axis([3 11 1.05 1.4]); grid on ; 
title('Effect of Finess Ratio on Body Form Factor','FontSize',18)
xlabel('Fineness Ratio, L/D','FontSize',15)
ylabel('Body form factor, K','FontSize',15) 

figure 
x = linspace(0,14) ; 
z = linspace(0.01,0.025);
[X Z] = meshgrid(x,z) ; 
Y = fig11point8fit(X,Z) ;
contour(X,Y,Z,'LineWidth',2); grid on ;
title('Airplane Efficiency Factor, e','FontSize',20)
xlabel('Aspect Ratio','FontSize',15) 
ylabel('Airplane Efficiency Factor, e','FontSize',15)
xlim([0 12])
colorbar
```

```matlab
function K = Kwing(M0,t_c,lambda)
% Calculates the wing form factor, K, as a function of M0 (flight Mach
% number), t/c (max thickness to chord ratio), lambda (wing sweepback
% angle, degrees) 

lambda = deg2rad(lambda) ; 
numZ = (2-M0^2).*cos(lambda) ; 
denZ = sqrt(1-M0^2.*(cos(lambda)).^2) ; 
Z = numZ./denZ ; 
K = 1+Z.*t_c+100.*t_c.^4 ; 
end 
```