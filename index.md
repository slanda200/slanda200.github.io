---
layout: default
title: Procvičovač – procvičuj zábavně
---

<div class="layout-wrapper">
  <!-- Horní lišta -->
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
    <!-- Sidebar vlevo -->
    <aside class="sidebar">
      <nav>
        <ul class="menu">
          <li class="has-submenu">
            <a href="#" class="menu-title">Čeština</a>
            <ul class="submenu">
              {% for i in (1..9) %}
                <li><a href="/cestina/{{ i }}.trida/">{{ i }}. třída</a></li>
              {% endfor %}
              <li><a href="/cestina/stredni/">Střední škola</a></li>
            </ul>
          </li>
          <li class="has-submenu">
            <a href="#" class="menu-title">Angličtina</a>
            <ul class="submenu">
              {% for i in (1..9) %}
                <li><a href="/anglictina/{{ i }}.trida/">{{ i }}. třída</a></li>
              {% endfor %}
              <li><a href="/anglictina/stredni/">Střední škola</a></li>
            </ul>
          </li>
          <li class="has-submenu">
            <a href="#" class="menu-title">Matematika</a>
            <ul class="submenu">
              {% for i in (1..9) %}
                <li><a href="/matematika/{{ i }}.trida/">{{ i }}. třída</a></li>
              {% endfor %}
              <li><a href="/matematika/stredni/">Střední škola</a></li>
            </ul>
          </li>
          <li class="has-submenu">
            <a href="#" class="menu-title">IT</a>
            <ul class="submenu">
              {% for i in (1..9) %}
                <li><a href="/it/{{ i }}.trida/">{{ i }}. třída</a></li>
              {% endfor %}
              <li><a href="/it/stredni/">Střední škola</a></li>
            </ul>
          </li>
        </ul>
      </nav>
    </aside>

    <!-- Hlavní obsah – čistý a jednoduchý -->
    <main class="main-content">
      <h1>Vítej v Procvičovači!</h1>
      <p>Vyber si předmět v menu vlevo a začni procvičovat.</p>
    </main>
  </div>
</div>

<style>
  /* Skrýt defaultní header */
  .site-header, .header, .post-header, .page-header, header[role="banner"], #site-header { display: none !important; }

  /* Horní bar – full-width, bez mezer */
  .top-bar {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 1000;
    background: var(--header-bg);
    padding: 0.8rem 0;
    box-shadow: 0 2px 10px rgba(0,0,0,0.15);
  }

  /* Obsah – sidebar vlevo bez mezer */
  .content-area {
    margin-top: 65px;
    display: flex;
    min-height: calc(100vh - 65px);
    padding: 0;
    margin: 0;
  }

  :root {
    --bg: #f8f9fa;
    --text: #1f2937;
    --header-bg: #e5e7eb;
    --sidebar-bg: #f1f5f9;
    --accent: #64748b;
    --sidebar-hover: #e2e8f0;
  }

  body.dark {
    --bg: #0f172a;
    --text: #e2e8f0;
    --header-bg: #1e293b;
    --sidebar-bg: #1e293b;
    --accent: #94a3b8;
    --sidebar-hover: #334155;
  }

  body {
    background: var(--bg);
    color: var(--text);
    margin: 0;
    font-family: system-ui, sans-serif;
  }

  .container {
    max-width: 100%;
    margin: 0;
    padding: 0 1.5rem;
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
  }

  .sidebar {
    width: 260px;
    background: var(--sidebar-bg);
    padding: 2rem 0.8rem;
    margin-left: 0;
    position: sticky;
    top: 65px;
    height: calc(100vh - 65px);
    overflow-y: auto;
    border-right: 1px solid var(--accent);
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
    max-height: 600px;
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
    padding: 4rem 2rem 4rem 1rem;
    max-width: 100%;
    margin: 0;
  }

  h1 { font-size: 2.8rem; margin-bottom: 1.5rem; }
  p { font-size: 1.15rem; line-height: 1.6; max-width: 800px; }

  @media (max-width: 992px) {
    .content-area { flex-direction: column; }
    .sidebar { width: 100%; position: static; height: auto; border-right: none; border-bottom: 1px solid var(--accent); padding: 1.5rem 0; }
    .main-content { padding: 2.5rem 1rem; }
  }
</style>

<script>
  // Rozbalování submenu
  document.querySelectorAll('.has-submenu > .menu-title').forEach(title => {
    title.addEventListener('click', function(e) {
      e.preventDefault();
      this.parentElement.classList.toggle('active');
    });
  });

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
