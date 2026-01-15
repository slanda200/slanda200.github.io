---
layout: default
title: Čeština – 1. třída
---

<div class="layout-wrapper">
  <!-- Horní lišta s mode toggle a přihlášením -->
  <header class="top-bar">
    <div class="container">
      <a href="/" class="logo">Procvičovač</a>
      
      <div class="right-controls">
        <button id="mode-toggle" class="mode-btn" title="Přepnout světlý / tmavý režim">🌞</button>
        <a href="#" class="profile-btn">Přihlásit se / Profil</a>
      </div>
    </div>
  </header>

  <!-- Obsah: sidebar s tématy + hlavní plocha -->
  <div class="content-area">
    <!-- Levý sidebar s tématy (s ikonami a box stylem) -->
    <aside class="sidebar">
      <nav>
        <ul class="menu">
          <li><a href="/cestina/1.trida/abeceda/" class="menu-title">📖 Abeceda a písmenka</a></li>
          <li><a href="/cestina/1.trida/i-y/" class="menu-title">🔤 Vybírání i/y</a></li>
          <li><a href="/cestina/1.trida/hledani-chyb/" class="menu-title">🔍 Hledání chyb</a></li>
          <li><a href="/cestina/1.trida/doplnovani-textu/" class="menu-title">✏️ Doplňování do textu</a></li>
          <li><a href="/cestina/1.trida/zaskrtavani/" class="menu-title">✅ Zaškrtávání</a></li>
          <li><a href="/cestina/1.trida/spojovani/" class="menu-title">🔗 Spojování</a></li>
          <!-- Přidej další témata s ikonami -->
        </ul>
      </nav>
    </aside>

    <!-- Hlavní obsah – úvod do třídy -->
    <main class="main-content">
      <h1>Čeština – 1. třída</h1>
      <p>Zde procvičuj základní češtinu pro 1. třídu. Vyber téma v levém menu a začni s úlohami!</p>

      <!-- Teaser na první téma -->
      <div class="teaser-box">
        <h2>Začni s abecedou</h2>
        <a href="/cestina/1.trida/abeceda/" class="start-btn">Přejít na úlohy</a>
      </div>
    </main>
  </div>
</div>

<style>
  /* Styl z hlavní stránky + vylepšení pro profi vzhled (zaoblené boxy, stínování) */
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
    position: sticky;
    top: 0;
    z-index: 100;
    box-shadow: 0 2px 8px rgba(0,0,0,0.08);
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

  .content-area {
    display: flex;
    min-height: calc(100vh - 65px);
  }

  .sidebar {
    width: 260px;
    background: var(--sidebar-bg);
    border-right: 1px solid var(--accent);
    padding: 2rem 1rem;
    position: sticky;
    top: 65px;
    height: calc(100vh - 65px);
    overflow-y: auto;
  }

  .menu {
    list-style: none;
    padding: 0;
    margin: 0;
  }

  .menu-title {
    display: flex;
    align-items: center;
    padding: 1rem 1.2rem;
    font-size: 1.15rem;
    font-weight: 600;
    color: var(--text);
    text-decoration: none;
    border-radius: 8px;
    background: var(--sidebar-bg);
    box-shadow: 0 2px 5px rgba(0,0,0,0.05);
    transition: all 0.3s;
  }

  .menu-title:hover {
    background: var(--sidebar-hover);
    box-shadow: 0 4px 10px rgba(0,0,0,0.1);
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

  .teaser-box {
    margin-top: 4rem;
    text-align: center;
    padding: 2.5rem;
    background: var(--sidebar-bg);
    border-radius: 12px;
    box-shadow: 0 4px 15px rgba(0,0,0,0.08);
  }

  .start-btn {
    background: var(--accent);
    color: white;
    padding: 1rem 2.5rem;
    border-radius: 8px;
    text-decoration: none;
    font-size: 1.25rem;
    display: inline-block;
    margin-top: 1.5rem;
  }

  @media (max-width: 992px) {
    .content-area { flex-direction: column; }
    .sidebar {
      width: 100%;
      position: static;
      height: auto;
      border-right: none;
      border-bottom: 1px solid var(--accent);
      padding: 1.5rem;
    }
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
