---
toc: True
layout: post
title: Background Hack Blog
permalink: /github/pages/background_changes
breakcrumbs: true 
comments: true
description: "Replaced the original space background with a mountains and sunset image by downloading the file, adding it to the repo under images/platformer/backgrounds/, and updating the front matter to point to it."
---

# Background Hack Update

**Updated site (with new background):** https://krishvisv.github.io/student/background

**Short write-up (what we changed & how):**

- We replaced the original "space" background with a mountains and sunset background.
- How we did it:
  1. Downloaded the desired background image from the web and saved it locally.
  2. Added the image file into the repository under `images/platformer/backgrounds/` and named the file `starwars background.jpeg`.
     - (Note: I originally downloaded the picture as a PNG, but the file in the repo is placed/renamed as `starwars background.jpeg` so the front matter references that filename.)
  3. Updated the page's YAML front matter to point to the new image by setting the `background` field to:
     ```
     background: "images/platformer/backgrounds/starwars background.jpeg"
     ```
  4. Committed and pushed the change to the repo so the GitHub Pages site (linked above) now serves the new mountains + sunset background.