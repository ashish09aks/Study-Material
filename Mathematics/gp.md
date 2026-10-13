# GEOMETRIC PROGRESSION (GP) - Problem First, Formula Later

```
HOW TO USE THIS MATERIAL

    Same 5-step rhythm as the AP material, in every chapter:

        1) PROBLEM          : a question is thrown at you first
        2) TRY IT           : try the slow/brute-force way (feel the pain)
        3) SPOT THE PATTERN : see what repeats
        4) FORMULA IS BORN  : the pattern becomes a formula (so you know WHERE it comes from)
        5) CHECK + USE      : verify on a small case, then solve MANY more examples

    Rule : never memorize a formula you have not seen being born.

    ONE-LINE DIFFERENCE FROM AP (keep this in your head the whole time)
        AP : next term = previous term  +  d      (we ADD the same number)
        GP : next term = previous term  *  r      (we MULTIPLY by the same number)

MENTAL MAP (the story of this whole topic)

    Ch 1 : Spot a pattern                -> what is a GP, what are a and r
    Ch 2 : "How many bacteria after 10 hours?" -> T(n) = a * r^(n-1)
    Ch 3 : "Which term is 768?"          -> run it backwards -> position, is-it-a-term, find the GP
    Ch 4 : "Total of a doubling habit"   -> shift-and-subtract trick -> S(n) formula
    Ch 5 : "Add forever?"                -> infinite GP -> S = a/(1 - r)
    Ch 6 : "Sum is given, find the term" -> T(n) = S(n) - S(n-1)  (same idea as AP)
    Ch 7 : "Is the middle one fair?"     -> b^2 = a*c
    Ch 8 : "Sum and product are given"   -> symmetric assumption  a/r, a, a*r
    Ch 9 : Real-life problems            -> growth, decay, interest, spreading
    Ch 10: AP vs GP side by side + revision
    Ch 11: Practice (try yourself)
```

---

## CHAPTER 1 : Spot the pattern

### PROBLEM

```
    Ramesh has a new savings habit :
        Day 1 : he puts Rs 1
        Day 2 : he puts Rs 2
        Day 3 : he puts Rs 4
        Day 4 : he puts Rs 8
    He keeps following the same habit.

    Q. What is the habit?  Is it "add the same amount every day"?
```

### SPOT THE PATTERN

```
    amounts :  1    2    4    8    ....
               +1   +2   +4          <- the gap keeps CHANGING, so this is NOT an AP

    Try dividing instead of subtracting :
               2/1  4/2  8/4
                2    2    2          <- the RATIO is always the same!

    So here every term = previous term * 2.

    A sequence where the ratio of adjacent terms is always the same is called
    a GEOMETRIC PROGRESSION (GP).

    NAMES
        first term                  : a      (for Ramesh, a = 1)
        common ratio                : r      (for Ramesh, r = 2)
        n_th term                   : T(n)
        sum of first n terms        : S(n)

        r = (any term) / (the term just before it)       -> LATER divided by EARLIER, always
```

### MORE EXAMPLES (find a and r yourself before reading the answer)

Find a & r by yourself and verify your answer

```
    1)  3, 6, 12, 24, ...              a = 3,   r = 6/3 = 2             (growing GP)
    2)  2, 6, 18, 54, ...              a = 2,   r = 6/2 = 3
    3)  81, 27, 9, 3, ...              a = 81,  r = 27/81 = 1/3         (r between 0 and 1 : shrinking GP)
    4)  5, -10, 20, -40, ...           a = 5,   r = -10/5 = -2          (negative r : signs alternate + - + -)
    5)  7, 7, 7, 7, ...                a = 7,   r = 1                   (r = 1 : constant sequence)
    6)  2, 3, 4.5, 6.75, ...           a = 2,   r = 3/2 = 1.5           (r can be a fraction or decimal)
    7)  1000, 100, 10, 1, ...          a = 1000, r = 1/10

    NOTE : a sequence like 7, 7, 7, 7 is BOTH an AP (d = 0) and a GP (r = 1).
```

### TEST : is it a GP?
You have to find the answers yourself

```
    Find ALL the adjacent ratios. If every one is the same -> GP, otherwise NOT a GP.

    is  3, 12, 48, 192  a GP ?     ratios: 4, 4, 4              -> yes
    is  1, 2, 3, 4      a GP ?     ratios: 2, 1.5, 1.33...      -> no  (it is an AP though!)
    is  2, 4, 6, 8      a GP ?     ratios: 2, 1.5, 1.33...      -> no  (also an AP)
    is  16, -8, 4, -2   a GP ?     ratios: -1/2, -1/2, -1/2     -> yes (r = -1/2)
    is  1, 4, 9, 16     a GP ?     ratios: 4, 2.25, 1.78        -> no  (squares, neither AP nor GP)
```

---

## CHAPTER 2 : "How many bacteria after 10 hours?" (the n_th term)

### PROBLEM

```
    A lab starts with 3 bacteria. The number doubles every hour.
        start      : 3
        after 1 hr : 6
        after 2 hr : 12
        after 3 hr : 24
    Q. How many bacteria are there at the 10th term of this sequence 3, 6, 12, 24, ... ?
       (a = 3, r = 2)
```

### TRY IT THE SLOW WAY

```
    Keep doubling:  3, 6, 12, 24, 48, 96, 192, 384, 768, 1536
    10 numbers is fine. But what about the 40th term? There must be a shortcut.
    Look at HOW each term is built.
```

### SPOT THE PATTERN

```
    T(1) = 3                          = a
    T(2) = 3 * 2                      = a * r          (r multiplied 1 time)
    T(3) = 3 * 2 * 2                  = a * r^2        (r multiplied 2 times)
    T(4) = 3 * 2 * 2 * 2              = a * r^3        (r multiplied 3 times)
    T(5) = 3 * 2 * 2 * 2 * 2          = a * r^4        (r multiplied 4 times)

    LOOK at the pattern :
        T(2) has r multiplied 1 time   -> that is (2 - 1)
        T(3) has r multiplied 2 times  -> that is (3 - 1)
        T(4) has r multiplied 3 times  -> that is (4 - 1)

    The power of r is always ONE LESS than the position.
    (Same reason as in AP : the first term a is already there, we only "walk" n-1 steps.)
```

### FORMULA IS BORN

T(n) = a * $r^{(n-1)}$

    T(n) = n_th term,  
    a = first term,  
    r = common ratio,  
    n = position


### CHECK + USE

```
    CHECK on a small case : T(4) = 3 * 2^3 = 24     (our list says 24, correct, 4th term is 24)

    Example 1 : the 10th term of  3, 6, 12, 24, ...
        T(10) = 3 * 2^9 = 3 * 512 = 1536     (matches the slow list!)

    Example 2 : the 7th term of  2, 6, 18, 54, ...
        a = 2, r = 3
        T(7) = 2 * 3^6 = 2 * 729 = 1458

    Example 3 : the 8th term of  81, 27, 9, 3, ...
        a = 81, r = 1/3
        T(8) = 81 * (1/3)^7 = 3^4 / 3^7 = 1 / 3^3 = 1/27

    Example 4 : the 6th term of  5, -10, 20, -40, ...
        a = 5, r = -2
        T(6) = 5 * (-2)^5 = 5 * (-32) = -160      (odd power of a negative number stays negative)

    Example 5 : the 5th term of  1000, 100, 10, 1, ...
        a = 1000, r = 1/10
        T(5) = 1000 * (1/10)^4 = 1000/10000 = 0.1

    Example 6 (real-life) : a ball is dropped from 160 m. After each bounce it rises to 1/2 of
                            the previous height. How high does it rise after the 5th bounce?
        heights : 80, 40, 20, ...   -> a GP with first term 80 (after bounce 1) and r = 1/2
        after the 5th bounce = T(5) = 80 * (1/2)^4 = 80/16 = 5 m
        (or directly: 160 * (1/2)^5 = 160/32 = 5 m, same)

    Example 7 (real-life) : a town has 2000 people and the population grows by 10% every year.
                            Population after 3 years?
        "grows by 10%" means multiply by 1.1 each year -> GP with r = 1.1
        year 0 : 2000 (this is a = T(1)),  year 3 is the 4th term
        T(4) = 2000 * 1.1^3 = 2000 * 1.331 = 2662 people
```

---

## CHAPTER 3 : "Which term is 768?" (running the formula backwards)

### PROBLEM A

```
    The sequence 3, 6, 12, 24, ... continues up to 768.
    Q. How many terms does it have?
```

### TRY IT THE SLOW WAY

```
    Keep doubling and count: 3, 6, 12, 24, 48, 96, 192, 384, 768  -> 9 terms.
    Fine here, but painful if the last term was 3 * 2^200.
```

### SPOT THE PATTERN (use the formula; the unknown is the POWER)

```
    The last term is the n_th term :   a * r^(n-1) = l
    Divide by a                    :   r^(n-1) = l / a

    Now it becomes a question of  "r raised to WHAT power gives l/a ?"
    The trick: write l/a as a power of r.
```

    Problem A : a = 3, r = 2, l = 768, find number of terms
$$3 * 2^{(n-1)} = 768$$
$$2^{(n-1)} = 768/3 = 256$$
$$now\ take\ (log_2)\ both \ sides$$

$$n-1 = log_2(256)$$
$$256 = 2^8$$
$${\implies} n - 1 = log_2(2^8)$$
$${\implies} n - 1 = 8*log_2(2)$$
$${\implies} n - 1 = 8$$
$${\implies} n = 8 + 1$$
$${\implies} n = 9$$

### FORMULA IS BORN

```
    There is NO new formula here. The method is :
        1) put T(n) = the given number
        2) divide both sides by a
        3) take log with base 'r'
        4) find n
```

### CHECK + USE
Try it yourself
```
    Example 1 : how many terms are in  1, 3, 9, ..., 729 ?


    Example 2 : how many terms are in  5, 10, 20, ..., 640 ?
  

    Example 3 : how many terms are in  256, 128, 64, ..., 1/4 ?
```


### PROBLEM B : "Two clues about an unknown GP"

```
    Q. The 3rd term of a GP is 12 and the 6th term is 96. Find the GP.

    IDEA : each clue is an equation in a and r.  In AP we SUBTRACTED to kill 'a'.
           In GP the terms are multiplied, so we DIVIDE to kill 'a'.

        T(3) = a*r^2 = 12     ...(i)
        T(6) = a*r^5 = 96     ...(ii)

        (ii) / (i) :  r^3 = 96/12 = 8   ->  r = 2
        put r = 2 in (i) :  a*4 = 12    ->  a = 3

    The GP is  3, 6, 12, 24, 48, 96, ...      CHECK : T(6) = 3 * 2^5 = 96   correct

    Example : the 4th term is 54 and the 7th term is 1458. Find the GP.
        a*r^3 = 54 ...(i),  a*r^6 = 1458 ...(ii)
        (ii)/(i) : r^3 = 1458/54 = 27  ->  r = 3
        a * 27 = 54  ->  a = 2           GP : 2, 6, 18, 54, 162, ...
        CHECK : T(7) = 2 * 3^6 = 1458   correct

    Example : the 2nd term is 6 and the 4th term is 24.  (Careful : two answers!)
        a*r = 6 ...(i),  a*r^3 = 24 ...(ii)
        (ii)/(i) : r^2 = 4  ->  r = 2 or r = -2
        r = 2  :  a = 3   ->  GP  3, 6, 12, 24, ...
        r = -2 :  a = -3  ->  GP  -3, 6, -12, 24, ...
        both are valid GPs (check the 2nd and 4th terms: 6 and 24 in both)
```

---

## CHAPTER 4 : "Total of a doubling habit" (the sum formula)

### PROBLEM

```
    Ramesh puts Rs 1 on day 1, Rs 2 on day 2, Rs 4 on day 3 ... doubling every day.
    Q. How much has he put in total after 10 days?
       1 + 2 + 4 + 8 + ... (10 terms)
```

### TRY IT THE SLOW WAY

```
    1 + 2 = 3,  3 + 4 = 7,  7 + 8 = 15,  15 + 16 = 31, 31 + 32 = 63,
    63 + 64 = 127, 127 + 128 = 255, 255 + 256 = 511, 511 + 512 = 1023.

    Notice : 1, 3, 7, 15, 31, 63, ... each total is ONE LESS than a power of 2 (2, 4, 8, 16, 32, 64...).
    Is it a coincidence?  Let us find out why.
    (The AP trick of reversing and adding will NOT work here, the columns do not give equal sums.)
```

### SPOT THE PATTERN (the shift-and-subtract trick)

```
    Write the sum S, then write r*S right below it, shifted one place to the right :

        S    = a + ar + ar^2 + ar^3 + ...... + ar^(n-1)
        r*S  =     ar + ar^2 + ar^3 + ...... + ar^(n-1) + ar^n

    Almost everything is common! Subtract the second line from the first:

        S - r*S = a - ar^n

    All the middle terms cancel, only the first and the last survive.
```

### FORMULA IS BORN

```
        S(1 - r) = a(1 - r^n)

        S(n) = a(1 - r^n)/(1 - r)         when r < 1   (keeps numbers positive)
        S(n) = a(r^n - 1)/(r - 1)         when r > 1   (same thing, both top and bottom multiplied by -1)

        special case r = 1 : every term is a, so S(n) = n*a      (formula would give 0/0, so treat it separately)
```
Remember this: $$S(n) = {\frac{a*(r^{n}-1)}{r-1}}$$
### CHECK + USE

```
    CHECK by hand : 1, 2, 4, 8  ->  1 + 2 + 4 + 8 = 15
        a = 1, r = 2, n = 4 :  S(4) = 1*(2^4 - 1)/(2 - 1) = 15   correct

    Back to the problem : a = 1, r = 2, n = 10
        S(10) = 1*(2^10 - 1)/(2 - 1) = 1024 - 1 = 1023      (matches the slow total!)
        This also explains the "one less than a power of 2" pattern.

    Example 1 : sum of the first 8 terms of  3, 6, 12, 24, ...
        a = 3, r = 2, n = 8
        S(8) = 3*(2^8 - 1)/(2 - 1) = 3*255 = 765

    Example 2 : sum of the first 6 terms of  2, 6, 18, 54, ...
        a = 2, r = 3, n = 6
        S(6) = 2*(3^6 - 1)/(3 - 1) = 2*728/2 = 728
        (by hand : 2 + 6 + 18 + 54 + 162 + 486 = 728, correct)

    Example 3 : sum of the first 5 terms of  81, 27, 9, 3, ...   (r < 1, so use the 1 - r^n form)
        a = 81, r = 1/3, n = 5
        S(5) = 81*(1 - (1/3)^5)/(1 - 1/3) = 81*(1 - 1/243)/(2/3)
             = 81*(242/243)*(3/2) = (242/3)*(3/2) = 121
        (by hand : 81 + 27 + 9 + 3 + 1 = 121, correct)

    Example 4 : sum of the first 5 terms of  5, -10, 20, -40, ...  (negative r)
        a = 5, r = -2, n = 5
        S(5) = 5*(1 - (-2)^5)/(1 - (-2)) = 5*(1 + 32)/3 = 5*33/3 = 55
        (by hand : 5 - 10 + 20 - 40 + 80 = 55, correct)

    Example 5 : find  1 + 3 + 9 + ... + 729   (last term given, first find n - Chapter 3)
        a = 1, r = 3, 3^(n-1) = 729 = 3^6  ->  n = 7
        S(7) = 1*(3^7 - 1)/(3 - 1) = 2186/2 = 1093

    Example 6 : a constant GP  7, 7, 7, ... (10 terms)   r = 1
        S(10) = 10 * 7 = 70        (do NOT use the formula when r = 1)

    Example 7 (real-life) : you save Re 1 on day 1 and double it every day. Total after 20 days?
        a = 1, r = 2, n = 20
        S(20) = 2^20 - 1 = 1048576 - 1 = 1048575      (over ten lakh rupees from a rupee!)

    WHICH FORM SHOULD I PICK?
        r > 1  ->  a(r^n - 1)/(r - 1)
        r < 1  ->  a(1 - r^n)/(1 - r)
        r = 1  ->  n*a
```

---

## CHAPTER 5 : "Add forever?" (sum to infinity)

### PROBLEM

```
    You have a 1-metre rope. Cut away half of it, then half of what is left, then half again ...

        piece lengths : 1/2, 1/4, 1/8, 1/16, ...      (a GP with a = 1/2, r = 1/2)

    Q. If you could keep going forever, what would the total length of all the pieces be?
```

### TRY IT THE SLOW WAY

```
    1/2                          = 0.5
    1/2 + 1/4                    = 0.75
    1/2 + 1/4 + 1/8              = 0.875
    1/2 + 1/4 + 1/8 + 1/16       = 0.9375
    ... the total keeps creeping towards 1 but never crosses it (you can't cut more than the whole rope).

    Let us see WHY from the formula.
```

### SPOT THE PATTERN

```
    Use S(n) = a(1 - r^n)/(1 - r) with a = 1/2, r = 1/2 :

        S(n) = (1/2)*(1 - (1/2)^n)/(1/2) = 1 - (1/2)^n

        n = 1  : 1 - 1/2   = 0.5
        n = 4  : 1 - 1/16  = 0.9375
        n = 10 : 1 - 1/1024 = 0.99902...
        n = 20 : 1 - 1/1048576 = 0.99999905...

    As n becomes huge, (1/2)^n becomes almost 0, so S(n) gets as close to 1 as we like.
    KEY POINT : r^n vanishes ONLY when r is a proper fraction (between -1 and 1).
                If |r| >= 1, r^n does not vanish (2^n just keeps growing) and the sum never settles.
```

### FORMULA IS BORN

```
    If -1 < r < 1 :  r^n -> 0, so  S(n) = a(1 - r^n)/(1 - r)  ->  a/(1 - r)

        S(infinity) = a/(1 - r)         valid ONLY when |r| < 1
```
if $|r| < 1$ then ${\infin}$ terms could be summed and the value is given by
$$S({\infin}) = {\frac{a}{1-r}}$$
### CHECK + USE

```
    CHECK : rope problem : a = 1/2, r = 1/2  ->  S = (1/2)/(1 - 1/2) = 1     matches

    Example 1 : 81 + 27 + 9 + 3 + ...  (to infinity)
        a = 81, r = 1/3
        S = 81/(1 - 1/3) = 81/(2/3) = 121.5
        (the first 5 terms already gave 121 in Chapter 4, so 121.5 is believable)

    Example 2 : turning a recurring decimal into a fraction.   0.333... = ?
        0.333... = 0.3 + 0.03 + 0.003 + ...    a = 0.3, r = 0.1
        S = 0.3/(1 - 0.1) = 0.3/0.9 = 1/3       (we all knew it, now we know WHY)

    Example 3 : 0.777... = ?
        a = 0.7, r = 0.1  ->  S = 0.7/0.9 = 7/9

    Example 4 : 0.454545... = ?
        0.45 + 0.0045 + 0.000045 + ...   a = 0.45, r = 0.01
        S = 0.45/0.99 = 45/99 = 5/11

    Example 5 (real-life) : a ball is dropped from 10 m and rebounds to 3/5 of its previous height
                            every time. Total distance travelled before it stops?
        down first : 10 m
        then up and down each time :  rise 6, then down 6 ; rise 3.6, then down 3.6 ; ...
        rise heights : 6, 3.6, 2.16, ...  GP with a = 6, r = 0.6
        sum of rises = 6/(1 - 0.6) = 6/0.4 = 15 m
        each rise is followed by an equal fall, so up + down = 2*15 = 30 m
        total distance = 10 + 30 = 40 m

    Example 6 : does 1 + 2 + 4 + 8 + ... (to infinity) have a sum?
        r = 2, |r| > 1 -> NO, the sum just keeps growing. The formula a/(1-r) must not be used.
```

---



## CHAPTER 6 : "Sum and product are given, find the numbers" (smart assumption)

### PROBLEM

```
    Three numbers are in GP. Their sum is 14 and their product is 64. Find them.
```

### TRY IT THE SLOW WAY

```
    Call them a, ar, ar^2.
        product : a * ar * ar^2 = a^3 * r^3 = 64      -> (a*r)^3 = 64 -> a*r = 4
        sum     : a + ar + ar^2 = 14
    It works, but we needed a little trick (cube root of a*r) to get going.
    Can we choose the numbers so that the product is trivial from the very start?
```

### SPOT THE PATTERN

```
    Choose the numbers SYMMETRICALLY around the middle one :

         a/r ,  a ,  a*r

    When we MULTIPLY them, the r and 1/r CANCEL :   (a/r) * a * (a*r) = a^3
    (In AP we used a - d, a, a + d so that d cancelled in the SUM; here r cancels in the PRODUCT.)
```

### FORMULA IS BORN (a trick, not a formula)

```
    3 terms in GP :  a/r,  a,  a*r                     product = a^3
    5 terms in GP :  a/r^2, a/r, a, a*r, a*r^2         product = a^5
    4 terms in GP :  a/r^3, a/r, a*r, a*r^3            (real ratio is r^2)
```

### CHECK + USE

```
    Solve the problem :
        numbers : a/r, a, ar
        product : a^3 = 64  ->  a = 4
        sum     : 4/r + 4 + 4r = 14   ->   4/r + 4r = 10
                  multiply by r :  4 + 4r^2 = 10r
                  4r^2 - 10r + 4 = 0  ->  2r^2 - 5r + 2 = 0  ->  (2r - 1)(r - 2) = 0
                  r = 2  or  r = 1/2
        r = 2   : 2, 4, 8
        r = 1/2 : 8, 4, 2     (same numbers, reverse order)
        CHECK : 2 + 4 + 8 = 14 and 2*4*8 = 64   correct

    Example 2 : three numbers in GP, sum 13, product 27.
        a^3 = 27 -> a = 3
        3/r + 3 + 3r = 13  ->  3 + 3r^2 = 10r  ->  3r^2 - 10r + 3 = 0  ->  (3r - 1)(r - 3) = 0
        r = 3  ->  1, 3, 9      (r = 1/3 gives 9, 3, 1)
        CHECK : 1 + 3 + 9 = 13, 1*3*9 = 27

    Example 3 : three numbers in GP, sum 21, product 216.
        a^3 = 216 -> a = 6
        6/r + 6 + 6r = 21  ->  6 + 6r^2 = 15r  ->  2r^2 - 5r + 2 = 0  ->  r = 2 or 1/2
        numbers : 3, 6, 12
        CHECK : 3 + 6 + 12 = 21, 3*6*12 = 216

    Example 4 : three numbers in GP, product 1000 and sum of the numbers is 35. Find them.
        a^3 = 1000 -> a = 10
        10/r + 10 + 10r = 35  ->  10 + 10r^2 = 25r  ->  2r^2 - 5r + 2 = 0 -> r = 2 or 1/2
        numbers : 5, 10, 20
        CHECK : 5 + 10 + 20 = 35, 5*10*20 = 1000
```

---


## CHAPTER 7 : PRACTICE QUESTIONS

> **DISCLAIMER:** Solve every question first on your own, on paper. Only after you have
> made a real attempt, give the question to any LLM to know the answer and compare
> your working with it. Do not skip the struggle, that is where the learning happens.
>
> TIP : whenever you get stuck, ask yourself "which chapter's PROBLEM does this look like?"

```
LEVEL 1 : Warm-up (Chapters 1 and 2)

    Q1.  Find the 9th term of the GP  2, 4, 8, 16, ...
    Q2.  Find the 8th term of the GP  729, 243, 81, 27, ...
    Q3.  Check whether  5, 15, 45, 135, ...  is a GP. If yes, write a and r.
    Q4.  Find the 6th term of the GP  2, -6, 18, -54, ...
    Q5.  The population of a village is 5000 and it grows by 20% every year.
         What will it be after 2 years?

LEVEL 2 : Run it backwards (Chapters 3 and 4)

    Q6.  Which term of the GP  3, 6, 12, 24, ...  is 384 ?
    Q7.  How many terms are there in the GP  1, 3, 9, ..., 6561 ?
    Q8.  Is 500 a term of the GP  2, 10, 50, 250, ... ?  Justify.  What about 1250 ?
    Q9.  The 2nd term of a GP is 6 and the 5th term is 162. Find the GP.
    Q10. Find the sum of the first 7 terms of  5, 15, 45, 135, ...
    Q11. Find the sum  1 + 2 + 4 + ... + 512  (last term given).
    Q12. Find the sum of the first 6 terms of  64, 32, 16, 8, ...



---

*Remember the story : a GP is built by multiplying by the same r again and again.
Every formula in this material is just that one idea, viewed from a different side.*