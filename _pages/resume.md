---
layout: splash
title: "Resume"
permalink: /resume/
author_profile: false
redirect_from:
  - /resume
---

<style>
  /* Remove default body margin so no gap around edges */
  body {
    margin: 0;
    padding: 0;
  }
</style>

<section style="
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  max-width: none;
  margin-left: 0;
  margin-right: 0;
  padding-left: 16px;  /* small padding so text not flush to edge */
  padding-right: 16px; /* optional for right side */
  color: #222;
  line-height: 1.5;
">

  <header style="margin-bottom: 1.5rem;">
    <h1 style="margin-bottom: 0.25rem; font-weight: 700; font-size: 2rem;">Raymond Dunn</h1>
    <p style="font-size: 1rem; margin: 0;">
      📧 <a href="mailto:raymonddunn25@gmail.com" style="color: #4a90e2; text-decoration: none;">raymonddunn25@gmail.com</a>
    </p>
    <hr style="margin: 1.5rem 0; border-color: #ccc;">
  </header>

<section style="margin-bottom: 2rem;">
  <h2 style="font-size: 1.4rem; font-weight: 600; margin-bottom: 0.75rem; border-bottom: 2px solid #4a90e2; padding-bottom: 0.25rem;">
    Education
  </h2>
  <div style="display: flex; align-items: center; justify-content: space-between; flex-wrap: wrap;">
    <span style="font-weight: 600; font-size: 1rem; margin-bottom: 0.5rem;">
      University of California, Irvine — BS in Aerospace Engineering, GPA: 3.4
    </span>
    <a href="/files/AerospaceBS.pdf" class="button-gradient">
      📄 <span>Degree PDF</span>
    </a>
  </div>
  <p style="margin-top: 0.4rem; font-style: italic; color: #555;">June 2024</p>
</section>

  <section style="margin-bottom: 2rem;">
    <h2 style="font-size: 1.4rem; font-weight: 600; margin-bottom: 0.75rem; border-bottom: 2px solid #4a90e2; padding-bottom: 0.25rem;">Experience</h2>

    <article style="margin-bottom: 1.2rem;">
      <h3 style="font-weight: 700; font-size: 1.1rem; margin-bottom: 0.2rem;">Design, Build Fly: Remote-Controlled Aircraft</h3>
      <p style="font-style: italic; margin-top: 0; margin-bottom: 0.5rem;">September 2022 — June 2023</p>
      <ul style="margin-top: 0; padding-left: 1.3rem; color: #333;">
        <li>Measured wing deflection to assess structural integrity after loading the surface with various sand weights</li>
        <li>Assembled wings by laser cutting and positioning ribs at precise intervals following the analysis of lift/drag curves to determine the ideal airfoil shape</li>
        <li>Redesigned nose cone shape by experimenting with various lengths and diameters to optimize fineness ratio and minimize parasitic drag</li>
      </ul>
    </article>
  </section>

  <section style="margin-bottom: 2rem;">
    <h2 style="font-size: 1.4rem; font-weight: 600; margin-bottom: 0.75rem; border-bottom: 2px solid #4a90e2; padding-bottom: 0.25rem;">Projects</h2>

    <article style="margin-bottom: 1.5rem;">
      <h3 style="font-weight: 700; font-size: 1.1rem; margin-bottom: 0.2rem;">
        <a href="/portfolio/methodofcharacteristics"
           style="color: #4a90e2; text-decoration: underline; cursor: pointer; transition: color 0.3s ease;"
           onmouseover="this.style.color='#1a5bb8';"
           onmouseout="this.style.color='#4a90e2';"
        >
          Supersonic Compressible Fluid Flow Analysis of Diverging Channel &nbsp;➔
        </a>
      </h3>
      <p style="font-style: italic; margin-top: 0; margin-bottom: 0.5rem;">September 2024 — December 2024</p>
      <ul style="margin-top: 0; padding-left: 1.3rem; color: #333;">
        <li>Developed a method to compute velocity and pressure fields in arbitrarily shaped channels using lattice point discretization and method of characteristics</li>
        <li>Coded MATLAB script to determine the geometry of Mach waves and derived Prandtl-Meyer function from Navier-Stokes equations to solve for Riemann invariants. Plotted characteristic lines</li>
        <li>Determined ideal wall contour shape for isentropic flow (no shocks, cancellation of waves)</li>
      </ul>
    </article>

    <article style="margin-bottom: 1.5rem;">
      <h3 style="font-weight: 700; font-size: 1.1rem; margin-bottom: 0.2rem;">
        <a href="/portfolio/numericalmethodsBLeqn/"
           style="color: #4a90e2; text-decoration: underline; cursor: pointer; transition: color 0.3s ease;"
           onmouseover="this.style.color='#1a5bb8';"
           onmouseout="this.style.color='#4a90e2';"
        >
          Numerical Solution to Falkner-Skan Boundary Layer Equation &nbsp;➔
        </a>
      </h3>
      <p style="font-style: italic; margin-top: 0; margin-bottom: 0.5rem;">January 2025 — March 2025</p>
      <ul style="margin-top: 0; padding-left: 1.3rem; color: #333;">
        <li>Employed a second-order finite difference scheme to solve for flow over flat plate with arbitrary pressure gradient to investigate effects of shear stress on an external body</li>
        <li>Generated velocity profile plots in MATLAB under successively stronger adverse pressure gradients, capturing the progression toward boundary layer separation</li>
        <li>Generalized results to flow over any object by using Von Karman momentum integral equations and compared with experimental results found in literature, found close agreement</li>
      </ul>
    </article>

    <article style="margin-bottom: 1.5rem;">
      <h3 style="font-weight: 700; font-size: 1.1rem; margin-bottom: 0.2rem;">
        Commercial Aircraft Sizing and Design Report
      </h3>
      <p style="font-style: italic; margin-top: 0; margin-bottom: 0.5rem;">January 2024 — March 2024</p>
      <ul style="margin-top: 0; padding-left: 1.3rem; color: #333;">
        <li>Hand-calculated the parasitic and induced drag contributions from the wings, tails, and fuselage to determine the ideal flight velocity to minimize drag</li>
        <li>Coded MATLAB script to size aircraft components, accounting for weight, takeoff lift/drag, thrust available, wing loading, aspect ratio, and sweep angle, in order to meet design requirements</li>
        <li>Demonstrated sizing results by modeling aircraft on SW and creating detailed drawings of fuselage interior, wings/tails, and landing gear</li>
      </ul>
    </article>

    <article style="margin-bottom: 1.5rem;">
  <h3 style="font-weight: 700; font-size: 1.1rem; margin-bottom: 0.2rem;">
    Autonomous Four-Legged Walking Robot Simulating Human Motion
  </h3>
  <p style="font-style: italic; margin-top: 0; margin-bottom: 0.5rem;">April 2024 — June 2024</p>
  <ul style="margin-top: 0; padding-left: 1.3rem; color: #333;">
    <li>Calibrated weight distribution to ensure center of gravity (CG) was within permitted bounds for control and balance after determining the CG position manually and through SolidWorks (SW) simulation</li>
    <li>Performed SW motion study analysis to visualize and troubleshoot range of movement and walking mechanism, identifying potential interference issues</li>
    <li>Tightened joint hole tolerances to improve leg linkages after observing that the leg mechanism was slack, resulting in more natural walking</li>
  </ul>
</article>

  </section>

<section style="margin-bottom: 2rem;">
  <h2 style="font-size: 1.4rem; font-weight: 600; margin-bottom: 0.75rem; border-bottom: 2px solid #4a90e2; padding-bottom: 0.25rem;">
    Certifications
  </h2>
  <div style="display: flex; align-items: center; flex-wrap: wrap; gap: 8px;">
    <span style="font-weight: 600;">SOLIDWORKS CAD Design Associate (CSWA)</span>
    <a href="/files/CSWA_Certification.pdf" class="button-gradient">
      📄 View
    </a>
  </div>
</section>

  <section>
    <h2 style="font-size: 1.4rem; font-weight: 600; margin-bottom: 0.75rem; border-bottom: 2px solid #4a90e2; padding-bottom: 0.25rem;">Extracurriculars</h2>
    <article>
      <h3 style="font-weight: 700; font-size: 1.1rem; margin-bottom: 0.2rem;">Board Member of American Society of Mechanical Engineers at UCI</h3>
      <p style="font-style: italic; margin-top: 0; margin-bottom: 0.5rem;">2021 — 2024</p>
      <ul style="margin-top: 0; padding-left: 1.3rem; color: #333;">
        <li>Appointed to board committee to decide on issues involving club outreach, senior engineering projects and community partnerships</li>
        <li>Strengthened local engineering community by organizing student-led events, mentoring underclassmen, and promoting growth opportunities (workshops)</li>
      </ul>
    </article>
  </section>

</section>
