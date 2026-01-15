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
      <p>Klikni na _ a vyber písmeno z vyskakovacího okénka.</p>

      <div class="task-box" id="exercise-text"></div>

      <div id="popup" class="modal">
        <div class="modal-content">
          <span onclick="closePopup()" class="close">&times;</span>
          <h3>Vyber písmeno</h3>
          <div id="options"></div>
        </div>
      </div>

      <button onclick="checkAnswers()">Zkontrolovat</button>
      <p id="result"></p>
    </main>
  </div>
</div>

<style>
  /* Skrýt default header */
  .site-header { display: none !important; }
  .top-bar { position: fixed; top: 0; width: 100%; z-index: 999; background: #e5e7eb; padding: 1rem 0; }
  .content-area { margin-top: 80px; display: flex; min-height: calc(100vh - 80px); }
  .main-content { flex: 1; padding: 4rem 3rem; max-width: 1200px; margin: 0 auto; width: 100%; }
  .task-box { padding: 2rem; background: #f1f5f9; border-radius: 12px; box-shadow: 0 4px 15px rgba(0,0,0,0.08); max-width: 700px; margin: 2rem auto; }
  .blank { background: yellow; padding: 0 0.2rem; cursor: pointer; }
  .modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.5); justify-content: center; align-items: center; }
  .modal-content { background: #f1f5f9; padding: 2rem; border-radius: 12px; max-width: 400px; width: 90%; text-align: center; }
  .close { float: right; font-size: 2rem; cursor: pointer; }
  #options button { margin: 0.5rem; padding: 1rem; font-size: 1.5rem; background: #64748b; color: white; border: none; border-radius: 8px; cursor: pointer; }
  button { padding: 0.8rem 1.5rem; background: #64748b; color: white; border: none; border-radius: 6px; cursor: pointer; margin-top: 1.5rem; }
  #result { font-weight: bold; margin-top: 1rem; color: green; }

  /* Dark mód */
  body.dark .task-box { background: #1e293b; }
  body.dark .modal-content { background: #1e293b; }
  body.dark #options button { background: #94a3b8; }
  body.dark { background: #0f172a; color: #e2e8f0; }
</style>

<script>
  let blanks = [];
  let spravne = [];
  let moznosti = ['i', 'y', 'í', 'ý']; // default, přepsá se z txt
  let currentBlank = null;

  // Načte cviceni.txt
  fetch('cviceni.txt')
    .then(r => r.text())
    .then(t => {
      const lines = t.split('\n');
      let html = '';
      lines.forEach(line => {
        if (line.startsWith('správné:')) {
          spravne.push(line.split(':')[1].trim());
        } else if (line.startsWith('možnosti:')) {
          moznosti = line.split(':')[1].split(',').map(o => o.trim());
        } else if (line.trim()) {
          html += `<p>${line.replace(/<>/g, () => {
            blanks.push(blanks.length);
            return '<span class="blank" onclick="openPopup(' + blanks.length + ')">_</span>';
          })}</p>`;
        }
      });
      document.getElementById('exercise-text').innerHTML = html;
    });

  function openPopup(index) {
    currentBlank = index - 1; // index blanků
    document.getElementById('popup').style.display = 'flex';
    let opts = '';
    moznosti.forEach(o => opts += `<button onclick="fill('${o}')">${o}</button>`);
    document.getElementById('options').innerHTML = opts;
  }

  function closePopup() {
    document.getElementById('popup').style.display = 'none';
  }

  function fill(pismeno) {
    const blankElements = document.querySelectorAll('.blank');
    blankElements[currentBlank].textContent = pismeno;
    closePopup();
  }

  function checkAnswers() {
    const blankElements = document.querySelectorAll('.blank');
    let result = '';
    let score = 0;
    blanks.forEach((_, i) => {
      if (blankElements[i].textContent === spravne[i]) {
        score++;
      } else {
        result += `Chyba v č. ${i+1}: správně je ${spravne[i]}<br>`;
      }
    });
    result = score === spravne.length ? 'Vše správně!' : `Správných: ${score}/${spravne.length}<br>${result}`;
    document.getElementById('result').innerHTML = result;
  }

  // Dark/light
  const toggle = document.getElementById('mode-toggle');
  if (localStorage.getItem('mode') === 'dark' || (!localStorage.getItem('mode') && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
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
