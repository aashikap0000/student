---
layout: base
title: Background with Object
description: Use JavaScript to have an in-motion background.
sprite: /student/images/platformer/sprites/flying-ufo.png
background: /student/images/platformer/backgrounds/alien_planet1.jpg
permalink: /background
---

<canvas id="world"></canvas>

<script>
  // Get canvas and context
  const canvas = document.getElementById("world");
  const ctx = canvas.getContext('2d');
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;

  // Load images
  const backgroundImg = new Image();
  const spriteImg = new Image();

  backgroundImg.src = '{{ page.background | relative_url }}';
  spriteImg.src = '{{ page.sprite | relative_url }}';

  let imagesLoaded = 0;

  backgroundImg.onload = function() {
    console.log('Background loaded:', backgroundImg.src);
    imagesLoaded++;
    startGameWorld();
  };
  backgroundImg.onerror = function() {
    console.error('Background failed to load:', backgroundImg.src);
  };

  spriteImg.onload = function() {
    console.log('Sprite loaded:', spriteImg.src);
    imagesLoaded++;
    startGameWorld();
  };
  spriteImg.onerror = function() {
    console.error('Sprite failed to load:', spriteImg.src);
  };

  function startGameWorld() {
    if (imagesLoaded < 2) return;

    class GameObject {
      constructor(image, width, height, x = 0, y = 0, speedRatio = 0) {
        this.image = image;
        this.width = width;
        this.height = height;
        this.x = x;
        this.y = y;
        this.speedRatio = speedRatio;
        this.speed = GameWorld.gameSpeed * this.speedRatio;
      }
      update() {}
      draw(ctx) {
        ctx.drawImage(this.image, this.x, this.y, this.width, this.height);
      }
    }

    class Background extends GameObject {
      constructor(image, gameWorld) {
        super(image, gameWorld.width, gameWorld.height, 0, 0, 0.1);
      }
      update() {
        this.x = (this.x - this.speed) % this.width;
      }
      draw(ctx) {
        ctx.drawImage(this.image, this.x, this.y, this.width, this.height);
        ctx.drawImage(this.image, this.x + this.width, this.y, this.width, this.height);
      }
    }

    class Player extends GameObject {
      constructor(image, gameWorld) {
        const width = image.naturalWidth / 2;
        const height = image.naturalHeight / 2;
        const x = (gameWorld.width - width) / 2;
        const y = (gameWorld.height - height) / 2;
        super(image, width, height, x, y);
        this.baseY = y;
        this.frame = 0;
      }
      update() {
        this.y = this.baseY + Math.sin(this.frame * 0.05) * 20;
        this.frame++;
      }
    }

    class GameWorld {
      static gameSpeed = 5;
      constructor(backgroundImg, spriteImg) {
        this.canvas = canvas;
        this.ctx = ctx;
        this.width = canvas.width;
        this.height = canvas.height;

        this.objects = [
          new Background(backgroundImg, this),
          new Player(spriteImg, this)
        ];
      }

      gameLoop() {
        this.ctx.clearRect(0, 0, this.width, this.height);
        for (const obj of this.objects) {
          obj.update();
          obj.draw(this.ctx);
        }
        requestAnimationFrame(this.gameLoop.bind(this));
      }

      start() {
        this.gameLoop();
      }
    }

    const world = new GameWorld(backgroundImg, spriteImg);
    world.start();
  }
</script>