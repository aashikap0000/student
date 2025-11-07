---
layout: post
title: Retrospective Blog 
permalink: /retrospectiveblog
comments: true
---

## 1. Comparing Myself to the Beginning of the Year

At the beginning of the year, I didn’t really know how to fix small bugs or understand what went wrong when my code broke. Now, I feel much more confident in debugging and solving technical issues independently. I’ve learned how to fix common VSCode and Git errors, like when make isn’t working, merge conflicts appear, or images don’t show up on a webpage. I now know to run pip install -r requirements.txt when dependencies are missing, to turn on autosave while coding, and to check the Git console when commits or file paths fail.

I’ve also grown in my ability to understand code structure. Even if I’ve never seen a specific piece of code before, I can usually tell what it’s doing and which language it’s written in. For example, during our coding language identification game, I learned to recognize differences between Python, Java, and JavaScript.

During our teaching presentations, I learned a lot about boolean expressions while preparing homework and solutions. We accidentally wrote our homework in Java instead of JavaScript, and that mistake helped me realize that console.log is one of JavaScript’s key identifiers.

When I created the Awareness game for our Night at the Museum project, I learned how design elements (like colors, backgrounds, and visuals) differ from logic-based code (like tracking lives or using drag-and-drop).

Behaviorally, I’ve also grown. I’m more collaborative, responsible, and engaged in class discussions. I’ve taken more ownership of my work, I coded the Awareness game for our Media Literacy Quest. I also reached out for help when needed, attending office hours and asking CSA friends for debugging advice.

---

## 📊 Skill Growth Evaluation

| Skill | Mastered (Y/N) | Self Rank (1-5) | Peer Rank (1-5) | Teacher Rank (1-5) | Average | Notes / Evidence |
|-------|----------------|------------------|-----------------|---------------------|---------|------------------|
| 🎯 **Core Behaviors** ||||| |
| Attendance | ✅ Y | 5 | 5 | 5 | 5.0 | Almost always present, if not present, check with group members about missed work or contributions |
| Work Habits | ❌ N | 3 | 3 | 4 | 3.3 | Sometimes distracted, but improving consistency by setting small goals. |
| Behavior | ✅ Y | 4 | 5 | 5 | 4.7 | Respectful and positive teammate, encourages others during work. Have improved in talking to group members and being focused in class. |
| Timeliness | ❌ N | 3 | 3 | 3 | 3.0 | Still late on a few commits/deliverables, but catching up faster than before. |
| 💻 **Technical Skills** ||||| |
| Tech/Cyber Sense | ✅ Y | 4 | 3 | 4 | 3.7 | Recognizes when code errors break main branch, improved at spotting JS, html issues. |
| Tech/Cyber Talk | ❌ N | 2 | 3 | 3 | 2.7 | Learning to use precise coding terms with peers, still mixes casual language. |
| Tech Growth | ✅ Y | 4 | 4 | 4 | 4.0 | Big improvement in debugging and was able to code a whole game. |
| 🤝 **Collaboration** ||||| |
| Advocacy | ❌ N | 2 | 3 | 3 | 2.7 | Hesitant to ask for help from advanced coders, working on speaking up more. |
| Communication & Collab | ✅ Y | 4 | 4 | 5 | 4.3 | Shares updates regularly, good at integrating feedback into the project. |
| 🎨 **Professional Skills** ||||| |
| Integrity | ✅ Y | 5 | 5 | 5 | 5.0 | Always credits teammates, documents mistakes instead of hiding them. |
| Organization | ❌ N | 3 | 2 | 3 | 2.7 | Needs to keep repos/blogs more organized, commits sometimes messy. |
| 📈 **TOTALS** |   | **39** | **40** | **44** | **41.0** | Sum of all ranks |
| 🎯 **AVERAGE SCORE** |   | **3.5** | **3.6** | **4.0** | **3.7** | Shows steady improvement |

---

## 2. Key Takeways from Past Sprints 

# Tools

- Always activate venv before running code.

- If “make” doesn’t work, run: pip install -r requirements.txt

- Always git pull before committing to avoid merge errors.

- Run make before committing to test the site and ensure it builds correctly.

# Fundamentals of JavaScript/Python

- JavaScript and Python look similar at first, but they differ in structure and syntax.

- JavaScript uses console.log() while Python uses print().

- Python uses indentation for structure, while JavaScript uses curly braces {}.

- Lucas’ API homework seemed confusing at first, but once I understood the logic, it became manageable — and that confidence helped me during later projects like Night at the Museum.

# Digital Famine

- Collaboration is key. Our planet looked great overall, but some inconsistencies (like different end screens) showed we could improve coordination.

- Having a clear plan and storyboard before coding made the process easier. It gave me a checklist of all features I wanted to include.

## 3. Digital Famine

One specific issue I ran into was with my background image not appearing on the deployed site. The code looked like this:

```html
<style>
body {
  min-height: 100vh;
  background: url('{{ site.baseurl }}/hacks/digital-famine/media-lit/media/assets/spacebackground.jpg') no-repeat center center fixed;
  background-size: cover;
  font-family: system-ui, -apple-system, sans-serif;
  color: #ffffff;
  overflow-x: hidden;
}
</style>
```

I realized later that the site couldn’t access the media source even though it was in the correct repo folder. The issue was caused by how Jekyll processes paths on GitHub Pages (relative paths sometimes fail depending on how the site is built). In the future, I’ll make sure the file path is accessible from the base URL or store images in a globally accessible folder.

One of my favorite parts of my project was the shield animation that grows each time the player gets an answer right. It took hours of trial and error to balance size, transparency, and timing (making sure it didn’t cover too much of the game but was still visible enough to feel rewarding).

This shield code is shown below as code (so the site displays the code and does not render the shield). I wrapped the examples with raw / fenced code blocks so Jekyll/GitHub Pages will show the code instead of executing or rendering it.

{% raw %}
```html
<!-- Shield: HTML (displayed as code on the deployed page) -->
<div class="shield" id="shield" aria-hidden="true">
  <svg viewBox="0 0 64 64" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Shield">
    <title>Shield</title>
    <path d="M32 2 L52 10 V26 C52 40 40 52 32 60 C24 52 12 40 12 26 V10 Z"
          fill="none" stroke="#00ccff" stroke-width="2.5" stroke-linejoin="round" stroke-linecap="round"/>
    <path d="M32 8 L44 14 V26 C44 36 36 44 32 48 C28 44 20 36 20 26 V14 Z"
          fill="none" stroke="#00ccff" stroke-opacity="0.6" stroke-width="1.2" />
  </svg>
</div>
```

```javascript
// Shield: JS (controls the animation)
// This code increases the shield size and adds a glowing effect each time the player answers correctly.
function showShieldEffect() {
  shieldEl.style.display = 'flex';
  const m = shieldEl.style.transform.match(/scale\(([\d.]+)\)/);
  let currentScale = m ? parseFloat(m[1]) : 0;
  currentScale = Math.min(currentScale + 0.15, 14.5);
  shieldEl.style.transform = `translate(-50%, -50%) scale(${currentScale})`;

  const prevBox = shieldEl.style.boxShadow;
  shieldEl.style.boxShadow = '0 0 160px #00ccff88, 0 0 300px #00ccff44';
  setTimeout(() => { shieldEl.style.boxShadow = prevBox || '0 0 120px #00ccff66, 0 0 250px #00ccff33'; }, 300);
}
```
{% endraw %}

What makes this code interesting is how it uses scaling (transform: scale()) and box shadows to simulate a glowing pulse effect, giving a visual sense of progress. This process taught me patience and persistence — each bug fixed taught me more about how animation timing and DOM manipulation work.

## 4. Night at the Museum

Night at the Museum went much better than I expected. I had several great conversations with people working in engineering and AI, and I got to explain how our game functioned from the headline logic to the progression of submodules.

An AI engineer asked how our headlines were categorized, and I explained that they were defined as true or false within the code. He mentioned that instead of just defining them, the program could analyze text patterns to detect tone or bias automatically, using techniques like sentiment analysis or keyword weighting. That conversation made me realize how powerful programming can be when combined with data science.

Overall, I received positive feedback and felt proud of my work and my team’s effort.

## 5. Next on Project

If we had more time, I’d want to make our project feel more cohesive and visually “game-like.” I really liked how CSSE’s game looked — it felt immersive. I’d love to add more space-themed visuals, interactive alien characters, and maybe a final “boss level” that challenges players on everything they learned.

## 6. What I Want to Learn Next in CSP

Next, I want to learn how to use APIs in JavaScript to bring live data into web projects. It seems like a practical next step that connects front-end code to real-world applications, and it’s beginner-friendly but still challenging.

## 7. Analytics Review 

<p align="center">
  <img src="{{ '/images/analytics.png' | relative_url }}" width="500" alt="Commit Analytics">
</p>

<p align="center">
  <img src="{{ '/images/analyticsagain.png' | relative_url }}" width="500" alt="Commit Analytics in ScratchersMediaLiteracy">
</p>

## 8. MCQ 

Score: 43/66

## Strategy:

I began by answering the questions I was confident about first, then used logical elimination and pattern recognition to narrow down the more difficult ones. When uncertain, I relied on understanding the concepts we've learned in CSP to see if I could find an answer that made sense. 

Below are detailed reflections on the questions I missed or found challenging.

## Q3 — What is an example of a citizen science project?

My Answer: An experiment that requires specialized knowledge and training to conduct

Correct Answer: An experiment that requires data measurements to be taken in many different locations

Explanation: Citizen science involves collecting data from a large number of volunteers in various locations — for example, tracking bird migrations or weather conditions. I incorrectly focused on the “research” aspect, assuming the key factor was expert knowledge, when in fact, the strength of citizen science lies in public participation and data scale, not specialization.

## Q9 — What is the main purpose of iterative development?

My Answer: It eliminates the need for programmers to test completed programs.

Correct Answer: It helps programmers identify errors as components are added to a working program.

Explanation: Iterative development emphasizes frequent testing during the build process. Each small change is tested before adding new components. My answer misunderstood “iterative” as “self-correcting,” but in reality, it increases testing frequency, ensuring that bugs are caught early rather than at the end.

## Q14 — Comparing outputs of two similar programs. Both programs display a list of numbers but use slightly different logic.

My Answer: Program A and Program B display a different number of values.

Correct Answer: Program A and Program B display the same number of values, but the values differ.

Explanation: I misread the loop structure. Both loops iterate the same number of times, so the quantity of outputs is identical. However, differences in their arithmetic operations lead to different numerical outputs. The correct answer highlights how small logic changes can alter results without affecting structure.

## Q20 — Which expression returns the largest of three values a, b, and c?

My Answer: Max(a, b) + Max(b, c) - Max(a, c)

Correct Answer: Max (Max(a, b), c)

Explanation: The Max() function should compare all three values directly. My answer tried to combine separate comparisons using arithmetic, which can distort results if overlapping values occur. The correct expression uses nested Max functions to ensure the program checks all three inputs systematically.

## Q21 — Which sequence of commands moves the robot to the gray square?

My Answer:

MoveXTimes(3)
RightXTimes(1)
MoveXTimes(3)

Correct Answer:

MoveXTimes(2)
RightXTimes(3)
MoveXTimes(3)

Explanation: The sequence didn’t turn the robot correctly, leaving it facing the wrong direction before moving. The correct sequence uses three right turns to orient the robot north, then moves it upward to reach the target square. This tested logical sequencing and spatial reasoning, not just code syntax.

## Q22 — Which Boolean correctly checks if at least half of the temperatures are 90 or above?

My Answer:

total > 0.5 * counter

Correct Answer:

counter > 0.5 * total

Explanation:
I accidentally flipped the operands. The Boolean should compare the number of high temperatures (counter) to half of the total values. My answer compared total count to the number of high temps, which reverses the logic and yields false results for most datasets.

## Q24 — What is true about Byte Pair Encoding (BPE)?

My Answer:

Byte pair encoding is lossy.

Correct Answer:

Byte pair encoding is lossless.

Explanation:
I confused BPE with compression algorithms like JPEG, which are lossy. BPE is lossless, meaning the original data can be perfectly reconstructed. I chose “lossy” because compression often implies some loss, but BPE uses a reversible dictionary replacement process, preserving all original information.

## Q26 — What is the correct pseudocode for moving the robot through the maze?

My Answer:

IF (CAN_MOVE(right)) {
  ROTATE_RIGHT()
  MOVE_FORWARD()
}


Correct Answer:

IF (CAN_MOVE(right)) {
  ROTATE_RIGHT()
}
MOVE_FORWARD()


Explanation:
In my version, the robot only moved when a right turn was possible. The correct version always moves forward, but only rotates right when possible. My error caused the robot to stop prematurely, highlighting the importance of control flow outside conditionals.

## Q28 — How many bits are needed to represent 200 unique characters?

My Answer:

6

Correct Answer:

8

Explanation:
Each additional bit doubles the possible number of combinations. 2^8 = 256 which exceeds 200 while 2^7 = 128 does not. I underestimated the exponential nature of binary growth. The correct answer ensures enough unique combinations to represent all 200 characters.

## Q29 — What is the final output of a given Boolean circuit?

My Answer:

A=false, B=false, C=false, D=true

Correct Answer:

A=true, B=false, C=false, D=false

Explanation:
I misread the order of logical operations in the circuit. Boolean circuits are evaluated using logical precedence (NOT before AND, AND before OR). I likely reversed a gate’s input or output in my reasoning, showing that visualizing gate flow is key in digital logic.

## Q30 — How many hours does the procedure take if Analysis() runs before and inside a loop?

My Answer:

1 hour

Correct Answer:

5 hours

Explanation:
The Analysis() function ran once before the loop, then four additional times inside it. I only counted the first call, missing the repeated calls in the loop. This demonstrates the importance of tracing code execution step-by-step, not just reading line by line.

## Q37 — Comparing two versions of code that calculate averages

My Answer:

Both correct, but II requires more operations.

Correct Answer:

Both correct, but I requires more operations.

Explanation:
Version I performed division inside the loop, meaning it calculated the average each time — inefficient. Version II summed first, then divided once at the end, reducing computational steps. I assumed the opposite because Version II looked longer, but efficiency depends on operation repetition, not line count.

## Q38 — Which code sets cost to 0 every 10th item?

My Answer:

IF (NOT (count MOD 10 = 0)) {
  cost <- 0
}

Correct Answer:

IF (count MOD 10 = 0) {
  cost <- 0
}

Explanation:
My version used the NOT operator incorrectly, inverting the condition. As a result, it triggered the reset for all values except multiples of 10. The correct code uses MOD to detect divisibility directly, a fundamental operation in periodic logic.

## Q40 — Which conclusions can be drawn from student score data?

My Answer:

I and III only

Correct Answer:

I, II, and III

Explanation:
All three statements could be determined from the data provided. I assumed one was irrelevant because I misinterpreted “correlation” as requiring outside data, but the dataset itself allowed all three conclusions. This tested data interpretation, not computation.

## Q42 — How many more unique addresses can IPv6 store compared to IPv4?

My Answer:

96 times as many

Correct Answer:

2^96

 times as many

Explanation:
I treated “96 bits longer” as a linear increase instead of an exponential one. Each bit doubles address capacity, so IPv6 provides 2^96 more unique combinations than IPv4. This mistake highlighted the difference between additive and exponential reasoning in binary systems.

## Q43 — Does the algorithm run in reasonable time?

My Answer:

Runs but not in reasonable time

Correct Answer:

Runs in reasonable time

Explanation:
The algorithm used polynomial time complexity (n²), which is considered efficient for most inputs. I confused polynomial time with exponential time, assuming any “nonlinear” growth was unreasonable. This emphasized the need to review Big-O notation definitions carefully.

## Q45 — What Boolean expression represents a NAND gate?

My Answer:

(NOT P) AND (NOT Q)


Correct Answer:

NOT (P AND Q)


Explanation:
A NAND gate outputs true unless both inputs are true. My answer actually represented a NOR gate, which is true only when both inputs are false. The difference lies in whether the NOT applies before or after the AND operation — order of operations matters greatly in logic design.

## Q50 — Which algorithm performs a binary search?

My Answer:

I only

Correct Answer:

II only

Explanation:
Binary search requires the list to be sorted and works by repeatedly dividing the search interval in half. I misidentified a linear search as binary because both appeared to iterate through data. The correct answer isolates the divide-and-conquer logic that defines binary search efficiency.

## Q54 — Which procedure generalizes Fourth(n) to raise n to any power?

My Answer:

Fourth(n)

Correct Answer:

Power(n, m)

Explanation:
The correct version introduces a second parameter m, allowing any exponent. My answer was specific (only raised to the 4th power) and didn’t generalize the procedure. I focused on familiarity rather than scalability, missing the concept of parameterization in algorithms.

## Q58 — Which statements describe positive effects of the internet?

My Answer:

I and III only

Correct Answer:

I and II only

Explanation:
Statements I and II accurately reflected collaboration and global access. I incorrectly chose III, which described overcoming computational limits — something the internet doesn’t affect directly. The internet improves connectivity, not processing capacity.

## Q64 — Which effects of cloud computing are accurate?

My Answer:

A and C

Correct Answer:

B and C

Explanation:
Cloud computing indeed improves collaboration (B) and introduces security concerns (C). I misread A as an advantage of local computing. This highlighted the importance of distinguishing between cloud-based benefits and local storage advantages when evaluating trade-offs.

## Q65 — When will this loop fail to end?

My Answer:

C and D

Correct Answer:

B and D

Explanation:
The loop failed when y was negative, as the condition never became false. I incorrectly chose C, assuming multiple factors caused the error. Correct reasoning required identifying which variables prevented loop termination, not just any logic issue.

## 9. Something Cool I Learned

- Only 38% of U.S. adults reported having learned how to analyze media messaging (such as advertising or TV programs) in high school.
- A 2024 study found that 82% of teens struggle to differentiate between news, advertisements, opinions, and entertainment.
- This is one of the reasons why we chose to teach about Media Literacy!