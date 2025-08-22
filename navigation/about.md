---
layout: post
title: About
permalink: /about/
comments: true
---

## 🌟 About Me

<style>
  .flag-buttons {
    display: flex;
    justify-content: center;
    gap: 20px;
    margin-bottom: 20px;
  }
  .flag-buttons img {
    width: 120px;
    cursor: pointer;
    border-radius: 8px;
    transition: transform 0.2s;
  }
  .flag-buttons img:hover {
    transform: scale(1.1);
  }

  ul.circle-list {
    list-style-type: circle;
    margin-left: 20px;
  }

  .food-buttons button {
    border: none;
    padding: 10px 15px;
    border-radius: 8px;
    cursor: pointer;
    font-size: 1rem;
    color: white;
  }
  .food-buttons {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin-top: 10px;
    margin-bottom: 20px;
  }

  .confetti-emoji {
    position: fixed;
    animation: fall 5s linear forwards;
    font-size: 2rem;
    pointer-events: none;
  }
  @keyframes fall {
    from { transform: translateY(-50px); opacity: 1; }
    to { transform: translateY(100vh); opacity: 0; }
  }

  .woof-button {
    background-color: pink;
    border: none;
    padding: 10px 15px;
    border-radius: 8px;
    cursor: pointer;
    font-size: 1rem;
    margin-top: 10px;
  }
</style>

<!-- FLAGS -->
<div class="flag-buttons">
  <img src="https://upload.wikimedia.org/wikipedia/commons/0/01/Flag_of_California.svg" alt="California Flag" onclick="releaseEmoji('🐻')">
  <img src="https://upload.wikimedia.org/wikipedia/en/4/41/Flag_of_India.svg" alt="India Flag" onclick="releaseEmoji('🦚')">
</div>

---

## Journey Through Life

<ul class="circle-list">
  <li>Elementary and middle school in San Diego</li>
  <li>High school in San Diego, currently a senior, class of 2026</li>
  <li>Want to study data science/engineering in college</li>
  <li>My dog Mocha is 9 years old</li>
  <li>My dream job is to own a really aesthetic coffee shop or study cafe</li>
</ul>

<img src="https://images.unsplash.com/photo-1504754524776-8f4f37790ca0" alt="Coffee Shop" width="400" style="border-radius: 10px; margin-top: 10px;">

---

## Fun Facts

<ul class="circle-list">
  <li>I found out I was allergic to peanuts when I was 5 years old on a Southwest flight (I wonder if they stopped serving peanuts because of me?)</li>
  <li>I’ve been doing Bharatanatyam classical dance for 11 years</li>
  <li>My dream vacation location is Bora Bora</li>
  <li>On the day I was born, this happened: The U.S. Food and Drug Administration allowed the production and sale of foods derived from cloned animals.</li>
</ul>

<button class="woof-button" onclick="releaseEmoji('🐶')">Woof</button>

---

## You Are What You Eat
<p>Some of my favorite foods </p>

<p>Click a food to make it appear — click again to make it disappear!</p>

<div class="food-buttons">
  <button style="background-color: #ffadad;" onclick="toggleFood('🍕','pizza')">Pizza</button>
  <button style="background-color: #ffd6a5;" onclick="toggleFood('🍝','pasta')">Pasta</button>
  <button style="background-color: #fdffb6;" onclick="toggleFood('🧀','cheese')">Cheese</button>
  <button style="background-color: #caffbf;" onclick="toggleFood('🍩','donuts')">Donuts</button>
  <button style="background-color: #9bf6ff;" onclick="toggleFood('🍦','icecream')">Icecream</button>
  <button style="background-color: #a0c4ff;" onclick="toggleFood('🍜','noodles')">Noodles</button>
  <button style="background-color: #bdb2ff;" onclick="toggleFood('☕','coffee')">Coffee</button>
  <button style="background-color: #ffc6ff;" onclick="toggleFood('🧁','cupcakes')">Cupcakes</button>
</div>

<script>
  // General emoji release (for flags + Woof button)
  function releaseEmoji(emoji) {
    for (let i = 0; i < 10; i++) {
      const span = document.createElement("span");
      span.textContent = emoji;
      span.classList.add("confetti-emoji");
      span.style.left = Math.random() * window.innerWidth + "px";
      span.style.top = "-50px";
      document.body.appendChild(span);
      setTimeout(() => span.remove(), 5000);
    }
  }

  // Toggleable food confetti
  const activeFood = {};
  function toggleFood(emoji, key) {
    if (activeFood[key]) {
      activeFood[key] = false;
    } else {
      activeFood[key] = true;
      for (let i = 0; i < 20; i++) {
        const span = document.createElement("span");
        span.textContent = emoji;
        span.classList.add("confetti-emoji", `food-${key}`);
        span.style.left = Math.random() * window.innerWidth + "px";
        span.style.top = "-50px";
        document.body.appendChild(span);
        setTimeout(() => span.remove(), 5000);
      }
      setTimeout(() => { activeFood[key] = false; }, 5000);
    }
  }
</script>