<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Jhon Albert Toledo | Portfolio</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&family=Space+Grotesk:wght@500;700&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    :root {
      --primary: #6366f1;
      --primary-dark: #4f46e5;
      --secondary: #ec4899;
      --accent: #06b6d4;
      --dark: #0f172a;
      --darker: #020617;
      --light: #f8fafc;
      --gray: #94a3b8;
      --active-color: #10b981;
    }

    body {
      font-family: 'Inter', sans-serif;
      background: linear-gradient(135deg, var(--darker) 0%, var(--dark) 100%);
      color: var(--light);
      min-height: 100vh;
      overflow-x: hidden;
      line-height: 1.6;
    }

    /* Animated Background */
    .bg-animation {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: -1;
      overflow: hidden;
    }

    .bg-animation span {
      position: absolute;
      width: 20px;
      height: 20px;
      background: rgba(99, 102, 241, 0.1);
      border-radius: 50%;
      animation: float 15s infinite;
    }

    @keyframes float {
      0%, 100% { transform: translateY(0) rotate(0deg); opacity: 0; }
      10% { opacity: 1; }
      90% { opacity: 1; }
      100% { transform: translateY(-100vh) rotate(720deg); opacity: 0; }
    }

    /* Navigation Buttons */
    nav {
      position: fixed;
      top: 0;
      width: 100%;
      padding: 1.5rem 5%;
      background: rgba(15, 23, 42, 0.9);
      backdrop-filter: blur(20px);
      z-index: 1000;
      border-bottom: 1px solid rgba(255,255,255,0.1);
    }

    nav ul {
      list-style: none;
      display: flex;
      justify-content: center;
      gap: 1rem;
      flex-wrap: wrap;
    }

    nav a {
      color: var(--gray);
      text-decoration: none;
      font-weight: 600;
      padding: 0.8rem 1.5rem;
      border-radius: 50px;
      transition: all 0.3s ease;
      position: relative;
      border: 2px solid transparent;
      background: rgba(255,255,255,0.05);
    }

    nav a:hover {
      color: var(--light);
      background: rgba(99, 102, 241, 0.2);
      border-color: var(--primary);
      transform: translateY(-2px);
      box-shadow: 0 5px 20px rgba(99, 102, 241, 0.3);
    }

    nav a.active {
      background: linear-gradient(135deg, var(--primary), var(--secondary));
      color: white;
      border-color: transparent;
      box-shadow: 0 5px 20px rgba(99, 102, 241, 0.4);
      transform: scale(1.05);
    }

    /* Hero Section */
    .hero {
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 2rem;
      position: relative;
    }

    .hero-content {
      text-align: center;
      max-width: 800px;
    }

    .profile-container {
      position: relative;
      display: inline-block;
      margin-bottom: 2rem;
      opacity: 0;
      animation: fadeInUp 1s ease-out forwards;
    }

    .profile-pic {
      width: 200px;
      height: 200px;
      border-radius: 50%;
      object-fit: cover;
      border: 4px solid transparent;
      background: linear-gradient(var(--dark), var(--dark)) padding-box,
                  linear-gradient(135deg, var(--primary), var(--secondary), var(--accent)) border-box;
      box-shadow: 0 20px 60px rgba(99, 102, 241, 0.3);
      transition: transform 0.3s, box-shadow 0.3s;
      animation: floatProfile 3s ease-in-out infinite;
    }

    @keyframes floatProfile {
      0%, 100% { transform: translateY(0px); }
      50% { transform: translateY(-10px); }
    }

    .profile-pic:hover {
      transform: scale(1.05);
      box-shadow: 0 30px 80px rgba(99, 102, 241, 0.5);
    }

    .status-badge {
      position: absolute;
      bottom: 10px;
      right: 10px;
      background: #10b981;
      width: 30px;
      height: 30px;
      border-radius: 50%;
      border: 4px solid var(--dark);
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0%, 100% { box-shadow: 0 0 0 0 rgba(16, 185, 129, 0.7); }
      50% { box-shadow: 0 0 0 10px rgba(16, 185, 129, 0); }
    }

    /* Name with Side Fade + Smith Effect */
    .name-container {
      margin-bottom: 0.5rem;
      overflow: hidden;
    }

    h1 {
      font-family: 'Space Grotesk', sans-serif;
      font-size: 4rem;
      font-weight: 700;
      background: linear-gradient(90deg, var(--light) 0%, var(--primary) 25%, var(--secondary) 50%, var(--primary) 75%, var(--light) 100%);
      background-size: 200% auto;
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      letter-spacing: -2px;
      animation: sideFadeIn 1s ease-out forwards, shine 3s linear infinite;
      display: inline-block;
      opacity: 0;
      transform: translateX(-100px);
    }

    @keyframes sideFadeIn {
      0% {
        opacity: 0;
        transform: translateX(-100px);
      }
      100% {
        opacity: 1;
        transform: translateX(0);
      }
    }

    @keyframes shine {
      0% { background-position: 200% center; }
      100% { background-position: -200% center; }
    }

    /* Tagline with Side Fade from Right */
    .tagline {
      font-size: 1.5rem;
      color: var(--gray);
      margin-bottom: 2rem;
      font-weight: 300;
      opacity: 0;
      transform: translateX(100px);
      animation: sideFadeInRight 1s ease-out 0.5s forwards;
    }

    @keyframes sideFadeInRight {
      0% {
        opacity: 0;
        transform: translateX(100px);
      }
      100% {
        opacity: 1;
        transform: translateX(0);
      }
    }

    .location {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      color: var(--accent);
      font-weight: 500;
      margin-bottom: 2rem;
      opacity: 0;
      animation: fadeInUp 1s ease-out 0.8s forwards;
    }

    @keyframes fadeInUp {
      from {
        opacity: 0;
        transform: translateY(30px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    @keyframes fadeIn {
      to { opacity: 1; }
    }

    .cta-buttons {
      display: flex;
      gap: 1rem;
      justify-content: center;
      flex-wrap: wrap;
      opacity: 0;
      animation: fadeInUp 1s ease-out 1s forwards;
    }

    .btn {
      padding: 1rem 2rem;
      border-radius: 50px;
      text-decoration: none;
      font-weight: 600;
      transition: all 0.3s;
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
    }

    .btn-primary {
      background: linear-gradient(135deg, var(--primary), var(--primary-dark));
      color: white;
      box-shadow: 0 10px 30px rgba(99, 102, 241, 0.4);
    }

    .btn-primary:hover {
      transform: translateY(-3px);
      box-shadow: 0 20px 40px rgba(99, 102, 241, 0.6);
    }

    .btn-secondary {
      border: 2px solid rgba(255,255,255,0.2);
      color: var(--light);
      background: rgba(255,255,255,0.05);
    }

    .btn-secondary:hover {
      background: rgba(255,255,255,0.1);
      border-color: var(--primary);
    }

    /* Sections */
    section {
      padding: 6rem 2rem;
      max-width: 1200px;
      margin: 0 auto;
    }

    .section-title {
      font-family: 'Space Grotesk', sans-serif;
      font-size: 2.5rem;
      text-align: center;
      margin-bottom: 3rem;
      position: relative;
      display: inline-block;
      left: 50%;
      transform: translateX(-50%);
    }

    .section-title::after {
      content: '';
      position: absolute;
      bottom: -10px;
      left: 50%;
      transform: translateX(-50%);
      width: 60px;
      height: 4px;
      background: linear-gradient(90deg, var(--primary), var(--secondary));
      border-radius: 2px;
    }

    /* About Section */
    .about-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 2rem;
      margin-top: 3rem;
    }

    .info-card {
      background: rgba(255,255,255,0.03);
      border: 1px solid rgba(255,255,255,0.1);
      border-radius: 20px;
      padding: 2rem;
      text-align: center;
      transition: all 0.3s;
      backdrop-filter: blur(10px);
    }

    .info-card:hover {
      transform: translateY(-10px);
      border-color: var(--primary);
      box-shadow: 0 20px 40px rgba(99, 102, 241, 0.2);
    }

    .info-card .icon {
      font-size: 2.5rem;
      margin-bottom: 1rem;
    }

    .info-card h3 {
      color: var(--primary);
      margin-bottom: 0.5rem;
      font-size: 1.2rem;
    }

    .info-card p {
      color: var(--gray);
      font-size: 0.95rem;
    }

    /* Skills Section */
    .skills-container {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 1.5rem;
      margin-top: 3rem;
    }

    .skill-tag {
      background: linear-gradient(135deg, rgba(99, 102, 241, 0.1), rgba(236, 72, 153, 0.1));
      border: 1px solid rgba(99, 102, 241, 0.3);
      padding: 1rem 2rem;
      border-radius: 50px;
      font-weight: 600;
      color: var(--light);
      transition: all 0.3s;
      position: relative;
      overflow: hidden;
    }

    .skill-tag::before {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 100%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
      transition: left 0.5s;
    }

    .skill-tag:hover {
      transform: translateY(-5px);
      border-color: var(--secondary);
      box-shadow: 0 10px 30px rgba(236, 72, 153, 0.3);
    }

    .skill-tag:hover::before {
      left: 100%;
    }

    /* Journey Section */
    .journey {
      background: rgba(255,255,255,0.02);
      border-radius: 30px;
      padding: 3rem;
      margin-top: 3rem;
      border: 1px solid rgba(255,255,255,0.05);
    }

    .journey-item {
      display: flex;
      align-items: flex-start;
      gap: 2rem;
      margin-bottom: 2rem;
      position: relative;
      padding-left: 2rem;
    }

    .journey-item::before {
      content: '';
      position: absolute;
      left: 0;
      top: 0;
      bottom: -2rem;
      width: 2px;
      background: linear-gradient(to bottom, var(--primary), var(--secondary));
    }

    .journey-item:last-child::before {
      display: none;
    }

    .journey-dot {
      width: 20px;
      height: 20px;
      background: var(--primary);
      border-radius: 50%;
      position: absolute;
      left: -9px;
      top: 0;
      box-shadow: 0 0 20px var(--primary);
    }

    .journey-content h4 {
      color: var(--light);
      margin-bottom: 0.5rem;
      font-size: 1.3rem;
    }

    .journey-content p {
      color: var(--gray);
    }

    /* Projects Section */
    .projects-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 2rem;
      margin-top: 3rem;
    }

    .project-card {
      background: rgba(255,255,255,0.03);
      border: 1px solid rgba(255,255,255,0.1);
      border-radius: 20px;
      padding: 2.5rem;
      text-align: center;
      transition: all 0.3s;
      text-decoration: none;
      color: inherit;
      display: block;
    }

    .project-card:hover {
      transform: translateY(-10px);
      border-color: var(--accent);
      box-shadow: 0 20px 40px rgba(6, 182, 212, 0.2);
    }

    .project-icon {
      font-size: 3rem;
      margin-bottom: 1rem;
    }

    .project-title {
      font-size: 1.3rem;
      font-weight: 600;
      margin-bottom: 0.5rem;
      color: var(--accent);
    }

    .project-desc {
      color: var(--gray);
      margin-bottom: 1rem;
    }

    .project-status {
      display: inline-block;
      padding: 0.5rem 1rem;
      background: var(--primary);
      color: white;
      border-radius: 20px;
      font-size: 0.85rem;
      font-weight: 600;
    }

    /* Contact Section */
    .contact-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 2rem;
      margin-top: 3rem;
    }

    .contact-card {
      background: linear-gradient(135deg, rgba(99, 102, 241, 0.1), rgba(6, 182, 212, 0.1));
      border: 1px solid rgba(255,255,255,0.1);
      border-radius: 20px;
      padding: 2.5rem;
      text-align: center;
      transition: all 0.3s;
      text-decoration: none;
      color: inherit;
      display: block;
    }

    .contact-card:hover {
      transform: translateY(-10px) scale(1.02);
      border-color: var(--accent);
      box-shadow: 0 20px 40px rgba(6, 182, 212, 0.2);
    }

    .contact-icon {
      width: 60px;
      height: 60px;
      background: rgba(99, 102, 241, 0.2);
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      margin: 0 auto 1.5rem;
      font-size: 1.5rem;
      transition: all 0.3s;
    }

    .contact-card:hover .contact-icon {
      background: var(--primary);
      transform: rotate(360deg);
    }

    .contact-card h3 {
      margin-bottom: 0.5rem;
      color: var(--light);
    }

    .contact-card p {
      color: var(--gray);
      font-size: 0.9rem;
    }

    /* Footer */
    footer {
      text-align: center;
      padding: 3rem 2rem;
      border-top: 1px solid rgba(255,255,255,0.1);
      color: var(--gray);
      margin-top: 4rem;
    }

    .social-links {
      display: flex;
      justify-content: center;
      gap: 1.5rem;
      margin-bottom: 2rem;
    }

    .social-links a {
      width: 50px;
      height: 50px;
      border: 1px solid rgba(255,255,255,0.2);
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      color: var(--light);
      text-decoration: none;
      transition: all 0.3s;
      font-size: 1.2rem;
    }

    .social-links a:hover {
      background: var(--primary);
      border-color: var(--primary);
      transform: translateY(-5px);
    }

    /* Animations */
    .fade-in {
      opacity: 0;
      transform: translateY(30px);
      transition: all 0.8s ease-out;
    }

    .fade-in.visible {
      opacity: 1;
      transform: translateY(0);
    }

    /* Responsive */
    @media (max-width: 768px) {
      h1 { font-size: 2.5rem; }
      .tagline { font-size: 1.2rem; }
      nav ul { gap: 0.5rem; }
      nav a { padding: 0.6rem 1rem; font-size: 0.9rem; }
      .section-title { font-size: 2rem; }
      .profile-pic { width: 150px; height: 150px; }
    }
  </style>
</head>
<body>

  <!-- Animated Background -->
  <div class="bg-animation" id="bgAnimation"></div>

  <!-- Navigation -->
  <nav>
    <ul>
      <li><a href="#home" class="nav-link active">Home</a></li>
      <li><a href="#about" class="nav-link">About Me</a></li>
      <li><a href="#skills" class="nav-link">Skills</a></li>
      <li><a href="#projects" class="nav-link">Projects</a></li>
      <li><a href="#contact" class="nav-link">Contact</a></li>
    </ul>
  </nav>

  <!-- Hero Section -->
  <section class="hero" id="home">
    <div class="hero-content">
      <div class="profile-container">
        <img src="https://kimi-web-img.moonshot.cn/img/avatarfiles.alphacoders.com/61b474d32d050d0872745eb02175c2a947d7cf41.jpg" alt="Jhon Albert Toledo Anime Profile" class="profile-pic">
        <div class="status-badge"></div>
      </div>
      <div class="name-container">
        <h1>Jhon Albert Toledo</h1>
      </div>
      <p class="tagline">✨ Aspiring Web Developer & Creative Thinker ✨</p>
      <div class="location">
        <svg width="20" height="20" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"></path>
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"></path>
        </svg>
        Iloilo City, Philippines
      </div>
      <div class="cta-buttons">
        <a href="#contact" class="btn btn-primary">
          <span>Get In Touch</span>
          <svg width="20" height="20" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"></path>
          </svg>
        </a>
        <a href="#about" class="btn btn-secondary">Learn More</a>
      </div>
    </div>
  </section>

  <!-- About Section -->
  <section id="about">
    <h2 class="section-title fade-in">About Me</h2>
    <div class="about-grid fade-in">
      <div class="info-card">
        <div class="icon">🎂</div>
        <h3>Age</h3>
        <p>19 years old</p>
      </div>
      <div class="info-card">
        <div class="icon">📅</div>
        <h3>Birthday</h3>
        <p>May 12, 2006</p>
      </div>
      <div class="info-card">
        <div class="icon">📍</div>
        <h3>Location</h3>
        <p>Iloilo City, Philippines</p>
      </div>
      <div class="info-card">
        <div class="icon">🎯</div>
        <h3>Goal</h3>
        <p>Become a Professional Web Developer</p>
      </div>
    </div>
    
    <div class="journey fade-in">
      <div class="journey-item">
        <div class="journey-dot"></div>
        <div class="journey-content">
          <h4>Current Focus</h4>
          <p>Learning HTML, CSS, and JavaScript fundamentals. Building responsive and interactive web experiences.</p>
        </div>
      </div>
      <div class="journey-item">
        <div class="journey-dot"></div>
        <div class="journey-content">
          <h4>Passion</h4>
          <p>Creating beautiful, user-friendly websites that make a difference. Always eager to learn new technologies.</p>
        </div>
      </div>
      <div class="journey-item">
        <div class="journey-dot"></div>
        <div class="journey-content">
          <h4>Future Vision</h4>
          <p>Mastering modern frameworks like React and Vue.js, contributing to open-source projects, and building innovative web applications.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- Skills Section -->
  <section id="skills">
    <h2 class="section-title fade-in">Technical Skills</h2>
    <div class="skills-container fade-in">
      <div class="skill-tag">HTML5</div>
      <div class="skill-tag">CSS3</div>
      <div class="skill-tag">JavaScript</div>
      <div class="skill-tag">Responsive Design</div>
      <div class="skill-tag">UI/UX Basics</div>
      <div class="skill-tag">Git & GitHub</div>
    </div>
  </section>

  <!-- Projects Section -->
  <section id="projects">
    <h2 class="section-title fade-in">Projects</h2>
    <div class="projects-grid fade-in">
      <div class="project-card">
        <div class="project-icon">🚀</div>
        <div class="project-title">Project Alpha</div>
        <div class="project-desc">Coming Soon - An innovative web application that will revolutionize user experience.</div>
        <span class="project-status">SOON</span>
      </div>
      <div class="project-card">
        <div class="project-icon">💡</div>
        <div class="project-title">Project Beta</div>
        <div class="project-desc">Coming Soon - A creative solution for everyday problems using modern web technologies.</div>
        <span class="project-status">SOON</span>
      </div>
      <div class="project-card">
        <div class="project-icon">🎨</div>
        <div class="project-title">Project Gamma</div>
        <div class="project-desc">Coming Soon - An artistic platform showcasing the intersection of design and functionality.</div>
        <span class="project-status">SOON</span>
      </div>
    </div>
  </section>

  <!-- Contact Section -->
  <section id="contact">
    <h2 class="section-title fade-in">Let's Connect</h2>
    <div class="contact-grid fade-in">
      <a href="mailto:jhontoledo1w@gmail.com" class="contact-card">
        <div class="contact-icon">✉️</div>
        <h3>Email</h3>
        <p>jhontoledo1w@gmail.com</p>
      </a>
      <a href="tel:+639630374922" class="contact-card">
        <div class="contact-icon">📱</div>
        <h3>Phone</h3>
        <p>0963 037 4922</p>
      </a>
      <a href="https://www.tiktok.com" target="_blank" class="contact-card">
        <div class="contact-icon">🎵</div>
        <h3>TikTok</h3>
        <p>Follow my journey</p>
      </a>
    </div>
  </section>

  <!-- Footer -->
  <footer>
    <div class="social-links">
      <a href="#" title="GitHub">GH</a>
      <a href="#" title="LinkedIn">LI</a>
      <a href="#" title="Twitter">TW</a>
      <a href="#" title="Instagram">IG</a>
    </div>
    <p>&copy; 2026 Jhon Albert Toledo. Crafted with passion.</p>
  </footer>

  <script>
    // Animated Background Particles
    const bgAnimation = document.getElementById('bgAnimation');
    for (let i = 0; i < 50; i++) {
      const span = document.createElement('span');
      span.style.left = Math.random() * 100 + '%';
      span.style.animationDelay = Math.random() * 15 + 's';
      span.style.animationDuration = (Math.random() * 10 + 10) + 's';
      bgAnimation.appendChild(span);
    }

    // Navigation Active State
    const navLinks = document.querySelectorAll('.nav-link');
    const sections = document.querySelectorAll('section');

    navLinks.forEach(link => {
      link.addEventListener('click', function(e) {
        // Remove active class from all links
        navLinks.forEach(l => l.classList.remove('active'));
        // Add active class to clicked link
        this.classList.add('active');
      });
    });

    // Update active nav on scroll
    window.addEventListener('scroll', () => {
      let current = '';
      sections.forEach(section => {
        const sectionTop = section.offsetTop;
        const sectionHeight = section.clientHeight;
        if (pageYOffset >= (sectionTop - 200)) {
          current = section.getAttribute('id');
        }
      });

      navLinks.forEach(link => {
        link.classList.remove('active');
        if (link.getAttribute('href').slice(1) === current) {
          link.classList.add('active');
        }
      });
    });

    // Scroll Animation
    const observerOptions = {
      threshold: 0.1,
      rootMargin: "0px 0px -50px 0px"
    };

    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible');
        }
      });
    }, observerOptions);

    document.querySelectorAll('.fade-in').forEach((el) => observer.observe(el));

    // Smooth Scroll
    document.querySelectorAll('a[href^="#"]').forEach(anchor => {
      anchor.addEventListener('click', function (e) {
        e.preventDefault();
        const target = document.querySelector(this.getAttribute('href'));
        if (target) {
          target.scrollIntoView({ behavior: 'smooth', block: 'start' });
        }
      });
    });
  </script>

</body>
</html>
