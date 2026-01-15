---
layout: default
title: Vybírání i/y – Cvičení 1
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
    <main class="main-content">
      <h1>Cvičení 1 – i/y</h1>
      <p>Doplň i nebo y do slov.</p>

      <div class="task-box">
        <p>1. M_l_ko (mléko)</p>
        <input type="text" id="ans1" placeholder="i nebo y" maxlength="1">

        <p>2. P_ták (pták)</p>
        <input type="text" id="ans2" placeholder="i nebo y" maxlength="1">

        <p>3. D_vka (dívka)</p>
        <input type="text" id="ans3" placeholder="i nebo y" maxlength="1">

        <button onclick="check()">Zkontrolovat</button>
        <p id="vysledek"></p>
      </div>
    </main>
  </div>
</div>

<style>
  .site-header { display: none !important; } /* skryje starý header */
  .top-bar { position: fixed; top: 0; width: 100%; z-index: 999; }
  .content-area { margin-top: 80px; }
  .task-box { padding: 2rem; background: #f1f5f9; border-radius: 12px; max-width: 600px; margin: 2rem auto; }
  input { padding: 0.5rem; width: 60px; text-align: center; }
  button { padding: 0.8rem 1.5rem; background: #64748b; color: white; border: none; border-radius: 6px; cursor: pointer; }
</style>

<script>
  function check() {
    let správně = 0;
    if (document.getElementById('ans1').value.toLowerCase() === 'i') správně++;
    if (document.getElementById('ans2').value.toLowerCase() === 'y') správně++;
    if (document.getElementById('ans3').value.toLowerCase() === 'í') správně++;
    
    document.getElementById('vysledek').innerHTML = správně === 3 ? "Správně!" : "Zkus to znovu (mílko, pýták, dívka)";
  }

  // Dark/light (pokud chceš)
  document.getElementById('mode-toggle').onclick = () => {
    document.body.classList.toggle('dark');
  };
</script>
