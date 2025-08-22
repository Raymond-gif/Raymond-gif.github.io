---
layout: single
title: "Formula Sheet"
permalink: /formula/
author_profile: false
---

<a href="/files/MAE_230C_Formula_Sheet.pdf" class="button-gradient">
  📄 Download MAE 230C Formula Sheet
</a>

<style>
  /* Section styling */
  .formula-section {
    background: #f9f9f9;
    border-left: 4px solid #4a90e2;
    padding: 1rem 1.2rem;
    margin: 1rem 0;
    border-radius: 6px;
  }

  .formula-section h2 {
    color: #357abd;
    margin-top: 0;
  }

  /* Collapsible style (open by default) */
  details[open] summary::after {
    content: "▼";
    float: right;
    font-size: 0.9rem;
  }
  details summary::after {
    content: "▶";
    float: right;
    font-size: 0.9rem;
  }
  summary {
    cursor: pointer;
    font-weight: bold;
    margin-bottom: 0.5rem;
  }
</style>

<style>
  /* Style the formula section summary as a big header */
  .formula-section summary {
    font-size: 1.5rem;      /* larger text */
    font-weight: bold;
    color: #4a90e2;         /* subtle blue color */
    margin-bottom: 0.5rem;  /* spacing below */
    cursor: pointer;        /* indicates it's clickable */
  }

  /* Optional: style the smaller titles inside */
  .formula-section p strong {
    font-size: 1.1rem;
    color: #222;            /* darker text for contrast */
  }

  .formula-section p {
  overflow-x: auto;       /* horizontal scroll if needed */
  overflow-y: hidden;     /* prevent vertical scroll */
  white-space: nowrap;    /* keep formula on one line */
  margin: 1rem 0;
  padding-bottom: 0.5rem;
}

</style>
<div class="formula-section">
  <details open>
    <summary>Integral Equations of Motion</summary>
    <!-- Conservation of Mass -->
    <p>
      <strong>Conservation of Mass:</strong><br>
      $$ 
      \frac{D}{Dt}\int\limits_{\text{CM}} \rho \, dV = \frac{\partial}{\partial t}
      \int\limits_{\text{CV}} \rho \, dV 
      + \int\limits_{\text{CS}} \rho (\mathbf{u} \cdot \mathbf{n}) \, dS = 0 \notag
      $$
    </p>
    <!-- Conservation of Momentum -->
    <p>
      <strong>Momentum Equation:</strong><br>
      $$
      \frac{D}{Dt} \int\limits_{\text{CM}}{\rho \mathbf{u} \, dV}= \frac{\partial}{\partial t}
      \int\limits_{\text{CV}} { \rho \mathbf{u}} \, dV 
      + \int\limits_{\text{CS}} \rho \mathbf{u} (\mathbf{u} \cdot \mathbf{n}) \, dS 
      = - \int\limits_{\text{CS}} p  \mathbf{n}\, dS + \int\limits_{\text{CS}} \boldsymbol{\underline{\underline{\tau}}} \cdot \mathbf{n} \, dS \notag
      $$
    </p>
    <!-- Conservation of Energy -->
    <p>
      <strong>Conservation of Energy:</strong><br>
      $$
      \begin{align*}
          \frac{D}{Dt}\int\limits_{\text{CM}} \rho e_0 \, dV
          = \frac{\partial}{\partial t}\int\limits_{\text{CV}} \rho e_0 \, dV 
          + \int\limits_{\text{CS}} \rho e_0 (\mathbf{u} \cdot \mathbf{n}) \, dS
          = - \int\limits_{ \text{CS}} p (\mathbf{u} \cdot \mathbf{n}) \, dS 
          &+ \int\limits_{\text{CS}} \boldsymbol{\underline{\underline{\tau}}} \cdot \mathbf{n} \cdot \mathbf{u} \, dS \\
          &+ \int\limits_{\text{CV}} \nabla \cdot \mathbf{q} \, dV 
      \end{align*}
      $$
    </p>
  </details>
</div>

<div class="formula-section">
  <details open>
    <summary>Differential Equations of Motion </summary>
    <!-- Conservation of Mass -->
    <p>
      <strong>Conservation of Mass</strong><br>
      $$
      \frac{\partial \rho}{\partial t} + \nabla \cdot (\rho {\mathbf{u}}) = 0, \quad
      \frac{D \rho}{D t} = -\rho \, \nabla \cdot {\mathbf{u}} \notag
      $$
    </p>
    <!-- Conservation of Momentum -->
    <p>
      <strong> Momentum Equation</strong><br>
      $$
      \frac{\partial (\rho {\mathbf{u}})}{\partial t} + \nabla \cdot \left( \rho {\mathbf{u}} {\mathbf{u}} \right) = -\nabla p + \nabla \cdot \underline{\underline{\boldsymbol{\tau}}}, \quad \rho\frac{D\mathbf{u}}{Dt}=-\nabla p +\nabla \cdot \boldsymbol{\underline{\underline{\tau}}} \notag
      $$ 
    </p>
    <!-- Conservation of Energy -->
    <p>
      <strong>Conservation of Energy</strong><br>
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
    </p>
  </details>
</div>

<div class="formula-section">
  <details open>
    <summary>Thermodynamics</summary>
    <p>
      <strong>1st Law of Thermodynamics</strong><br>
      $$
      de=\delta w + \delta q \notag
      $$
    </p>
    <p>
      <strong> Fundamental Thermodynamic Relations (Gibbs Equation)</strong><br>
      $$
      h=e+pv, \quad de= Tds - pdv ,\quad dh=Tds + v dp \notag
      $$
    </p>
    <p>
      <strong>Second Law of Thermodynamics</strong><br>
      $$
      ds=\frac{\delta q_{\text{rev}}}{T} \notag
      $$
    </p>
    <p>
      <strong>Specific Heat Ratio Definition </strong><br>
      $$
      c_v=\left[\frac{\partial e}{\partial T}\right]_v, \quad c_p =\left[\frac{\partial h}{\partial T}\right]_p \notag
      $$
    </p>
    <p>
      <strong>Equations for Perfect Gas </strong><br>
      $$
      R=c_p-c_v,\quad \gamma=\frac{c_p}{c_v},\quad c_p=\frac{\gamma R}{\gamma-1},\quad c_v=\frac{R}{\gamma-1}
      \notag
      $$
      $$
      pv= RT \rightarrow \frac{dp}{p}=\frac{d\rho}{\rho}+\frac{dT}{T},\quad de=c_v dT,\quad dh = c_pdT
      \notag
      $$
      $$
      ds=c_p \frac{dT}{T}-R\frac{dp}{p}=c_v \frac{dT}{T}+R\frac{dv}{v}, \quad a^2=\left( \frac{\partial p}{\partial\rho}\right)_s,\quad a^2=\gamma RT=\gamma \frac{p}{\rho},\quad u^2= \gamma M^2\frac{p}{\rho}
      \notag
      $$
    </p>
    <p>
      <strong>Internal Energy and Enthalpy for Calorically Perfect Gas</strong><br>
      $$
      e=c_vT, \quad h=c_pT \notag
      $$
    </p>
    <p>
      <strong>Entropy Relations Calorically Perfect Gas </strong><br>
      $$ 
      \frac{T_2}{T_1} = \left(\frac{\rho_2}{\rho_1}\right)^{\gamma - 1} = \left(\frac{p_2}{p_1}\right)^{\frac{\gamma - 1}{\gamma}}
      \notag
      $$
      $$
      s_2-s_1=c_p\ln\left(\frac{T_2}{T_1}\right)-R\ln{\left(\frac{p_2}{p_1}\right)}=c_v \ln{\left( \frac{T_2}{T_1}\right)} + R\ln{\left(\frac{v_2}{v_1}\right)}
      \notag
      $$
      $$
      d \left(p^{\gamma-1}T^{-\gamma} \right) =0,\quad d \left(T \rho^{1-\gamma}\right)    =0, \quad d    \left(p \rho^{-\gamma} \right) =0 \notag
      $$
    </p>
    <p>
      <strong>Total Properties Definition (CPG)</strong><br>
      $$
      {\frac{T_0}{T}}=1+\frac{\gamma-1}{2}M^2, \quad {\frac{p_0}{p}}=\left[ 1+\frac{\gamma-1}{2}M^2\right]^{\frac{\gamma}{\gamma-1}},\quad {\frac{\rho_0}{\rho}}=\left[ 1+\frac{\gamma-1}{2}M^2\right]^{\frac{1}{\gamma-1}}\notag 
      $$
    </p>
  </details>
</div>

<div class="formula-section">
  <details open>
    <summary>Q1D Flow (steady, adiabatic, no viscous effects, isentropic):  \( dT_0=0, \quad dp_0=0,\quad d\rho_0=0 \)</summary>
    <p>
      $$
      \mathbf{M < 1:}
      \; \boldsymbol{dA +}: \; (dp, \; d\rho, \; dT) +, \; (du, \;dM) -,
      \quad \boldsymbol{dA-}: \; (dp, \; d\rho, \; dT) -, \; (du, \; dM) +
      \notag
      $$
      $$
      \mathbf{M > 1:}
      \; \boldsymbol{dA +}: \; (dp,  \; d\rho, \; dT) -, \; (du,\; dM) +,
      \quad \boldsymbol{dA -}: \; (dp, \; d\rho, \; dT) +, \; (du, \;dM) -
      \notag
      $$
      $$
      \frac{d\rho}{\rho}+\frac{du}{u}+\frac{dA}{A}=0, \quad dp+\rho u du =0 , \quad dh+udu=0, \quad \frac{dA}{A}=(M^2-1)\frac{du}{u} 
      \notag
      $$
      $$
      \rho_1u_1A_1=\rho_2u_2A_2, \quad p_1A_1+\rho_1u_1^2A_1 +\int_{A_1}^{A_2}p dA=p_2A_2+\rho_2u_2^2A_2,\quad h_1+\frac{1}{2}u_1^2=h_2+\frac{1}{2}u_2^2
      \notag
      $$
      $$
      \frac{A}{A^*}=\frac{1}{M}\left[\frac{2}{\gamma+1} \left[1+\frac{\gamma-1}{2}M^2 \right] \right]^{\frac{\gamma+1}{2(\gamma-1)}} \notag 
      $$
      $$
      \text{Adiabatic Energy Equation: 
      }
      a_*^2 = \frac{2(\gamma - 1)}{\gamma + 1} \left[ \frac{a^2}{\gamma - 1} + \frac{u^2}{2} \right] \notag
      $$
      $$
      \text{Differential Identities: }\frac{du^2}{u^2}=\frac{dM^2}{M^2}+\frac{dT}{T},\quad \frac{du}{u}=\frac{1}{2}\frac{du^2}{u^2} \notag 
      $$
      $$
      \text{Mach Number definition: } \frac{dV}{V}=\frac{dM}{M}+\frac{1}{2}\frac{dT}{T}\notag 
      $$
    </p>
  </details>
</div>

<div class="formula-section">
  <details open>
    <summary>Fanno Flow: 1D-Adiabatic Flow w/ Irreversibilities (Non-Isentropic):  \(dT_0=0 \)</summary>
    <p>
      <strong>General Trends</strong><br>
      $$
      \boxed{\mathbf{M < 1} \colon (ds, \, du, \, dM) \, +, \quad (dT, \, dp, \, d\rho, \, dp_0) \, -} \notag $$
      $$
      \boxed{\mathbf{M > 1} \colon (ds, \, dT, \, dp, \, d\rho) \, +, \quad (dp_0, \, du, \, dM) \, -}
      \notag 
      $$
    </p>
    <p>
      <strong> Differential Equations of Motion</strong><br>
    $$
    \frac{d\rho}{\rho}+\frac{du}{u}=0, \quad dp+\rho udu =-\rho T ds,\quad dh+udu=0 \notag
    $$
    </p>
    <p>
      <strong>Integral Equations of Motion</strong><br>
      $$
      \rho_1u_1=\rho_2u_2,\quad p_1+\rho_1u_1^2=p_2+\rho_2u_2^2+\text{?}, \quad h_1+\frac{u_1^2}{2}=h_2+\frac{u_2^2}{2} \notag 
      $$
      $$
      \frac{dT}{T}+(\gamma-1)M^2 \frac{du}{u}=0,\enspace \frac{dT}{ds}=-\frac{T}{c_v}\left( \frac{M^2}{1-M^2}\right), \enspace \frac{ds}{R}=\left( 1 - M^2 \right)\frac{du}{u} \notag
      $$
      $$
      \frac{s- s_*}{c_p}=\ln\left[M^{\frac{\gamma-1}{\gamma}} \left(\left[\frac{2}{\gamma+1} \right]\left[1+\frac{\gamma-1}{2}M^2\right] \right)^{-\frac{\gamma+1}{2\gamma}} \right]\notag 
      $$
      $$
      \frac{T_2}{T_1}=\frac{2+(\gamma-1) M_1^2}{2+(\gamma-1) M_2^2},\enspace \frac{\rho_2}{\rho_1}=\frac{M_1}{M_2} \left[\frac{2+(\gamma-1)M_2^2}{2+(\gamma-1)M_1^2} \right]^{\frac{1}{2}} \notag
      $$
      $$
      \enspace \frac{p_2}{p_1}=\frac{M_1}{M_2} \left[ \frac{2+(\gamma -1)M_1^2}{2+(\gamma -1)M_2^2} \right]^{\frac{1}{2}},\enspace \frac{p_{02}}{p_{01}}=\frac{M_1}{M_2}\left[\frac{2+(\gamma -1)M_2^2}{2+(\gamma -1)M_1^2} \right]^{\frac{\gamma+1}{2(\gamma -1)}}\notag 
      $$
      $$
      \frac{T}{T_*}=\frac{\gamma+1}{2+(\gamma-1)M^2},\quad \frac{p}{p_*}=\frac{1}{M}\left[ \frac{\gamma+1}{2+(\gamma-1)M^2}\right]^{1/2} \notag
      $$
      $$
      \frac{\rho}{\rho_*}=\frac{1}{M}\left[\frac{2+(\gamma-1)M^2}{\gamma+1}\right]^{1/2},\quad \frac{p_{0}}{p_{0_*}}=\frac{1}{M} \left[ \frac{2+(\gamma-1)M^2}{\gamma+1}\right]^{\frac{\gamma+1}{2(\gamma-1)}}\notag 
      $$
    </p>
  </details>
</div>

<div class="formula-section">
  <details open>
    <summary>1-D Rayleigh Flow:  (Reversible Heat Addition, Non-adiabatic + Non-Isentropic)</summary>
    <p>
      <strong>General Trends:</strong><br>
      $$
      \begin{align*}
          \mathbf{M < 1:}
          \quad & \boldsymbol{\delta q +}: \, (ds, \, du, \, dM, \,dT_0) +, \quad (dp, \, d\rho, \, dp_0) -, \quad dT \pm (M=\gamma^{-1/2}) \\
          & \boldsymbol{\delta q -}: \, (ds, \, du, \, dM, \, dT_0) -, \quad (dp, \, d\rho, \, dp_0)+, \quad dT \mp
      \end{align*}
      $$
      $$
      \begin{align*}
          \mathbf{M > 1:}
          \quad & \boldsymbol{\delta q +}: \quad (ds  \, , dp \,, d\rho \,, dT_0,  \, dT ) +,
          \quad (dp_0  \,, du, \, dM ) - \\
          & \boldsymbol{\delta q -}: \quad (ds , \, dp,  \, d\rho , \, dT_0 , \, dT )-, \quad (dp_0 , \, du, \, dM)+
      \end{align*}
      $$
    </p>
    <p>
      <strong> Differential Equations of Motion: </strong><br>
      $$
      \frac{d\rho}{\rho}+\frac{du}{u}=0, \quad dp+\rho u du =0, \quad dh + udu=\delta q \notag 
      $$ 
    </p>
    <p>
      <strong>Integral Equations of Motion</strong><br>
      $$
      \rho_1u_1 =\rho_2 u_2, \quad p_1+\rho_1u_1^2=p_2+\rho_2u_2^2, \quad h_1 +\frac{u_1^2}{2}+q=h_2+\frac{u_2^2}{2} \notag 
      $$
      $$
      \frac{dT}{ds}=\frac{T}{c_p}\left[ \frac{1-\gamma M^2}{1-M^2}\right],
      \quad \frac{\delta q}{h}= \left( 1-M^2 \right) \frac{du}{u}, \quad \frac{dT}{T}=\frac{\delta q}{h}-\left(\gamma-1 \right)M^2  \frac{du}{u}
      \notag 
      $$
      $$
      \frac{p}{p_*}=\frac{1+\gamma}{1+\gamma M^2}, \quad \frac{T}{T_*}=M^2 \left(\frac{\gamma+1}{1+\gamma M^2} \right)^2,\quad \frac{\rho}{\rho_*}=\frac{1}{M^2}\left(\frac{1+\gamma M^2}{\gamma+1} \right) \notag
      $$
      $$
      \frac{p_0}{p_{0*}}= \left[\frac{1}{\gamma+1}\bigg(2+(\gamma-1)M^2 \bigg) \right]^{\frac{\gamma}{\gamma-1}}\left( \frac{\gamma+1}{1+\gamma M^2}\right) \notag 
      $$
      $$
      \frac{T_0}{T_{0*}}=\frac{M^2(\gamma+1)}{(1+\gamma M^2)^2} \left[2+(\gamma-1)M^2 \right],\quad \frac{s - s_*}{c_p} = \ln \left[ M^2 \left( \frac{\gamma + 1}{1 + \gamma M^2} \right)^{\frac{\gamma+1}{\gamma}} \right]\notag 
      $$
    </p>
  </details>
</div>

<div class="formula-section">
  <details open>
    <summary>Shock Theory</summary>
    <p>
      <strong>General Trends for Stationary Adiabatic Normal Shocks</strong><br>
      $$
      \Delta\rho +,\Delta p+,\Delta T+, \Delta T_0= 0,\Delta u-,\Delta M-,\Delta p_0 - \notag 
      $$
      $$
      \rho_1 u_1=\rho_2u_2,\quad p_1+\rho_1u_1^2=p_2+\rho_2u_2^2,\quad h_1+\frac{u_1^2}{2}=h_2+\frac{u_2^2}{2}
      \notag 
      $$
    </p>
    <p>
      <strong>Rankine-Hugoniot Relation for any gas: </strong><br>
      $$
      h_2 - h_1 = \frac{1}{2} \left( p_2 - p_1 \right) \left( \frac{1}{\rho_1} + \frac{1}{\rho_2} \right), \quad e_2-e_1=\frac{p_2+p_1}{2}\left(v_1-v_2 \right) \notag
      $$ 
    </p>
    <p>
      <strong>Property Ratios for Calorically Perfect Gas</strong><br>
      $$
      \frac{\rho_2}{\rho_1}=\frac{1+\frac{\gamma+1}{\gamma-1}\frac{p_2}{p_1}}{\frac{\gamma+1}{\gamma-1}+\frac{p_2}{p_1}}, \quad \frac{T_2}{T_1}=\frac{p_2}{p_1}\left[\frac{\frac{\gamma+1}{\gamma-1}+\frac{p_2}{p_1}}{1+\frac{\gamma+1}{\gamma-1}\frac{p_2}{p_1}}\right]\notag 
      $$
      $$
      M_2^2=\frac{1+\frac{\gamma-1}{2}M_1^2}{\gamma M_1^2-\frac{\gamma-1}{2}},\quad \frac{T_2}{T_1}=\left[\frac{2+(\gamma-1)M_1^2}{(\gamma+1)M_1^2}\right] \left[1+\frac{2\gamma}{\gamma+1}(M_1^2-1) \right] \notag
      $$
      $$
      \frac{\rho_2}{\rho_1}=\frac{(\gamma+1)M_1^2}{2+(\gamma-1)M_1^2},\quad \frac{p_2}{p_1}=1+\frac{2\gamma}{\gamma+1}\left(M_1^2-1 \right)\notag 
      $$
      $$
      \frac{p_{02}}{p_{01}} =
      \left[ \frac{(\gamma + 1) M_1^2}{2 + (\gamma - 1) M_1^2} \right]^{\frac{\gamma}{\gamma - 1}}
      \left[ \frac{\gamma + 1}{2\gamma M_1^2 - (\gamma - 1)} \right]^{\frac{1}{\gamma - 1}}\notag 
      $$
    </p>
    <p>
      <strong>Unsteady Shock Waves</strong><br>
      $$
      \frac{\Delta u}{a_1}=\frac{2}{\gamma+1}\left[ M_s-\frac{1}{M_s}\right]=\frac{1}{\gamma}\left[ \frac{p_2}{p_1}-1\right] \left[ \frac{\frac{2\gamma}{\gamma+1}}{\frac{p_2}{p_1}+\frac{\gamma-1}{\gamma+1}} \right]^{\frac{1}{2}},\enspace M_s^2=1+{\frac{\gamma+1}{2\gamma}} \left[ \frac{p_2}{p_1}-1 \right]\notag 
      $$
    </p>
  </details>
</div>

<div class="formula-section">
  <details open>
    <summary>Finite Waves (Isentropic Equations of Motion)</summary>
    <p>
    $$
    \frac{\partial \rho}{\partial t} + \mathbf{u} \cdot \nabla \rho +\rho\nabla\cdot \mathbf{u}=0,
    \quad \frac{\partial \textbf{u}}{\partial t}+\textbf{u}\cdot\nabla \textbf{u}+\frac{a^2}{\rho} \nabla \rho=0
    \notag 
    $$
    </p>
    <p>
      <strong>One-Dimensional Specialization</strong><br>
      In terms of density and velocity,
      $$
      \text{mass: } \frac{1}{a^2} \left( \frac{\partial p}{\partial t} + u \frac{\partial p}{\partial x} \right) + \rho \frac{\partial u}{\partial x} = 0, \quad \frac{\partial \rho}{\partial t} +u \frac{\partial \rho}{\partial x} + \rho \frac{\partial u}{\partial x} =0 \notag 
      $$
      $$
      \text{momentum: } \frac{\partial u}{\partial t} + u \frac{\partial u}{\partial x} + \frac{1}{\rho} \frac{\partial p}{\partial x} = 0, \quad \frac{\partial u}{\partial t}+ u \frac{\partial u}{\partial x} + \frac{a^2}{\rho} \frac{\partial \rho}{\partial x}=0 \notag 
      $$
      In terms of condensation and velocity,
      $$
      \text{mass: } \rho_1 \frac{\partial \tilde{s}}{\partial t}+ \rho_1 \left( \frac{\partial u }{\partial x}+\tilde{s} \frac{\partial u}{\partial x} \right) +\rho_1u \frac{\partial \tilde{s}}{\partial x}=0 \notag
      $$
      $$
      \text{momentum: } \frac{\partial u}{\partial t} + u \frac{\partial u}{\partial x}+\frac{a^2}{\tilde{s}+1} \frac{\partial \tilde{s}}{\partial x}=0\notag 
      $$
      $$
      \frac{dx}{dt}= u \pm a, \quad du = \pm \frac{dp}{\rho a }, \quad J_{\pm}= u \pm \frac{2 a}{\gamma - 1} \notag 
      $$
      $$
      a=\frac{\gamma-1}{4}(J_+ -J_-), \quad u=\frac{1}{2}(J_+ + J_-), \quad \tilde{s}=\frac{\rho'}{\rho_1}=\frac{\rho-\rho_1}{\rho_1}\notag 
      $$
      $$
      \frac{p}{p_1}=\left(\frac{\rho}{\rho_1} \right)^\gamma=\left( 1+\tilde{s} \right)^\gamma, \quad \frac{T}{T_1}=\left( 1+\tilde{s} \right)^{\gamma-1}\notag 
      $$
    </p>
    <p>
      <strong>Left-Facing, Simple-Centered Expansion Wave </strong><br>
      $$
      \frac{a}{a_1}=1-{\frac{\gamma-1}{2}}\left( \frac{u}{a_1} \right) , \quad \frac{T}{T_1}=\left[ 1-{\frac{\gamma-1}{2}} \left( \frac{u}{a_1} \right) \right]^2, \quad \frac{p}{p_1}=\left[1-{\frac{\gamma-1}{2}} \left( \frac{u}{a_1} \right) \right]^{\frac{2\gamma}{\gamma-1}} \notag
      $$
      $$
      \frac{\rho}{\rho_1}
      =\left[  1-{\frac{\gamma-1}{2}} \left( \frac{u}{a_1} \right) \right] ^{\frac{2}{\gamma-1}}, \quad
      u=\frac{2}{\gamma+1} \left(a_1+\frac{x}{t} \right) \notag 
      $$
    </p>
    <p>
      <strong>Right-Facing, Isentropic Compression Wave </strong><br>
      $$
      \frac{a}{a_1}=1+{\frac{\gamma-1}{2}}\left( \frac{u}{a_1} \right) , \quad \frac{T}{T_1}=\left[ 1+{\frac{\gamma-1}{2}} \left( \frac{u}{a_1} \right) \right] ^2 \notag
      $$
      $$
      \frac{p}{p_1}= \left[  1+{\frac{\gamma-1}{2}} \left( \frac{u}{a_1} \right) \right]^{\frac{2\gamma}{\gamma-1}}, \quad \frac{\rho}{\rho_1}= \left[ 1+{\frac{\gamma-1}{2}} \left( \frac{u}{a_1} \right) \right]^{\frac{2}{\gamma-1}} \notag 
      $$
    </p>
    <p>
      <strong>Shock Tube Equation</strong><br>
      $$
    \frac{p_4}{p_1}=\frac{1+\frac{2\gamma_1}{\gamma_1+1} \left(M_s^2-1 \right)}{\left[1-\frac{a_1}{a_4}\frac{\gamma_4-1}{\gamma_1+1}
    \left(M_s-\dfrac{1}{M_s}\right)\right]^{\frac{2\gamma_4}{\gamma_4 - 1}}}= \frac{p_2}{p_1} \left[ 1 - \frac{(\gamma_4 - 1) \left( \frac{a_1}{a_4} \right) \left( \frac{p_2}{p_1} - 1 \right)}
    {\sqrt{2 \gamma_1 \left[ 2 \gamma_1 + (\gamma_1 + 1) \left( \frac{p_2}{p_1} - 1 \right) \right] }} \right]^{\frac{-2 \gamma_4}{\gamma_4 - 1}}
    \notag 
    $$
    </p>
  </details>
</div>

<div class="formula-section">
  <details open>
    <summary>Acoustic Theory (Isentropic)</summary>
    <p>
    $$
    \begin{aligned}
    \text{mass: } \frac{\partial \rho'}{\partial t}+\rho_1 \nabla \cdot \mathbf{u'}=0, \enspace \frac{\partial \tilde{s}}{\partial t} + \nabla \cdot \mathbf{u'}&=0,  
        \quad \text{mom: } \frac{\partial \mathbf{u'}}{\partial t}+\frac{a_1^2}{\rho_1}\nabla \rho'=0, \enspace \frac{\partial \mathbf{u'}}{\partial t}+a_1^2 \nabla \tilde{s}=0 \\
        \frac{\partial^2 \mathbf{u'}}{\partial t^2} - a_1^2 \nabla (\nabla \cdot \mathbf{u'}) &= 0, \qquad \frac{\partial^2 \tilde{s}}{\partial t^2} - a_1^2 \nabla^2 \tilde{s} = 0
    \end{aligned}
    \notag 
    $$
    </p>
    <p>
      <strong>One-Dimensional-Rectilinear Specialization</strong><br>
      $$
      \text{mass: }\frac{\partial \rho'}{\partial t}+\rho_{1}\frac{\partial u'}{\partial x}=0, \enspace \frac{\partial \tilde{s}}{\partial t} + \frac{\partial u'}{\partial x}=0, \quad \text{mom: } \rho_{1} \frac{\partial u'}{\partial t}+a_{1}^2\frac{\partial \rho'}{\partial x}=0, \enspace \frac{\partial u'}{\partial t} + a_1^2 \frac{\partial \tilde{s}}{\partial x}=0\notag 
      $$
      $$
      \frac{\partial^2 \rho'}{\partial t^2}-a_{1}^2 \frac{\partial^2 \rho'}{\partial x^2}=0,\quad \frac{\partial^2 u'}{\partial t^2}-a_{1}^2 \frac{\partial^2 u'}{\partial x^2}=0,\quad \frac{\partial^2 \tilde{s}}{\partial t^2} - a_1^2 \frac{\partial^2 \tilde{s}}{\partial x^2}=0\notag 
      $$
      $$
      \tilde{s} = F(\xi)  + G(\eta), \enspace  u' = f(\xi) + g(\eta), \enspace
      \xi = x - a_{1} t, \enspace \eta = x + a_{1} t
      \notag
      $$
      $$
      f=a_1 F ,\enspace g=-a_1 G,\enspace u' = \pm a_1 \tilde{s}= \pm \frac{p'}{\rho_1a_1}, \enspace p'=\pm \gamma p_1 \tilde{s}
      \notag 
      $$
    </p>
    <p>
      <strong>Linearized Isentropic: </strong><br>
      $$
      \frac{p}{p_1}=1+\gamma \tilde{s}, \quad \frac{T}{T_1}=1+(\gamma-1) \tilde{s}, \quad u'=a_1[F(\xi)-G(\eta)], \quad p'=\gamma p_1[F(\xi) + G(\eta)]\notag 
      $$
    </p>
    <p>
      <strong>Spherical Acoustics </strong><br>
    $$
    \frac{\partial^2(r \tilde{s})}{\partial t^2}-a_1^2 \frac{\partial^2(r \tilde{s})}{\partial r^2}=0 \notag
    $$
    $$
    \tilde{s}=\frac{1}{r} \mathcal{F}(r-a_1 t)+\frac{1}{r}\mathcal{G}(r+a_1t)=\frac{1}{r} F\left(t-\frac{r}{a_1}\right)+\frac{1}{r}G\left(t+\frac{r}{a_1}\right)\notag 
    $$
    </p>
  </details>
</div>

<div class="formula-section">
  <details open>
    <summary>Oblique Shock Theory</summary>
    <p>
    $$
    M_{n1}=M_1 \sin{(\beta)}, \quad M_2=\frac{M_{n2}}{\sin{(\beta-\theta)}}, \notag
    $$
    $$
    \tan(\theta) = 2 \cot(\beta) \left[ \frac{M_1^2 \sin^2(\beta) - 1}{M_1^2 (\gamma + \cos(2\beta)) + 2} \right], \quad M_1^2 \sin^2{\beta} -1=\frac{\gamma +1}{2} M_1^2 \frac{\sin{\beta}\sin{\theta}}{\cos (\beta-\theta)}
    \notag 
    $$
    $$
    \text{Mach: } \mu = \sin^{-1}{\left(\frac{1}{M}\right)}\notag 
    $$
    </p>
  </details>
</div>

<div class="formula-section">
  <details open>
    <summary>Steady, Homentropic, Homenthalpic, 2-D Flow</summary>
    <p>
    $$
    \mathbf{u} \cdot \left[\mathbf{u} \cdot \nabla \mathbf{u}\right]-a^2 \nabla \cdot \mathbf{u}=0\notag 
    $$
    </p>
    <p>
      <strong>2D Specialization</strong><br>
      $$
      \left[ u^2 - a^2 \right]\frac{\partial u}{\partial x}+ \left[ v^2 - a^2 \right] \frac{\partial v}{\partial y}+ uv \left[\frac{\partial u}{\partial y}+ \frac{\partial v}{\partial x} \right]=0 \notag 
      $$
      $$
      [u^2 - a^2] {\phi_{xx}} + 2uv {\phi_{xy}} + [v^2 - a^2] \phi_{yy} = 0, \enspace \frac{dy}{dx}=\frac{\frac{uv}{a^2}\pm \sqrt{M^2-1}}{\frac{u^2}{a^2}-1}=\tan{[\theta \pm \mu]}\notag 
      $$
      $$
      \frac{dn}{ds}=\pm \frac{1}{\sqrt{M^2-1}}= \tan(\pm \mu), \quad d \theta \mp \sqrt{M^2-1}\frac{dV}{V}=0 \notag
      $$
      $$
      d\nu=\frac{\sqrt{M^2-1}}{1+\frac{\gamma-1}{2}M^2} \frac{dM}{M}, \quad \theta \mp \nu=C \notag 
      $$
      $$
      \nu(M) = \sqrt{\frac{\gamma+1}{\gamma-1}} \tan^{-1} \left( \sqrt{\frac{\gamma-1}{\gamma+1} (M^2 -1)} \right) - \tan^{-1}(\sqrt{M^2-1})
      \notag 
      $$
    </p>
  </details>
</div>

<div class="formula-section">
  <details open>
    <summary>Perturbation Theory (Subsonic + Supersonic)</summary>
    <p>
    $$
    \left( 1-M_{\infty}^2 \right) \frac{\partial u'}{\partial x} + \frac{\partial v'}{\partial y} + \frac{\partial w'}{\partial z}=0, \quad (1-M_{\infty}^2) \frac{\partial^2 \phi'}{\partial x^2}+\frac{\partial^2 \phi'}{\partial y^2}+ \frac{\partial^2 \phi'}{\partial z^2}=0 \notag
    $$
    $$
    c_p=\frac{2}{\gamma M_{\infty}^2} \left[\frac{p}{p_{\infty}}-1 \right], \quad
    c_p = \frac{2}{\gamma M_{\infty}^2} 
    \Bigg[ 
    \left[1+ \frac{\gamma - 1}{2} M_{\infty}^2 \left( 1 - \frac{\mathbf{u} \cdot \mathbf{u}}{U_{\infty}^2} \right)  \right]^{\frac{\gamma}{\gamma - 1}} - 1
    \Bigg]
    \notag 
    $$
    </p>
    <p>
      <strong>Linearized Pressure Coefficient</strong><br>
      $$ 
      \text{2D: } c_p= -2\frac{u'}{U_{\infty}}=-\frac{2}{U_{\infty}} \frac{\partial \phi'}{\partial x},\quad
      \text{3D: } c_p=-2\frac{ u'}{U_{\infty}}-\frac{v'^2 + w'^2}{U_{\infty}^2}, \quad \text{BC: } \left(\frac{\partial \phi'}{\partial y} \right)_{y=0}=U_{\infty}\frac{dy_w}{dx} \notag 
      $$
    </p>
    <p>
      <strong>2D-Supersonic Perturbation Theory</strong><br>
    $$
    \lambda^2=M_{\infty}^2-1, \quad \frac{\partial^2 \phi'}{\partial x^2}-\frac{1}{\lambda^2}\frac{\partial^2 \phi'}{\partial y^2}=0, \quad \phi=f(x-\lambda y) + g(x+\lambda y)\notag 
    $$
    $$
    f'(x-\lambda y_1) - g'(x+\lambda y_1)=-\frac{U_{\infty}}{\lambda} \frac{dy_{w1}}{dx}, \quad f'(x-\lambda y_2) - g'(x+\lambda y_2)=-\frac{U_{\infty}}{\lambda} \frac{dy_{w2}}{dx} \notag 
    $$
    </p>
    <p>
      <strong>General Airfoil Drag and Lift Coefficient Formula</strong><br>
     $$
    C_d=\frac{1}{c}\int\limits_{LE}^{TE} \left(C_{pu} \frac{dy_u}{dx}-C_{pl}\frac{dy_l}{dx}\right) \, dx,\quad C_l=\frac{1}{c}\int\limits_{LE}^{TE} \left( C_{pl}-C_{pu} \right) \, dx \notag 
    $$
    </p>
    <p>
      <strong>Supersonic Thin Airfoil Theory</strong><br>
      $$
      C_{pu}=\frac{2}{\lambda}\frac{dy_u}{dx}, \quad C_{pl}=-\frac{2}{\lambda} \frac{dy_l}{dx}, \quad C_l=-\frac{2}{\lambda c} \int\limits_{0}^{c} \left[\frac{dy_l}{dx}+\frac{dy_u}{dx} \right] \, dx=\frac{4}{\lambda}\alpha, \quad \notag 
      $$
      $$
      C_d=\frac{2}{\lambda c} \int\limits_{0}^{c} \left[\left( \frac{dy_u}{dx} \right)^2+ \left( \frac{dy_l}{dx}\right) ^2 \right] \, dx=\frac{1}{\lambda c} \int\limits_{0}^{c} \left[4 \left(\frac{dy_c}{dx} \right)^2+\left( \frac{dh}{dx} \right)^2 \right] \, dx\notag 
      $$
    </p>
    <p>
      <strong>Similarity Rules</strong><br>
    $$
    \phi(x,y)=\frac{1}{\sqrt{1-M_1^2}} \frac{U_1}{U_i} \frac{\tau_1}{\tau_i} \Phi \left(x,y \sqrt{1-M_1^2} \right), \quad C_p(x,y)=\frac{1}{\sqrt{1-M_1^2}} \frac{\tau_1}{\tau_i}C_{pi} \left( x,y\sqrt{1-M_1^2} \right) \notag 
    $$
    </p>
  </details>
</div>