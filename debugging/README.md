# C++ Debugging Practice Repository — Capgemini Exceller Debugging Assessment

## Purpose

This repository is a complete, self-contained practice bank for the **Capgemini Exceller Debugging Assessment**. It contains **250 pre-written C++ debugging programs**, each with one or more hidden bugs that you must find and fix.

Every question simulates the real assessment flow:

```
Read the code  →  Trace the logic  →  Identify the bug  →  Fix it  →  Think about hidden test cases
```

None of these are "write a program from scratch" tasks. The code is already written, it *looks* functional, and in most cases it passes obvious test inputs — the bug is only exposed by careful tracing or by an edge-case hidden test.

## Language

**C++ only.** All 250 questions use modern but assessment-friendly C++:

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <algorithm>
#include <unordered_map>
#include <stack>
#include <queue>
using namespace std;
```

## Question Distribution (250 total)

| Folder | Topic | Questions |
|---|---|---:|
| `01_Control_Flow` | Control Flow & Logic | 40 |
| `02_Arrays` | Arrays | 50 |
| `03_Strings` | Strings | 40 |
| `04_Searching_Sorting` | Searching & Sorting | 35 |
| `05_Functions_Pointers_References` | Functions, Pointers & References | 30 |
| `06_Data_Structures_Algorithms` | Data Structures & Algorithms | 30 |
| `07_Mixed_Debugging` | Mixed Debugging (assessment-style) | 25 |
| **Total** | | **250** |

## Folder Structure

```
debugging/
│
├── README.md
│
├── 01_Control_Flow/
│   └── control_flow.md          # 40 questions + 40 solutions
│
├── 02_Arrays/
│   └── arrays.md                # 50 questions + 50 solutions
│
├── 03_Strings/
│   └── strings.md               # 40 questions + 40 solutions
│
├── 04_Searching_Sorting/
│   └── searching_sorting.md     # 35 questions + 35 solutions
│
├── 05_Functions_Pointers_References/
│   └── functions_pointers_references.md   # 30 questions + 30 solutions
│
├── 06_Data_Structures_Algorithms/
│   └── data_structures_algorithms.md      # 30 questions + 30 solutions
│
└── 07_Mixed_Debugging/
    └── mixed_debugging.md       # 25 questions + 25 solutions
```

Each topic is a single Markdown file. Inside every file:

1. **All questions first** (`## Question N`) — problem, bug type, buggy code, your task, and expected behavior for hidden-style inputs.
2. **Then all solutions** (`# Solutions` → `## Solution N`) — the bug, why it is wrong, and the complete corrected code.

There are no answers next to the questions, so you can genuinely practice before checking.

## Difficulty Progression

Every topic file progresses **Easy → Medium → Hard**:

| Level | Where | What it trains |
|---|---|---|
| Easy | First questions in each file | Obvious boundaries, wrong operators, wrong initialization, simple indexing |
| Medium | Middle questions | Nested conditions/loops, array/string edge cases, search & sort bugs, function/pointer interactions |
| Hard | Final questions | Two interacting bugs, hidden edge cases, subtle logic, recursion, pointer issues, data structures |
| Mixed Debugging file | Q6–Q25 mostly Hard | Assessment-closest questions combining arrays, strings, search, sort, pointers, recursion, hashing, linked lists, matrices |

## Bug Categories Covered

Across the 250 questions you will repeatedly encounter:

- **Logic & condition errors** — `<` vs `<=`, `>` vs `>=`, `==` vs `!=`, `&&` vs `||`, wrong branch, wrong variable
- **Off-by-one errors** — `i <= n` vs `i < n`, `i = 1` vs `i = 0`, `i < n-1` vs `i < n`, `n - i` vs `n - 1 - i`, `i > 0` vs `i >= 0`
- **Initialization errors** — `sum = 1` vs `sum = 0`, `product = 0` vs `product = 1`, wrong max/min defaults
- **Assignment errors** — `x =+ y` vs `x += y`, assignment instead of comparison, updating the wrong variable
- **Runtime errors** — out-of-bounds reads, null pointer dereference, division by zero, infinite loops, invalid recursion
- **Data-structure bugs** — wrong head/top/front updates, missing null checks, incorrect recursive base cases, wrong frequency-map updates

## Hidden Test Cases

Every question includes an **Expected Behavior** section with 2–3 input/output pairs. One of them (usually the last) is the *hidden test* that exposes the bug — the buggy code fails it even though it passes the obvious baseline input. Common traps used across the bank:

- Empty input (`n = 0`) · single element (`n = 1`)
- Duplicate values · all-equal values
- Negative numbers · zero · very large values
- Already-sorted / reverse-sorted arrays
- Empty strings · single-character strings · strings with spaces
- Boundary values (`10` vs `9`, `n - 1`, the last index, etc.)

## How to Practice

1. **Pick a topic** and read the questions in order (Easy → Medium → Hard).
2. For each question:
   - Read the Problem and understand the *intended* output.
   - Run the Buggy Code mentally (or actually compile/run it).
   - Test the Expected Behavior inputs yourself.
   - Find and fix the bug **before** scrolling down.
3. **Ask yourself these questions every time:**
   - What is the intended output?
   - What happens on the first iteration? On the last iteration?
   - What happens when `n = 0` or `n = 1`?
   - Can an index go out of range?
   - Is the variable/accumulator initialized correctly?
   - Is the loop guaranteed to terminate?
   - Is the condition checking the correct variable?
   - Does the function return the correct value?
   - Is the pointer/reference valid?
   - What happens with duplicate / negative / empty input?

## How to Use the Solutions

- Solutions are **at the end of each topic file** under the `# Solutions` heading.
- `## Solution N` always corresponds to `## Question N`.
- Use them in two ways:
  - **After** you attempt a question, to verify your fix.
  - **Repeatedly**, to memorize the debugging insight — each solution ends with a short, memorable rule.

## Recommended Practice Order

1. `01_Control_Flow/control_flow.md` — warm-up with conditions, loops, off-by-one, init errors.
2. `02_Arrays/arrays.md` — the largest set; core indexing and boundary skills.
3. `03_Strings/strings.md` — string manipulation and edge cases.
4. `04_Searching_Sorting/searching_sorting.md` — algorithm logic and search boundaries.
5. `05_Functions_Pointers_References/functions_pointers_references.md` — pass-by-value vs reference, pointers.
6. `06_Data_Structures_Algorithms/data_structures_algorithms.md` — stacks, queues, linked lists, trees, recursion.
7. `07_Mixed_Debugging/mixed_debugging.md` — full assessment-style practice combining everything.

## Golden Debugging Rules (remember these)

1. A loop that "looks right" still needs a boundary check — always test the **first and last iterations**.
2. Accumulators and max/min defaults are wrong more often than you think.
3. The comparator direction decides the whole algorithm — check `>`, `<`, `>=`, `<=` carefully.
4. When a search "misses" a value you know exists, check the loop bound and the index variable.
5. In C++, compare string content with `==`/`.compare()` at the `std::string` level and never read past `n-1` in raw arrays.
6. For recursion, always validate the base case with the smallest possible input first.

Good luck with the Capgemini Exceller Debugging Assessment.