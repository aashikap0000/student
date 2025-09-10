---
layout: post
title: "Tools Setup"
description: "Javascript"
permalink: /sprint/1/agile
breadcrumb: true
toc: true
nav: sprint_1.html
---

Switching to setting up everything on my MacBook for CSP required downloading VS Code, managing multiple repositories, and troubleshooting all kinds of errors until I could finally get everything running. Here’s how I set everything up, step by step!

## 🍎 1. Installing VS Code and Dependencies on Mac

Downloaded VS Code from [https://code.visualstudio.com/](https://code.visualstudio.com/) and installed it on my Mac. Once installed, I set up the key extensions I needed:

- **Python (Microsoft)** – for debugging and running code  
- **Jupyter (Microsoft)** – for notebooks integration  
- **GitLens** – for Git history and insights  

Verified installations in the Mac terminal:

```bash
python3 --version
git --version
Configured Git with my info:

bash
Copy
Edit
git config --global user.name "Aashika Patel"
git config --global user.email "aashikap0000@gmail.com"

📂 2. Organizing My Repositories
I cloned jm1021’s student template repo to create my own personal repo, and also cloned jm1021’s pages repo to contribute to the class site.

To stay organized, I kept:

pages and student in the opencs directory

student-2 (my personal repo) in the aashikap0000 directory

This required me to move student-2 from opencs → aashikap0000 using:

bash
Copy
Edit
mv ~/opencs/student-2 ~/aashikap0000/
🐍 3. Setting Up a Virtual Environment
Created and activated a Python virtual environment to run everything smoothly:

bash
Copy
Edit
python3 -m venv venv
source venv/bin/activate   # in Mac terminal or VS Code terminal
Installed all dependencies from requirements.txt:

bash
Copy
Edit
pip install -r requirements.txt
When some errors showed up, I had to install extra tools like wget and nbconvert:

bash
Copy
Edit
brew install wget
pip install nbconvert
⚙️ 4. Figuring Out make
Getting make to work was one of the most frustrating parts. I had to figure out:

making sure my virtual environment was activated before running make

ensuring my student-2 repo was in the aashikap0000 directory (not in opencs)

downloading requirements properly and rerunning when errors came up

This was a trial-and-error process 😅 but eventually, I built a system: check directory, activate venv, re-run make.

🤝 5. Repository Collaboration
To work with my team, I forked the team repository and cloned it locally. This allowed me to collaborate by committing changes and pushing updates.

👾 6. Alien Background Hack
One of the more fun challenges was getting the alien background and flying UFO to appear on my site. At first, my screen was completely white, then just grey. After debugging with my team, I realized:

I wasn’t saving my changes (Cmd + S) before committing

The code paths for the images were slightly off. We fixed it by making sure the image links used relative paths

I also had to adjust canvas dimensions to fit the entire screen window and handle window resizes

After lots of small edits and testing, the game finally displayed correctly 🚀.

🌟 Final Thoughts
This whole process taught me how important organization (repos, directories), patience (trial and error with make), and collaboration (team debugging sessions) are in coding. While it was difficult at times, I appreciated how much my team helped me out, and how each step taught me something new about working with Mac, GitHub, and VS Code.

Overall, I feel much more confident now about setting up tools, handling errors, and working as part of a collaborative team 🙌.