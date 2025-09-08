---
permalink: /
layout: splash
title: About Me 
redirect_from: 
  - /about/
  - /about.html
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
  gap:1.5rem;
  justify-content:center;
  flex-wrap:wrap;
  margin-top:2rem;
}

.rd-card {
  background:#f7f7f7; /* light gray solid background */
  border-radius:12px;
  padding:1rem;
  max-width:340px;
  text-align:center;
  box-shadow:0 4px 12px rgba(0,0,0,0.1); /* subtle shadow */
  border:1px solid #e5e5e5; /* light border for definition */
  transition: transform 0.25s, box-shadow 0.25s;
}

.rd-card:hover {
  transform: translateY(-5px);
  box-shadow:0 8px 20px rgba(0,0,0,0.15); /* stronger shadow on hover */
}

.rd-card img {
  width:100%;
  height:200px; /* consistent with your other cards */
  object-fit:cover;
  border-radius:8px;
  margin-bottom:0.75rem;
}

.rd-card h3 {
  margin:0.5rem 0;
}

.rd-card h3 a {
  text-decoration:none;
  color:#222; /* dark readable text */
  transition:color 0.25s;
}

.rd-card h3 a:hover {
  color:#0055a5; /* brand blue hover */
}

.rd-card p {
  color:#555; /* medium-dark text for readability */
  margin-bottom:1rem;
  font-size:0.95rem;
  line-height:1.5;
}

.rd-btn {
  display:inline-block;
  padding:0.55rem 1rem;
  border-radius:6px; /* matches other buttons */
  text-decoration:none;
  font-weight:bold;
  background:#0055a5;
  color:#fff;
  transition:background 0.25s;
}

.rd-btn:hover {
  background:#003f7d; /* darker on hover */
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
    <a href="/academics/">
      <img src="/images/tensorsimage.png" alt="Academic Work">
    </a>
    <h3><a href="/academics/">Academic Work</a></h3>
    <p> Notes, coursework, research, and academic projects on applied mathematics in fluid dynamics, compressible flow, and related topics.</p>
    <a class="rd-btn" href="/academics/">View Academic Work</a>
  </div>

  <div class="rd-card">
    <a href="/portfolio/">
      <img src="/images/portfolioimage.png" alt="Portfolio">
    </a>
    <h3><a href="/portfolio/">Portfolio</a></h3>
    <p>A curated selection of projects, models, and designs that I have built. </p>
    <a class="rd-btn" href="/portfolio/">View Portfolio</a>
  </div>

<!-- Footer CTA -->
<div style="text-align:center; padding:4rem 2rem; background:#f0f0f0;">
  <p style="font-size:1.1rem; margin-bottom:1rem;">Interested in collaborating or learning more about my work?</p>
  
  <!-- Contact info -->
  <p style="font-size:1rem; margin:0.25rem 0;">Email: raymonddunn25@gmail.com,  rdunn1@uci.edu </p>
  <p style="font-size:1rem; margin:0.25rem 0;">LinkedIn: <a href="https://www.linkedin.com/in/raymond-dunn-b13362200" target="_blank" style="color:#0a66c2; text-decoration:none;">linkedin.com/in/raymond-dunn-b13362200</a></p>
  
  <!-- Optional button links -->
  <div style="display:flex; justify-content:center; gap:1rem; flex-wrap:wrap; margin-top:1rem;">
    <a href="mailto: raymonddunn25@gmail.com" style="padding:0.75rem 1.5rem; background-color:#0055a5; color:#fff; border-radius:8px; text-decoration:none; font-weight:bold;">Email Me</a>
    <a href="https://www.linkedin.com/in/raymond-dunn-b13362200" target="_blank" style="padding:0.75rem 1.5rem; background-color:#0a66c2; color:#fff; border-radius:8px; text-decoration:none; font-weight:bold;">LinkedIn</a>
  </div>
</div>



