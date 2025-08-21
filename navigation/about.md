---
layout: base
title: I'm Aashika Patel
hide: true
---

### Me and Team

Hi! My name is Aashika Patel.

| Role         | Name     | Repo Location                       | Stream                | Repo Name |
|--------------|----------|-------------------------------------|-----------------------|-----------|
| Scrum Master | John     | github.com/jm1021/student           | upstream (OCS fork)   | student   |
| Scrummer     | Torin    | github.com/torin/student            | downstream (fork)     | student   |
| Scrummer     | Avantika | github.com/avantika/student         | downstream (fork)     | student   |
| Scrummer     | Aadit    | github.com/aaadit/student           | downstream (fork)     | student   |


## Links to Learning

### Development Environment

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
    <span style="color: #000000">Turtle</span>
</a>

<br>

---

## 🌎 Journey Through Life

<div style="text-align:center;">
    <img src="https://upload.wikimedia.org/wikipedia/commons/0/01/Flag_of_California.svg" alt="California Flag" width="120">
    <img src="https://upload.wikimedia.org/wikipedia/en/4/41/Flag_of_India.svg" alt="India Flag" width="120">
</div>

- 📍 Elementary and middle school in San Diego  
- 🎓 High school in San Diego, currently a senior (Class of 2026)  
- 📊 Want to study **data science/engineering** in college  
- 🐶 My dog **Mocha** is 9 years old  
- ☕ Dream job → owning a really **aesthetic coffee shop or study cafe**  

<div style="text-align:center; margin-top:10px;">
    <img src="https://images.unsplash.com/photo-1509042239860-f550ce710b93" alt="Coffee Shop" width="400" style="border-radius: 15px; box-shadow: 0px 4px 8px rgba(0,0,0,0.2);">
</div>

---

## 🎉 Culture, Family, Fun

- 🐕 Click below to release a few dogs on the screen!  
<button onclick="releaseDogs()" style="background-color:#ffd9e8; padding:10px; border:none; border-radius:10px; cursor:pointer;">
    🐶 Release Dogs
</button>  

- 👩‍👧 I have one older sister who's **22 years old**  
- 🎶 I love listening to music, reading, and dancing in my free time  

<script>
function releaseDogs() {
    for (let i = 0; i < 3; i++) {
        let dog = document.createElement("div");
        dog.innerHTML = "🐕";
        dog.style.position = "fixed";
        dog.style.left = Math.random() * window.innerWidth + "px";
        dog.style.top = Math.random() * window.innerHeight + "px";
        dog.style.fontSize = "40px";
        dog.style.zIndex = "1000";
        document.body.appendChild(dog);
    }
}
</script>

---

## 🍴 Favorite Foods Gallery

<p>Click on the food buttons below to make them appear on the screen!</p>

<div style="display:flex; flex-wrap:wrap; gap:15px;">
    <button onclick="spawnFood('🍩')" style="border:none; background:none; cursor:pointer;">
        <img src="https://upload.wikimedia.org/wikipedia/commons/d/d6/Donut.png" width="70">
    </button>
    <button onclick="spawnFood('🍦')" style="border:none; background:none; cursor:pointer;">
        <img src="https://upload.wikimedia.org/wikipedia/commons/d/d3/Vanilla_Ice_Cream_Cone_at_Central_Market.jpg" width="70">
    </button>
    <button onclick="spawnFood('🧀')" style="border:none; background:none; cursor:pointer;">
        <img src="https://upload.wikimedia.org/wikipedia/commons/4/44/Macaroni_and_cheese.jpg" width="70">
    </button>
    <button onclick="spawnFood('🍝')" style="border:none; background:none; cursor:pointer;">
        <img src="https://upload.wikimedia.org/wikipedia/commons/0/0b/Spaghetti_alle_vongole.jpg" width="70">
    </button>
    <button onclick="spawnFood('🍕')" style="border:none; background:none; cursor:pointer;">
        <img src="https://upload.wikimedia.org/wikipedia/commons/d/d1/Pepperoni_pizza.jpg" width="70">
    </button>
    <button onclick="spawnFood('🥡')" style="border:none; background:none; cursor:pointer;">
        <img src="https://upload.wikimedia.org/wikipedia/commons/5/55/Chinese_take_out_box.jpg" width="70">
    </button>
</div>

<script>
function spawnFood(foodEmoji) {
    let food = document.createElement("div");
    food.innerHTML = foodEmoji;
    food.style.position = "fixed";
    food.style.left = Math.random() * window.innerWidth + "px";
    food.style.top = Math.random() * window.innerHeight + "px";
    food.style.fontSize = "50px";
    food.style.zIndex = "1000";
    document.body.appendChild(food);
}
</script>

---

<!-- Contact Section -->
### Get in Touch

<p style="color: #dac4e4ff;">Open Coding Society: <a href="https://opencodingsociety.com" style="color: #9dbee5ff; text-decoration: underline;">Socials</a></p>