---
layout: post
title: Tools Set-Up Blog on Mac
permalink: /tools/setup-mac
comments: true
---

Switching to a MacBook for my CSP class required setting up VS Code, connecting GitHub, and learning how deployments and GitHub Actions worked. Here’s a walkthrough of my journey—from downloading VS Code to successfully organizing repositories, setting up environments, and collaborating with my team. 💻✨

## 🖥️ Installing VS Code and Dependencies on Mac

Downloaded VS Code from [https://code.visualstudio.com/](https://code.visualstudio.com/) and installed it. During installation, I ensured:

- **Add VS Code to PATH** (so I can open it from Terminal)
- **Enable Jupyter Notebook support**

**Installed VS Code Extensions:**

- `Python (Microsoft)` – Python support and debugging
- `Jupyter (Microsoft)` – Notebook integration
- `GitLens` – Advanced Git history and insights

## ✅ Verified Installations and Configured Git

Check versions and set up Git:

Check Python version
python3 --version

Check Git version
git --version

Configure Git with my username and email
git config --global user.name "Aashika P"
git config --global user.email "aashikap0000@example.com"

markdown
Copy
Edit

## 📂 Organizing Repositories on Mac

I structured my repositories carefully in directories for clarity:

- `~/opencs/`
  - `pages` – Cloned from jm1021
  - `student` – Template student repo
- `~/aashikap0000/`
  - `student-2` – My personal repo, moved here from `opencs`

**Cloning repositories:**

Clone pages repo
git clone https://github.com/jm1021/pages.git ~/opencs/pages

Clone template student repo
git clone https://github.com/jm1021/student.git ~/opencs/student

Clone personal repo (moved later to aashikap0000)
git clone https://github.com/aashikap0000/student-2.git ~/opencs/student-2
mv ~/opencs/student-2 ~/aashikap0000/student-2

css
Copy
Edit

## 🐍 Setting Up a Virtual Environment

I used Terminal (or VS Code integrated terminal) to create and activate a virtual environment:

Navigate to my repo
cd ~/aashikap0000/student-2

Create virtual environment
python3 -m venv venv

Activate virtual environment
source venv/bin/activate

Install requirements
pip install -r requirements.txt

Install wget and nbconvert for certain notebook errors
brew install wget
pip install nbconvert

markdown
Copy
Edit

Getting `make` to run was tricky—it took trial and error. I had to make sure:

- Virtual environment was activated
- All dependencies from `requirements.txt` were installed
- My student-2 repo was in the correct `~/aashikap0000` directory

Test make
make

vbnet
Copy
Edit

It didn’t work at first, but systematically checking directories, dependencies, and saving changes finally got everything running. 💪

## 🤝 Repository Collaboration

Created a fork of the team repository to collaborate with peers. This allowed me to push changes without affecting the main repo directly:

Fork the repo on GitHub, then clone
git clone https://github.com/aashikap0000/team-repo.git ~/opencs/team

vbnet
Copy
Edit

## 👾 Working on Backgrounds / Alien Hack

I ran into an issue where my background screen appeared white, then grey. After investigation:

- The problem was due to unsaved changes. I had to use **Cmd + S** and commit changes to make sure updates took effect.
- Edited the code to adjust how background images were loaded so that it would display correctly.

This taught me how small oversights in saving and committing could break code. It also showed how important debugging and iteration are. 🛠️

## ✅ Overcoming Challenges

The journey taught me a lot about:

- Directory structures and managing multiple repos
- Setting up virtual environments and troubleshooting commands like `make`
- The necessity of saving, committing, and carefully editing code
- How collaborative coding requires teamwork, patience, and trial-and-error problem-solving

I really appreciated my team for their guidance and learned the value of working together to figure things out. Collaboration and persistence made this complex setup manageable and rewarding! 🌟

## 📚 Key Git Commands I Used

Check status
git status

Add changes
git add <file_name>

Commit changes
git commit -m "Description of changes"

Push changes to my fork
git push
