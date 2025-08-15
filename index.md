---
layout: base
title: I'm [Your Full Name]
hide: true
---

### Me and Team

Hi! My name is -Aashika Patel.

| Role         | Name     | Repo Location                       | Stream                | Repo Name |
|--------------|----------|-------------------------------------|-----------------------|-----------|
| Scrum Master | John     | github.com/jm1021/student           | upstream (OCS fork)   | student   |
| Scrummer     | Torin    | github.com/torin/student            | downstream (fork)     | student   |
| Scrummer     | Avantika | github.com/avantika/student         | downstream (fork)     | student   |
| Scrummer     | Aadit    | github.com/aaadit/student           | downstream (fork)     | student   |


## Links to Learning

### Development Environment

> Coding starts with tools, explore these tools and procedures with a click.

<a href="https://github.com/Open-Coding-Society/student">
    <img src="https://img.shields.io/badge/GitHub-181717?logo=github&logoColor=white" alt="GitHub">
</a>
<a href="https://open-coding-society.github.io/student">
    <img src="https://img.shields.io/badge/GitHub%20Pages-327FC7?logo=github&logoColor=white" alt="GitHub Pages">
</a>
<a href="https://kasm.opencodingsociety.com/" class="button small" style="background-color: #ffacdfff">
    KASM
</a>
<a href="https://vscode.dev/" class="button small" style="background-color: #941e55ff">
    <span style="color: #FFFFFF">VSCODE</span>
</a>

<br>

### Class Progress

<a href="{{site.baseurl}}/snake" class="button small" style="background-color: #ceacfeff">
    Snake Game
</a>
<a href="{{site.baseurl}}/turtle" class="button small" style="background-color: #f1d0f3ff">
    <span style="color: #95c7e4ff">Turtle</span>
</a>

<br>

<!-- Contact Section -->
### Get in Touch

> Feel free to reach out if you'd like to collaborate or learn more about our work.

<p style="color: #dac4e4ff;">Open Coding Society: <a href="https://opencodingsociety.com" style="color: #9dbee5ff; text-decoration: underline;">Socials</a></p>
<!-- 🎉 Donuts + Confetti Overlay -->
<style>
  /* Containers sit on top but don't block clicks */
  #donut-field, #confetti-container {
    position: fixed;
    inset: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
    pointer-events: none;
  }
  #donut-field { z-index: 5; }
  #confetti-container { z-index: 10; }

  /* Donuts */
  .donut {
    position: absolute;
    filter: drop-shadow(0 6px 6px rgba(0,0,0,0.15));
    opacity: 0.9;
    animation: bob var(--bob-duration, 8s) ease-in-out infinite,
               drift var(--drift-duration, 18s) linear infinite,
               spin var(--spin-duration, 10s) linear infinite;
    will-change: transform;
  }

  @keyframes bob {
    0%, 100% { transform: translateY(-6px); }
    50% { transform: translateY(6px); }
  }
  @keyframes drift {
    0%   { transform: translateX(0); }
    100% { transform: translateX(var(--drift-x, 80px)); }
  }
  @keyframes spin {
    to { rotate: 360deg; }
  }

  /* Confetti strips & squares */
  .confetti {
    position: absolute;
    top: -10vh;
    width: var(--w, 6px);
    height: var(--h, 14px);
    background: var(--c, #ff6b6b);
    transform: translateY(-100%);
    opacity: 0.9;
    animation: fall var(--fall, 7s) linear var(--delay, 0s) infinite,
               twirl var(--twirl, 1.4s) ease-in-out var(--delay, 0s) infinite alternate;
    will-change: transform;
  }

  .confetti.round { border-radius: 999px; }
  .confetti.square { aspect-ratio: 1 / 1; height: auto; }

  @keyframes fall {
    to { transform: translateY(110vh) rotate(var(--rot, 360deg)); }
  }
  @keyframes twirl {
    from { transform: translateY(0) rotate(0deg) }
    to   { transform: translateY(0) rotate(180deg) }
  }

  /* Reduce motion for users who prefer it */
  @media (prefers-reduced-motion: reduce) {
    .donut, .confetti {
      animation: none !important;
    }
  }
</style>

<div id="donut-field" aria-hidden="true"></div>
<div id="confetti-container" aria-hidden="true"></div>

<script>
  (function () {
    // --- Configuration ---
    const DONUT_COUNT = 36;     // number of 🍩
    const CONFETTI_COUNT = 160; // total confetti pieces

    const confettiColors = [
      "#ffa5eeff", "#cc98dfff", "#06D6A0", "#118AB2", "#9B5DE5",
      "#F15BB5", "#00BBF9", "#FEE440", "#8AC926", "#c4151aff"
    ];

    // Create random helper
    const rand = (min, max) => Math.random() * (max - min) + min;
    const sample = arr => arr[Math.floor(Math.random() * arr.length)];

    // --- Donuts ---
    const donutField = document.getElementById("donut-field");
    const DONUTS = ["🍩","🍩","🍩","🍩","🍩","🍩","🍩","🍩"]; // (kept simple; all donuts!)
    for (let i = 0; i < DONUT_COUNT; i++) {
      const el = document.createElement("span");
      el.className = "donut";
      el.textContent = sample(DONUTS);

      const size = rand(28, 96); // px
      el.style.fontSize = size + "px";

      // Random position
      el.style.left = rand(0, 100) + "vw";
      el.style.top  = rand(0, 100) + "vh";

      // Random animation timings
      el.style.setProperty("--bob-duration", rand(6, 12) + "s");
      el.style.setProperty("--drift-duration", rand(14, 24) + "s");
      el.style.setProperty("--spin-duration", rand(8, 18) + "s");
      el.style.setProperty("--drift-x", (Math.random() < 0.5 ? -1 : 1) * rand(40, 140) + "px");

      donutField.appendChild(el);
    }

    // --- Confetti ---
    const confettiWrap = document.getElementById("confetti-container");
    for (let i = 0; i < CONFETTI_COUNT; i++) {
      const c = document.createElement("div");
      c.className = "confetti " + (Math.random() < 0.5 ? "round" : "square");

      // Random start X across the viewport
      c.style.left = rand(0, 100) + "vw";

      // Random size & aspect
      const w = rand(3, 9);
      const h = rand(8, 18);
      c.style.setProperty("--w", w + "px");
      c.style.setProperty("--h", h + "px");

      // Random color and timings
      c.style.setProperty("--c", sample(confettiColors));
      c.style.setProperty("--fall", rand(5.5, 9.5) + "s");
      c.style.setProperty("--delay", rand(0, 5) + "s");
      c.style.setProperty("--twirl", rand(0.9, 2) + "s");
      c.style.setProperty("--rot", (Math.random() < 0.5 ? "-" : "") + rand(120, 540) + "deg");

      confettiWrap.appendChild(c);
    }

    // Keep overlays sized correctly if the page height changes
    const resize = () => {
      donutField.style.height = confettiWrap.style.height = window.innerHeight + "px";
      donutField.style.width = confettiWrap.style.width = window.innerWidth + "px";
    };
    resize();
    window.addEventListener("resize", resize);
  })();
</script>