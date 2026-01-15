---
layout: default
title: Čeština – 1. třída
---

<div class="layout-wrapper">
  <!-- Stejný horní bar jako na hlavní stránce -->
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
    <!-- Levý sidebar s tématy pro 1. třídu češtiny -->
    <aside class="sidebar">
      <nav>
        <ul class="menu">
          <li><a href="/cestina/1.trida/abeceda/" class="menu-title">Abeceda a písmenka</a></li>
          <li><a href="/cestina/1.trida/i-y/" class="menu-title">Vybírání i/y</a></li>
          <li><a href="/cestina/1.trida/hledani-chyb/" class="menu-title">Hledání chyb</a></li>
          <li><a href="/cestina/1.trida/doplnovani-textu/" class="menu-title">Doplňování do textu</a></li>
          <li><a href="/cestina/1.trida/zaskrtavani/" class="menu-title">Zaškrtávání</a></li>
          <li><a href="/cestina/1.trida/spojovani/" class="menu-title">Spojování</a></li>
          <!-- Přidej další témata podle osnov (např. slova, věty) -->
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
  /* Celý styl z hlavní stránky – vlož sem kompletní <style> z tvého index.md, aby bylo konzistentní */
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

  /* ... zkopíruj zbytek stylu z tvého hlavního index.md ... */
</style>

<script>
  /* Celý script z hlavní stránky – pro mode a rozbalování (pokud bys měl rozbalovací témata) */
  // Rozbalování submenu (pokud přidáš has-submenu)
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
