---
layout: default
title: Procvičovač – procvičuj zábavně
---

<header class="site-header">
  <div class="container">
    <a href="/" class="logo">
      <strong>Procvičovač</strong>
    </a>

    <span class="slogan">Procvičuj češtinu, angličtinu a matiku zábavně a zdarma</span>

    <div class="user-controls">
      <button id="mode-toggle" class="mode-btn" title="Přepnout světlý / tmavý režim">🌞</button>
      <a href="#" class="profile-link">Přihlásit se / Profil</a>
    </div>
  </div>
</header>

<main class="main-content">
  <h1>Vyber si předmět</h1>
  
  <div class="subject-grid">
    <a href="/cestina/" class="subject-card">Čeština</a>
    <a href="/anglictina/" class="subject-card">Angličtina</a>
    <a href="/matematika/" class="subject-card">Matematika</a>
  </div>
</main>

<style>
  :root {
    --bg: #f8f9fa;
    --text: #1f2937;
    --header-bg: #e5e7eb;
    --card-bg: #e5e7eb;
    --card-hover: #d1d5db;
    --accent: #6b7280;
  }

  body.dark {
    --bg: #111827;
    --text: #f3f4f6;
    --header-bg: #1f2937;
    --card-bg: #374151;
    --card-hover: #4b5563;
    --accent: #9ca3af;
  }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: system-ui, -apple-system, sans-serif;
    margin: 0;
    transition: background 0.4s, color 0.4s;
  }

  .site-header {
    background: var(--header-bg);
    padding: 1.2rem 0;
    position: sticky;
    top: 0;
    z-index: 100;
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
  }

  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 1.5rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 1rem;
  }

  .logo {
    text-decoration: none;
    color: var(--text);
    font-size: 2.2rem;
    font-weight: bold;
  }

  .slogan {
    font-size: 1.1rem;
    color: var(--accent);
    font-weight: 400;
    flex: 1;
    text-align: center;
    min-width: 200px;
  }

  .user-controls {
    display: flex;
    align-items: center;
    gap: 1.5rem;
  }

  .mode-btn {
    background: none;
    border: none;
    font-size: 1.8rem;
    cursor: pointer;
    color: var(--text);
    transition: transform 0.2s;
  }

  .mode-btn:hover { transform: scale(1.15); }

  .profile-link {
    background: var(--accent);
    color: white;
    padding: 0.6rem 1.2rem;
    border-radius: 8px;
    text-decoration: none;
    font-weight: 500;
    transition: background 0.2s;
  }

  .profile-link:hover { background: #4b5563; }

  .main-content {
    text-align: center;
    padding: 5rem 1rem 8rem;
  }

  h1 {
    font-size: 3rem;
    margin-bottom: 3.5rem;
    font-weight: 700;
  }

  .subject-grid {
    display: flex;
    justify-content: center;
    gap: 3rem;
    flex-wrap: wrap;
  }

  .subject-card {
    background: var(--card-bg);
    color: var(--text);
    padding: 4rem 7rem;
    font-size: 2.4rem;
    font-weight: bold;
    border-radius: 20px;
    text-decoration: none;
    box-shadow: 0 8px 20px rgba(0,0,0,0.15);
    transition: all 0.3s ease;
    min-width: 240px;
  }

  .subject-card:hover {
    background: var(--card-hover);
    transform: translateY(-10px);
    box-shadow: 0 15px 30px rgba(0,0,0,0.2);
  }

  @media (max-width: 900px) {
    .container { flex-direction: column; text-align: center; }
    .slogan { margin: 0.5rem 0; }
    .subject-grid { gap: 2rem; }
    .subject-card { padding: 3rem 5rem; font-size: 2rem; }
  }
</style>

<script>
  const toggleBtn = document.getElementById('mode-toggle');
  
  if (localStorage.getItem('mode') === 'dark' || 
      (!localStorage.getItem('mode') && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
    document.body.classList.add('dark');
    toggleBtn.textContent = '🌙';
  } else {
    toggleBtn.textContent = '🌞';
  }

  toggleBtn.addEventListener('click', () => {
    document.body.classList.toggle('dark');
    if (document.body.classList.contains('dark')) {
      toggleBtn.textContent = '🌙';
      localStorage.setItem('mode', 'dark');
    } else {
      toggleBtn.textContent = '🌞';
      localStorage.setItem('mode', 'light');
    }
  });
</script>
