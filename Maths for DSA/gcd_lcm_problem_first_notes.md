# GCD & LCM

## 1. Basics

- **Divisor of n:** a number d with `n % d == 0`. Divisors of 12: 1, 2, 3, 4, 6, 12.
- **Multiple of n:** n, 2n, 3n, ...
- **GCD(a, b):** the largest number that divides both a and b.
- **LCM(a, b):** the smallest positive number that both a and b divide.

Example, a = 12, b = 18:

```
divisors of 12 : 1 2 3 4 6 12
divisors of 18 : 1 2 3 6 9 18
common         : 1 2 3 6      -> GCD = 6

multiples of 12 : 12 24 36 48 ...
multiples of 18 : 18 36 54 ...
common          : 36 72 ...   -> LCM = 36
```

If gcd(a, b) = 1, the numbers are **coprime** (e.g. 8 and 9).

---

## 2. Computing the GCD

**Brute force:** try every d from min(a, b) down to 1. This takes up to min(a, b) steps, which is far too slow for 10^9.

**Key observation:** `gcd(a, b) = gcd(a - b, b)`

Proof: any d that divides a and b also divides a - b. Conversely, any d that divides a - b and b also divides (a - b) + b = a. Both pairs have the same common divisors, so they have the same greatest one.  
If this proof doesn't make sense to you, ask any LLM for further simple explaination and ask you doubts

Repeating the subtraction works, but it is slow when the numbers are far apart:

```
gcd(1000000, 1): (1000000,1) -> (999999,1) -> ... -> (1,1)    999999 steps
```

Subtracting b from a as many times as possible leaves exactly `a % b` (why? search about it!!). So do it all at once:

**Euclid's algorithm:** `gcd(a, b) = gcd(b, a % b)`, and stop when b == 0. The answer is a.

```cpp
// recursive code:

int gcd(int a,int b){
    if(b==0) return a;
    return gcd(b,a%b);
}

// iterative code: 
int gcd(int a, int b) {
    while (b != 0) {
        int r = a % b;
        a = b;
        b = r;
    }
    return a;
}
```

If a < b, they will be swaped after the first operation: (18, 48) -> (48, 18).  
(18 % 48  = 18) You never need to check which is larger.

C++17 has `std::gcd` and `std::lcm` in `<numeric>`, and GCC has `__gcd`.

### Dry runs

Each step is (a, b) -> (b, a % b).

```
gcd(48, 18):    (48,18) -> (18,12) -> (12,6) -> (6,0)                 = 6
gcd(252, 105):  (252,105) -> (105,42) -> (42,21) -> (21,0)            = 21
gcd(17, 5):     (17,5) -> (5,2) -> (2,1) -> (1,0)                     = 1
gcd(18, 48):    (18,48) -> (48,18) -> (18,12) -> (12,6) -> (6,0)      = 6
gcd(1000, 7):   (1000,7) -> (7,6) -> (6,1) -> (1,0)                   = 1
```

---

## 3. Time complexity: O(log(min(a, b)))

**Claim:** for a >= b > 0, `a % b < a/2`.  
Proof:

- If b <= a/2: the remainder is smaller than b, so `a % b < b <= a/2`.
- If b > a/2: b fits into a only once, so `a % b = a - b < a - a/2 = a/2`.

Examples: 100 % 40 = 20 < 50, 100 % 51 = 49 < 50, 100 % 99 = 1 < 50.

**One step** turns (a, b) into (b, r1), where r1 = a % b < a/2. Only the old a is guaranteed to have shrunk. The number b has just moved to the first slot.

**Two steps** turn (a, b) into (b, r1) and then into (r1, r2), where r2 = b % r1 < b/2. So after two steps **both** numbers are less than half of what they were.

```
(1071, 462) -> (462, 147) -> (147, 21)
  147 < 1071/2 = 535.5,   21 < 462/2 = 231
```

**Counting:** the smaller number m = min(a, b) at least halves every 2 steps, so after 2k steps it is below m / 2^k. The loop ends when it reaches 0, which needs 2^k > m, i.e. k > log2(m). Total steps are at most about 2·log2(m) (plus one if the first step is a swap).

- **Why min:** if a is huge and b is small, the first step brings everything down to size b. For example, gcd(10^18, 7) needs only a handful of steps.
- **Scale:** for min(a, b) around 10^9 the bound is about 60 steps, and the true worst case is about 43.
- **Worst case:** consecutive Fibonacci numbers, where every quotient is 1. (89, 55) takes 9 steps: (89,55) -> (55,34) -> (34,21) -> (21,13) -> (13,8) -> (8,5) -> (5,3) -> (3,2) -> (2,1) -> (1,0).

---

## 4. gcd(0, x) = x

d divides n means `n = d·k` for some integer k. For n = 0 this holds with k = 0 for every d, so **every number divides 0**.

The common divisors of 0 and x are therefore just the divisors of x, and the greatest is x. So `gcd(0, x) = gcd(x, 0) = x`.

- gcd(0, 9) = 9, and the loop handles it with one swap: (0, 9) -> (9, 0).
- gcd(0, 0): every number divides both, so there is no greatest one. By convention it is 0, and the code returns 0.
- This is why the loop can stop at (a, 0), and why 0 is the neutral starting value for the gcd of an array.

---

## 5. LCM

For any two positive integers:

```
gcd(a, b) * lcm(a, b) = a * b
```

Checks: (12, 18): 6·36 = 216 = 12·18. (4, 6): 2·12 = 24. (8, 9): 1·72 = 72.

**Why (splitting out the gcd):** let g = gcd(a, b), so a = g·x and b = g·y with gcd(x, y) = 1. Then lcm = g·x·y, and a·b = g·(g·x·y) = g·lcm.

**Why (prime factors):** 12 = 2²·3 and 18 = 2·3². The gcd takes the smaller exponent of each prime (2·3 = 6) and the lcm takes the larger (2²·3² = 36). Smaller + larger = the sum of the two exponents.

**Code:** divide first, then multiply, so that a·b doesn't overflow.

```cpp
long long lcm(long long a, long long b) {
    if (a == 0 || b == 0) return 0;
    return a / gcd(a, b) * b;
}
```

Examples: lcm(12, 18) = 12/6·18 = 36. lcm(21, 6) = 21/3·6 = 42.

### When the formula cannot be used directly

1. **More than two numbers.** `a·b·c / gcd(a,b,c)` is wrong.
   - For 2, 3, 4 it gives 24, but the real lcm is 12.
   - For 6, 10, 15 it gives 900, but the real lcm is 30.
   - Fold two at a time instead: `lcm(a, b, c) = lcm(lcm(a, b), c)`.
2. **Overflow.**
   - `a·b` can overflow even if the answer fits, so write `a / gcd * b`.
   - The lcm itself can exceed `long long`. lcm(1..42) = 219060189739591200 fits, but lcm(1..43) = 9419588158802421600 is above 9.22·10^18.
   - Use `__int128`, a cap, or modular arithmetic.
3. **Zero.** gcd(0, 0) = 0 would divide by zero. By definition lcm(a, 0) = 0, so check for zero first.
4. **LCM modulo M.** You cannot do `l = lcm(l, a) % M` in a loop, because after the `%` the real value is lost and gcd is computed on the wrong number. Instead, factorise each element (SPF sieve), keep the maximum exponent of each prime in a vector, and multiply `p^maxExp` mod M at the end.
5. **Negative numbers.** Take `abs()` first.

---

## 6. GCD and LCM of an array

Common divisors of {a, b, c} are the same as those of {gcd(a, b), c}, so `gcd(a, b, c) = gcd(gcd(a, b), c)`. The same holds for lcm. Keep one running value and combine it with each element.

The start value must satisfy f(start, x) = x:

- **gcd:** start = **0**, since gcd(0, x) = x.
- **lcm:** start = **1**, since lcm(1, x) = x.

```cpp
long long gcd_arr(const vector<long long>& v) {
    long long g = 0;
    for (long long x : v) g = gcd(g, x);
    return g;
}

long long lcm_arr(const vector<long long>& v) {
    long long l = 1;
    for (long long x : v) l = lcm(l, x);
    return l;
}
```

Dry run, A = {12, 18, 24, 30}:

```
read    g = gcd(g, x)     l = lcm(l, x)
12      gcd(0,12)  = 12   lcm(1,12)  = 12
18      gcd(12,18) = 6    lcm(12,18) = 36
24      gcd(6,24)  = 6    lcm(36,24) = 72
30      gcd(6,30)  = 6    lcm(72,30) = 360
```

GCD = 6, LCM = 360.

More examples:

```
{24, 36, 60, 10}: GCD = 2,  LCM = 360
{6, 10, 15}:      GCD = 1,  LCM = 30
{7}:              GCD = 7,  LCM = 7
{0, 8, 12}:       GCD = 4   (zeros do not hurt gcd), LCM = 0
{} (empty):       GCD = 0,  LCM = 1
```

**Cost:** the running gcd only shrinks, so the total work is about O(n + log(max)), not O(n·log(max)).

**GCD of the array without element i** (prefix and suffix vectors):

```cpp
vector<long long> gcd_without_each(const vector<long long>& A) {
    int n = A.size();
    vector<long long> pre(n + 1, 0), suf(n + 2, 0), ans(n);
    for (int i = 0; i < n; i++)      pre[i + 1] = gcd(pre[i], A[i]);
    for (int i = n - 1; i >= 0; i--) suf[i]     = gcd(suf[i + 1], A[i]);
    for (int i = 0; i < n; i++)      ans[i]     = gcd(pre[i], suf[i + 1]);
    return ans;
}
```

For {24, 36, 60, 10} the answers are 2, 2, 2, 12. Removing 10 raises the gcd from 2 to 12.

---

## 7. Practice

> **DISCLAIMER:** Solve every question first on your own, on paper. Only after you have made a real attempt, give the question to any LLM to know the answer and compare your working with it.

1. Run Euclid by hand on gcd(84, 36), gcd(35, 64) and gcd(36, 84). Compare the step counts of the first and third.
2. A hall is 156 m by 117 m. What is the largest square tile that covers it exactly, and how many tiles are needed?
3. Prove that gcd(a, b) = gcd(a − b, b).
4. How many steps do subtraction-only and modulo Euclid take for gcd(10^6, 3)?
5. Prove that a % b < a/2 for a ≥ b > 0, then fill in the (a, b) table for (987, 610) and show both numbers halve every two steps.
6. In four sentences, explain why Euclid runs in O(log(min(a, b))).
7. Why is gcd(0, x) = x? What goes wrong if you define gcd(x, 0) = 1?
8. Find lcm(36, 48) and verify gcd·lcm = a·b.
9. Give your own example (not 2,3,4 or 6,10,15) showing that a·b·c / gcd(a, b, c) is not the lcm.
10. Find the gcd and lcm of {18, 27, 45, 9} with folds, and show the running values.
11. Three lights blink every 4, 6 and 14 seconds. When do they blink together again, and how many times in the first 10 minutes (counting time 0)?
12. Find the smallest positive number that leaves remainder 3 when divided by each of 4, 6 and 10.
13. Why must the gcd fold start at 0 and the lcm fold at 1?
14. Describe how to compute lcm(a1..an) mod 1e9+7 with a_i ≤ 10^6, using only vectors and an SPF sieve.
15. Find the longest subarray of A with gcd > 1. (Hint: the running gcd only shrinks as the right end moves.)
16. Write gcd without the `%` operator, using only subtraction and shifts (binary GCD).