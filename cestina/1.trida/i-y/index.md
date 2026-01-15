---
layout: default
title: Čeština – 1. třída – Vybírání i/y
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

  <!-- Hlavní obsah s úlohou -->
  <div class="content-area">
    <main class="main-content">
      <h1>Vybírání i/y</h1>
      <p>Doplň správně i nebo y do slov. Klikni na "Zkontrolovat" pro výsledek.</p>

      <!-- Jednoduchá úloha -->
      <div class="task-box">
        <p>Doplň: m_l_ko (mléko)</p>
        <input type="text" id="answer1" placeholder="i nebo y" maxlength="1">
        <p>Doplň: p_ták (pták)</p>
        <input type="text" id="answer2" placeholder="i nebo y" maxlength="1">
        <button onclick="checkAnswers()">Zkontrolovat</button>
        <p id="result"></p>
      </div>
    </main>
  </div>
</div>

<style>
  /* Zkopíruj celý styl z předchozího souboru pro konzistenci */
  /* ... vlož celý <style> z 1.trida/index.md ... */

  /* Dodatečné styly pro úlohu */
  .task-box {
    padding: 2rem;
    background: var(--sidebar-bg);
    border-radius: 12px;
    box-shadow: 0 4px 15px rgba(0,0,0,0.08);
    max-width: 600px;
    margin: 2rem auto;
  }

  input {
    padding: 0.5rem;
    margin: 0.5rem 0;
    border: 1px solid var(--accent);
    border-radius: 6px;
  }

  button {
    background: var(--accent);
    color: white;
    padding: 0.8rem 1.6rem;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    margin-top: 1rem;
  }

  #result {
    font-weight: bold;
    margin-top: 1rem;
  }
</style>

<script>
  // Kontrola odpovědí
  function checkAnswers() {
    const ans1 = document.getElementById('answer1').value.toLowerCase();
    const ans2 = document.getElementById('answer2').value.toLowerCase();
    let result = '';

    if (ans1 === 'l' && ans2 === 't') {
      result = 'Správně! Dobrá práce.';
    } else {
      result = 'Chyba. Zkus to znovu. (Nápověda: m_l_ko = mléko, p_ták = pták)';
    }

    document.getElementById('result').textContent = result;
  }

  // Dark/light mód (zkopíruj z předchozího)
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
