---
title: Citation Blitz
comments: true
hide: true
layout: base
description: Arcade citation card game — click the correctly formatted citation before time runs out!
permalink: /citation-blitz/
---

<style>
@import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&family=Syne:wght@600;800&family=Space+Mono:ital,wght@0,400;0,700;1,400&display=swap');

/* ── Tokens ── */
:root {
  --bg:        #060810;
  --surface:   #0c1020;
  --card-bg:   #0f1830;
  --border:    rgba(100,130,255,0.18);
  --cyan:      #22d3ee;
  --green:     #4ade80;
  --red:       #f43f5e;
  --gold:      #fbbf24;
  --text:      #e2e8f0;
  --muted:     #64748b;
  --arcade:    'Press Start 2P', monospace;
  --ui:        'Syne', sans-serif;
  --cite:      'Space Mono', monospace;
}

#blitz-root *, #blitz-root *::before, #blitz-root *::after {
  box-sizing: border-box; margin: 0; padding: 0;
}

/* scanline texture overlay */
#blitz-root::before {
  content: '';
  position: fixed;
  inset: 0;
  background: repeating-linear-gradient(
    0deg,
    transparent,
    transparent 2px,
    rgba(0,0,0,0.03) 2px,
    rgba(0,0,0,0.03) 4px
  );
  pointer-events: none;
  z-index: 9999;
}

#blitz-root {
  background: var(--bg);
  color: var(--text);
  font-family: var(--ui);
  min-height: 80vh;
  padding: 1.5rem 1rem 4rem;
  position: relative;
}

/* ── Screen switching ── */
.blitz-screen { display: none; }
.blitz-screen.active { display: block; }

/* ════════════════════════════════
   START SCREEN
════════════════════════════════ */
#screen-start {
  text-align: center;
  max-width: 600px;
  margin: 0 auto;
  padding-top: 2rem;
}

.blitz-logo {
  font-family: var(--arcade);
  font-size: clamp(.9rem, 3.5vw, 1.4rem);
  color: var(--cyan);
  text-shadow: 0 0 30px rgba(34,211,238,.6), 0 0 60px rgba(34,211,238,.3);
  margin-bottom: .4rem;
  letter-spacing: .04em;
}
.blitz-logo span { color: var(--gold); }

.blitz-sub {
  font-family: var(--arcade);
  font-size: clamp(.45rem, 1.5vw, .6rem);
  color: var(--muted);
  letter-spacing: .06em;
  margin-bottom: 2.5rem;
}

.how-box {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 12px;
  padding: 1.4rem;
  text-align: left;
  margin-bottom: 2rem;
}
.how-box h3 {
  font-family: var(--arcade);
  font-size: .55rem;
  color: var(--cyan);
  letter-spacing: .08em;
  margin-bottom: 1rem;
}
.how-box li {
  font-size: .85rem;
  color: var(--muted);
  margin-bottom: .55rem;
  list-style: none;
  padding-left: 1.4rem;
  position: relative;
  line-height: 1.5;
}
.how-box li::before { content: '▶'; position: absolute; left: 0; color: var(--cyan); font-size: .7rem; top: 2px; }

.style-chips { display: flex; gap: .6rem; justify-content: center; flex-wrap: wrap; margin-bottom: 1.8rem; }
.chip {
  padding: .45rem 1rem;
  border-radius: 99px;
  border: 1.5px solid var(--border);
  background: transparent;
  color: var(--muted);
  font-family: var(--arcade);
  font-size: .48rem;
  letter-spacing: .04em;
  cursor: pointer;
  transition: all .15s;
}
.chip.selected, .chip:hover {
  border-color: var(--cyan);
  color: var(--cyan);
  background: rgba(34,211,238,.08);
  box-shadow: 0 0 14px rgba(34,211,238,.2);
}

.btn-start {
  display: inline-block;
  padding: 1rem 2.8rem;
  background: var(--cyan);
  color: #060810;
  border: none;
  border-radius: 8px;
  font-family: var(--arcade);
  font-size: .8rem;
  letter-spacing: .04em;
  cursor: pointer;
  box-shadow: 0 0 30px rgba(34,211,238,.4), 0 4px 20px rgba(0,0,0,.4);
  transition: transform .1s, box-shadow .1s;
  animation: pulseCTA 2s ease-in-out infinite;
}
.btn-start:hover { transform: translateY(-2px); box-shadow: 0 0 44px rgba(34,211,238,.55), 0 6px 28px rgba(0,0,0,.5); }
.btn-start:active { transform: translateY(1px); }

@keyframes pulseCTA {
  0%,100% { box-shadow: 0 0 30px rgba(34,211,238,.4), 0 4px 20px rgba(0,0,0,.4); }
  50%      { box-shadow: 0 0 48px rgba(34,211,238,.65), 0 4px 20px rgba(0,0,0,.4); }
}

/* ════════════════════════════════
   GAME SCREEN
════════════════════════════════ */
#screen-game { max-width: 680px; margin: 0 auto; }

/* HUD bar */
.hud {
  display: flex;
  align-items: center;
  gap: .75rem;
  margin-bottom: 1.2rem;
  flex-wrap: wrap;
}
.hud-pill {
  font-family: var(--arcade);
  font-size: .55rem;
  padding: .38rem .8rem;
  border-radius: 99px;
  border: 1.5px solid var(--border);
  letter-spacing: .04em;
  white-space: nowrap;
}
.hud-round { color: var(--cyan);  border-color: rgba(34,211,238,.3); }
.hud-lives { color: var(--red);   border-color: rgba(244,63,94,.3); }
.hud-score { color: var(--gold);  border-color: rgba(251,191,36,.3); }

/* Source info card */
.source-card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 10px;
  padding: 1rem 1.2rem;
  margin-bottom: .9rem;
}
.source-card-header {
  display: flex;
  align-items: center;
  gap: .75rem;
  margin-bottom: .75rem;
}
.source-label {
  font-family: var(--arcade);
  font-size: .48rem;
  color: var(--muted);
  letter-spacing: .06em;
}
.style-badge {
  font-family: var(--arcade);
  font-size: .5rem;
  padding: .28rem .7rem;
  border-radius: 4px;
  letter-spacing: .06em;
  margin-left: auto;
}
.badge-apa     { background: rgba(34,211,238,.15); color: var(--cyan); }
.badge-mla     { background: rgba(74,222,128,.15); color: var(--green); }
.badge-chicago { background: rgba(251,191,36,.15); color: var(--gold); }

.source-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: .3rem .8rem;
  font-size: .82rem;
}
.source-row { display: flex; gap: .5rem; align-items: baseline; }
.src-key {
  font-family: var(--cite);
  font-size: .65rem;
  color: var(--muted);
  flex-shrink: 0;
  min-width: 52px;
}
.src-val { color: var(--text); line-height: 1.4; font-size: .82rem; }

/* Timer */
.timer-wrap {
  height: 7px;
  background: rgba(255,255,255,.08);
  border-radius: 99px;
  overflow: hidden;
  margin-bottom: 1rem;
}
.timer-bar {
  height: 100%;
  border-radius: 99px;
  background: var(--cyan);
  transition: width .1s linear, background .3s;
}
.timer-bar.warn  { background: var(--gold); }
.timer-bar.crit  { background: var(--red); animation: timerPulse .4s ease-in-out infinite; }

@keyframes timerPulse { 0%,100% { opacity:1; } 50% { opacity:.5; } }

/* Citation card grid — 2x2 */
.cards-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: .75rem;
  margin-bottom: 1rem;
}

.cite-card {
  background: var(--card-bg);
  border: 1.5px solid var(--border);
  border-radius: 10px;
  padding: .9rem 1rem;
  cursor: pointer;
  transition: border-color .15s, box-shadow .15s, transform .12s;
  animation: dealIn .35s cubic-bezier(.34,1.56,.64,1) both;
  position: relative;
  min-height: 110px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.cite-card:nth-child(1) { animation-delay: .0s; }
.cite-card:nth-child(2) { animation-delay: .07s; }
.cite-card:nth-child(3) { animation-delay: .14s; }
.cite-card:nth-child(4) { animation-delay: .21s; }

@keyframes dealIn {
  from { opacity:0; transform: scale(.7) translateY(20px); }
  to   { opacity:1; transform: scale(1) translateY(0); }
}

.cite-card:hover:not(:disabled):not(.locked) {
  border-color: rgba(34,211,238,.5);
  box-shadow: 0 0 20px rgba(34,211,238,.12);
  transform: translateY(-2px);
}

.cite-card.locked { pointer-events: none; }
.cite-card.correct {
  border-color: var(--green) !important;
  box-shadow: 0 0 24px rgba(74,222,128,.25) !important;
  animation: correctPop .4s ease;
}
.cite-card.wrong {
  border-color: var(--red) !important;
  background: rgba(244,63,94,.08) !important;
  animation: wrongShake .4s ease;
}
.cite-card.fade { opacity: .3; }

@keyframes correctPop {
  0%   { transform: scale(1); }
  40%  { transform: scale(1.04); }
  100% { transform: scale(1); }
}
@keyframes wrongShake {
  0%,100% { transform: translateX(0); }
  20%      { transform: translateX(-7px); }
  40%      { transform: translateX(7px); }
  60%      { transform: translateX(-5px); }
  80%      { transform: translateX(5px); }
}

.card-letter {
  font-family: var(--arcade);
  font-size: .5rem;
  color: var(--muted);
  margin-bottom: .55rem;
  letter-spacing: .04em;
}
.card-cite-text {
  font-family: var(--cite);
  font-size: .72rem;
  line-height: 1.55;
  color: var(--text);
  flex: 1;
}
.card-cite-text em { font-style: italic; }

.card-result-icon {
  position: absolute;
  top: .6rem;
  right: .7rem;
  font-size: 1rem;
  display: none;
}

/* Feedback banner */
.feedback-bar {
  text-align: center;
  padding: .7rem 1rem;
  border-radius: 8px;
  font-family: var(--arcade);
  font-size: .55rem;
  letter-spacing: .04em;
  margin-bottom: .9rem;
  display: none;
  animation: fadeSlideUp .2s ease;
}
@keyframes fadeSlideUp { from { opacity:0; transform:translateY(8px); } to { opacity:1; transform:translateY(0); } }
.feedback-bar.correct { background: rgba(74,222,128,.15); color: var(--green); border: 1px solid rgba(74,222,128,.3); }
.feedback-bar.wrong   { background: rgba(244,63,94,.15);  color: var(--red);   border: 1px solid rgba(244,63,94,.3); }
.feedback-bar.timeout { background: rgba(251,191,36,.12); color: var(--gold);  border: 1px solid rgba(251,191,36,.3); }

.btn-next {
  width: 100%;
  padding: .75rem;
  background: rgba(34,211,238,.12);
  border: 1.5px solid var(--cyan);
  border-radius: 8px;
  color: var(--cyan);
  font-family: var(--arcade);
  font-size: .58rem;
  letter-spacing: .05em;
  cursor: pointer;
  display: none;
  transition: background .15s;
}
.btn-next:hover { background: rgba(34,211,238,.22); }

/* ════════════════════════════════
   END SCREEN
════════════════════════════════ */
#screen-end {
  text-align: center;
  max-width: 520px;
  margin: 2rem auto 0;
}
.end-title {
  font-family: var(--arcade);
  font-size: clamp(.8rem, 2.5vw, 1.1rem);
  margin-bottom: .5rem;
  letter-spacing: .04em;
}
.end-score-big {
  font-family: var(--arcade);
  font-size: clamp(2rem, 8vw, 3.8rem);
  color: var(--gold);
  text-shadow: 0 0 40px rgba(251,191,36,.5);
  display: block;
  margin: .8rem 0 .3rem;
  animation: scorePop .5s cubic-bezier(.34,1.56,.64,1);
}
@keyframes scorePop { from { transform:scale(.5); opacity:0; } to { transform:scale(1); opacity:1; } }
.end-grade {
  font-family: var(--arcade);
  font-size: .6rem;
  color: var(--muted);
  margin-bottom: 1.8rem;
}

.end-results {
  text-align: left;
  margin-bottom: 1.8rem;
}
.end-result-row {
  display: flex;
  align-items: baseline;
  gap: .75rem;
  padding: .55rem .9rem;
  border-radius: 6px;
  margin-bottom: .4rem;
  background: var(--surface);
  border: 1px solid var(--border);
  font-size: .82rem;
  animation: dealIn .3s ease both;
}
.end-result-row:nth-child(1) { animation-delay:.1s }
.end-result-row:nth-child(2) { animation-delay:.18s }
.end-result-row:nth-child(3) { animation-delay:.26s }
.end-result-row:nth-child(4) { animation-delay:.34s }
.end-result-row:nth-child(5) { animation-delay:.42s }
.er-pts {
  font-family: var(--arcade);
  font-size: .48rem;
  white-space: nowrap;
  flex-shrink: 0;
}
.er-pts.ok  { color: var(--green); }
.er-pts.bad { color: var(--red); }
.er-title { color: var(--muted); }
.er-style {
  font-family: var(--arcade);
  font-size: .42rem;
  color: var(--cyan);
  margin-left: auto;
  flex-shrink: 0;
}

.btn-again {
  padding: .85rem 2.5rem;
  background: var(--cyan);
  color: #060810;
  border: none;
  border-radius: 8px;
  font-family: var(--arcade);
  font-size: .7rem;
  letter-spacing: .04em;
  cursor: pointer;
  box-shadow: 0 0 28px rgba(34,211,238,.35);
  transition: transform .1s;
}
.btn-again:hover { transform: translateY(-2px); }
</style>

<!-- ════════════════════════════════════════════════════════
     CITATION BLITZ
     Purpose: Arcade card game — click the correctly
     formatted citation before the timer hits zero.
     Teaches APA, MLA, and Chicago formatting patterns
     through fast-paced, pressured recognition rounds.
════════════════════════════════════════════════════════ -->
<div id="blitz-root">

  <!-- ── START SCREEN ── -->
  <div id="screen-start" class="blitz-screen active">
    <h1 class="blitz-logo">CITATION <span>BLITZ</span></h1>
    <p class="blitz-sub">spot · click · score</p>

    <div class="how-box">
      <h3>▌ How To Play</h3>
      <ul>
        <li>A source (author, date, title, publication) appears with a required format</li>
        <li>4 citation cards deal out — only ONE is correctly formatted</li>
        <li>Click the correct card before the timer runs out</li>
        <li>Wrong click or timeout = lose a life ❤️ · You start with 3</li>
        <li>5 rounds · up to 150 pts each (100 base + time bonus)</li>
      </ul>
    </div>

    <!-- INPUT: user picks a practice mode -->
    <div class="style-chips">
      <button class="chip selected" data-style="random">🎲 Random</button>
      <button class="chip" data-style="apa">APA Only</button>
      <button class="chip" data-style="mla">MLA Only</button>
      <button class="chip" data-style="chicago">Chicago Only</button>
    </div>

    <button class="btn-start" id="btn-start">INSERT COIN →</button>
  </div>

  <!-- ── GAME SCREEN ── -->
  <div id="screen-game" class="blitz-screen">

    <!-- OUTPUT: heads-up display -->
    <div class="hud">
      <div class="hud-pill hud-round" id="hud-round">RND 1/5</div>
      <div class="hud-pill hud-lives" id="hud-lives">❤️ 3</div>
      <div class="hud-pill hud-score" id="hud-score">⭐ 0</div>
    </div>

    <!-- OUTPUT: source info shown to player -->
    <div class="source-card">
      <div class="source-card-header">
        <span class="source-label">SOURCE INFO</span>
        <span class="style-badge" id="style-badge">APA</span>
      </div>
      <div class="source-grid">
        <div class="source-row"><span class="src-key">Author</span><span class="src-val" id="si-author">—</span></div>
        <div class="source-row"><span class="src-key">Date</span>  <span class="src-val" id="si-date">—</span></div>
        <div class="source-row"><span class="src-key">Title</span> <span class="src-val" id="si-title">—</span></div>
        <div class="source-row"><span class="src-key">Source</span><span class="src-val" id="si-source">—</span></div>
      </div>
    </div>

    <!-- OUTPUT: timer bar drains in real time -->
    <div class="timer-wrap"><div class="timer-bar" id="timer-bar"></div></div>

    <!-- OUTPUT: 4 citation cards rendered here -->
    <div class="cards-grid" id="cards-grid"></div>

    <!-- OUTPUT: feedback after click or timeout -->
    <div class="feedback-bar" id="feedback-bar"></div>
    <button class="btn-next" id="btn-next">NEXT ROUND ▶</button>
  </div>

  <!-- ── END SCREEN ── -->
  <div id="screen-end" class="blitz-screen">
    <div class="end-title" id="end-title">GAME OVER</div>
    <span class="end-score-big" id="end-score">0</span>
    <p class="end-grade" id="end-grade">out of 750 pts</p>
    <div class="end-results" id="end-results"></div>
    <button class="btn-again" id="btn-again">PLAY AGAIN →</button>
  </div>

</div><!-- #blitz-root -->

<script>
/* =====================================================================
   CITATION BLITZ — game script
   Purpose : Arcade card game teaching citation formatting.
   AI Credit: AI (Claude) assisted with debugging the buildCitation
              procedure's formatting rules and parenthetical logic.
              Game loop, timer, card rendering, and distractor
              generation were written by the student.
   ===================================================================== */

// ════════════════════════════════════════════════════════════════
// LIST REQUIREMENT
// SOURCES is the primary collection — an array of 8 source objects
// the game randomly draws from each playthrough.
// gameRounds and results are also lists built/used at runtime.
// ════════════════════════════════════════════════════════════════
const SOURCES = [
  { author: "Patel, R.",    date: "2022, March 14",    title: "AI in classrooms",         source: "Education Weekly",    url: "https://educationweekly.com" },
  { author: "Kim, S.",      date: "2023, July 8",      title: "Ocean plastic wildlife",    source: "National Geographic", url: "https://natgeo.com" },
  { author: "Torres, M.",   date: "2021, November 2",  title: "Social media & teen health",source: "The Atlantic",        url: "https://theatlantic.com" },
  { author: "Chen, L.",     date: "2024, January 19",  title: "Renewable energy trends",   source: "BBC News",            url: "https://bbc.com/energy" },
  { author: "Williams, A.", date: "2020, April 30",    title: "Voter turnout patterns",    source: "The Guardian",        url: "https://theguardian.com" },
  { author: "Nguyen, T.",   date: "2022, September 5", title: "Urban farming solutions",   source: "Bloomberg",           url: "https://bloomberg.com" },
  { author: "Okafor, E.",   date: "2023, February 22", title: "Bias in hiring algorithms", source: "MIT Tech Review",     url: "https://technologyreview.com" },
  { author: "Lopez, J.",    date: "2021, August 11",   title: "Psychology of fake news",   source: "Scientific American", url: "https://scientificamerican.com" }
];

// Game constants
const TOTAL_ROUNDS  = 5;
const MAX_LIVES     = 3;
const BASE_PTS      = 100;
const MAX_TIME_BONUS = 50;
const ALL_STYLES    = ['apa', 'mla', 'chicago'];

// Timer speeds (ms) per level — gets faster each round
const ROUND_TIME_MS = [10000, 9000, 8000, 7000, 6000];

// ════════════════════════════════════════════════════════════════
// PROCEDURE REQUIREMENT
//
// Name        : buildCitation
// Return type : Object  { citation: string, parenthetical: string }
// Parameters  :
//   author (string) – "Last, First" formatted author name
//   date   (string) – publication date string
//   title  (string) – article or page title
//   source (string) – publication / website name
//   url    (string) – source URL
//   style  (string) – "apa" | "mla" | "chicago"
//
// AI Credit: AI assisted with debugging formatting rules
//            and writing the parenthetical citation logic.
//
// ALGORITHM — the body of this procedure contains:
//   SEQUENCING  : parts always assembled in a fixed, deliberate order
//   SELECTION   : if/else branches apply different style rules
//   ITERATION   : a for-loop joins non-empty parts into one string
// ════════════════════════════════════════════════════════════════
function buildCitation(author, date, title, source, url, style) {

  // ── SEQUENCING Step 1: build the parts list for this style ──
  let parts = [];

  // ── SELECTION: different citation rules per style ──
  if (style === 'apa') {
    // APA: Author. (Date). Title. *Source*. URL
    if (author) parts.push(author + '.');
    if (date)   parts.push('(' + date + ').');
    if (title)  parts.push(title + '.');
    if (source) parts.push('<em>' + source + '</em>.');
    if (url)    parts.push(url);

  } else if (style === 'mla') {
    // MLA 9th ed.: Author. "Title." *Source*, Date, URL.
    if (author) parts.push(author + '.');
    if (title)  parts.push('"' + title + '."');
    if (source) parts.push('<em>' + source + '</em>,');
    if (date)   parts.push(date + ',');
    if (url)    parts.push(url + '.');

  } else {
    // Chicago author-date: Author. "Title." (Date). *Source*. URL
    if (author) parts.push(author + '.');
    if (title)  parts.push('"' + title + '."');
    if (date)   parts.push('(' + date + ').');
    if (source) parts.push('<em>' + source + '</em>.');
    if (url)    parts.push(url);
  }

  // ── SEQUENCING Step 2: build parenthetical citation ──
  const yearMatch = date ? date.match(/\d{4}/) : null;
  const year      = yearMatch ? yearMatch[0] : '';
  const lastName  = author ? author.split(',')[0].trim() : '';

  let parenthetical = '';
  if (style === 'mla') {
    parenthetical = lastName ? '(' + lastName + ')' : '';
  } else if (style === 'chicago') {
    parenthetical = (lastName && year) ? '(' + lastName + ' ' + year + ')' : '';
  } else {
    parenthetical = (lastName && year) ? '(' + lastName + ', ' + year + ')' : '';
  }

  // ── ITERATION Step 3: loop over parts, skip blanks, join ──
  let citation = '';
  for (let i = 0; i < parts.length; i++) {
    // SELECTION inside iteration: skip any empty/whitespace part
    if (parts[i] && parts[i].trim() !== '') {
      citation += (citation ? ' ' : '') + parts[i];
    }
  }

  // ── SEQUENCING Step 4: return assembled result ──
  return { citation, parenthetical };
}
// ══════════════════ END PROCEDURE ══════════════════


// ── Shuffle array in place (Fisher-Yates) ──
function shuffle(arr) {
  for (let i = arr.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [arr[i], arr[j]] = [arr[j], arr[i]];
  }
  return arr;
}

// ── Pick n items at random from an array ──
function pick(arr, n) { return shuffle([...arr]).slice(0, n); }

// ── Build 3 wrong-answer distractor strings for one source + style ──
// (Also calls buildCitation internally, so the procedure is called 3+ times per round)
// AI Credit: student wrote distractor logic; AI helped debug the scrambled variant.
function makeDistractors(src, correctStyle) {
  const { author, date, title, source, url } = src;
  const wrong = [];

  // Distractor A: correct content, different style — teaches by contrast
  const others = ALL_STYLES.filter(s => s !== correctStyle);
  wrong.push(buildCitation(author, date, title, source, url, others[0]).citation);

  // Distractor B: third style
  wrong.push(buildCitation(author, date, title, source, url, others[1]).citation);

  // Distractor C: same style, deliberate punctuation / order mistake
  let badParts = [];
  if (correctStyle === 'apa') {
    // Common APA mistake: title before date, missing parentheses
    if (author) badParts.push(author + '.');
    if (title)  badParts.push(title + '.');       // title first — wrong order
    if (date)   badParts.push(date + '.');         // no parentheses around date
    if (source) badParts.push('<em>' + source + '</em>.');
    if (url)    badParts.push(url);
  } else if (correctStyle === 'mla') {
    // Common MLA mistake: date before title
    if (author) badParts.push(author + '.');
    if (date)   badParts.push(date + ',');         // date moved up — wrong order
    if (title)  badParts.push('"' + title + '."');
    if (source) badParts.push('<em>' + source + '</em>,');
    if (url)    badParts.push(url + '.');
  } else {
    // Common Chicago mistake: title not quoted
    if (author) badParts.push(author + '.');
    if (title)  badParts.push(title + '.');        // missing quote marks
    if (date)   badParts.push('(' + date + ').');
    if (source) badParts.push('<em>' + source + '</em>.');
    if (url)    badParts.push(url);
  }
  wrong.push(badParts.join(' '));

  return wrong;
}


// ════════════════════════════════════════════
// GAME STATE
// ════════════════════════════════════════════
let practiceStyle = 'random';
let gameRounds    = [];   // LIST: one object per round
let results       = [];   // LIST: outcome per round
let currentRound  = 0;
let lives         = MAX_LIVES;
let score         = 0;
let timerInterval = null;
let timeLeft      = 0;
let roundLocked   = false;


// ── Style chip INPUT ──
document.querySelectorAll('.chip').forEach(chip => {
  chip.addEventListener('click', function () {
    document.querySelectorAll('.chip').forEach(c => c.classList.remove('selected'));
    this.classList.add('selected');
    practiceStyle = this.dataset.style;
  });
});

// INPUT: Start button
document.getElementById('btn-start').addEventListener('click', startGame);

// INPUT: Next round button
document.getElementById('btn-next').addEventListener('click', advanceRound);

// INPUT: Play again button
document.getElementById('btn-again').addEventListener('click', startGame);


// ════════════════════════════════════════════
// CALL TO PROCEDURE: startGame
// Builds the gameRounds LIST, then calls loadRound
// which calls buildCitation for every round's options.
// ════════════════════════════════════════════
function startGame() {
  lives  = MAX_LIVES;
  score  = 0;
  results = [];
  currentRound = 0;

  // BUILD gameRounds list — pick 5 random sources + assign a style each
  const chosen = pick(SOURCES, TOTAL_ROUNDS);
  gameRounds = chosen.map((src, i) => {
    // SELECTION: which style does this round test?
    const style = (practiceStyle === 'random')
      ? ALL_STYLES[i % ALL_STYLES.length]
      : practiceStyle;
    return { src, style };
  });
  shuffle(gameRounds);

  showScreen('screen-game');
  loadRound(0);
}


// ── Set up one round ──
function loadRound(idx) {
  roundLocked = false;
  const { src, style } = gameRounds[idx];

  // OUTPUT: update HUD
  document.getElementById('hud-round').textContent = 'RND ' + (idx + 1) + '/' + TOTAL_ROUNDS;
  document.getElementById('hud-lives').textContent = '❤️ ' + lives;
  document.getElementById('hud-score').textContent = '⭐ ' + score;

  // OUTPUT: fill source info card
  document.getElementById('si-author').textContent = src.author;
  document.getElementById('si-date').textContent   = src.date;
  document.getElementById('si-title').textContent  = src.title;
  document.getElementById('si-source').textContent = src.source;

  // Style badge
  const badge = document.getElementById('style-badge');
  badge.textContent = style.toUpperCase();
  badge.className   = 'style-badge badge-' + style;

  // ── CALL TO buildCitation (developed procedure) ──
  // Generate the correct answer for this round
  const correct = buildCitation(src.author, src.date, src.title, src.source, src.url, style).citation;

  // Generate 3 wrong distractors (each also calls buildCitation internally)
  const wrongs  = makeDistractors(src, style);

  // Build the choices LIST for this round — 1 correct + 3 wrong, shuffled
  const choices = shuffle([
    { html: correct, isCorrect: true },
    { html: wrongs[0], isCorrect: false },
    { html: wrongs[1], isCorrect: false },
    { html: wrongs[2], isCorrect: false }
  ]);

  // OUTPUT: render the 4 citation cards
  renderCards(choices, correct, style);

  // Hide feedback + next button, then start the timer
  const fb = document.getElementById('feedback-bar');
  fb.style.display = 'none';
  fb.className = 'feedback-bar';
  document.getElementById('btn-next').style.display = 'none';

  startTimer(idx, correct, style);
}


// ── Render the 4 citation cards ──
// OUTPUT: each card is a visual, clickable citation option
function renderCards(choices, correct, style) {
  const grid    = document.getElementById('cards-grid');
  const letters = ['A', 'B', 'C', 'D'];
  grid.innerHTML = '';

  // ITERATION: loop through choices list and create a card for each
  for (let i = 0; i < choices.length; i++) {
    const choice = choices[i];
    const card   = document.createElement('div');
    card.className = 'cite-card';

    card.innerHTML =
      '<div class="card-letter">' + letters[i] + '</div>' +
      '<div class="card-cite-text">' + choice.html + '</div>' +
      '<div class="card-result-icon" id="icon-' + i + '"></div>';

    // INPUT: click on a citation card
    card.addEventListener('click', function () {
      if (roundLocked) return;
      handleCardClick(choice.isCorrect, card, correct, style, i);
    });

    grid.appendChild(card);
  }
}


// ── Handle a card click ──
// INPUT: user clicks a citation card
// OUTPUT: visual feedback, score/lives update, next-round prompt
function handleCardClick(isCorrect, clickedCard, correct, style, clickedIdx) {
  roundLocked = true;
  clearInterval(timerInterval);

  // Lock all cards
  document.querySelectorAll('.cite-card').forEach(c => c.classList.add('locked'));

  const timeBonus = Math.round((timeLeft / ROUND_TIME_MS[Math.min(currentRound, 4)]) * MAX_TIME_BONUS);
  const fb = document.getElementById('feedback-bar');

  if (isCorrect) {
    // Correct answer
    const pts = BASE_PTS + timeBonus;
    score += pts;
    clickedCard.classList.add('correct');
    document.getElementById('icon-' + clickedIdx).textContent = '✓';
    document.getElementById('icon-' + clickedIdx).style.display = 'block';

    // OUTPUT: feedback
    fb.className = 'feedback-bar correct';
    fb.textContent = 'CORRECT! +' + pts + ' pts (base ' + BASE_PTS + ' + ' + timeBonus + ' time bonus)';
    results.push({ correct: true, style, pts, title: gameRounds[currentRound].src.title });
  } else {
    // Wrong answer
    lives--;
    clickedCard.classList.add('wrong');
    document.getElementById('icon-' + clickedIdx).textContent = '✗';
    document.getElementById('icon-' + clickedIdx).style.display = 'block';

    // Reveal which card was correct (highlight correct card green)
    document.querySelectorAll('.cite-card').forEach(c => {
      const txt = c.querySelector('.card-cite-text');
      // strip HTML tags to compare plain text
      const div = document.createElement('div');
      div.innerHTML = correct;
      const correctPlain = div.textContent;
      if (txt) {
        const cardDiv = document.createElement('div');
        cardDiv.innerHTML = txt.innerHTML;
        if (cardDiv.textContent === correctPlain) {
          c.classList.add('correct');
        } else if (c !== clickedCard) {
          c.classList.add('fade');
        }
      }
    });

    // OUTPUT: feedback
    fb.className = 'feedback-bar wrong';
    fb.textContent = 'WRONG! -1 ❤️  — the correct card is highlighted';
    results.push({ correct: false, style, pts: 0, title: gameRounds[currentRound].src.title });
  }

  fb.style.display = 'block';
  document.getElementById('hud-lives').textContent = '❤️ ' + lives;
  document.getElementById('hud-score').textContent = '⭐ ' + score;

  // SELECTION: game over if out of lives, else show next button
  if (lives <= 0) {
    document.getElementById('btn-next').textContent = 'SEE RESULTS ▶';
  } else if (currentRound === TOTAL_ROUNDS - 1) {
    document.getElementById('btn-next').textContent = 'SEE RESULTS ▶';
  } else {
    document.getElementById('btn-next').textContent = 'NEXT ROUND ▶';
  }
  document.getElementById('btn-next').style.display = 'block';
}


// ── Timer logic ──
// OUTPUT: timer bar width updates in real time; triggers auto-fail on expiry
function startTimer(roundIdx, correct, style) {
  const totalMs = ROUND_TIME_MS[Math.min(roundIdx, ROUND_TIME_MS.length - 1)];
  timeLeft = totalMs;
  const bar = document.getElementById('timer-bar');
  bar.style.width = '100%';
  bar.className = 'timer-bar';

  const tick = 50; // update every 50ms for smooth animation

  timerInterval = setInterval(function () {
    timeLeft -= tick;
    const pct = Math.max(0, (timeLeft / totalMs) * 100);
    bar.style.width = pct + '%';

    // SELECTION: change bar color as time runs low
    if (pct < 25) {
      bar.className = 'timer-bar crit';
    } else if (pct < 50) {
      bar.className = 'timer-bar warn';
    }

    // Time ran out — auto-fail the round
    if (timeLeft <= 0) {
      clearInterval(timerInterval);
      if (roundLocked) return;
      roundLocked = true;
      lives--;

      // Lock all cards + fade them
      document.querySelectorAll('.cite-card').forEach(c => {
        c.classList.add('locked', 'fade');
      });

      // OUTPUT: timeout feedback
      const fb = document.getElementById('feedback-bar');
      fb.className = 'feedback-bar timeout';
      fb.textContent = "TIME'S UP! -1 ❤️";
      fb.style.display = 'block';

      document.getElementById('hud-lives').textContent = '❤️ ' + lives;

      results.push({ correct: false, style, pts: 0, title: gameRounds[currentRound].src.title });

      const nextLabel = (lives <= 0 || currentRound === TOTAL_ROUNDS - 1)
        ? 'SEE RESULTS ▶' : 'NEXT ROUND ▶';
      document.getElementById('btn-next').textContent = nextLabel;
      document.getElementById('btn-next').style.display = 'block';
    }
  }, tick);
}


// ── Advance to next round or end screen ──
function advanceRound() {
  currentRound++;
  if (currentRound >= TOTAL_ROUNDS || lives <= 0) {
    showEndScreen();
  } else {
    loadRound(currentRound);
  }
}


// ── End screen ──
// OUTPUT: final score, letter grade, per-round breakdown
function showEndScreen() {
  clearInterval(timerInterval);
  showScreen('screen-end');

  const maxScore = TOTAL_ROUNDS * (BASE_PTS + MAX_TIME_BONUS);
  const pct      = Math.round((score / maxScore) * 100);

  // SELECTION: assign a grade label
  let grade;
  if (pct === 100)    grade = 'S RANK — PERFECT! 🏆';
  else if (pct >= 80) grade = 'A RANK — Excellent!';
  else if (pct >= 60) grade = 'B RANK — Nice work!';
  else if (pct >= 40) grade = 'C RANK — Keep practicing!';
  else                grade = 'D RANK — Try again!';

  document.getElementById('end-title').textContent = grade;
  document.getElementById('end-score').textContent = score;
  document.getElementById('end-grade').textContent = 'out of ' + maxScore + ' points (' + pct + '%)';

  const list = document.getElementById('end-results');
  list.innerHTML = '';

  // OUTPUT + ITERATION: loop through results list and render each row
  for (let i = 0; i < results.length; i++) {
    const r   = results[i];
    const div = document.createElement('div');
    div.className = 'end-result-row';
    div.innerHTML =
      '<span class="er-pts ' + (r.correct ? 'ok' : 'bad') + '">' +
        (r.correct ? '+' + r.pts : '+0') +
      '</span>' +
      '<span class="er-title">' + r.title + '</span>' +
      '<span class="er-style">' + r.style.toUpperCase() + '</span>';
    list.appendChild(div);
  }
}


// ── Screen switcher ──
function showScreen(id) {
  document.querySelectorAll('.blitz-screen').forEach(s => s.classList.remove('active'));
  document.getElementById(id).classList.add('active');
}

// Initialise on page load — show start screen
showScreen('screen-start');
</script>