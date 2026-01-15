---
layout: default
title: Procvičovač – procvičuj zábavně
---

<div class="layout-container">
  <!-- Horní header – jen jedna lišta -->
  <header class="top-header">
    <div class="container">
      <a href="/" class="logo">Procvičovač</a>
      <div class="user-controls">
        <button id="mode-toggle" class="mode-btn" title="Přepnout režim">🌞</button>
        <a href="#" class="profile-link">Přihlásit se / Profil</a>
      </div>
    </div>
  </header>

  <!-- Hlavní obsah: sidebar + hlavní plocha -->
  <div class="main-wrapper">
    <!-- Levý sidebar -->
    <aside class="sidebar">
      <nav class="sidebar-nav">
        <ul>
          <li class="category">
            <a href="/cestina/" class="category-title">Čeština</a>
            <ul class="subcategories">
              {% for i in (1..9) %}
                <li><a href="/cestina/{{ i }}.trida/">{{ i }}. třída</a></li>
              {% endfor %}
              <li><a href="/cestina/stredni/">Střední škola</a></li>
            </ul>
          </li>
          <li><a href="/anglictina/" class="category-title">Angličtina</a></li>
          <li><a href="/matematika/" class="category-title">Matematika</a></li>
        </ul>
      </nav>
    </aside>

    <!-- Hlavní obsah (na indexu uvítací text) -->
    <main class="content">
      <h1>Vítej v Procvičovači!</h1>
      <p>Vyber si předmět v levém menu a začni procvičovat. Zábavně, zdarma a s přehledem tvého pokroku.</p>

      <!-- Prozatím teaser – můžeš sem dát něco interaktivního později -->
      <div class="teaser">
        <h2>Začni hned s češtinou</h2>
        <a href="/cestina/" class="btn">Přejít na češtinu</a>
      </div>
    </main>
  </div>
</div>

<style>
  :root {
    --bg: #f8f9fa;
    --text: #1f2937;
    --header-bg: #e5e7eb;
    --sidebar-bg: #f1f5f9;
    --sidebar-hover: #e2e8f0;
    --accent: #6b7280;
  }

  body.dark {
    --bg: #111827;
    --text: #f3f4f6;
    --header-bg: #1f2937;
    --sidebar-bg: #1e293b;
    --sidebar-hover: #334155;
    --accent: #9ca3af;
  }

  body { 
    background: var(--bg); 
    color: var(--text); 
    margin: 0; 
    font-family: system-ui, sans-serif; 
  }

  .top-header {
    background: var(--header-bg);
    padding: 1rem 0;
    position: sticky;
    top: 0;
    z-index: 100;
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
  }

  .container {
    max-width: 1400px;
    margin: 0 auto;
    padding: 0 1.5rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .logo {
    font-size: 1.8rem;
    font-weight: bold;
    color: var(--text);
    text-decoration: none;
  }

  .user-controls {
    display: flex;
    gap: 1.5rem;
    align-items: center;
  }

  .mode-btn { background: none; border: none; font-size: 1.6rem; cursor: pointer; }
  .profile-link {
    background: var(--accent);
    color: white;
    padding: 0.5rem 1rem;
    border-radius: 6px;
    text-decoration: none;
  }

  .main-wrapper {
    display: flex;
    min-height: calc(100vh - 70px); /* header výška ~70px */
  }

  .sidebar {
    width: 280px;
    background: var(--sidebar-bg);
    border-right: 1px solid var(--accent);
    padding: 2rem 1rem;
    position: sticky;
    top: 70px;
    height: calc(100vh - 70px);
    overflow-y: auto;
  }

  .sidebar-nav ul { list-style: none; padding: 0; margin: 0; }
  .category-title {
    display: block;
    padding: 1rem;
    font-size: 1.3rem;
    font-weight: bold;
    color: var(--text);
    text-decoration: none;
    border-radius: 8px;
    transition: background 0.2s;
  }
  .category-title:hover { background: var(--sidebar-hover); }

  .subcategories {
    list-style: none;
    padding-left: 1.5rem;
    max-height: 0;
    overflow: hidden;
    transition: max-height 0.4s ease;
  }

  .category.active .subcategories { max-height: 500px; } /* dost velký pro rozbalení */

  .subcategories li a {
    display: block;
    padding: 0.8rem 1rem;
    color: var(--text);
    text-decoration: none;
    border-radius: 6px;
  }
  .subcategories li a:hover { background: var(--sidebar-hover); }

  .content {
    flex: 1;
    padding: 4rem 3rem;
    max-width: 900px;
  }

  h1 { font-size: 2.8rem; margin-bottom: 1.5rem; }
  .teaser { margin-top: 4rem; text-align: center; }
  .btn {
    background: var(--accent);
    color: white;
    padding: 1rem 2rem;
    border-radius: 8px;
    text-decoration: none;
    font-size: 1.2rem;
  }

  @media (max-width: 992px) {
    .main-wrapper { flex-direction: column; }
    .sidebar { width: 100%; position: static; height: auto; border-right: none; border-bottom: 1px solid var(--accent); }
    .content { padding: 2rem 1.5rem; }
  }
</style>

<script>
// Rozbalování podkategorií (jen pro Češtinu na indexu)
document.querySelectorAll('.category-title').forEach(title => {
  title.addEventListener('click', (e) => {
    if (title.parentElement.classList.contains('category')) {
      e.preventDefault(); // zabrání okamžitému přechodu na /cestina/
      title.parentElement.classList.toggle('active');
    }
  });
});

// Dark/light mód (stejný jako dřív)
const toggleBtn = document.getElementById('mode-toggle');
if (localStorage.getItem('mode') === 'dark' || 
    (!localStorage.getItem('mode') && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
  document.body.classList.add('dark');
  toggleBtn.textContent = '🌙';
} else {
  toggleBtn.textContent = '🌞';
}

toggleBtn.addEventListener('click', () => {
  document.body.classList.toggle('dark');
  toggleBtn.textContent = document.body.classList.contains('dark') ? '🌙' : '🌞';
  localStorage.setItem('mode', document.body.classList.contains('dark') ? 'dark' : 'light');
});
</script>
