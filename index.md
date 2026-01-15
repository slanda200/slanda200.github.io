---
layout: default
title: Procvičovač – procvičuj zábavně
---

<div class="layout-wrapper">
  <!-- Jediná horní lišta -->
  <header class="top-bar">
    <div class="container">
      <a href="/" class="logo">Procvičovač</a>
      
      <div class="right-controls">
        <button id="mode-toggle" class="mode-btn" title="Přepnout světlý / tmavý režim">🌞</button>
        <a href="#" class="profile-btn">Přihlásit se / Profil</a>
      </div>
    </div>
  </header>

  <!-- Obsah: sidebar + hlavní plocha -->
  <div class="content-area">
    <!-- Levý sidebar -->
    <aside class="sidebar">
      <nav>
        <ul class="menu">
          <li class="has-submenu">
            <a href="/cestina/" class="menu-title">Čeština</a>
            <ul class="submenu">
              {% for i in (1..9) %}
                <li><a href="/cestina/{{ i }}.trida/">{{ i }}. třída</a></li>
              {% endfor %}
              <li><a href="/cestina/stredni/">Střední škola</a></li>
            </ul>
          </li>
          <li><a href="/anglictina/" class="menu-title">Angličtina</a></li>
          <li><a href="/matematika/" class="menu-title">Matematika</a></li>
        </ul>
      </nav>
    </aside>

    <!-- Hlavní obsah – roztáhlý -->
    <main class="main-content">
      <h1>Vítej v Procvičovači!</h1>
      <p>Vyber si předmět v levém menu a začni procvičovat. Zábavně, zdarma a s přehledem tvého pokroku.</p>

      <div class="teaser-box">
        <h2>Začni hned s češtinou</h2>
        <a href="/cestina/" class="start-btn">Přejít na češtinu</a>
      </div>
    </main>
  </div>
</div>

<style>
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
    display: block;
    padding: 0.9rem 1rem;
    font-size: 1.15rem;
    font-weight: 600;
    color: var(--text);
    text-decoration: none;
    border-radius: 6px;
  }

  .menu-title:hover,
  .has-submenu.active > .menu-title {
    background: var(--sidebar-hover);
  }

  .submenu {
    list-style: none;
    padding: 0.5rem 0 0.5rem 1.5rem;
    margin: 0;
    max-height: 0;
    overflow: hidden;
    transition: max-height 0.35s ease;
  }

  .has-submenu.active .submenu {
    max-height: 600px; /* dost pro všechny třídy */
  }

  .submenu li a {
    display: block;
    padding: 0.7rem 1rem;
    color: var(--text);
    text-decoration: none;
    border-radius: 6px;
    font-size: 0.95rem;
  }

  .submenu li a:hover {
    background: var(--sidebar-hover);
  }

  .main-content {
    flex: 1;
    padding: 4rem 3rem;
    max-width: 1200px; /* omezení pro čitelnost, ale na velkém monitoru zabere skoro celou šířku */
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
// Rozbalování submenu pro Češtinu (jen kliknutí na titul)
document.querySelectorAll('.has-submenu > .menu-title').forEach(title => {
  title.addEventListener('click', function(e) {
    e.preventDefault(); // zabrání okamžitému přechodu na /cestina/
    this.parentElement.classList.toggle('active');
  });
});

// Dark / Light mód
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
