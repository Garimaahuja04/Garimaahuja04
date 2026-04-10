<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Garima Ahuja – Data Analyst & Software Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;600;700;900&family=Raleway:wght@300;400;500;600&family=Crimson+Text:ital,wght@0,400;0,600;1,400&display=swap" rel="stylesheet">
<style>
  :root {
    --gold: #c9a84c;
    --gold-light: #f0d080;
    --gold-dim: #8a6f2e;
    --deep-purple: #0d0618;
    --mid-purple: #1a0a2e;
    --purple: #2d1458;
    --purple-bright: #5b2d8e;
    --blue-dark: #0a0f2e;
    --blue-mid: #0f1f5c;
    --blue-bright: #2040a0;
    --silver: #c8cfe8;
    --silver-dim: #8890b0;
    --white: #f0eaff;
    --text: #d4cce8;
    --glow-gold: rgba(201,168,76,0.35);
    --glow-purple: rgba(91,45,142,0.5);
  }

  *, *::before, *::after { margin:0; padding:0; box-sizing:border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--deep-purple);
    color: var(--text);
    font-family: 'Raleway', sans-serif;
    font-weight: 400;
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom cursor */
  .cursor {
    position: fixed; width: 12px; height: 12px;
    background: var(--gold); border-radius: 50%;
    pointer-events: none; z-index: 99999;
    transform: translate(-50%,-50%);
    transition: transform 0.1s, background 0.2s;
    mix-blend-mode: screen;
  }
  .cursor-trail {
    position: fixed; width: 32px; height: 32px;
    border: 1px solid var(--gold-light);
    border-radius: 50%; pointer-events: none;
    z-index: 99998; transform: translate(-50%,-50%);
    transition: all 0.18s ease; opacity: 0.5;
  }

  /* Stars background */
  .stars-bg {
    position: fixed; top:0; left:0; width:100%; height:100%;
    pointer-events: none; z-index: 0; overflow: hidden;
  }
  .star {
    position: absolute; background: white; border-radius: 50%;
    animation: twinkle var(--dur, 3s) var(--delay, 0s) infinite alternate;
  }
  @keyframes twinkle {
    from { opacity: 0.1; transform: scale(0.8); }
    to   { opacity: 0.9; transform: scale(1.2); }
  }

  /* Floating particles */
  .particle {
    position: fixed; pointer-events: none; z-index: 1;
    border-radius: 50%;
    animation: float-up linear infinite;
    opacity: 0;
  }
  @keyframes float-up {
    0%   { transform: translateY(100vh) translateX(0) scale(0); opacity:0; }
    10%  { opacity: 0.6; }
    90%  { opacity: 0.3; }
    100% { transform: translateY(-10vh) translateX(var(--drift,20px)) scale(1); opacity:0; }
  }

  /* Navbar */
  nav {
    position: fixed; top:0; width:100%; z-index:1000;
    padding: 0 5%;
    display: flex; align-items: center; justify-content: space-between;
    height: 70px;
    transition: all 0.4s ease;
    border-bottom: 1px solid transparent;
  }
  nav.scrolled {
    background: rgba(13,6,24,0.92);
    backdrop-filter: blur(16px);
    border-bottom-color: rgba(201,168,76,0.2);
    box-shadow: 0 4px 30px rgba(0,0,0,0.5);
  }
  .nav-logo {
    font-family: 'Cinzel', serif;
    font-size: 1.3rem;
    font-weight: 700;
    color: var(--gold-light);
    letter-spacing: 2px;
    text-decoration: none;
    text-shadow: 0 0 20px var(--glow-gold);
  }
  .nav-logo span { color: var(--silver); }
  .nav-links { display: flex; gap: 2rem; list-style: none; }
  .nav-links a {
    color: var(--silver-dim);
    text-decoration: none;
    font-size: 0.78rem;
    letter-spacing: 2px;
    text-transform: uppercase;
    font-weight: 500;
    transition: color 0.3s, text-shadow 0.3s;
    position: relative;
  }
  .nav-links a::after {
    content: '';
    position: absolute; bottom: -4px; left:0; width:0; height:1px;
    background: var(--gold); transition: width 0.3s;
  }
  .nav-links a:hover, .nav-links a.active {
    color: var(--gold-light);
    text-shadow: 0 0 12px var(--glow-gold);
  }
  .nav-links a:hover::after, .nav-links a.active::after { width: 100%; }

  /* Hamburger */
  .hamburger { display:none; flex-direction:column; gap:5px; cursor:pointer; }
  .hamburger span {
    width:25px; height:2px; background: var(--gold);
    transition: all 0.3s; display:block;
  }
  .hamburger.open span:nth-child(1) { transform: rotate(45deg) translate(5px,5px); }
  .hamburger.open span:nth-child(2) { opacity:0; }
  .hamburger.open span:nth-child(3) { transform: rotate(-45deg) translate(5px,-5px); }

  /* Sections */
  section { position: relative; z-index: 10; }

  /* ── HERO ── */
  #hero {
    min-height: 100vh;
    display: flex; align-items: center; justify-content: center;
    padding: 100px 5% 60px;
    overflow: hidden;
    background:
      radial-gradient(ellipse 80% 60% at 50% 20%, rgba(91,45,142,0.3) 0%, transparent 60%),
      radial-gradient(ellipse 50% 40% at 80% 80%, rgba(32,64,160,0.25) 0%, transparent 50%),
      radial-gradient(ellipse 40% 30% at 20% 70%, rgba(201,168,76,0.08) 0%, transparent 50%);
  }
  .hero-inner {
    max-width: 900px; width:100%;
    display: flex; flex-direction: column; align-items: center;
    text-align: center; gap: 1.6rem;
  }
  .hero-badge {
    display: inline-flex; align-items: center; gap: 0.5rem;
    border: 1px solid rgba(201,168,76,0.4);
    padding: 0.4rem 1.2rem; border-radius: 999px;
    font-size: 0.72rem; letter-spacing: 3px; text-transform: uppercase;
    color: var(--gold); background: rgba(201,168,76,0.06);
    animation: fadeDown 0.8s ease both;
  }
  .hero-badge::before { content: '✦'; font-size: 0.6rem; }
  .hero-badge::after  { content: '✦'; font-size: 0.6rem; }

  .hero-name {
    font-family: 'Cinzel', serif;
    font-size: clamp(2.8rem, 8vw, 6.5rem);
    font-weight: 900;
    line-height: 1;
    letter-spacing: 0.04em;
    background: linear-gradient(135deg, var(--gold-light) 0%, var(--gold) 40%, var(--silver) 70%, var(--gold-light) 100%);
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    background-clip: text;
    filter: drop-shadow(0 0 30px var(--glow-gold));
    animation: fadeUp 1s 0.2s ease both;
  }
  .hero-title {
    font-family: 'Cinzel', serif;
    font-size: clamp(0.9rem, 2.5vw, 1.2rem);
    letter-spacing: 4px; text-transform: uppercase;
    color: var(--silver-dim); font-weight: 400;
    animation: fadeUp 1s 0.4s ease both;
  }
  .hero-divider {
    width: 120px; height: 1px;
    background: linear-gradient(90deg, transparent, var(--gold), transparent);
    animation: fadeUp 1s 0.5s ease both;
  }
  .hero-tagline {
    font-family: 'Crimson Text', serif;
    font-style: italic;
    font-size: clamp(1rem, 2.5vw, 1.35rem);
    color: var(--text); max-width: 600px;
    line-height: 1.7;
    animation: fadeUp 1s 0.6s ease both;
  }
  .hero-cta {
    display: flex; gap: 1rem; flex-wrap: wrap; justify-content: center;
    animation: fadeUp 1s 0.8s ease both;
  }
  .btn-primary {
    padding: 0.85rem 2.4rem;
    background: linear-gradient(135deg, var(--gold-dim), var(--gold));
    border: none; border-radius: 4px;
    font-family: 'Cinzel', serif;
    font-size: 0.75rem; letter-spacing: 2.5px; text-transform: uppercase;
    color: var(--deep-purple); font-weight: 700;
    cursor: none; text-decoration: none;
    position: relative; overflow: hidden;
    transition: transform 0.3s, box-shadow 0.3s;
    box-shadow: 0 4px 24px rgba(201,168,76,0.3);
  }
  .btn-primary::before {
    content: ''; position:absolute; inset:0;
    background: linear-gradient(135deg, var(--gold-light), var(--gold-dim));
    opacity: 0; transition: opacity 0.3s;
  }
  .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 8px 40px rgba(201,168,76,0.5); }
  .btn-primary:hover::before { opacity: 1; }
  .btn-primary span { position: relative; z-index:1; }

  .btn-outline {
    padding: 0.85rem 2.4rem;
    background: transparent;
    border: 1px solid rgba(201,168,76,0.5); border-radius: 4px;
    font-family: 'Cinzel', serif;
    font-size: 0.75rem; letter-spacing: 2.5px; text-transform: uppercase;
    color: var(--gold); cursor: none; text-decoration: none;
    transition: all 0.3s;
  }
  .btn-outline:hover {
    background: rgba(201,168,76,0.08);
    border-color: var(--gold);
    box-shadow: 0 0 24px rgba(201,168,76,0.2);
  }

  .hero-scroll {
    margin-top: 1rem;
    animation: fadeUp 1s 1s ease both;
    display: flex; flex-direction: column; align-items: center; gap: 0.5rem;
  }
  .hero-scroll span { font-size: 0.65rem; letter-spacing: 3px; text-transform: uppercase; color: var(--silver-dim); }
  .scroll-line {
    width: 1px; height: 50px;
    background: linear-gradient(180deg, var(--gold), transparent);
    animation: scrollPulse 2s infinite;
  }
  @keyframes scrollPulse {
    0%,100% { opacity: 0.3; transform: scaleY(1); }
    50% { opacity: 1; transform: scaleY(1.2); }
  }

  /* Crest decoration */
  .hero-crest {
    position: absolute; top: 50%; right: 5%;
    transform: translateY(-50%);
    width: 220px; height: 220px;
    opacity: 0.06;
    pointer-events: none;
  }

  /* ── SECTION COMMON ── */
  .section-wrap {
    max-width: 1100px; margin: 0 auto;
    padding: 100px 5%;
  }
  .section-header {
    text-align: center; margin-bottom: 60px;
  }
  .section-eyebrow {
    font-size: 0.68rem; letter-spacing: 4px;
    text-transform: uppercase; color: var(--gold);
    display: flex; align-items: center; justify-content: center; gap: 1rem;
    margin-bottom: 1rem;
  }
  .section-eyebrow::before, .section-eyebrow::after {
    content: ''; flex: 1; max-width: 60px; height:1px;
    background: linear-gradient(90deg, transparent, var(--gold));
  }
  .section-eyebrow::after { background: linear-gradient(90deg, var(--gold), transparent); }
  .section-title {
    font-family: 'Cinzel', serif;
    font-size: clamp(1.8rem, 4vw, 2.8rem);
    font-weight: 700;
    color: var(--white);
    letter-spacing: 0.05em;
    text-shadow: 0 0 40px rgba(201,168,76,0.2);
  }

  /* Reveal animation */
  .reveal {
    opacity: 0; transform: translateY(40px);
    transition: opacity 0.8s ease, transform 0.8s ease;
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }
  .reveal-left {
    opacity: 0; transform: translateX(-40px);
    transition: opacity 0.8s ease, transform 0.8s ease;
  }
  .reveal-left.visible { opacity: 1; transform: translateX(0); }
  .reveal-right {
    opacity: 0; transform: translateX(40px);
    transition: opacity 0.8s ease, transform 0.8s ease;
  }
  .reveal-right.visible { opacity: 1; transform: translateX(0); }

  /* ── ABOUT ── */
  #about { background: linear-gradient(180deg, var(--deep-purple) 0%, var(--mid-purple) 100%); }
  .about-grid {
    display: grid; grid-template-columns: 1fr 1fr; gap: 60px; align-items: center;
  }
  .about-visual {
    display: flex; justify-content: center;
  }
  .about-crest-wrap {
    position: relative; width: 260px; height: 300px;
  }
  .crest-ring {
    position: absolute; top:50%; left:50%;
    border-radius: 50%;
    border: 1px solid rgba(201,168,76,0.25);
    transform: translate(-50%,-50%);
    animation: rotate-ring 20s linear infinite;
  }
  .crest-ring-1 { width:220px; height:220px; animation-direction: normal; }
  .crest-ring-2 { width:280px; height:280px; animation-direction: reverse; animation-duration: 30s; }
  @keyframes rotate-ring {
    from { transform: translate(-50%,-50%) rotate(0deg); }
    to   { transform: translate(-50%,-50%) rotate(360deg); }
  }
  .crest-center {
    position:absolute; top:50%; left:50%; transform:translate(-50%,-50%);
    width: 140px; height: 140px;
    background: radial-gradient(circle, rgba(91,45,142,0.6), rgba(13,6,24,0.9));
    border-radius: 4px 40px 4px 40px;
    border: 1px solid rgba(201,168,76,0.4);
    display: flex; align-items: center; justify-content: center;
    box-shadow: 0 0 40px var(--glow-purple), inset 0 0 30px rgba(201,168,76,0.05);
    font-family: 'Cinzel', serif;
    font-size: 3.5rem; color: var(--gold);
    text-shadow: 0 0 20px var(--glow-gold);
  }
  .about-text h3 {
    font-family: 'Cinzel', serif;
    font-size: 1.6rem; color: var(--gold-light);
    margin-bottom: 1.2rem; letter-spacing: 1px;
  }
  .about-text p {
    font-size: 0.95rem; line-height: 1.85;
    color: var(--text); margin-bottom: 1.2rem;
  }
  .about-facts {
    display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 1.5rem;
  }
  .fact-item {
    padding: 0.8rem 1rem;
    background: rgba(201,168,76,0.05);
    border: 1px solid rgba(201,168,76,0.15);
    border-radius: 6px;
  }
  .fact-label { font-size: 0.62rem; letter-spacing: 2px; text-transform: uppercase; color: var(--gold); margin-bottom: 0.3rem; }
  .fact-value { font-size: 0.88rem; color: var(--white); font-weight: 500; }

  /* ── SKILLS ── */
  #skills {
    background: linear-gradient(180deg, var(--mid-purple) 0%, var(--blue-dark) 100%);
  }
  .skills-grid {
    display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 1.5rem;
  }
  .skill-category {
    background: rgba(255,255,255,0.03);
    border: 1px solid rgba(201,168,76,0.15);
    border-radius: 12px; padding: 1.8rem;
    position: relative; overflow: hidden;
    transition: border-color 0.3s, box-shadow 0.3s, transform 0.3s;
  }
  .skill-category::before {
    content:''; position:absolute; top:0; left:0; right:0; height:2px;
    background: linear-gradient(90deg, transparent, var(--gold), transparent);
    opacity: 0; transition: opacity 0.3s;
  }
  .skill-category:hover {
    border-color: rgba(201,168,76,0.35);
    box-shadow: 0 8px 40px rgba(201,168,76,0.1);
    transform: translateY(-4px);
  }
  .skill-category:hover::before { opacity: 1; }
  .skill-cat-icon {
    font-size: 1.6rem; margin-bottom: 0.8rem;
    filter: drop-shadow(0 0 8px var(--glow-gold));
  }
  .skill-cat-title {
    font-family: 'Cinzel', serif;
    font-size: 0.85rem; letter-spacing: 2px;
    text-transform: uppercase; color: var(--gold-light);
    margin-bottom: 1.2rem;
  }
  .skill-tags { display: flex; flex-wrap: wrap; gap: 0.5rem; }
  .skill-tag {
    padding: 0.35rem 0.85rem;
    background: rgba(91,45,142,0.3);
    border: 1px solid rgba(91,45,142,0.5);
    border-radius: 999px;
    font-size: 0.75rem; color: var(--silver);
    transition: all 0.3s; cursor: default;
  }
  .skill-tag:hover {
    background: rgba(201,168,76,0.15);
    border-color: var(--gold-dim);
    color: var(--gold-light);
  }

  /* Skill bars */
  .skill-bar-list { margin-top: 1.5rem; display:flex; flex-direction:column; gap:0.9rem; }
  .skill-bar-item {}
  .skill-bar-header { display:flex; justify-content:space-between; margin-bottom:0.35rem; }
  .skill-bar-name { font-size:0.82rem; color: var(--text); }
  .skill-bar-pct { font-size:0.75rem; color: var(--gold); font-family:'Cinzel',serif; }
  .skill-bar-track {
    height: 4px; background: rgba(255,255,255,0.07); border-radius:999px; overflow:hidden;
  }
  .skill-bar-fill {
    height:100%; width:0; border-radius:999px;
    background: linear-gradient(90deg, var(--gold-dim), var(--gold-light));
    transition: width 1.2s cubic-bezier(0.25,1,0.5,1);
    box-shadow: 0 0 8px var(--glow-gold);
  }

  /* ── PROJECTS ── */
  #projects {
    background: linear-gradient(180deg, var(--blue-dark) 0%, var(--mid-purple) 100%);
  }
  .projects-grid {
    display: grid; grid-template-columns: repeat(auto-fit, minmax(320px, 1fr)); gap: 1.8rem;
  }
  .project-card {
    background: rgba(255,255,255,0.025);
    border: 1px solid rgba(201,168,76,0.12);
    border-radius: 14px; padding: 2rem;
    position: relative; overflow: hidden;
    transition: all 0.4s ease;
    cursor: none;
  }
  .project-card::after {
    content:''; position:absolute;
    bottom:0; left:0; right:0; height:3px;
    background: linear-gradient(90deg, var(--blue-bright), var(--purple-bright), var(--gold-dim));
    transform: scaleX(0); transform-origin: left;
    transition: transform 0.4s ease;
  }
  .project-card:hover {
    border-color: rgba(201,168,76,0.3);
    transform: translateY(-6px);
    box-shadow: 0 16px 60px rgba(0,0,0,0.5), 0 0 40px rgba(91,45,142,0.2);
  }
  .project-card:hover::after { transform: scaleX(1); }
  .project-num {
    font-family: 'Cinzel', serif;
    font-size: 3rem; font-weight: 900;
    color: rgba(201,168,76,0.08);
    position: absolute; top: 1rem; right: 1.5rem;
    line-height: 1;
  }
  .project-icon {
    font-size: 2rem; margin-bottom: 1rem;
    display: inline-block;
    filter: drop-shadow(0 0 12px var(--glow-gold));
  }
  .project-title {
    font-family: 'Cinzel', serif;
    font-size: 1.1rem; color: var(--gold-light);
    margin-bottom: 0.8rem; letter-spacing: 0.5px;
  }
  .project-desc {
    font-size: 0.88rem; color: var(--text);
    line-height: 1.75; margin-bottom: 1.2rem;
  }
  .project-tags { display:flex; flex-wrap:wrap; gap:0.4rem; }
  .project-tag {
    padding: 0.25rem 0.7rem;
    background: rgba(32,64,160,0.3);
    border: 1px solid rgba(32,64,160,0.5);
    border-radius: 4px; font-size: 0.68rem;
    letter-spacing: 1px; color: var(--silver);
    text-transform: uppercase;
  }

  /* ── RESEARCH ── */
  #research {
    background: linear-gradient(180deg, var(--mid-purple) 0%, var(--deep-purple) 100%);
  }
  .research-grid {
    display: grid; grid-template-columns: 1fr 1fr; gap: 2rem;
  }
  .research-card {
    padding: 2.2rem;
    background: rgba(255,255,255,0.02);
    border: 1px solid rgba(201,168,76,0.1);
    border-radius: 12px; position: relative;
    transition: all 0.3s;
  }
  .research-card::before {
    content: ''; position:absolute; left:0; top:0; bottom:0;
    width:3px; border-radius:3px 0 0 3px;
    background: linear-gradient(180deg, var(--gold), var(--purple-bright));
  }
  .research-card:hover {
    border-color: rgba(201,168,76,0.25);
    box-shadow: 0 8px 40px rgba(0,0,0,0.3);
    transform: translateX(4px);
  }
  .research-icon { font-size:1.5rem; margin-bottom:0.8rem; }
  .research-title {
    font-family: 'Cinzel', serif;
    font-size: 1rem; color: var(--gold-light);
    margin-bottom: 0.8rem; line-height: 1.4;
  }
  .research-desc {
    font-size: 0.85rem; color: var(--text); line-height: 1.7;
  }

  /* ── EDUCATION ── */
  #education {
    background: linear-gradient(180deg, var(--deep-purple) 0%, var(--blue-dark) 100%);
  }
  .edu-timeline {
    position:relative; max-width:700px; margin:0 auto;
    padding-left: 40px;
  }
  .edu-timeline::before {
    content:''; position:absolute; left:11px; top:0; bottom:0; width:1px;
    background: linear-gradient(180deg, var(--gold), rgba(201,168,76,0.1));
  }
  .edu-item {
    position:relative; margin-bottom:3rem; padding-bottom:0.5rem;
  }
  .edu-dot {
    position:absolute; left:-40px; top:4px;
    width:22px; height:22px; border-radius:50%;
    background: var(--deep-purple);
    border: 2px solid var(--gold);
    box-shadow: 0 0 16px var(--glow-gold);
    display:flex; align-items:center; justify-content:center;
  }
  .edu-dot::after {
    content:''; width:8px; height:8px; border-radius:50%; background:var(--gold);
  }
  .edu-year {
    font-size:0.68rem; letter-spacing:2px; text-transform:uppercase;
    color:var(--gold); margin-bottom:0.5rem;
  }
  .edu-degree {
    font-family:'Cinzel',serif; font-size:1.1rem; color:var(--white);
    margin-bottom:0.4rem;
  }
  .edu-school {
    font-size:0.9rem; color:var(--text); margin-bottom:0.4rem;
  }
  .edu-grade {
    display:inline-block; padding:0.25rem 0.8rem;
    background:rgba(201,168,76,0.1);
    border:1px solid rgba(201,168,76,0.3);
    border-radius:4px; font-size:0.78rem; color:var(--gold);
    font-family:'Cinzel',serif;
  }

  /* ── ACHIEVEMENTS ── */
  #achievements {
    background: var(--blue-dark);
  }
  .ach-wrap {
    display:flex; justify-content:center;
  }
  .ach-card {
    max-width:600px; width:100%;
    padding: 2.5rem 3rem;
    background: radial-gradient(ellipse at top, rgba(91,45,142,0.3) 0%, transparent 60%),
                rgba(255,255,255,0.02);
    border: 1px solid rgba(201,168,76,0.2);
    border-radius:16px; text-align:center;
    position:relative; overflow:hidden;
  }
  .ach-card::before {
    content:''; position:absolute; top:-1px; left:20%; right:20%; height:2px;
    background: linear-gradient(90deg, transparent, var(--gold), transparent);
  }
  .ach-medal { font-size:3.5rem; display:block; margin-bottom:1.2rem; }
  .ach-title {
    font-family:'Cinzel',serif; font-size:1.3rem; color:var(--gold-light);
    margin-bottom:0.8rem; letter-spacing:1px;
  }
  .ach-desc { font-size:0.9rem; color:var(--text); line-height:1.7; }

  /* ── CONTACT ── */
  #contact {
    background: linear-gradient(180deg, var(--blue-dark) 0%, var(--deep-purple) 100%);
  }
  .contact-wrap {
    display:grid; grid-template-columns:1fr 1fr; gap:60px; align-items:start;
  }
  .contact-info h3 {
    font-family:'Cinzel',serif; font-size:1.6rem; color:var(--gold-light);
    margin-bottom:1rem;
  }
  .contact-info p { font-size:0.9rem; color:var(--text); line-height:1.8; margin-bottom:2rem; }
  .contact-links { display:flex; flex-direction:column; gap:1rem; }
  .contact-link {
    display:flex; align-items:center; gap:1rem;
    padding:1rem 1.2rem;
    background:rgba(255,255,255,0.02);
    border:1px solid rgba(201,168,76,0.12);
    border-radius:8px; text-decoration:none;
    transition:all 0.3s; cursor:none;
  }
  .contact-link:hover {
    background:rgba(201,168,76,0.06);
    border-color:rgba(201,168,76,0.3);
    transform:translateX(6px);
    box-shadow:0 4px 24px rgba(0,0,0,0.3);
  }
  .contact-link-icon { font-size:1.3rem; flex-shrink:0; }
  .contact-link-text {}
  .contact-link-label { font-size:0.62rem; letter-spacing:2px; text-transform:uppercase; color:var(--gold); }
  .contact-link-val { font-size:0.88rem; color:var(--white); }

  .contact-form {
    background:rgba(255,255,255,0.02);
    border:1px solid rgba(201,168,76,0.12);
    border-radius:14px; padding:2rem;
  }
  .form-group { margin-bottom:1.2rem; }
  .form-group label {
    display:block; font-size:0.68rem; letter-spacing:2px;
    text-transform:uppercase; color:var(--gold);
    margin-bottom:0.5rem;
  }
  .form-group input, .form-group textarea {
    width:100%; padding:0.8rem 1rem;
    background:rgba(255,255,255,0.04);
    border:1px solid rgba(201,168,76,0.15);
    border-radius:6px; color:var(--white);
    font-family:'Raleway',sans-serif; font-size:0.88rem;
    transition:border-color 0.3s, box-shadow 0.3s;
    outline:none; resize:vertical;
  }
  .form-group textarea { min-height:100px; }
  .form-group input:focus, .form-group textarea:focus {
    border-color:rgba(201,168,76,0.4);
    box-shadow:0 0 16px rgba(201,168,76,0.1);
  }
  .form-group input::placeholder, .form-group textarea::placeholder { color:var(--silver-dim); }

  /* Footer */
  footer {
    position:relative; z-index:10;
    text-align:center; padding:2rem;
    border-top:1px solid rgba(201,168,76,0.1);
    background:var(--deep-purple);
  }
  .footer-text {
    font-size:0.72rem; letter-spacing:2px; text-transform:uppercase;
    color:var(--silver-dim);
  }
  .footer-text span { color:var(--gold); }

  /* Animations */
  @keyframes fadeUp {
    from { opacity:0; transform:translateY(30px); }
    to   { opacity:1; transform:translateY(0); }
  }
  @keyframes fadeDown {
    from { opacity:0; transform:translateY(-20px); }
    to   { opacity:1; transform:translateY(0); }
  }

  /* Dividers */
  .section-divider {
    position:relative; z-index:10;
    height:1px;
    background:linear-gradient(90deg, transparent, rgba(201,168,76,0.2), transparent);
  }

  /* Responsive */
  @media (max-width:900px) {
    .about-grid, .research-grid, .contact-wrap { grid-template-columns:1fr; }
    .about-visual { display:none; }
    .nav-links {
      position:fixed; top:70px; left:0; right:0;
      background:rgba(13,6,24,0.97); backdrop-filter:blur(16px);
      flex-direction:column; padding:2rem;
      transform:translateY(-120%); transition:transform 0.4s;
      border-bottom:1px solid rgba(201,168,76,0.15);
    }
    .nav-links.open { transform:translateY(0); }
    .hamburger { display:flex; }
    .hero-crest { display:none; }
  }
  @media (max-width:600px) {
    .about-facts { grid-template-columns:1fr; }
    .projects-grid { grid-template-columns:1fr; }
  }

  /* Magical sparkle dots on scroll */
  .sparkle {
    position:fixed; pointer-events:none; z-index:9999;
    width:6px; height:6px; border-radius:50%;
    background:var(--gold-light);
    animation:sparkle-pop 0.6s ease-out forwards;
  }
  @keyframes sparkle-pop {
    0%   { transform:scale(0) rotate(0deg); opacity:1; }
    50%  { transform:scale(1.5) rotate(180deg); opacity:0.8; }
    100% { transform:scale(0) rotate(360deg); opacity:0; }
  }
</style>
</head>
<body>

<!-- Custom cursor -->
<div class="cursor" id="cursor"></div>
<div class="cursor-trail" id="cursorTrail"></div>

<!-- Stars background -->
<div class="stars-bg" id="starsContainer"></div>

<!-- Particles -->
<div id="particlesContainer"></div>

<!-- Navbar -->
<nav id="navbar">
  <a href="#hero" class="nav-logo">G<span>A</span></a>
  <ul class="nav-links" id="navLinks">
    <li><a href="#about">About</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#research">Research</a></li>
    <li><a href="#education">Education</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <div class="hamburger" id="hamburger">
    <span></span><span></span><span></span>
  </div>
</nav>

<!-- HERO -->
<section id="hero">
  <svg class="hero-crest" viewBox="0 0 200 240" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path d="M100 10 L190 50 L190 140 Q190 200 100 230 Q10 200 10 140 L10 50 Z" stroke="gold" stroke-width="2" fill="none"/>
    <path d="M100 30 L170 60 L170 135 Q170 185 100 210 Q30 185 30 135 L30 60 Z" stroke="gold" stroke-width="1" fill="none" opacity="0.5"/>
    <line x1="100" y1="10" x2="100" y2="230" stroke="gold" stroke-width="0.5" opacity="0.3"/>
    <line x1="10" y1="120" x2="190" y2="120" stroke="gold" stroke-width="0.5" opacity="0.3"/>
    <circle cx="100" cy="120" r="30" stroke="gold" stroke-width="1" fill="none" opacity="0.5"/>
    <text x="100" y="128" text-anchor="middle" fill="gold" font-size="28" font-family="serif" opacity="0.6">⚡</text>
  </svg>

  <div class="hero-inner">
    <div class="hero-badge reveal">Data Analyst & Developer</div>
    <h1 class="hero-name">Garima Ahuja</h1>
    <p class="hero-title">Crafting Digital Magic with Data</p>
    <div class="hero-divider reveal"></div>
    <p class="hero-tagline reveal">"Transforming data into meaningful insights and digital solutions"</p>
    <div class="hero-cta">
      <a href="#projects" class="btn-primary"><span>View My Work</span></a>
      <a href="#contact" class="btn-outline">Contact Me</a>
    </div>
    <div class="hero-scroll">
      <span>Scroll</span>
      <div class="scroll-line"></div>
    </div>
  </div>
</section>

<div class="section-divider"></div>

<!-- ABOUT -->
<section id="about">
  <div class="section-wrap">
    <div class="section-header">
      <div class="section-eyebrow reveal">Who I Am</div>
      <h2 class="section-title reveal">About Me</h2>
    </div>
    <div class="about-grid">
      <div class="about-visual reveal-left">
        <div class="about-crest-wrap">
          <div class="crest-ring crest-ring-1"></div>
          <div class="crest-ring crest-ring-2"></div>
          <div class="crest-center">⚡</div>
        </div>
      </div>
      <div class="about-text reveal-right">
        <h3>The Wizard Behind the Data</h3>
        <p>Motivated Computer Science undergraduate with a strong foundation in data analytics, Python programming, and NLP-based solutions. Like a spell-caster decoding ancient runes, I decode complex data into actionable intelligence.</p>
        <p>Experienced in building end-to-end data analysis tools spanning data preprocessing, visualization, and sentiment classification across domains including social media, academics, and product analytics.</p>
        <div class="about-facts">
          <div class="fact-item">
            <div class="fact-label">Location</div>
            <div class="fact-value">Gurugram, India</div>
          </div>
          <div class="fact-item">
            <div class="fact-label">Degree</div>
            <div class="fact-value">B.Tech CSE (2024–28)</div>
          </div>
          <div class="fact-item">
            <div class="fact-label">Focus</div>
            <div class="fact-value">Data Analytics & NLP</div>
          </div>
          <div class="fact-item">
            <div class="fact-label">CGPA</div>
            <div class="fact-value">7.62</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<div class="section-divider"></div>

<!-- SKILLS -->
<section id="skills">
  <div class="section-wrap">
    <div class="section-header">
      <div class="section-eyebrow reveal">My Arsenal</div>
      <h2 class="section-title reveal">Skills & Expertise</h2>
    </div>
    <div class="skills-grid">
      <div class="skill-category reveal">
        <div class="skill-cat-icon">🐍</div>
        <div class="skill-cat-title">Programming Languages</div>
        <div class="skill-tags">
          <span class="skill-tag">Python</span>
          <span class="skill-tag">SQL</span>
        </div>
        <div class="skill-bar-list">
          <div class="skill-bar-item">
            <div class="skill-bar-header"><span class="skill-bar-name">Python</span><span class="skill-bar-pct">88%</span></div>
            <div class="skill-bar-track"><div class="skill-bar-fill" data-width="88"></div></div>
          </div>
          <div class="skill-bar-item">
            <div class="skill-bar-header"><span class="skill-bar-name">SQL</span><span class="skill-bar-pct">72%</span></div>
            <div class="skill-bar-track"><div class="skill-bar-fill" data-width="72"></div></div>
          </div>
        </div>
      </div>

      <div class="skill-category reveal">
        <div class="skill-cat-icon">📚</div>
        <div class="skill-cat-title">Libraries & Frameworks</div>
        <div class="skill-tags">
          <span class="skill-tag">Pandas</span>
          <span class="skill-tag">NumPy</span>
          <span class="skill-tag">Matplotlib</span>
          <span class="skill-tag">Scikit-learn</span>
        </div>
        <div class="skill-bar-list">
          <div class="skill-bar-item">
            <div class="skill-bar-header"><span class="skill-bar-name">Pandas / NumPy</span><span class="skill-bar-pct">85%</span></div>
            <div class="skill-bar-track"><div class="skill-bar-fill" data-width="85"></div></div>
          </div>
          <div class="skill-bar-item">
            <div class="skill-bar-header"><span class="skill-bar-name">Matplotlib</span><span class="skill-bar-pct">80%</span></div>
            <div class="skill-bar-track"><div class="skill-bar-fill" data-width="80"></div></div>
          </div>
          <div class="skill-bar-item">
            <div class="skill-bar-header"><span class="skill-bar-name">Scikit-learn</span><span class="skill-bar-pct">70%</span></div>
            <div class="skill-bar-track"><div class="skill-bar-fill" data-width="70"></div></div>
          </div>
        </div>
      </div>

      <div class="skill-category reveal">
        <div class="skill-cat-icon">🔮</div>
        <div class="skill-cat-title">Core Areas</div>
        <div class="skill-tags">
          <span class="skill-tag">Data Analysis</span>
          <span class="skill-tag">Data Visualization</span>
          <span class="skill-tag">NLP</span>
          <span class="skill-tag">Sentiment Analysis</span>
          <span class="skill-tag">Web Development</span>
        </div>
      </div>

      <div class="skill-category reveal">
        <div class="skill-cat-icon">🛠️</div>
        <div class="skill-cat-title">Tools</div>
        <div class="skill-tags">
          <span class="skill-tag">GitHub</span>
          <span class="skill-tag">Excel</span>
          <span class="skill-tag">Jupyter Notebook</span>
        </div>
      </div>
    </div>
  </div>
</section>

<div class="section-divider"></div>

<!-- PROJECTS -->
<section id="projects">
  <div class="section-wrap">
    <div class="section-header">
      <div class="section-eyebrow reveal">Spells Cast</div>
      <h2 class="section-title reveal">Projects</h2>
    </div>
    <div class="projects-grid">
      <div class="project-card reveal">
        <div class="project-num">01</div>
        <div class="project-icon">📸</div>
        <h3 class="project-title">Instagram Performance Analyzer</h3>
        <p class="project-desc">A Python-based tool to analyze Instagram post metrics and evaluate engagement performance. Applied data visualization techniques to present engagement trends and performance summaries across posts.</p>
        <div class="project-tags">
          <span class="project-tag">Python</span>
          <span class="project-tag">Pandas</span>
          <span class="project-tag">Matplotlib</span>
          <span class="project-tag">Data Viz</span>
        </div>
      </div>

      <div class="project-card reveal">
        <div class="project-num">02</div>
        <div class="project-icon">📊</div>
        <h3 class="project-title">Student Marks Analyzer</h3>
        <p class="project-desc">A tool that analyzes student marks to evaluate performance and generate actionable insights. Generated statistical summaries including averages, rankings, and trend analysis using NumPy and Pandas.</p>
        <div class="project-tags">
          <span class="project-tag">Python</span>
          <span class="project-tag">NumPy</span>
          <span class="project-tag">Pandas</span>
          <span class="project-tag">Statistics</span>
        </div>
      </div>

      <div class="project-card reveal">
        <div class="project-num">03</div>
        <div class="project-icon">🧠</div>
        <h3 class="project-title">Product Review Analyzer</h3>
        <p class="project-desc">A tool that analyzes product reviews to determine customer sentiment and overall product feedback. Implemented NLP-based sentiment classification to categorize reviews as positive, negative, or neutral.</p>
        <div class="project-tags">
          <span class="project-tag">NLP</span>
          <span class="project-tag">Scikit-learn</span>
          <span class="project-tag">Sentiment</span>
          <span class="project-tag">Python</span>
        </div>
      </div>
    </div>
  </div>
</section>

<div class="section-divider"></div>

<!-- RESEARCH -->
<section id="research">
  <div class="section-wrap">
    <div class="section-header">
      <div class="section-eyebrow reveal">Scholarly Pursuits</div>
      <h2 class="section-title reveal">Research</h2>
    </div>
    <div class="research-grid">
      <div class="research-card reveal-left">
        <div class="research-icon">🌾</div>
        <h3 class="research-title">E-Agriculture & ICT for Sustainable Agricultural Development</h3>
        <p class="research-desc">Investigated the role of Information and Communication Technology in transforming agricultural practices through digital tools and data-driven approaches. Explored how e-agriculture platforms can empower farmers with real-time information, market access, and resource optimization.</p>
      </div>
      <div class="research-card reveal-right">
        <div class="research-icon">🏡</div>
        <h3 class="research-title">Tapping Tribal Potential – Social Business in Wasteland Regions</h3>
        <p class="research-desc">Investigated development of wasteland into productive agricultural land through sustainable and eco-friendly practices. Explored social business models that bridge economic gaps while preserving cultural heritage in rural tribal regions.</p>
      </div>
    </div>
  </div>
</section>

<div class="section-divider"></div>

<!-- EDUCATION -->
<section id="education">
  <div class="section-wrap">
    <div class="section-header">
      <div class="section-eyebrow reveal">The Learning Path</div>
      <h2 class="section-title reveal">Education</h2>
    </div>
    <div class="edu-timeline">
      <div class="edu-item reveal">
        <div class="edu-dot"></div>
        <div class="edu-year">2024 – 2028</div>
        <div class="edu-degree">B.Tech – Computer Science Engineering</div>
        <div class="edu-school">Dronacharya College of Engineering, Gurugram</div>
        <span class="edu-grade">CGPA: 7.62</span>
      </div>
      <div class="edu-item reveal">
        <div class="edu-dot"></div>
        <div class="edu-year">Class XII – CBSE</div>
        <div class="edu-degree">Senior Secondary Education</div>
        <div class="edu-school">DAV Public School, Sector 14</div>
        <span class="edu-grade">90%</span>
      </div>
      <div class="edu-item reveal">
        <div class="edu-dot"></div>
        <div class="edu-year">Class X – CBSE</div>
        <div class="edu-degree">Secondary Education</div>
        <div class="edu-school">Our Lady of Fatima Convent Sr. Sec. School</div>
        <span class="edu-grade">92%</span>
      </div>
    </div>
  </div>
</section>

<div class="section-divider"></div>

<!-- ACHIEVEMENTS -->
<section id="achievements">
  <div class="section-wrap">
    <div class="section-header">
      <div class="section-eyebrow reveal">Honours & Accolades</div>
      <h2 class="section-title reveal">Achievements</h2>
    </div>
    <div class="ach-wrap">
      <div class="ach-card reveal">
        <span class="ach-medal">🏅</span>
        <h3 class="ach-title">NSS Volunteer – RDC Parade Representative</h3>
        <p class="ach-desc">Honoured to represent as an NSS Volunteer in the Republic Day Camp (RDC) Parade at Kartavya Path, New Delhi — a testament to discipline, national service, and leadership excellence.</p>
      </div>
    </div>
  </div>
</section>

<div class="section-divider"></div>

<!-- CONTACT -->
<section id="contact">
  <div class="section-wrap">
    <div class="section-header">
      <div class="section-eyebrow reveal">Owl Post</div>
      <h2 class="section-title reveal">Contact Me</h2>
    </div>
    <div class="contact-wrap">
      <div class="contact-info reveal-left">
        <h3>Let's Create Magic Together</h3>
        <p>Whether you have a project in mind, a question about my work, or just want to connect — I'd love to hear from you. Send an owl or reach out through any of these portals.</p>
        <div class="contact-links">
          <a href="mailto:garimaa410@gmail.com" class="contact-link">
            <span class="contact-link-icon">✉️</span>
            <div class="contact-link-text">
              <div class="contact-link-label">Email</div>
              <div class="contact-link-val">garimaa410@gmail.com</div>
            </div>
          </a>
          <a href="https://linkedin.com/in/garima-ahuja-a4102006" target="_blank" class="contact-link">
            <span class="contact-link-icon">💼</span>
            <div class="contact-link-text">
              <div class="contact-link-label">LinkedIn</div>
              <div class="contact-link-val">garima-ahuja-a4102006</div>
            </div>
          </a>
          <a href="https://github.com/Garimaahuja04" target="_blank" class="contact-link">
            <span class="contact-link-icon">🐙</span>
            <div class="contact-link-text">
              <div class="contact-link-label">GitHub</div>
              <div class="contact-link-val">Garimaahuja04</div>
            </div>
          </a>
        </div>
      </div>
      <div class="contact-form reveal-right">
        <div class="form-group">
          <label>Your Name</label>
          <input type="text" placeholder="Enter your name">
        </div>
        <div class="form-group">
          <label>Email Address</label>
          <input type="email" placeholder="your@email.com">
        </div>
        <div class="form-group">
          <label>Message</label>
          <textarea placeholder="Your message here..."></textarea>
        </div>
        <button class="btn-primary" style="width:100%; text-align:center; display:block;" onclick="alert('Message sent! ✨')">
          <span>Send Message ✦</span>
        </button>
      </div>
    </div>
  </div>
</section>

<footer>
  <p class="footer-text">Crafted with <span>✦</span> by Garima Ahuja · 2024 <span>·</span> Gurugram, India</p>
</footer>

<script>
// ── Stars ──
(function(){
  const c = document.getElementById('starsContainer');
  for(let i=0;i<180;i++){
    const s = document.createElement('div');
    s.className='star';
    const size = Math.random()*2.5+0.5;
    s.style.cssText=`
      width:${size}px;height:${size}px;
      top:${Math.random()*100}%;left:${Math.random()*100}%;
      --dur:${2+Math.random()*4}s;
      --delay:${Math.random()*4}s;
    `;
    c.appendChild(s);
  }
})();

// ── Particles ──
(function(){
  const c = document.getElementById('particlesContainer');
  const colors = ['rgba(201,168,76,0.6)','rgba(91,45,142,0.6)','rgba(200,207,232,0.4)','rgba(255,255,255,0.5)'];
  for(let i=0;i<20;i++){
    const p = document.createElement('div');
    p.className='particle';
    const size = Math.random()*4+2;
    p.style.cssText=`
      width:${size}px;height:${size}px;
      left:${Math.random()*100}%;
      background:${colors[Math.floor(Math.random()*colors.length)]};
      animation-duration:${8+Math.random()*12}s;
      animation-delay:${Math.random()*10}s;
      --drift:${(Math.random()-0.5)*100}px;
    `;
    c.appendChild(p);
  }
})();

// ── Custom Cursor ──
const cursor = document.getElementById('cursor');
const trail  = document.getElementById('cursorTrail');
let mx=0,my=0,tx=0,ty=0;
document.addEventListener('mousemove',e=>{
  mx=e.clientX; my=e.clientY;
  cursor.style.left=mx+'px'; cursor.style.top=my+'px';
});
setInterval(()=>{
  tx+=(mx-tx)*0.12; ty+=(my-ty)*0.12;
  trail.style.left=tx+'px'; trail.style.top=ty+'px';
},16);

// Sparkle on click
document.addEventListener('click',e=>{
  for(let i=0;i<6;i++){
    const sp=document.createElement('div');
    sp.className='sparkle';
    sp.style.left=(e.clientX-3+Math.random()*30-15)+'px';
    sp.style.top=(e.clientY-3+Math.random()*30-15)+'px';
    document.body.appendChild(sp);
    setTimeout(()=>sp.remove(),700);
  }
});

// ── Navbar ──
const navbar = document.getElementById('navbar');
const hamburger = document.getElementById('hamburger');
const navLinks = document.getElementById('navLinks');

window.addEventListener('scroll',()=>{
  navbar.classList.toggle('scrolled',window.scrollY>50);
  updateActiveNav();
});

hamburger.addEventListener('click',()=>{
  hamburger.classList.toggle('open');
  navLinks.classList.toggle('open');
});

navLinks.querySelectorAll('a').forEach(a=>a.addEventListener('click',()=>{
  hamburger.classList.remove('open');
  navLinks.classList.remove('open');
}));

function updateActiveNav(){
  const sections = ['hero','about','skills','projects','research','education','contact'];
  const links = navLinks.querySelectorAll('a');
  let current='';
  sections.forEach(id=>{
    const sec = document.getElementById(id);
    if(sec && window.scrollY >= sec.offsetTop-150) current=id;
  });
  links.forEach(a=>{
    a.classList.remove('active');
    if(a.getAttribute('href')==='#'+current) a.classList.add('active');
  });
}

// ── Reveal on Scroll ──
const revealEls = document.querySelectorAll('.reveal,.reveal-left,.reveal-right');
const observer = new IntersectionObserver((entries)=>{
  entries.forEach(e=>{
    if(e.isIntersecting){
      e.target.classList.add('visible');
      // Animate skill bars
      e.target.querySelectorAll('.skill-bar-fill').forEach(bar=>{
        setTimeout(()=>{bar.style.width=bar.dataset.width+'%';},100);
      });
      observer.unobserve(e.target);
    }
  });
},{threshold:0.1,rootMargin:'0px 0px -60px 0px'});

revealEls.forEach(el=>observer.observe(el));

// Stagger reveals
const groups = document.querySelectorAll('.skills-grid, .projects-grid, .research-grid, .contact-wrap');
groups.forEach(group=>{
  group.querySelectorAll('.reveal,.reveal-left,.reveal-right').forEach((el,i)=>{
    el.style.transitionDelay=`${i*0.12}s`;
  });
});
</script>
</body>
</html>
