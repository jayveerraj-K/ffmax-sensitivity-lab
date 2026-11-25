FFMAX Sensitivity Lab

A single-file, mobile-friendly sensitivity calibration tool.

Complete Website

Save the following code as "index.html" if you want to run it as a website:

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FFMAX Sensitivity Lab</title>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  min-height: 100vh;
  font-family: Arial, sans-serif;
  color: #f4f7fb;
  background:
    radial-gradient(circle at top right, rgba(124,92,255,.25), transparent 35%),
    radial-gradient(circle at bottom left, rgba(0,212,255,.12), transparent 35%),
    #07090d;
}

.container {
  width: min(1000px, 92%);
  margin: auto;
}

header {
  padding: 24px 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  font-size: 22px;
  font-weight: 800;
}

.status {
  color: #7fffd4;
  font-size: 13px;
}

.hero {
  padding: 60px 0 35px;
}

.hero h1 {
  font-size: clamp(40px, 8vw, 75px);
  line-height: .95;
}

.hero p {
  margin-top: 20px;
  max-width: 650px;
  color: #8d98a8;
  line-height: 1.6;
}

.card {
  background: rgba(16,20,28,.9);
  border: 1px solid rgba(255,255,255,.08);
  border-radius: 22px;
  padding: 25px;
  margin-bottom: 20px;
}

.card h2 {
  margin-bottom: 20px;
}

.grid {
  display: grid;
  grid-template-columns: repeat(2,1fr);
  gap: 16px;
}

.field label {
  display: block;
  color: #8d98a8;
  font-size: 13px;
  margin-bottom: 8px;
}

select {
  width: 100%;
  padding: 13px;
  border-radius: 12px;
  border: 1px solid rgba(255,255,255,.08);
  background: #151b25;
  color: white;
}

.sensitivity {
  display: grid;
  gap: 18px;
}

.slider-row {
  display: grid;
  grid-template-columns: 110px 1fr 45px;
  align-items: center;
  gap: 15px;
}

.slider-value {
  text-align: right;
  font-weight: bold;
}

input[type="range"] {
  width: 100%;
  accent-color: #7c5cff;
}

.buttons {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  margin-top: 25px;
}

button {
  padding: 13px 20px;
  border: 0;
  border-radius: 12px;
  cursor: pointer;
  font-weight: bold;
  color: white;
  background: linear-gradient(135deg,#7c5cff,#00d4ff);
}

button.secondary {
  background: #151b25;
  border: 1px solid rgba(255,255,255,.08);
}

#result {
  margin-top: 20px;
  padding: 18px;
  border-radius: 14px;
  background: #0b0f16;
  white-space: pre-line;
  display: none;
}

.preset {
  padding: 15px;
  margin-top: 10px;
  border-radius: 13px;
  background: #151b25;
}

.preset small {
  display: block;
  color: #8d98a8;
  margin-top: 5px;
}

footer {
  text-align: center;
  padding: 35px 0;
  color: #8d98a8;
  font-size: 13px;
}

@media(max-width:650px) {
  .grid {
    grid-template-columns: 1fr;
  }

  .slider-row {
    grid-template-columns: 90px 1fr 40px;
    gap: 9px;
  }

  .card {
    padding: 19px;
  }
}
</style>
</head>

<body>

<div class="container">

<header>
  <div class="logo">FFMAX LAB</div>
  <div class="status">● OFFLINE READY</div>
</header>

<section class="hero">
  <h1>Find your<br>sweet spot.</h1>
  <p>
    Build a personalized Free Fire MAX sensitivity profile
    based on your device and preferred play style.
  </p>
</section>

<section class="card">

<h2>Device Setup</h2>

<div class="grid">

<div class="field">
<label>Screen Size</label>
<select id="screen">
<option>Small</option>
<option selected>Medium</option>
<option>Large</option>
</select>
</div>

<div class="field">
<label>DPI</label>
<select id="dpi">
<option>Low</option>
<option selected>Medium</option>
<option>High</option>
</select>
</div>

<div class="field">
<label>Play Style</label>
<select id="style">
<option>Balanced</option>
<option>Aggressive</option>
<option>Precision</option>
<option>Rush</option>
</select>
</div>

<div class="field">
<label>Main Focus</label>
<select id="focus">
<option>Headshots</option>
<option>Close Range</option>
<option>Long Range</option>
<option>All Round</option>
</select>
</div>

</div>
</section>

<section class="card">

<h2>Sensitivity</h2>

<div class="sensitivity">

<div class="slider-row">
<span>General</span>
<input id="general" type="range" min="0" max="100" value="90">
<span class="slider-value" id="generalValue">90</span>
</div>

<div class="slider-row">
<span>Red Dot</span>
<input id="redDot" type="range" min="0" max="100" value="85">
<span class="slider-value" id="redDotValue">85</span>
</div>

<div class="slider-row">
<span>2x Scope</span>
<input id="scope2x" type="range" min="0" max="100" value="80">
<span class="slider-value" id="scope2xValue">80</span>
</div>

<div class="slider-row">
<span>4x Scope</span>
<input id="scope4x" type="range" min="0" max="100" value="75">
<span class="slider-value" id="scope4xValue">75</span>
</div>

<div class="slider-row">
<span>Sniper</span>
<input id="sniper" type="range" min="0" max="100" value="55">
<span class="slider-value" id="sniperValue">55</span>
</div>

<div class="slider-row">
<span>Free Look</span>
<input id="freeLook" type="range" min="0" max="100" value="70">
<span class="slider-value" id="freeLookValue">70</span>
</div>

</div>

<div class="buttons">
<button onclick="generateProfile()">Generate Profile</button>
<button class="secondary" onclick="resetSettings()">Reset</button>
<button class="secondary" onclick="savePreset()">Save Preset</button>
</div>

<div id="result"></div>

</section>

<section class="card">

<h2>Saved Presets</h2>

<div id="presets">
No saved presets yet.
</div>

</section>

<footer>
FFMAX Sensitivity Lab · Independent calibration utility
</footer>

</div>

<script>

const sliders = [
  "general",
  "redDot",
  "scope2x",
  "scope4x",
  "sniper",
  "freeLook"
];

const defaults = {
  general: 90,
  redDot: 85,
  scope2x: 80,
  scope4x: 75,
  sniper: 55,
  freeLook: 70
};

function updateValue(id) {
  const input = document.getElementById(id);
  const output = document.getElementById(id + "Value");

  if (input && output) {
    output.textContent = input.value;
  }
}

function updateAllValues() {
  sliders.forEach(updateValue);
}

function getProfile() {
  const profile = {};

  sliders.forEach(id => {
    profile[id] =
      Number(document.getElementById(id).value);
  });

  return profile;
}

function generateProfile() {

  const p = getProfile();

  const result = `
GENERAL      : ${p.general}
RED DOT      : ${p.redDot}
2X SCOPE     : ${p.scope2x}
4X SCOPE     : ${p.scope4x}
SNIPER       : ${p.sniper}
FREE LOOK    : ${p.freeLook}
`;

  const box = document.getElementById("result");

  box.style.display = "block";
  box.textContent =
    "YOUR SENSITIVITY PROFILE\n\n" + result;

  navigator.clipboard
    .writeText(result)
    .catch(() => {});
}

function resetSettings() {

  sliders.forEach(id => {
    document.getElementById(id).value =
      defaults[id];
  });

  updateAllValues();

  document.getElementById("result").style.display =
    "none";
}

function savePreset() {

  const name =
    prompt("Enter a name for this preset:");

  if (!name) return;

  const presets =
    JSON.parse(
      localStorage.getItem("ffmax_presets") || "[]"
    );

  presets.push({
    name: name,
    profile: getProfile(),
    date: new Date().toLocaleString()
  });

  localStorage.setItem(
    "ffmax_presets",
    JSON.stringify(presets)
  );

  renderPresets();
}

function renderPresets() {

  const container =
    document.getElementById("presets");

  const presets =
    JSON.parse(
      localStorage.getItem("ffmax_presets") || "[]"
    );

  if (!presets.length) {
    container.textContent =
      "No saved presets yet.";
    return;
  }

  container.innerHTML = "";

  presets.forEach((preset,index) => {

    const div =
      document.createElement("div");

    div.className = "preset";

    div.innerHTML = `
      <strong>${escapeHTML(preset.name)}</strong>
      <small>${escapeHTML(preset.date)}</small>

      <div class="buttons">
        <button onclick="loadPreset(${index})">
          Load
        </button>

        <button
          class="secondary"
          onclick="deletePreset(${index})">
          Delete
        </button>
      </div>
    `;

    container.appendChild(div);
  });
}

function loadPreset(index) {

  const presets =
    JSON.parse(
      localStorage.getItem("ffmax_presets") || "[]"
    );

  const preset = presets[index];

  if (!preset) return;

  sliders.forEach(id => {

    if (preset.profile[id] !== undefined) {

      document.getElementById(id).value =
        preset.profile[id];

    }

  });

  updateAllValues();
}

function deletePreset(index) {

  const presets =
    JSON.parse(
      localStorage.getItem("ffmax_presets") || "[]"
    );

  presets.splice(index,1);

  localStorage.setItem(
    "ffmax_presets",
    JSON.stringify(presets)
  );

  renderPresets();
}

function escapeHTML(value) {

  return String(value)
    .replaceAll("&","&amp;")
    .replaceAll("<","&lt;")
    .replaceAll(">","&gt;")
    .replaceAll('"',"&quot;")
    .replaceAll("'","&#039;");
}

sliders.forEach(id => {

  document
    .getElementById(id)
    .addEventListener(
      "input",
      () => updateValue(id)
    );

});

updateAllValues();
renderPresets();

</script>

</body>
</html>

About

FFMAX Sensitivity Lab is an independent calibration and practice utility. It does not modify Free Fire MAX, automate gameplay, interact with game files, or bypass anti-cheat systems.

License

For personal and educational use.
