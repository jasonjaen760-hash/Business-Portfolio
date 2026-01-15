<!-- NAVBAR -->
<nav>
  <h1><!-- EDIT: Business Name -->My Business</h1>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#services">Services</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#team">Team</a></li>
    <li><a href="#testimonials">Testimonials</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <button id="toggleTheme">Dark Mode</button>
</nav>

<!-- HERO SECTION -->
<header class="hero fade">
  <img src="https://via.placeholder.com/150" class="avatar" alt="Business Logo">
  <h2><!-- EDIT: Tagline -->We Build Premium Solutions</h2>
  <p><!-- EDIT: Short Intro -->Professional, modern, and editable business portfolio template.</p>
  <button class="cta" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">Contact Now</button>
</header>

<!-- ABOUT -->
<section id="about" class="fade">
  <h3>About Us</h3>
  <p><!-- EDIT: About Info -->We are a company committed to providing top-quality web solutions for small and medium businesses.</p>
</section>

<!-- SERVICES -->
<section id="services" class="fade">
  <h3>Our Services</h3>
  <div class="grid">
    <div class="card slide">Web Development</div>
    <div class="card slide">UI/UX Design</div>
    <div class="card slide">Digital Marketing</div>
    <div class="card slide">SEO Optimization</div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects" class="fade">
  <h3>Our Projects</h3>
  <div class="grid">
    <div class="card slide">E-commerce Website</div>
    <div class="card slide">Portfolio Site</div>
    <div class="card slide">Corporate Website</div>
  </div>
</section>

<!-- TEAM -->
<section id="team" class="fade">
  <h3>Meet the Team</h3>
  <div class="grid">
    <div class="card slide">John Doe - CEO</div>
    <div class="card slide">Jane Smith - Designer</div>
    <div class="card slide">Mike Lee - Developer</div>
  </div>
</section>

<!-- TESTIMONIALS -->
<section id="testimonials" class="fade">
  <h3>Testimonials</h3>
  <div class="grid">
    <div class="card slide">"Excellent service, highly recommended!" - Client A</div>
    <div class="card slide">"Our website looks amazing!" - Client B</div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact" class="fade">
  <h3>Contact Us</h3>
  <p><!-- EDIT: Contact Info -->Email: info@mybusiness.com | Phone: 09123456789</p>
</section>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap');

* { margin:0; padding:0; box-sizing:border-box; }

body {
  font-family:"Inter", sans-serif;
  background: linear-gradient(135deg, #ff6fd8, #6fd8ff, #fffb7d);
  background-size: 300% 300%;
  animation: gradientMove 8s ease infinite;
  color:#fff;
  padding: 40px;
  transition: .4s ease;
}

/* NAVBAR */
nav {
  display:flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 40px;
}

.nav-links { display:flex; list-style:none; gap:15px; }

.nav-links li a { color:#fff; text-decoration:none; font-weight:500; }

#toggleTheme {
  padding:8px 14px;
  border:none;
  border-radius:6px;
  background: rgba(0,0,0,0.6);
  color:white;
  cursor:pointer;
}

/* HERO */
.hero { text-align:center; margin-bottom:50px; }
.avatar { width:120px; height:120px; border-radius:100px; margin-bottom:15px; border:3px solid rgba(255,255,255,0.5);}
.hero h2 { font-size:32px; font-weight:700; text-shadow:0 0 12px rgba(255,255,255,.7);}
.hero p { opacity:.8; margin-bottom:20px;}
.cta {
  padding:12px 25px;
  border:none;
  border-radius:8px;
  background: #ff6fd8;
  color:#fff;
  font-weight:600;
  cursor:pointer;
  transition:.3s;
}
.cta:hover { background:#6fd8ff; color:#222; }

/* SECTIONS */
section { margin-bottom:50px;}
section h3 { font-size:24px; margin-bottom:16px; font-weight:600; }
.grid { display:grid; gap:12px; grid-template-columns: repeat(auto-fit,minmax(220px,1fr)); }
.card {
  padding:18px;
  background: rgba(255,255,255,.2);
  backdrop-filter: blur(10px);
  border-radius:12px;
  color:#fff;
  font-weight:500;
  box-shadow: 0 0 12px rgba(255,255,255,.2);
  opacity:0;
  transform: translateY(30px);
  animation: slideUp .7s forwards;
  transition:0.3s ease;
}
.card:hover { transform:translateY(-6px) scale(1.05); box-shadow:0 0 25px rgba(255,255,255,.6); }

/* ANIMATIONS */
.fade { opacity:0; animation: fadeIn 1s forwards; }
@keyframes fadeIn { to{opacity:1;} }
@keyframes slideUp { to{opacity:1; transform:translateY(0);} }
@keyframes gradientMove {0%{background-position:0% 50%;}50%{background-position:100% 50%;}100%{background-position:0% 50%;}}

/* DARK MODE */
body.dark { background: linear-gradient(135deg, #1b1b2f, #162447, #1f4068);}
body.dark .card { background: rgba(255,255,255,.05); border:1px solid rgba(255,255,255,.2);}
// Dark Mode Toggle
const btn = document.getElementById("toggleTheme");
btn.addEventListener("click", () => {
  document.body.classList.toggle("dark");
  btn.textContent =
    document.body.classList.contains("dark") ? "Light Mode" : "Dark Mode";
});

// Hero Typing Effect
const heroText = document.querySelector(".hero h2");
const tagline = "We Build Premium Solutions...";
let index = 0;
function typeEffect() {
  heroText.textContent = tagline.slice(0, index);
  index++;
  if (index <= tagline.length) setTimeout(typeEffect, 100);
}
typeEffect();

// Scroll Reveal Animation
function revealOnScroll() {
  const reveals = document.querySelectorAll(".fade, .slide");
  for (let i = 0; i < reveals.length; i++) {
    const windowHeight = window.innerHeight;
    const elementTop = reveals[i].getBoundingClientRect().top;
    const revealPoint = 150;
    if (elementTop < windowHeight - revealPoint) {
      reveals[i].classList.add("active");
    }
  }
}
window.addEventListener("scroll", revealOnScroll);
