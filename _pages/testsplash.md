---
layout: splash
title: "About Me"
permalink: /testsplash/
---

<!-- Hero Image with Title Overlay -->
<div style="position:relative; width:100%; max-height:700px; overflow:hidden; border-radius:20px; box-shadow:0 8px 40px rgba(0,0,0,0.25); margin-bottom:50px;">
  <img src="/images/profile.jpg" alt="Raymond Dunn"
       style="width:100%; height:700px; object-fit:cover; object-position:center 10%; display:block;">
       
  <div style="position:absolute; bottom:40px; left:50%; transform:translateX(-50%); text-align:center; 
              color:#ffffff; background:rgba(0,0,0,0.35); padding:1rem 2rem; border-radius:12px;">
    <h1 style="font-size:3rem; margin:0;">Raymond Dunn</h1>
    <p style="font-size:1.2rem; margin:0;">Aerospace Engineer | Fluid Dynamics & Continuum Mechanics</p>
  </div>
</div>


<!-- Bio Section -->
<div style="max-width:800px; margin:0 auto; text-align:center; line-height:1.6; color:#000000;">
  <p>Hi, I’m <strong>Raymond Dunn</strong>. I received my B.S. in Aerospace Engineering in <strong>Spring 2024</strong> and am passionate about <strong>fluid dynamics</strong> and <strong>continuum mechanics</strong>.</p>

  <p>I am currently exploring <strong>tensor formulations</strong> of the fundamental equations governing fluid flow. Tensors capture the physical nature of motion, independent of coordinate systems. By analyzing how coordinate transformations influence the equations of motion, I aim to deepen my understanding of the mathematical structure behind fluids.</p>

  <p>Other work includes:</p>
  <ul style="list-style-type:none; padding:0; margin:0 0 1rem 0;">
    <li>• <strong>Compressible Flow:</strong> Using the Method of Characteristics to analyze 2D flow through arbitrary diverging channels.</li>
    <li>• <strong>Future Goals:</strong> Diving further into <strong>Computational Fluid Dynamics (CFD)</strong> and advanced simulation techniques.</li>
  </ul>

  <p>This website documents my research, projects, and learning in fluid mechanics.</p>

  <p><em>Outside of research, I enjoy creating computational visualizations and exploring new ways to make fluid mechanics intuitive.</em></p>
</div>

<!-- Responsive Card Row -->
<style>
.rd-cards {
  display:flex;
  gap:1.25rem;
  justify-content:center;
  flex-wrap:wrap;
  margin-top:2rem;
}
.rd-card {
  background:rgba(255,255,255,0.02);
  border-radius:12px;
  padding:1rem;
  max-width:340px;
  text-align:center;
  box-shadow:0 6px 18px rgba(0,0,0,0.12);
  border:1px solid rgba(255,255,255,0.02);
  transition: all 0.3s ease;
}
.rd-card:hover {
  transform: translateY(-5px);
  box-shadow:0 10px 25px rgba(0,0,0,0.15);
}
.rd-card img {
  width:100%;
  height:160px;
  object-fit:cover;
  border-radius:8px;
  margin-bottom:0.75rem;
}
.rd-card h3 {
  margin:0.5rem 0;
}
.rd-card p {
  color:var(--muted-text-color,#a0a0a0);
  margin-bottom:1rem;
  font-size:0.95rem;
}
.rd-btn {
  display:inline-block;
  padding:0.55rem 1rem;
  border-radius:999px;
  text-decoration:none;
  font-weight:600;
  border:1px solid rgba(255,255,255,0.06);
  background:linear-gradient(to bottom,rgba(255,255,255,0.03),rgba(255,255,255,0.01));
}
@media (max-width:680px) {
  .rd-card {
    max-width:100%;
    width:100%;
  }
}
</style>

<div class="rd-cards">
  <div class="rd-card">
    <img src="/images/tensorsimage.png" alt="Academic Work">
    <h3>Academic Work</h3>
    <p>Publications, notes, and research projects on compressible flow, differential geometry in fluids, and related topics.</p>
    <a class="rd-btn" href="/academic/">View Academic Work</a>
  </div>

  <div class="rd-card">
    <img src="/images/portfolio.jpg" alt="Portfolio">
    <h3>Portfolio</h3>
    <p>A curated selection of projects, visualizations, and tools I’ve built — MATLAB, LaTeX resources, and more.</p>
    <a class="rd-btn" href="/portfolio/">View Portfolio</a>
  </div>
</div>
