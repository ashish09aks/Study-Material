# ARITHMETIC PROGRESSION (AP) - Problem First, Formula Later

```
HOW TO USE THIS MATERIAL

    Every chapter follows the same 5-step rhythm:

        1) PROBLEM        : a question is thrown at you first
        2) TRY IT         : try the slow/brute-force way (feel the pain)
        3) SPOT THE PATTERN : see what repeats
        4) FORMULA IS BORN : the pattern becomes a formula (so you know WHERE it comes from)
        5) CHECK + USE    : verify on a small case, then solve more problems with it

    Rule : never memorize a formula you have not seen being born.
    If you feel like you're not getting something, use LLMs

MENTAL MAP (the story of this whole topic)

    Ch 1 : Spot a pattern               -> what is an AP, what are a and d
    Ch 2 : "What is the 58th term?"     -> listing is too slow -> T(n) = a + (n-1)d
    Ch 3 : "Which term is 99?"          -> run the formula backwards -> number of terms
    Ch 4 : "Add 1 to 100 quickly"       -> Gauss trick -> S(n) formula
    Ch 5 : "Sum is given, find term"    -> T(n) = S(n) - S(n-1)
    Ch 6 : "Is the middle one fair?"    -> 2b = a + c
    Ch 7 : "Sum is given, find numbers" -> symmetric assumption trick
    Ch 8 : Real-life problems           -> everything together
    Ch 9 : Practice (try yourself)
```

---

## CHAPTER 1 : Spot the pattern

### PROBLEM

```
    Ramesh starts saving money in a piggy bank.
        Day 1 : he puts Rs 10
        Day 2 : he puts Rs 15
        Day 3 : he puts Rs 20
        Day 4 : he puts Rs 25
    He keeps following the same habit.

    Q. What do you notice about the amounts?
```

### SPOT THE PATTERN

```
    amounts :  10   15   20   25   .....
                  +5   +5   +5

    every next amount = previous amount + 5   (the GAP is always the same)

    A sequence where the gap between adjacent terms is always the same
    is called an ARITHMETIC PROGRESSION (AP).

    Now compare with a sequence that does NOT behave like that:
        2   4   8   16   ....
          +2  +4  +8        -> the gap keeps changing -> NOT an AP

    NAMES (we will need them from now on)
        first term                 : a      (for Ramesh, a = 10)
        common difference (the gap): d      (for Ramesh, d = 5)
        n_th term                  : T(n)   (T(1) = 10, T(2) = 15, T(3) = 20 ...)
        sum of first n terms       : S(n)   (a sum of a sequence is called a series)

        d = (any term) - (the term just before it)       -> LATER minus EARLIER, always

    Examples  (find a and d yourself before reading the answer)
        1  5  9  13  17 ...        a = 1,   d = 4
        20 15 10 5 ...             a = 20,  d = -5      (d can be negative: decreasing AP)
        7  7  7  7 ...             a = 7,   d = 0       (d can be 0: constant AP)
        1  1.5  2  2.5 ...         a = 1,   d = 0.5     (d can be a decimal or fraction)

    TEST : is  3, 7, 11, 15  an AP?   gaps: 4, 4, 4  -> yes
           is  10, 6, 2, -2  an AP?   gaps: -4, -4, -4 -> yes (d = -4)
           is  1, 4, 9, 16   an AP?   gaps: 3, 5, 7  -> no
```

---

## CHAPTER 2 : "What is the 58th term?"

### PROBLEM

```
    Take the sequence   1  5  9  13  17  21 ....   (a = 1, d = 4)
    Q. What is the 58th term?
```

### TRY IT THE SLOW WAY

```
    Keep adding 4 again and again:
        1, 5, 9, 13, 17, 21, 25, 29, 33, 37, 41, ... (57 times adding 4!)

    This works, but now imagine the question is "what is the 5000th term?"
    There must be a shortcut. Let us look at HOW each term is built.
```

### SPOT THE PATTERN

```
    T(1) = 1                         = a
    T(2) = 1 + 4                     = a + d          (d added 1 time)
    T(3) = 1 + 4 + 4                 = a + 2d         (d added 2 times)
    T(4) = 1 + 4 + 4 + 4             = a + 3d         (d added 3 times)
    T(5) = 1 + 4 + 4 + 4 + 4         = a + 4d         (d added 4 times)

    LOOK at the pattern :
        T(2) has d added 1 time   -> that is (2 - 1)
        T(3) has d added 2 times  -> that is (3 - 1)
        T(4) has d added 3 times  -> that is (4 - 1)

    The number of d's is always ONE LESS than the position.
    (Reason : the first term a is already there, we only need to "walk" n-1 steps to reach the n_th term.)
```

### FORMULA IS BORN

```
    T(n) = a + (n-1)*d

    T(n) = n_th term,  a = first term,  n = position,  d = common difference
```

### CHECK + USE

```
    CHECK on a small case : T(5) = 1 + 4*4 = 17     (our list says 17, correct)

    Back to our problem : 58th term of 1 5 9 13 ...
        a = 1, d = 4, n = 58
        T(58) = 1 + (58 - 1)*4 = 1 + 57*4 = 1 + 228 = 229
        so 229 is the 58th term

    PROBLEM 2 : How much does Ramesh put in the piggy bank on day 30? (10, 15, 20, ...)
        a = 10, d = 5, n = 30
        T(30) = 10 + 29*5 = 10 + 145 = 155        -> Rs 155

    PROBLEM 3 : Find the 20th term of  7, 3, -1, -5, ...
        a = 7, d = 3 - 7 = -4, n = 20
        T(20) = 7 + 19*(-4) = 7 - 76 = -69
        (a negative d works with the same formula, no new rule needed)

    PROBLEM 4 : Find the 15th term of  1/2, 1, 3/2, 2, ...
        a = 1/2, d = 1/2, n = 15
        T(15) = 1/2 + 14*(1/2) = 1/2 + 7 = 7.5
```

---

## CHAPTER 3 : "Which term is 99?" (running the formula backwards)

### PROBLEM A

```
    The sequence  3, 7, 11, 15, ...  continues up to 99.
    Q. How many terms does it have?
```

### TRY IT THE SLOW WAY

```
    List: 3, 7, 11, 15, 19, 23, ... and count until you hit 99. Painful.

    BETTER IDEA : we already know a formula that connects position and value.
    The LAST term l = 99 is just the n_th term, so  T(n) = 99.
```

### FORMULA IS BORN

```
    l = a + (n-1)*d            (last term is the n_th term)
    l - a = (n-1)*d            (move a to the other side)
    (l - a)/d = n - 1          (divide by d)

    n = (l - a)/d + 1          <- number of terms
```

### CHECK + USE

```
    CHECK : 3, 7, 11 (3 terms). a = 3, d = 4, l = 11
            n = (11 - 3)/4 + 1 = 2 + 1 = 3   correct

    Problem A solved : a = 3, d = 4, l = 99
        n = (99 - 3)/4 + 1 = 96/4 + 1 = 24 + 1 = 25 terms

    PROBLEM A2 : how many terms are in  5, 8, 11, ..., 62 ?
        a = 5, d = 3, l = 62
        n = (62 - 5)/3 + 1 = 19 + 1 = 20
```

### PROBLEM B : "Is 150 a term?"

```
    Q. Is 150 a term of  1, 5, 9, 13, ... ?   What about 153 ?

    IDEA : if 150 is a term, it sits at some position n. So put T(n) = 150 and solve for n.
           A position must be a positive WHOLE number (there is no "38.25th" term).

    150 :  1 + (n-1)*4 = 150
           (n-1)*4 = 149
           n - 1 = 37.25   ->  n = 38.25     not a whole number -> 150 is NOT a term

    153 :  1 + (n-1)*4 = 153
           (n-1)*4 = 152
           n - 1 = 38      ->  n = 39        whole number -> 153 IS a term (the 39th)

    PROBLEM B2 : is -100 a term of  40, 35, 30, 25, ... ?
           40 + (n-1)*(-5) = -100
           (n-1)*(-5) = -140
           n - 1 = 28  ->  n = 29           yes, it is the 29th term
```

### PROBLEM C : "Two clues about an unknown AP"

```
    Q. The 5th term of an AP is 17 and the 9th term is 29. Find the AP.

    IDEA : we do not know a and d, but each clue is ONE equation in a and d.
           Two unknowns need two equations.

        T(5) = a + 4d = 17   ...(i)
        T(9) = a + 8d = 29   ...(ii)

        (ii) - (i) :  4d = 12   ->  d = 3         (subtracting kills 'a')
        put d = 3 in (i) :  a + 12 = 17  ->  a = 5

    The AP is  5, 8, 11, 14, 17, ...    and  T(n) = 5 + (n-1)*3 = 3n + 2
    CHECK : T(9) = 3*9 + 2 = 29   correct
```

---

## CHAPTER 4 : "Add 1 to 100 quickly" (the sum formula)

### PROBLEM

```
    Ramesh's friend says: "Add all numbers from 1 to 100 in your head, fast."
        1 + 2 + 3 + ... + 98 + 99 + 100 = ?
    (Famous story: a young Gauss solved this in seconds.)
```

### TRY IT THE SLOW WAY

```
    1 + 2 = 3,  3 + 3 = 6,  6 + 4 = 10, ...   100 additions. Too slow, easy to slip.
```

### SPOT THE PATTERN (the Gauss trick)

```
    Write the sum twice, the second time in REVERSE order, and add them column by column:

        S =   1  +   2  +   3  + ... +  98  +  99  + 100
        S = 100  +  99  +  98  + ... +   3  +   2  +   1
        ------------------------------------------------
       2S = 101  + 101  + 101  + ... + 101  + 101  + 101

    Every column adds to 101, and there are 100 columns.
        2S = 100 * 101     ->     S = 100*101/2 = 5050
```

### FORMULA IS BORN (do the same trick on a general AP)

```
    S(n) = a + (a+d) + (a+2d) + ...... + (l-d) + l          (l = last term)
    S(n) = l + (l-d) + (l-2d) + ...... + (a+d) + a          (same sum, reversed)
    -----------------------------------------------------
    2*S  = (a+l) + (a+l) + (a+l) + ...... + (a+l) + (a+l)   (every column = a + l)

    There are n columns (one for each term), so

        2*S = n*(a + l)

        S(n) = (n/2)*(a + l)                    <- FORM 1 (use when the last term is known)

    And since the last term is l = a + (n-1)*d (Chapter 2), put it in:

        S(n) = (n/2)*(a + a + (n-1)*d)

        S(n) = (n/2)*(2a + (n-1)*d)             <- FORM 2 (use when d is known, l is not)
```

### CHECK + USE

```
    CHECK by hand : first 4 terms of 1 5 9 13  ->  1 + 5 + 9 + 13 = 28
        Form 2 :  a = 1, d = 4, n = 4
                  S(4) = (4/2)*(2*1 + 3*4) = 2*14 = 28    correct

    PROBLEM 1 : find the sum of the first 10 terms of  1 5 9 13 ...
        a = 1, n = 10, d = 4
        S(10) = (10/2)*(2*1 + 9*4) = 5*(2 + 36) = 5*38 = 190
        (sanity check with the pair idea: terms are 1,5,...,37 ; 1+37 = 5+33 = ... = 38 ; 5 pairs -> 190)

    PROBLEM 2 : how much has Ramesh saved in 30 days?  (10, 15, 20, ... , d = 5)
        a = 10, d = 5, n = 30
        S(30) = (30/2)*(2*10 + 29*5) = 15*(20 + 145) = 15*165 = 2475      -> Rs 2475
        cross-check with Form 1 : last term = T(30) = 155 (Chapter 2)
        S = 15*(10 + 155) = 15*165 = 2475     same answer

    PROBLEM 3 : find the sum  5 + 8 + 11 + ... + 62
        last term is given -> first find n (Chapter 3):  n = (62 - 5)/3 + 1 = 20
        S = (20/2)*(5 + 62) = 10*67 = 670

    PROBLEM 4 : find the sum of all multiples of 7 between 1 and 100
        multiples : 7, 14, 21, ..., 98       a = 7, d = 7, l = 98
        n = (98 - 7)/7 + 1 = 14
        S = (14/2)*(7 + 98) = 7*105 = 735

    PROBLEM 5 : find the sum of the first n natural numbers 1 + 2 + ... + n
        a = 1, d = 1, l = n
        S = (n/2)*(1 + n) = n(n+1)/2          (for n = 100 : 100*101/2 = 5050, our first problem)

    WHICH FORM SHOULD I PICK?
        last term known      -> S = (n/2)*(a + l)
        last term not known  -> S = (n/2)*(2a + (n-1)*d)
```

---




## CHAPTER 8 : Real-life problems (everything together)

```
    How to recognise an AP word problem :
        "increases by a FIXED amount", "each row has 2 more seats", "5 more pages every day"
        -> same amount added each time -> AP

    PROBLEM 1 : A hall has 25 rows. The first row has 20 seats and every next row has 2 more seats.
                (a) How many seats are in the last row?
                (b) How many seats are there in total?
                (c) Which row has 50 seats?

        a = 20, d = 2, n = 25

        (a) last row = T(25) = 20 + 24*2 = 68                      (Chapter 2 formula)
        (b) total = (25/2)*(20 + 68) = 25*44 = 1100                (Chapter 4, last term known)
            cross-check : (25/2)*(2*20 + 24*2) = (25/2)*88 = 1100   same
        (c) 20 + (n-1)*2 = 50 -> n - 1 = 15 -> n = 16              (Chapter 3 idea)
            the 16th row has 50 seats

    PROBLEM 2 : A person saves Rs 100 in the first month and Rs 20 more every month than the
                previous month. How much has he saved in 12 months?
        a = 100, d = 20, n = 12
        S(12) = (12/2)*(2*100 + 11*20) = 6*420 = 2520              -> Rs 2520
```

---

## QUICK REVISION (after you have understood, not before)

```
    n_th term               : T(n) = a + (n-1)*d            (add d, n-1 times)
    number of terms         : n = (l - a)/d + 1             (T(n) = l, solved for n)
    sum (last term known)   : S(n) = (n/2)*(a + l)          (Gauss pairing)
    sum (d known)           : S(n) = (n/2)*(2a + (n-1)*d)   (put l = a + (n-1)d)
    term from sum           : T(n) = S(n) - S(n-1)          (today = total - yesterday's total)
    middle term             : 2b = a + c                    (gap before = gap after)
    smart assumption        : 3 terms -> a-d, a, a+d ; 4 terms -> a-3d, a-d, a+d, a+3d

    COMMON MISTAKES
        1) using n instead of (n-1) in T(n)
        2) d = EARLIER - LATER (sign flipped)  -> always LATER minus EARLIER
        3) not checking that n is a whole number in "is X a term?"
        4) in sum problems, putting the last term where the NUMBER of terms should go
```

---

## CHAPTER 9 : PRACTICE QUESTIONS

> **DISCLAIMER:** Solve every question first on your own, on paper. Only after you have
> made a real attempt, give the question to any LLM to know the answer and compare
> your working with it. Do not skip the struggle, that is where the learning happens.
>
> TIP : whenever you get stuck, ask yourself "which chapter's PROBLEM does this look like?"

```
LEVEL 1 : Warm-up (Chapters 1 and 2)

    Q1.  Find the 25th term of the AP  3, 8, 13, 18, ...
    Q2.  Find the 10th term of the AP  20, 17, 14, 11, ...
    Q3.  Check whether  4, 10, 16, 22, ...  is an AP. If yes, write a and d.
    Q4.  Find the sum of the first 15 terms of  4, 9, 14, 19, ...

LEVEL 2 : Run it backwards (Chapters 3 and 4)

    Q5.  Which term of the AP  2, 9, 16, 23, ...  is 247 ?
    Q6.  How many terms are there in the AP  12, 18, 24, ..., 300 ?
    Q7.  Is 301 a term of the AP  4, 11, 18, 25, ... ?  Justify.
    Q8.  The 3rd term of an AP is 14 and the 8th term is 39. Find a, d and the 20th term.
    Q9.  Find the sum  1 + 3 + 5 + ... + 99  (odd numbers up to 99).

LEVEL 3 : Think a little (Chapters 5, 6, 7, 8)

    Q10. The sum of the first n terms of an AP is  S(n) = n^2 + 4n.
         Find the n_th term and the 10th term.
    Q11. Find the sum of all 3-digit numbers which are multiples of 9.
    Q12. A person saves Rs 500 in the first month and Rs 50 more each month than the previous
         month. How much will he have saved in 2 years?

LEVEL 4 : Challenge (derive it yourself, as we did in the chapters)

    Q13. Show that the sum of the first n odd numbers is n^2.
         (hint : which AP is this? what are a and d? which sum form is easier?)
```

---

*Remember the story : an AP is built by adding the same d again and again.
Every formula in this chapter is just that one idea, viewed from a different side.*