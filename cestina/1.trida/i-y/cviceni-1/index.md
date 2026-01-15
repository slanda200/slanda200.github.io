<script>
let currentBlank = null;
let answers = [];
let options = [];

// Načtení JSON cvičení
fetch("exercise.json")
  .then(res => res.json())
  .then(data => {
    document.querySelector("h1").textContent = data.title;
   document.getElementById("instruction").textContent = data.instruction;


    answers = data.answers;
    options = data.options;

    let blankIndex = 0;
    let html = "";

    data.text.forEach(line => {
      html += "<p>" + line.replace(/<>/g, () => {
        const index = blankIndex;
        blankIndex++;
        return `<span class="blank" data-index="${index}" onclick="openPopup(${index})">_</span>`;
      }) + "</p>";
    });

    document.getElementById("exercise-text").innerHTML = html;
  });

function openPopup(index) {
  currentBlank = index;
  document.getElementById("popup").style.display = "flex";

  let html = "";
  options.forEach(o => {
    html += `<button onclick="fill('${o}')">${o}</button>`;
  });
  document.getElementById("options").innerHTML = html;
}

function closePopup() {
  document.getElementById("popup").style.display = "none";
}

function fill(letter) {
  const blanks = document.querySelectorAll(".blank");
  blanks[currentBlank].textContent = letter;
  closePopup();
}

function checkAnswers() {
  const blanks = document.querySelectorAll(".blank");
  let correct = 0;
  let resultHtml = "";

  blanks.forEach((blank, i) => {
    const userAnswer = blank.textContent;

    if (userAnswer === "_") {
      blank.style.background = "#fde68a"; // žlutá
      resultHtml += `❗ Nevyplněno – pozice ${i + 1}<br>`;
    } else if (userAnswer === answers[i]) {
      blank.style.background = "#86efac"; // zelená
      correct++;
    } else {
      blank.style.background = "#fca5a5"; // červená
      resultHtml += `❌ Chyba ${i + 1}: správně je <b>${answers[i]}</b><br>`;
    }
  });

  const percent = Math.round((correct / answers.length) * 100);

  document.getElementById("result").innerHTML =
    `<b>Výsledek:</b> ${correct}/${answers.length} (${percent} %)<br><br>` +
    resultHtml;
}
</script>
