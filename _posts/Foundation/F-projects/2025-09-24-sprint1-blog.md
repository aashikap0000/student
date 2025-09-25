---
layout: post
title: Sprint 1 Experiences Blog 
permalink: /sprint 1 blog
comments: true
---

# 🚀 Sprint 1 Experiences Blog  

## 🎮 What We Did on the Game  
During Sprint 1, our team created a **quiz-style coding game** aimed at helping rookie coders strengthen their skills. The game currently covers **JavaScript, Python, CSS, HTML, and Markdown**, and each language is introduced through simple code snippets and multiple-choice questions.  

**Core Features we built in Sprint 1:**  
- ✅ **Progress bar** to track advancement through questions  
- ✅ **Multiple levels** that unlock automatically  
- ✅ **Score counter** for each language (shows where a player struggles)  
- ✅ **Explanations** for every correct answer (so players learn, not just guess)  
- ✅ **Auto-level up** after 15 correct answers  

This setup made our game more than just a quiz — it became an **interactive learning tool** that adapts to a player’s progress.  



## ✍️ My Contributions  
My main focus was writing **explanations for Level 3 code snippets** across all languages. Instead of only showing whether an answer was right or wrong, I wanted to ensure players understood **why** the answer was correct.  

**How I approached this:**  
- Broke down code syntax and **symbols** like `=>`, `==`, or `[]`  
- Pointed out **language-specific features** (e.g., Python slicing, JS fetch)  
- Connected code snippets to **real-world coding uses**  
- Wrote in a **rookie-friendly style** to reduce intimidation  

### 🧑‍🏫 Examples of My Explanations

**JavaScript Example:**  
```javascript
fetch('/api/data')
  .then(res => res.json())
  .then(d => console.log(d));
```
*This highlights JS’s fetch API and Promise chaining. Players learn that `fetch` makes network requests, `res.json()` parses the data, and `console.log` displays it. This shows JS’s strength in asynchronous web programming.*

**Python Example:**  
```python
s == s[::-1]
```
*The slicing `[::-1]` is unique to Python and reverses a string. The comparison checks if `s` is the same as its reverse, effectively testing for a palindrome. This snippet teaches Python’s concise syntax.*

**HTML Example:**  
```html
<form>
  <input type="text" />
  <button>Go</button>
</form>
```
*This demonstrates the structure of an HTML form. `<input>` collects user text, and `<button>` submits it. This teaches rookies about web page interactivity and form-building.*

By writing these explanations, I learned how to think like a beginner again, which was both challenging and rewarding.

---

## 😅 Problems & What I Learned
- Sprint 1 wasn’t smooth sailing — I ran into some real problems that taught me a lot:

- ❌ Small mistakes caused big problems. A missing bracket or symbol in my commits broke our start + level buttons, stopping the game from running.

- ⚡ Learned to use version control effectively. I had to revert to older commits and re-copy working code to fix errors.

- 🔄 Importance of testing before pushing. I now run make consistently before committing code to catch issues early.

- 🌱 Debugging mindset. I learned not to panic when something breaks, but to carefully trace back changes and find the root cause.

# Key Takeaway: Even small contributions affect the whole project, so carefulness and testing matter just as much as writing new code.

---

## 🤝 Team’s Plan with Lessons

From feedback and reflection, our team realized we needed to connect the game more with class lessons and make it more engaging and accessible.

# Feedback we received:

- 👍 Fun and engaging concept for rookies

- 👎 Needs to tie more directly to course lessons

- 👩‍💻 Should collaborate with advanced coders for design + accessibility improvements

# Our plan moving forward:

- 📝 Integrate actual lesson content into the quiz (not just random snippets)

- 🎥 Add short (<1 min) explanatory videos alongside written explanations

- 🧩 Offer targeted practice based on scoreboard results

- 🎨 Improve visual design + accessibility (color contrast, fonts, layout)

- 🌐 Eventually integrate into the OpenCS platform for broader use

---

## 🎯 My Personal Goals for Next Sprint  

🔧 **Increase confidence in committing code**  
- Double-check all changes with `make` and test locally before pushing  
- Aim to reduce the number of errors introduced in commits  
- Build a checklist system for myself to catch common mistakes (missing symbols, typos, etc.)  

📝 **Write clearer and more impactful explanations**  
- Focus on connecting code snippets to **real-world coding situations** (e.g., how `fetch` relates to APIs students might see in real projects)  
- Use simpler, rookie-friendly language while keeping explanations technically accurate  
- Add analogies where possible so new coders can “see” how the code functions  

🐞 **Strengthen debugging process**  
- Practice identifying **root causes** of broken functionality instead of just surface-level errors  
- Learn to use debugging tools (like browser console, breakpoints, or `console.log` strategically)  
- Reduce reliance on teammates by building confidence in solving issues on my own first  

💻 **Contribute beyond explanations**  
- Begin working on **game logic** (e.g., scoring, level transitions)  
- Learn small pieces of frontend design (CSS/HTML tweaks) to support the overall project look  
- Push myself to write code that is part of the core functionality, not just the learning layer  

🤝 **Collaborate and learn from others**  
- Actively ask teammates (especially more experienced coders) for help when I get stuck instead of staying silent  
- Use their feedback to **improve my own coding knowledge**  
- Contribute ideas during team meetings and integrate my work into the bigger vision  
- Focus on becoming a better **team communicator**, not just an individual contributor  

🌍 **Bigger-picture growth**  
- Develop confidence not only in coding but also in explaining **why my contributions matter to the team’s end product**  
- Gain experience in balancing **technical accuracy** with **teaching clarity**  
- Improve at **thinking like a rookie coder** while steadily leveling up my own skills  
- Work toward being someone who can eventually **mentor others** in the same way I’m being mentored now  

---

## 🌟 Overall Takeaway

Sprint 1 was a mix of successes and struggles, but both pushed me to grow. I learned that:

- Explaining code forces you to truly understand it yourself

- Small errors can cause big setbacks, but version control + testing are lifesavers

- Working in a team means balancing my contributions with accountability

# I’m excited to take what I learned from Sprint 1 and push myself further in Sprint 2 🚀.