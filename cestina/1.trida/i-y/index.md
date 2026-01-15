---
layout: default
title: Čeština – 1. třída – Vybírání i/y
---

<div class="layout-wrapper">
  <!-- Tvá jediná horní lišta -->
  <header class="top-bar">
    <div class="container">
      <a href="/" class="logo">Procvičovač</a>
      
      <div class="right-controls">
        <button id="mode-toggle" class="mode-btn" title="Přepnout světlý / tmavý režim">🌞</button>
        <a href="#" class="profile-btn">Přihlásit se / Profil</a>
      </div>
    </div>
  </header>

  <!-- Hlavní obsah -->
  <div class="content-area">
    <main class="main-content">
      <h1>Vybírání i/y</h1>
      <p>Vyber si konkrétní cvičení, které chceš procvičit:</p>

      <div class="exercise-grid">
        <a href="/cestina/1.trida/i-y/cviceni-1/" class="exercise-card">
          <h3>Cvičení 1</h3>
          <p>Základní slova s i/y</p>
        </a>

        <a href="/cestina/1.trida/i-y/cviceni-2/" class="exercise-card">
          <h3>Cvičení 2</h3>
          <p>Delší věty a texty</p>
        </a>

        <a href="/cestina/1.trida/i-y/cviceni-3/" class="exercise-card">
          <h3>Cvičení 3</h3>
          <p>Smíšené úlohy s chybami</p>
        </a>

        <!-- Přidej další cvičení zde -->
      </div>
    </main>
  </div>
</div>

<style>
  /* === SKRYJE DEFAULTNÍ MINIMA HEADERY === */
  .site-header,
  .header,
  .post-header,
  .page-header,
  header[role="banner"],
  #site-header,
  nav[role="navigation"],
  .banner,
  .masthead,
  .site-title,
  .header-inner,
  .masthead-inner {
    display: none !important;
  }

  .top-bar {
    display: flex !important;
    position: fixed !important;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 9999;
    box-shadow: 0 2px 10px rgba(0,0,0,0.15);
  }

  .content-area,
  main,
  .main-content {
    margin-top: 75px !important;
  }

  /* Tvé původní styly + nové pro grid cvičení */
  :root {
    --bg: #f8f9fa;
    --text: #1f2937;
    --header-bg: #e5e7eb;
    --sidebar-bg: #f1f5f9;
    --sidebar-hover: #e2e8f0;
    --accent: #64748b;
  }

  body.dark {
    --bg: #0f172a;
    --text: #e2e8f0;
    --header-bg: #1e293b;
    --sidebar-bg: #1e293b;
    --sidebar-hover: #334155;
    --accent: #94a3b8;
  }

  body {
    background: var(--bg);
    color: var(--text);
    margin: 0;
    font-family: system-ui, -apple-system, sans-serif;
  }

  .top-bar {
    background: var(--header-bg);
    padding: 1rem 0;
  }

  .container {
    max-width: 1600px;
    margin: 0 auto;
    padding: 0 2rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .logo {
    font-size: 1.9rem;
    font-weight: bold;
    color: var(--text);
    text-decoration: none;
  }

  .right-controls {
    display: flex;
    align-items: center;
    gap: 1.5rem;
  }

  .mode-btn {
    background: none;
    border: none;
    font-size: 1.7rem;
    cursor: pointer;
    color: var(--text);
  }

  .profile-btn {
    background: var(--accent);
    color: white;
    padding: 0.55rem 1.1rem;
    border-radius: 6px;
    text-decoration: none;
    font-size: 0.95rem;
  }

  .main-content {
    flex: 1;
    padding: 4rem 3rem;
    max-width: 1200px;
    margin: 0 auto;
    width: 100%;
  }

  h1 { font-size: 2.8rem; margin-bottom: 1.5rem; }
  p { font-size: 1.15rem; line-height: 1.6; max-width: 800px; }

  .exercise-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 2rem;
    margin-top: 3rem;
  }

  .exercise-card {
    background: var(--sidebar-bg);
    padding: 2rem;
    border-radius: 12px;
    box-shadow: 0 4px 15px rgba(0,0,0,0.08);
    text-decoration: none;
    color: var(--text);
    text-align: center;
    transition: all 0.3s;
  }

  .exercise-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 20px rgba(0,0,0,0.15);
  }

  .exercise-card h3 {
    margin: 0 0 1rem;
    font-size: 1.4rem;
  }

  .exercise-card p {
    margin: 0;
    opacity: 0.8;
  }

  @media (max-width: 992px) {
    .main-content { padding: 2.5rem 1.5rem; }
  }
</style>

<script>
  // Dark/light mód
  const toggle = document.getElementById('mode-toggle');
  if (localStorage.getItem('mode') === 'dark' ||
      (!localStorage.getItem('mode') && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
    document.body.classList.add('dark');
    toggle.textContent = '🌙';
  } else {
    toggle.textContent = '🌞';
  }

  toggle.addEventListener('click', () => {
    document.body.classList.toggle('dark');
    toggle.textContent = document.body.classList.contains('dark') ? '🌙' : '🌞';
    localStorage.setItem('mode', document.body.classList.contains('dark') ? 'dark' : 'light');
  });
</script>
