---
layout: default
title: Čeština – 1. třída
---

<div class="layout-wrapper">
  <header class="top-bar">
    <div class="container">
      <a href="/" class="logo">Procvičovač</a>
      <div class="right-controls">
        <button id="mode-toggle" class="mode-btn">🌞</button>
        <a href="#" class="profile-btn">Přihlásit se / Profil</a>
      </div>
    </div>
  </header>

  <div class="content-area">
    <aside class="sidebar">
      <nav>
        <ul class="menu">
          <li><a href="/cestina/1.trida/abeceda/" class="menu-title">📖 Abeceda</a></li>
          <li><a href="/cestina/1.trida/i-y/" class="menu-title">🔤 i/y</a></li>
          <!-- Přidej další témata -->
        </ul>
      </nav>
    </aside>

    <main class="main-content">
      <h1>Čeština – 1. třída</h1>
      <p>Vyber téma v menu vlevo.</p>
    </main>
  </div>
</div>

<style>
  /* Skrýt default header */
  .site-header { display: none !important; }

  /* Styly jako v hlavní stránce */
  .top-bar { position: fixed; top: 0; width: 100%; z-index: 9999; background: #e5e7eb; padding: 1rem 0; box-shadow: 0 2px 10px rgba(0,0,0,0.15); }

  .content-area { margin-top: 75px; display: flex; min-height: calc(100vh - 75px); }

  :root { --bg: #f8f9fa; --text: #1f2937; --header-bg: #e5e7eb; --sidebar-bg: #f1f5f9; --accent: #64748b; --sidebar-hover: #e2e8f0; }

  body.dark { --bg: #0f172a; --text: #e2e8f0; --header-bg: #1e293b; --sidebar-bg: #1e293b; --accent: #94a3b8; --sidebar-hover: #334155; }

  body { background: var(--bg); color: var(--text); margin: 0; font-family: system-ui; }

  .container { max-width: 1600px; margin: 0 auto; padding: 0 2rem; display: flex; justify-content: space-between; align-items: center; }

  .logo { font-size: 1.9rem; font-weight: bold; color: var(--text); text-decoration: none; }

  .right-controls { display: flex; gap: 1.5rem; }

  .mode-btn { background: none; border: none; font-size: 1.7rem; cursor: pointer; color: var(--text); }

  .profile-btn { background: var(--accent); color: white; padding: 0.55rem 1.1rem; border-radius: 6px; text-decoration: none; }

  .sidebar { width: 260px; background: var(--sidebar-bg); padding: 2rem 1rem; position: sticky; top: 75px; height: calc(100vh - 75px); overflow-y: auto; border-right: 1px solid var(--accent); }

  .menu { list-style: none; padding: 0; margin: 0; }

  .menu-title { display: block; padding: 0.9rem 1rem; font-size: 1.15rem; font-weight: 600; color: var(--text); text-decoration: none; border-radius: 6px; }

  .menu-title:hover { background: var(--sidebar-hover); }

  .main-content { flex: 1; padding: 4rem 3rem; max-width: 1200px; margin: 0 auto; width: 100%; }

  h1 { font-size: 2.8rem; margin-bottom: 1.5rem; }
  p { font-size: 1.15rem; line-height: 1.6; max-width: 800px; }

  @media (max-width: 992px) { .content-area { flex-direction: column; } .sidebar { width: 100%; position: static; height: auto; border-right: none; border-bottom: 1px solid var(--accent); padding: 1.5rem; } .main-content { padding: 2.5rem 1.5rem; } }
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
