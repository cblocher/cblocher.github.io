<div class="about-layout">

  <div class="about-image">
    <img src="/assets/images/headshot.png" alt="Chris Blocher Headshot" />
  </div>

  <div class="about-content">
    <h1>About me</h1>
    
    <p>Whether you see me as a Technical Writer, Content Designer, Content Strategist, or Instructional Designer, my work centers on a single purpose: helping people reach their goals quickly and confidently.</p>

    <p>Professionally, I strive to help customers perform better on the job. I enjoy uncovering what customers truly need and watching their confidence grow as they apply the solutions we create. I help organizations adopt content practices that raise their overall maturity and make their information more actionable and sustainable.</p>

    <p>I increasingly use AI throughout solution development, from brainstorming to identifying gaps and opportunities. AI-driven critiques and pre-mortems help me explore alternatives early and often.</p>

    <p>Personally, I’ve learned that content works best when it’s connected across the organization…not siloed. When it’s consistent and intelligently reused. And when it’s treated as equal to other phases of the development process.</p>
</div>

</div>

<!-- Roles Section -->
<div class="role-grid">
  <div class="role-card">
    <img src="/assets/images/role-tw.webp" alt="Technical Writer" />
    <h3>Technical Writer</h3>
    <p>I create concept, process, task, and reference topics. Long‑form content doubles as a knowledge base and a product history that supports AI‑driven solutions.</p>
  </div>
  <div class="role-card">
    <img src="/assets/images/role-cd.webp" alt="Content Designer" />
    <h3>Content Designer</h3>
    <p>I craft labels, messages, and guidance that keep customers moving. Clear and communicative workflows build confidence, trust, and retention.</p>
  </div>
  <div class="role-card">
    <img src="/assets/images/role-cs.webp" alt="Content Strategist" />
    <h3>Content Strategist</h3>
    <p>I align business goals with customer needs by setting clear content priorities and success metrics. Content outcomes scale with data, research, and cross‑functional partnerships.</p>
  </div>
  <div class="role-card">
    <img src="/assets/images/role-id.webp" alt="Instructional Designer" />
    <h3>Instructional Designer</h3>
    <p>I apply the 5 Moments of Need framework to design workflows, learning experiences, and performance support. Low‑risk tasks benefit from digital coaching. High‑risk tasks require hands‑on instruction.</p>
  </div>
</div>

<!-- Quotes Carousel -->
<div class="quote-carousel-wrapper">
  <div class="quote-carousel">
    <blockquote class="quote-card">
      <p>"Being a new hire is quite daunting, but Chris has been a kind and inclusive mentor. He was patient with all my questions as I ramped up on my first project. His wealth of knowledge is immeasurable, and he shares it generously."</p>
      <footer><strong>New Content Designer, Content Experience</strong></footer>
    </blockquote>
    <blockquote class="quote-card">
      <p>"Chris fully supported the extensions project and provided an innovative way to reuse learning content assets. With the new method, Designers can work on design assets more flexibly without constraints or additional Dev efforts."</p>
      <footer><strong>Design Manager, User Experience</strong></footer>
    </blockquote>
    <blockquote class="quote-card">
      <p>"Thank you for your contribution to the Editorial Style Council! You raised so many great issues and could always be counted on. Developing editorial style guidelines is challenging. I appreciate your commitment to keeping the art and craft front and center."</p>
      <footer><strong>Content Strategy Manager, Brand</strong></footer>
    </blockquote>
    <blockquote class="quote-card">
      <p>"Chris brings strong domain expertise and a rare ability to identify common solutions to hard, ambiguous problems. He is a master of his craft and genuinely a pleasure to work alongside."</p>
      <footer><strong>Frontend Manager, Engineering</strong></footer>
    </blockquote>
    <blockquote class="quote-card">
      <p>"He asks the right questions to get to the essence of what problem we are solving. At every moment he was a team player that would partner and understand the best approach."</p>
      <footer><strong>Technical Program Manager, Product</strong></footer>
    </blockquote>
  </div>
  <div class="carousel-nav">
    <span class="dot"></span><span class="dot"></span><span class="dot"></span><span class="dot"></span><span class="dot"></span>
  </div>
</div>

<script>
  // Simple script for quote carousel dots
  const carousel = document.querySelector('.quote-carousel');
  const dots = document.querySelectorAll('.carousel-nav .dot');
  
  if(carousel && dots.length > 0) {
    carousel.addEventListener('scroll', () => {
      let index = Math.round(carousel.scrollLeft / carousel.offsetWidth);
      dots.forEach((dot, i) => {
        dot.classList.toggle('active', i === index);
      });
    });
    // Set initial
    dots[0].classList.add('active');
    
    // Click dots to scroll
    dots.forEach((dot, i) => {
      dot.addEventListener('click', () => {
        carousel.scrollTo({
          left: i * carousel.offsetWidth,
          behavior: 'smooth'
        });
      });
    });
  }
</script>

<!-- Certification Section -->
<div class="cert-grid">
  <a href="https://www.coursera.org/professional-certificates/google-ai" target="_blank" class="cert-card">
    <img src="/assets/images/cert-google-ai.png" alt="Google AI Professional" />
    <span class="cert-title">Google AI Professional</span>
    <span class="cert-link-text">Program &rarr;</span>
  </a>
  <a href="https://www.applysynergies.com/5-moments-of-need-design-program/" target="_blank" class="cert-card">
    <img src="/assets/images/cert-5-moments.png" alt="5 Moments of Need" />
    <span class="cert-title">5 Moments of Need</span>
    <span class="cert-link-text">Program &rarr;</span>
  </a>
  <a href="https://www.pendo.io/academy/" target="_blank" class="cert-card">
    <img src="/assets/images/cert-pendo.png" alt="Pendo Administrator" />
    <span class="cert-title">Pendo Administrator</span>
    <span class="cert-link-text">Program &rarr;</span>
  </a>
  <a href="https://www.td.org/" target="_blank" class="cert-card">
    <img src="/assets/images/cert-atd.png" alt="Association for Talent Development" />
    <span class="cert-title">Association for Talent Development</span>
    <span class="cert-link-text">Site &rarr;</span>
  </a>
</div>

<div class="mentorship-section">
  <p style="text-align: center; font-size: 1.25rem;"><strong>Let's talk!</strong><br>I believe in giving back to the generous community that helped shape my career. Recently, I've begun mentoring on ADPList to assist aspiring designers unlock their content-design potential. Whether you're navigating a career transition due to AI or just untangling a complex content model, I'm here to help.</p>

  <div class="widget-wrapper" style="height: 496px; width: 100%; max-width: 650px; margin: 2rem auto 0 auto;">
    <iframe src="https://adplist.org/mentors/chris-blocher?session=52227-mentorship-session" title="Book a mentoring session with Chris" width="100%" height="100%" loading="lazy" style="border: 0px;"></iframe>
  </div>

  <p style="text-align: center; margin-top: 1rem;">Also consider providing guidance to students on <a href="https://www.careervillage.org">CareerVillage.org</a>!</p>
</div>
