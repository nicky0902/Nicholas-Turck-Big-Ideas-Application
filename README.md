<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Nicholas Turck | Big Ideas 2026</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400;1,700&family=DM+Sans:opsz,wght@9..40,300;9..40,400;9..40,500&display=swap" rel="stylesheet">
  <style>
    :root {
      --cream: #faf7f2;
      --warm-white: #fff9f4;
      --ink: #1c1810;
      --ink-soft: #3d3529;
      --gold: #c8a96e;
      --gold-light: #e8d5a8;
      --rust: #c4602a;
      --sage: #7a8c6e;
      --paper: #f0ead8;
    }

    *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }
    html { scroll-behavior: smooth; }

    body {
      background: var(--cream);
      color: var(--ink);
      font-family: 'DM Sans', sans-serif;
      font-weight: 300;
      line-height: 1.8;
      overflow-x: hidden;
    }

    /* grain overlay */
    body::after {
      content: '';
      position: fixed; inset: 0;
      pointer-events: none; z-index: 9999; opacity: 0.28;
      background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='300' height='300'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='300' height='300' filter='url(%23n)' opacity='0.08'/%3E%3C/svg%3E");
    }

    /* ── NAV ── */
    header {
      position: fixed; top: 0; width: 100%; z-index: 200;
      padding: 1.3rem 6%;
      display: flex; align-items: center; justify-content: space-between;
      background: rgba(250,247,242,0.92);
      backdrop-filter: blur(18px);
      border-bottom: 1px solid rgba(200,169,110,0.18);
    }
    .logo { font-family: 'Playfair Display', serif; font-size: 1.25rem; font-weight: 700; color: var(--ink); }
    .logo span { color: var(--gold); }
    nav { display: flex; gap: 2.2rem; }
    nav a {
      font-size: 0.75rem; font-weight: 500; letter-spacing: 0.13em;
      text-transform: uppercase; color: var(--ink-soft); text-decoration: none;
      position: relative; transition: color 0.3s;
    }
    nav a::after {
      content: ''; position: absolute; bottom: -3px; left: 0;
      width: 0; height: 1px; background: var(--gold); transition: width 0.3s;
    }
    nav a:hover { color: var(--ink); }
    nav a:hover::after { width: 100%; }

    /* ── HERO ── */
    .hero {
      min-height: 100vh;
      display: grid; grid-template-columns: 1fr 1fr;
      padding: 0 6%; padding-top: 5rem;
      gap: 5rem; align-items: center;
      position: relative; overflow: hidden;
    }
    .hero::before {
      content: 'NT';
      position: absolute; right: -2%; bottom: 0;
      font-family: 'Playfair Display', serif;
      font-size: 38vw; font-weight: 900; line-height: 0.8;
      color: transparent;
      -webkit-text-stroke: 1px rgba(200,169,110,0.1);
      pointer-events: none; user-select: none;
    }
    .hero-text { position: relative; z-index: 2; }

    .eyebrow {
      display: inline-flex; align-items: center; gap: 0.8rem;
      font-size: 0.72rem; font-weight: 500;
      letter-spacing: 0.16em; text-transform: uppercase;
      color: var(--gold); margin-bottom: 1.6rem;
      opacity: 0; animation: fadeUp 0.7s 0.15s ease forwards;
    }
    .eyebrow::before { content: ''; display: block; width: 28px; height: 1px; background: var(--gold); }

    .hero h1 {
      font-family: 'Playfair Display', serif;
      font-size: clamp(3rem, 5.5vw, 5.2rem);
      font-weight: 900; line-height: 1.04; letter-spacing: -0.025em;
      color: var(--ink); margin-bottom: 1.8rem;
      opacity: 0; animation: fadeUp 0.7s 0.3s ease forwards;
    }
    .hero h1 em { font-style: italic; color: var(--rust); }

    .hero-body {
      font-size: 1.05rem; color: var(--ink-soft);
      line-height: 1.85; max-width: 460px;
      opacity: 0; animation: fadeUp 0.7s 0.45s ease forwards;
    }
    .hero-actions {
      margin-top: 2.8rem; display: flex; gap: 1.4rem; align-items: center;
      opacity: 0; animation: fadeUp 0.7s 0.6s ease forwards;
    }
    .btn-dark {
      display: inline-block; padding: 13px 32px;
      background: var(--ink); color: var(--cream);
      font-size: 0.78rem; font-weight: 500; letter-spacing: 0.1em;
      text-transform: uppercase; text-decoration: none; border-radius: 2px;
      position: relative; overflow: hidden; transition: color 0.3s;
    }
    .btn-dark::before {
      content: ''; position: absolute; inset: 0;
      background: var(--rust); transform: translateX(-101%);
      transition: transform 0.38s ease;
    }
    .btn-dark:hover::before { transform: translateX(0); }
    .btn-dark span { position: relative; z-index: 1; }
    .btn-link {
      font-size: 0.82rem; font-weight: 500; color: var(--ink-soft);
      text-decoration: none; border-bottom: 1px solid var(--gold);
      padding-bottom: 2px; transition: color 0.3s;
    }
    .btn-link:hover { color: var(--rust); }

    .hero-visual {
      position: relative; height: 72vh; min-height: 440px;
      opacity: 0; animation: fadeIn 1s 0.5s ease forwards;
    }
    .hero-img {
      width: 100%; height: 100%; object-fit: cover;
      border-radius: 3px; filter: saturate(0.82) contrast(1.06); display: block;
    }
    .hero-img-overlay {
      position: absolute; inset: 0; border-radius: 3px;
      background: linear-gradient(to bottom, transparent 55%, rgba(28,24,16,0.38));
    }
    .hero-pill {
      position: absolute; bottom: -1.4rem; left: -1.4rem;
      background: var(--cream); border: 1px solid var(--gold-light);
      padding: 1.3rem 1.7rem; border-radius: 3px;
      box-shadow: 0 8px 28px rgba(0,0,0,0.1);
    }
    .hero-pill .num { font-family: 'Playfair Display', serif; font-size: 2.4rem; font-weight: 700; color: var(--rust); line-height: 1; }
    .hero-pill .lbl { font-size: 0.7rem; font-weight: 500; letter-spacing: 0.1em; text-transform: uppercase; color: var(--ink-soft); margin-top: 0.25rem; }
    .hero-tag {
      position: absolute; top: 1.4rem; right: -0.8rem;
      background: var(--rust); color: white;
      font-size: 0.68rem; font-weight: 500; letter-spacing: 0.12em;
      text-transform: uppercase; padding: 6px 14px; border-radius: 2px;
      writing-mode: vertical-rl; transform: rotate(180deg);
    }

    /* ── SHARED ── */
    .s { padding: 110px 6%; }
    .s-inner { max-width: 1280px; margin: 0 auto; }

    .tag {
      display: inline-flex; align-items: center; gap: 0.7rem;
      font-size: 0.7rem; font-weight: 500; letter-spacing: 0.18em;
      text-transform: uppercase; color: var(--gold); margin-bottom: 1.1rem;
    }
    .tag::before { content: ''; display: block; width: 22px; height: 1px; background: var(--gold); }

    h2.title {
      font-family: 'Playfair Display', serif;
      font-size: clamp(2.2rem, 4vw, 3.6rem);
      font-weight: 900; line-height: 1.06; letter-spacing: -0.02em; color: var(--ink);
    }
    h2.title em { font-style: italic; color: var(--rust); }
    h2.title.light { color: var(--cream); }
    h2.title.light em { color: var(--gold); }

    /* ── QUALITIES ── */
    #qualities { background: var(--warm-white); }

    .qualities-grid {
      display: grid; grid-template-columns: 1fr 1fr;
      gap: 6rem; align-items: start; margin-top: 1rem;
    }
    .q-intro p {
      margin-top: 1.5rem; font-size: 1.02rem;
      color: var(--ink-soft); line-height: 1.88; max-width: 430px;
    }
    .q-cards { display: flex; flex-direction: column; gap: 1.4rem; }
    .q-card {
      background: white;
      border: 1px solid rgba(200,169,110,0.18);
      border-left: 3px solid var(--gold);
      padding: 1.9rem 2.1rem; border-radius: 0 3px 3px 0;
      transition: all 0.32s ease; position: relative; overflow: hidden;
    }
    .q-card::before {
      content: ''; position: absolute; top: 0; left: 0;
      width: 0; height: 100%;
      background: linear-gradient(to right, rgba(200,169,110,0.055), transparent);
      transition: width 0.38s ease;
    }
    .q-card:hover { transform: translateX(5px); border-left-color: var(--rust); }
    .q-card:hover::before { width: 100%; }
    .q-num { font-family: 'Playfair Display', serif; font-size: 0.7rem; font-weight: 700; color: var(--gold); letter-spacing: 0.12em; margin-bottom: 0.55rem; }
    .q-card h3 { font-family: 'Playfair Display', serif; font-size: 1.2rem; font-weight: 700; color: var(--ink); margin-bottom: 0.65rem; }
    .q-card p { font-size: 0.93rem; color: var(--ink-soft); line-height: 1.78; }

    /* ── HOBBIES ── */
    #hobbies { background: var(--paper); }

    .hobbies-top {
      display: grid; grid-template-columns: 1fr 1fr;
      gap: 4rem; align-items: end; margin-bottom: 4rem;
    }
    .hobbies-top p { font-size: 1.02rem; color: var(--ink-soft); line-height: 1.88; }

    .hobbies-grid {
      display: grid;
      grid-template-columns: 1.25fr 1fr 1fr;
      gap: 1.6rem;
    }

    .h-card {
      background: white; border-radius: 3px; overflow: hidden;
      box-shadow: 0 3px 22px rgba(28,24,16,0.08);
      transition: transform 0.38s ease, box-shadow 0.38s ease;
    }
    .h-card:hover { transform: translateY(-7px); box-shadow: 0 18px 42px rgba(28,24,16,0.15); }

    .h-img-wrap { overflow: hidden; }
    .h-img {
      width: 100%; height: 270px; object-fit: cover; display: block;
      filter: saturate(0.82) contrast(1.06);
      transition: transform 0.5s ease, filter 0.4s ease;
    }
    .h-card:hover .h-img { transform: scale(1.04); filter: saturate(1) contrast(1.06); }

    .h-chip {
      display: inline-block; margin: 1.4rem 1.7rem 0;
      padding: 4px 11px; background: var(--paper);
      border-radius: 2px; font-size: 0.68rem; font-weight: 500;
      letter-spacing: 0.13em; text-transform: uppercase; color: var(--sage);
    }
    .h-body { padding: 0.85rem 1.7rem 1.9rem; }
    .h-caption { font-size: 0.76rem; font-style: italic; color: var(--gold); margin-bottom: 0.35rem; display: block; }
    .h-body h3 { font-family: 'Playfair Display', serif; font-size: 1.22rem; font-weight: 700; color: var(--ink); margin-bottom: 0.7rem; line-height: 1.2; }
    .h-body p { font-size: 0.9rem; color: var(--ink-soft); line-height: 1.8; }

    /* ── SKILLS ── */
    #skills { background: var(--warm-white); }

    .skills-layout {
      display: grid; grid-template-columns: 1fr 2fr;
      gap: 6rem; align-items: start; margin-top: 2.5rem;
    }
    .skills-intro p { font-size: 1rem; color: var(--ink-soft); line-height: 1.88; margin-top: 1.5rem; }

    .skills-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 1.4rem; }

    .sk-card {
      background: white; border: 1px solid rgba(200,169,110,0.15);
      padding: 1.9rem; border-radius: 3px;
      transition: all 0.32s ease; position: relative; overflow: hidden;
    }
    .sk-card::after {
      content: ''; position: absolute; bottom: 0; left: 0;
      width: 100%; height: 2px;
      background: linear-gradient(to right, var(--gold), var(--rust));
      transform: scaleX(0); transform-origin: left; transition: transform 0.38s ease;
    }
    .sk-card:hover { transform: translateY(-4px); box-shadow: 0 10px 28px rgba(0,0,0,0.08); }
    .sk-card:hover::after { transform: scaleX(1); }
    .sk-icon { font-size: 1.5rem; margin-bottom: 1.1rem; display: block; }
    .sk-card h3 { font-family: 'Playfair Display', serif; font-size: 1.08rem; font-weight: 700; color: var(--ink); margin-bottom: 0.6rem; }
    .sk-card p { font-size: 0.9rem; color: var(--ink-soft); line-height: 1.78; }

    /* ── WHY BIG IDEAS ── */
    #why { background: var(--ink); }
    #why .tag { color: var(--gold); }

    .why-layout {
      display: grid; grid-template-columns: 1fr 1fr;
      gap: 5rem; margin-top: 3.5rem; align-items: start;
    }

    .why-cards { display: flex; flex-direction: column; gap: 1.3rem; }
    .w-card {
      padding: 1.7rem 2rem;
      border: 1px solid rgba(200,169,110,0.15);
      border-radius: 3px; transition: all 0.32s ease;
    }
    .w-card:hover { background: rgba(200,169,110,0.07); border-color: rgba(200,169,110,0.32); }
    .w-card h3 { font-family: 'Playfair Display', serif; font-size: 1.1rem; font-weight: 700; color: var(--gold); margin-bottom: 0.65rem; }
    .w-card p { font-size: 0.91rem; line-height: 1.8; color: rgba(250,247,242,0.68); }

    /* ── PERSONAL PHOTOS STRIP ── */
    .photos-strip {
      background: #111008;
      padding: 70px 6%;
    }
    .photos-strip-inner {
      max-width: 1280px;
      margin: 0 auto;
    }
    .photos-strip-label {
      display: inline-flex; align-items: center; gap: 0.7rem;
      font-size: 0.7rem; font-weight: 500; letter-spacing: 0.18em;
      text-transform: uppercase; color: var(--gold); margin-bottom: 2.5rem;
    }
    .photos-strip-label::before { content: ''; display: block; width: 22px; height: 1px; background: var(--gold); }

    .photos-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 1.2rem;
    }

    .p-card {
      position: relative; overflow: hidden; border-radius: 3px;
      background: #1a1710;
    }
    .p-card img {
      width: 100%; display: block;
      object-fit: cover;
      filter: saturate(0.75) brightness(0.88);
      transition: transform 0.5s ease, filter 0.4s ease;
    }
    .p-card:hover img { transform: scale(1.04); filter: saturate(1) brightness(0.95); }

    .p-card .p-caption {
      position: absolute;
      bottom: 0; left: 0; right: 0;
      padding: 2.5rem 1.6rem 1.4rem;
      background: linear-gradient(to top, rgba(15,12,6,0.85) 0%, transparent 100%);
      font-size: 0.82rem;
      font-style: italic;
      color: rgba(250,247,242,0.8);
      transition: opacity 0.3s;
    }
    .p-card .p-caption strong {
      display: block;
      font-family: 'Playfair Display', serif;
      font-size: 0.72rem;
      font-style: normal;
      font-weight: 700;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 0.25rem;
    }

    /* tall card spans 2 rows */
    .p-card.tall { grid-row: span 2; }
    .p-card.tall img { height: 100%; min-height: 500px; }
    .p-card:not(.tall) img { height: 280px; }

    /* ── FOOTER ── */
    footer {
      background: #0a0905; padding: 2.8rem 6%;
      display: flex; align-items: center; justify-content: space-between;
      border-top: 1px solid rgba(200,169,110,0.1);
    }
    .foot-logo { font-family: 'Playfair Display', serif; font-size: 1.15rem; font-weight: 700; color: var(--cream); }
    .foot-logo span { color: var(--gold); }
    .foot-info { font-size: 0.78rem; letter-spacing: 0.06em; color: rgba(250,247,242,0.3); text-align: right; line-height: 1.7; }

    /* ── ANIMATIONS ── */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(22px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    @keyframes fadeIn {
      from { opacity: 0; } to { opacity: 1; }
    }

    .reveal {
      opacity: 0; transform: translateY(30px);
      transition: opacity 0.72s ease, transform 0.72s ease;
    }
    .reveal.on { opacity: 1; transform: none; }

    .stagger > * {
      opacity: 0; transform: translateY(22px);
      transition: opacity 0.6s ease, transform 0.6s ease;
    }
    .stagger.on > *:nth-child(1) { opacity:1; transform:none; transition-delay:0.05s; }
    .stagger.on > *:nth-child(2) { opacity:1; transform:none; transition-delay:0.17s; }
    .stagger.on > *:nth-child(3) { opacity:1; transform:none; transition-delay:0.29s; }
    .stagger.on > *:nth-child(4) { opacity:1; transform:none; transition-delay:0.41s; }

    /* ── RESPONSIVE ── */
    @media (max-width: 960px) {
      .hero { grid-template-columns: 1fr; padding-top: 7rem; }
      .hero-visual { height: 52vw; min-height: 260px; }
      .hero::before { display: none; }
      .qualities-grid, .why-layout, .skills-layout, .hobbies-top { grid-template-columns: 1fr; gap: 2.5rem; }
      .hobbies-grid { grid-template-columns: 1fr; }
      .skills-grid { grid-template-columns: 1fr; }
      .photos-grid { grid-template-columns: 1fr; }
      .p-card.tall { grid-row: span 1; }
      .p-card.tall img { min-height: 300px; }
      footer { flex-direction: column; gap: 1rem; text-align: center; }
      .foot-info { text-align: center; }
    }
  </style>
</head>
<body>

  <header>
    <div class="logo">Nicholas <span>Turck</span></div>
    <nav>
      <a href="#qualities">Qualities</a>
      <a href="#hobbies">Hobbies</a>
      <a href="#skills">Skills</a>
      <a href="#why">Why Big Ideas</a>
    </nav>
  </header>

  <!-- ═══ HERO ═══ -->
  <section class="hero">
    <div class="hero-text">
      <div class="eyebrow">Big Ideas Programme · 2026 Application</div>
      <h1>Discipline.<br><em>Initiative.</em><br>Collaboration.</h1>
      <p class="hero-body">I'm Nicholas — a Grade 9 student from Cape Town who trains MMA five days a week, builds websites for real clients, and spends his evenings pushing the limits of what AI tools can do. I believe in showing up, taking ownership, and doing the work even when it's hard. These are the qualities I'm bringing to Big Ideas 2026.</p>
      <div class="hero-actions">
        <a href="#qualities" class="btn-dark"><span>Explore My Profile</span></a>
        <a href="#why" class="btn-link">Why Big Ideas fits me →</a>
      </div>
    </div>

    <div class="hero-visual">
      <!-- Nicholas in school uniform — personal photo -->
      <img class="hero-img" src="grade8.jpg" alt="Nicholas Turck">
      <div class="hero-img-overlay"></div>
      <div class="hero-pill">
        <div class="num">14</div>
        <div class="lbl">Years old · Cape Town</div>
      </div>
      <div class="hero-tag">Grade 9</div>
    </div>
  </section>

  <!-- ═══ QUALITIES ═══ -->
  <section id="qualities" class="s">
    <div class="s-inner">
      <div class="qualities-grid">
        <div class="q-intro reveal">
          <div class="tag">Who I Am</div>
          <h2 class="title">Qualities I<br>bring to the<br><em>table</em></h2>
          <p>These aren't things I chose because they sound good in an application. They're qualities I've had to actually develop — through early mornings, hard training sessions, real client deadlines, and moments where quitting would have been much easier. Every single one of them has been tested and earned over time.</p>
        </div>

        <div class="q-cards stagger">
          <div class="q-card">
            <div class="q-num">01</div>
            <h3>Proactive & Self-Starting</h3>
            <p>I've never been someone who waits around for things to happen. When I see a gap or spot an opportunity, my instinct is to go after it. Starting a web development business at 14 wasn't something anyone suggested to me — I just realised I could do it and started doing it. That bias toward action is something I carry into everything: school, training, and projects I genuinely care about.</p>
          </div>
          <div class="q-card">
            <div class="q-num">02</div>
            <h3>Resilient & Calm Under Pressure</h3>
            <p>MMA has a way of teaching you what you're actually made of. When you're completely exhausted and still expected to perform, you quickly learn whether your mindset holds up or falls apart. Mine holds up. I've got a lot of practice staying composed when things get uncomfortable — and that same calmness shows up in how I handle pressure in schoolwork, deadlines, and anything that feels genuinely high-stakes.</p>
          </div>
          <div class="q-card">
            <div class="q-num">03</div>
            <h3>Consistent, No Matter What</h3>
            <p>I think consistency is one of the most underrated qualities a person can have. Motivation comes and goes — what matters is whether you show up anyway. I've built habits around training, client communication, and studying that don't depend on how I'm feeling that day. I'm the kind of person you can count on to still be there, still doing the work, a month from now.</p>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ═══ HOBBIES ═══ -->
  <section id="hobbies" class="s">
    <div class="s-inner">
      <div class="hobbies-top reveal">
        <div>
          <div class="tag">What I Do</div>
          <h2 class="title">Hobbies &<br><em>Passions</em></h2>
        </div>
        <p>These aren't just ways I fill time. Each of these activities has genuinely shaped who I am and how I think. They've pushed me in different directions and given me real, practical skills — not just interests I list on a form to sound interesting.</p>
      </div>

      <div class="hobbies-grid stagger">

        <!-- MMA — personal team photo -->
        <div class="h-card">
          <div class="h-img-wrap">
            <img class="h-img"
              src="mma-team.jpg"
              alt="Nicholas with his MMA team at Pride Fighting Academy"
              onerror="this.src='https://images.unsplash.com/photo-1555597673-b21d5c935865?w=800&q=80&fit=crop'">
          </div>
          <span class="h-chip">Discipline · Resilience</span>
          <div class="h-body">
            <span class="h-caption">My team at Pride Fighting Academy</span>
            <h3>Mixed Martial Arts</h3>
            <p>MMA has pushed me harder than anything else in my life. It's not glamorous — it's early starts, sore muscles, and sessions where nothing clicks. But that's exactly why I keep coming back. The sport has built a kind of mental toughness in me that you genuinely can't get from a classroom. I've learned to stay calm under pressure, to trust my teammates, and to find something left in the tank when I'm convinced there's nothing there. Everything I've built on the mat I carry into real life.</p>
          </div>
        </div>

        <!-- Web Dev — baby-at-computer personal photo -->
        <div class="h-card">
          <div class="h-img-wrap">
            <img class="h-img"
              src="web-dev.jpg"
              alt="Always been good with computers"
              style="object-position: center top;">
          </div>
          <span class="h-chip">Initiative · Real-World</span>
          <div class="h-body">
            <span class="h-caption">I've always been good with computers</span>
            <h3>Web Development & Running a Small Business</h3>
            <p>At 14, I build websites for actual paying clients. That means managing expectations, hitting deadlines, explaining technical things in plain English, and standing behind my work when something goes wrong. It's taught me more about professional responsibility than anything else I've done. I also genuinely enjoy the craft — the logic of clean code, the satisfaction of solving a problem elegantly, and the moment a client sees something I built and loves it.</p>
          </div>
        </div>

        <!-- AI — Nicholas meeting Lando Norris via AI -->
        <div class="h-card">
          <div class="h-img-wrap">
            <img class="h-img"
              src="ai-lando.jpg"
              alt="Nicholas with Lando Norris"
              style="object-position: center top;">
          </div>
          <span class="h-chip">Curiosity · Innovation</span>
          <div class="h-body">
            <span class="h-caption">My attempt to meet Lando Norris using AI</span>
            <h3>Exploring Artificial Intelligence</h3>
            <p>I've been curious about AI since before it became a buzzword — and yes, I've already used it to make things happen that probably wouldn't have otherwise. I spend real time experimenting with different tools, testing their limits, and thinking critically about how they actually work. I use AI to think through complex problems, organise messy ideas, and ask better questions. I'm just as interested in what it can't do, and in what all of this means for the future.</p>
          </div>
        </div>

      </div>
    </div>
  </section>

  <!-- ═══ SKILLS ═══ -->
  <section id="skills" class="s">
    <div class="s-inner">
      <div class="skills-layout">
        <div class="skills-intro reveal">
          <div class="tag">What I Bring</div>
          <h2 class="title">Skills &<br><em>Strengths</em></h2>
          <p>None of these came from a course or a textbook. They came from doing real things — managing actual client projects, keeping up a training schedule that doesn't let you off the hook, and caring enough about my work to do it properly every single time. These are practical strengths that show up in how I work with others and how I tackle problems under pressure.</p>
        </div>

        <div class="skills-grid stagger">
          <div class="sk-card">
            <span class="sk-icon">🛠</span>
            <h3>Practical Problem Solving</h3>
            <p>I approach problems methodically and without panicking. Whether it's a broken website the night before a client deadline, a tough moment in training, or a confusing assignment — I slow down, think it through, and work toward a solution. I've learned that most problems look much worse than they actually are if you take them apart carefully and stay calm while you do it.</p>
          </div>
          <div class="sk-card">
            <span class="sk-icon">💬</span>
            <h3>Clear Communication</h3>
            <p>Working with real clients has made me far more thoughtful about how I communicate than most people my age. I've had to explain technical things simply, set expectations carefully, and make sure nothing important gets lost between two people with very different levels of knowledge. I've got good instincts for what someone actually needs — not just what they're literally asking for.</p>
          </div>
          <div class="sk-card">
            <span class="sk-icon">⏱</span>
            <h3>Time Management & Ownership</h3>
            <p>Fitting five-plus days of training a week, client work, and full-time school into the same schedule forces you to be serious about how you manage your time and energy. I've had to make real trade-offs and stay accountable when nobody's checking on me. I take ownership of my commitments — not because I have to, but because that's the kind of person I want to be.</p>
          </div>
          <div class="sk-card">
            <span class="sk-icon">🤝</span>
            <h3>Being a Reliable Team Member</h3>
            <p>In MMA and in group school projects, I've learned that a team is only as strong as its least reliable member. I actively try to fill gaps, notice when someone's struggling, and add energy to a group rather than drain it. Reliability genuinely matters to me — I don't want to be the person others have to chase up or work around. I'd rather be the one doing the carrying.</p>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ═══ WHY BIG IDEAS ═══ -->
  <section id="why" class="s">
    <div class="s-inner">
      <div class="reveal">
        <div class="tag">The Bigger Picture</div>
        <h2 class="title light">Why <em>Big Ideas</em><br>fits me</h2>
      </div>

      <div class="why-layout">
        <div class="why-cards stagger">
          <div class="w-card">
            <h3>Real-World Challenges</h3>
            <p>I do my best work when the stakes are actual. When there's a real problem on the table — something that affects real people and needs genuine thinking to solve — I become a different kind of student. I've found that meaningful work pulls out abilities in me that comfortable, low-stakes tasks simply don't reach. Big Ideas feels built around exactly that kind of challenge, and I want to be in the room where it happens.</p>
          </div>
          <div class="w-card">
            <h3>Connecting Ideas Across Fields</h3>
            <p>The thing I find most exciting about the intersection of technology, creativity, and real-world problem solving is that the connections always surprise you. I naturally look for patterns across different areas — how design thinking applies to training structure, how what I've learned about AI reshapes how I approach almost everything else. Big Ideas is built for that kind of cross-disciplinary curiosity, and it's where I naturally thrive.</p>
          </div>
          <div class="w-card">
            <h3>A Collaborative Environment</h3>
            <p>The best moments I've had — in the gym, in client work, in group school projects — all came from working alongside people who genuinely pushed each other toward something better. I love being part of a team where everyone wants the whole group to succeed. I bring honesty, energy, and real reliability to that dynamic. I'm not afraid to challenge an idea when I think it matters — and I can take the same honest pushback in return.</p>
          </div>
          <div class="w-card">
            <h3>Growing Into Someone Bigger</h3>
            <p>I'm 14 and I'm already clear on the kind of person I want to become: someone who builds meaningful things, thinks critically, works hard without being told to, and actually makes a difference. Big Ideas 2026 feels like the kind of experience that doesn't just add a line to a CV — it genuinely shapes who you are. That's what I'm looking for, and what I'm ready to give everything to.</p>
          </div>
        </div>

        <!-- Right column: stacked why cards visual filler with dark aesthetic text -->
        <div class="reveal" style="display:flex; flex-direction:column; gap:1.5rem; justify-content:center;">
          <div style="padding:2.5rem; border:1px solid rgba(200,169,110,0.2); border-radius:3px;">
            <div style="font-family:'Playfair Display',serif; font-size:3.5rem; font-weight:900; color:var(--gold); line-height:1; margin-bottom:0.5rem;">2026</div>
            <div style="font-size:0.75rem; font-weight:500; letter-spacing:0.14em; text-transform:uppercase; color:rgba(250,247,242,0.35);">Big Ideas Cohort</div>
          </div>
          <div style="padding:2.5rem; border:1px solid rgba(200,169,110,0.2); border-radius:3px; background:rgba(200,169,110,0.05);">
            <div style="font-family:'Playfair Display',serif; font-style:italic; font-size:1.3rem; color:rgba(250,247,242,0.8); line-height:1.5; margin-bottom:1rem;">"I'm excited to bring my discipline, curiosity, and genuine drive to Big Ideas — and to be part of something that actually matters."</div>
            <div style="font-size:0.72rem; font-weight:500; letter-spacing:0.12em; text-transform:uppercase; color:var(--gold);">— Nicholas Turck</div>
          </div>
          <div style="padding:2.5rem; border:1px solid rgba(200,169,110,0.2); border-radius:3px;">
            <div style="display:flex; gap:2rem;">
              <div>
                <div style="font-family:'Playfair Display',serif; font-size:2.2rem; font-weight:700; color:var(--gold); line-height:1;">5+</div>
                <div style="font-size:0.7rem; letter-spacing:0.1em; text-transform:uppercase; color:rgba(250,247,242,0.35); margin-top:0.3rem;">Days training/week</div>
              </div>
              <div style="width:1px; background:rgba(200,169,110,0.15);"></div>
              <div>
                <div style="font-family:'Playfair Display',serif; font-size:2.2rem; font-weight:700; color:var(--gold); line-height:1;">9</div>
                <div style="font-size:0.7rem; letter-spacing:0.1em; text-transform:uppercase; color:rgba(250,247,242,0.35); margin-top:0.3rem;">Grade</div>
              </div>
              <div style="width:1px; background:rgba(200,169,110,0.15);"></div>
              <div>
                <div style="font-family:'Playfair Display',serif; font-size:2.2rem; font-weight:700; color:var(--gold); line-height:1;">14</div>
                <div style="font-size:0.7rem; letter-spacing:0.1em; text-transform:uppercase; color:rgba(250,247,242,0.35); margin-top:0.3rem;">Years old</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ═══ PERSONAL PHOTOS ═══ -->
  <section class="photos-strip">
    <div class="photos-strip-inner">
      <div class="photos-strip-label reveal">A Glimpse of My Life</div>

      <div class="photos-grid reveal">

        <!-- Tall left: grandparents dinner -->
        <div class="p-card tall">
          <img src="grandparents.jpg" alt="Dinner with grandparents and cousin" style="object-position: center;">
          <div class="p-caption">
            <strong>Family</strong>
            Me with my grandparents and cousin at dinner
          </div>
        </div>

        <!-- Right column: grade 8 photo stacked -->
        <div style="display:flex; flex-direction:column; gap:1.2rem;">
          <div class="p-card">
            <img src="grade8.jpg" alt="First day of Grade 8" style="height:280px; object-fit:cover; object-position:center top;">
            <div class="p-caption">
              <strong>September 2024</strong>
              My first day in Grade 8
            </div>
          </div>

          <!-- Dark stat card -->
          <div style="background:#1a1710; border-radius:3px; padding:2rem 2.2rem; border:1px solid rgba(200,169,110,0.12); display:flex; flex-direction:column; justify-content:center; gap:0.6rem;">
            <div style="font-size:0.68rem; font-weight:500; letter-spacing:0.16em; text-transform:uppercase; color:var(--gold);">Cape Town, South Africa</div>
            <div style="font-family:'Playfair Display',serif; font-size:1.5rem; font-weight:700; color:var(--cream); line-height:1.2;">Grade 9 · Big Ideas<br>Applicant · 2026</div>
            <div style="font-size:0.85rem; color:rgba(250,247,242,0.4); margin-top:0.4rem; line-height:1.7;">MMA athlete · Web developer<br>AI explorer · Cape Town</div>
          </div>
        </div>

      </div>
    </div>
  </section>

  <!-- ═══ FOOTER ═══ -->
  <footer>
    <div class="foot-logo">Nicholas <span>Turck</span></div>
    <div class="foot-info">
      <div>Grade 9 · Cape Town, South Africa</div>
      <div>Big Ideas 2026 Application</div>
    </div>
  </footer>

  <script>
    const io = new IntersectionObserver((entries) => {
      entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('on'); });
    }, { threshold: 0.1, rootMargin: '0px 0px -50px 0px' });
    document.querySelectorAll('.reveal, .stagger').forEach(el => io.observe(el));
  </script>

</body>
</html>
