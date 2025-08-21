<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>About Me</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="https://kit.fontawesome.com/a2e0e6ad65.js" crossorigin="anonymous"></script>
  <style>
    body {
      background-color: #fefefe;
      font-family: 'Arial', sans-serif;
    }
    .food-emoji {
      position: absolute;
      font-size: 2rem;
      animation: float 5s linear infinite;
    }
    @keyframes float {
      from { transform: translateY(0); opacity: 1; }
      to { transform: translateY(-100vh); opacity: 0; }
    }
  </style>
</head>
<body class="p-6">

  <!-- Flags -->
  <div class="flex justify-center gap-6 mb-6">
    <img src="https://upload.wikimedia.org/wikipedia/commons/0/01/Flag_of_California.svg" alt="California Flag" class="w-32 shadow-md rounded">
    <img src="https://upload.wikimedia.org/wikipedia/en/4/41/Flag_of_India.svg" alt="India Flag" class="w-32 shadow-md rounded">
  </div>

  <!-- Journey Section -->
  <section class="mb-10">
    <h2 class="text-3xl font-bold text-center mb-4">Journey Through Life</h2>
    <ul class="list-disc list-inside text-lg space-y-2">
      <li>Elementary and middle school in San Diego</li>
      <li>High school in San Diego, currently a senior, class of 2026</li>
      <li>Want to study data science/engineering in college</li>
      <li>My dog Mocha is 9 years old</li>
      <li>Dream job: owning a really aesthetic coffee shop or study cafe</li>
    </ul>
    <div class="flex justify-center mt-4">
      <img src="https://images.unsplash.com/photo-1509042239860-f550ce710b93" alt="Coffee Shop" class="w-96 rounded-2xl shadow-md">
    </div>
  </section>

  <!-- Fun Facts -->
  <section class="mb-10">
    <h2 class="text-3xl font-bold text-center mb-4">Fun Facts</h2>
    <ul class="list-disc list-inside text-lg space-y-2">
      <li>I found out I was allergic to peanuts when I was 5 years old on a Southwest flight (I wonder if they stopped serving peanuts because of me?)</li>
      <li>I've been doing Bharatanatyam classical dance for 11 years</li>
      <li>My dream vacation location is Bora Bora</li>
      <li>On the day I was born: The U.S. FDA allowed the production and sale of foods derived from cloned animals.</li>
    </ul>
    <div class="text-center mt-4">
      <button onclick="releaseDogs()" class="bg-blue-500 text-white px-4 py-2 rounded-lg shadow">Release Dogs 🐶</button>
    </div>
  </section>

  <!-- You Are What You Eat -->
  <section class="mb-10">
    <h2 class="text-3xl font-bold text-center mb-6">You Are What You Eat</h2>
    <div class="flex flex-wrap justify-center gap-4">
      <button onclick="toggleFood('donut','🍩')" class="px-4 py-2 bg-pink-300 rounded-lg shadow">Donuts</button>
      <button onclick="toggleFood('icecream','🍦')" class="px-4 py-2 bg-blue-300 rounded-lg shadow">Icecream</button>
      <button onclick="toggleFood('cheese','🧀')" class="px-4 py-2 bg-yellow-300 rounded-lg shadow">Cheese</button>
      <button onclick="toggleFood('noodles','🍜')" class="px-4 py-2 bg-green-300 rounded-lg shadow">Noodles</button>
      <button onclick="toggleFood('pasta','🍝')" class="px-4 py-2 bg-orange-300 rounded-lg shadow">Pasta</button>
      <button onclick="toggleFood('pizza','🍕')" class="px-4 py-2 bg-red-300 rounded-lg shadow">Pizza</button>
      <button onclick="toggleFood('coffee','☕')" class="px-4 py-2 bg-brown-300 rounded-lg shadow">Coffee</button>
      <button onclick="toggleFood('cupcake','🧁')" class="px-4 py-2 bg-purple-300 rounded-lg shadow">Cupcake</button>
    </div>
  </section>

  <!-- Food & Dog Scripts -->
  <script>
    let activeFoods = {};

    function toggleFood(name, emoji) {
      if (activeFoods[name]) {
        activeFoods[name].forEach(el => el.remove());
        delete activeFoods[name];
      } else {
        activeFoods[name] = [];
        for (let i = 0; i < 20; i++) {
          const food = document.createElement('div');
          food.classList.add('food-emoji');
          food.textContent = emoji;
          food.style.left = Math.random() * 100 + 'vw';
          food.style.top = (Math.random() * 80 + 10) + 'vh';
          food.style.fontSize = (Math.random() * 2 + 1) + 'rem';
          document.body.appendChild(food);
          activeFoods[name].push(food);
        }
      }
    }

    function releaseDogs() {
      for (let i = 0; i < 5; i++) {
        const dog = document.createElement('div');
        dog.classList.add('food-emoji');
        dog.textContent = '🐶';
        dog.style.left = Math.random() * 100 + 'vw';
        dog.style.top = (Math.random() * 80 + 10) + 'vh';
        dog.style.fontSize = (Math.random() * 2 + 1) + 'rem';
        document.body.appendChild(dog);
        setTimeout(() => dog.remove(), 5000);
      }
    }
  </script>

</body>
</html>