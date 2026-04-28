<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ritick Pandey</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,600;0,700;1,600&family=Inter:wght@300;400;500&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
:root {
  --bg:      #080d14;
  --bg2:     #0c1420;
  --bg3:     #111c2d;
  --surface: #162338;
  --b1:      #3b82f6;
  --b2:      #60a5fa;
  --b3:      #93c5fd;
  --text:    #f0f6ff;
  --off:     #a8bdd8;
  --muted:   #5a7a99;
  --border:  rgba(59,130,246,0.18);
  --border2: rgba(255,255,255,0.07);
}

*, *::before, *::after { margin:0; padding:0; box-sizing:border-box; }
html { scroll-behavior: smooth; }

body {
  background: var(--bg);
  color: var(--text);
  font-family: 'Inter', sans-serif;
  overflow-x: hidden;
  line-height: 1.6;
}

/* top glow */
body::before {
  content: '';
  position: fixed;
  top: -300px; left: 50%;
  transform: translateX(-50%);
  width: 900px; height: 600px;
  background: radial-gradient(ellipse, rgba(59,130,246,0.08) 0%, transparent 65%);
  pointer-events: none;
  z-index: 0;
}

/* gradient text */
.grad {
  background: linear-gradient(135deg, var(--b1), var(--b3));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

/* ── NAV ── */
nav {
  position: fixed;
  top: 0; left: 0; right: 0;
  z-index: 100;
  padding: 1.1rem 6rem;
  display: flex;
  justify-content: flex-end;
  align-items: center;
  background: rgba(8,13,20,0.88);
  backdrop-filter: blur(18px);
  border-bottom: 1px solid var(--border2);
}

.nav-links {
  display: flex;
  gap: 2.4rem;
  list-style: none;
}

.nav-links a {
  font-size: 0.82rem;
  font-weight: 400;
  color: var(--muted);
  text-decoration: none;
  transition: color 0.2s;
  position: relative;
}

.nav-links a::after {
  content: '';
  position: absolute;
  bottom: -3px; left: 0;
  height: 1px; width: 0;
  background: linear-gradient(90deg, var(--b1), var(--b3));
  transition: width 0.25s ease;
}

.nav-links a:hover { color: var(--b3); }
.nav-links a:hover::after { width: 100%; }

/* ── SECTIONS ── */
section {
  position: relative;
  z-index: 1;
  padding: 110px 6rem 80px;
}

/* ── HERO ── */
#hero {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding-top: 120px;
}

.hero-hi {
  font-size: 1.05rem;
  font-weight: 300;
  color: var(--off);
  margin-bottom: 0.5rem;
  opacity: 0;
  animation: up 0.6s 0.15s forwards;
}

.hero-name {
  font-family: 'Playfair Display', serif;
  font-size: clamp(2.8rem, 5.5vw, 4.8rem);
  font-weight: 700;
  line-height: 1.08;
  letter-spacing: -0.5px;
  margin-bottom: 0.9rem;
  opacity: 0;
  animation: up 0.6s 0.3s forwards;
}

.hero-role {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.9rem;
  font-weight: 400;
  color: var(--b2);
  margin-bottom: 1.8rem;
  opacity: 0;
  animation: up 0.6s 0.45s forwards;
  letter-spacing: 0.3px;
}

.hero-bio {
  max-width: 480px;
  color: var(--muted);
  font-size: 0.96rem;
  font-weight: 300;
  line-height: 1.85;
  margin-bottom: 2.4rem;
  opacity: 0;
  animation: up 0.6s 0.6s forwards;
}

.hero-actions {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  opacity: 0;
  animation: up 0.6s 0.75s forwards;
  margin-bottom: 2.8rem;
}

.btn {
  font-size: 0.82rem;
  font-weight: 500;
  padding: 0.68rem 1.6rem;
  border-radius: 6px;
  text-decoration: none;
  display: inline-flex;
  align-items: center;
  gap: 6px;
  transition: all 0.22s;
  border: none;
  cursor: pointer;
}

.btn-solid {
  background: var(--b1);
  color: #fff;
}
.btn-solid:hover {
  background: var(--b2);
  transform: translateY(-2px);
  box-shadow: 0 8px 24px rgba(59,130,246,0.35);
}

.btn-ghost {
  border: 1px solid var(--border);
  color: var(--off);
  background: transparent;
}
.btn-ghost:hover {
  border-color: var(--b1);
  color: var(--b3);
  transform: translateY(-2px);
}

/* social strip */
.social-strip {
  display: flex;
  align-items: center;
  gap: 1.3rem;
  opacity: 0;
  animation: up 0.6s 0.9s forwards;
}

.social-strip span {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.6rem;
  color: var(--muted);
  letter-spacing: 1.5px;
  text-transform: uppercase;
}

.soc-link {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  font-size: 0.78rem;
  color: var(--muted);
  text-decoration: none;
  transition: color 0.2s;
}
.soc-link:hover { color: var(--b3); }
.soc-link svg { width: 14px; height: 14px; fill: currentColor; flex-shrink: 0; }

.dot-sep { width: 3px; height: 3px; border-radius: 50%; background: var(--surface); flex-shrink: 0; }

/* scroll hint */
.scroll-hint {
  position: absolute;
  bottom: 2.5rem; left: 6rem;
  display: flex;
  align-items: center;
  gap: 0.7rem;
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.6rem;
  color: var(--muted);
  letter-spacing: 2px;
  text-transform: uppercase;
  opacity: 0;
  animation: up 0.6s 1.1s forwards;
}

.scroll-pulse {
  width: 5px; height: 5px;
  border-radius: 50%;
  background: var(--b1);
  animation: breathe 2.2s ease-in-out infinite;
}
@keyframes breathe { 0%,100%{opacity:0.35;transform:scale(1)} 50%{opacity:1;transform:scale(1.5)} }

/* ── SECTION HEADER ── */
.sec-hdr { margin-bottom: 3.5rem; }

.sec-label {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.65rem;
  color: var(--b1);
  letter-spacing: 2.5px;
  text-transform: uppercase;
  margin-bottom: 0.55rem;
}

.sec-title {
  font-family: 'Playfair Display', serif;
  font-size: clamp(1.7rem, 3.5vw, 2.5rem);
  font-weight: 600;
  line-height: 1.15;
  color: var(--text);
}

.sec-rule {
  margin-top: 0.8rem;
  width: 36px; height: 2px;
  background: linear-gradient(90deg, var(--b1), var(--b3));
  border-radius: 1px;
}

/* ── ABOUT ── */
#about { background: var(--bg2); }

.about-wrap {
  display: grid;
  grid-template-columns: 1.2fr 0.8fr;
  gap: 5rem;
  align-items: start;
}

.about-text p {
  color: var(--off);
  font-size: 0.96rem;
  font-weight: 300;
  line-height: 1.9;
  margin-bottom: 1.2rem;
}
.about-text p strong { color: var(--text); font-weight: 500; }

.stat-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}

.stat-box {
  background: var(--bg3);
  border: 1px solid var(--border2);
  border-radius: 10px;
  padding: 1.2rem 1rem;
  transition: border-color 0.25s, transform 0.25s;
}
.stat-box:hover { border-color: var(--border); transform: translateY(-3px); }

.stat-val {
  font-family: 'Playfair Display', serif;
  font-size: 2rem;
  font-weight: 600;
  line-height: 1;
  margin-bottom: 0.35rem;
}

.stat-lbl { font-size: 0.74rem; color: var(--muted); }

/* ── SKILLS ── */
#skills { }

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 1.4rem;
}

.skill-cat {
  background: var(--bg2);
  border: 1px solid var(--border2);
  border-radius: 10px;
  padding: 1.4rem;
  transition: border-color 0.25s, transform 0.25s;
}
.skill-cat:hover { border-color: var(--border); transform: translateY(-3px); }

.skill-cat-title {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.62rem;
  color: var(--b2);
  letter-spacing: 2px;
  text-transform: uppercase;
  margin-bottom: 1rem;
}

.tags { display: flex; flex-wrap: wrap; gap: 0.45rem; }

.tag {
  font-size: 0.74rem;
  padding: 0.28rem 0.72rem;
  border-radius: 20px;
  background: var(--surface);
  border: 1px solid var(--border2);
  color: var(--off);
  transition: all 0.2s;
  cursor: default;
}
.tag:hover {
  background: rgba(59,130,246,0.12);
  border-color: rgba(59,130,246,0.35);
  color: var(--b3);
}

/* ── PROJECTS ── */
#projects { background: var(--bg2); }

.proj-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(290px, 1fr));
  gap: 1.5rem;
}

.proj-card {
  background: var(--bg3);
  border: 1px solid var(--border2);
  border-radius: 12px;
  padding: 1.8rem;
  display: flex;
  flex-direction: column;
  gap: 0.8rem;
  transition: border-color 0.25s, transform 0.28s, box-shadow 0.28s;
  position: relative;
  overflow: hidden;
}

.proj-card::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 2px;
  background: linear-gradient(90deg, var(--b1), var(--b3));
  opacity: 0;
  transition: opacity 0.3s;
}

.proj-card:hover {
  border-color: rgba(59,130,246,0.3);
  transform: translateY(-5px);
  box-shadow: 0 18px 40px rgba(0,0,0,0.5);
}
.proj-card:hover::before { opacity: 1; }

.proj-num {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.62rem;
  color: var(--muted);
  letter-spacing: 1px;
}

.proj-title {
  font-family: 'Playfair Display', serif;
  font-size: 1.05rem;
  font-weight: 600;
  color: var(--text);
  line-height: 1.3;
}

.proj-desc {
  font-size: 0.85rem;
  color: var(--off);
  font-weight: 300;
  line-height: 1.78;
  flex: 1;
}

.proj-tags { display: flex; flex-wrap: wrap; gap: 0.4rem; }

.ptag {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.62rem;
  padding: 0.2rem 0.5rem;
  border-radius: 4px;
  background: rgba(59,130,246,0.1);
  color: var(--b3);
  border: 1px solid rgba(59,130,246,0.2);
}

.proj-link {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.68rem;
  color: var(--b2);
  text-decoration: none;
  display: inline-flex;
  align-items: center;
  gap: 5px;
  width: fit-content;
  transition: gap 0.2s, color 0.2s;
  margin-top: 0.3rem;
}
.proj-link:hover { color: var(--b3); gap: 9px; }

/* ── EXPERIENCE / EDUCATION ── */
#experience { }

.ee-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4.5rem;
}

.ee-col-title {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.62rem;
  color: var(--muted);
  letter-spacing: 2px;
  text-transform: uppercase;
  margin-bottom: 2rem;
  padding-bottom: 0.8rem;
  border-bottom: 1px solid var(--border2);
}

.tl { display: flex; flex-direction: column; gap: 2rem; }

.tl-item {
  display: flex;
  gap: 1.2rem;
  opacity: 0;
  transform: translateY(14px);
  transition: opacity 0.55s, transform 0.55s;
}
.tl-item.visible { opacity: 1; transform: none; }

.tl-marker {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 5px;
  flex-shrink: 0;
}

.tl-dot {
  width: 7px; height: 7px;
  border-radius: 50%;
  background: var(--b1);
  flex-shrink: 0;
  box-shadow: 0 0 8px rgba(59,130,246,0.6);
}

.tl-line {
  width: 1px; flex: 1;
  min-height: 20px;
  background: var(--border2);
  margin-top: 7px;
}

.tl-item:last-child .tl-line { display: none; }

.tl-period {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.62rem;
  color: var(--b2);
  letter-spacing: 0.5px;
  margin-bottom: 0.3rem;
}

.tl-title {
  font-family: 'Playfair Display', serif;
  font-size: 1rem;
  font-weight: 600;
  margin-bottom: 0.2rem;
  color: var(--text);
}

.tl-org {
  font-size: 0.82rem;
  color: var(--muted);
  font-weight: 300;
  margin-bottom: 0.6rem;
}

.tl-pts { list-style: none; }
.tl-pts li {
  font-size: 0.82rem;
  color: var(--off);
  font-weight: 300;
  padding-left: 0.9rem;
  position: relative;
  margin-bottom: 0.22rem;
  line-height: 1.65;
}
.tl-pts li::before {
  content: '–';
  position: absolute; left: 0;
  color: var(--b1);
}

/* ── CONTACT ── */
#contact { background: var(--bg2); }

.contact-wrap {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 5rem;
  align-items: start;
}

.contact-intro {
  color: var(--off);
  font-size: 0.97rem;
  font-weight: 300;
  line-height: 1.85;
  margin-bottom: 2rem;
}

.contact-links { display: flex; flex-direction: column; gap: 1rem; }

.contact-item {
  display: flex;
  align-items: center;
  gap: 0.9rem;
  padding: 1rem 1.2rem;
  background: var(--bg3);
  border: 1px solid var(--border2);
  border-radius: 10px;
  text-decoration: none;
  transition: border-color 0.22s, transform 0.22s;
}
.contact-item:hover { border-color: var(--border); transform: translateX(4px); }

.contact-icon {
  width: 36px; height: 36px;
  border-radius: 8px;
  background: linear-gradient(135deg, var(--b1), var(--b3));
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}
.contact-icon svg { width: 15px; height: 15px; fill: #fff; }

.contact-body { display: flex; flex-direction: column; gap: 1px; }
.contact-lbl {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.6rem;
  color: var(--muted);
  letter-spacing: 1.5px;
  text-transform: uppercase;
}
.contact-val { font-size: 0.86rem; color: var(--text); font-weight: 400; }

.contact-card {
  padding: 2rem;
  background: var(--bg3);
  border: 1px solid var(--border2);
  border-radius: 12px;
}

.contact-card h3 {
  font-family: 'Playfair Display', serif;
  font-size: 1.1rem;
  font-weight: 600;
  margin-bottom: 0.9rem;
  color: var(--text);
}

.contact-card p {
  font-size: 0.88rem;
  color: var(--off);
  font-weight: 300;
  line-height: 1.8;
  margin-bottom: 1.5rem;
}

.email-btn {
  display: inline-flex;
  align-items: center;
  gap: 7px;
  padding: 0.7rem 1.5rem;
  background: var(--b1);
  color: #fff;
  font-size: 0.82rem;
  font-weight: 500;
  border-radius: 6px;
  text-decoration: none;
  transition: background 0.22s, transform 0.22s, box-shadow 0.22s;
}
.email-btn:hover {
  background: var(--b2);
  transform: translateY(-2px);
  box-shadow: 0 8px 22px rgba(59,130,246,0.35);
}

/* ── FOOTER ── */
footer {
  position: relative;
  z-index: 1;
  background: var(--bg);
  border-top: 1px solid var(--border2);
  padding: 2.5rem 6rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.foot-left {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.68rem;
  color: var(--muted);
}

.foot-socials { display: flex; align-items: center; gap: 1.5rem; }

.foot-soc {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  font-size: 0.75rem;
  color: var(--muted);
  text-decoration: none;
  transition: color 0.2s;
}
.foot-soc:hover { color: var(--b3); }
.foot-soc svg { width: 14px; height: 14px; fill: currentColor; flex-shrink: 0; }

/* ── ANIMATIONS ── */
@keyframes up {
  from { opacity: 0; transform: translateY(20px); }
  to   { opacity: 1; transform: translateY(0); }
}

.reveal {
  opacity: 0;
  transform: translateY(18px);
  transition: opacity 0.6s ease, transform 0.6s ease;
}
.reveal.visible { opacity: 1; transform: none; }

/* ── RESPONSIVE ── */
@media (max-width: 860px) {
  nav { padding: 1rem 1.5rem; }
  section { padding: 90px 1.5rem 60px; }
  #hero { padding-top: 100px; }
  .about-wrap, .ee-grid, .contact-wrap { grid-template-columns: 1fr; gap: 2.5rem; }
  footer { padding: 2rem 1.5rem; flex-direction: column; gap: 1.2rem; align-items: flex-start; }
  .scroll-hint { left: 1.5rem; }
}
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#experience">Experience</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- HERO -->
<section id="hero">
  <p class="hero-hi">Hi, I'm</p>
  <h1 class="hero-name"><span class="grad">Ritick Pandey.</span></h1>
  <p class="hero-role">Full Stack Developer</p>
  <p class="hero-bio">
    B.Tech CSE student at KIIT University building scalable backends, ML models, and full-stack web applications. Focused on clean code and data-driven solutions.
  </p>
  <div class="hero-actions">
    <a href="https://github.com/RitickPandey" target="_blank" class="btn btn-solid">GitHub ↗</a>
    <a href="#contact" class="btn btn-ghost" id="contact-btn">Contact</a>
  </div>
  <div class="social-strip">
    <span>Find me on</span>
    <div class="dot-sep"></div>
    <a href="https://www.linkedin.com/in/ritickpandey/" target="_blank" class="soc-link">
      <svg viewBox="0 0 24 24"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
      LinkedIn
    </a>
    <div class="dot-sep"></div>
    <a href="https://www.instagram.com/ritick_007/" target="_blank" class="soc-link">
      <svg viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zM12 0C8.741 0 8.333.014 7.053.072 2.695.272.273 2.69.073 7.052.014 8.333 0 8.741 0 12c0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98C8.333 23.986 8.741 24 12 24c3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98C15.668.014 15.259 0 12 0zm0 5.838a6.162 6.162 0 100 12.324 6.162 6.162 0 000-12.324zM12 16a4 4 0 110-8 4 4 0 010 8zm6.406-11.845a1.44 1.44 0 100 2.881 1.44 1.44 0 000-2.881z"/></svg>
      Instagram
    </a>
    <div class="dot-sep"></div>
    <a href="https://github.com/RitickPandey" target="_blank" class="soc-link">
      <svg viewBox="0 0 24 24"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/></svg>
      GitHub
    </a>
  </div>
  <div class="scroll-hint">
    <div class="scroll-pulse"></div>
    scroll down
  </div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="sec-hdr reveal">
    <p class="sec-label">01 — About</p>
    <h2 class="sec-title">Who I Am</h2>
    <div class="sec-rule"></div>
  </div>
  <div class="about-wrap">
    <div class="about-text reveal">
      <p>I'm a <strong>Computer Science student</strong> at KIIT University (2023–2027), in my second year with a CGPA of 7.72. My focus spans <strong>Java backend development</strong>, <strong>machine learning</strong>, and full-stack web applications.</p>
      <p>I enjoy building things that are both efficient and meaningful — whether that's an ML model trained from scratch or a full doctor appointment system with an admin panel.</p>
      <p>I've completed a <strong>Java Development internship at 1Stop</strong>, collaborating on live Spring Boot applications and sharpening my backend instincts.</p>
    </div>
    <div class="stat-grid reveal">
      <div class="stat-box">
        <div class="stat-val grad" data-target="7.72" data-dec="2">0</div>
        <div class="stat-lbl">CGPA at KIIT</div>
      </div>
      <div class="stat-box">
        <div class="stat-val grad" data-target="3" data-sfx="+">0</div>
        <div class="stat-lbl">Projects</div>
      </div>
      <div class="stat-box">
        <div class="stat-val grad" data-target="1">1</div>
        <div class="stat-lbl">Internship</div>
      </div>
      <div class="stat-box">
        <div class="stat-val grad" data-target="6" data-sfx="+">0</div>
        <div class="stat-lbl">Languages</div>
      </div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills">
  <div class="sec-hdr reveal">
    <p class="sec-label">02 — Skills</p>
    <h2 class="sec-title">What I Work With</h2>
    <div class="sec-rule"></div>
  </div>
  <div class="skills-grid">
    <div class="skill-cat reveal">
      <div class="skill-cat-title">Languages</div>
      <div class="tags"><span class="tag">Python</span><span class="tag">Java</span><span class="tag">C</span><span class="tag">JavaScript</span><span class="tag">HTML / CSS</span><span class="tag">SQL</span></div>
    </div>
    <div class="skill-cat reveal">
      <div class="skill-cat-title">Frameworks &amp; DB</div>
      <div class="tags"><span class="tag">Spring Boot</span><span class="tag">PHP</span><span class="tag">MySQL</span><span class="tag">JUnit</span><span class="tag">WordPress</span></div>
    </div>
    <div class="skill-cat reveal">
      <div class="skill-cat-title">ML &amp; Data</div>
      <div class="tags"><span class="tag">NumPy</span><span class="tag">Pandas</span><span class="tag">Seaborn</span><span class="tag">Matplotlib</span><span class="tag">Logistic Regression</span></div>
    </div>
    <div class="skill-cat reveal">
      <div class="skill-cat-title">Tools &amp; Platforms</div>
      <div class="tags"><span class="tag">VS Code</span><span class="tag">Eclipse</span><span class="tag">GitHub</span><span class="tag">Jenkins</span><span class="tag">Linux</span><span class="tag">GCP</span><span class="tag">Android Studio</span></div>
    </div>
    <div class="skill-cat reveal">
      <div class="skill-cat-title">CS Core</div>
      <div class="tags"><span class="tag">DSA</span><span class="tag">OOP</span><span class="tag">OS</span><span class="tag">DBMS</span><span class="tag">Algorithms</span><span class="tag">Linear Algebra</span></div>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div class="sec-hdr reveal">
    <p class="sec-label">03 — Projects</p>
    <h2 class="sec-title">Things I've Built</h2>
    <div class="sec-rule"></div>
  </div>
  <div class="proj-grid">
    <div class="proj-card reveal">
      <div class="proj-num">01</div>
      <h3 class="proj-title">Breast Cancer Diagnosis</h3>
      <p class="proj-desc">Logistic regression built from scratch in Python to classify tumours as benign or malignant. Evaluated on a real-world medical dataset using accuracy metrics.</p>
      <div class="proj-tags"><span class="ptag">Python</span><span class="ptag">NumPy</span><span class="ptag">Pandas</span><span class="ptag">ML</span></div>
      <a href="https://github.com/RitickPandey" target="_blank" class="proj-link">GitHub →</a>
    </div>
    <div class="proj-card reveal">
      <div class="proj-num">02</div>
      <h3 class="proj-title">Uber Ride Data Analysis</h3>
      <p class="proj-desc">EDA on Uber ride data surfacing patterns, peak hours, and trip frequency. Insights into customer behaviour visualised using Seaborn and Matplotlib.</p>
      <div class="proj-tags"><span class="ptag">Python</span><span class="ptag">Pandas</span><span class="ptag">Seaborn</span><span class="ptag">Matplotlib</span></div>
      <a href="https://github.com/RitickPandey" target="_blank" class="proj-link">GitHub →</a>
    </div>
    <div class="proj-card reveal">
      <div class="proj-num">03</div>
      <h3 class="proj-title">Doctor Appointment Website</h3>
      <p class="proj-desc">Full-stack web app with user auth, specialisation filtering, appointment booking, profile pages, and a complete admin panel for managing doctors.</p>
      <div class="proj-tags"><span class="ptag">HTML/CSS</span><span class="ptag">JavaScript</span><span class="ptag">PHP</span><span class="ptag">MySQL</span></div>
      <a href="https://github.com/RitickPandey" target="_blank" class="proj-link">GitHub →</a>
    </div>
  </div>
</section>

<!-- EXPERIENCE & EDUCATION -->
<section id="experience">
  <div class="sec-hdr reveal">
    <p class="sec-label">04 — Background</p>
    <h2 class="sec-title">Experience &amp; Education</h2>
    <div class="sec-rule"></div>
  </div>
  <div class="ee-grid">
    <div>
      <div class="ee-col-title">Work Experience</div>
      <div class="tl">
        <div class="tl-item">
          <div class="tl-marker"><div class="tl-dot"></div><div class="tl-line"></div></div>
          <div>
            <div class="tl-period">May 2025 – June 2025</div>
            <div class="tl-title">Java Development Intern</div>
            <div class="tl-org">1Stop Keep Growing · Remote</div>
            <ul class="tl-pts">
              <li>Built core Java modules for live web-based applications</li>
              <li>Applied OOP principles for scalable backend services</li>
              <li>Integrated Spring Boot APIs with frontend interfaces</li>
              <li>Debugged runtime issues to improve system reliability</li>
            </ul>
          </div>
        </div>
      </div>
    </div>
    <div>
      <div class="ee-col-title">Education</div>
      <div class="tl">
        <div class="tl-item">
          <div class="tl-marker"><div class="tl-dot"></div><div class="tl-line"></div></div>
          <div>
            <div class="tl-period">2023 – 2027</div>
            <div class="tl-title">B.Tech — Computer Science</div>
            <div class="tl-org">KIIT University, Bhubaneswar</div>
            <ul class="tl-pts"><li>CGPA: 7.72 (Current)</li></ul>
          </div>
        </div>
        <div class="tl-item">
          <div class="tl-marker"><div class="tl-dot"></div><div class="tl-line"></div></div>
          <div>
            <div class="tl-period">2022</div>
            <div class="tl-title">Senior Secondary (12th)</div>
            <div class="tl-org">CBSE Board</div>
            <ul class="tl-pts"><li>65.4%</li></ul>
          </div>
        </div>
        <div class="tl-item">
          <div class="tl-marker"><div class="tl-dot"></div><div class="tl-line"></div></div>
          <div>
            <div class="tl-period">2020</div>
            <div class="tl-title">Secondary (10th)</div>
            <div class="tl-org">CBSE Board</div>
            <ul class="tl-pts"><li>80.2%</li></ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="sec-hdr reveal">
    <p class="sec-label">05 — Contact</p>
    <h2 class="sec-title">Get In Touch</h2>
    <div class="sec-rule"></div>
  </div>
  <div class="contact-wrap">
    <div class="reveal">
      <p class="contact-intro">I'm open to internships, collaborations, and interesting projects. Feel free to reach out through any of the channels below.</p>
      <div class="contact-links">
        <a href="mailto:23053293@kiit.ac.in" class="contact-item">
          <div class="contact-icon">
            <svg viewBox="0 0 24 24"><path d="M24 5.457v13.909c0 .904-.732 1.636-1.636 1.636h-3.819V11.73L12 16.64l-6.545-4.91v9.273H1.636A1.636 1.636 0 010 19.366V5.457c0-2.023 2.309-3.178 3.927-1.964L5.455 4.64 12 9.548l6.545-4.91 1.528-1.145C21.69 2.28 24 3.434 24 5.457z"/></svg>
          </div>
          <div class="contact-body">
            <span class="contact-lbl">Email</span>
            <span class="contact-val">23053293@kiit.ac.in</span>
          </div>
        </a>
        <a href="https://www.linkedin.com/in/ritickpandey/" target="_blank" class="contact-item">
          <div class="contact-icon">
            <svg viewBox="0 0 24 24"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
          </div>
          <div class="contact-body">
            <span class="contact-lbl">LinkedIn</span>
            <span class="contact-val">linkedin.com/in/ritickpandey</span>
          </div>
        </a>
        <a href="https://www.instagram.com/ritick_007/" target="_blank" class="contact-item">
          <div class="contact-icon">
            <svg viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zM12 0C8.741 0 8.333.014 7.053.072 2.695.272.273 2.69.073 7.052.014 8.333 0 8.741 0 12c0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98C8.333 23.986 8.741 24 12 24c3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98C15.668.014 15.259 0 12 0zm0 5.838a6.162 6.162 0 100 12.324 6.162 6.162 0 000-12.324zM12 16a4 4 0 110-8 4 4 0 010 8zm6.406-11.845a1.44 1.44 0 100 2.881 1.44 1.44 0 000-2.881z"/></svg>
          </div>
          <div class="contact-body">
            <span class="contact-lbl">Instagram</span>
            <span class="contact-val">@ritick_007</span>
          </div>
        </a>
        <a href="https://github.com/RitickPandey" target="_blank" class="contact-item">
          <div class="contact-icon">
            <svg viewBox="0 0 24 24"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/></svg>
          </div>
          <div class="contact-body">
            <span class="contact-lbl">GitHub</span>
            <span class="contact-val">github.com/RitickPandey</span>
          </div>
        </a>
      </div>
    </div>
    <div class="contact-card reveal">
      <h3>Say Hello 👋</h3>
      <p>Whether you have a project idea, want to collaborate, or just want to connect — my inbox is always open. I'll get back to you as soon as I can.</p>
      <a href="mailto:23053293@kiit.ac.in" class="email-btn">Send me an email →</a>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="foot-left">© 2025 Ritick Pandey · Bihar, India</div>
  <div class="foot-socials">
    <a href="https://github.com/RitickPandey" target="_blank" class="foot-soc">
      <svg viewBox="0 0 24 24"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/></svg>
      GitHub
    </a>
    <a href="https://www.linkedin.com/in/ritickpandey/" target="_blank" class="foot-soc">
      <svg viewBox="0 0 24 24"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
      LinkedIn
    </a>
    <a href="https://www.instagram.com/ritick_007/" target="_blank" class="foot-soc">
      <svg viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zM12 0C8.741 0 8.333.014 7.053.072 2.695.272.273 2.69.073 7.052.014 8.333 0 8.741 0 12c0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98C8.333 23.986 8.741 24 12 24c3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98C15.668.014 15.259 0 12 0zm0 5.838a6.162 6.162 0 100 12.324 6.162 6.162 0 000-12.324zM12 16a4 4 0 110-8 4 4 0 010 8zm6.406-11.845a1.44 1.44 0 100 2.881 1.44 1.44 0 000-2.881z"/></svg>
      Instagram
    </a>
  </div>
</footer>

<script>
/* COUNT-UP */
function countUp(el) {
  const tgt = parseFloat(el.dataset.target);
  const dec = parseInt(el.dataset.dec || 0);
  const sfx = el.dataset.sfx || '';
  const dur = 1200, t0 = performance.now();
  (function run(now) {
    const p = Math.min((now - t0) / dur, 1);
    const e = 1 - Math.pow(1 - p, 3);
    el.textContent = (tgt * e).toFixed(dec) + sfx;
    if (p < 1) requestAnimationFrame(run);
    else el.textContent = tgt.toFixed(dec) + sfx;
  })(t0);
}

/* SCROLL REVEAL */
const io = new IntersectionObserver(entries => {
  entries.forEach(en => {
    if (!en.isIntersecting) return;
    en.target.classList.add('visible');
    en.target.querySelectorAll('[data-target]').forEach(countUp);
    io.unobserve(en.target);
  });
}, { threshold: 0.12 });

document.querySelectorAll('.reveal, .tl-item').forEach((el, i) => {
  el.style.transitionDelay = (i % 5 * 0.07) + 's';
  io.observe(el);
});

/* SMOOTH SCROLL — Contact button */
document.querySelectorAll('a[href="#contact"]').forEach(a => {
  a.addEventListener('click', e => {
    e.preventDefault();
    document.getElementById('contact').scrollIntoView({ behavior: 'smooth', block: 'start' });
  });
});
</script>
</body>
</html>
