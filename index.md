---
layout: default
title: Procvičovač – procvičuj zábavně
---

<div class="layout-wrapper" style="background-image: url('/images/pozadi.png'); background-size: cover; background-position: center; background-repeat: no-repeat; min-height: 100vh;">
  <!-- Horní lišta – viditelně označená -->
  <header class="top-bar">
    <div class="container">
      <a href="/" class="logo">Procvičovač</a>
      
      <div class="right-controls">
        <button id="mode-toggle" class="mode-btn" title="Přepnout světlý / tmavý režim">🌞</button>
        <a href="#" class="profile-btn">Přihlásit se / Profil</a>
      </div>
    </div>
  </header>

  <!-- Hlavní obsah – pod lištou -->
  <div class="content-area">
    <main class="main-content">
      <h1>Vítej v Procvičovači!</h1>
      <p>Vyber si předmět v menu vlevo a začni procvičovat. Zábavně, zdarma a s přehledem tvého pokroku.</p>
    </main>
  </div>
</div>

<style>
  /* Skrýt defaultní šedý header */
  .site-header, .header, .post-header, .page-header, header[role="banner"], #site-header { display: none !important; }

  /* Horní lišta – výrazně označená */
  .top-bar {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 1000;
    background: rgba(30, 41, 59, 0.92); /* tmavě modrošedá, viditelná na pozadí */
    backdrop-filter: blur(12px); /* rozostření pro moderní vzhled */
    border-bottom: 2px solid #64748b; /* modrý okraj dole */
    box-shadow: 0 4px 15px rgba(0,0,0,0.4); /* silnější stín */
    padding: 1rem 0;
  }

  .container {
    max-width: 100%;
    margin: 0;
    padding: 0 2rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .logo {
    font-size: 2rem;
    font-weight: bold;
    color: white;
    text-decoration: none;
    text-shadow: 0 0 5px rgba(0,0,0,0.5);
  }

  .right-controls {
    display: flex;
    gap: 1.5rem;
    align-items: center;
  }

  .mode-btn {
    background: none;
    border: none;
    font-size: 1.8rem;
    cursor: pointer;
    color: white;
  }

  .profile-btn {
    background: #64748b;
    color: white;
    padding: 0.6rem 1.2rem;
    border-radius: 8px;
    text-decoration: none;
    font-weight: 500;
  }

  /* Obsah – pod lištou */
  .content-area {
    margin-top: 80px; /* přesně pod lištou */
    padding: 2rem;
  }

  .main-content {
    color: white;
    text-shadow: 1px 1px 3px black;
    max-width: 900px;
    margin: 0 auto;
  }

  h1 {
    font-size: 3.5rem;
    margin-bottom: 1rem;
  }

  p {
    font-size: 1.4rem;
    line-height: 1.6;
  }
</style>

<script>
  // Dark/light mód (pokud ho chceš)
  const toggle = document.getElementById('mode-toggle');
  toggle.addEventListener('click', () => {
    document.body.classList.toggle('dark');
    toggle.textContent = document.body.classList.contains('dark') ? '🌙' : '🌞';
  });
</script>
