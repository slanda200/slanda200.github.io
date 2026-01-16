---
layout: default
title: Čeština – 1. třída – Vybírání i/y
---

<div class="page">
  <header class="navbar">
    <a href="/" class="logo">Procvičovač</a>
    <div class="nav-right">
      <button id="mode-toggle" class="mode-btn" title="Přepnout světlý / tmavý režim">🌞</button>
      <a href="#" class="profile-btn">Přihlásit se / Profil</a>
    </div>
  </header>

  <main class="container">
    <div class="card">
      <h1>Vybírání i/y</h1>
      <p class="instruction">Vyber si konkrétní cvičení, které chceš procvičit:</p>

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
      </div>
    </div>
  </main>
</div>

<style>
  .site-header,
  .header,
  .post-header,
  .page-header,
  header[role="banner"],
  #site-header,
  nav[role="navigation"],
  .banner,
  .masthead,
  .site-title {
    display: none !important;
  }

  :root {
    --bg: #f8fafc;
    --card: #ffffff;
    --primary: #2563eb;
    --muted: #64748b;
    --line: #e5e7eb;
    --shadow: 0 12px 28px rgba(15, 23, 42, 0.08);
  }

  body.dark {
    --bg: #0f172a;
    --card: #111827;
    --primary: #60a5fa;
    --muted: #cbd5f5;
    --line: #1f2937;
    --shadow: 0 12px 28px rgba(15, 23, 42, 0.35);
  }

  body {
    margin: 0;
    font-family: system-ui, -apple-system, BlinkMacSystemFont, sans-serif;
    background: var(--bg);
    color: #0f172a;
  }

  body.dark {
    color: #e2e8f0;
  }

  .page {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
  }

  .navbar {
    background: var(--card);
    border-bottom: 1px solid var(--line);
    padding: 0.8rem 1.5rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    position: sticky;
    top: 0;
    z-index: 10;
  }

  .logo {
    font-weight: 700;
    font-size: 1.2rem;
    color: var(--primary);
    text-decoration: none;
  }

  .nav-right {
    display: flex;
    align-items: center;
    gap: 1rem;
  }

  .profile-btn {
    text-decoration: none;
    color: var(--muted);
    font-weight: 600;
  }

  .mode-btn {
    border: none;
    background: transparent;
    font-size: 1.5rem;
    cursor: pointer;
  }

  .container {
    max-width: 1000px;
    margin: 2.5rem auto;
    padding: 0 1.5rem;
    width: 100%;
  }

  .card {
    background: var(--card);
    border-radius: 18px;
    padding: 2.5rem;
    box-shadow: var(--shadow);
  }

  h1 {
    margin-top: 0;
    font-size: 2.4rem;
  }

  .instruction {
    color: var(--muted);
    font-size: 1.1rem;
  }

  .exercise-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 1.5rem;
    margin-top: 2rem;
  }

  .exercise-card {
    background: rgba(148, 163, 184, 0.12);
    padding: 1.8rem;
    border-radius: 14px;
    text-decoration: none;
    color: inherit;
    transition: transform 0.2s ease, box-shadow 0.2s ease;
  }

  .exercise-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 10px 20px rgba(15, 23, 42, 0.12);
  }

  .exercise-card h3 {
    margin-top: 0;
    margin-bottom: 0.6rem;
  }

  .exercise-card p {
    margin: 0;
    color: var(--muted);
  }
</style>

<script>
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
