<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Richard — Frontend Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:ital,wght@0,400;0,700;1,400&family=Bebas+Neue&family=Outfit:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
 :root {
   --bg: #03030a;
   --card: #0c0c18;
   --border: #16162a;
   --text: #e8e6ff;
   --muted: #5a587a;
   --dim: #2a2845;
   --accent: #7b5ea7;
   --glow: #a78bfa;
   --lime: #b8ff57;
   --cyan: #57ffe0;
   --red: #ff5757;
 }

 *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }
 html { scroll-behavior: smooth; }

 body {
   font-family: 'Outfit', sans-serif;
   background: var(--bg);
   color: var(--text);
   overflow-x: hidden;
 }

 body::after {
   content: '';
   position: fixed;
   inset: 0;
   pointer-events: none;
   z-index: 9999;
   opacity: 0.025;
   background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='300' height='300'%3E%3Cfilter id='g'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='300' height='300' filter='url(%23g)' opacity='1'/%3E%3C/svg%3E");
 }

 body { cursor: none; }
 #cursor {
   position: fixed;
   width: 10px; height: 10px;
   background: var(--lime);
   border-radius: 50%;
   pointer-events: none;
   z-index: 10000;
   transform: translate(-50%, -50%);
   transition: transform 0.1s, width 0.2s, height 0.2s, background 0.2s;
   mix-blend-mode: difference;
 }
 #cursor-ring {
   position: fixed;
   width: 36px; height: 36px;
   border: 1px solid rgba(167,139,250,0.4);
   border-radius: 50%;
   pointer-events: none;
   z-index: 9999;
   transform: translate(-50%, -50%);
   transition: transform 0.18s ease, width 0.3s, height 0.3s;
 }

 nav {
   position: fixed;
   top: 0; left: 0; right: 0;
   z-index: 500;
   display: flex;
   justify-content: space-between;
   align-items: center;
   padding: 1.1rem 3rem;
   background: rgba(3,3,10,0.8);
   backdrop-filter: blur(20px);
   border-bottom: 1px solid var(--border);
 }

 .nav-brand {
   font-family: 'Bebas Neue', sans-serif;
   font-size: 1.4rem;
   letter-spacing: .15em;
   color: var(--text);
   text-decoration: none;
 }
 .nav-brand span { color: var(--lime); }
 .nav-links { display: flex; gap: 2.5rem; align-items: center; }
 .nav-links a {
   font-family: 'Space Mono', monospace;
   font-size: 0.65rem;
   letter-spacing: .15em;
   text-transform: uppercase;
   color: var(--muted);
   text-decoration: none;
   transition: color .2s;
 }
 .nav-links a:hover { color: var(--lime); }
 .nav-dot {
   width: 8px; height: 8px;
   border-radius: 50%;
   background: var(--lime);
   animation: blink 1.5s step-end infinite;
 }
 @keyframes blink { 50% { opacity: 0; } }

 .hero {
   min-height: 100vh;
   display: grid;
   grid-template-rows: 1fr auto;
   padding: 0 3rem;
   position: relative;
   overflow: hidden;
 }
 .hero-glow {
   position: absolute;
   width: 700px; height: 700px;
   border-radius: 50%;
   background: radial-gradient(circle, rgba(123,94,167,0.18) 0%, transparent 70%);
   top: -200px; right: -200px;
   pointer-events: none;
 }
 .hero-glow2 {
   position: absolute;
   width: 500px; height: 500px;
   border-radius: 50%;
   background: radial-gradient(circle, rgba(87,255,224,0.05) 0%, transparent 70%);
   bottom: 0; left: -100px;
   pointer-events: none;
 }
 .hero-content {
   display: flex;
   flex-direction: column;
   justify-content: center;
   padding-top: 7rem;
   position: relative;
   z-index: 1;
 }
 .hero-eyebrow {
   font-family: 'Space Mono', monospace;
   font-size: 0.68rem;
   letter-spacing: .3em;
   color: var(--glow);
   text-transform: uppercase;
   margin-bottom: 1.5rem;
   display: flex;
   align-items: center;
   gap: 1rem;
 }
 .hero-eyebrow::before {
   content: '';
   width: 30px; height: 1px;
   background: var(--glow);
 }
 .hero-name {
   font-family: 'Bebas Neue', sans-serif;
   font-size: clamp(5rem, 14vw, 13rem);
   line-height: 0.88;
   letter-spacing: .02em;
   margin-bottom: 1rem;
 }
 .hero-name .line1 { color: var(--text); display: block; }
 .hero-name .line2 {
   color: transparent;
   -webkit-text-stroke: 1px var(--dim);
   display: block;
   transition: -webkit-text-stroke-color .3s;
 }
 .hero-name .line2:hover { -webkit-text-stroke-color: var(--glow); }
 .hero-subtitle {
   font-family: 'Space Mono', monospace;
   font-size: 0.78rem;
   color: var(--muted);
   max-width: 420px;
   line-height: 1.8;
   margin-bottom: 3rem;
   letter-spacing: .03em;
 }
 .hero-subtitle .hl { color: var(--lime); }
 .hero-actions { display: flex; gap: 1rem; flex-wrap: wrap; }

 .btn-primary {
   display: inline-flex;
   align-items: center;
   gap: 0.7rem;
   padding: 0.85rem 2rem;
   background: var(--lime);
   color: #000;
   text-decoration: none;
   font-family: 'Space Mono', monospace;
   font-size: 0.7rem;
   font-weight: 700;
   letter-spacing: .12em;
   text-transform: uppercase;
   transition: all .25s;
   border: 2px solid var(--lime);
 }
 .btn-primary:hover {
   background: transparent;
   color: var(--lime);
   transform: translate(-3px, -3px);
   box-shadow: 6px 6px 0 var(--lime);
 }
 .btn-ghost {
   display: inline-flex;
   align-items: center;
   gap: 0.7rem;
   padding: 0.85rem 2rem;
   background: transparent;
   color: var(--text);
   text-decoration: none;
   font-family: 'Space Mono', monospace;
   font-size: 0.7rem;
   letter-spacing: .12em;
   text-transform: uppercase;
   border: 1px solid var(--dim);
   transition: all .25s;
 }
 .btn-ghost:hover { border-color: var(--glow); color: var(--glow); }

 .hero-bottom {
   padding: 2rem 0;
   border-top: 1px solid var(--border);
   display: flex;
   justify-content: space-between;
   align-items: center;
   position: relative;
   z-index: 1;
 }
 .hero-scroll {
   font-family: 'Space Mono', monospace;
   font-size: 0.6rem;
   letter-spacing: .2em;
   color: var(--muted);
   text-transform: uppercase;
   display: flex;
   align-items: center;
   gap: 0.8rem;
 }
 .hero-scroll-line {
   width: 40px; height: 1px;
   background: var(--muted);
   position: relative;
   overflow: hidden;
 }
 .hero-scroll-line::after {
   content: '';
   position: absolute;
   inset: 0;
   background: var(--lime);
   transform: translateX(-100%);
   animation: scanline 2s ease-in-out infinite;
 }
 @keyframes scanline { to { transform: translateX(100%); } }
 .hero-tags { display: flex; gap: 0.6rem; }
 .hero-tag {
   font-family: 'Space Mono', monospace;
   font-size: 0.6rem;
   padding: 0.3rem 0.8rem;
   border: 1px solid var(--dim);
   color: var(--muted);
   letter-spacing: .1em;
 }

 .section { padding: 7rem 3rem; border-top: 1px solid var(--border); }
 .sec-label {
   font-family: 'Space Mono', monospace;
   font-size: 0.6rem;
   letter-spacing: .3em;
   color: var(--glow);
   text-transform: uppercase;
   margin-bottom: 0.8rem;
   display: flex;
   align-items: center;
   gap: 0.8rem;
 }
 .sec-label::before { content: ''; width: 20px; height: 1px; background: var(--glow); }
 .sec-title {
   font-family: 'Bebas Neue', sans-serif;
   font-size: clamp(2.5rem, 5vw, 4.5rem);
   letter-spacing: .04em;
   line-height: 1;
   margin-bottom: 3rem;
 }

 .about-grid {
   display: grid;
   grid-template-columns: 1.2fr 1fr;
   gap: 5rem;
   align-items: start;
 }
 .about-text p {
   font-size: 0.95rem;
   color: var(--muted);
   line-height: 1.9;
   margin-bottom: 1.2rem;
   font-weight: 300;
 }
 .about-text p strong { color: var(--text); font-weight: 500; }

 .terminal {
   background: var(--card);
   border: 1px solid var(--border);
   border-radius: 8px;
   overflow: hidden;
   font-family: 'Space Mono', monospace;
   font-size: 0.72rem;
 }
 .terminal-bar {
   background: var(--border);
   padding: 0.7rem 1rem;
   display: flex;
   align-items: center;
   gap: 0.5rem;
 }
 .t-dot { width: 10px; height: 10px; border-radius: 50%; }
 .t-dot.r { background: #ff5f57; }
 .t-dot.y { background: #febc2e; }
 .t-dot.g { background: #28c840; }
 .t-title { margin-left: auto; color: var(--muted); font-size: 0.6rem; letter-spacing: .1em; }
 .terminal-body { padding: 1.5rem; line-height: 2; }
 .t-line { display: flex; gap: 0.8rem; }
 .t-prompt { color: var(--glow); }
 .t-cmd { color: var(--lime); }
 .t-out { color: var(--muted); padding-left: 1.5rem; }
 .t-key { color: var(--cyan); }
 .t-val { color: var(--text); }

 .skills-wrap { margin-top: 3rem; }
 .skill-group { margin-bottom: 2.5rem; }
 .skill-group-title {
   font-family: 'Space Mono', monospace;
   font-size: 0.62rem;
   letter-spacing: .2em;
   text-transform: uppercase;
   color: var(--muted);
   margin-bottom: 1rem;
 }
 .skill-pills { display: flex; flex-wrap: wrap; gap: 0.5rem; }
 .skill-pill {
   padding: 0.45rem 1rem;
   font-family: 'Space Mono', monospace;
   font-size: 0.65rem;
   letter-spacing: .08em;
   border: 1px solid var(--border);
   color: var(--text);
   transition: all .2s;
   cursor: default;
   position: relative;
   overflow: hidden;
 }
 .skill-pill::before {
   content: '';
   position: absolute;
   inset: 0;
   background: var(--lime);
   transform: translateX(-101%);
   transition: transform .25s;
   z-index: -1;
 }
 .skill-pill:hover { color: #000; border-color: var(--lime); }
 .skill-pill:hover::before { transform: translateX(0); }

 .projects-list { display: flex; flex-direction: column; gap: 1px; }
 .project-row {
   display: grid;
   grid-template-columns: 80px 1fr auto;
   align-items: center;
   gap: 2rem;
   padding: 2rem 0;
   border-bottom: 1px solid var(--border);
   cursor: pointer;
   transition: background .2s;
   position: relative;
 }
 .project-row::before {
   content: '';
   position: absolute;
   left: -3rem; right: -3rem; top: 0; bottom: 0;
   background: rgba(123,94,167,0.04);
   opacity: 0;
   transition: opacity .2s;
 }
 .project-row:hover::before { opacity: 1; }
 .proj-num {
   font-family: 'Bebas Neue', sans-serif;
   font-size: 2.5rem;
   color: var(--dim);
   line-height: 1;
   transition: color .2s;
 }
 .project-row:hover .proj-num { color: var(--glow); }
 .proj-info h3 {
   font-family: 'Bebas Neue', sans-serif;
   font-size: 1.8rem;
   letter-spacing: .05em;
   margin-bottom: 0.4rem;
   transition: color .2s;
 }
 .project-row:hover .proj-info h3 { color: var(--lime); }
 .proj-info p {
   font-size: 0.8rem;
   color: var(--muted);
   line-height: 1.6;
   max-width: 500px;
 }
 .proj-tags { display: flex; gap: 0.4rem; margin-top: 0.8rem; flex-wrap: wrap; }
 .proj-tag {
   font-family: 'Space Mono', monospace;
   font-size: 0.58rem;
   letter-spacing: .1em;
   padding: 0.2rem 0.5rem;
   border: 1px solid var(--dim);
   color: var(--muted);
 }
 .proj-arrow {
   font-size: 1.5rem;
   color: var(--dim);
   transition: all .2s;
   flex-shrink: 0;
 }
 .project-row:hover .proj-arrow { color: var(--lime); transform: translate(4px, -4px); }

 .contact-grid {
   display: grid;
   grid-template-columns: 1fr 1.2fr;
   gap: 6rem;
   align-items: start;
 }
 .contact-email-link {
   display: flex;
   align-items: center;
   gap: 0.8rem;
   text-decoration: none;
   color: var(--text);
   font-family: 'Space Mono', monospace;
   font-size: 0.72rem;
   letter-spacing: .06em;
   padding-bottom: 0.6rem;
   border-bottom: 1px solid var(--dim);
   transition: all .2s;
   word-break: break-all;
 }
 .contact-email-link:hover { color: var(--lime); border-color: var(--lime); }
 .contact-email-link .icon { font-size: 1rem; flex-shrink: 0; }

 .contact-form { display: flex; flex-direction: column; gap: 1.2rem; }
 .f-row { display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; }
 .f-field { display: flex; flex-direction: column; gap: 0.5rem; }
 .f-field label {
   font-family: 'Space Mono', monospace;
   font-size: 0.58rem;
   letter-spacing: .2em;
   text-transform: uppercase;
   color: var(--muted);
 }
 .f-field input,
 .f-field textarea,
 .f-field select {
   background: var(--card);
   border: 1px solid var(--border);
   padding: 0.85rem 1rem;
   color: var(--text);
   font-family: 'Outfit', sans-serif;
   font-size: 0.85rem;
   outline: none;
   transition: border-color .2s;
   width: 100%;
   appearance: none;
   -webkit-appearance: none;
 }
 .f-field input:focus,
 .f-field textarea:focus,
 .f-field select:focus { border-color: var(--glow); }
 .f-field input::placeholder,
 .f-field textarea::placeholder { color: var(--dim); font-size: 0.8rem; }
 .f-field textarea { min-height: 130px; resize: vertical; }
 .f-check {
   display: flex;
   align-items: center;
   gap: 0.7rem;
   font-size: 0.78rem;
   color: var(--muted);
   cursor: pointer;
 }
 .f-check input { width: 15px; height: 15px; accent-color: var(--lime); cursor: pointer; }
 .f-submit {
   display: flex;
   align-items: center;
   justify-content: space-between;
   padding: 1rem 1.5rem;
   background: var(--lime);
   color: #000;
   border: none;
   font-family: 'Space Mono', monospace;
   font-size: 0.72rem;
   font-weight: 700;
   letter-spacing: .15em;
   text-transform: uppercase;
   cursor: pointer;
   transition: all .25s;
   width: 100%;
 }
 .f-submit:hover {
   background: transparent;
   color: var(--lime);
   box-shadow: inset 0 0 0 2px var(--lime);
 }

 footer {
   padding: 2rem 3rem;
   border-top: 1px solid var(--border);
   display: flex;
   justify-content: space-between;
   align-items: center;
   flex-wrap: wrap;
   gap: 1rem;
 }
 .footer-brand {
   font-family: 'Bebas Neue', sans-serif;
   font-size: 1.1rem;
   letter-spacing: .15em;
   color: var(--muted);
 }
 .footer-brand span { color: var(--lime); }
 .footer-copy {
   font-family: 'Space Mono', monospace;
   font-size: 0.6rem;
   color: var(--muted);
   letter-spacing: .1em;
   text-align: center;
 }
 .footer-status {
   display: flex;
   align-items: center;
   gap: 0.5rem;
   font-family: 'Space Mono', monospace;
   font-size: 0.6rem;
   color: var(--muted);
   letter-spacing: .1em;
 }
 .pulse {
   width: 7px; height: 7px;
   border-radius: 50%;
   background: var(--lime);
   animation: pulseAnim 2s ease-in-out infinite;
 }
 @keyframes pulseAnim {
   0%, 100% { opacity: 1; box-shadow: 0 0 0 0 rgba(184,255,87,0.4); }
   50% { opacity: 0.6; box-shadow: 0 0 0 6px rgba(184,255,87,0); }
 }

 [data-reveal] {
   opacity: 0;
   transform: translateY(30px);
   transition: opacity .8s ease, transform .8s ease;
 }
 [data-reveal].in { opacity: 1; transform: translateY(0); }

 @media (max-width: 900px) {
   nav { padding: 1rem 1.5rem; }
   .hero { padding: 0 1.5rem; }
   .section { padding: 5rem 1.5rem; }
   .about-grid { grid-template-columns: 1fr; gap: 3rem; }
   .contact-grid { grid-template-columns: 1fr; gap: 3rem; }
   .f-row { grid-template-columns: 1fr; }
   .project-row { grid-template-columns: 60px 1fr; }
   .proj-arrow { display: none; }
   footer { padding: 1.5rem; flex-direction: column; text-align: center; }
   body { cursor: auto; }
   #cursor, #cursor-ring { display: none; }
 }
</style>
</head>
<body>

<div id="cursor"></div>
<div id="cursor-ring"></div>

<nav>
 <a class="nav-brand" href="#"><span>R</span>ICHARD</a>
 <div class="nav-links">
   <a href="#about">About</a>
   <a href="#projects">Projects</a>
   <a href="#contact">Contact</a>
   <div class="nav-dot"></div>
 </div>
</nav>

<section class="hero" id="home">
 <div class="hero-glow"></div>
 <div class="hero-glow2"></div>
 <div class="hero-content">
   <div class="hero-eyebrow">Frontend Developer & UI Craftsman</div>
   <h1 class="hero-name">
     <span class="line1">RICHARD</span>
     <span class="line2">BUILDS IT</span>
   </h1>
   <p class="hero-subtitle">
     I write <span class="hl">clean code</span>, craft <span class="hl">pixel-perfect</span> interfaces,
     and turn complex problems into elegant web experiences.
   </p>
   <div class="hero-actions">
     <a href="#projects" class="btn-primary">View Work →</a>
     <a href="#contact" class="btn-ghost">Get in Touch</a>
   </div>
 </div>
 <div class="hero-bottom">
   <div class="hero-scroll">
     <div class="hero-scroll-line"></div>
     Scroll to explore
   </div>
   <div class="hero-tags">
     <span class="hero-tag">HTML</span>
     <span class="hero-tag">CSS</span>
     <span class="hero-tag">JS</span>
     <span class="hero-tag">React</span>
   </div>
 </div>
</section>

<section class="section" id="about">
 <div class="sec-label">01 — About</div>
 <div class="about-grid">
   <div data-reveal>
     <h2 class="sec-title">THE MIND BEHIND THE CODE</h2>
     <div class="about-text">
       <p>Hi, I'm <strong>Richard</strong> — a frontend developer who obsesses over the details that most people never notice but everyone feels.</p>
       <p>I believe that <strong>great software is invisible</strong>. When it works perfectly, users don't think about the code — they just enjoy the experience. That's what I build toward.</p>
       <p>Whether it's a polished UI, a snappy interaction, or a full-stack application, I bring <strong>precision, creativity, and curiosity</strong> to every project I touch.</p>
     </div>
     <div class="skills-wrap">
       <div class="skill-group">
         <div class="skill-group-title">// Frontend</div>
         <div class="skill-pills">
           <span class="skill-pill">HTML5</span>
           <span class="skill-pill">CSS3</span>
           <span class="skill-pill">JavaScript</span>
           <span class="skill-pill">React</span>
           <span class="skill-pill">Responsive Design</span>
         </div>
       </div>
       <div class="skill-group">
         <div class="skill-group-title">// Tools</div>
         <div class="skill-pills">
           <span class="skill-pill">Git</span>
           <span class="skill-pill">VS Code</span>
           <span class="skill-pill">Figma</span>
           <span class="skill-pill">Chrome DevTools</span>
         </div>
       </div>
     </div>
   </div>
   <div data-reveal>
     <div class="terminal">
       <div class="terminal-bar">
         <div class="t-dot r"></div>
         <div class="t-dot y"></div>
         <div class="t-dot g"></div>
         <span class="t-title">richard.json</span>
       </div>
       <div class="terminal-body">
         <div class="t-line"><span class="t-prompt">$</span><span class="t-cmd">cat richard.json</span></div>
         <div style="height:.5rem"></div>
         <div class="t-out">{</div>
         <div class="t-out">&nbsp;&nbsp;<span class="t-key">"name"</span>: <span class="t-val">"Richard"</span>,</div>
         <div class="t-out">&nbsp;&nbsp;<span class="t-key">"role"</span>: <span class="t-val">"Frontend Developer"</span>,</div>
         <div class="t-out">&nbsp;&nbsp;<span class="t-key">"status"</span>: <span class="t-val" style="color:var(--lime)">"Available"</span>,</div>
         <div class="t-out">&nbsp;&nbsp;<span class="t-key">"skills"</span>: [</div>
         <div class="t-out">&nbsp;&nbsp;&nbsp;&nbsp;<span class="t-val">"HTML"</span>, <span class="t-val">"CSS"</span>,</div>
         <div class="t-out">&nbsp;&nbsp;&nbsp;&nbsp;<span class="t-val">"JavaScript"</span>, <span class="t-val">"React"</span></div>
         <div class="t-out">&nbsp;&nbsp;],</div>
         <div class="t-out">&nbsp;&nbsp;<span class="t-key">"passion"</span>: <span class="t-val">"Clean UI"</span>,</div>
         <div class="t-out">&nbsp;&nbsp;<span class="t-key">"coffee"</span>: <span class="t-val" style="color:var(--cyan)">true</span></div>
         <div class="t-out">}</div>
         <div style="height:.5rem"></div>
         <div class="t-line"><span class="t-prompt">$</span><span style="animation:blink 1s step-end infinite;color:var(--lime)">▋</span></div>
       </div>
     </div>
   </div>
 </div>
</section>

<section class="section" id="projects">
 <div class="sec-label">02 — Work</div>
 <h2 class="sec-title">SELECTED PROJECTS</h2>
 <div class="projects-list" data-reveal>

   <div class="project-row">
     <div class="proj-num">01</div>
     <div class="proj-info">
       <h3>Portfolio Website</h3>
       <p>A personal portfolio built to showcase projects and skills with a clean, modern aesthetic and smooth interactions.</p>
       <div class="proj-tags">
         <span class="proj-tag">HTML</span>
         <span class="proj-tag">CSS</span>
         <span class="proj-tag">JavaScript</span>
       </div>
     </div>
     <div class="proj-arrow">↗</div>
   </div>

   <div class="project-row">
     <div class="proj-num">02</div>
     <div class="proj-info">
       <h3>Task Manager App</h3>
       <p>A productivity app with local storage persistence, task prioritization, and a minimal distraction-free UI.</p>
       <div class="proj-tags">
         <span class="proj-tag">JavaScript</span>
         <span class="proj-tag">LocalStorage</span>
         <span class="proj-tag">CSS</span>
       </div>
     </div>
     <div class="proj-arrow">↗</div>
   </div>

   <div class="project-row">
     <div class="proj-num">03</div>
     <div class="proj-info">
       <h3>Landing Page Design</h3>
       <p>A high-conversion landing page with responsive layout, animated sections, and mobile-first design principles.</p>
       <div class="proj-tags">
         <span class="proj-tag">HTML</span>
         <span class="proj-tag">CSS</span>
         <span class="proj-tag">Animations</span>
       </div>
     </div>
     <div class="proj-arrow">↗</div>
   </div>

   <div class="project-row">
     <div class="proj-num">04</div>
     <div class="proj-info">
       <h3>UI Component Library</h3>
       <p>A collection of reusable, accessible UI components built from scratch — buttons, modals, forms, and more.</p>
       <div class="proj-tags">
         <span class="proj-tag">CSS</span>
         <span class="proj-tag">JavaScript</span>
         <span class="proj-tag">Accessibility</span>
       </div>
     </div>
     <div class="proj-arrow">↗</div>
   </div>

 </div>
</section>

<section class="section" id="contact">
 <div class="sec-label">03 — Contact</div>
 <div class="contact-grid">
   <div data-reveal>
     <span style="font-family:'Bebas Neue',sans-serif;font-size:clamp(2.5rem,5vw,4rem);line-height:1;letter-spacing:.04em;display:block;">
       LET'S BUILD<br><span style="color:var(--lime)">SOMETHING</span><br>GREAT
     </span>
     <p style="font-size:0.85rem;color:var(--muted);line-height:1.8;margin:1.5rem 0 2.5rem;">
       Have a project in mind? Looking to collaborate or just want to connect? My inbox is always open.
     </p>
     <a href="mailto:optimalyoungforever@gmail.com" class="contact-email-link">
       <span class="icon">✉</span>
       optimalyoungforever@gmail.com
     </a>
   </div>

   <form class="contact-form" data-reveal onsubmit="submitForm(event)">
     <div class="f-row">
       <div class="f-field">
         <label>Full Name</label>
         <input type="text" placeholder="John Doe" required />
       </div>
       <div class="f-field">
         <label>Email</label>
         <input type="email" placeholder="john@email.com" required />
       </div>
     </div>
     <div class="f-row">
       <div class="f-field">
         <label>Phone</label>
         <input type="tel" placeholder="+1 000 000 0000" />
       </div>
       <div class="f-field">
         <label>Subject</label>
         <select>
           <option value="">General Inquiry</option>
           <option>Project Collaboration</option>
           <option>Freelance Work</option>
           <option>Job Opportunity</option>
         </select>
       </div>
     </div>
     <div class="f-field">
       <label>Message</label>
       <textarea placeholder="Tell me about your project..." minlength="20" required></textarea>
     </div>
     <label class="f-check">
       <input type="checkbox" />
       Subscribe to updates & newsletter
     </label>
     <button type="submit" class="f-submit">
       Send Message <span>→</span>
     </button>
   </form>
 </div>
</section>

<footer>
 <div class="footer-brand"><span>R</span>ICHARD</div>
 <div class="footer-copy">© 2026 Richard — All Rights Reserved</div>
 <div class="footer-status">
   <div class="pulse"></div>
   Open to opportunities
 </div>
</footer>

<script>
 const cursor = document.getElementById('cursor');
 const ring = document.getElementById('cursor-ring');
 let mx = 0, my = 0, rx = 0, ry = 0;

 document.addEventListener('mousemove', e => {
   mx = e.clientX; my = e.clientY;
   cursor.style.left = mx + 'px';
   cursor.style.top = my + 'px';
 });

 function animateRing() {
   rx += (mx - rx) * 0.12;
   ry += (my - ry) * 0.12;
   ring.style.left = rx + 'px';
   ring.style.top = ry + 'px';
   requestAnimationFrame(animateRing);
 }
 animateRing();

 document.querySelectorAll('a, button, .project-row, .skill-pill').forEach(el => {
   el.addEventListener('mouseenter', () => {
     cursor.style.width = '20px';
     cursor.style.height = '20px';
     ring.style.width = '56px';
     ring.style.height = '56px';
   });
   el.addEventListener('mouseleave', () => {
     cursor.style.width = '10px';
     cursor.style.height = '10px';
     ring.style.width = '36px';
     ring.style.height = '36px';
   });
 });

 const reveals = document.querySelectorAll('[data-reveal]');
 const obs = new IntersectionObserver(entries => {
   entries.forEach((e, i) => {
     if (e.isIntersecting) {
       setTimeout(() => e.target.classList.add('in'), i * 80);
     }
   });
 }, { threshold: 0.08 });
 reveals.forEach(el => obs.observe(el));

 function submitForm(e) {
   e.preventDefault();
   const btn = e.target.querySelector('.f-submit');
   btn.innerHTML = 'Sent! ✓';
   btn.style.background = 'var(--cyan)';
   setTimeout(() => {
     btn.innerHTML = 'Send Message <span>→</span>';
     btn.style.background = '';
     e.target.reset();
   }, 3000);
 }
</script>
</body>
</html>
