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

From feedback and reflection, our team realized we needed to connect the game more with **specific class lessons** and make it more engaging and accessible for all rookie coders. Below is a concrete, lesson-by-lesson plan + implementation roadmap and handoff strategy so the project scales and other students/teams can reuse our work.

---

# 💬 Feedback We Received  
- 👍 Fun and engaging concept for rookie coders  
- 👎 Needs to tie more directly to course lessons (**Boolean, Iterations, Lists**)  
- 👩‍💻 Should collaborate with advanced coders for design + accessibility improvements — advanced coders can elevate our idea by making it more professional and challenging

---

# 🚀 Our Plan Moving Forward (Detailed & Actionable)

### 1) Implement 3 Lessons into the Game (Immediate Priority)  
**Goal:** fully implement one playable, lesson-aligned quiz level for each of the three target lessons.  
- **Boolean (Aashika + Varada):**
  - Build a Level structure that focuses on expressions and conditionals: `true/false`, `and/or/not`, precedence, and compound conditions.
  - Example question types: evaluate `if (x && y)` outcomes; predict the boolean result of chained comparisons.
  - Add short, interactive examples that demonstrate how booleans drive program flow (e.g., a branching story visual).  
- **Iterations (Nick + Anwita):**
  - Create loop-focused questions: `for`, `while`, loop counters, off-by-one pitfalls.
  - Example question types: predict loop output, choose correct loop to accomplish a task, fix an infinite loop.
  - Visualize loops as repeated tasks (e.g., an animation showing repeated steps).  
- **Lists (Ethan + Adhav):**
  - Implement list/array operations: indexing, slicing, appending, removing, sorting.
  - Example question types: choose the correct index to access an element, predict final list after operations.
  - Use a "backpack" visual that collects items to illustrate list mutation.

**Deliverable for each pair by end of sprint:** one fully functional lesson level with 15 questions, per-language scoring, and at least 5 detailed explanations.

---

### 2) Once Implemented — Create Lesson Materials (Teacher-Friendly)  
**Goal:** convert each in-game lesson into a short classroom-ready lesson plan that teachers can pair with the game.  
- **Lesson Plan Components (for each lesson):**
  - Learning objective (e.g., "Students will evaluate boolean expressions and identify logical operators")  
  - 3–5 slide bullet points covering the concept with one worked example  
  - Quiz-game mapping: which in-game level/questions align with which slide/topic  
  - 1 short homework prompt that uses the game (e.g., "Play Boolean Level, screenshot your scoreboard, and explain two mistakes")  
- **Format:** `lesson-name.md` (or PDF) stored in repo `/lessons/` with links to the game-level permalink.

**Deliverable:** 1 lesson file per implemented lesson, plus a teacher quick-start (how to assign the level and interpret scoreboard data).

---

### 3) Give "Hacks" & Implementation Guides to Other People (Scale & Reuse)  
**Goal:** make it simple for others to adopt or fork our lesson-levels into their own games or class sites. Provide pragmatic, copy-paste friendly “hacks.”  
- **What a "hack" guide includes:**
  - Minimal code snippet for embedding a level (iframe/embed + parameters)  
  - JSON example for question format (question, options, correct answer, explanation) so other teams can drop questions into their own engines  
  - A short how-to: “3 steps to add a lesson to your site” (clone repo → copy `/levels/boolean.json` → update permalink)  
  - Common pitfalls & fixes (e.g., how to escape HTML examples, ensure accessibility attributes, pre-commit `make` step)  
- **Distribution:** add `/docs/hacks/` in repo with markdown files and a single `HACKS.md` overview; tweet or post in class Slack/Discord with a short how-to and link.

---

### 4) Multimedia & Targeted Practice (Enhancements)  
- **Short videos (<1 min)** for each lesson highlighting concept + a micro-demo.  
  - Boolean: decision tree animation.  
  - Iterations: animated loop counter showing changes per iteration.  
  - Lists: visual push/pop/insert operations.  
- **Targeted practice:** scoreboard analytics will suggest follow-up drills:
  - If Boolean errors > 30% → show 5 additional boolean-only questions + 1 micro-video.
  - If Iterations errors concentrated around loop boundaries → show off-by-one drills.
  - If Lists errors are index-based → show index mapping exercises and drag-and-drop practice.

---

### 5) Design, Accessibility & Advanced-Coder Collaboration  
- Pair lesson pairs with one advanced coder reviewer to:
  - Improve UI affordances (clearer buttons for novices, larger hit targets).  
  - Ensure color contrast and keyboard navigation (WCAG basics).  
  - Add ARIA labels for screen readers and test with a basic screen reader workflow.  
- Advanced coders help refactor performance-sensitive parts (question loading, scoreboard calculations) and assist with embedding/analytics.

---

### 6) Integration with OpenCS & Teacher Workflow (Longer-Term)  
- Provide an OpenCS integration plan: one page per lesson with embed code and teacher notes.  
- Add an **assign** feature so teachers can create short assignments linking to a level and collect screenshots or scoreboard data.  
- Pilot the OpenCS integration in one class section and collect feedback before full rollout.

---

## ✅ Success Criteria (how we'll know it's working)
- Each lesson level is playable and maps to a 1-page lesson doc.  
- New users can implement a level on their site using `HACKS.md` within 15 minutes.  
- Playtest with 5 rookie coders shows measurable improvement (e.g., average score increase after explanations + one day of practice).  
- At least one teacher integrates a lesson into their OpenCS flow for a pilot.

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