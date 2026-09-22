# SECTION 7 — PROGRAMMING & PSEUDOCODE (25 Questions)

### Q1. What is printed by the following code?

```
int x = 7;
x += 3;
print x
```

A. 73

B. 10

C. 7

D. 4

**Correct Answer:** B

**Difficulty:** Easy

**Topic:** Operators — Compound Assignment

**Explanation:**
`x += 3` means `x = x + 3`, so x becomes 10. Note that in string contexts `+` may concatenate, but here x is an int, so arithmetic applies.

**Why the other options are wrong:**
- A: '73' would imply string concatenation.
- C: Ignores the update.
- D: Subtra-acre instead of adding.

**Key Concept:** `+=` is compound addition in place.

---

### Q2. With integer variables, what is the value of `7 / 2` in most statically-typed languages (e.g., C, Java with ints)?

A. 3.5

B. 4

C. 2

D. 3

**Correct Answer:** D

**Difficulty:** Easy

**Topic:** Integer Division

**Explanation:**
When both operands are integers, division truncates the fractional part, so 7/2 = 3. 3.5 requires at least one operand to be a float/double.

**Why the other options are wrong:**
- A: Result of floating division.
- B: Not a rounding-up ('ceiling') rule.
- C: Arithmetic error.

**Key Concept:** `int / int` truncates toward zero.

---

### Q3. What is the result of `10 % 3`?

A. 1

B. 3

C. 0

D. 10

**Correct Answer:** A

**Difficulty:** Easy

**Topic:** Modulus Operator

**Explanation:**
The modulo operator returns the remainder of division: 10 = 3×3 + 1, so remainder is 1.

**Why the other options are wrong:**
- B: The quotient.
- C: Remainder would be 0 only if evenly divisible.
- D: That's the dividend itself.

**Key Concept:** `%` gives the remainder of integer division.

---

### Q4. What is the output of this loop?

```
for (int i = 0; i < 3; i++)
    print i
```

A. 0 1 2 3

B. 1 2 3

C. 0 1 2

D. 1 2

**Correct Answer:** C

**Difficulty:** Easy

**Topic:** For-Loop Boundaries

**Explanation:**
i starts at 0 and the loop runs while i < 3, printing 0, 1, 2. When i reaches 3 the condition fails, so 3 is never printed.

**Why the other options are wrong:**
- A: Includes 3, which fails the condition.
- B: Misses the initial 0.
- D: Misses both endpoints.

**Key Concept:** `< n` prints exactly 0..n-1.

---

### Q5. What is the value of `2 + 3 * 4` in most languages?

A. 20

B. 24

C. 11

D. 14

**Correct Answer:** D

**Difficulty:** Easy

**Topic:** Operator Precedence

**Explanation:**
Multiplication binds tighter than addition: 3*4 = 12, then 2 + 12 = 14. "Left to right naively" would give an incorrect 20.

**Why the other options are wrong:**
- A: 20 comes from evaluating left-to-right ((2+3)*4).
- B/C: Other miscounts.

**Key Concept:** `*` and `/` bind before `+` and `-`.

---

### Q6. What is printed?

```
int a = 5, b = 3;
if (a < b)
    print "x"
else
    print "y"
```

A. y

B. x

C. nothing

D. error

**Correct Answer:** A

**Difficulty:** Easy

**Topic:** Conditional Logic

**Explanation:**
The condition 5 < 3 is false, so the else branch runs and y is printed. x would print only if the condition were true.

**Why the other options are wrong:**
- B: Condition is false.
- C/D: One branch always executes.

**Key Concept:** False condition takes the else path.

---

### Q7. What is the final value of i?

```
int i = 0;
while (i < 5)
    i++;
```

A. 4

B. 0

C. 5

D. 6

**Correct Answer:** C

**Difficulty:** Moderate

**Topic:** While-Loop Tracing

**Explanation:**
The loop increments while i < 5: i becomes 1,2,3,4,5. At i=5 the condition fails and the loop exits — final value is 5.

**Why the other options are wrong:**
- A: Loop body runs for 0..4, ending with 5.
- B: Would mean the body never ran.
- D: Would require an extra pass after 5.

**Key Concept:** A `while (i < n) i++` ends with i == n.

---

### Q8. Given `arr = [10, 20, 30]`, what is the value of `arr[1]`?

A. 10

B. 20

C. 30

D. undefined

**Correct Answer:** B

**Difficulty:** Easy

**Topic:** Array Indexing

**Explanation:**
Indices start at 0: arr[0]=10, arr[1]=20, arr[2]=30. So arr[1] is the second element.

**Why the other options are wrong:**
- A: That is arr[0].
- C: That is arr[2].
- D: The index is within bounds.

**Key Concept:** Arrays are zero-indexed.

---

### Q9. How many times does the inner statement execute?

```
for (int i = 0; i < 3; i++)
    for (int j = 0; j < 2; j++)
        print i, j
```

A. 5

B. 3

C. 2

D. 6

**Correct Answer:** D

**Difficulty:** Moderate

**Topic:** Nested Loops

**Explanation:**
For each of the 3 outer iterations, the inner loop runs 2 times: 3 × 2 = 6 total prints.

**Why the other options are wrong:**
- A/B/C: Incorrect products of iteration counts.

**Key Concept:** Total inner executions = product of loop counts.

---

### Q10. What is `fact(4)` given `fact(n) = n <= 1 ? 1 : n * fact(n - 1)`?

A. 24

B. 12

C. 16

D. 4

**Correct Answer:** A

**Difficulty:** Moderate

**Topic:** Recursion Tracing

**Explanation:**
fact(4)=4×fact(3)=4×3×fact(2)=4×3×2×fact(1)=4×3×2×1=24.

**Why the other options are wrong:**
- B: 12 = 4×3 only (missing further factors).
- C: Would come from 4².
- D: Ignores recursive expansion.

**Key Concept:** Recursion unwinds into a product chain.

---

### Q11. What is `f(5)` given `f(n) = n + f(n-1)` and `f(1) = 1`?

A. 16

B. 15

C. 10

D. 5

**Correct Answer:** B

**Difficulty:** Moderate

**Topic:** Recursion — Sum Tracing

**Explanation:**
f(5)=5+f(4)=5+4+f(3)=...=5+4+3+2+1=15.

**Why the other options are wrong:**
- A: 16 includes an extra step.
- C: 10 = first four numbers only.
- D: Ignores the recursion.

**Key Concept:** This recursion computes the sum of 1..n.

---

### Q12. In Java, what does `"CAPGEMINI".length()` return?

A. 10

B. 11

C. 9

D. 8

**Correct Answer:** C

**Difficulty:** Easy

**Topic:** String Operations

**Explanation:**
C·A·P·G·E·M·I·N·I = 9 characters. length() counts characters, not words.

**Why the other options are wrong:**
- A/B: Overcounts the letters.
- D: Undercounts (8 = a common typo missing one I).

**Key Concept:** length() returns the character count.

---

### Q13. What is wrong with this code that is intended to sum an array's elements?

```
int[] arr = {1, 2, 3};
int sum = 0;
for (int i = 1; i <= arr.length; i++)
    sum += arr[i];
```

A. The condition is correct; nothing is wrong

B. It sums correctly, just slowly

C. It never adds the first element and reads one element past the end (index arr.length is out of bounds)

D. sum is declared too late

**Correct Answer:** C

**Difficulty:** Moderate

**Topic:** Debugging — Array Boundaries

**Explanation:**
Valid indices are 0..2. Starting at i=1 skips arr[0], and `i <= 3` accesses arr[3] which is out of bounds. It should be `i = 0; i < arr.length`.

**Why the other options are wrong:**
- A: The boundary logic is flawed.
- B: It is not merely slow.
- D: Declaration position is irrelevant.

**Key Concept:** Off-by-one on both ends = skipped first + overflow at last.

---

### Q14. A function reverses the string "abc" character-by-character. What is the result?

A. cba

B. abc

C. bac

D. cab

**Correct Answer:** A

**Difficulty:** Moderate

**Topic:** String Manipulation

**Explanation:**
Reversing 'a','b','c' yields 'c','b','a' — the last character moves first.

**Why the other options are wrong:**
- B: Unchanged input.
- C/D: Wrong permutations.

**Key Concept:** Reverse swaps first↔last.

---

### Q15. What is printed?

```
int i = 3;
print i++;     // prints first, then increments
print ++i;     // increments first, then prints
```

A. 3 4

B. 4 4

C. 3 5

D. 4 5

**Correct Answer:** C

**Difficulty:** Hard

**Topic:** i++ vs ++i

**Explanation:**
`i++` returns the old value (3) then sets i=4. `++i` first increments i to 5, then returns 5. So output is "3 5".

**Why the other options are wrong:**
- A: Second value would be 4 only if no second increment applied.
- B: Both printed values ignore the sequencing.
- D: Misses that the first prints before incrementing.

**Key Concept:** `i++` = post-increment; `++i` = pre-increment.

---

### Q16. A nested loop prints a right-angled triangle of stars with n=4 rows:

```
for (i = 1; i <= 4; i++)
    for (j = 1; j <= i; j++)
        print "*"
```

How many stars total?

A. 8

B. 10

C. 16

D. 12

**Correct Answer:** B

**Difficulty:** Hard

**Topic:** Nested Loops — Pattern Counting

**Explanation:**
Row i prints i stars: 1+2+3+4 = 10 = n(n+1)/2.

**Why the other options are wrong:**
- A: 8 = 2×(rows count).
- C: 16 = 4² (square).
- D: Overly close but wrong sum.

**Key Concept:** Triangle patterns print n(n+1)/2 items.

---

### Q17. What does `f(4)` return?

```
int f(int n) {
    if (n < 2) return n;
    return f(n - 1) + f(n - 2);
}
```

A. 5

B. 4

C. 2

D. 3

**Correct Answer:** D

**Difficulty:** Hard

**Topic:** Recursion — Fibonacci Trace

**Explanation:**
This is Fibonacci shifted: f(0)=0, f(1)=1, so f(2)=1, f(3)=2, f(4)=1+2=3.

**Why the other options are wrong:**
- A: 5 is f(5).
- B: 4 is the input, not the value.
- C: 2 is f(3).

**Key Concept:** Trace to base cases; f(4)=f(3)+f(2)=2+1=3.

---

### Q18. What is the result of `6 & 4` (bitwise AND)?

A. 4

B. 6

C. 2

D. 0

**Correct Answer:** A

**Difficulty:** Hard

**Topic:** Bitwise Operators

**Explanation:**
6 = 110₂, 4 = 100₂. AND yields 100₂ = 4.

**Why the other options are wrong:**
- B: 110 would be OR.
- C: 010 would come from 6 & 2.
- D: Only if no common bit.

**Key Concept:** Bitwise AND keeps only bits set in both.

---

### Q19. What is printed?

```
int x = 0;
boolean b = (x > 0) && (x = 5) == 5;
print x
```

A. 5

B. true

C. 0

D. error

**Correct Answer:** C

**Difficulty:** Hard

**Topic:** Short-Circuit Evaluation

**Explanation:**
`x > 0` is false, so `&&` short-circuits and the right side `(x = 5)` never runs. x stays 0.

**Why the other options are wrong:**
- A: Would need the right operand to evaluate.
- B: The boolean result is false, and anyway you are printing x.
- D: The code is legal.

**Key Concept:** `&&`/`||` skip evaluation once the outcome is decided.

---

### Q20. A function is declared to return `int`, but one branch has no return statement. What is the issue?

A. Nothing — it is mandatory to omit returns

B. The function can reach the end without returning a value — a compile error/undefined behaviour depending on the language

C. An extra return is needed inside the loop

D. Only void functions must return values

**Correct Answer:** B

**Difficulty:** Moderate

**Topic:** Debugging — Missing Return

**Explanation:**
Paths that end without returning produce a compile error (Java/C#) or undefined value (C/C++). Every non-void function must return on all reachable paths.

**Why the other options are wrong:**
- A: Returns are required on all paths.
- C: The problem is the missing return, not an extra one.
- D: void functions may omit returning a value, not the reverse.

**Key Concept:** Non-void functions need a return on every path.

---

### Q21. An array has size n. What is wrong with:

```
for (int i = n; i >= 0; i--)
    arr[i] = 0;
```

A. Nothing, the whole array is cleared

B. It clears only the first half

C. It clears elements twice

D. It accesses arr[n], which is one position past the end — out of bounds

**Correct Answer:** D

**Difficulty:** Hard

**Topic:** Debugging — Boundary Condition

**Explanation:**
Valid indices are 0..n-1. Starting at index n reads/writes out of bounds. It should start at n-1.

**Why the other options are wrong:**
- A/B/C: All misdiagnose the boundary error.

**Key Concept:** Rewrites in decreasing order must start at length-1.

---

### Q22. What is printed?

```
int x = 10;
x %= 4;
x += 2;
print x
```

A. 4

B. 12

C. 6

D. 2

**Correct Answer:** A

**Difficulty:** Moderate

**Topic:** Compound Operators Sequence

**Explanation:**
x = 10 % 4 = 2, then x = 2 + 2 = 4.

**Why the other options are wrong:**
- B: 12 = 10+2 ignoring the modulo.
- C: 6 would be 10%4=2 plus 4.
- D: Only the modulo step.

**Key Concept:** Apply operators in program order.

---

### Q23. In Java/C, `int max = 2147483647;` then `print max + 1`. What happens?

A. 2147483648 is printed

B. A long is created automatically

C. The value wraps around to a large negative number (integer overflow)

D. The program stops permanently

**Correct Answer:** C

**Difficulty:** Advanced

**Topic:** Integer Overflow

**Explanation:**
Signed 32-bit ints go to 2^31−1; adding 1 overflows to −2^31. Modern languages don't auto-promote `max+1` to long here.

**Why the other options are wrong:**
- A: Int can't hold 2,147,483,648.
- B: No automatic widening in these languages.
- D: It continues with the wrapped value.

**Key Concept:** Adding past the max wraps to negative.

---

### Q24. In Python, why does `0.1 + 0.2 == 0.3` evaluate to False?

A. Because 0.3 is not a number

B. Because floating-point binary representation is approximate; the addition yields 0.30000000000000004

C. Because + in Python concatenates floats

D. Because Python rounds to the nearest integer

**Correct Answer:** B

**Difficulty:** Advanced

**Topic:** Floating-Point Precision

**Explanation:**
Decimal fractions like 0.1 are not exactly representable in binary, and arithmetic compounds the tiny error. Comparisons should use tolerance (abs(diff) < eps).

**Why the other options are wrong:**
- A: 0.3 exists as a float.
- C: + on floats is addition.
- D: No integer rounding.

**Key Concept:** Never exact-compare floats; use an epsilon.

---

### Q25. What is printed?

```
int a = 2;
a = a * a + a;
print a
```

A. 8

B. 4

C. 10

D. 6

**Correct Answer:** D

**Difficulty:** Moderate

**Topic:** Expression Evaluation

**Explanation:**
The right-hand side is evaluated with the current a=2: 2×2 + 2 = 6. Then the result is assigned to a.

**Why the other options are wrong:**
- A: 8 = 2^3 (cube assumption).
- B: 4 = only a×a.
- C: 10 = product plus original plus extra.

**Key Concept:** Evaluate RHS with old value, then assign.

---

# SECTION 8 — DSA (30 Questions)

### Q1. What is the time complexity of binary search on a sorted array of n elements?

A. O(1)

B. O(log n)

C. O(n)

D. O(n log n)

**Correct Answer:** B

**Difficulty:** Easy

**Topic:** Searching Complexity

**Explanation:**
Each comparison halves the search space, so the number of steps is log₂n. Linear scan would be O(n).

**Why the other options are wrong:**
- A: O(1) is direct index access.
- C: That's linear search.
- D: That's the cost of n searches or typical sort.

**Key Concept:** Halving → logarithmic.

---

### Q2. Which data structure follows FIFO (First-In-First-Out) order?

A. Queue

B. Stack

C. Tree

D. Graph

**Correct Answer:** A

**Difficulty:** Easy

**Topic:** Queue

**Explanation:**
Queues serve the oldest element first (like a line). Stacks are LIFO.

**Why the other options are wrong:**
- B: LIFO, the opposite.
- C/D: Not ordered access structures by insertion time.

**Key Concept:** Queue = FIFO.

---

### Q3. What is the time complexity of accessing an array element by its index?

A. O(log n)

B. O(n)

C. O(n log n)

D. O(1)

**Correct Answer:** D

**Difficulty:** Easy

**Topic:** Array Access

**Explanation:**
Arrays store elements contiguously; index access is base + index×size — constant time regardless of n.

**Why the other options are wrong:**
- A/B/C: All depend on the array size in some way.

**Key Concept:** Direct index access is O(1).

---

### Q4. Which searching algorithm requires the input to be SORTED?

A. Linear search

B. Jump search on unordered data

C. Binary search

D. Hashing lookups

**Correct Answer:** C

**Difficulty:** Easy

**Topic:** Binary Search Precondition

**Explanation:**
Binary search relies on the midpoint comparison to discard halves — that logic only holds if the data is sorted. Linear search and hash lookups work without any sorting.

**Why the other options are wrong:**
- A: Works on unordered data.
- B: Jump search itself also needs sorted data; the option describes it on unordered data, which is invalid.
- D: Hashing works without sorting.

**Key Concept:** Binary search demands sorted data.

---

### Q5. A stack removes elements in which order?

A. LIFO — the most recently added element is removed first

B. FIFO — the oldest element is removed first

C. In random order

D. LRU — least recently used first

**Correct Answer:** A

**Difficulty:** Easy

**Topic:** Stack

**Explanation:**
Stacks mirror a physical stack of plates: last pushed, first popped. FIFO describes queues; LRU describes certain caches.

**Why the other options are wrong:**
- B: That is queue order.
- C: Order is strictly defined.
- D: Cache eviction policy, not a stack.

**Key Concept:** Stack = LIFO.

---

### Q6. What is the time complexity of inserting a node at the head of a singly linked list?

A. O(n)

B. O(log n)

C. O(1)

D. O(n log n)

**Correct Answer:** C

**Difficulty:** Easy

**Topic:** Linked List Operations

**Explanation:**
Insertion at head only requires adjusting the new node's pointer and the head reference — no traversal needed, so O(1).

**Why the other options are wrong:**
- A: Traversal is only needed for tail insertion without a tail pointer.
- B/D: Not applicable to head insertion.

**Key Concept:** Head insertion in a linked list is O(1).

---

### Q7. A program does one O(1) operation n times, and inside each iteration a nested loop also runs n times. What is the overall time complexity?

A. O(n)

B. O(n²)

C. O(2n)

D. O(log n)

**Correct Answer:** B

**Difficulty:** Moderate

**Topic:** Complexity Composition

**Explanation:**
Outer n iterations each trigger an inner loop of n steps: n×n = n² dominated term. O(2n) collapses to O(n), but the nested product remains quadratic.

**Why the other options are wrong:**
- A: Only counts the outer loop.
- C: Linear term plus one, not nested.
- D: Logarithmic is unrelated to this nesting.

**Key Concept:** Nested loops multiply their iteration counts.

---

### Q8. What is the WORST-CASE time complexity of bubble sort on n elements?

A. O(n)

B. O(n log n)

C. O(log n)

D. O(n²)

**Correct Answer:** D

**Difficulty:** Moderate

**Topic:** Sorting Complexity

**Explanation:**
Bubble sort compares and swaps in nested loops over n, so worst (and average) case is O(n²). Best case (already sorted + swap flag) is O(n).

**Why the other options are wrong:**
- A: That's optimistic best-case-with-flag.
- B: That's merge/quick/heap territory.
- C: Unrelated.

**Key Concept:** Bubble sort is O(n²) in the worst case.

---

### Q9. A compiler parses an expression with nested parentheses/brackets. Which data structure is the natural choice to check balanced parentheses?

A. Stack

B. Queue

C. Binary tree

D. Hash map

**Correct Answer:** A

**Difficulty:** Moderate

**Topic:** Stack Application

**Explanation:**
Each '(' is pushed; each matching ')' pops. Correct matching is exactly LIFO — the innermost open bracket closes first. That's a stack.

**Why the other options are wrong:**
- B: Queue can’t give last-open-first-close.
- C/D: Not designed for this matched-order logic.

**Key Concept:** Balance checking = stack.

---

### Q10. An editor needs an "Undo" feature. Which structure best implements it?

A. Queue

B. Hash map

C. Stack

D. Array sorted

**Correct Answer:** C

**Difficulty:** Moderate

**Topic:** Stack Application

**Explanation:**
Undo reverts the most recent action first — LIFO. Push each action; pop on undo.

**Why the other options are wrong:**
- A: FIFO would undo the oldest action.
- B/D: Lacking natural 'most recent' ordering.

**Key Concept:** Undo = stack (most recent first).

---

### Q11. A print server processes print jobs in the order they arrive. Which structure is most appropriate?

A. Stack

B. Queue

C. Heap

D. Hash table

**Correct Answer:** B

**Difficulty:** Moderate

**Topic:** Queue Application

**Explanation:**
Jobs must print in arrival order — first-in first-out — which is exactly a queue.

**Why the other options are wrong:**
- A: LIFO would print newest first.
- C: Priority would reorder.
- D: No ordering semantics.

**Key Concept:** Fairness by arrival = queue.

---

### Q12. What is the AVERAGE-case time complexity of a lookup in a hash table with n items and good hashing?

A. O(log n)

B. O(n)

C. O(n log n)

D. O(1)

**Correct Answer:** D

**Difficulty:** Moderate

**Topic:** Hashing

**Explanation:**
Hash function maps each key to a bucket in constant time, so a successful lookup averages O(1). O(n) is only the worst case when all keys collide.

**Why the other options are wrong:**
- A/B/C: Growth functions for structures without hashing.

**Key Concept:** Average hash lookup = O(1).

---

### Q13. What is the time complexity of merge sort in ALL cases (best, average, worst)?

A. O(n log n)

B. O(n²)

C. O(log n)

D. O(n)

**Correct Answer:** A

**Difficulty:** Moderate

**Topic:** Sorting Complexity

**Explanation:**
Merge sort always halves and merges n elements at each of log n levels, giving Θ(n log n) regardless of input order.

**Why the other options are wrong:**
- B: That's bubble/insertion worst cases (or quick sort worst).
- C/D: Too small for comparison sorts.

**Key Concept:** Merge sort is stable O(n log n) always.

---

### Q14. A full binary tree has height h (root at height 0). What is the MAXIMUM total number of nodes?

A. 2^h

B. 2h

C. 2^(h+1) − 1

D. h²

**Correct Answer:** C

**Difficulty:** Moderate

**Topic:** Binary Tree Properties

**Explanation:**
A perfect tree of height h has 1+2+4+...+2^h = 2^(h+1)−1 nodes. 2^h alone counts only the last level.

**Why the other options are wrong:**
- A: Only the bottom level.
- B/D: Not the geometric series sum.

**Key Concept:** Max nodes = 2^(h+1) − 1.

---

### Q15. You must INSERT a new element into a SORTED array of n elements while keeping it sorted. What is the worst-case time?

A. O(1)

B. O(n)

C. O(log n)

D. O(n log n)

**Correct Answer:** B

**Difficulty:** Moderate

**Topic:** Array Insertion

**Explanation:**
Finding the spot may be O(log n) via binary search, but shifting the following elements to make room is O(n) in the worst case.

**Why the other options are wrong:**
- A: Contiguous storage forbids constant insertion.
- C: That's search only, ignoring the shift.
- D: Overestimate for a single insert.

**Key Concept:** Sorted-array insertion is dominated by shifting → O(n).

---

### Q16. Which of these sorting algorithms is STABLE (preserves relative order of equal keys) ?

A. Selection sort

B. Heap sort

C. Quick sort (typical Lomuto partition)

D. Merge sort

**Correct Answer:** D

**Difficulty:** Moderate

**Topic:** Sorting Stability

**Explanation:**
Merge sort's merge keeps left-half ties before right-half ties, preserving order. Selection, heap, and ordinary quick sort reorder equal elements.

**Why the other options are wrong:**
- A: Selection swaps can break tie order.
- B: Heap extraction scrambles ties.
- C: Standard quicksort is not stable.

**Key Concept:** Stability matters when keys tie (e.g., sorting by two columns).

---

### Q17. What is the worst-case time to search in a BALANCED vs severely UNBALANCED BST?

A. Balanced O(log n); unbalanced (degenerate) O(n)

B. Both O(log n)

C. Both O(n)

D. Unbalanced is faster

**Correct Answer:** A

**Difficulty:** Moderate

**Topic:** BST Search Complexity

**Explanation:**
A balanced BST keeps height log n. If insertions create a linear chain (like a linked list), height becomes n and searches degrade to O(n).

**Why the other options are wrong:**
- B: Assumes everyone is balanced.
- C: Ignores balance benefits.
- D: Opposite of reality.

**Key Concept:** BST performance depends on height.

---

### Q18. What is the total EXTRA SPACE (space complexity) of iterative-free recursive merge sort on n elements?

A. O(1)

B. O(log n)

C. O(n)

D. O(n log n)

**Correct Answer:** C

**Difficulty:** Moderate

**Topic:** Space Complexity

**Explanation:**
Merge sort allocates an auxiliary array of size n (plus O(log n) recursion depth). The dominant extra space is O(n).

**Why the other options are wrong:**
- A: In-place sorts like heap reach O(1).
- B: Only the recursion stack alone.
- D: Counts the recursion depth multiplied wrongly.

**Key Concept:** Merge sort trades O(n) space for stable sort.

---

### Q19. A divide-and-conquer algorithm satisfies T(n) = 2T(n/2) + n. What is its complexity?

A. O(log n)

B. O(n log n)

C. O(n)

D. O(n²)

**Correct Answer:** B

**Difficulty:** Hard

**Topic:** Recurrence Analysis

**Explanation:**
Two equal halves each with linear combine work — this is the merge-sort recurrence. Master theorem case 2 gives Θ(n log n).

**Why the other options are wrong:**
- A: No super-constant combine.
- C: That's T(n) = T(n/2) + O(1).
- D: That's T(n) = 2T(n/2) + n².

**Key Concept:** T(n)=2T(n/2)+n → O(n log n).

---

### Q20. A "queue with delete-middle" implementation must delete one element from the middle of a normal array-backed queue of n elements. What is the cost?

A. O(1)

B. O(log n)

C. O(1) amortized

D. O(n)

**Correct Answer:** D

**Difficulty:** Hard

**Topic:** Operation Cost Reasoning

**Explanation:**
Deleting from the middle of a contiguous array requires shifting all following elements, so O(n) — queue's usual O(1) front/back operation argument doesn't apply mid-array.

**Why the other options are wrong:**
- A: Only front deletion is O(1).
- B/C: No amortization magic for middle deletes.

**Key Concept:** Middle operations on arrays are O(n).

---

### Q21. You append n elements to an array-backed list that doubles its capacity when full. What is the total AMORTIZED cost of all n appends?

A. O(n)

B. O(n²)

C. O(n log n)

D. O(log n)

**Correct Answer:** A

**Difficulty:** Hard

**Topic:** Amortized Analysis

**Explanation:**
Most appends are O(1); the occasional resize copies the current array. Charge a fixed token per append to cover future copies → geometric doubling totals O(n) for n appends.

**Why the other options are wrong:**
- B: Would happen with +1-slot growth.
- C/D: Not the doubling pattern.

**Key Concept:** Doubling growth amortizes to O(1) per append.

---

### Q22. To find the MIDDLE node of a singly linked list in one pass, the two-pointer approach runs in:

A. O(n) time, O(n) space

B. O(n²) time

C. O(n) time, O(1) space

D. O(log n) time

**Correct Answer:** C

**Difficulty:** Hard

**Topic:** Two Pointer Technique

**Explanation:**
The slow pointer advances once, fast pointer twice. When fast reaches the end, slow is at the middle — a single O(n) pass with only two pointers (O(1) space).

**Why the other options are wrong:**
- A: No extra array is needed.
- B: A naive count-then-walk is 2 passes (still O(n)) but not quadratic.
- D: No halving of data.

**Key Concept:** Tortoise-and-hare finds the middle in one pass.

---

### Q23. Which data-structure combo is typical for implementing an LRU cache with O(1) get and put?

A. A single sorted array

B. Hash map + doubly linked list

C. Two stacks

D. A binary tree only

**Correct Answer:** B

**Difficulty:** Hard

**Topic:** LRU Cache Design

**Explanation:**
The hash map gives O(1) lookup of the node; the doubly linked list maintains recency order and allows O(1) removal/re-insertion on access. That pair is the standard LRU recipe.

**Why the other options are wrong:**
- A: Array shifts cost O(n).
- C: Stacks can't reorder on access.
- D: A tree alone adds ordering overhead for LRU.

**Key Concept:** Hash for lookup + DLL for recency = O(1) LRU.

---

### Q24. A recursive function runs T(n) = T(n−1) + n (linear work at each level, one fewer input each time). What is the complexity?

A. O(n)

B. O(n log n)

C. O(log n)

D. O(n²)

**Correct Answer:** D

**Difficulty:** Hard

**Topic:** Recurrence Analysis

**Explanation:**
Sum over n levels: n + (n−1) + ... + 1 = n(n+1)/2 → O(n²).

**Why the other options are wrong:**
- A: Would be constant work each level.
- B/C: Not the arithmetic series.

**Key Concept:** T(n) = T(n−1) + n is the classic O(n²) recurrence.

---

### Q25. What is the most efficient cycle-detection approach for a LARGE singly linked list?

A. Floyd's tortoise-and-hare: O(n) time, O(1) space

B. A visited hash set: O(n) time, O(n) space

C. Sorting the list first, then checking

D. Counting nodes twice

**Correct Answer:** A

**Difficulty:** Hard

**Topic:** Cycle Detection

**Explanation:**
Floyd's algorithm moves fast 2× slow; if they meet, a cycle exists — O(n) time with constant space, beating the hash-set's O(n) space.

**Why the other options are wrong:**
- B: Correct but uses O(n) space.
- C: Sorting a linked list is convoluted and doesn't detect cycles.
- D: Counting doesn't detect cycles.

**Key Concept:** Cycle detection = Floyd's, constant extra space.

---

### Q26. The Towers of Hanoi with n disks requires how many moves in the optimal solution?

A. n²

B. n!

C. 2^n − 1

D. n log n

**Correct Answer:** C

**Difficulty:** Hard

**Topic:** Exponential Algorithm

**Explanation:**
Move n−1, move the bottom, move n−1 again: M(n) = 2M(n−1)+1 → 2^n − 1. That exponential growth justifies why n=64 is infeasible.

**Why the other options are wrong:**
- A/B/D: Not the doubling recurrence.

**Key Concept:** Hanoi = 2^n − 1 moves.

---

### Q27. The naive (unmemoised) recursive Fibonacci computation for f(n) has what time complexity?

A. O(n)

B. O(2^n)

C. O(n²)

D. O(n log n)

**Correct Answer:** B

**Difficulty:** Advanced

**Topic:** Naive Recursion / Exponentiality

**Explanation:**
Each call spawns two calls until base cases: a branching tree of ~2^n node (f(4)=3 requires 9 calls). Dynamic programming reduces it to O(n).

**Why the other options are wrong:**
- A: That's the DP/memoised version.
- C/D: Other growth rates.

**Key Concept:** Unmemoised Fibonacci ≈ O(2^n).

---

### Q28. In hashing with separate chaining, all n keys hash to the same bucket. What is the complexity of a search?

A. O(1)

B. O(log n)

C. O(n) — hashing collapses to a linear scan of that bucket

D. O(n log n)

**Correct Answer:** C

**Difficulty:** Advanced

**Topic:** Hash Collision Degradation

**Explanation:**
Good hashing spreads keys evenly, keeping buckets short. A pathological collision storm puts everything in one chain, making search O(n) — a reminder that hash quality matters.

**Why the other options are wrong:**
- A: Only true under good spread.
- B/D: Not the pathological bound.

**Key Concept:** Worst-case hashing degenerates to O(n).

---

### Q29. Which sort is usually BEST for data that is already almost sorted?

A. Insertion sort

B. Merge sort

C. Heap sort

D. Quick sort (median-of-3 on random data)

**Correct Answer:** A

**Difficulty:** Advanced

**Topic:** Algorithm Selection

**Explanation:**
Insertion sort runs O(n) on nearly-sorted input because few elements move. Merge/heap stay O(n log n); quick sort is fine but not as adaptive.

**Why the other options are wrong:**
- B/C: Fixed O(n log n) regardless of order.
- D: Doesn't exploit near-sortedness.

**Key Concept:** Near-sorted data → insertion sort wins.

---

### Q30. With a binary heap implementing a priority queue of n items, what is the complexity of extract-min (removing the minimum)?

A. O(1)

B. O(n)

C. O(log n)

D. O(n log n)

**Correct Answer:** C

**Difficulty:** Advanced

**Topic:** Heaps / Priority Queues

**Explanation:**
extract-min removes the root and sifts the last element down the heap — the sift-down walks at most the tree height, O(log n). Only reading the min is O(1).

**Why the other options are wrong:**
- A: Reading the min is O(1); removing/heapifying is not.
- B: That's array-based extract with shifting.
- D: That's n extractions.

**Key Concept:** Heap extract-min = O(log n).