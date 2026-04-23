<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Narrative-Driven UX Wireframing — Favour Boluwade</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400;1,700&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet" />
<style>
  :root {
    --berry:    #6D2E46;
    --rose:     #A26769;
    --cream:    #F9F4EF;
    --warmGray: #E8DDD5;
    --charcoal: #2A1F24;
    --sand:     #D9C4B0;
    --accent:   #C9714F;
    --white:    #FFFFFF;
    --textDark: #1E1218;
    --textMid:  #5C4351;
    --textLight:#9B7B8A;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--cream);
    color: var(--textDark);
    overflow-x: hidden;
  }

  /* ── NAV ── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 1rem 3rem;
    background: rgba(42,31,36,0.94);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid rgba(217,196,176,0.15);
  }
  .nav-brand {
    font-family: 'Playfair Display', serif;
    font-size: 1.05rem; font-weight: 700;
    color: var(--cream); letter-spacing: 0.02em;
  }
  .nav-brand span { color: var(--accent); }
  .nav-links { display: flex; gap: 2rem; list-style: none; }
  .nav-links a {
    color: var(--sand); text-decoration: none;
    font-size: 0.82rem; font-weight: 500; letter-spacing: 0.06em;
    text-transform: uppercase; transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--accent); }

  /* ── HERO ── */
  #hero {
    min-height: 100vh; display: grid;
    grid-template-columns: 1fr 1fr;
    background: var(--charcoal);
    position: relative; overflow: hidden;
  }
  .hero-left {
    display: flex; flex-direction: column; justify-content: center;
    padding: 8rem 4rem 4rem 5rem;
    position: relative; z-index: 2;
  }
  .hero-eyebrow {
    font-size: 0.72rem; font-weight: 600; letter-spacing: 0.2em;
    text-transform: uppercase; color: var(--sand);
    margin-bottom: 1.5rem;
  }
  .hero-eyebrow span { color: var(--accent); }
  .hero-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2.8rem, 5vw, 4.5rem);
    font-weight: 900; line-height: 1.05;
    color: var(--white);
    margin-bottom: 2rem;
  }
  .hero-title em { color: var(--rose); font-style: italic; }
  .hero-rule {
    width: 60px; height: 3px;
    background: var(--accent); margin-bottom: 1.8rem;
  }
  .hero-sub {
    font-size: 1.05rem; font-weight: 300; line-height: 1.7;
    color: var(--warmGray); max-width: 420px;
    margin-bottom: 3rem;
  }
  .hero-meta {
    font-size: 0.82rem; color: var(--textLight);
    line-height: 1.8;
  }
  .hero-cta {
    display: inline-flex; align-items: center; gap: 0.5rem;
    margin-top: 2.5rem;
    padding: 0.85rem 2rem;
    background: var(--accent); color: var(--white);
    text-decoration: none; font-size: 0.85rem; font-weight: 600;
    letter-spacing: 0.06em; text-transform: uppercase;
    transition: background 0.2s, transform 0.2s;
    border: none; cursor: pointer;
  }
  .hero-cta:hover { background: var(--berry); transform: translateY(-2px); }

  .hero-right {
    display: flex; align-items: center; justify-content: center;
    position: relative; overflow: hidden;
    background: var(--berry);
  }
  .hero-wordcloud {
    position: relative; width: 100%; height: 100%;
    display: flex; align-items: center; justify-content: center;
  }
  .wc-word {
    position: absolute;
    font-family: 'Playfair Display', serif;
    font-weight: 900; line-height: 1;
    opacity: 0;
    animation: fadeUp 0.8s ease forwards;
  }
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  .circle-deco {
    position: absolute; border-radius: 50%;
    background: rgba(162,103,105,0.25);
    animation: pulse 8s ease-in-out infinite;
  }
  @keyframes pulse {
    0%,100% { transform: scale(1); opacity: 0.25; }
    50%      { transform: scale(1.08); opacity: 0.4; }
  }

  /* ── SECTION SHELL ── */
  section { padding: 6rem 0; }
  .container { max-width: 1100px; margin: 0 auto; padding: 0 2.5rem; }
  .section-label {
    font-size: 0.7rem; font-weight: 600;
    letter-spacing: 0.22em; text-transform: uppercase;
    color: var(--textLight); margin-bottom: 0.75rem;
  }
  .section-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2rem, 3.5vw, 2.8rem);
    font-weight: 700; line-height: 1.15;
    color: var(--charcoal); margin-bottom: 1rem;
  }
  .section-title em { color: var(--berry); font-style: italic; }
  .section-intro {
    font-size: 1.05rem; line-height: 1.75;
    color: var(--textMid); max-width: 640px;
    margin-bottom: 3.5rem;
  }

  /* ── ABOUT ── */
  #about { background: var(--white); }
  .about-grid {
    display: grid; grid-template-columns: 1fr 1fr;
    gap: 5rem; align-items: center;
  }
  .about-block-label {
    font-size: 0.7rem; letter-spacing: 0.15em;
    text-transform: uppercase; color: var(--accent);
    font-weight: 600; margin-bottom: 0.5rem;
  }
  .about-argument {
    font-family: 'Playfair Display', serif;
    font-size: 1.25rem; line-height: 1.6;
    color: var(--berry); font-style: italic;
    border-left: 3px solid var(--accent);
    padding-left: 1.5rem; margin: 2rem 0;
  }
  .about-body { font-size: 0.95rem; line-height: 1.8; color: var(--textMid); }

  .roles-list { display: flex; flex-direction: column; gap: 1.5rem; }
  .role-card {
    display: grid; grid-template-columns: 48px 1fr;
    gap: 1rem; align-items: start;
    padding: 1.4rem 1.6rem;
    background: var(--cream);
    border-left: 3px solid var(--berry);
    transition: transform 0.2s, box-shadow 0.2s;
  }
  .role-card:hover { transform: translateX(4px); box-shadow: 4px 0 16px rgba(109,46,70,0.08); }
  .role-icon {
    width: 48px; height: 48px; border-radius: 50%;
    background: var(--berry);
    display: flex; align-items: center; justify-content: center;
    font-size: 1.3rem; flex-shrink: 0;
  }
  .role-card h3 {
    font-size: 0.95rem; font-weight: 600; color: var(--berry);
    margin-bottom: 0.3rem;
  }
  .role-card p { font-size: 0.88rem; color: var(--textMid); line-height: 1.6; }

  /* ── FRAMEWORK ── */
  #framework { background: var(--charcoal); }
  #framework .section-label { color: var(--sand); }
  #framework .section-title { color: var(--white); }
  #framework .section-title em { color: var(--rose); }
  #framework .section-intro { color: var(--warmGray); }

  .scholar-grid {
    display: grid; grid-template-columns: 1fr 1fr;
    gap: 1.5rem;
  }
  .scholar-card {
    background: rgba(255,255,255,0.04);
    border: 1px solid rgba(217,196,176,0.12);
    padding: 2rem;
    position: relative; overflow: hidden;
    transition: background 0.25s, transform 0.25s;
  }
  .scholar-card::before {
    content: ''; position: absolute; top: 0; left: 0;
    width: 100%; height: 3px;
  }
  .scholar-card:nth-child(1)::before { background: var(--berry); }
  .scholar-card:nth-child(2)::before { background: var(--rose); }
  .scholar-card:nth-child(3)::before { background: var(--accent); }
  .scholar-card:nth-child(4)::before { background: var(--sand); }
  .scholar-card:hover { background: rgba(255,255,255,0.08); transform: translateY(-3px); }
  .scholar-card h3 {
    font-family: 'Playfair Display', serif;
    font-size: 1.05rem; color: var(--white); margin-bottom: 0.3rem;
  }
  .scholar-work {
    font-size: 0.82rem; font-style: italic;
    color: var(--textLight); margin-bottom: 1rem;
  }
  .scholar-insight {
    font-size: 0.92rem; line-height: 1.65; color: var(--warmGray);
  }

  /* ── JOURNEY ── */
  #journey { background: var(--cream); }
  .journey-stages {
    display: grid; grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem;
  }
  .stage-card {
    background: var(--white);
    padding: 2.5rem 2rem;
    position: relative; overflow: hidden;
    box-shadow: 0 4px 24px rgba(42,31,36,0.07);
    transition: transform 0.25s, box-shadow 0.25s;
  }
  .stage-card:hover { transform: translateY(-6px); box-shadow: 0 12px 40px rgba(42,31,36,0.12); }
  .stage-num {
    width: 52px; height: 52px; border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-family: 'Playfair Display', serif;
    font-size: 1.3rem; font-weight: 700; color: var(--white);
    margin-bottom: 1.5rem;
  }
  .stage-card:nth-child(1) .stage-num { background: var(--berry); }
  .stage-card:nth-child(2) .stage-num { background: var(--rose); }
  .stage-card:nth-child(3) .stage-num { background: var(--accent); }
  .stage-card h3 {
    font-family: 'Playfair Display', serif;
    font-size: 1.4rem; font-weight: 700;
    color: var(--charcoal); margin-bottom: 0.4rem;
  }
  .stage-page {
    font-size: 0.75rem; font-weight: 600;
    letter-spacing: 0.12em; text-transform: uppercase;
    margin-bottom: 1rem;
  }
  .stage-card:nth-child(1) .stage-page { color: var(--berry); }
  .stage-card:nth-child(2) .stage-page { color: var(--rose); }
  .stage-card:nth-child(3) .stage-page { color: var(--accent); }
  .stage-rule { width: 40px; height: 2px; margin-bottom: 1rem; }
  .stage-card:nth-child(1) .stage-rule { background: var(--berry); }
  .stage-card:nth-child(2) .stage-rule { background: var(--rose); }
  .stage-card:nth-child(3) .stage-rule { background: var(--accent); }
  .stage-desc { font-size: 0.92rem; line-height: 1.7; color: var(--textMid); }

  /* ── VISUAL DESIGN ── */
  #visual { background: var(--white); }
  .visual-grid {
    display: grid; grid-template-columns: 1fr 1fr;
    gap: 4rem; align-items: start;
  }
  .design-items { display: flex; flex-direction: column; gap: 2rem; }
  .design-item { display: grid; grid-template-columns: 40px 1fr; gap: 1rem; }
  .design-icon {
    width: 40px; height: 40px; border-radius: 50%;
    background: var(--accent); opacity: 0.15;
    flex-shrink: 0; font-size: 1.1rem;
    display: flex; align-items: center; justify-content: center;
  }
  .design-item-wrap .design-icon { opacity: 1; }
  .design-item h3 { font-size: 1rem; font-weight: 600; color: var(--berry); margin-bottom: 0.35rem; }
  .design-item p  { font-size: 0.9rem; line-height: 1.65; color: var(--textMid); }

  .tools-block { display: flex; flex-direction: column; gap: 1.2rem; }
  .tool-card {
    padding: 1.5rem 1.8rem;
    border: 1px solid var(--warmGray);
    border-left: 4px solid var(--berry);
    background: var(--cream);
    transition: border-color 0.2s;
  }
  .tool-card:nth-child(2) { border-left-color: var(--rose); }
  .tool-card:nth-child(3) { border-left-color: var(--accent); }
  .tool-card:hover { border-color: var(--berry); }
  .tool-name {
    font-family: 'Playfair Display', serif;
    font-size: 1.1rem; font-weight: 700;
    color: var(--berry); margin-bottom: 0.4rem;
  }
  .tool-card:nth-child(2) .tool-name { color: var(--rose); }
  .tool-card:nth-child(3) .tool-name { color: var(--accent); }
  .tool-desc { font-size: 0.88rem; line-height: 1.6; color: var(--textMid); }

  /* ── REFLECTION ── */
  #reflection { background: var(--berry); }
  #reflection .section-label { color: rgba(255,255,255,0.5); }
  #reflection .section-title { color: var(--white); }
  #reflection .section-title em { color: var(--sand); }
  #reflection .section-intro { color: rgba(255,255,255,0.7); }

  .reflect-grid {
    display: grid; grid-template-columns: 1fr 1fr;
    gap: 3rem;
  }
  .reflect-col h3 {
    font-family: 'Playfair Display', serif;
    font-size: 1.3rem; color: var(--sand);
    margin-bottom: 1.5rem;
    padding-bottom: 0.75rem;
    border-bottom: 1px solid rgba(255,255,255,0.15);
  }
  .strength-item, .revision-item {
    display: flex; gap: 1rem; margin-bottom: 1.5rem;
  }
  .reflect-num {
    width: 28px; height: 28px; border-radius: 50%;
    background: rgba(255,255,255,0.12);
    display: flex; align-items: center; justify-content: center;
    font-size: 0.78rem; font-weight: 700; color: var(--white);
    flex-shrink: 0; margin-top: 2px;
  }
  .strength-item strong, .revision-item strong {
    display: block; font-size: 0.95rem; color: var(--white);
    margin-bottom: 0.3rem;
  }
  .strength-item p, .revision-item p {
    font-size: 0.88rem; line-height: 1.65;
    color: rgba(255,255,255,0.65);
  }

  /* ── WORKS CITED ── */
  #works { background: var(--cream); }
  .works-list {
    display: flex; flex-direction: column; gap: 0.8rem;
    max-width: 800px;
  }
  .cite {
    font-size: 0.9rem; line-height: 1.65;
    color: var(--textMid);
    padding-left: 2rem; text-indent: -2rem;
  }

  /* ── FOOTER ── */
  footer {
    background: var(--charcoal);
    padding: 3rem 2.5rem;
    text-align: center;
  }
  footer p {
    font-size: 0.82rem; color: var(--textLight); line-height: 1.8;
  }
  footer strong { color: var(--sand); }

  /* ── SCROLL ANIMATIONS ── */
  .reveal {
    opacity: 0; transform: translateY(30px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }
  .reveal-delay-1 { transition-delay: 0.1s; }
  .reveal-delay-2 { transition-delay: 0.2s; }
  .reveal-delay-3 { transition-delay: 0.3s; }
  .reveal-delay-4 { transition-delay: 0.4s; }

  /* ── RESPONSIVE ── */
  @media (max-width: 800px) {
    #hero { grid-template-columns: 1fr; }
    .hero-right { min-height: 280px; }
    .hero-left { padding: 7rem 2rem 3rem; }
    .about-grid, .reflect-grid, .visual-grid,
    .scholar-grid, .journey-stages { grid-template-columns: 1fr; }
    nav { padding: 1rem 1.5rem; }
    .nav-links { gap: 1rem; }
    .container { padding: 0 1.5rem; }
    section { padding: 4rem 0; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-brand">Favour <span>Boluwade</span></div>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#framework">Framework</a></li>
    <li><a href="#journey">Journey</a></li>
    <li><a href="#visual">Design</a></li>
    <li><a href="#reflection">Reflection</a></li>
    <li><a href="#works">Sources</a></li>
  </ul>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="hero-left">
    <p class="hero-eyebrow"><span>ENC 6931</span> · Digital Portfolio · April 2026</p>
    <h1 class="hero-title">Narrative-<br/>Driven <em>UX</em><br/>Wireframing</h1>
    <div class="hero-rule"></div>
    <p class="hero-sub">How brand discourse, tone, and narrative structure shape interface design — applied to Heart it out Media.</p>
    <div class="hero-meta">
      Favour Boluwade &nbsp;·&nbsp; Dr. Sara Raffel &nbsp;·&nbsp; April 2026
    </div>
    <a href="#about" class="hero-cta">Explore the Project ↓</a>
  </div>
  <div class="hero-right">
    <div class="hero-wordcloud">
      <div class="circle-deco" style="width:320px;height:320px;top:-60px;right:-80px;"></div>
      <div class="circle-deco" style="width:180px;height:180px;bottom:-40px;left:20px;background:rgba(201,113,79,0.2);animation-delay:3s"></div>
      <span class="wc-word" style="font-size:3.2rem;color:#F9F4EF;top:18%;left:8%;animation-delay:0.3s">Narrative</span>
      <span class="wc-word" style="font-size:2.2rem;color:#A26769;top:35%;right:5%;animation-delay:0.6s">Design</span>
      <span class="wc-word" style="font-size:4.5rem;color:#C9714F;top:46%;left:15%;animation-delay:0.9s">UX</span>
      <span class="wc-word" style="font-size:1.5rem;color:#9B7B8A;top:30%;left:52%;animation-delay:1.2s">Rhetoric</span>
      <span class="wc-word" style="font-size:2.5rem;color:#E8DDD5;top:64%;left:5%;animation-delay:1.5s">Story</span>
      <span class="wc-word" style="font-size:1.8rem;color:#A26769;bottom:14%;right:6%;animation-delay:1.8s">Brand</span>
      <span class="wc-word" style="font-size:1.3rem;color:#5C4351;bottom:6%;left:30%;animation-delay:2.1s">Journey</span>
    </div>
  </div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="container">
    <p class="section-label reveal">Project Overview</p>
    <h2 class="section-title reveal">What is this <em>project?</em></h2>
    <div class="about-grid">
      <div>
        <p class="about-body reveal">This project explores how narrative and discourse function as design strategies within UX wireframing. It focuses on designing a wireframe for <strong>Heart it out Media (HOME)</strong>, a boutique media brand centered on creative expression, storytelling, and digital engagement for small businesses and individuals.</p>
        <blockquote class="about-argument reveal">
          "The wireframe for HOME succeeds as a technical communication project because it treats interface design as narrative architecture."
        </blockquote>
        <p class="about-body reveal">Rather than treating interface design as just a tool, the project creates a user journey in which users move through stages of <em>discovery</em>, <em>connection</em>, and <em>expression</em> — grounded in scholarly frameworks from Quesenbery &amp; Brooks, Norman, Miller, and Mirel.</p>
      </div>
      <div class="roles-list">
        <div class="role-card reveal reveal-delay-1">
          <div class="role-icon">🗺</div>
          <div>
            <h3>Narrative supports design</h3>
            <p>User personas and journey mapping shape every design decision from the outset.</p>
          </div>
        </div>
        <div class="role-card reveal reveal-delay-2">
          <div class="role-icon">⬛</div>
          <div>
            <h3>Design facilitates narrative</h3>
            <p>The interface structure guides users along a purposeful story arc — not just a task flow.</p>
          </div>
        </div>
        <div class="role-card reveal reveal-delay-3">
          <div class="role-icon">💬</div>
          <div>
            <h3>Design delivers narrative</h3>
            <p>Visual elements directly communicate the brand's identity, values, and voice.</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- THEORETICAL FRAMEWORK -->
<section id="framework">
  <div class="container">
    <p class="section-label reveal">Scholarly Foundations</p>
    <h2 class="section-title reveal">The <em>Theoretical</em> Framework</h2>
    <p class="section-intro reveal">Every design decision in this project is grounded in a body of scholarship that positions technical communication as both functional and meaningful.</p>
    <div class="scholar-grid">
      <div class="scholar-card reveal reveal-delay-1">
        <h3>Quesenbery &amp; Brooks</h3>
        <p class="scholar-work">Storytelling for User Experience (2010)</p>
        <p class="scholar-insight">Three roles of narrative in design: narrative can support the design process, design can facilitate a narrative, and design can deliver a narrative.</p>
      </div>
      <div class="scholar-card reveal reveal-delay-2">
        <h3>Don Norman</h3>
        <p class="scholar-work">The Design of Everyday Things (2013)</p>
        <p class="scholar-insight">Reflective design produces meaning and identity beyond pure usability — design shapes how people understand themselves in relation to objects and systems.</p>
      </div>
      <div class="scholar-card reveal reveal-delay-3">
        <h3>Carolyn Miller</h3>
        <p class="scholar-work">"Genre as Social Action" (1984)</p>
        <p class="scholar-insight">Rhetorical genres are not just formal categories but sites of social action, requiring sensitivity to context, audience, and communicative purpose.</p>
      </div>
      <div class="scholar-card reveal reveal-delay-4">
        <h3>Barbara Mirel</h3>
        <p class="scholar-work">Interaction Design for Complex Problem Solving (2004)</p>
        <p class="scholar-insight">Meaningful interface design must account for the full range of user agency — not just task completion, but participation and voice.</p>
      </div>
    </div>
  </div>
</section>

<!-- USER JOURNEY -->
<section id="journey">
  <div class="container">
    <p class="section-label reveal">Wireframe Architecture</p>
    <h2 class="section-title reveal">The Three-Part <em>User Journey</em></h2>
    <p class="section-intro reveal">The wireframe structures users through a guided narrative arc, each section corresponding to a stage of meaningful engagement with the brand.</p>
    <div class="journey-stages">
      <div class="stage-card reveal reveal-delay-1">
        <div class="stage-num">01</div>
        <h3>Discovery</h3>
        <p class="stage-page">Homepage</p>
        <div class="stage-rule"></div>
        <p class="stage-desc">A prominent hero section with expressive typography and a bold visual banner signals the brand's creative identity before users read a single word of body text. Visual entry points (Kostelnick &amp; Roberts) draw users in before directing them forward.</p>
      </div>
      <div class="stage-card reveal reveal-delay-2">
        <div class="stage-num">02</div>
        <h3>Connection</h3>
        <p class="stage-page">Content Exploration</p>
        <div class="stage-rule"></div>
        <p class="stage-desc">A card-based layout with image previews and short narrative hooks guides users toward deeper engagement through progressive disclosure — surfacing just enough information to invite the next interaction without cognitive overload.</p>
      </div>
      <div class="stage-card reveal reveal-delay-3">
        <div class="stage-num">03</div>
        <h3>Expression</h3>
        <p class="stage-page">Submission Page</p>
        <div class="stage-rule"></div>
        <p class="stage-desc">Users become co-authors of the brand story. The submission page is designed as a rhetorical invitation — not just a contact form, but a participation framework that extends HOME's storytelling mission beyond passive consumption (Mirel, 2004).</p>
      </div>
    </div>
  </div>
</section>

<!-- VISUAL DESIGN -->
<section id="visual">
  <div class="container">
    <p class="section-label reveal">Visual Design Choices</p>
    <h2 class="section-title reveal">Design Decisions That <em>Tell the Story</em></h2>
    <div class="visual-grid">
      <div class="design-items">
        <div class="design-item reveal reveal-delay-1">
          <div class="design-icon" style="background:var(--berry);opacity:1;color:white;font-size:1rem;">⬛</div>
          <div>
            <h3>Visual Hierarchy</h3>
            <p>Hero sections create visual entry points that readers scan before committing to linear reading (Kostelnick &amp; Roberts). The homepage anchors users in the brand's narrative before inviting exploration.</p>
          </div>
        </div>
        <div class="design-item reveal reveal-delay-2">
          <div class="design-icon" style="background:var(--rose);opacity:1;color:white;font-size:1rem;">🎨</div>
          <div>
            <h3>Color &amp; Atmosphere</h3>
            <p>Warm earth tones offset by vibrant accent colors evoke creativity, warmth, and energy — all consistent with HOME's brand voice. White space is deployed deliberately to prevent cognitive overload.</p>
          </div>
        </div>
        <div class="design-item reveal reveal-delay-3">
          <div class="design-icon" style="background:var(--accent);opacity:1;color:white;font-size:1rem;">💡</div>
          <div>
            <h3>Progressive Disclosure</h3>
            <p>The content exploration page surfaces just enough information through each card to invite the next interaction — grounded in the principle that good interfaces never overwhelm, only invite.</p>
          </div>
        </div>
      </div>

      <div>
        <div class="about-block-label reveal" style="color:var(--textLight);font-size:0.7rem;letter-spacing:0.15em;text-transform:uppercase;font-weight:600;margin-bottom:1rem;">Tools Used</div>
        <div class="tools-block">
          <div class="tool-card reveal reveal-delay-1">
            <div class="tool-name">Figma</div>
            <p class="tool-desc">Information architecture, component design, user flows, and interactive prototyping. Primary structural tool for the wireframe.</p>
          </div>
          <div class="tool-card reveal reveal-delay-2">
            <div class="tool-name">Canva</div>
            <p class="tool-desc">Visual storytelling and brand-consistent graphic design. Supports the expressive layer of the interface where narrative voice lives.</p>
          </div>
          <div class="tool-card reveal reveal-delay-3">
            <div class="tool-name">Generative AI</div>
            <p class="tool-desc">UI/UX concept refinement and visual ideation, helping to iterate quickly on layout and visual direction early in the process.</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- REFLECTION -->
<section id="reflection">
  <div class="container">
    <p class="section-label reveal">Reflective Analysis</p>
    <h2 class="section-title reveal">Strengths &amp; <em>What I'd Change</em></h2>
    <p class="section-intro reveal">Reflection is central to iterative design practice. These are the project's major strengths — and what a second iteration would look like.</p>
    <div class="reflect-grid">
      <div class="reflect-col">
        <h3 class="reveal">Project Strengths</h3>
        <div class="strength-item reveal reveal-delay-1">
          <div class="reflect-num">1</div>
          <div>
            <strong>Theoretical Coherence</strong>
            <p>Every design decision traces back to a scholarly source. The project functions as both a design artifact and a rhetorical argument grounded in technical communication theory.</p>
          </div>
        </div>
        <div class="strength-item reveal reveal-delay-2">
          <div class="reflect-num">2</div>
          <div>
            <strong>Audience-Centered Design</strong>
            <p>Working with a real brand and its real community forced context-specific choices over generic UX conventions — the hallmark of effective technical communication.</p>
          </div>
        </div>
        <div class="strength-item reveal reveal-delay-3">
          <div class="reflect-num">3</div>
          <div>
            <strong>Usability + Narrative Integration</strong>
            <p>The wireframe treats functional clarity and experiential meaning as complementary — not competing — frameworks for interface design.</p>
          </div>
        </div>
      </div>
      <div class="reflect-col">
        <h3 class="reveal">If I Started Over</h3>
        <div class="revision-item reveal reveal-delay-1">
          <div class="reflect-num">1</div>
          <div>
            <strong>Empirical User Research</strong>
            <p>Conduct interviews or surveys with actual HOME users before wireframing. Real stories produce more precise design decisions than theorized personas (Quesenbery &amp; Brooks).</p>
          </div>
        </div>
        <div class="revision-item reveal reveal-delay-2">
          <div class="reflect-num">2</div>
          <div>
            <strong>High-Fidelity Prototype</strong>
            <p>Build a fully clickable Figma prototype so the narrative journey can be experienced directly — not just described in text.</p>
          </div>
        </div>
        <div class="revision-item reveal reveal-delay-3">
          <div class="reflect-num">3</div>
          <div>
            <strong>Genuine Co-Design</strong>
            <p>Involve HOME's actual stakeholders in defining narrative goals and reviewing iterations. Technical communication is always a relational practice.</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- WORKS CITED -->
<section id="works">
  <div class="container">
    <p class="section-label reveal">MLA Format</p>
    <h2 class="section-title reveal"><em>Works Cited</em></h2>
    <div class="works-list">
      <p class="cite reveal">Kostelnick, Charles, and David Roberts. <em>Designing Visual Language: Strategies for Professional Communicators.</em> Longman, 1998.</p>
      <p class="cite reveal">McCloud, Scott. <em>Understanding Comics: The Invisible Art.</em> HarperPerennial, 1994.</p>
      <p class="cite reveal">Miller, Carolyn R. "Genre as Social Action." <em>Quarterly Journal of Speech,</em> vol. 70, no. 2, 1984, pp. 151–167.</p>
      <p class="cite reveal">Mirel, Barbara. <em>Interaction Design for Complex Problem Solving: Developing Useful and Usable Software.</em> Morgan Kaufmann, 2004.</p>
      <p class="cite reveal">Norman, Don. <em>The Design of Everyday Things.</em> Revised and expanded ed., Basic Books, 2013.</p>
      <p class="cite reveal">Quesenbery, Whitney, and Kevin Brooks. <em>Storytelling for User Experience: Crafting Stories for Better Design.</em> Rosenfeld Media, 2010.</p>
      <p class="cite reveal">Schriver, Karen A. <em>Dynamics in Document Design: Creating Texts for Readers.</em> Wiley, 1997.</p>
      <p class="cite reveal">Williams, Joseph M., and Joseph Bizup. <em>Style: Lessons in Clarity and Grace.</em> 12th ed., Pearson, 2017.</p>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <p><strong>Favour Boluwade</strong> &nbsp;·&nbsp; Narrative-Driven UX Wireframing &nbsp;·&nbsp; ENC 6931</p>
  <p style="margin-top:0.5rem;">Dr. Sara Raffel &nbsp;·&nbsp; April 2026 &nbsp;·&nbsp; University of Central Florida</p>
</footer>

<script>
  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) { e.target.classList.add('visible'); }
    });
  }, { threshold: 0.12 });
  reveals.forEach(r => observer.observe(r));
</script>
</body>
</html>
