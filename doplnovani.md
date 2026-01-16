---
layout: default
title: Doplňování i/y a další
---

<div class="page">
  <div class="navbar">
    <a href="/" class="logo">Procvičovač</a>
    <div class="nav-right">
      <button id="mode-toggle" class="mode-btn" title="Přepnout světlý / tmavý režim">🌞</button>
      <a href="#" class="profile-btn">Přihlásit se</a>
    </div>
  </div>

  <main class="container">
    <div class="card">
      <h1>Doplňování – jednoduché cvičení</h1>

      <p class="instruction">Klikni na prázdné místo a vyber písmeno z okénka.</p>

      <div id="text">
        M_l_ko je bílé. (mléko)<br>
        P_ták letí. (pták)<br>
        D_vka běží. (dívka)<br>
        H_ška je červená. (hýška)<br>
        L_st je zelený. (líst)
      </div>
    </div>
  </main>
</div>

<!-- Vyskakovací okénko -->
<div id="popup" class="modal">
  <div class="modal-content">
    <h3>Vyber písmeno</h3>
    <div class="options">
      <button onclick="fill('i')">i</button>
      <button onclick="fill('y')">y</button>
      <button onclick="fill('í')">í</button>
      <button onclick="fill('ý')">ý</button>
    </div>
    <button class="close-btn" onclick="closePopup()">Zavřít</button>
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
    --shadow: 0 10px 25px rgba(0,0,0,0.05);
  }

  body.dark {
    --bg: #0f172a;
    --card: #111827;
    --primary: #60a5fa;
    --muted: #cbd5f5;
    --line: #1f2937;
    --shadow: 0 12px 30px rgba(15, 23, 42, 0.35);
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

  .container {
    max-width: 900px;
    margin: 2.5rem auto;
    padding: 0 1.5rem;
    width: 100%;
  }

  .card {
    background: var(--card);
    padding: 2rem;
    border-radius: 16px;
    box-shadow: var(--shadow);
  }

  .instruction {
    color: var(--muted);
    margin-bottom: 1.5rem;
  }

  #text {
    line-height: 1.8;
    font-size: 1.1rem;
  }

  .modal {
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.5);
    justify-content: center;
    align-items: center;
    z-index: 1000;
  }

  .modal-content {
    background: var(--card);
    padding: 1.8rem;
    border-radius: 14px;
    text-align: center;
    min-width: 260px;
  }

  .options {
    display: flex;
    justify-content: center;
    gap: 0.6rem;
    margin: 1rem 0;
    flex-wrap: wrap;
  }

  .options button {
    font-size: 1.4rem;
    padding: 0.6rem 1.2rem;
    border-radius: 8px;
    border: none;
    cursor: pointer;
    background: #e5e7eb;
  }

  body.dark .options button {
    background: #1f2937;
    color: #e2e8f0;
  }

  .close-btn {
    border: none;
    background: var(--primary);
    color: white;
    padding: 0.6rem 1.2rem;
    border-radius: 8px;
    cursor: pointer;
  }
</style>

<script>
let aktualniMisto = null;

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

document.querySelectorAll('#text span').forEach(span => {
  span.onclick = () => {
    aktualniMisto = span;
    document.getElementById('popup').style.display = 'flex';
  };
});

function fill(pismeno) {
  if (aktualniMisto) {
    aktualniMisto.textContent = pismeno.toUpperCase();
    aktualniMisto.style.background = 'lightgreen';
  }
  closePopup();
}

function closePopup() {
  document.getElementById('popup').style.display = 'none';
}
</script>
