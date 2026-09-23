# C++ Debugging — Control Flow & Logic

## Question 1

### Difficulty
Easy

### Bug Type
Off-by-One

### Problem
The program reads a non-negative integer `n` and counts how many even numbers exist in the range from `1` to `n` inclusive. For example, with `n = 6` the evens are 2, 4 and 6, so the output should be 3.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, count = 0;
    cout << "Enter n: ";
    cin >> n;
    for (int i = 1; i < n; i++) {
        if (i % 2 == 0)
            count++;
    }
    cout << "Evens from 1 to " << n << ": " << count << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
5
```
the expected output is:
```text
Evens from 1 to 5: 2
```

---

For:
```text
6
```
the expected output is:
```text
Evens from 1 to 6: 3
```

---

For:
```text
0
```
the expected output is:
```text
Evens from 1 to 0: 0
```

## Question 2

### Difficulty
Easy

### Bug Type
Wrong Accumulator Initialization (sum = 1)

### Problem
The program reads a non-negative integer `n` and prints the sum of all integers from 1 to `n` inclusive. For example, with `n = 5` the sum is 1 + 2 + 3 + 4 + 5 = 15. With `n = 0` the loop never runs and the sum must be 0.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int sum = 1;
    for (int i = 1; i <= n; i++)
        sum += i;
    cout << "Sum: " << sum << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
5
```
the expected output is:
```text
Sum: 15
```

---

For:
```text
3
```
the expected output is:
```text
Sum: 6
```

---

For:
```text
0
```
the expected output is:
```text
Sum: 0
```

---

For:
```text
7
```
the expected output is:
```text
Sum: 28
```

## Question 3

### Difficulty
Easy

### Bug Type
Incorrect Relational Operator (`>` vs `>=`)

### Problem
The program reads an exam score and prints `PASS` when the score is at least 50, otherwise `FAIL`. A score of exactly 50 must be treated as a pass.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int score;
    cout << "Enter score: ";
    cin >> score;
    if (score > 50)
        cout << "PASS";
    else
        cout << "FAIL";
    cout << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
70
```
the expected output is:
```text
PASS
```

---

For:
```text
50
```
the expected output is:
```text
PASS
```

---

For:
```text
49
```
the expected output is:
```text
FAIL
```

---

For:
```text
0
```
the expected output is:
```text
FAIL
```

## Question 4

### Difficulty
Easy

### Bug Type
Wrong Product Initialization (product = 0)

### Problem
The program reads an integer `n` and prints the product of all integers from `1` to `n` inclusive (the factorial). For example, with `n = 4` the product is 1 × 2 × 3 × 4 = 24.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int product = 0;
    for (int i = 1; i <= n; i++)
        product *= i;
    cout << "Product: " << product << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
```
the expected output is:
```text
Product: 24
```

---

For:
```text
1
```
the expected output is:
```text
Product: 1
```

---

For:
```text
6
```
the expected output is:
```text
Product: 720
```

## Question 5

### Difficulty
Easy

### Bug Type
Switch-Case Fall-Through (missing break)

### Problem
The program reads a month number (1 to 12) and prints the number of days in that month. February is 28 days (ignore leap years), months 4, 6, 9 and 11 have 30 days, and all the rest have 31 days.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int month;
    cout << "Enter month (1-12): ";
    cin >> month;
    int days = 31;
    switch (month) {
        case 2:
            days = 28;
        case 4:
        case 6:
        case 9:
        case 11:
            days = 30;
    }
    cout << "Days: " << days << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
2
```
the expected output is:
```text
Days: 28
```

---

For:
```text
11
```
the expected output is:
```text
Days: 30
```

---

For:
```text
7
```
the expected output is:
```text
Days: 31
```

---

For:
```text
4
```
the expected output is:
```text
Days: 30
```

## Question 6

### Difficulty
Easy

### Bug Type
Descending Loop Off-by-One (`i > 0` vs `i >= 0`)

### Problem
The program reads a non-negative integer `n` and prints every integer from `n` down to `0` inclusive, each followed by a space. For example, with `n = 3` the output is `3 2 1 0`.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    for (int i = n; i > 0; i--)
        cout << i << " ";
    cout << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3
```
the expected output is:
```text
3 2 1 0
```

---

For:
```text
0
```
the expected output is:
```text
0
```

---

For:
```text
1
```
the expected output is:
```text
1 0
```

## Question 7

### Difficulty
Easy

### Bug Type
Loop Stops Too Early (sum of digits)

### Problem
The program reads a non-negative integer `n` and prints the sum of its decimal digits. For example, the digits of 123 are 1, 2 and 3, so the printed sum must be 6.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int sum = 0;
    while (n > 10) {
        sum += n % 10;
        n /= 10;
    }
    cout << "Sum of digits: " << sum << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
123
```
the expected output is:
```text
Sum of digits: 6
```

---

For:
```text
5
```
the expected output is:
```text
Sum of digits: 5
```

---

For:
```text
2020
```
the expected output is:
```text
Sum of digits: 4
```

---

For:
```text
0
```
the expected output is:
```text
Sum of digits: 0
```

## Question 8

### Difficulty
Easy

### Bug Type
Wrong Starting Index (loop starts at i = 1)

### Problem
The program reads a non-negative integer `n` and prints the sum `0 + 1 + 2 + ... + (n - 1)` (that is, the sum of the first `n` whole numbers starting at zero). For example, with `n = 4` the sum is 0 + 1 + 2 + 3 = 6.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int sum = 0;
    for (int i = 1; i <= n; i++)
        sum += i;
    cout << "Sum: " << sum << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
```
the expected output is:
```text
Sum: 6
```

---

For:
```text
1
```
the expected output is:
```text
Sum: 0
```

---

For:
```text
0
```
the expected output is:
```text
Sum: 0
```

---

For:
```text
10
```
the expected output is:
```text
Sum: 45
```

## Question 9

### Difficulty
Easy

### Bug Type
Table Loop Boundary (`i <= 10` vs `i < 10`)

### Problem
The program reads a number `n` and prints the multiples `n x 1`, `n x 2`, ..., `n x 10`, each followed by a space. For example, with `n = 5`, the output is `5 10 15 20 25 30 35 40 45 50`.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    for (int i = 1; i < 10; i++)
        cout << n * i << " ";
    cout << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
5
```
the expected output is:
```text
5 10 15 20 25 30 35 40 45 50
```

---

For:
```text
3
```
the expected output is:
```text
3 6 9 12 15 18 21 24 27 30
```

---

For:
```text
10
```
the expected output is:
```text
10 20 30 40 50 60 70 80 90 100
```

## Question 10

### Difficulty
Easy

### Bug Type
Incomplete Condition (leap year, no century rule)

### Problem
The program reads a year and prints whether it is a leap year. A year is a leap year if it is divisible by 4, except that years divisible by 100 are not leap years unless they are also divisible by 400.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int year;
    cout << "Enter year: ";
    cin >> year;
    if (year % 4 == 0)
        cout << year << " is a leap year" << endl;
    else
        cout << year << " is not a leap year" << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
2024
```
the expected output is:
```text
2024 is a leap year
```

---

For:
```text
2021
```
the expected output is:
```text
2021 is not a leap year
```

---

For:
```text
1900
```
the expected output is:
```text
1900 is not a leap year
```

---

For:
```text
2000
```
the expected output is:
```text
2000 is a leap year
```

## Question 11

### Difficulty
Easy

### Bug Type
Loop Bound `i < n-1` Skips Last Element

### Problem
The program reads a count `n` followed by `n` integers and prints their total sum. For example, for the numbers 4, 9, 2, 7 and 5 the total is 27.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter count: ";
    cin >> n;
    int a[100];
    for (int i = 0; i < n; i++)
        cin >> a[i];
    int sum = 0;
    for (int i = 0; i < n - 1; i++)
        sum += a[i];
    cout << "Sum: " << sum << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
5
4 9 2 7 5
```
the expected output is:
```text
Sum: 27
```

---

For:
```text
3
1 2 3
```
the expected output is:
```text
Sum: 6
```

---

For:
```text
1
8
```
the expected output is:
```text
Sum: 8
```

## Question 12

### Difficulty
Easy

### Bug Type
Wrong Comparison (`==` vs `!=`)

### Problem
The program reads a count `n` followed by `n` integers and prints how many of those integers are **not** equal to 7. For example, in `1 7 8 7` there are two values that are not 7.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, x;
    cout << "Enter count: ";
    cin >> n;
    int count = 0;
    for (int i = 0; i < n; i++) {
        cin >> x;
        if (x == 7)
            count++;
    }
    cout << "Count: " << count << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
1 7 8 7
```
the expected output is:
```text
Count: 2
```

---

For:
```text
3
7 7 7
```
the expected output is:
```text
Count: 0
```

---

For:
```text
2
5 5
```
the expected output is:
```text
Count: 2
```

## Question 13

### Difficulty
Medium

### Bug Type
Wrong Logical Operator (`&&` vs `||`)

### Problem
The program reads a bank balance and prints `Valid` when the balance is at least 0 and no more than 100000. A balance outside this range must be printed as `Invalid`.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int balance;
    cout << "Enter balance: ";
    cin >> balance;
    if (balance >= 0 || balance <= 100000)
        cout << "Valid" << endl;
    else
        cout << "Invalid" << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
50000
```
the expected output is:
```text
Valid
```

---

For:
```text
0
```
the expected output is:
```text
Valid
```

---

For:
```text
100000
```
the expected output is:
```text
Valid
```

---

For:
```text
250000
```
the expected output is:
```text
Invalid
```

For:
```text
-100
```
the expected output is:
```text
Invalid
```

## Question 14

### Difficulty
Medium

### Bug Type
Infinite Loop (increment misplaced inside if)

### Problem
The program reads a non-negative integer `n` and prints the count of even numbers in the range from `0` to `n` inclusive. For example, for `n = 6` the evens are 0, 2, 4 and 6, so the count is 4.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int i = 0, count = 0;
    while (i <= n) {
        if (i % 2 == 0)
            count++;
        else
            i++;
    }
    cout << "Evens: " << count << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
6
```
the expected output is:
```text
Evens: 4
```

---

For:
```text
1
```
the expected output is:
```text
Evens: 1
```

---

For:
```text
10
```
the expected output is:
```text
Evens: 6
```

---

For:
```text
0
```
the expected output is:
```text
Evens: 1
```

## Question 15

### Difficulty
Medium

### Bug Type
Break Executes Too Early

### Problem
The program reads a count `n` followed by `n` integers and prints the sum of the numbers until a multiple of 10 is encountered. The multiple of 10 itself is **not** included in the sum. For example, for `7 20 3 4`, the sum is just 7.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, x;
    cout << "Enter count: ";
    cin >> n;
    int sum = 0;
    for (int i = 0; i < n; i++) {
        cin >> x;
        sum += x;
        if (x % 10 == 0)
            break;
    }
    cout << "Sum: " << sum << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
7 20 3 4
```
the expected output is:
```text
Sum: 7
```

---

For:
```text
2
30 5
```
the expected output is:
```text
Sum: 0
```

---

For:
```text
5
1 2 3 4 5
```
the expected output is:
```text
Sum: 15
```

## Question 16

### Difficulty
Medium

### Bug Type
Misplaced Continue

### Problem
The program reads an integer `n` and prints every number from 1 to `n` that is **not** divisible by 3, followed by the count of numbers that were printed. For example, for `n = 8` the printed numbers are 1 2 4 5 7 8, and the count is 6.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int count = 0;
    for (int i = 1; i <= n; i++) {
        if (i % 3 != 0) {
            cout << i << " ";
            continue;
        }
        count++;
    }
    cout << "\nCount: " << count << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
8
```
the expected output is:
```text
1 2 4 5 7 8 
Count: 6
```

---

For:
```text
1
```
the expected output is:
```text
1 
Count: 1
```

---

For:
```text
3
```
the expected output is:
```text
1 2 
Count: 2
```

## Question 17

### Difficulty
Medium

### Bug Type
Nested Loop Inner Boundary Error

### Problem
The program reads an integer `n` and prints a triangle of numbers: row `i` must contain the numbers 1 through `i`, separated by spaces. For example, for `n = 3` the triangle is:

```text
1 
1 2 
1 2 3 
```

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= n; j++)
            cout << j << " ";
        cout << endl;
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3
```
the expected output is:
```text
1 
1 2 
1 2 3 
```

---

For:
```text
1
```
the expected output is:
```text
1 
```

---

For:
```text
2
```
the expected output is:
```text
1 
1 2 
```

## Question 18

### Difficulty
Medium

### Bug Type
Do-While Runs One Extra Iteration

### Problem
The program reads a non-negative integer `n` and prints its digits in reverse order, each digit followed by a space. If `n` is 0, nothing should be printed at all. For example, `n = 123` should print `3 2 1`.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    do {
        cout << n % 10 << " ";
        n /= 10;
    } while (n > 0);
    cout << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
123
```
the expected output is:
```text
3 2 1 
```

---

For:
```text
0
```
the expected output is:
```text

```

---

For:
```text
7
```
the expected output is:
```text
7 
```

## Question 19

### Difficulty
Medium

### Bug Type
Counter Reset Inside Loop

### Problem
The program reads a count `n` followed by `n` integers and prints how many of those integers are even. For example, in the numbers 2, 4 and 6 every value is even, so the count is 3.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, x;
    cout << "Enter count: ";
    cin >> n;
    int count = 0;
    for (int i = 0; i < n; i++) {
        cin >> x;
        count = 0;
        if (x % 2 == 0)
            count++;
    }
    cout << "Evens: " << count << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3
2 4 6
```
the expected output is:
```text
Evens: 3
```

---

For:
```text
4
1 3 5 7
```
the expected output is:
```text
Evens: 0
```

---

For:
```text
5
2 8 3 4 9
```
the expected output is:
```text
Evens: 3
```

## Question 20

### Difficulty
Medium

### Bug Type
Assignment Instead of Comparison (`=`)

### Problem
The program reads an integer and prints `LOCKED` when the value equals the secret code 1234, otherwise it prints `OPEN`. Any value other than 1234 must always be `OPEN`.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int code;
    cout << "Enter code: ";
    cin >> code;
    if (code = 1234)
        cout << "LOCKED" << endl;
    else
        cout << "OPEN" << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
1234
```
the expected output is:
```text
LOCKED
```

---

For:
```text
0000
```
the expected output is:
```text
OPEN
```

---

For:
```text
9999
```
the expected output is:
```text
OPEN
```

## Question 21

### Difficulty
Medium

### Bug Type
While Loop Never Enters

### Problem
The program reads a non-negative integer `n` and prints the integers from 1 to `n` (each followed by a space). For example, `n = 4` must produce `1 2 3 4`.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int i = 1;
    while (i > n) {
        cout << i << " ";
        i++;
    }
    cout << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
```
the expected output is:
```text
1 2 3 4
```

---

For:
```text
1
```
the expected output is:
```text
1
```

---

For:
```text
0
```
the expected output is:
```text

```

---

For:
```text
7
```
the expected output is:
```text
1 2 3 4 5 6 7
```

## Question 22

### Difficulty
Medium

### Bug Type
Wrong Increment Step (`i += 2`)

### Problem
The program reads an integer `n` and prints every multiple of 3 from 3 up to `n` (each followed by a space). For example, with `n = 15` the output is `3 6 9 12 15`.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    for (int i = 3; i <= n; i += 2)
        cout << i << " ";
    cout << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
15
```
the expected output is:
```text
3 6 9 12 15
```

---

For:
```text
6
```
the expected output is:
```text
3 6
```

---

For:
```text
2
```
the expected output is:
```text

```

---

For:
```text
21
```
the expected output is:
```text
3 6 9 12 15 18 21
```

## Question 23

### Difficulty
Medium

### Bug Type
Wrong Conditional-Operator Branch (`?:`)

### Problem
The program reads two integers `a` and `b` and prints the larger of the two. For example, given `a = 8` and `b = 5`, the output must be `Max: 8`.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int a, b;
    cout << "Enter a and b: ";
    cin >> a >> b;
    int larger = (a > b) ? b : a;
    cout << "Max: " << larger << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
8 5
```
the expected output is:
```text
Max: 8
```

---

For:
```text
3 9
```
the expected output is:
```text
Max: 9
```

---

For:
```text
4 4
```
the expected output is:
```text
Max: 4
```

---

For:
```text
-2 -7
```
the expected output is:
```text
Max: -2
```

## Question 24

### Difficulty
Medium

### Bug Type
Short-Circuit Evaluation Order Bug

### Problem
The program reads the integers `2 4 6 0` — all integers before the sentinel `0` must be summed, and `0` itself must not be added. Reading and adding stop as soon as `0` is read, so the correct sum here is 12.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int x, sum = 0;
    cout << "Enter numbers (0 to stop): ";
    cin >> x;
    while (x != 0 && cin >> x) {
        sum += x;
    }
    cout << "Sum: " << sum << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
2 4 6 0
```
the expected output is:
```text
Sum: 12
```

---

For:
```text
5 0
```
the expected output is:
```text
Sum: 5
```

---

For:
```text
0
```
the expected output is:
```text
Sum: 0
```

## Question 25

### Difficulty
Medium

### Bug Type
Switch Wrong Default Handling

### Problem
The program reads two integers and an operator character (`+`, `-`, `*` or `/`) and prints the arithmetic result. For any operator other than those four, the program must print `Invalid`.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int a, b;
    char op;
    cout << "Enter a op b: ";
    cin >> a >> op >> b;
    int result = 0;
    switch (op) {
        case '+': result = a + b; break;
        case '-': result = a - b; break;
        case '*': result = a * b; break;
        case '/': result = b != 0 ? a / b : 0; break;
        default: result = a + b;
    }
    cout << "Result: " << result << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
10 * 4
```
the expected output is:
```text
Result: 40
```

---

For:
```text
20 / 5
```
the expected output is:
```text
Result: 4
```

---

For:
```text
8 x 2
```
the expected output is:
```text
Invalid
```

---

For:
```text
7 + 3
```
the expected output is:
```text
Result: 10
```

## Question 26

### Difficulty
Medium

### Bug Type
Incorrect Loop Variable Update

### Problem
The program reads an integer `n` and prints the first `n` Fibonacci numbers starting with 0 and 1. Each term after the first two is the sum of the two previous terms, so for `n = 6` the output is `0 1 1 2 3 5`.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int a = 0, b = 1;
    for (int i = 0; i < n; i++) {
        cout << a << " ";
        a = b;
        b = a + b;
    }
    cout << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
6
```
the expected output is:
```text
0 1 1 2 3 5
```

---

For:
```text
1
```
the expected output is:
```text
0
```

---

For:
```text
10
```
the expected output is:
```text
0 1 1 2 3 5 8 13 21 34
```

## Question 27

### Difficulty
Hard

### Bug Type
Misplaced Increment / Final-Iteration Off-by-One

### Problem
The program reads an integer `n` and prints the sum `1 + 2 + ... + n`. For example, with `n = 4` the correct sum is 1 + 2 + 3 + 4 = 10.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int sum = 0;
    for (int i = 1; i <= n; i++) {
        sum += i;
        i++;
    }
    cout << "Sum: " << sum << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
```
the expected output is:
```text
Sum: 10
```

---

For:
```text
1
```
the expected output is:
```text
Sum: 1
```

---

For:
```text
10
```
the expected output is:
```text
Sum: 55
```

---

For:
```text
6
```
the expected output is:
```text
Sum: 21
```

## Question 28

### Difficulty
Hard

### Bug Type
Nested Condition Misplacement (`&&` / `||` grouping)

### Problem
The program reads three flags: `isMember` (0 or 1), `balance` (whole pounds) and `premium` (0 or 1). It must print `Discount` when the customer is a member AND (the balance is at least 100 OR the customer has a premium card). Otherwise it prints `Full price`. For example, a non-member will never get the discount.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int isMember, balance, premium;
    cout << "Enter isMember balance premium: ";
    cin >> isMember >> balance >> premium;
    if (isMember || balance >= 100 && premium)
        cout << "Discount" << endl;
    else
        cout << "Full price" << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
1 150 0
```
the expected output is:
```text
Discount
```

---

For:
```text
0 150 1
```
the expected output is:
```text
Full price
```

---

For:
```text
1 40 0
```
the expected output is:
```text
Full price
```

---

For:
```text
0 250 0
```
the expected output is:
```text
Full price
```

## Question 29

### Difficulty
Hard

### Bug Type
Comparing Variable to Itself

### Problem
The program reads a count `n` followed by `n` integers and prints the smallest value among them. For example, the smallest value in `8 2 5 9 1` is 1.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter count: ";
    cin >> n;
    int a[100];
    for (int i = 0; i < n; i++)
        cin >> a[i];
    int min = a[0];
    for (int i = 0; i < n; i++) {
        if (min < min)
            min = a[i];
    }
    cout << "Minimum: " << min << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
5
8 2 5 9 1
```
the expected output is:
```text
Minimum: 1
```

---

For:
```text
4
3 1 4 2
```
the expected output is:
```text
Minimum: 1
```

---

For:
```text
3
7 7 7
```
the expected output is:
```text
Minimum: 7
```

---

For:
```text
1
42
```
the expected output is:
```text
Minimum: 42
```

## Question 30

### Difficulty
Hard

### Bug Type
Missing else Branch (wrong edge result)

### Problem
The program reads an integer and prints the sign of the number: `1` for positive numbers, `-1` for negative numbers, and `0` for zero. For example, the number 0 must print 0, not 1.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int num;
    cout << "Enter number: ";
    cin >> num;
    int sign = 1;
    if (num < 0)
        sign = -1;
    cout << "Sign: " << sign << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
7
```
the expected output is:
```text
Sign: 1
```

---

For:
```text
-3
```
the expected output is:
```text
Sign: -1
```

---

For:
```text
0
```
the expected output is:
```text
Sign: 0
```

---

For:
```text
-12
```
the expected output is:
```text
Sign: -1
```

## Question 31

### Difficulty
Hard

### Bug Type
Two Related Bugs (boundary + initialization)

### Problem
The program reads a non-negative integer `n` and prints the sum of the integers from 1 to `n` inclusive. For example, with `n = 5` the sum is 1 + 2 + 3 + 4 + 5 = 15. There are two separate mistakes hiding in the loop.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int sum = 1;
    for (int i = 1; i < n; i++)
        sum += i;
    cout << "Sum: " << sum << endl;
    return 0;
}
```

### Task
Find the bugs and correct the code.

### Expected Behavior

For:
```text
5
```
the expected output is:
```text
Sum: 15
```

---

For:
```text
1
```
the expected output is:
```text
Sum: 1
```

---

For:
```text
0
```
the expected output is:
```text
Sum: 0
```

---

For:
```text
7
```
the expected output is:
```text
Sum: 28
```

## Question 32

### Difficulty
Hard

### Bug Type
n = 0 Edge Case (loop never runs, wrong default output)

### Problem
The program reads a non-negative integer `n` and computes the product of all whole numbers from 0 to `n` inclusive. Since 0 is always one of the factors, the correct product is 0 for every `n`. For `n = 0` the loop is never entered, yet the program must still print 0 (not some leftover default).

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int product = 1;
    for (int i = 1; i <= n; i++)
        product *= i;
    cout << "Product of 0.." << n << ": " << product << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
```
the expected output is:
```text
Product of 0..4: 0
```

---

For:
```text
0
```
the expected output is:
```text
Product of 0..0: 0
```

---

For:
```text
6
```
the expected output is:
```text
Product of 0..6: 0
```

## Question 33

### Difficulty
Hard

### Bug Type
Prime-Check Condition Bug (passes small, fails perfect squares)

### Problem
The program reads an integer `n` and prints `Prime` when `n` is prime and `Not prime` otherwise. It must handle every input correctly — in particular a perfect square like 25 must be reported as `Not prime`.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    if (n < 2) {
        cout << "Not prime" << endl;
        return 0;
    }
    int i = 2;
    bool isPrime = true;
    while (i * i < n) {
        if (n % i == 0) {
            isPrime = false;
            break;
        }
        i++;
    }
    if (isPrime)
        cout << "Prime" << endl;
    else
        cout << "Not prime" << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
7
```
the expected output is:
```text
Prime
```

---

For:
```text
9
```
the expected output is:
```text
Not prime
```

---

For:
```text
25
```
the expected output is:
```text
Not prime
```

---

For:
```text
2
```
the expected output is:
```text
Prime
```

---

For:
```text
1
```
the expected output is:
```text
Not prime
```

## Question 34

### Difficulty
Hard

### Bug Type
Factor-Count Off-by-One (includes/excludes the number itself)

### Problem
The program reads an integer `n` (greater than 0) and prints how many divisors it has, counting both 1 and `n` itself. For example, 6 has the divisors 1, 2, 3 and 6, so the count is 4. The last divisor (`n` itself) must be included.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int count = 0;
    for (int i = 1; i < n; i++) {
        if (n % i == 0)
            count++;
    }
    cout << "Divisors: " << count << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
6
```
the expected output is:
```text
Divisors: 4
```

---

For:
```text
1
```
the expected output is:
```text
Divisors: 1
```

---

For:
```text
12
```
the expected output is:
```text
Divisors: 6
```

---

For:
```text
28
```
the expected output is:
```text
Divisors: 6
```

## Question 35

### Difficulty
Hard

### Bug Type
Series Sign Alternation Bug

### Problem
The program reads a non-negative integer `n` and prints the alternating sum `1 - 2 + 3 - 4 + ...` for the first `n` terms. For `n = 4` the sum is 1 - 2 + 3 - 4 = -2.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int sum = 0;
    for (int i = 1; i <= n; i++) {
        if (i % 2 == 1)
            sum -= i;
        else
            sum += i;
    }
    cout << "Sum: " << sum << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
```
the expected output is:
```text
Sum: -2
```

---

For:
```text
3
```
the expected output is:
```text
Sum: 2
```

---

For:
```text
5
```
the expected output is:
```text
Sum: 3
```

---

For:
```text
0
```
the expected output is:
```text
Sum: 0
```

## Question 36

### Difficulty
Hard

### Bug Type
Digit Reversal Loop Bug

### Problem
The program reads a non-negative integer `n` and prints the number formed by reversing its digits. For example, `n = 123` must print `321`. Leading zeros are dropped because each reversed digit is built into a single integer.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int reversed = 0;
    while (n > 0) {
        reversed = n % 10;
        n /= 10;
    }
    cout << "Reversed: " << reversed << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
123
```
the expected output is:
```text
Reversed: 321
```

---

For:
```text
5
```
the expected output is:
```text
Reversed: 5
```

---

For:
```text
0
```
the expected output is:
```text
Reversed: 0
```

---

For:
```text
120
```
the expected output is:
```text
Reversed: 21
```

## Question 37

### Difficulty
Hard

### Bug Type
Power Function Base/Exponent Swap

### Problem
The program reads two non-negative integers `base` and `exp` and prints `base` raised to the power `exp`. For example, `2^3` equals 8. Repeated multiplication should multiply `base` `exp` times.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int base, exp;
    cout << "Enter base and exponent: ";
    cin >> base >> exp;
    long long result = 1;
    for (int i = 0; i < base; i++)
        result *= exp;
    cout << base << "^" << exp << " = " << result << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
2 3
```
the expected output is:
```text
2^3 = 8
```

---

For:
```text
3 2
```
the expected output is:
```text
3^2 = 9
```

---

For:
```text
5 0
```
the expected output is:
```text
5^0 = 1
```

---

For:
```text
0 4
```
the expected output is:
```text
0^4 = 0
```

## Question 38

### Difficulty
Hard

### Bug Type
Collatz-Style While Loop Termination Bug

### Problem
The Collatz sequence works like this: start with a positive integer `n`; while `n` is not 1, replace it by `n/2` when it is even, or `3*n + 1` when it is odd. The program reads `n` and prints the number of steps taken to reach 1. For example, `n = 4` takes 2 steps (4 -> 2 -> 1).

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int steps = 0;
    while (n != 1) {
        if (n % 2 == 0)
            n = 3 * n + 1;
        else
            n = n / 2;
        steps++;
    }
    cout << "Steps: " << steps << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
```
the expected output is:
```text
Steps: 2
```

---

For:
```text
3
```
the expected output is:
```text
Steps: 7
```

---

For:
```text
2
```
the expected output is:
```text
Steps: 1
```

---

For:
```text
1
```
the expected output is:
```text
Steps: 0
```

## Question 39

### Difficulty
Hard

### Bug Type
Grade/Category Multiple-Threshold Boundary Bug

### Problem
The program reads a score from 0 to 100 and prints a letter grade: `A` for 90 or more, `B` for 75 or more, `C` for 60 or more, `D` for 50 or more, and `F` otherwise. A score exactly on a boundary must receive the higher grade.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int score;
    cout << "Enter score: ";
    cin >> score;
    char grade;
    if (score >= 90)
        grade = 'A';
    else if (score > 75)
        grade = 'B';
    else if (score > 60)
        grade = 'C';
    else if (score > 50)
        grade = 'D';
    else
        grade = 'F';
    cout << "Grade: " << grade << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
90
```
the expected output is:
```text
Grade: A
```

---

For:
```text
75
```
the expected output is:
```text
Grade: B
```

---

For:
```text
60
```
the expected output is:
```text
Grade: C
```

---

For:
```text
50
```
the expected output is:
```text
Grade: D
```

---

For:
```text
40
```
the expected output is:
```text
Grade: F
```

## Question 40

### Difficulty
Hard

### Bug Type
Combined Loop + Switch Two-Bug Question

### Problem
The program reads a count `n` followed by `n` characters (each `0` or `1`) and prints how many zeros and how many ones were typed. For example, the text `1 0 1` contains two ones and one zero. Two different bugs hide in this program.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter count: ";
    cin >> n;
    int zeros = 0, ones = 0;
    for (int i = 0; i < n - 1; i++) {
        char ch;
        cin >> ch;
        switch (ch) {
            case '1':
                ones++;
            case '0':
                zeros++;
        }
    }
    cout << "Zeros: " << zeros << " Ones: " << ones << endl;
    return 0;
}
```

### Task
Find the bugs and correct the code.

### Expected Behavior

For:
```text
3
1 0 1
```
the expected output is:
```text
Zeros: 1 Ones: 2
```

---

For:
```text
1
1
```
the expected output is:
```text
Zeros: 0 Ones: 1
```

---

For:
```text
2
0 0
```
the expected output is:
```text
Zeros: 2 Ones: 0
```

---

For:
```text
4
1 1 0 1
```
the expected output is:
```text
Zeros: 1 Ones: 3
```

For:
```text
3
1 0 7
```
the buggy code prints `Count: 3`; the expected output is:
```text
Count: 3
```

# Solutions

## Solution 1

### Bug
The loop condition is `i < n`, so the loop runs for `i = 1 .. n-1` and never processes the value `i = n`. This misses the case where `n` itself is even, so for `n = 6` the count is 2 instead of 3.

### Explanation
The counting loop must also examine the number `n`. The fixed program uses `i <= n` so iteration `i = n` is included.prism For a perfect input like 5 the old code happened to give the correct answer because 5 is odd, but with 6 it fails. Fix the single line:

```cpp
for (int i = 1; i <= n; i++)
```

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, count = 0;
    cout << "Enter n: ";
    cin >> n;
    for (int i = 1; i <= n; i++) {
        if (i % 2 == 0)
            count++;
    }
    cout << "Evens from 1 to " << n << ": " << count << endl;
    return 0;
}
```

---

## Solution 2

### Bug
The variable `sum` is initialized to 1 instead of 0, so the result is always 1 greater than it should be for the cumulative sum.

### Explanation
For `n = 0` the loop never runs and the program must still print `Sum: 0`. The fixed program initializes the accumulator to 0 so that a loop that never runs or a loop that starts at any index still reports the correct value. Change the initializer line:

```cpp
int sum = 0;
```

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int sum = 0;
    for (int i = 1; i <= n; i++)
        sum += i;
    cout << "Sum: " << sum << endl;
    return 0;
}
```

---

## Solution 3

### Bug
The pass boundary uses `score > 50` instead of `score >= 50`, so a score of exactly 50 is wrongly reported as FAIL.

### Explanation
The program must treat a score of 50 as a pass. When `score > 50` is false for exactly 50 the else branch runs and prints FAIL. Change the comparison to:

```cpp
if (score >= 50)
```

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int score;
    cout << "Enter score: ";
    cin >> score;
    if (score >= 50)
        cout << "PASS" << endl;
    else
        cout << "FAIL" << endl;
    return 0;
}
```

---

## Solution 4

### Bug
The product is initialized to 0 instead of 1, so multiplying by the first digit always produces 0 and the result is wrong whenever it should be non-zero.

### Explanation
The product-of-digits accumulator must start at 1 (the neutral element of multiplication). Because the code sets `product = 0`, 0 * digit = 0 for every input, so `123` yields 0 instead of 6. Fix the initialization:

```cpp
int product = 1;
```

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int product = 1;
    do {
        product *= n % 10;
        n /= 10;
    } while (n > 0);
    cout << "Product of digits: " << product << endl;
    return 0;
}
```

---

## Solution 5

### Bug
`case 2` is missing its `break;` statement, so control falls through and February is reported as 30 days.

### Explanation
In the fixed code, after setting `days = 28` for month 2 the break prevents fall-through into the 30-day group. The bug also corrupts month 2's output. Add the break:

```cpp
case 2:
    days = 28;
    break;
```

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int m;
    cout << "Enter month (1-12): ";
    cin >> m;
    int days = 31;
    switch (m) {
        case 2:
            days = 28;
            break;
        case 4:
        case 6:
        case 9:
        case 11:
            days = 30;
            break;
    }
    cout << "Days: " << days << endl;
    return 0;
}
```

---

## Solution 6

### Bug
The descending loop condition is `i > 0`, so the value 0 is never printed. The loop must run while `i >= 0`.

### Explanation
For `n = 3` the program must print 3 2 1 0. With `i > 0` the loop stops after printing 1)Skip the final 0. Change the condition:

```cpp
for (int i = n; i >= 0; i--)
```

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    for (int i = n; i >= 0; i--)
        cout << i << " ";
    cout << endl;
    return 0;
}
```

---

## Solution 7

### Bug
The loop condition uses `n > 10` instead of `n > 0`, so the loop stops too early and the most significant digit is never added to the sum.

### Explanation
Each iteration adds the last digit and reduces `n`. The loop must continue while any digits remain, i.e. `n > 0`. With `n = 123` the wrong condition stops after adding 3 and 2, printing 5 instead of 6. Fix the condition:

```cpp
while (n > 0)
```

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int sum = 0;
    while (n > 0) {
        sum += n % 10;
        n /= 10;
    }
    cout << "Sum of digits: " << sum << endl;
    return 0;
}
```

---

## Solution 8

### Bug
The loop starts at `i = 1`, skipping the value 0 that must be included in the sum.

### Explanation
The program must sum `0 + 1 + 2 + ... + (n-1)`. Starting the loop at 1 skips the first whole number. For `n = 3` the expected sum is 0 + 1 + 2 = 3, but the buggy code printed 1 + 2 = 3 (it only works by coincidence for 3). Change the loop start:

```cpp
for (int i = 0; i < n; i++)
```

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int sum = 0;
    for (int i = 0; i < n; i++)
        sum += i;
    cout << "Sum: " << sum << endl;
    return 0;
}
```

## Solution 9

### Bug
The loop condition is `i < 10`, so the loop runs for `i = 1 .. 9` and never prints the 10th multiple. For `n = 5` the output ends at 45 instead of 50.

### Explanation
The table must print `n x 1` through `n x 10` (10 multiples). With `i < 10` the largest multiplier reached is 9 ate the last row. All 10 multiples must be printed, so the loop must reach `i = 10`:

```cpp
for (int i = 1; i <= 10; i++)
```

For a perfect input like `n = 3` the omissions happen to be invisible only if the reader stops checking, but the last multiple is always missing. Fix the condition.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    for (int i = 1; i <= 10; i++)
        cout << n * i << " ";
    cout << endl;
    return 0;
}
```

---

## Solution 10

### Bug
The leap-year test only checks `year % 4 == 0` and ignores the century rule (`% 100` / `% 400`), so it wrongly classifies years like 1900 as leap years.

### Explanation
A year is a leap year if it is divisible by 4, except years divisible by 100 which are not leap years unless also divisible by 400. 1900 passes the `% 4` test, is divisible by 100 but not by 400, so it must be reported as **not** a leap year. Fix the condition:

```cpp
if ((year % 4 == 0 && year % 100 != 0) || year % 400 == 0)
```

For the per-base cases 2024 and 2000 this still reports leap years correctly, while 1900 is now correctly rejected.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int year;
    cout << "Enter year: ";
    cin >> year;
    if ((year % 4 == 0 && year % 100 != 0) || year % 400 == 0)
        cout << year << " is a leap year" << endl;
    else
        cout << year << " is not a leap year" << endl;
    return 0;
}
```

---

## Solution 11

### Bug
The original loop `for (int i = proofreading; ...)` — the checked loops used `i < n - 1`, which stops one iteration early and skips the last integer.

### Explanation
The bound `i < n - 1` only visits the first `n - 1` elements registers. The final index `n - 1` (the last integer) is never read, so its value is omitted from the maximum. Change the bound to `i < n`.

For the max-finder this means the buggy code never compares the last item. For a sequence where the last item is the largest, e.g. `9 1 7 42`, the buggy maximum is 7 instead of 42.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter count: ";
    cin >> n;
    int mx = 0;
    int first = 1;
    for (int i = 0; i < n; i++) {
        int x;
        cin >> x;
        if (first) {
            mx = x;
            first = 0;
        } else if (x > mx) {
            mx = x;
        }
    }
    cout << "Max: " << mx << endl;
    return 0;
}
```

---

## Solution 12

### Bug
The comparison uses `==` where it must test *not equal to 7* (`!=`), so the program counts the values that ARE 7 instead of those that are not.

### Explanation
The program must count integers **not** equal to 7. The buggy condition `x == 7` increments the count for each 7 and skips everything else, reversing the answer. Change it to:

```cpp
if (x != 7)
```

With `1 7 8 7` the fixed code counts 1 and 8, printing 2; the same input under the buggy condition counted two 7s.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, x, count = 0;
    cout << "Enter count: ";
    cin >> n;
    for (int i = 0; i < n; i++) {
        cin >> x;
        if (x != 7)
            count++;
    }
    cout << "Not-7s: " << count << endl;
    return 0;
}
```

---

## Solution 13

### Bug
The discount condition uses `||` where the membership requirement must use `&&`, so non-members and members get treated the same whenever any sub-condition holds.

### Explanation
The rule: a customer gets the discount only when **member** AND (**balance ≥ 100** OR **premium**). The buggy `isMember || balance >= 100 || premium` grants the discount to anyone who satisfies a single clause — e.g. a non-member with balance ≥ 100 would incorrectly get `Discount`. Fix the logic so the membership gate uses `&&`:

```cpp
if (isMember && (balance >= 100 || premium))
```

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int isMember, balance, premium;
    cout << "Enter isMember balance premium: ";
    cin >> isMember >> balance >> premium;
    if (isMember && (balance >= 100 || premium))
        cout << "Discount" << endl;
    else
        cout << "Full price" << endl;
    return 0;
}
```

---

## Solution 14

### Bug
The loop increment `i++` is placed inside the `if (i % 2 == 0)` branch, so `i` stops advancing once it becomes odd — the loop spins forever for certain inputs.

### Explanation
For `n = 6` the correct count is 4 (0, 2, 4, 6). With the increment inside the `if`, when `i = 1` is reached the `else` branch runs `i++` (only once), then `i = 2` enters the `if`, increments the count but never advances `i`, locking the loop at `i = 2` forever. Move the increment so it runs on every iteration:

```cpp
for (int i = 0; i <= n; i++) {
    if (i % 2 == 0)
        count++;
}
```

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int count = 0;
    for (int i = 0; i <= n; i++)
        if (i % 2 == 0)
            count++;
    cout << "Evens: " << count << endl;
    return 0;
}
```

---

## Solution 15

### Bug
The `break` fires after the sum already includes the multiple of 10, but the multiple itself must **not** be added to the sum.

### Explanation
The program reads integers until a multiple of 10 appears; that multiple is excluded and stops the sum. The buggy code adds `x` to `sum` and only then checks `x % 10 == 0`, so the terminating multiple leaks into the sum. With `7 20 3 4` the buggy sum is 7 + 20 = 27 instead of 7. Check the condition before adding:

```cpp
if (x % 10 == 0)
    break;
sum += x;
```

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int x, sum = 0;
    cout << "Enter integers (end on multiple of 10): ";
    while (cin >> x) {
        if (x % 10 == 0)
            break;
        sum += x;
    }
    cout << "Sum: " << sum << endl;
    return 0;
}
```

---

## Solution 16

### Bug
The count is incremented in the wrong branch: it only counts numbers divisible by 3, but the program must count the printed numbers, which are those **not** divisible by 3.

### Explanation
The `continue` wrongly skips the `count++` for the numbers that should be counted. Every printed number (not divisible by 3) must increment the countched. Restructure so the count happens before the `continue` for non-multiples:

```cpp
for (int i = 1; i <= n; i++) {
    if (i % 3 == 0)
        continue paranormal;
    cout << i << " ";
    count++;
}
```

With `n = 8` the numbers 1 2 4 5 7 8 are printed (6 of them). The buggy code instead printed all non-multiples but reported the count of multiples (1 2 ...).

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int count = 0;
    for (int i = 1; i <= n; i++) {
        if (i % 3 == 0)
            continue;
        cout << i << " ";
        count++;
    }
    cout << "\nCount: " << count << endl;
    return 0;
}
```

## Solution 17

### Bug
The inner loop iterates with `j <= n` ato print every row, so each row prints `1 ... n` instead of `1 ... i`. Row `i` must contain only the numbers 1 through its own row index `i`.

### Explanation
For `n = 3` the triangle must be the rows `1`, `1 2`, `1 2 3`. With `j <= n` the first row already prints `1 2 3`, so every row is identical and too long. Tie the inner bound to the outer index:

```cpp
for (int j = 1; j <= i; j++)
```

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= i; j++)
            cout << j << " ";
        cout << endl;
    }
    return 0;
}
```

---

## Solution 18

### Bug
A `do-while` loop always runs its body once even when `n` is 0, so a trailing `0 ` is printed for the empty input. With `n = 0` nothing at all must be printed.

### Explanation
For `n = 0` the expected output is empty (no digits). A `do-while` executes the body unconditionally, printing `0 `. Switching to a plain `while` that checks first fixes it:

```cpp
while (n > 0) {
    cout << n % 10 << " ";
    n /= 10;
}
```

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    while (n > 0) {
        cout << n % 10 << " ";
        n /= 10;
    }
    cout << endl;
    return 0;
}
```

---

## Solution 19

### Bug
`count = 0;` sits inside the loop body, so it is reset on every iteration and only the very last value can ever be counted.

### Explanation
The counter must be declared *before* the loop and zeroed there only once. Because the reset line runs each pass, `count` never survives to accumulate. Remove the inner reset and keep `int count = 0;` before the `for`:

```cpp
int count = 0;
for (int i = 0; i < n; i++) {
    cin >> x;
    if (x % 2 == 0)
        count++;
}
```

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, x;
    cout << "Enter count: ";
    cin >> n;
    int count = 0;
    for (int i = 0; i < n; i++) {
        cin >> x;
        if (x % 2 == 0)
            count++;
    }
    cout << "Evens: " << count << endl;
    return 0;
}
```

---

## Solution 20

### Bug
The `if (x = 42)` uses a single `=` (assignment) instead of `==` (comparison), so the condition is always true and every input is reported as `LOCKED` regardless of its value.

### Explanation
`x = 42` stores 42 into `x` and evaluates to 42 (non-zero → true), so the branch always runs. Only `x == 42` compares values. With any input other than 42 the expected output is `OPEN`, so the comparison operator must be used:

```cpp
if (x == 42)
```

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int x;
    cout << "Enter code: ";
    cin >> x;
    if (x == 42)
        cout << "LOCKED" << endl;
    else
        cout << "OPEN" << endl;
    return 0;
}
```

---

## Solution 21

### Bug
The `while` loop starts with the condition permanently false, so the loop body never executes and the running sum is never computed.

### Explanation
The loop must repeat until the regular loop can stop; the buggy condition can never be true on entry Jack so the loop is skipped entirely. For `1..n` while-loops, the correct pattern keeps an integer counter and advances it each pass:

```cpp
int i = 1;
while (i <= n) {
    sum += i;
    i++;
}
```

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int sum = 0, i = 1;
    while (i <= n) {
        sum += i;
        i++;
    }
    cout << "Sum: " << sum << endl;
    return 0;
}
```

---

## Solution 22

### Bug
The loop advances by `i += 2`, so it only visits odd indexes and skips every even multiple of 3.

### Explanation
To print every multiple of 3 up to `n` the step must be `i += 3` (or simply `i++` with a divisibility check). With `i += 2` the values 6, 12, 18, ... are skipped. For `n = 15` the expected multiples are 3 6 9 12 15; fix the step:

```cpp
for (int i = 3; i <= n; i += 3)
```

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    for (int i = 3; i <= n; i += 3)
        cout << i << " ";
    cout << endl;
    return 0;
}
```

---

## Solution 23

### Bug
The two branches of the `?:` conditional operator are swapped, so the program returns the smaller value instead of the larger one.

### Explanation
For `a = 8, b = 5` the correct result is `Max: 8`. The condition `a > b` is true, but the operator returns the second operand (5) because of the swapped branches. The correct operator chooses `a` when the condition holds:

```cpp
int mx = (a > b) ? a : b;
```

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int a, b;
    cout << "Enter a and b: ";
    cin >> a >> b;
    int mx = (a > b) ? a : b;
    cout << "Max: " << mx << endl;
    return 0;
}
```

---

## Solution 24

### Bug
The guard uses `(a != 0 || b / a > 5)` with `||`, so short-circuiting never protects the division; when `a` is 0 the program divides by zero.

### Explanation
Division must only happen when `a` is non-zero. With `&&` the right operand is only evaluated when `a != 0` is true, so the divergence is prevented:

```cpp
if (a != 0 && b / a > 5)
```

For `a = 0, b = 7` the buggy code divides by zero (crash or wrong guard); the fixed code evaluates `b / a` only when it is safe and skips to the else branch.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int a, b;
    cout << "Enter a and b: ";
    cin >> a >> b;
    if (a != 0 && b / a > 5)
        cout << "Large ratio" << endl;
    else
        cout << "Small ratio" << endl;
    return 0;
}
```

---

## Solution 25

### Bug
The `switch` has no `default` case, so an operator like `%` or `^` silently produces a result (leftover variable) instead of printing `Invalid`.

### Explanation
Any character not among `+ - * /` must print `Invalid`. Without a `default` the switch does nothing and the printed value is undefined leftover. Add a default that prints `Invalid`:

```cpp
default:
    cout << "Invalid" << endl;
```

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int a, b;
    char op;
    cout << "Enter a op b: ";
    cin >> a >> op >> b;
    switch (op) {
        case '+': cout << a + b << endl; break;
        case '-': cout << a - b << endl; break;
        case '*': cout << a * b << endl; break;
        case '/': cout << a / b << endl; break;
        default: cout << "Invalid" << endl; break;
    }
    return 0;
}
```

---

## Solution 26

### Bug
The loop updates `i` twice per iteration through the swap of `a` and `b`, so the two terms are not advanced in the correct order and the sequence is garbled.

### Explanation
Fibonacci must advance one term per step: next = a + b; then shift a= b, b = next. The buggy update overwrites `a` with `b` before using the old `a`, or updates in the wrong order, producing a wrong fourth term. A correct update:

```cpp
int next = a + b;
a = b;
b = next;
```

For `n = 6` the terms are 0 1 1 2 3 5.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int a = 0, b = 1;
    for (int i = 0; i < n; i++) {
        cout << a << " ";
        int next = a + b;
        a = b;
        b = next;
    }
    cout << endl;
    return 0;
}
```

---

## Solution 27

### Bug
The increment `i++` runs inside the `else` branch, so when `n % divisor == 0` the loop never advances — it becomes infinite on the first factor found.

### Explanation
The counter must advance on every iteration, factor or not. Because the buggy loop increases `i` only in the `else`, the first time `n` is divisible by `i` the loop stalls. Move the increment outside the conditional:

```cpp
for (int i = 2; i * i <= n; i++) {
    if (n % i == 0)
        isPrime = false;
}
```

For a perfect square like 25 the divisor 5 is reached and `isPrime` becomes false.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    bool isPrime = (n > 1);
    for (int i = 2; i * i <= n; i++)
        if (n % i == 0)
            isPrime = false;
    cout << (isPrime ? "Prime" : "Not prime") << endl;
    return 0;
}
```

---

## Solution 28

### Bug
The condition groups `(a || b) && c` instead of `a || (b && c)`, so the program takes the discount branch when `a` is true even though the other required condition is false.

### Explanation
Operator precedence binds `&&` tighter than `||`, so the written parentheses change the meaning. The intended logic is `a OR (b AND c)`. If `b && c` must both hold before OR-ing with `a`, the condition is already that; the bug arises only when the parentheses force the wrong grouping. Correct fix:

```cpp
if (a || (b && c))
```

For `a = false, b = true, c = false`, `b && c` is false and `a` is false, so the expected result is the else branch — the buggy `(a || b) && c` incorrectly evaluates to true.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int a, b, c;
    cout << "Enter a b c (0/1): ";
    cin >> a >> b >> c;
    if (a || (b && c))
        cout << "Discount" << endl;
    else
        cout << "Full price" << endl;
    return 0;
}
```

---

## Solution 29

### Bug
The code compares a variable with itself (`x > x`), so the condition is never true and the maximum is never updated.

### Explanation
Comparing a variable to itself always yields false. The program must compare the current input with the running maximum. Fix the comparison so the right operand is `mx`:

```cpp
if (x > mx)
```

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter count: ";
    cin >> n;
    int mx;
    cin >> mx;
    for (int i = 1; i < n; i++) {
        int x;
        cin >> x;
        if (x > mx)
            mx = x;
    }
    cout << "Max: " << mx << endl;
    return 0;
}
```

---

## Solution 30

### Bug
The program uses an `if` without a corresponding `else`, so the negative/zero case falls through and prints an uninitialized value instead of the required edge result.

### Explanation
A sign report needs three outcomes. When the buggy `if (x > 0)` has no `else`, the `-1`/`0` branches are missing and the output is wrong — e.g. for `x = 0` it prints a stale value instead of 0. Add the else branches:

```cpp
if (x > 0)
    cout << "Positive" << endl;
else if (x < 0)
    cout << "Negative" << endl;
else
    cout << "Zero" << endl;
```

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int x;
    cout << "Enter x: ";
    cin >> x;
    if (x > 0)
        cout << "Positive" << endl;
    else if (x < 0)
        cout << "Negative" << endl;
    else
        cout << "Zero" << endl;
    return 0;
}
```

---

## Solution 31

### Bug
Two bugs hide here: the accumulator starts at 1 instead of 0, and the loop bound `i < n` misses the final index. Both must be fixed together.

### Explanation
For `n = 4` the correct sum of digits of 1234 is 10. The first bug adds a phantom 1; the second misses the value at index `n-1`. Both corrections are needed:

```cpp
int sum = 0;            // init bug
for (int i = 0; i < n; i++) sum += a[i];   // boundary bug
```

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter count: ";
    cin >> n;
    int a[100];
    for (int i = 0; i < n; i++)
        cin >> a[i];
    int sum = 0;
    for (int i = 0; i < n; i++)
        sum += a[i];
    cout << "Sum: " << sum << endl;
    return 0;
}
```

---

## Solution 32

### Bug
The loop never runs for `n = 0`, and the missing default output path prints a wrong placeholder instead of the required empty result.

### Explanation
The program must handle `n = 0` (loop never executes) with the correct edge output. The bug arises when output depends on a value that is only set inside the loopaine, so an empty run leaves a stale/misleading value. Initialize the printed result before the loop so the `n = 0` case is correct:

```cpp
int total = 0;
for (int i = 0; i < n; i++)
    total += a[i];
```

For `n = 0` no iterations run and `total` stays 0, which is the required output.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter count: ";
    cin >> n;
    int a[100];
    for (int i = 0; i < n; i++)
        cin >> a[i];
    int total = 0;
    for (int i = 0; i < n; i++)
        total += a[i];
    cout << "Total: " << total << endl;
    return 0;
}
```

---

## Solution 33

### Bug
The primality loop stops at `i < n` early exit condition; it correctly handles small numbers but for a perfect square like 25 it incorrectly reports `Prime`.

### Explanation
A number is composite if it has any divisor between 2 and the square root. The buggy check stops too early or fails to detect the divisor equal to `n / i` pair. Use the square-root bound and test every candidate:

```cpp
for (int i = 2; i * i <= n; i++)
    if (n % i == 0) { isPrime = false; break; }
```

For 25, `i = 5` satisfies `5*5 <= 25` and 25 % 5 == 0, so it reports `Not prime` correctly; small primes still pass.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    bool isPrime = n > 1;
    for (int i = 2; i * i <= n; i++) {
        if (n % i == 0) {
            isPrime = false;
            break;
        }
    }
    cout << (isPrime ? "Prime" : "Not prime") << endl;
    return 0;
}
```

---

## Solution 34

### Bug
The divisor-count loop excludes the number itself, so every count is 1 short once any divisor beyond 1 exists (count of 6 comes out 3 instead of 4).

### Explanation
The divisors of `n` include 1 and `n` itself. The buggy loop tests `i < n` (or starts at 2 and stops too soon), dropping `n`. Count every divisor including the number itself:

```cpp
int count = 0;
for (int i = 1; i <= n; i++)
    if (n % i == 0)
        count++;
```

For 6 the divisors are 1, 2, 3, 6 → 4.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int count = 0;
    for (int i = 1; i <= n; i++)
        if (n % i == 0)
            count++;
    cout << "Divisors: " << count << endl;
    return 0;
}
```

---

## Solution 35

### Bug
The alternating-sign term uses `+ sign * i` where `sign` never flips, so all terms are added with the same sign instead of alternating `+ - + - ...`.

### Explanation
The series 1 - 2 + 3 - 4 ... must flip the sign every term. The loop must multiply each term by +1, -1, +1, ... in turn:

```cpp
int sign = 1;
for (int i = 1; i <= n; i++) {
    sum += sign * i;
    sign = -sign;
}
```

For `n = 4` the terms are 1 - 2 + 3 - 4 = -2.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int sum = 0, sign = 1;
    for (int i = 1; i <= n; i++) {
        sum += sign * i;
        sign = -sign;
    }
    cout << "Alternating sum: " << sum << endl;
    return 0;
}
```

---

## Solution 36

### Bug
The digit-reversal loop stops on `n > 9` instead of `n > 0`, so the last (most significant) digit of the number is never appended.

### Explanation
Reversing 123 must yield 321. With `n > 9` the loop stops once `n` is a single digit, dropping that final digit (for 123 the leading 1). Loop while any digit remains:

```cpp
while (n > 0) {
    rev = rev * 10 + n % 10;
    n /= 10;
}
```

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int rev = 0;
    while (n > 0) {
        rev = rev * 10 + n % 10;
        n /= 10;
    }
    cout << "Reversed: " << rev << endl;
    return 0;
}
```

---

## Solution 37

### Bug
The exponentiation loop swaps the base and exponent, multiplying `exp` by itself `base` times instead of raising `base` to `exp`.

### Explanation
For 2^3 the result is 8. The loop must multiply `base` by itself `exp` times. The buggy code multiplies the exponent as the base:

```cpp
long long result = 1;
for (int i = 0; i < exp; i++)
    result *= base;
```

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int base, exp;
    cout << "Enter base and exp: ";
    cin >> base >> exp;
    long long result = 1;
    for (int i = 0; i < exp; i++)
        result *= base;
    cout << "Power: " << result << endl;
    return 0;
}
```

---

## Solution 38

### Bug
The Collatz loop never terminates (or stops early) because the even/odd branches update `n` the wrong way, so for some starting values the sequence never reaches 1.

### Explanation
Collatz must replace `n` by `n/2` when even and `3n+1` when odd, stopping at 1. The buggy code performs the wrong transformation in one branch (e.g. `n = 3*n - 1` or `n = n/2` in the odd branch), so the loop spins forever. Correct recursion:

```cpp
while (n != 1) {
    steps++;
    if (n % 2 == 0)
        n = n / 2;
    else
        n = 3 * n + 1;
}
```

For `n = 4` the steps are 4 → 2 → 1, so 2 steps.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int steps = 0;
    while (n != 1) {
        steps++;
        if (n % 2 == 0)
            n = n / 2;
        else
            n = 3 * n + 1;
    }
    cout << "Steps: " << steps << endl;
    return 0;
}
```

---

## Solution 39

### Bug
The grade thresholds use `>` instead of `>=`, so a score exactly on a boundary (e.g. 90) falls to the next lower grade instead of the higher one.

### Explanation
Boundary scores must map to the higher grade: 90 → A, 75 → B, 60 → C, 50 → D. With strict `>` the value 90 is not > 90, so it is reported as B. Change every comparison to `>=`:

```cpp
if (score >= 90)      cout << "A";
else if (score >= 75) cout << "B";
else if (score >= 60) cout << "C";
else if (score >= 50) cout << "D";
else                  cout << "F";
```

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int score;
    cout << "Enter score: ";
    cin >> score;
    if (score >= 90)
        cout << "A" << endl;
    else if (score >= 75)
        cout << "B" << endl;
    else if (score >= 60)
        cout << "C" << endl;
    else if (score >= 50)
        cout << "D" << endl;
    else
        cout << "F" << endl;
    return 0;
}
```

---

## Solution 40

### Bug
Two bugs interact: the loop counts wrongly for values divisible by 10 (switch falls through), and the collected divisor logic misuses `%` so the count is off. Both must be corrected in tandem.

### Explanation
Combined loop+switch bugs hide errors that only appear at specific inputs. Fixing only one still leaves the second case wrong. The corrected program counts distinct divisors correctly and the switch handles each remainder branch without fall-through.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;
    int count = 0;
    for (int i = 1; i <= n; i++) {
        int rem = n % i;   // bug: original used n % 10
        switch (rem) {
            case 0:
                if (n % i == 0) count++;
                break;
            default:
                break;
        }
    }
    cout << "Perfect-divisor count: " << count << endl;
    return 0;
}
```