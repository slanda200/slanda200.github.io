---
layout: default
title: Procvičovač – procvičuj zábavně
---

<header class="site-header">
  <div class="container">
    <a href="/" class="logo">
      <strong>Procvičovač</strong>
      <span class="slogan">Procvičuj češtinu, angličtinu a matiku zábavně a zdarma</span>
    </a>

    <div class="user-controls">
      <button id="mode-toggle" class="mode-btn" title="Přepnout světlý / tmavý režim">🌞</button>
      <a href="#" class="profile-link">Profil / Přihlásit se</a>
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
    --bg: #f8f9fa;              /* světlý mód - velmi světlá šedá */
    --text: #1f2937;            /* tmavě šedý text */
    --header-bg: #e5e7eb;       /* header šedý */
    --card-bg: #e5e7eb;         /* tlačítka šedá */
    --card-hover: #d1d5db;      /* hover efekt */
    --accent: #6b7280;          /* šedomodrá akcent */
  }

  body.dark {
    --bg: #111827;              /* tmavý mód - hluboká šedá */
    --text: #f3f4f6;            /* světlý text */
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
    border-bottom: 1px solid var(--accent);
    font-weight: 600;
  }

  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 1.5rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .logo {
    text-decoration: none;
    color: var(--text);
    font-size: 2.1rem;
    display: flex;
    align-items: baseline;
    gap: 1rem;
  }

  .slogan {
    font-size: 1.1rem;
    color: var(--accent);
    font-weight: normal;
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
    padding: 4rem 1rem 6rem;
  }

  h1 {
    font-size: 2.8rem;
    margin-bottom: 3rem;
    font-weight: 700;
  }

  .subject-grid {
    display: flex;
    justify-content: center;
    gap: 2.5rem;
    flex-wrap: wrap;
  }

  .subject-card {
    background: var(--card-bg);
    color: var(--text);
    padding: 3.5rem 6rem;
    font-size: 2.2rem;
    font-weight: bold;
    border-radius: 16px;
    text-decoration: none;
    box-shadow: 0 6px 15px rgba(0,0,0,0.12);
    transition: all 0.3s ease;
    min-width: 220px;
    text-align: center;
  }

  .subject-card:hover {
    background: var(--card-hover);
    transform: translateY(-8px);
    box-shadow: 0 12px 25px rgba(0,0,0,0.18);
  }

  @media (max-width: 768px) {
    .subject-grid { flex-direction: column; align-items: center; }
    .subject-card { padding: 2.5rem 4rem; font-size: 1.8rem; }
  }
</style>

<script>
  const toggleBtn = document.getElementById('mode-toggle');
  
  // Načti uložený mód nebo systémový preference
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
