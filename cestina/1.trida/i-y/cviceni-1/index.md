---
layout: default
title: Cvičení 1 – i/y
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
      <p>Klikni na _ a vyber písmeno.</p>

      <div id="exercise-text"></div>

      <div id="popup" style="display:none; position:fixed; top:0; left:0; width:100%; height:100%; background:rgba(0,0,0,0.5); align-items:center; justify-content:center;">
        <div style="background: #f1f5f9; padding:2rem; border-radius:12px; text-align:center;">
          <button onclick="fill('i')">i</button>
          <button onclick="fill('y')">y</button>
          <button onclick="fill('í')">í</button>
          <button onclick="fill('ý')">ý</button>
          <br>
          <button onclick="closePopup()">Zavřít</button>
        </div>
      </div>

      <button onclick="check()">Zkontrolovat</button>
      <p id="result"></p>
    </main>
  </div>
</div>

<style>
  .site-header { display: none !important; }
  .top-bar { position: fixed; top: 0; width: 100%; z-index: 999; }
  .content-area { margin-top: 80px; }
  #exercise-text { font-size: 1.2rem; line-height: 1.8; }
  .blank { background: yellow; padding: 0 0.2rem; cursor: pointer; }
  #popup button { margin: 0.5rem; padding: 1rem; font-size: 1.5rem; }
</style>

<script>
  // Načte text z cviceni.txt
  fetch('/cestina/1.trida/i-y/cviceni-1/cviceni.txt')
    .then(r => r.text())
    .then(t => {
      let html = t.replace(/<>/g, '<span class="blank" onclick="openPopup(this)">_</span>');
      document.getElementById('exercise-text').innerHTML = html;
    });

  let currentBlank = null;

  function openPopup(blank) {
    currentBlank = blank;
    document.getElementById('popup').style.display = 'flex';
  }

  function closePopup() {
    document.getElementById('popup').style.display = 'none';
  }

  function fill(letter) {
    currentBlank.textContent = letter;
    closePopup();
  }

  function check() {
    document.getElementById('result').textContent = 'Hotovo! Zkontroluj s učitelem.';
  }

  document.getElementById('mode-toggle').onclick = () => document.body.classList.toggle('dark');
</script>
