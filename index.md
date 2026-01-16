---
layout: default
title: Procvičovač – procvičuj zábavně
---

<style>
  body, html {
    margin: 0;
    padding: 0;
    height: 100%;
    background-image: url('/images/pozadi.png');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
  }

  /* Skryje defaultní header od Minima */
  .site-header, .header, .post-header, .page-header, header[role="banner"], #site-header {
    display: none !important;
  }

  /* Horní lišta – průhledná, černá čára dole */
  .top-bar {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 1000;
    background: rgba(0,0,0,0.4);  /* průhledná černá */
    backdrop-filter: blur(10px);
    border-bottom: 2px solid black;  /* černá oddělovací čára */
    padding: 0.8rem 0;
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
    font-size: 1.9rem;
    font-weight: bold;
    color: white;
    text-decoration: none;
  }

  .right-controls {
    display: flex;
    gap: 1.5rem;
    align-items: center;
  }

  .mode-btn {
    background: none;
    border: none;
    font-size: 1.7rem;
    cursor: pointer;
    color: white;
  }

  .profile-btn {
    background: rgba(100,116,139,0.7);
    color: white;
    padding: 0.5rem 1rem;
    border-radius: 6px;
    text-decoration: none;
  }

  /* Obsah – začíná pod lištou */
  .content-area {
    margin-top: 65px;
    padding: 2rem;
    color: white;
    text-shadow: 1px 1px 3px black;
  }

  h1 {
    font-size: 3.5rem;
    margin-bottom: 1rem;
  }

  p {
    font-size: 1.4rem;
    max-width: 800px;
  }
</style>

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

  <!-- Obsah -->
  <div class="content-area">
    <h1>Vítej v Procvičovači!</h1>
    <p>Vyber si předmět v menu vlevo a začni procvičovat. Zábavně, zdarma a s přehledem tvého pokroku.</p>
  </div>
</div>
