---
layout: splash
title: "Example Page with Sidebar TOC"
permalink: /testscroll/
---

<!-- Sidebar TOC -->
<div class="sidebar-toc">
  <h3>Table of Contents</h3>
  <ul>
    <li><a href="#introduction">Introduction</a></li>
    <li>
      <a href="#section-1">Section 1</a>
      <ul>
        <li><a href="#subsection-1-1">Subsection 1.1</a></li>
        <li><a href="#subsection-1-2">Subsection 1.2</a></li>
      </ul>
    </li>
    <li><a href="#section-2">Section 2</a></li>
    <li><a href="#conclusion">Conclusion</a></li>
  </ul>
</div>


<h2 id="introduction">Introduction</h2>
<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec nec purus eu ligula aliquet bibendum.jfioasjfioasdjfioasdjfio sjfioasjdfoiasjiofdjsaiodfj ioafadsfasdfsfsafjasfjiasfjioasfjioasjfio adfasdfasdfsdfa</p>
<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur nec odio ac sapien ultricies laoreet.</p>
<p>Aliquam erat volutpat. Vestibulum euismod turpis vitae mauris malesuada, et interdum lectus pharetra.</p>

<h2 id="section-1">Section 1</h2>
<p>Phasellus posuere, urna eget egestas tincidunt, libero felis ultrices urna, sit amet hendrerit velit urna at felis.</p>
<p>Donec blandit suscipit ligula, vitae efficitur leo. Sed vitae risus eget orci porta vestibulum.</p>
<p>Vivamus ut imperdiet eros. Morbi suscipit, ligula nec fringilla congue, felis erat fringilla odio, a eleifend lorem nisi nec lorem.</p>

<h3 id="subsection-1-1">Subsection 1.1</h3>
<p>Suspendisse potenti. Sed ultricies sem at quam ultrices, vel vehicula nunc fermentum.</p>
<p>Nullam nec justo eget risus scelerisque varius. Integer vel neque id lacus luctus fermentum.</p>
<p>Etiam sit amet congue risus, eget tincidunt ipsum. Sed eu velit ac augue ultricies efficitur.</p>

<h3 id="subsection-1-2">Subsection 1.2</h3>
<p>Integer euismod, nisl a sodales varius, ex eros suscipit nulla, ac varius metus turpis ac lacus.</p>
<p>Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas.</p>
<p>Curabitur sodales, nisl a tempor tristique, nulla mi ullamcorper orci, non porta lectus mi sed massa.</p>

<h2 id="section-2">Section 2</h2>
<p>Fusce facilisis massa id dui tincidunt, vel ultricies est gravida. Aliquam erat volutpat.</p>
<p>Proin ac arcu eu augue bibendum commodo. Donec feugiat metus nec magna tincidunt.</p>
<p>Sed et ligula tincidunt, luctus purus a, tristique ipsum. Donec vitae arcu est.</p>
<p>Sed bibendum, lacus nec fermentum ullamcorper, eros eros vehicula magna, ut varius ligula turpis eget nunc.</p>
<p>Phasellus posuere felis nec ligula feugiat ullamcorper. Duis sed lacinia sapien, non suscipit sapien.</p>
<p>Praesent at lacinia nibh. Suspendisse et erat velit. Nullam ac nunc felis.</p>

<h2 id="conclusion">Conclusion</h2>
<p>Donec tristique elit in erat ultricies, nec malesuada turpis dapibus.</p>
<p>Aliquam erat volutpat. Cras nec est eros. Donec at convallis nisi.</p>
<p>Sed rhoncus, urna nec posuere gravida, nisi justo varius erat, nec convallis eros nisl eget ligula.</p>


<!-- CSS -->
<style>
.page-content {
  margin-right: 270px; /* push main text to the left of sidebar */
  max-width: 700px;
}

.sidebar-toc {
  position: fixed;
  top: 100px;
  right: 20px; /* move to right */
  width: 220px;
  max-height: 80vh;
  overflow-y: auto;
  padding: 1rem;
  background: #f8f9fa;
  border: 1px solid #ddd;
  border-radius: 8px;
  font-size: 0.95rem;
}

.sidebar-toc h3 {
  margin-top: 0;
  font-size: 1.1rem;
  border-bottom: 1px solid #ccc;
  padding-bottom: 0.5rem;
}

.sidebar-toc ul {
  list-style: none;
  padding-left: 0;
}

.sidebar-toc li {
  margin: 0.4rem 0;
}

.sidebar-toc a {
  text-decoration: none;
  color: #333;
}

.sidebar-toc a:hover {
  color: #007acc;
}

.sidebar-toc a.active {
  font-weight: bold;
  color: #007acc;
}
</style>

<!-- Optional JS for active section highlighting -->
<script>
document.addEventListener("scroll", function () {
  const links = document.querySelectorAll(".sidebar-toc a");
  let current = "";
  document.querySelectorAll("h2, h3").forEach(section => {
    const sectionTop = section.offsetTop - 130;
    if (window.scrollY >= sectionTop) {
      current = section.getAttribute("id");
    }
  });
  links.forEach(link => {
    link.classList.remove("active");
    if (link.getAttribute("href") === "#" + current) {
      link.classList.add("active");
    }
  });
});
</script>
