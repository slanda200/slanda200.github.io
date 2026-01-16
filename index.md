---
layout: default
title: Procvičovač – procvičuj zábavně
---

<div class="page">
  <header class="navbar">
    <a href="/" class="logo">Procvičovač</a>
    <div class="nav-right">
      <button id="mode-toggle" class="mode-btn" title="Přepnout světlý / tmavý režim">🌞</button>
      <a href="#" class="profile-btn">Přihlásit se / Profil</a>
    </div>
  </header>

  <div class="layout">
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
          <li class="has-submenu">
            <a href="/anglictina/" class="menu-title">Angličtina</a>
            <ul class="submenu">
              {% for i in (1..9) %}
                <li><a href="/anglictina/{{ i }}.trida/">{{ i }}. třída</a></li>
              {% endfor %}
              <li><a href="/anglictina/stredni/">Střední škola</a></li>
            </ul>
          </li>
          <li class="has-submenu">
            <a href="/matematika/" class="menu-title">Matematika</a>
            <ul class="submenu">
              {% for i in (1..9) %}
                <li><a href="/matematika/{{ i }}.trida/">{{ i }}. třída</a></li>
              {% endfor %}
              <li><a href="/matematika/stredni/">Střední škola</a></li>
            </ul>
          </li>
          <li class="has-submenu">
            <a href="/it/" class="menu-title">IT</a>
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

    <main class="content">
      <div class="card">
        <h1>Vítej v Procvičovači!</h1>
        <p class="instruction">Vyber si předmět v levém menu a začni procvičovat. Zábavně, zdarma a s přehledem tvého pokroku.</p>

        <div class="cta">
          <h2>Začni hned s češtinou</h2>
          <a href="/cestina/" class="start-btn">Přejít na češtinu</a>
        </div>
      </div>
    </main>
  </div>
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

  .layout {
    display: flex;
    flex: 1;
    min-height: calc(100vh - 64px);
  }

  .sidebar {
    width: 260px;
    padding: 1.5rem 1rem;
    background: var(--card);
    border-right: 1px solid var(--line);
  }

  .menu {
    list-style: none;
    margin: 0;
    padding: 0;
    display: flex;
    flex-direction: column;
    gap: 0.4rem;
  }

  .menu-title {
    display: block;
    padding: 0.85rem 1rem;
    font-size: 1.05rem;
    font-weight: 700;
    color: inherit;
    text-decoration: none;
    border-radius: 10px;
    background: rgba(148, 163, 184, 0.12);
  }

  .menu-title:hover,
  .has-submenu.active > .menu-title {
    background: rgba(37, 99, 235, 0.12);
    color: var(--primary);
  }

  .submenu {
    list-style: none;
    margin: 0.35rem 0 0 0;
    padding: 0 0 0 1rem;
    max-height: 0;
    overflow: hidden;
    transition: max-height 0.35s ease;
    display: flex;
    flex-direction: column;
    gap: 0.2rem;
  }

  .has-submenu.active .submenu {
    max-height: 600px;
  }

  .submenu li a {
    display: block;
    padding: 0.6rem 0.9rem;
    border-radius: 8px;
    color: inherit;
    text-decoration: none;
    font-size: 0.95rem;
  }

  .submenu li a:hover {
    background: rgba(148, 163, 184, 0.2);
  }

  .content {
    flex: 1;
    padding: 2.5rem 3rem;
    display: flex;
    justify-content: center;
  }

  .card {
    background: var(--card);
    border-radius: 18px;
    padding: 2.5rem;
    box-shadow: var(--shadow);
    max-width: 900px;
    width: 100%;
  }

  h1 {
    margin-top: 0;
    font-size: 2.4rem;
  }

  .instruction {
    color: var(--muted);
    font-size: 1.1rem;
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

  @media (max-width: 992px) {
    .layout {
      flex-direction: column;
    }

    .sidebar {
      width: 100%;
      border-right: none;
      border-bottom: 1px solid var(--line);
    }

    .content {
      padding: 2rem 1.5rem;
    }
  }
</style>

<script>
  document.querySelectorAll('.has-submenu > .menu-title').forEach(title => {
    title.addEventListener('click', event => {
      event.preventDefault();
      title.parentElement.classList.toggle('active');
    });
  });

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
