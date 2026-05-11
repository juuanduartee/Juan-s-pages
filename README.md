<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Juan José Duarte – Portfolio</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:wght@300;400;500&family=Fraunces:ital,opsz,wght@0,9..144,300;0,9..144,600;1,9..144,300&display=swap" rel="stylesheet">
<style>
*, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }
:root {
  --bg: #0a0b0e;
  --surface: #111318;
  --surface2: #181b23;
  --border: #21242e;
  --border2: #2d3140;
  --accent: #c9f135;
  --accent-dim: rgba(201,241,53,0.12);
  --accent2: #5b8dff;
  --text: #eaecf2;
  --muted: #5e6578;
  --muted2: #9198ad;
  --serif: 'Fraunces', Georgia, serif;
  --mono: 'DM Mono', monospace;
  --sans: 'Syne', sans-serif;
}
html { scroll-behavior: smooth; }
body { background: var(--bg); color: var(--text); font-family: var(--sans); overflow-x: hidden; cursor: none; }
a { cursor: none; } button { cursor: none; }

/* SCROLL BAR */
#scroll-bar { position: fixed; top: 0; left: 0; height: 2px; width: 0%; background: linear-gradient(90deg, var(--accent), var(--accent2)); z-index: 9999; transition: width 0.04s linear; }

/* CURSOR */
.cursor { width: 8px; height: 8px; background: var(--accent); border-radius: 50%; position: fixed; pointer-events: none; z-index: 9998; transform: translate(-50%,-50%); transition: transform 0.12s ease; mix-blend-mode: difference; }
.cursor-ring { width: 34px; height: 34px; border: 1.5px solid rgba(201,241,53,0.35); border-radius: 50%; position: fixed; pointer-events: none; z-index: 9997; transform: translate(-50%,-50%); transition: left 0.06s linear, top 0.06s linear, transform 0.2s ease, border-color 0.2s; }
.cursor.hovering { transform: translate(-50%,-50%) scale(2.5); }
.cursor-ring.hovering { transform: translate(-50%,-50%) scale(1.4); border-color: rgba(201,241,53,0.7); }

/* NOISE */
body::after { content: ''; position: fixed; inset: 0; pointer-events: none; z-index: 9996; background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.035'/%3E%3C/svg%3E"); }

/* NAV */
nav { position: fixed; top: 0; left: 0; right: 0; z-index: 500; display: flex; justify-content: space-between; align-items: center; padding: 1.25rem 3rem; background: rgba(10,11,14,0.8); backdrop-filter: blur(24px); border-bottom: 1px solid var(--border); }
.nav-logo { font-family: var(--mono); font-size: 0.75rem; color: var(--accent); letter-spacing: 0.18em; text-transform: uppercase; }
.nav-links { display: flex; gap: 2.5rem; list-style: none; }
.nav-links a { font-family: var(--mono); font-size: 0.7rem; color: var(--muted2); text-decoration: none; letter-spacing: 0.1em; text-transform: uppercase; transition: color 0.2s; position: relative; }
.nav-links a::after { content: ''; position: absolute; bottom: -3px; left: 0; width: 0; height: 1px; background: var(--accent); transition: width 0.25s; }
.nav-links a:hover { color: var(--accent); }
.nav-links a:hover::after { width: 100%; }

.nav-burger { display: none; flex-direction: column; gap: 5px; background: none; border: none; padding: 4px; }
.nav-burger span { display: block; width: 22px; height: 1.5px; background: var(--text); transition: all 0.3s; }
.nav-burger.open span:nth-child(1) { transform: translateY(6.5px) rotate(45deg); }
.nav-burger.open span:nth-child(2) { opacity: 0; }
.nav-burger.open span:nth-child(3) { transform: translateY(-6.5px) rotate(-45deg); }

.nav-mobile { display: none; position: fixed; inset: 0; top: 60px; background: rgba(10,11,14,0.97); backdrop-filter: blur(30px); z-index: 499; flex-direction: column; align-items: center; justify-content: center; gap: 3rem; }
.nav-mobile.open { display: flex; }
.nav-mobile a { font-family: var(--serif); font-size: 2.2rem; font-weight: 300; color: var(--text); text-decoration: none; transition: color 0.2s; }
.nav-mobile a:hover { color: var(--accent); }

/* HERO */
.hero { min-height: 100vh; display: grid; grid-template-columns: 1.1fr 0.9fr; align-items: center; padding: 9rem 3rem 5rem; position: relative; overflow: hidden; gap: 4rem; }
.hero-grid { position: absolute; inset: 0; pointer-events: none; background-image: linear-gradient(rgba(201,241,53,0.025) 1px, transparent 1px), linear-gradient(90deg, rgba(201,241,53,0.025) 1px, transparent 1px); background-size: 56px 56px; mask-image: radial-gradient(ellipse 80% 80% at 30% 50%, black 40%, transparent 100%); }
.hero-glow { position: absolute; width: 700px; height: 700px; pointer-events: none; background: radial-gradient(circle, rgba(91,141,255,0.07) 0%, transparent 65%); right: -200px; top: 50%; transform: translateY(-50%); }
.hero-glow2 { position: absolute; width: 400px; height: 400px; pointer-events: none; background: radial-gradient(circle, rgba(201,241,53,0.05) 0%, transparent 65%); left: -100px; bottom: 0; }
.hero-left { position: relative; z-index: 2; }

.hero-eyebrow { font-family: var(--mono); font-size: 0.68rem; color: var(--accent); letter-spacing: 0.22em; text-transform: uppercase; margin-bottom: 1.6rem; display: flex; align-items: center; gap: 0.8rem; opacity: 0; animation: fadeUp 0.7s 0.1s ease forwards; }
.hero-eyebrow::before { content: ''; display: block; width: 28px; height: 1px; background: var(--accent); flex-shrink: 0; }
h1 { font-family: var(--serif); font-size: clamp(3rem, 5.5vw, 5.2rem); font-weight: 300; line-height: 1.05; letter-spacing: -0.01em; opacity: 0; animation: fadeUp 0.8s 0.2s ease forwards; }
h1 em { font-style: italic; color: var(--accent); }
.hero-role { font-family: var(--mono); font-size: 0.75rem; color: var(--muted); letter-spacing: 0.14em; text-transform: uppercase; margin: 1.8rem 0 1.5rem; opacity: 0; animation: fadeUp 0.8s 0.35s ease forwards; }
.hero-desc { font-size: 0.95rem; color: var(--muted2); line-height: 1.8; max-width: 480px; margin-bottom: 2.5rem; opacity: 0; animation: fadeUp 0.8s 0.45s ease forwards; }
.hero-cta { display: flex; gap: 1rem; flex-wrap: wrap; opacity: 0; animation: fadeUp 0.8s 0.55s ease forwards; }

.btn { display: inline-flex; align-items: center; gap: 0.5rem; padding: 0.8rem 1.8rem; font-family: var(--sans); font-size: 0.75rem; font-weight: 700; letter-spacing: 0.12em; text-transform: uppercase; text-decoration: none; border: none; transition: transform 0.2s, box-shadow 0.2s, background 0.2s, color 0.2s, border-color 0.2s; }
.btn-primary { background: var(--accent); color: var(--bg); }
.btn-primary:hover { transform: translate(-3px,-3px); box-shadow: 5px 5px 0 rgba(201,241,53,0.25); }
.btn-ghost { background: transparent; color: var(--muted2); border: 1px solid var(--border2); }
.btn-ghost:hover { border-color: var(--accent); color: var(--accent); }

.hero-right { position: relative; z-index: 2; display: flex; flex-direction: column; gap: 1.5px; opacity: 0; animation: fadeRight 0.9s 0.5s ease forwards; }
.stat-card { background: var(--surface); border: 1px solid var(--border); padding: 1.8rem 2rem; position: relative; overflow: hidden; transition: background 0.2s; }
.stat-card:hover { background: var(--surface2); }
.stat-card::before { content: ''; position: absolute; left: 0; top: 0; bottom: 0; width: 3px; background: var(--accent); transform: scaleY(0); transform-origin: bottom; transition: transform 0.3s ease; }
.stat-card:hover::before { transform: scaleY(1); }
.stat-num { font-family: var(--serif); font-size: 2.6rem; font-weight: 300; color: var(--accent); line-height: 1; display: block; margin-bottom: 0.3rem; }
.stat-label { font-family: var(--mono); font-size: 0.62rem; color: var(--muted); letter-spacing: 0.15em; text-transform: uppercase; }

/* SECTION */
.section-wrap { max-width: 1200px; margin: 0 auto; padding: 6rem 3rem; }
.section-label { font-family: var(--mono); font-size: 0.65rem; color: var(--accent); letter-spacing: 0.22em; text-transform: uppercase; margin-bottom: 0.6rem; display: flex; align-items: center; gap: 0.7rem; }
.section-label::before { content: ''; display: block; width: 20px; height: 1px; background: var(--accent); }
h2 { font-family: var(--serif); font-size: clamp(1.9rem, 3.5vw, 2.8rem); font-weight: 300; line-height: 1.1; margin-bottom: 3rem; }
h2 em { font-style: italic; color: var(--accent); }

/* SOBRE MÍ */
.about-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 1.5px; background: var(--border); border: 1px solid var(--border); }
.about-text { background: var(--surface); padding: 3rem; font-size: 0.93rem; color: var(--muted2); line-height: 1.85; }
.about-text p + p { margin-top: 1.2rem; }
.about-text strong { color: var(--text); font-weight: 600; }
.about-values { background: var(--surface); padding: 3rem; display: flex; flex-direction: column; gap: 1.8rem; }
.value-item { display: flex; gap: 1.2rem; align-items: flex-start; }
.value-num { font-family: var(--mono); font-size: 0.6rem; color: var(--accent); letter-spacing: 0.12em; flex-shrink: 0; margin-top: 0.2rem; border: 1px solid rgba(201,241,53,0.25); padding: 0.2rem 0.4rem; }
.value-title { font-family: var(--sans); font-size: 0.88rem; font-weight: 700; margin-bottom: 0.3rem; }
.value-desc { font-family: var(--mono); font-size: 0.7rem; color: var(--muted2); line-height: 1.6; }

/* SKILLS */
.skills-outer { display: grid; grid-template-columns: repeat(3, 1fr); gap: 1.5px; background: var(--border); border: 1px solid var(--border); }
.skill-card { background: var(--surface); padding: 2rem; position: relative; overflow: hidden; transition: background 0.2s; }
.skill-card::after { content: ''; position: absolute; bottom: 0; left: 0; right: 0; height: 2px; background: var(--accent); transform: scaleX(0); transform-origin: left; transition: transform 0.35s ease; }
.skill-card:hover { background: var(--surface2); }
.skill-card:hover::after { transform: scaleX(1); }
.skill-icon { font-size: 1.6rem; display: block; margin-bottom: 0.9rem; }
.skill-title { font-family: var(--sans); font-size: 0.85rem; font-weight: 700; margin-bottom: 1rem; }
.skill-items { display: flex; flex-direction: column; gap: 0.6rem; }
.skill-row { display: flex; flex-direction: column; gap: 0.25rem; }
.skill-name { font-family: var(--mono); font-size: 0.67rem; color: var(--muted2); display: flex; justify-content: space-between; }
.skill-name span { color: var(--accent); }
.skill-bar-bg { height: 2px; background: var(--border2); border-radius: 1px; overflow: hidden; }
.skill-bar { height: 100%; background: var(--accent); width: 0; transition: width 1s cubic-bezier(0.4,0,0.2,1); border-radius: 1px; }
.skill-tags { display: flex; flex-wrap: wrap; gap: 0.4rem; margin-top: 0.5rem; }
.skill-tag { font-family: var(--mono); font-size: 0.6rem; color: var(--muted); background: var(--surface2); border: 1px solid var(--border2); padding: 0.2rem 0.55rem; letter-spacing: 0.08em; }

/* EXPERIENCE */
.exp-list { border-left: 1px solid var(--border2); padding-left: 2.5rem; display: flex; flex-direction: column; }
.exp-item { position: relative; padding-bottom: 3.5rem; opacity: 0; transform: translateY(16px); transition: opacity 0.6s ease, transform 0.6s ease; }
.exp-item.visible { opacity: 1; transform: none; }
.exp-item:last-child { padding-bottom: 0; }
.exp-dot { position: absolute; left: -2.75rem; top: 0.45rem; width: 10px; height: 10px; background: var(--bg); border: 2px solid var(--accent); border-radius: 50%; transition: background 0.2s; }
.exp-item:hover .exp-dot { background: var(--accent); }
.exp-meta { display: flex; align-items: center; gap: 1rem; margin-bottom: 0.6rem; flex-wrap: wrap; }
.exp-date { font-family: var(--mono); font-size: 0.62rem; color: var(--muted); letter-spacing: 0.15em; text-transform: uppercase; }
.exp-badge { font-family: var(--mono); font-size: 0.58rem; color: var(--accent); background: var(--accent-dim); border: 1px solid rgba(201,241,53,0.2); padding: 0.15rem 0.55rem; letter-spacing: 0.1em; text-transform: uppercase; }
.exp-title { font-family: var(--sans); font-size: 1.1rem; font-weight: 700; margin-bottom: 0.25rem; }
.exp-org { font-family: var(--mono); font-size: 0.7rem; color: var(--accent); margin-bottom: 0.9rem; }
.exp-desc { font-size: 0.88rem; color: var(--muted2); line-height: 1.72; max-width: 640px; }
.exp-chips { display: flex; flex-wrap: wrap; gap: 0.4rem; margin-top: 0.9rem; }
.exp-chip { font-family: var(--mono); font-size: 0.58rem; color: var(--muted); border: 1px solid var(--border2); padding: 0.2rem 0.55rem; letter-spacing: 0.08em; }

/* EDUCATION */
.edu-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 1.5px; background: var(--border); border: 1px solid var(--border); margin-bottom: 1.5px; }
.edu-card { background: var(--surface); padding: 2.5rem; position: relative; overflow: hidden; }
.edu-card.highlight::before { content: ''; position: absolute; top: 0; left: 0; right: 0; height: 3px; background: linear-gradient(90deg, var(--accent), var(--accent2)); }
.edu-chip { font-family: var(--mono); font-size: 0.6rem; color: var(--accent); background: var(--accent-dim); border: 1px solid rgba(201,241,53,0.2); padding: 0.2rem 0.55rem; letter-spacing: 0.1em; text-transform: uppercase; display: inline-block; margin-bottom: 1.2rem; }
.edu-degree { font-family: var(--serif); font-size: 1.5rem; font-weight: 300; line-height: 1.25; margin-bottom: 0.5rem; }
.edu-school { font-family: var(--mono); font-size: 0.68rem; color: var(--muted2); margin-bottom: 0.4rem; }
.edu-avg { font-family: var(--mono); font-size: 0.65rem; color: var(--muted); letter-spacing: 0.1em; }
.edu-tags { display: flex; flex-wrap: wrap; gap: 0.4rem; margin-top: 1.2rem; }
.edu-tag { font-family: var(--mono); font-size: 0.58rem; color: var(--muted); background: var(--surface2); border: 1px solid var(--border2); padding: 0.2rem 0.6rem; letter-spacing: 0.07em; }

/* GRADES ACCORDION */
.grades-panel { background: var(--surface); border: 1px solid var(--border); }
.grades-header { width: 100%; background: none; border: none; border-bottom: 1px solid transparent; padding: 1.2rem 2rem; display: flex; justify-content: space-between; align-items: center; transition: background 0.2s, border-color 0.2s; }
.grades-header:hover { background: var(--surface2); border-color: var(--border2); }
.grades-header-label { font-family: var(--mono); font-size: 0.68rem; color: var(--muted2); letter-spacing: 0.12em; text-transform: uppercase; }
.grades-arrow { font-family: var(--mono); font-size: 0.65rem; color: var(--accent); transition: transform 0.3s; display: inline-block; }
.grades-arrow.open { transform: rotate(180deg); }
.grades-body { max-height: 0; overflow: hidden; transition: max-height 0.45s ease; }
.grades-body.open { max-height: 900px; }
.grades-table { width: 100%; border-collapse: collapse; }
.grades-table th { font-family: var(--mono); font-size: 0.58rem; color: var(--muted); letter-spacing: 0.15em; text-transform: uppercase; text-align: left; padding: 0.6rem 2rem; border-bottom: 1px solid var(--border); }
.grades-table td { font-family: var(--mono); font-size: 0.68rem; color: var(--muted2); padding: 0.55rem 2rem; border-bottom: 1px solid rgba(33,36,46,0.6); }
.grades-table tr:hover td { background: var(--surface2); color: var(--text); }
.grade-hi { color: var(--accent) !important; font-weight: 500; }

/* CONTACT */
.contact-hero { display: grid; grid-template-columns: 1fr 1fr; gap: 4rem; align-items: start; }
.contact-intro { font-size: 0.92rem; color: var(--muted2); line-height: 1.85; margin-bottom: 1.5rem; }
.contact-cards { display: grid; grid-template-columns: 1fr 1fr; gap: 1.5px; background: var(--border); border: 1px solid var(--border); }
.contact-card { background: var(--surface); padding: 1.5rem 1.8rem; display: flex; gap: 1rem; align-items: flex-start; transition: background 0.2s; }
.contact-card:hover { background: var(--surface2); }
.contact-icon { font-size: 1.1rem; flex-shrink: 0; margin-top: 0.1rem; }
.contact-label { font-family: var(--mono); font-size: 0.58rem; color: var(--muted); letter-spacing: 0.15em; text-transform: uppercase; margin-bottom: 0.3rem; }
.contact-val { font-family: var(--mono); font-size: 0.75rem; color: var(--text); text-decoration: none; transition: color 0.2s; word-break: break-all; }
.contact-val:hover { color: var(--accent); }

.cta-box { background: var(--surface); border: 1px solid var(--border); padding: 2.5rem; position: relative; overflow: hidden; }
.cta-box::before { content: ''; position: absolute; top: 0; left: 0; right: 0; height: 2px; background: linear-gradient(90deg, var(--accent), var(--accent2)); }
.cta-box h3 { font-family: var(--serif); font-size: 1.8rem; font-weight: 300; margin-bottom: 0.8rem; line-height: 1.2; }
.cta-box h3 em { font-style: italic; color: var(--accent); }
.cta-box p { font-size: 0.88rem; color: var(--muted2); line-height: 1.75; margin-bottom: 1.8rem; }

.avail-pill { display: inline-flex; align-items: center; gap: 0.5rem; font-family: var(--mono); font-size: 0.6rem; color: var(--accent); border: 1px solid rgba(201,241,53,0.25); padding: 0.3rem 0.8rem; letter-spacing: 0.12em; text-transform: uppercase; margin-bottom: 1.5rem; }
.dot-pulse { width: 6px; height: 6px; background: var(--accent); border-radius: 50%; animation: pulse 2s infinite; }
@keyframes pulse { 0%,100%{opacity:1;transform:scale(1)}50%{opacity:0.35;transform:scale(0.7)} }

/* FOOTER */
footer { border-top: 1px solid var(--border); padding: 1.8rem 3rem; display: flex; justify-content: space-between; align-items: center; }
.footer-left { font-family: var(--mono); font-size: 0.62rem; color: var(--muted); letter-spacing: 0.1em; }
.footer-right { font-family: var(--mono); font-size: 0.6rem; color: var(--muted); }
.footer-right span { color: var(--accent); }

/* ANIMATIONS */
@keyframes fadeUp { from{opacity:0;transform:translateY(22px)} to{opacity:1;transform:none} }
@keyframes fadeRight { from{opacity:0;transform:translateX(22px)} to{opacity:1;transform:none} }
.reveal { opacity: 0; transform: translateY(20px); transition: opacity 0.65s ease, transform 0.65s ease; }
.reveal.visible { opacity: 1; transform: none; }
.reveal-d1 { transition-delay: 0.12s; }
.reveal-d2 { transition-delay: 0.22s; }

/* RESPONSIVE */
@media (max-width: 960px) {
  nav { padding: 1.1rem 1.5rem; }
  .nav-links { display: none; }
  .nav-burger { display: flex; }
  .hero { grid-template-columns: 1fr; padding: 7.5rem 1.5rem 4rem; gap: 3rem; }
  .hero-right { flex-direction: row; flex-wrap: wrap; gap: 1.5px; }
  .stat-card { flex: 1 1 calc(33% - 2px); min-width: 130px; }
  .about-grid, .edu-grid { grid-template-columns: 1fr; }
  .skills-outer { grid-template-columns: 1fr 1fr; }
  .contact-hero { grid-template-columns: 1fr; gap: 2.5rem; }
  .section-wrap { padding: 4.5rem 1.5rem; }
  footer { flex-direction: column; gap: 0.6rem; text-align: center; padding: 1.5rem; }
  body { cursor: auto; }
  .cursor, .cursor-ring { display: none; }
  a, button { cursor: pointer !important; }
}
@media (max-width: 600px) {
  .skills-outer { grid-template-columns: 1fr; }
  .contact-cards { grid-template-columns: 1fr; }
  .hero-right { flex-direction: column; }
  h1 { font-size: 2.8rem; }
}
</style>
</head>
<body>

<div id="scroll-bar"></div>
<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- NAV -->
<nav>
  <div class="nav-logo">JJD &mdash; Portfolio</div>
  <ul class="nav-links">
    <li><a href="#sobre-mi">Sobre mí</a></li>
    <li><a href="#habilidades">Habilidades</a></li>
    <li><a href="#experiencia">Experiencia</a></li>
    <li><a href="#educacion">Educación</a></li>
    <li><a href="#contacto">Contacto</a></li>
  </ul>
  <button class="nav-burger" id="burger" aria-label="Menú">
    <span></span><span></span><span></span>
  </button>
</nav>
<div class="nav-mobile" id="navMobile">
  <a href="#sobre-mi"    onclick="closeMobile()">Sobre mí</a>
  <a href="#habilidades" onclick="closeMobile()">Habilidades</a>
  <a href="#experiencia" onclick="closeMobile()">Experiencia</a>
  <a href="#educacion"   onclick="closeMobile()">Educación</a>
  <a href="#contacto"    onclick="closeMobile()">Contacto</a>
</div>

<!-- HERO -->
<div class="hero">
  <div class="hero-grid"></div>
  <div class="hero-glow"></div>
  <div class="hero-glow2"></div>
  <div class="hero-left">
    <div class="hero-eyebrow">Paraná, Entre Ríos &nbsp;·&nbsp; Disponible inmediatamente</div>
    <h1>Juan José<br><em>Duarte</em></h1>
    <p class="hero-role">Técnico en Computación &nbsp;·&nbsp; Ing. en IA – FICH UNL</p>
    <p class="hero-desc">
      Egresado técnico con formación sólida en redes, sistemas operativos, programación
      y administración de infraestructura. Actualmente cursando Ingeniería en Inteligencia
      Artificial en la UNL. Proactivo, orientado al trabajo en equipo y con ganas genuinas
      de crecer en entornos técnicos reales.
    </p>
    <div class="hero-cta">
      <a href="#contacto" class="btn btn-primary">Contactar →</a>
      <a href="#sobre-mi" class="btn btn-ghost">Ver portfolio</a>
    </div>
  </div>
  <div class="hero-right">
    <div class="stat-card">
      <span class="stat-num" data-target="7.62">0</span>
      <span class="stat-label">Promedio general — Título técnico</span>
    </div>
    <div class="stat-card">
      <span class="stat-num" data-target="7">0</span>
      <span class="stat-label">Años de formación técnica</span>
    </div>
    <div class="stat-card">
      <span class="stat-num" data-target="9.33">0</span>
      <span class="stat-label">Nota — Inglés Técnico II</span>
    </div>
  </div>
</div>

<!-- SOBRE MÍ -->
<section id="sobre-mi">
  <div class="section-wrap">
    <div class="section-label">Perfil</div>
    <h2>Sobre <em>mí</em></h2>
    <div class="about-grid reveal">
      <div class="about-text">
        <p>Soy <strong>Juan José Duarte</strong>, egresado del Técnico en Computación de la E.T. N°1 "Gral. Francisco Ramírez" de Paraná con un promedio de 7.62, y actualmente cursando <strong>Ingeniería en Inteligencia Artificial</strong> en la FICH-UNL de Santa Fe.</p>
        <p>Mi formación técnica de siete años me dio habilidades reales en redes LAN/VLAN, servidores, sistemas operativos y programación. Participé en Olimpiadas de Informática como especialista en redes, lideré equipos técnicos en actividades interescolares y desarrollé proyectos web durante mis prácticas profesionalizantes.</p>
        <p>Me caracterizo por ser <strong>proactivo</strong>, con excelente predisposición para el trabajo en equipo, alto desempeño en entornos desafiantes y comunicación clara y efectiva tanto con compañeros, superiores y clientes.</p>
        <p>Tengo interés genuino en <strong>automatización, inteligencia artificial e impacto social de la tecnología</strong>, áreas que complementan mi carrera universitaria con exploración práctica continua.</p>
      </div>
      <div class="about-values">
        <div class="value-item">
          <div class="value-num">01</div>
          <div>
            <div class="value-title">Proactividad</div>
            <div class="value-desc">Tomo la iniciativa ante los problemas y propongo soluciones sin esperar que me las indiquen.</div>
          </div>
        </div>
        <div class="value-item">
          <div class="value-num">02</div>
          <div>
            <div class="value-title">Trabajo en equipo</div>
            <div class="value-desc">Coordiné equipos técnicos en contextos reales con otras instituciones educativas.</div>
          </div>
        </div>
        <div class="value-item">
          <div class="value-num">03</div>
          <div>
            <div class="value-title">Aprendizaje continuo</div>
            <div class="value-desc">Estudio Ingeniería en IA mientras exploro automatización, Python y desarrollo de bots en paralelo.</div>
          </div>
        </div>
        <div class="value-item">
          <div class="value-num">04</div>
          <div>
            <div class="value-title">Comunicación efectiva</div>
            <div class="value-desc">Adapto el lenguaje técnico y no técnico al contexto, con trato claro y profesional.</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- HABILIDADES -->
<section id="habilidades" style="background:var(--surface);">
  <div class="section-wrap">
    <div class="section-label">Competencias</div>
    <h2>Habilidades <em>técnicas</em></h2>
    <div class="skills-outer reveal" id="skillsGrid">
      <div class="skill-card">
        <span class="skill-icon">🖧</span>
        <div class="skill-title">Redes & Infraestructura</div>
        <div class="skill-items">
          <div class="skill-row"><div class="skill-name">LAN / VLAN <span>avanzado</span></div><div class="skill-bar-bg"><div class="skill-bar" data-w="85"></div></div></div>
          <div class="skill-row"><div class="skill-name">Diagramado de red <span>avanzado</span></div><div class="skill-bar-bg"><div class="skill-bar" data-w="80"></div></div></div>
          <div class="skill-row"><div class="skill-name">Servidores NAS <span>intermedio</span></div><div class="skill-bar-bg"><div class="skill-bar" data-w="68"></div></div></div>
        </div>
      </div>
      <div class="skill-card">
        <span class="skill-icon">🖥</span>
        <div class="skill-title">Sistemas Operativos</div>
        <div class="skill-items">
          <div class="skill-row"><div class="skill-name">Windows 10/11 <span>avanzado</span></div><div class="skill-bar-bg"><div class="skill-bar" data-w="88"></div></div></div>
          <div class="skill-row"><div class="skill-name">Linux <span>intermedio-av.</span></div><div class="skill-bar-bg"><div class="skill-bar" data-w="74"></div></div></div>
          <div class="skill-row"><div class="skill-name">Soporte técnico <span>avanzado</span></div><div class="skill-bar-bg"><div class="skill-bar" data-w="82"></div></div></div>
        </div>
      </div>
      <div class="skill-card">
        <span class="skill-icon">💻</span>
        <div class="skill-title">Programación</div>
        <div class="skill-items">
          <div class="skill-row"><div class="skill-name">HTML / CSS <span>intermedio</span></div><div class="skill-bar-bg"><div class="skill-bar" data-w="68"></div></div></div>
          <div class="skill-row"><div class="skill-name">Algoritmos <span>intermedio</span></div><div class="skill-bar-bg"><div class="skill-bar" data-w="65"></div></div></div>
          <div class="skill-row"><div class="skill-name">Python <span>básico</span></div><div class="skill-bar-bg"><div class="skill-bar" data-w="35"></div></div></div>
        </div>
      </div>
      <div class="skill-card">
        <span class="skill-icon">📄</span>
        <div class="skill-title">Ofimática & Admin</div>
        <div class="skill-items">
          <div class="skill-row"><div class="skill-name">MS Office 365 <span>avanzado</span></div><div class="skill-bar-bg"><div class="skill-bar" data-w="90"></div></div></div>
          <div class="skill-row"><div class="skill-name">Google Workspace <span>avanzado</span></div><div class="skill-bar-bg"><div class="skill-bar" data-w="85"></div></div></div>
          <div class="skill-row"><div class="skill-name">LibreOffice <span>avanzado</span></div><div class="skill-bar-bg"><div class="skill-bar" data-w="80"></div></div></div>
        </div>
      </div>
      <div class="skill-card">
        <span class="skill-icon">🤖</span>
        <div class="skill-title">IA & Automatización</div>
        <div class="skill-tags">
          <span class="skill-tag">Ing. en IA – UNL</span>
          <span class="skill-tag">Ética en IA</span>
          <span class="skill-tag">Automatización</span>
          <span class="skill-tag">Bots & scraping</span>
          <span class="skill-tag">n8n</span>
          <span class="skill-tag">Ollama / LLMs</span>
          <span class="skill-tag">Impacto social TIC</span>
        </div>
      </div>
      <div class="skill-card">
        <span class="skill-icon">🌐</span>
        <div class="skill-title">Idiomas</div>
        <div class="skill-items">
          <div class="skill-row"><div class="skill-name">Español <span>nativo</span></div><div class="skill-bar-bg"><div class="skill-bar" data-w="100"></div></div></div>
          <div class="skill-row"><div class="skill-name">Inglés Técnico I&II <span>9.33 / 9</span></div><div class="skill-bar-bg"><div class="skill-bar" data-w="80"></div></div></div>
          <div class="skill-row"><div class="skill-name">Inglés general (AACI) <span>intermedio</span></div><div class="skill-bar-bg"><div class="skill-bar" data-w="60"></div></div></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- EXPERIENCIA -->
<section id="experiencia">
  <div class="section-wrap">
    <div class="section-label">Trayectoria</div>
    <h2>Experiencia <em>profesional</em></h2>
    <div class="exp-list">
      <div class="exp-item">
        <div class="exp-dot"></div>
        <div class="exp-meta"><span class="exp-date">2024</span><span class="exp-badge">Liderazgo</span></div>
        <div class="exp-title">Líder de Equipo Técnico</div>
        <div class="exp-org">Actividad Cooperativa Interescolar &mdash; E.S. N°26 &middot; Paraná</div>
        <div class="exp-desc">Coordinación de equipo técnico en el marco de una actividad colaborativa real con otra institución educativa. Gestión de tareas, asignación de roles, resolución de problemas en tiempo real y comunicación efectiva con docentes y compañeros.</div>
        <div class="exp-chips"><span class="exp-chip">Liderazgo</span><span class="exp-chip">Trabajo en equipo</span><span class="exp-chip">Resolución de problemas</span><span class="exp-chip">Comunicación</span></div>
      </div>
      <div class="exp-item">
        <div class="exp-dot"></div>
        <div class="exp-meta"><span class="exp-date">2024</span><span class="exp-badge">Práctica profesionalizante</span></div>
        <div class="exp-title">Frontend Junior</div>
        <div class="exp-org">Empresa Simulada "Cupcakes" &mdash; E.T. N°1 &middot; Paraná</div>
        <div class="exp-desc">Diseño y desarrollo de sitio web institucional con HTML y CSS para una empresa simulada. Atención directa al cliente, asesoramiento técnico y presentación de productos digitales dentro del marco de prácticas profesionalizantes.</div>
        <div class="exp-chips"><span class="exp-chip">HTML</span><span class="exp-chip">CSS</span><span class="exp-chip">Diseño web</span><span class="exp-chip">Atención al cliente</span><span class="exp-chip">Asesoramiento técnico</span></div>
      </div>
      <div class="exp-item">
        <div class="exp-dot"></div>
        <div class="exp-meta"><span class="exp-date">2023 – 2024</span><span class="exp-badge">Competencia</span></div>
        <div class="exp-title">Especialista en Redes</div>
        <div class="exp-org">Olimpiadas de Informática &mdash; Entre Ríos</div>
        <div class="exp-desc">Diagramado, presupuestado, implementación y configuración completa de una red de servidores de complejidad media en el contexto de las Olimpiadas de Informática. Trabajo bajo presión y condiciones de evaluación técnica real.</div>
        <div class="exp-chips"><span class="exp-chip">Redes LAN</span><span class="exp-chip">Servidores</span><span class="exp-chip">Diagramado</span><span class="exp-chip">Presupuestado</span><span class="exp-chip">Trabajo bajo presión</span></div>
      </div>
    </div>
  </div>
</section>

<!-- EDUCACIÓN -->
<section id="educacion" style="background:var(--surface);">
  <div class="section-wrap">
    <div class="section-label">Formación</div>
    <h2>Educación <em>&amp; títulos</em></h2>
    <div class="edu-grid reveal">
      <div class="edu-card highlight">
        <span class="edu-chip">En curso · 2026 →</span>
        <div class="edu-degree">Ingeniería en<br>Inteligencia Artificial</div>
        <div class="edu-school">FICH · Universidad Nacional del Litoral, Santa Fe</div>
        <div class="edu-avg">Institución pública nacional de excelencia</div>
        <div class="edu-tags">
          <span class="edu-tag">Álgebra I</span><span class="edu-tag">Programación I</span><span class="edu-tag">IA & ML</span><span class="edu-tag">FICH–UNL</span>
        </div>
      </div>
      <div class="edu-card">
        <span class="edu-chip">Egresado · Dic 2025</span>
        <div class="edu-degree">Técnico en<br>Computación</div>
        <div class="edu-school">E.T. N°1 "Gral. Francisco Ramírez" · Paraná, Entre Ríos</div>
        <div class="edu-avg">Promedio: 7.62 &nbsp;·&nbsp; Validez nacional RM N°795/2016</div>
        <div class="edu-tags">
          <span class="edu-tag">Programación I/II/III</span><span class="edu-tag">Laboratorio I/II/III</span><span class="edu-tag">Redes & VLAN</span><span class="edu-tag">Bases de datos</span><span class="edu-tag">Sistemas Admin.</span><span class="edu-tag">Análisis de sistemas</span><span class="edu-tag">Simulación</span><span class="edu-tag">Inglés Técnico I & II</span><span class="edu-tag">Lógica</span><span class="edu-tag">Contabilidad</span>
        </div>
      </div>
    </div>
    <div class="grades-panel reveal reveal-d1">
      <button class="grades-header" onclick="toggleGrades()">
        <span class="grades-header-label">📋 &nbsp;Calificaciones destacadas del título técnico</span>
        <span class="grades-arrow" id="gradesArrow">▼</span>
      </button>
      <div class="grades-body" id="gradesBody">
        <table class="grades-table">
          <thead><tr><th>Materia</th><th>Año</th><th>Nota</th></tr></thead>
          <tbody>
            <tr><td>Educación Física</td><td>5° y 6°</td><td class="grade-hi">9.66</td></tr>
            <tr><td>Inglés Técnico II</td><td>7°</td><td class="grade-hi">9.33</td></tr>
            <tr><td>Geografía Económica General</td><td>6°</td><td class="grade-hi">9.33</td></tr>
            <tr><td>Laboratorio I</td><td>5°</td><td class="grade-hi">9.33</td></tr>
            <tr><td>Inglés Técnico I</td><td>6°</td><td class="grade-hi">9.00</td></tr>
            <tr><td>Programación I</td><td>5°</td><td class="grade-hi">9.00</td></tr>
            <tr><td>Lógica</td><td>5°</td><td class="grade-hi">9.00</td></tr>
            <tr><td>Lengua Extranjera (Inglés)</td><td>5°</td><td class="grade-hi">9.00</td></tr>
            <tr><td>Técnicas Digitales</td><td>6°</td><td>8.66</td></tr>
            <tr><td>Educación Física</td><td>7°</td><td>8.66</td></tr>
            <tr><td>Psicología</td><td>6°</td><td>8.33</td></tr>
            <tr><td>Sistemas Administrativos</td><td>6°</td><td>8.33</td></tr>
            <tr><td>Historia Económica Argentina</td><td>6°</td><td>8.33</td></tr>
            <tr><td>Sistema de Proc. de Datos II</td><td>6°</td><td>8.33</td></tr>
            <tr><td>Simulación</td><td>7°</td><td>8.00</td></tr>
            <tr><td>Contabilidad de Costos</td><td>7°</td><td>8.00</td></tr>
            <tr><td>Psicología Aplicada a la Empresa</td><td>7°</td><td>8.00</td></tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</section>

<!-- CONTACTO -->
<section id="contacto">
  <div class="section-wrap">
    <div class="section-label">Conectar</div>
    <h2>¿Hablamos <em>?</em></h2>
    <div class="contact-hero">
      <div>
        <div class="avail-pill"><div class="dot-pulse"></div>Disponible inmediatamente</div>
        <div class="cta-box reveal">
          <h3>Listo para<br><em>sumar al equipo</em></h3>
          <p>Busco pasantías, trabajo part-time o proyectos de tecnología donde pueda aplicar mis conocimientos y seguir creciendo. Tengo disponibilidad inmediata y muchas ganas de aportar valor desde el primer día.</p>
          <a href="mailto:nico.romr1234@gmail.com" class="btn btn-primary">Escribime →</a>
        </div>
      </div>
      <div>
        <p class="contact-intro">Podés contactarme por cualquiera de estos medios. Respondo rápido y con buena disposición.</p>
        <div class="contact-cards reveal reveal-d1">
          <div class="contact-card">
            <div class="contact-icon">📧</div>
            <div><div class="contact-label">Correo</div><a href="mailto:nico.romr1234@gmail.com" class="contact-val">nico.romr1234@gmail.com</a></div>
          </div>
          <div class="contact-card">
            <div class="contact-icon">📱</div>
            <div><div class="contact-label">Teléfono</div><a href="tel:+5433454547871" class="contact-val">+54 343 454-7871</a></div>
          </div>
          <div class="contact-card">
            <div class="contact-icon">💼</div>
            <div><div class="contact-label">LinkedIn</div><a href="https://linkedin.com/in/juan-jose-duarte-8a84a735b" target="_blank" class="contact-val">juan-jose-duarte</a></div>
          </div>
          <div class="contact-card">
            <div class="contact-icon">📍</div>
            <div><div class="contact-label">Ubicación</div><span class="contact-val">Francia 1095 · Paraná, ER</span></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-left">© 2026 Juan José Duarte &nbsp;·&nbsp; Paraná, Argentina</div>
  <div class="footer-right">Diseñado con <span>♥</span> &nbsp;·&nbsp; Portfolio personal</div>
</footer>

<script>
// Cursor
const cur = document.getElementById('cursor');
const ring = document.getElementById('cursorRing');
document.addEventListener('mousemove', e => {
  cur.style.left = e.clientX+'px'; cur.style.top = e.clientY+'px';
  ring.style.left = e.clientX+'px'; ring.style.top = e.clientY+'px';
});
document.querySelectorAll('a,button,.skill-card,.contact-card,.stat-card,.exp-item,.edu-card').forEach(el => {
  el.addEventListener('mouseenter',()=>{ cur.classList.add('hovering'); ring.classList.add('hovering'); });
  el.addEventListener('mouseleave',()=>{ cur.classList.remove('hovering'); ring.classList.remove('hovering'); });
});

// Scroll progress
window.addEventListener('scroll', () => {
  const h = document.documentElement;
  document.getElementById('scroll-bar').style.width = (window.scrollY / (h.scrollHeight - h.clientHeight) * 100) + '%';
});

// Reveal on scroll
const revObs = new IntersectionObserver(entries => {
  entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
}, { threshold: 0.08 });
document.querySelectorAll('.reveal').forEach(el => revObs.observe(el));

// Experience stagger
const expObs = new IntersectionObserver(entries => {
  entries.forEach((e, i) => { if (e.isIntersecting) setTimeout(() => e.target.classList.add('visible'), i * 130); });
}, { threshold: 0.1 });
document.querySelectorAll('.exp-item').forEach(el => expObs.observe(el));

// Skill bars
const barObs = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.querySelectorAll('.skill-bar').forEach(b => { b.style.width = b.dataset.w + '%'; });
      barObs.unobserve(e.target);
    }
  });
}, { threshold: 0.2 });
const sg = document.getElementById('skillsGrid');
if (sg) barObs.observe(sg);

// Counter animation
function animateNum(el) {
  const target = parseFloat(el.dataset.target);
  const dec = String(target).includes('.') ? String(target).split('.')[1].length : 0;
  const dur = 1600; const start = performance.now();
  function step(now) {
    const p = Math.min((now - start) / dur, 1);
    const e2 = 1 - Math.pow(1 - p, 3);
    el.textContent = dec ? (e2 * target).toFixed(dec) : Math.floor(e2 * target);
    if (p < 1) requestAnimationFrame(step);
    else el.textContent = dec ? target.toFixed(dec) : target;
  }
  requestAnimationFrame(step);
}
const cntObs = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) { document.querySelectorAll('.stat-num[data-target]').forEach(animateNum); cntObs.disconnect(); }
  });
}, { threshold: 0.5 });
const hr = document.querySelector('.hero-right');
if (hr) cntObs.observe(hr);

// Grades accordion
function toggleGrades() {
  document.getElementById('gradesBody').classList.toggle('open');
  document.getElementById('gradesArrow').classList.toggle('open');
}

// Mobile menu
const burger = document.getElementById('burger');
const nm = document.getElementById('navMobile');
burger.addEventListener('click', () => {
  burger.classList.toggle('open'); nm.classList.toggle('open');
  document.body.style.overflow = nm.classList.contains('open') ? 'hidden' : '';
});
function closeMobile() {
  burger.classList.remove('open'); nm.classList.remove('open');
  document.body.style.overflow = '';
}
</script>
</body>
</html>
