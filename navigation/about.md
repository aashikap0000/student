---
layout: base
title: About Me
---

<h1>About Me</h1>

<!-- Flags -->
<div style="display: flex; justify-content: center; gap: 20px; margin: 20px 0;">
  <img src="https://upload.wikimedia.org/wikipedia/commons/0/01/Flag_of_California.svg" alt="California Flag" width="150">
  <img src="https://upload.wikimedia.org/wikipedia/en/4/41/Flag_of_India.svg" alt="India Flag" width="150">
</div>

<!-- Journey through life -->
<section>
  <h2>Journey Through Life</h2>
  <ul>
    <li>Elementary and middle school in San Diego</li>
    <li>High school in San Diego, currently a senior, class of 2026</li>
    <li>Want to study data science/engineering in college</li>
    <li>My dog Mocha is 9 years old</li>
    <li>My dream job is to own a really aesthetic coffee shop or study cafe</li>
  </ul>
  <img src="https://images.unsplash.com/photo-1504754524776-8f4f37790ca0" alt="Coffee Shop" width="400" style="border-radius: 10px; margin-top: 10px;">
</section>

<!-- Fun Facts -->
<section>
  <h2>Fun Facts</h2>
  <ul>
    <li>I found out I was allergic to peanuts when I was 5 years old on a Southwest flight (I wonder if they stopped serving peanuts because of me?)</li>
    <li>I’ve been doing Bharatanatyam classical dance for 11 years</li>
    <li>My dream vacation location is Bora Bora</li>
    <li>On the day I was born, this happened: The U.S. Food and Drug Administration allowed the production and sale of foods derived from cloned animals.</li>
  </ul>
  <button onclick="releaseDogs()" style="padding:10px; margin-top:10px; border-radius:8px;">🐶 Release the Dogs</button>
</section>

<!-- Favorite Foods -->
<section>
  <h2>You Are What You Eat</h2>
  <p>Click a food to make it appear — click again to make it disappear!</p>
  <div style="display: flex; flex-wrap: wrap; gap: 10px; margin-bottom: 20px;">
    <button onclick="toggleFood('🍩', 'donuts')">Donuts</button>
    <button onclick="toggleFood('🍦', 'icecream')">Icecream</button>
    <button onclick="toggleFood('🧀', 'cheese')">Cheese</button>
    <button onclick="toggleFood('🍜', 'noodles')">Noodles</button>
    <button onclick="toggleFood('🍝', 'pasta')">Pasta</button>
    <button onclick="toggleFood('🍕', 'pizza')">Pizza</button>
    <button onclick="toggleFood('☕', 'coffee')">Coffee</button>
    <button onclick="toggleFood('🧁', 'cupcake')">Cupcake</button>
  </div>
  <div id="foodContainer" style="font-size: 2rem; min-height: 50px;"></div>
</section>

<script>
  // Toggle food emojis
  const activeFoods = {};
  function toggleFood(emoji, key) {
    const container = document.getElementById("foodContainer");
    if (activeFoods[key]) {
      // remove food
      container.querySelectorAll(`.food-${key}`).forEach(el => el.remove());
      delete activeFoods[key];
    } else {
      // add food
      for (let i = 0; i < 15; i++) {
        const span = document.createElement("span");
        span.textContent = emoji;
        span.classList.add(`food-${key}`);
        span.style.margin = "5px";
        container.appendChild(span);
      }
      activeFoods[key] = true;
    }
  }

  // Release a few dogs
  function releaseDogs() {
    const container = document.body;
    for (let i = 0; i < 5; i++) {
      const dog = document.createElement("div");
      dog.textContent = "🐕";
      dog.style.position = "fixed";
      dog.style.left = Math.random() * window.innerWidth + "px";
      dog.style.top = Math.random() * window.innerHeight + "px";
      dog.style.fontSize = "2rem";
      container.appendChild(dog);
      setTimeout(() => dog.remove(), 4000);
    }
  }
</script>