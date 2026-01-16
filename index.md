---
layout: default
title: Procvičovač – procvičuj zábavně
---

<div class="page">
  <div class="navbar">
    <a href="/" class="logo">Procvičovač</a>
    <div class="nav-right">
      <button id="mode-toggle" class="mode-btn" title="Přepnout světlý / tmavý režim">🌞</button>
      <a href="#" class="profile-btn">Přihlásit se / Profil</a>
    </div>
  </div>

  <main class="container">
    <div class="card">
      <h1>Vítej v Procvičovači!</h1>
      <p class="instruction">Vyber si předmět a začni procvičovat. Zábavně, zdarma a s přehledem tvého pokroku.</p>

      <div class="subject-grid">
        <a href="/cestina/" class="subject-card">
          <span class="subject-title">Čeština</span>
          <span class="subject-desc">i/y, abeceda, slovní zásoba</span>
        </a>
        <a href="/matematika/" class="subject-card">
          <span class="subject-title">Matematika</span>
          <span class="subject-desc">počítání, logika, slovní úlohy</span>
        </a>
        <a href="/anglictina/" class="subject-card">
          <span class="subject-title">Angličtina</span>
          <span class="subject-desc">slovíčka, gramatika, fráze</span>
        </a>
        <a href="/it/" class="subject-card">
          <span class="subject-title">IT</span>
          <span class="subject-desc">základy informatiky a digitální svět</span>
        </a>
      </div>

      <div class="cta">
        <h2>Začni hned s češtinou</h2>
        <a href="/cestina/" class="start-btn">Přejít na češtinu</a>
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
    padding: 2.5rem;
    border-radius: 18px;
    box-shadow: var(--shadow);
  }

  h1 {
    margin-top: 0;
    font-size: 2.4rem;
  }

  .instruction {
    color: var(--muted);
    margin-bottom: 2rem;
    font-size: 1.1rem;
  }

  .subject-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 1rem;
  }

  .subject-card {
    border: 1px solid var(--line);
    border-radius: 14px;
    padding: 1.2rem 1.4rem;
    text-decoration: none;
    color: inherit;
    display: flex;
    flex-direction: column;
    gap: 0.4rem;
    background: rgba(148, 163, 184, 0.08);
    transition: transform 0.2s ease, border-color 0.2s ease;
  }

  .subject-card:hover {
    transform: translateY(-3px);
    border-color: var(--primary);
  }

  .subject-title {
    font-weight: 700;
    font-size: 1.1rem;
  }

  .subject-desc {
    color: var(--muted);
    font-size: 0.95rem;
  }

  .cta {
    margin-top: 2.5rem;
    text-align: center;
    padding: 2rem;
    border-radius: 16px;
    background: rgba(37, 99, 235, 0.08);
  }

  .cta h2 {
    margin-top: 0;
  }

  .start-btn {
    display: inline-block;
    margin-top: 1rem;
    padding: 0.8rem 2rem;
    border-radius: 10px;
    background: var(--primary);
    color: white;
    text-decoration: none;
    font-weight: 600;
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
