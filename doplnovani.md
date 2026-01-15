---
layout: default
title: Doplňování i/y a další
---

<h1>Doplňování – jednoduché cvičení</h1>

<p>Klikni na prázdné místo a vyber písmeno z okénka.</p>

<div id="text">
  M_l_ko je bílé. (mléko)<br>
  P_ták letí. (pták)<br>
  D_vka běží. (dívka)<br>
  H_ška je červená. (hýška)<br>
  L_st je zelený. (líst)
</div>

<!-- Vyskakovací okénko -->
<div id="popup" style="display:none; position:fixed; top:0; left:0; width:100%; height:100%; background:rgba(0,0,0,0.5); justify-content:center; align-items:center;">
  <div style="background:white; padding:2rem; border-radius:12px; text-align:center;">
    <h3>Vyber písmeno</h3>
    <button onclick="fill('i')" style="margin:0.5rem; padding:1rem; font-size:1.5rem;">i</button>
    <button onclick="fill('y')" style="margin:0.5rem; padding:1rem; font-size:1.5rem;">y</button>
    <button onclick="fill('í')" style="margin:0.5rem; padding:1rem; font-size:1.5rem;">í</button>
    <button onclick="fill('ý')" style="margin:0.5rem; padding:1rem; font-size:1.5rem;">ý</button>
    <br>
    <button onclick="closePopup()" style="margin-top:1rem;">Zavřít</button>
  </div>
</div>

<script>
let aktualniMisto = null;

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
