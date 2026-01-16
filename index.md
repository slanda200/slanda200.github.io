---
layout: default
title: Procvičovač – procvičuj zábavně
---

<div class="layout-wrapper" style="background-image: url('/images/pozadi.png'); background-size: cover; background-position: center; background-repeat: no-repeat; min-height: 100vh;">
  <!-- Horní lišta (poloprůhledná, aby byl vidět background) -->
  <header class="top-bar">
    <div class="container">
      <a href="/" class="logo">Procvičovač</a>
      
      <div class="right-controls">
        <button id="mode-toggle" class="mode-btn" title="Přepnout světlý / tmavý režim">🌞</button>
        <a href="#" class="profile-btn">Přihlásit se / Profil</a>
      </div>
    </div>
  </header>

  <!-- Obsah – sidebar + hlavní plocha -->
  <div class="content-area">
    <!-- Sidebar vlevo -->
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

    <!-- Hlavní obsah -->
    <main class="main-content">
      <h1>Vítej v Procvičovači!</h1>
      <p>Vyber si předmět v menu vlevo a začni procvičovat. Zábavně, zdarma a s přehledem tvého pokroku.</p>
    </main>
  </div>
</div>

<style>
  /* Skryje defaultní Minima header */
  .site-header, .header, .post-header, .page-header, header[role="banner"], #site-header { display: none !important; }

  /* Horní lišta – poloprůhledná, aby byl vidět background */
  .top-bar {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 1000;
    background: rgba(229, 231, 235, 0.85); /* poloprůhledná šedá */
    backdrop-filter: blur(8px); /* rozostření pro moderní vzhled */
    padding: 0.8rem 0;
    box-shadow: 0 2px 10px rgba(0,0,0,0.15);
  }

  /* Obsah – sidebar a hlavní část */
  .content-area {
    margin-top: 65px;
    display: flex;
    min-height: calc(100vh - 65px);
  }

  .sidebar {
    width: 260px;
    background: rgba(241, 245, 249, 0.9); /* poloprůhledná, aby byl vidět background */
    backdrop-filter: blur(5px);
    padding: 2rem 0.8rem;
    position: sticky;
    top: 65px;
    height: calc(100vh - 65px);
    overflow-y: auto;
    border-right: 1px solid rgba(0,0,0,0.1);
  }

  .main-content {
    flex: 1;
    padding: 4rem 2rem;
    color: #1f2937; /* tmavší text kvůli pozadí */
  }

  body.dark .main-content { color: #e2e8f0; }
  body.dark .sidebar { background: rgba(30, 41, 59, 0.9); }
  body.dark .top-bar { background: rgba(30, 41, 59, 0.85); }

  /* Zbytek tvých stylů (menu, barvy atd.) */
  :root { --bg: transparent; --text: #1f2937; --header-bg: transparent; --sidebar-bg: transparent; --accent: #64748b; --sidebar-hover: rgba(226, 232, 240, 0.5); }
  body.dark { --text: #e2e8f0; --sidebar-hover: rgba(51, 65, 85, 0.5); }

  /* Tvé původní menu styly */
  .menu { list-style: none; padding: 0; margin: 0; }
  .menu-title { display: block; padding: 0.9rem 1rem; font-size: 1.15rem; font-weight: 600; color: var(--text); text-decoration: none; border-radius: 6px; }
  .menu-title:hover { background: var(--sidebar-hover); }
  .submenu { list-style: none; padding: 0.5rem 0 0.5rem 1.5rem; max-height: 0; overflow: hidden; transition: max-height 0.35s ease; }
  .has-submenu.active .submenu { max-height: 600px; }
  .submenu li a { display: block; padding: 0.7rem 1rem; color: var(--text); text-decoration: none; border-radius: 6px; font-size: 0.95rem; }
  .submenu li a:hover { background: var(--sidebar-hover); }
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
