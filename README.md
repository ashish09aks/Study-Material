- [Roadmap Sheet](https://docs.google.com/spreadsheets/d/133mPyXA-dGDM94rTUFvJmdR6Cz5MyoEyykJcR1s5MBs/edit?usp=sharing)

# Guideline for Problem Solving (DSA & Competitive Programming)

A practical guide on **how to practice**: how to attack a problem, how long to struggle, what to do when you are stuck, and how to turn every problem into a lesson.

---

## Table of Contents

1. Mindset and Goal of Practice
2. How to Read a Problem
3. A Step-by-Step Problem-Solving Framework
4. Time Boxing: How Long Before You Look at a Solution
5. What to Do When You Have No Ideas
6. How to Use Editorials and Solutions the Right Way
7. Debugging and Testing
8. Learning Topic-Wise vs Problem-Wise
9. Building a Practice Routine
10. Contest Strategy (CP)
11. Tracking Progress
12. Common Mistakes Students Make
13. Good Habits and Tools
14. Quick Checklist and One-Page Summary

---

## 1. Mindset and Goal of Practice

**The goal is not to solve many problems. The goal is to become a person who can solve problems you have never seen.**

- **Learning per problem matters more than problem count.** One problem you struggled with, understood deeply and can re-solve a week later is worth more than ten problems you solved by copying an idea.
- **Struggle is the training.** Your brain builds problem-solving skill only while it is trying and failing. If every problem feels easy, you are not improving. If every problem feels impossible, the level is too high. Aim for problems where you get stuck but can eventually make progress (roughly 40-60% of the time you can solve them yourself).
- **Consistency beats cramming.** 1-2 hours every day for three months is far better than 12 hours once a week. Skill needs repeated exposure and sleep.
- **Ratings and streaks are side effects, not goals.** Do not compare your day 30 with someone else's year 3.
- **Mistakes are data.** Every wrong answer tells you which idea, edge case or habit needs work.

---

## 2. How to Read a Problem

Most wrong answers begin with misreading. Spend the first 2-5 minutes reading, not coding.

**Read twice.** The first read gives the story. The second read picks out the exact rules: what is given, what is asked, what is guaranteed.

**Extract these items on paper:**

- **Input:** what are the variables and what do they mean?
- **Output:** exactly what must be printed (a number, YES/NO, a list, the lexicographically smallest answer, any valid answer?)
- **Constraints:** the limits on n, on values, and on the number of test cases.
- **Special words:** "distinct", "non-empty", "subsequence" vs "subarray", "at most" vs "exactly", "modulo 10^9+7", "1-indexed".

**Dry-run the sample tests by hand.** Make sure you can produce the sample output yourself. If you cannot, you have not understood the problem.

**Use constraints to guess the intended complexity.**

A typical judge executes about 10^8 simple operations per second (rough rule).

| Constraint on n | Likely intended complexity | Typical tools |
|---|---|---|
| n <= 10 | O(n!) | permutations, brute force |
| n <= 20 | O(2^n) | bitmask, subsets, meet in the middle |
| n <= 500 | O(n^3) | triple loops, Floyd-Warshall, interval DP |
| n <= 5,000 | O(n^2) | double loops, simple DP |
| n <= 10^5 | O(n log n) | sorting, binary search, heap, segment tree |
| n <= 10^6 | O(n) or O(n log n) | linear scan, two pointers, prefix sums, sieve |
| n <= 10^9 | O(sqrt n) or O(log n) | math, binary search on the answer, fast exponentiation |
| n <= 10^18 | O(log n) or O(1) | formula, number theory |

This table is a heuristic. It tells you what to try first, not what must be true.

**Example.** "Given n <= 10^5 numbers, find a pair with the maximum sum less than K." n = 10^5 rules out O(n^2) (about 10^10 operations). So think of sorting plus two pointers or binary search.

---

## 3. A Step-by-Step Problem-Solving Framework

Use the same recipe on every problem so that it becomes automatic.

```
 1. UNDERSTAND  -> restate the problem in your own words, dry-run the samples
 2. BRUTE FORCE -> describe (or write) the simplest correct solution, ignoring speed
 3. BOTTLENECK  -> where is the brute force wasting work? what repeats?
 4. OPTIMISE    -> use a data structure, an observation, a pattern, or a known technique
 5. VERIFY      -> prove it on paper: why is it correct? how fast is it?
 6. CODE        -> write clean code from the verified idea
 7. TEST        -> samples, edge cases, then a stress test against the brute force
```

### Worked example

**Problem.** Given an array of n integers (n <= 10^5), count the pairs (i, j) with i < j and a[i] + a[j] = K.

1. **Understand.** Pairs of positions, not values. For a = [1, 2, 3, 2], K = 4 the pairs are (1,3) and (2,4) -> answer 2.
2. **Brute force.** Check all pairs. O(n^2) = 10^10 for n = 10^5. Too slow, but it is correct and will be used later as a test oracle.
3. **Bottleneck.** For every i we scan all j to find a[j] = K - a[i]. That "search for a value" is repeated work.
4. **Optimise.** Sort the array and use two pointers, or keep a count of values seen so far (in a sorted array plus binary search, or in a hashing structure). Use the one allowed in your course. Sorting plus two pointers gives O(n log n). Care is needed when equal values form many pairs (count by groups).
5. **Verify.** Why is two pointers correct? When the sum is too small the left pointer must move right, because moving the right pointer left can only make it smaller. State this out loud.
6. **Code.** Now write it.
7. **Test.** Samples, then all-equal values, n = 1, n = 2, large values (the count can reach about 5*10^9, so use `long long`), and then a random stress test against the O(n^2) code.

The important habit: **never start typing code until you can explain the idea in two or three sentences.**

---

## 4. Time Boxing: How Long Before You Look at a Solution

Without a rule, students give up after 5 minutes (too early, no learning) or stare for 3 hours (too long, no progress). Use a time box.

### Suggested time limits (per problem, before reading any hint)

| Problem difficulty (for you) | Think + try | Then |
|---|---|---|
| Easy | 20-30 min | take a small hint |
| Medium | 40-60 min | take a small hint |
| Hard | 60-90 min | take a small hint, then split the effort over 2 days |
| Contest (live) | see Section 10 | |

Adjust these numbers to your level: beginners use the lower end, strong students can use the upper end.

### Productive struggle vs wasted time

**Productive** (keep going):
- You are trying new small cases, drawing pictures, testing ideas, finding why an idea fails.
- Each 10 minutes leaves you with new information.

**Wasted** (stop and move to Section 5 or 6):
- You are re-reading the same statement without writing anything.
- You keep trying the same idea that already failed.
- You are tired or distracted.
- You are stuck on a prerequisite you simply do not know (for example, you have never seen binary search on answer). No amount of thinking will invent a technique you were never taught. Learn the technique, then return.

### The "15-minute check"

Every 15 minutes ask: *"What new thing did I learn about this problem in the last 15 minutes?"* If the answer is "nothing", change your approach (draw, simplify, try small cases, or take a hint).

### Escalation ladder (do not jump to the full solution)

1. Think and try for the full time box.
2. Sleep on it. Take a walk. Return the next day if the problem is hard (the brain keeps working in the background).
3. Read **only the tags** (topic names) or **only the first hint**.
4. Try again for 15-20 minutes.
5. Read the editorial's idea (not the code).
6. Code the solution **yourself** without looking.
7. Only if still stuck: read the code, then rewrite it later from memory.

---

## 5. What to Do When You Have No Ideas

Run through this checklist **in order**. Most "no idea" moments are fixed by steps 1-4.

1. **Re-read the statement.** Underline every constraint. Is there something you have been ignoring (for example "the array is sorted", "all numbers are distinct", "n is small")?
2. **Solve small cases by hand.** Take n = 1, 2, 3, 4 and compute the answer manually. Write the answers in a table and look for a pattern.
3. **Write the brute force.** Even if it is slow, it shows you what you are computing and often reveals what repeats. The brute force is also your test oracle later.
4. **Ask what repeats.** Overlapping subproblems point to DP. Repeated range queries point to prefix sums or a data structure. Repeated searches point to sorting plus binary search or hashing-like counting.
5. **Simplify the problem.**
   - Remove a constraint (what if there were no K? what if the array were sorted?).
   - Solve it for a special case (all values equal, all values 0/1, a path instead of a tree).
   - Reduce the dimension (solve it in 1D before 2D).
6. **Change the viewpoint.**
   - Work backwards from the answer.
   - Fix one element and count/choose the rest (contribution technique: "how many times does each element contribute to the answer?").
   - Think about the answer instead of the input: "can the answer be X?" -> binary search on the answer.
   - Sort the data and see whether the problem becomes easier.
7. **Draw it.** Arrays as boxes, graphs as dots and arrows, grids as grids. Many ideas are visual.
8. **Compare with known problems.** "Where have I seen this shape?" Does it look like two pointers, prefix sums, greedy with sorting, a DP on prefixes, BFS on a grid, a graph shortest path?
9. **Check the bounds again.** The constraints often name the technique (Section 2).
10. **Take a break.** A 10-30 minute walk, water, a short sleep. Diffuse thinking often produces the idea you could not force.
11. **Explain it to someone** (a friend, or a rubber duck on your desk). Saying it out loud exposes the gap.
12. **Take one hint**, then go back to your own thinking (Section 6).

### A short self-interview you can use

- What exactly is being asked?
- What is the simplest correct (even slow) solution?
- Why is it slow?
- What information am I computing again and again?
- What happens in the smallest, biggest and weirdest case?
- Which topic do the constraints point to?

---

## 6. How to Use Editorials and Solutions the Right Way

Reading solutions is not a failure. Reading them **in the wrong way** is.

**Bad way:** open the solution, read the code, nod, move on. You will remember nothing.

**Good way:**

1. **Hint first.** Read only the first hint or only the tags. Close the page and try again.
2. **Idea, not code.** If you still need more, read the explanation of the approach. Stop before the code.
3. **Close the editorial and write the code yourself.** If you cannot, you have not understood the idea yet. Read again.
4. **After it is accepted, ask:**
   - Why does this work? (Can I prove it?)
   - What was the key observation I was missing?
   - Which technique/pattern is this an example of?
   - Is there a simpler solution? (Look at other accepted solutions *after* you have your own.)
5. **Write a 2-3 line note** in your mistake log (Section 11): the idea in your own words.
6. **Re-solve it from scratch** after 3-7 days, and again after 3-4 weeks. If you can do it without help, it is learned. If not, repeat.

**Rule of thumb:** *a problem is not "done" when it is accepted. It is done when you can solve it again from a blank screen.*

---

## 7. Debugging and Testing

### Understand the verdict

| Verdict | Usual causes |
|---|---|
| Wrong Answer (WA) | wrong logic, missed edge case, integer overflow, wrong output format, uninitialised variable |
| Time Limit Exceeded (TLE) | too slow complexity, hidden O(n) inside a loop, slow input/output |
| Runtime Error (RE) | array out of bounds, division by zero, deep recursion (stack overflow), negative index |
| Memory Limit Exceeded (MLE) | arrays too big, unnecessary copies |
| Compilation Error | syntax/type errors, missing includes |

### Common bugs checklist

- **Overflow:** products and sums above about 2*10^9 need `long long`. Check intermediate results too (for example `a * b` before the modulo).
- **Off-by-one:** loop bounds (`<` vs `<=`), 0-indexed vs 1-indexed, prefix sum sizes.
- **Uninitialised variables / arrays** that are not reset between test cases.
- **Wrong data type:** integer division where a real number is wanted, `int` index overflow.
- **Edge cases:** n = 1, empty result, all elements equal, already sorted, maximum values, negative numbers, zeros.
- **Modulo mistakes:** forgetting to take the modulo after each multiplication; negative values after subtraction (add the modulus before taking `%`).
- **Reading input wrongly:** extra test cases, wrong order of variables.
- **Wrong assumption** that the answer always exists, or that values are distinct.

### Debugging method

1. Re-read the statement once more (misreading is the number one cause of WA).
2. Run the samples. They must pass.
3. **Make your own small tests**, especially edge cases.
4. **Print intermediate values** and compare them with what you computed by hand.
5. **Stress test** (the most powerful tool, see below).

### Stress testing (find the failing case yourself)

You need three programs:

- `brute`: slow but obviously correct.
- `fast`: your solution.
- `gen`: a random small test generator.

Loop: generate a test, run both, compare outputs. When they differ, you have a **small failing test**, and small tests are easy to trace by hand.

```bash
# Linux/macOS example
for i in $(seq 1 1000); do
    ./gen $i > in.txt
    ./brute < in.txt > out1.txt
    ./fast  < in.txt > out2.txt
    if ! cmp -s out1.txt out2.txt; then
        echo "Difference found on seed $i"
        break
    fi
done
```

Use tiny sizes (n <= 6, values <= 10) so that failures are easy to read.

### When to trust your code

After it passes: samples, your edge cases, and (for important problems) a stress test with hundreds or thousands of random cases.

---

## 8. Learning Topic-Wise vs Problem-Wise

Both are needed, in this order:

1. **Learn the concept** (read an article or watch a lecture, understand the idea and the code).
2. **Practice that topic** with 8-10 graded problems: first 2-3 easy (apply the idea as it is), then 3-4 medium (idea plus a twist), then 2-3 harder (idea plus another idea).
3. **Mixed practice.** Once you know several topics, solve random problems without topic tags. This is where you learn to *recognise* which technique applies, which is the real skill in contests and interviews.

### A sensible topic order

```
Level 1 : basics: loops, arrays, strings, simple math, input/output
Level 2 : sorting, binary search, prefix sums, two pointers, frequency counting
Level 3 : recursion and backtracking, bit manipulation, number theory basics (gcd, primes, sieve, modular arithmetic)
Level 4 : greedy, stacks and queues, heaps, intervals
Level 5 : dynamic programming (1D -> 2D -> knapsack -> on strings -> on subsequences)
Level 6 : graphs (BFS, DFS, shortest paths, DSU, topological sort), trees
Level 7 : advanced (segment trees, tries, DP on trees/bitmasks, string algorithms, advanced math)
```

Do not skip levels. Do not stay in one level forever either: after you can solve most Level N problems in the time box, move on, and come back through mixed practice.

---

## 9. Building a Practice Routine

### Principles

- **Fixed daily time**, even if short (60-90 minutes is enough when focused).
- **Phone away** during the session. Deep focus is the main multiplier.
- **Balance** the three kinds of work: new learning, practice, revision.

### Sample weekly plan (about 1.5 hours per day)

| Day | Focus |
|---|---|
| Mon | Learn a new concept (30 min) + 2 easy problems on it |
| Tue | 2-3 problems on the same concept (one medium) |
| Wed | 2 problems of mixed topics + review the mistake log |
| Thu | Learn or deepen one more concept + 2 problems |
| Fri | Re-solve 2-3 old problems from your log (no help) |
| Sat | Virtual contest or a set of 3-4 mixed problems (timed) |
| Sun | Upsolve the unsolved problems, update your notes, rest/light reading |

### Difficulty mix per week (guideline)

- About 50% problems that you can solve with some effort (your comfort level).
- About 30% problems one step above your level (this is where improvement happens).
- About 20% easy problems (confidence, speed and revision).

### Revision

- Keep a **revision list** of problems you needed help with.
- Re-solve them after **3-7 days**, then **3-4 weeks**, then again after **2-3 months**.
- Revise **ideas**, not just code: for each one, say the key observation in one line.

---

## 10. Contest Strategy (CP)

### Before the contest

- Sleep well. Have your template ready (fast input/output, common includes), water, and a pen and paper.
- Decide the language and stick to it.

### During the contest

1. **Read all problems quickly** (the first 5-10 minutes) or at least the first 3-4. Order them by how solvable they look for *you*, not by position.
2. **Solve in order of ease.** Do not get stuck on one problem while an easier one is waiting.
3. **Time box inside a contest:** if you have no progress on a problem after about 20-25 minutes, switch to another and come back later.
4. **Think before coding.** Five minutes of thinking saves twenty minutes of debugging. Verify the idea against the samples and one extra case.
5. **Write simple, clean code.** Avoid fancy tricks. Prefer a slightly slower solution that is obviously correct if it fits the limits.
6. **Test before submitting:** samples plus 1-2 edge cases. A penalty costs time.
7. **If a submission fails:** re-read the statement, check overflow and edge cases, and do not resubmit blindly. If you are stuck, move on and return later.
8. **Do not look at the scoreboard obsessively.** It affects your mood and not your problem-solving.

### After the contest (the most important part)

- **Upsolve:** solve every problem you could not solve during the contest, within 1-2 days, using the escalation ladder from Section 4.
- Read the editorial for the problems you did solve too: there is often a cleaner idea.
- Write down: What did I miss? Was it a topic gap, a bug, a misread, or a time-management issue?
- Rating drops are normal. Judge yourself by what you learned, not by the number.

### Practice contests

Use **virtual contests** (past contests with a timer) once a week. They train speed, decisions under pressure and stamina.

---

## 11. Tracking Progress

What is not written down is forgotten. Keep a **notebook or a document** (the **mistake log**).

### Template for each problem

```
Problem      : (name + link)
Date         : 
Difficulty   : easy / medium / hard (for me)
Topic(s)     : 
Result       : solved alone / solved with hint / solved after editorial / failed
Time spent   : 
Key idea     : (one or two lines in my own words)
Mistake / what blocked me : (misread? missing technique? bug? overflow?)
What I will do differently : 
Revise on    : (date)
```

### Weekly review (15 minutes every Sunday)

- How many problems did I solve alone vs with help?
- Which topics keep appearing in my "blocked" notes? -> those are my **weak topics**.
- Plan next week: pick 1-2 weak topics and schedule focused practice.
- Look for patterns in mistakes: if overflow caused three WAs, make "check types" a habit.

### Measure the right things

- **Percentage solved without help** (should slowly go up).
- **Time to solve** problems of the same level (should go down).
- **Topics you can explain** to a friend.
- Not just the total count or the rating.

---

## 12. Common Mistakes Students Make

1. **Looking at the editorial too early** and learning nothing. (See Section 4: time boxes.)
2. **Never looking at it** and wasting days on a problem with a missing prerequisite.
3. **Solving only easy problems** because they feel good. Growth needs discomfort.
4. **Solving only very hard problems** and getting demotivated. Stay near your level.
5. **Jumping topics** every day without finishing any, or **staying on one topic** for months.
6. **Copying code** that you do not understand.
7. **Coding before thinking.** Typing feels productive but is often just guessing.
8. **Skipping edge cases and overflow checks.**
9. **Not revising.** Solving a problem once and never seeing it again.
10. **Comparing yourself** to people who started years earlier.
11. **Practising passively:** watching lecture after lecture without solving problems. Watching is not practising.
12. **Ignoring fundamentals** (complexity analysis, basic maths) and then struggling with every harder topic.
13. **Not stress testing** and relying on "it passed the samples".
14. **Giving up after a bad contest** instead of learning from it.

---

## 13. Good Habits and Tools

### Code habits

- Use **meaningful variable names** and short functions for repeated logic.
- Keep a personal **template** (fast input/output, common includes, typedefs) and a small **library of snippets** you wrote yourself (gcd, sieve, DSU, binary search, modular power).
- **Comment the idea**, not the obvious. A one-line comment on *why* something is correct helps your future self.
- Learn the **standard library** of your language (sorting, vectors/lists, strings, math functions) so that you do not waste time re-implementing.
- Practise **typing speed and accuracy**: a small but real advantage in contests.

### Thinking habits

- Always compute the **time and space complexity** of your idea before coding.
- Say the **invariant** or the proof in one sentence (for example, "the left pointer never has to move back because...").
- Think about **edge cases first**, before the code, not after the failure.

### Trusted resources

- **Practice platforms:** Codeforces, LeetCode, AtCoder, CodeChef, CSES Problem Set (a very good curated set), HackerRank.
- **Learning material:** cp-algorithms (clear articles on algorithms), your course notes, well-known textbooks and lecture series.
- **Editorials and other people's solutions** (after your own attempt).

### Study group

- Discuss solved problems with friends: explaining an idea is the best test of understanding.
- Set small shared goals (for example, a weekly virtual contest together).
- Do not copy; **discuss ideas**, not code.

---

## 14. Quick Checklist and One-Page Summary

### Before solving

- [ ] Read the statement twice. Do I know exactly what is asked?
- [ ] Wrote down input, output, constraints and special words.
- [ ] Dry-ran the sample by hand.
- [ ] Guessed the intended complexity from the constraints.

### While solving

- [ ] Thought of (or wrote) a brute force.
- [ ] Found the bottleneck (what repeats?).
- [ ] Tried small cases and a drawing.
- [ ] Time box running: 15-minute check "what did I learn?".
- [ ] Can explain the idea in 2-3 sentences and argue why it is correct.
- [ ] Checked complexity, types (overflow) and edge cases *before* coding.

### If stuck

- [ ] Re-read, simplify, try small cases, change viewpoint.
- [ ] Took a break or slept on it.
- [ ] Took **one hint** only, then tried again.
- [ ] Read the idea (not the code), then wrote the code myself.

### After solving

- [ ] Wrote the key idea in my own words in the mistake log.
- [ ] Noted what blocked me (topic gap, bug, misread, time).
- [ ] Scheduled a re-solve after 3-7 days and again after a month.
- [ ] Looked at other solutions *after* mine to learn a cleaner way.

### The one-page summary

```
1. Goal      : learn to solve NEW problems, not to collect solved problems.
2. Read      : twice. Extract input, output, constraints. Dry-run samples.
3. Frame     : understand -> brute force -> bottleneck -> optimise -> verify -> code -> test.
4. Time box  : easy 20-30 min, medium 40-60, hard 60-90, then ONE hint, not the whole solution.
5. Stuck?    : small cases, simplify, draw, what repeats?, change viewpoint, break, then a hint.
6. Editorial : hint -> idea -> write code yourself -> re-solve later.
7. Debug     : check overflow, off-by-one, edge cases; stress test against brute force.
8. Learn     : concept first, then 8-10 graded problems, then mixed practice.
9. Routine   : daily, focused, balanced between learning, practice and revision.
10. Contests : easy first, think before coding, upsolve afterwards.
11. Track    : mistake log + weekly review + revision schedule.
12. Avoid    : early editorials, only-easy problems, copying, no revision, comparison.
13. Habits   : templates, clean code, complexity check, discuss ideas with friends.
```

> **Remember:** Improvement comes from *deliberate* practice: solving at the edge of your ability, getting stuck, reflecting, and returning. Be patient and consistent, and the results will follow.