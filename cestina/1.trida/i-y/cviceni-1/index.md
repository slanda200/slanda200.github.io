---
layout: default
title: Čeština – 1. třída – Vybírání i/y – Cvičení 1
---

<div class="layout-wrapper">
  <!-- Tvá jediná horní lišta -->
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
      <h1>Vybírání i/y – Cvičení 1</h1>
      <p>Doplň tvrdé nebo měkké i/y do slov podle vyjmenovaných slov (např. mýlit = měkké ý, pýtka = tvrdé y). Klikni na "Zkontrolovat" pro vyhodnocení.</p>

      <div class="task-box">
        <p>1. M_l_ko je bílé. (nápověda: mysl na mýlit)</p>
        <input type="text" id="ans1" placeholder="i/y/í/ý" maxlength="1">

        <p>2. P_ták letí vysoko. (nápověda: mysl na pýtka)</p>
        <input type="text" id="ans2" placeholder="i/y/í/ý" maxlength="1">

        <p>3. D_vka jde do školy. (nápověda: mysl na dýka)</p>
        <input type="text" id="ans3" placeholder="i/y/í/ý" maxlength="1">

        <p>4. H_ška je červená. (nápověda: mysl na hýška)</p>
        <input type="text" id="ans4" placeholder="i/y/í/ý" maxlength="1">

        <p>5. L_st je zelený. (nápověda: mysl na lýst)</p>
        <input type="text" id="ans5" placeholder="i/y/í/ý" maxlength="1">

        <button onclick="checkAnswers()">Zkontrolovat</button>
        <p id="result"></p>
      </div>
    </main>
  </div>
</div>

<style>
  /* === SKRYJE DEFAULTNÍ MINIMA HEADERY === */
  .site-header,
  .header,
  .post-header,
  .page-header,
  header[role="banner"],
  #site-header,
  nav[role="navigation"],
  .banner,
  .masthead,
  .site-title,
  .header-inner,
  .masthead-inner,
  .page-title,
  .post-title {
    display: none !important;
  }

  .top-bar {
    display: flex !important;
    position: fixed !important;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 9999;
    box-shadow: 0 2px 10px rgba(0,0,0,0.15);
  }

  .content-area,
  main,
  .main-content {
    margin-top: 75px !important;
  }

  /* Tvé původní styly + pro úlohu */
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

  body {
    background: var(--bg);
    color: var(--text);
    margin: 0;
    font-family: system-ui, -apple-system, sans-serif;
  }

  .top-bar {
    background: var(--header-bg);
    padding: 1rem 0;
  }

  .container {
    max-width: 1600px;
    margin: 0 auto;
    padding: 0 2rem;
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
    align-items: center;
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
    font-size: 0.95rem;
  }

  .content-area {
    display: flex;
    min-height: calc(100vh - 65px);
  }

  .main-content {
    flex: 1;
    padding: 4rem 3rem;
    max-width: 1200px;
    margin: 0 auto;
    width: 100%;
  }

  h1 { font-size: 2.8rem; margin-bottom: 1.5rem; }
  p { font-size: 1.15rem; line-height: 1.6; max-width: 800px; }

  .task-box {
    padding: 2rem;
    background: var(--sidebar-bg);
    border-radius: 12px;
    box-shadow: 0 4px 15px rgba(0,0,0,0.08);
    max-width: 700px;
    margin: 2rem auto;
  }

  .task-box p { margin-bottom: 1rem; }
  .task-box input { padding: 0.5rem; border: 1px solid var(--accent); border-radius: 6px; width: 100px; }
  .task-box button { background: var(--accent); color: white; padding: 0.8rem 1.6rem; border: none; border-radius: 8px; cursor: pointer; margin-top: 1.5rem; }
  .task-box #result { font-weight: bold; margin-top: 1rem; color: green; }

  @media (max-width: 992px) {
    .main-content { padding: 2.5rem 1.5rem; }
  }
</style>

<script>
  // Funkce pro vyhodnocení odpovědí
  function checkAnswers() {
    const ans1 = document.getElementById('ans1').value.toLowerCase();
    const ans2 = document.getElementById('ans2').value.toLowerCase();
    const ans3 = document.getElementById('ans3').value.toLowerCase();
    const ans4 = document.getElementById('ans4').value.toLowerCase();
    const ans5 = document.getElementById('ans5').value.toLowerCase();

    let score = 0;
    let feedback = '';

    if (ans1 === 'í') { score++; } else { feedback += '1. Mílko = í (měkké)<br>'; }
    if (ans2 === 'y') { score++; } else { feedback += '2. Pýták = y (tvrdé)<br>'; }
    if (ans3 === 'ý') { score++; } else { feedback += '3. Dývka = ý (tvrdé)<br>'; }
    if (ans4 === 'ý') { score++; } else { feedback += '4. Hýška = ý (měkké)<br>'; }
    if (ans5 === 'í') { score++; } else { feedback += '5. Líst = í (měkké)<br>'; }

    const result = (score === 5) ? 'Vše správně! Dobrá práce.' : `Správných: ${score}/5<br>${feedback}`;

    document.getElementById('result').innerHTML = result;
  }

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
