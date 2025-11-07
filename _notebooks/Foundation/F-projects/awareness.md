---
layout: post
title: "Awareness"
description: "First line of defense from foreign invaders"
permalink: /digital-famine/media-lit/submodule_1/
parent: "Analytics/Admin"
team: "Scratchers"
submodule: 1
categories: [CSP, Submodule, Analytics/Admin]
tags: [analytics, submodule, curators]
breadcrumb: true
author: "Aashika Patel, Varada Vichare"
date: 2025-10-21
---

# Awareness — Media Purpose Sorter 🎯

### Mission Briefing
The alien misinformation swarm has begun its first assault!  
They’ve hurled **different media signals** — some trying to *persuade*, some to *sell*, and others to *inform*.  
Your mission: **sort them correctly** before the confusion spreads across Media Literacy Planet.

Drag each piece of media into its correct bin — or use the *Autofill* ability to sort instantly.  
Score 7 points to level up your **Shield Level** and move on to the next defense — *Media Bias Detection*.

---

<style>
body {
  min-height: 100vh;
  background: url('{{ site.baseurl }}/hacks/digital-famine/media-lit/media/assets/spacebackground.jpg') no-repeat center center fixed;
  background-size: cover;
}
.game-container {
    background: linear-gradient(135deg, #353e74ff, #9384d5ff);
    border-radius: 15px;
    padding: 25px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.1);
    margin: 20px 0;
    font-family: system-ui, -apple-system, sans-serif;
}
.game-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
    padding-bottom: 15px;
    border-bottom: 2px solid rgba(255,255,255,0.5);
}
.player-info {
    display: flex;
    gap: 20px;
    align-items: center;
}
.info-pill {
    background: rgba(255,255,255,0.5);
    padding: 8px 15px;
    border-radius: 20px;
    font-weight: 600;
    color: #2c5282;
}
.bins-container {
    display: flex;
    justify-content: space-between;
    gap: 20px;
    margin: 20px 0;
}
.bin {
    flex: 1;
    min-height: 150px;
    background: rgba(255,255,255,0.4);
    border: 2px dashed #4299e1;
    border-radius: 10px;
    padding: 15px;
    transition: all 0.3s ease;
    display: flex;
    flex-direction: column;
    align-items: center;
}
.bin.highlight {
    background: rgba(255,255,255,0.6);
    border-color: #2b6cb0;
    transform: translateY(-2px);
    box-shadow: 0 5px 15px rgba(66,153,225,0.2);
}
.bin-label {
    font-weight: 600;
    color: #2c5282;
    margin-bottom: 10px;
}
.images-area {
    display: flex;
    flex-wrap: wrap;
    gap: 15px;
    padding: 20px;
    background: rgba(255,255,255,0.3);
    border-radius: 10px;
    min-height: 100px;
}
.image {
    width: 100px;
    height: 100px;
    object-fit: cover;
    padding: 8px;
    background: white;
    border-radius: 8px;
    box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    cursor: grab;
    transition: transform 0.2s ease, opacity 0.2s ease;
}
.image:hover { transform: translateY(-2px); }
.image.dragging { opacity: 0.5; transform: scale(0.95); }
.controls {
    display: flex;
    justify-content: flex-end;
    gap: 15px;
    margin-top: 20px;
}
.btn {
    padding: 10px 20px;
    border-radius: 8px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.2s ease;
    border: none;
}
.btn-primary { background: #4299e1; color: white; }
.btn-ghost { background: rgba(255,255,255,0.5); color: #2c5282; }
.btn:hover { transform: translateY(-1px); box-shadow: 0 2px 8px rgba(66,153,225,0.2); }
.leaderboard {
  background: linear-gradient(180deg, rgba(95, 73, 174, 0.18), rgba(60, 97, 156, 0.4));
  border-radius: 10px;
  padding: 20px;
  margin-top: 20px;
  color: #eaf6ff;
  border: 1px solid rgba(255,255,255,0.04);
}
.leaderboard-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 15px;
}
.leaderboard-table {
    width: 100%;
    border-collapse: collapse;
}
.leaderboard-table th,
.leaderboard-table td {
  padding: 10px;
  text-align: left;
  color: inherit;
}
.leaderboard-table tr:nth-child(even) {
  background: rgba(255,255,255,0.02);
}
</style>

<div class="game-container">
  <div class="game-header">
    <div class="player-info">
      <div class="info-pill" id="player-name">Player: Guest</div>
      <div class="info-pill" id="score">Score: 0</div>
    </div>
  </div>

  <div class="bins-container">
    <div class="bin" data-bin="Persuade">
      <div class="bin-label">Persuade 🧠</div>
      <div class="bin-content"></div>
    </div>
    <div class="bin" data-bin="Sell">
      <div class="bin-label">Sell 💰</div>
      <div class="bin-content"></div>
    </div>
    <div class="bin" data-bin="Inform">
      <div class="bin-label">Inform 📰</div>
      <div class="bin-content"></div>
    </div>
  </div>

  <div class="images-area" id="images"></div>

  <div class="controls">
    <button class="btn btn-ghost" id="reset-btn">Reset</button>
    <button class="btn btn-ghost" id="autofill-btn">Autofill</button>
    <button class="btn btn-primary" id="submit-btn">Submit Score</button>
  </div>

  <div class="leaderboard">
    <div class="leaderboard-header">
      <h3>Top Players</h3>
      <button class="btn btn-ghost" id="refresh-lb">Refresh</button>
    </div>
    <table class="leaderboard-table">
      <thead>
        <tr><th>Rank</th><th>Player</th><th>Score</th></tr>
      </thead>
      <tbody id="leaderboard-body"></tbody>
    </table>
  </div>
</div>

<script type="module">
import { javaURI, fetchOptions } from '{{site.baseurl}}/assets/js/api/config.js';

// --- CONFIGURATION ---
const IMAGE_BASE = '{{site.baseurl}}/hacks/digital-famine/media-lit/media/assets/';
const imageFiles = [
  { src: 'ad_coke.png', purpose: 'Sell' },
  { src: 'political_poster.png', purpose: 'Persuade' },
  { src: 'news_article.png', purpose: 'Inform' },
  { src: 'charity_campaign.png', purpose: 'Persuade' },
  { src: 'tech_ad.png', purpose: 'Sell' },
  { src: 'health_report.png', purpose: 'Inform' },
  { src: 'environment_petition.png', purpose: 'Persuade' },
  { src: 'store_sale.png', purpose: 'Sell' }
];

let score = 0;
let currentPlayer = 'Guest';
let placed = new Set();

// --- UI ELEMENTS ---
const bins = document.querySelectorAll('.bin');
const imagesArea = document.getElementById('images');
const scoreDisplay = document.getElementById('score');
const playerDisplay = document.getElementById('player-name');

// --- FUNCTIONS ---
function updateDisplays() {
  scoreDisplay.textContent = `Score: ${score}`;
  playerDisplay.textContent = `Player: ${currentPlayer}`;
}

function createImage(file, index) {
  const img = document.createElement('img');
  img.src = IMAGE_BASE + file.src;
  img.alt = file.purpose;
  img.className = 'image';
  img.draggable = true;
  img.dataset.purpose = file.purpose;
  img.dataset.id = `img-${index}`;

  img.addEventListener('dragstart', e => {
    if (placed.has(img.dataset.id)) e.preventDefault();
    img.classList.add('dragging');
    e.dataTransfer.setData('text/plain', img.dataset.id);
  });
  img.addEventListener('dragend', () => img.classList.remove('dragging'));

  return img;
}

function initGame() {
  imagesArea.innerHTML = '';
  document.querySelectorAll('.bin-content').forEach(el => el.innerHTML = '');
  placed.clear();
  score = 0;
  updateDisplays();

  const selected = imageFiles.sort(() => 0.5 - Math.random()).slice(0, 6);
  selected.forEach((file, i) => imagesArea.appendChild(createImage(file, i)));
}

bins.forEach(bin => {
  bin.addEventListener('dragover', e => { e.preventDefault(); bin.classList.add('highlight'); });
  bin.addEventListener('dragleave', () => bin.classList.remove('highlight'));
  bin.addEventListener('drop', e => {
    e.preventDefault();
    bin.classList.remove('highlight');
    const id = e.dataTransfer.getData('text/plain');
    const img = document.querySelector(`[data-id="${id}"]`);
    if (!img || placed.has(id)) return;

    if (img.dataset.purpose === bin.dataset.bin) {
      bin.querySelector('.bin-content').appendChild(img);
      placed.add(id);
      img.style.opacity = '0.6';
      score++;
      if (score >= 7) showShieldMessage();
    } else {
      img.animate([
        { transform: 'translateX(0)' },
        { transform: 'translateX(-5px)' },
        { transform: 'translateX(5px)' },
        { transform: 'translateX(0)' }
      ], { duration: 300 });
    }
    updateDisplays();
  });
});

function showShieldMessage() {
  const msg = document.createElement('div');
  msg.style.position = 'fixed';
  msg.style.top = '0';
  msg.style.left = '0';
  msg.style.width = '100vw';
  msg.style.height = '100vh';
  msg.style.background = 'rgba(0,0,0,0.6)';
  msg.style.display = 'flex';
  msg.style.alignItems = 'center';
  msg.style.justifyContent = 'center';
  msg.style.zIndex = '9999';
  msg.innerHTML = `
    <div style="background:#6a75c8ff;padding:36px;border-radius:18px;box-shadow:0 8px 32px #353e7444;text-align:center;max-width:420px;">
      <h2 style='color:#fff;margin-bottom:12px;'>Shield Level 1 Unlocked! 🛡️</h2>
      <div style='font-size:1.1rem;color:#cce4ff;margin-bottom:18px;'>You’ve successfully identified media purposes.<br>Move on to <b>Media Bias</b> training!</div>
      <a href="{{site.baseurl}}/digital-famine/media-lit/submodule_2/" style="padding:10px 18px;background:#4299e1;color:white;font-weight:700;border-radius:8px;text-decoration:none;">Go to Next Task</a>
    </div>`;
  document.body.appendChild(msg);
}

// Autofill
document.getElementById('autofill-btn').addEventListener('click', () => {
  document.querySelectorAll('.bin-content').forEach(el => el.innerHTML = '');
  placed.clear();
  score = 0;
  document.querySelectorAll('.image').forEach(img => {
    const bin = Array.from(bins).find(b => b.dataset.bin === img.dataset.purpose);
    bin.querySelector('.bin-content').appendChild(img);
    img.style.opacity = '0.6';
    placed.add(img.dataset.id);
    score++;
  });
  updateDisplays();
  if (score >= 7) showShieldMessage();
});

// Reset
document.getElementById('reset-btn').addEventListener('click', initGame);

// Submit + Leaderboard
async function fetchUser() {
  try {
    const res = await fetch(javaURI + '/api/person/get', fetchOptions);
    if (res.ok) {
      const data = await res.json();
      currentPlayer = data.name || data.username || 'Guest';
    }
  } catch {}
  updateDisplays();
}

async function postScore(user, score) {
  try {
    const res = await fetch(`${javaURI}/api/awareness/score/${encodeURIComponent(user)}/${score}`, { method: 'POST' });
    if (res.ok) fetchLeaderboard();
  } catch (err) { console.error(err); }
}

async function fetchLeaderboard() {
  const tbody = document.getElementById('leaderboard-body');
  try {
    const res = await fetch(javaURI + '/api/awareness/');
    const data = await res.json();
    tbody.innerHTML = '';
    data.forEach((e, i) => {
      const r = tbody.insertRow();
      r.insertCell().textContent = e.rank || i + 1;
      r.insertCell().textContent = e.username || 'Unknown';
      r.insertCell().textContent = e.score || 0;
    });
  } catch {
    tbody.innerHTML = '<tr><td colspan="3">Leaderboard unavailable</td></tr>';
  }
}

document.getElementById('submit-btn').addEventListener('click', () => {
  postScore(currentPlayer, score);
  if (score >= 7) showShieldMessage();
});
document.getElementById('refresh-lb').addEventListener('click', fetchLeaderboard);

// --- INIT ---
fetchUser();
initGame();
fetchLeaderboard();
setInterval(fetchLeaderboard, 30000);
</script>