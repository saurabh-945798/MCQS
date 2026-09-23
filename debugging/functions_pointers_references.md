# C++ Debugging — Functions, Pointers & References

## Question 1

### Difficulty
Easy

### Bug Type
Pass-by-Value Swap Doesn't Affect Caller

### Problem
The program reads two integers and swaps them using a helper function `swapValues`. The intended behavior is that after calling `swapValues(x, y)`, the variable `x` holds the old value of `y` and vice versa. The caller then prints the swapped values.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

void swapValues(int a, int b) {
    int temp = a;
    a = b;
    b = temp;
}

int main() {
    int x, y;
    cin >> x >> y;
    swapValues(x, y);
    cout << x << " " << y << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
5 10
```
the expected output is:
```text
10 5
```

For:
```text
7 7
```
the expected output is:
```text
7 7
```

For:
```text
12 99
```
the expected output is:
```text
99 12
```

---

## Question 2

### Difficulty
Easy

### Bug Type
Missing Dereference

### Problem
A counter variable `score` is meant to be increased by 1 each time the helper function `bump` is called on its address. The program calls `bump` twice and expects the score to rise by 2 overall.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

void bump(int *value) {
    value++;
}

int main() {
    int score = 95;
    bump(&score);
    bump(&score);
    cout << score << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
score = 95, bump called twice
```
the expected output is:
```text
97
```

For:
```text
score = 0, bump called once
```
the expected output is:
```text
1
```

For:
```text
score = 95, no bump call yet
```
the expected output is:
```text
95
```

---

## Question 3

### Difficulty
Easy

### Bug Type
Returning the Wrong Value from a Function

### Problem
The function `getMax` is supposed to return the larger of its two integer arguments. It is used to decide which of two prices is higher before printing a message. The program reads two integers and prints the larger one.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int getMax(int a, int b) {
    if (a > b)
        return b;
    return a;
}

int main() {
    int p, q;
    cin >> p >> q;
    cout << getMax(p, q) << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
5 9
```
the expected output is:
```text
9
```

For:
```text
9 5
```
the expected output is:
```text
9
```

For:
```text
5 5
```
the expected output is:
```text
5
```

---

## Question 4

### Difficulty
Easy

### Bug Type
Local Variable Shadows Global

### Problem
A global bank balance starts at 100. The function `addMoney` should add a user-supplied amount to the global balance. The main function reads the deposit amount, calls `addMoney`, and prints the global balance afterward.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int balance = 100;

void addMoney(int amount) {
    int balance = 100;
    balance += amount;
}

int main() {
    int choice;
    cin >> choice;
    addMoney(choice);
    cout << balance << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
50
```
the expected output is:
```text
150
```

For:
```text
0
```
the expected output is:
```text
100
```

For:
```text
200
```
the expected output is:
```text
300
```

---

## Question 5

### Difficulty
Easy

### Bug Type
Missing Return Statement

### Problem
A delivery app charges a fare based on zone. Zone 1 costs 100, zone 2 costs 200, and any unknown zone should be free (charge 0). The function `zonePrice` returns the price for a given zone number read from the user.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int zonePrice(int zone) {
    if (zone == 1)
        return 100;
    if (zone == 2)
        return 200;
    return 100;
}

int main() {
    int z;
    cin >> z;
    cout << zonePrice(z) << endl;
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
200
```

For:
```text
5
```
the expected output is:
```text
0
```

For:
```text
1
```
the expected output is:
```text
100
```

---

## Question 6

### Difficulty
Easy

### Bug Type
Function Modifies the Wrong Parameter

### Problem
The function `bump` is supposed to add the same amount `amt` to both of its reference arguments `a` and `b`. The main function reads two integers and an amount, calls `bump`, and prints the updated values.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

void bump(int &a, int &b, int amt) {
    a += amt;
    a += amt;
}

int main() {
    int p, q, amt;
    cin >> p >> q >> amt;
    bump(p, q, amt);
    cout << p << " " << q << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
7 3 5
```
the expected output is:
```text
12 8
```

For:
```text
7 3 0
```
the expected output is:
```text
7 3
```

For:
```text
10 4 2
```
the expected output is:
```text
12 6
```

---

## Question 7

### Difficulty
Easy

### Bug Type
Index vs Pointer Traversal Mix-Up

### Problem
The program computes the sum of the first three elements of an integer array using a pointer. It walks the array with pointer `p` while a loop counter `i` is also used. The intended behavior is to add exactly the three elements 40, 60 and 80.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int marks[] = {40, 60, 80, 100, 120};
    int *p = marks;
    int total = 0;
    for (int i = 0; i < 3; i++) {
        total += p[i];
        p++;
    }
    cout << total << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
marks = {40, 60, 80, 100, 120}, sum first 3 elements
```
the expected output is:
```text
180
```

For:
```text
marks = {5, 5, 5, 5, 5}, sum first 3 elements
```
the expected output is:
```text
15
```

For:
```text
marks = {40}, a single element
```
the expected output is:
```text
40
```

---

## Question 8

### Difficulty
Easy

### Bug Type
Basic Null Check Missing

### Problem
The function `head` returns the first element of an integer array. It is called first on a valid array and then on an empty (NULL) array. A crash on the second call must be avoided, so the function needs a basic null check before touching the array.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int head(int nums[]) {
    return nums[0];
}

int main() {
    int values[] = {7, 8, 9};
    cout << head(values) << endl;
    int *empty = NULL;
    cout << head(empty) << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
array = {7, 8, 9}
```
the expected output is:
```text
7
```

For:
```text
array = NULL
```
the expected output is:
```text
-1
```

(the buggy code prints 7 and then crashes before printing the second line)

For:
```text
array = {1, 2}
```
the expected output is:
```text
1
```

---

## Question 9

### Difficulty
Medium

### Bug Type
Array Parameter Decays to Pointer — Wrong sizeof

### Problem
A reporting utility prints the number of elements in an integer array. In `main` the count is computed with `sizeof`, and the same kind of count is expected when the array is passed to the helper `reportSize`. Both prints should agree.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

void reportSize(int data[]) {
    cout << sizeof(data) / sizeof(data[0]) << endl;
}

int main() {
    int numbers[] = {1, 2, 3, 4, 5};
    cout << sizeof(numbers) / sizeof(numbers[0]) << endl;
    reportSize(numbers);
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
numbers = {1, 2, 3, 4, 5}
```
the expected output is:
```text
5
5
```

For:
```text
numbers = {10, 20, 30}
```
the expected output is:
```text
3
3
```

For:
```text
numbers = {7}
```
the expected output is:
```text
1
1
```

---

## Question 10

### Difficulty
Medium

### Bug Type
Modifying a Local Copy Instead of the Original Array

### Problem
The function `reset` is supposed to set the first element of the array it receives to 0. The program prints the first element, calls `reset`, and prints the first element again, expecting it to have become 0.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

void reset(int arr[]) {
    int first = arr[0];
    first = 0;
}

int main() {
    int data[] = {42, 7, 7};
    cout << data[0] << endl;
    reset(data);
    cout << data[0] << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
data = {42, 7, 7}
```
the expected output is:
```text
42
0
```

For:
```text
data = {0, 9, 3}
```
the expected output is:
```text
0
0
```

For:
```text
data = {15, 6}
```
the expected output is:
```text
15
0
```

---

## Question 11

### Difficulty
Medium

### Bug Type
Double Pointer Wrong Access Level

### Problem
The function `assignValue` receives a pointer-to-pointer and a source pointer. Its job is to copy the value lying behind `newPointer` into the memory location behind `holder` (which is `a` in main). The program prints `a` and the value `*p` (`p` still points at `a`), expecting both to be 60.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

void assignValue(int **holder, int *newPointer) {
    *holder = newPointer;
}

int main() {
    int a = 50, b = 60;
    int *p = &a;
    int **pp = &p;
    assignValue(pp, &b);
    cout << a << " " << *p << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
a = 50, b = 60
```
the expected output is:
```text
60 60
```

For:
```text
a = 50, b = 50
```
the expected output is:
```text
50 50
```

For:
```text
a = 8, b = 21
```
the expected output is:
```text
21 21
```

---

## Question 12

### Difficulty
Medium

### Bug Type
Recursion Parameter Shadowing

### Problem
A global step size of 1 controls how `seriesSum` walks down from `n`, summing every number from `n` down to 0. For input 5 the expected sum is 5 + 4 + 3 + 2 + 1 = 15. The recursion steps down by the global `step`.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int step = 1;

int seriesSum(int n) {
    if (n <= 0)
        return 0;
    int step = 2;
    return n + seriesSum(n - step);
}

int main() {
    int input;
    cin >> input;
    cout << seriesSum(input) << endl;
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
15
```

For:
```text
0
```
the expected output is:
```text
0
```

For:
```text
4
```
the expected output is:
```text
10
```

---

## Question 13

### Difficulty
Medium

### Bug Type
Pointer Arithmetic Skips Elements

### Problem
The program walks an integer array with a pointer and adds up the first three elements (1 + 2 + 3 = 6). Each iteration should move the pointer forward by exactly one element.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int nums[] = {1, 2, 3, 4, 5};
    int *p = nums;
    int sum = 0;
    for (int i = 0; i < 3; i++) {
        sum += *p;
        p += 2;
    }
    cout << sum << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
nums = {1, 2, 3, 4, 5}
```
the expected output is:
```text
6
```

For:
```text
nums = {2, 4, 6, 8, 10}
```
the expected output is:
```text
12
```

For:
```text
nums = {1, 1, 1, 1, 1}
```
the expected output is:
```text
3
```

---

## Question 14

### Difficulty
Medium

### Bug Type
Function-Dispatch Bug (wrong branch selected)

### Problem
A courier service charges by weight: up to 2 kg costs 50, 3–5 kg costs 100, 6–10 kg costs 200, and anything over 10 kg costs 500. The function `shippingCost` should select the right price bracket for the weight read from the user.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int shippingCost(int weight) {
    if (weight <= 2)
        return 50;
    if (weight <= 5)
        return 100;
    if (weight <= 9)
        return 200;
    return 500;
}

int main() {
    int w;
    cin >> w;
    cout << shippingCost(w) << endl;
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
100
```

For:
```text
10
```
the expected output is:
```text
200
```

For:
```text
12
```
the expected output is:
```text
500
```

---

## Question 15

### Difficulty
Medium

### Bug Type
Default Argument Not Applied

### Problem
A store computes the price of an order by applying a tax rate that defaults to 10%. When the caller passes no rate, the 10% default must still be charged. The program prints the taxed price for an order of 1000 using the default rate, and then 1000 with an explicit 20% rate.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int applyTax(int amount, int rate = 10) {
    bool usedDefault = (rate == 10);
    if (usedDefault)
        rate = 0;
    return amount + amount * rate / 100;
}

int main() {
    cout << applyTax(1000) << endl;
    cout << applyTax(1000, 20) << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
amount = 1000, default rate
```
the expected output is:
```text
1100
```

For:
```text
amount = 1000, rate = 20
```
the expected output is:
```text
1200
```

For:
```text
amount = 0, default rate
```
the expected output is:
```text
0
```

---

## Question 16

### Difficulty
Medium

### Bug Type
Accumulator Through Reference Wrong Update

### Problem
A cash register keeps a running total that must survive across many sales. Each call to `recordSale` should add the sale amount to the reference `runningTotal`. Two sales of 25 and 10 should leave a running total of 35.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

void recordSale(double amount, double &runningTotal) {
    double updated = runningTotal + amount;
    amount = updated;
}

int main() {
    double total = 0.0;
    recordSale(25.0, total);
    recordSale(10.0, total);
    cout << total << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
sales = 25.0 then 10.0
```
the expected output is:
```text
35
```

For:
```text
sales = 0.0 then 0.0
```
the expected output is:
```text
0
```

For:
```text
sales = 4.5 then 3.5
```
the expected output is:
```text
8
```

---

## Question 17

### Difficulty
Medium

### Bug Type
Null Check in the Wrong Place

### Problem
The function `combine` adds two ints pointed to by `x` and `y`. Either pointer may be NULL, in which case the function should print "invalid" and return -1. The program tests three calls, including one where `y` is NULL.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int combine(int *x, int *y) {
    if (x == NULL) {
        cout << "invalid" << endl;
        return -1;
    }
    return *x + *y;
}

int main() {
    int v1 = 30, v2 = 12;
    cout << combine(&v1, &v2) << endl;
    int *nothing = NULL;
    cout << combine(&v1, nothing) << endl;
    cout << combine(nothing, &v2) << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
both pointers valid (30 and 12)
```
the expected output is:
```text
42
```

For:
```text
y = NULL
```
the expected output is:
```text
invalid
-1
```

For:
```text
x = NULL
```
the expected output is:
```text
invalid
-1
```

(the buggy code prints 42 and then crashes on the second call)

---

## Question 18

### Difficulty
Medium

### Bug Type
Const-Cast Misuse

### Problem
The function `raiseAll` adds the same amount to every element of an integer array. In `main` it is applied to a writable local `budget` array and then to a file-wide `const` array `quota`. A const object must never be modified, so the second use must not compile-time/run-time corrupt the read-only data.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

const int quota[3] = {100, 200, 300};

void raiseAll(int *data, int size, int amount) {
    for (int i = 0; i < size; i++)
        data[i] += amount;
}

int main() {
    int budget[3] = {100, 200, 300};
    raiseAll(budget, 3, 50);
    cout << budget[0] << " " << budget[1] << " " << budget[2] << endl;

    raiseAll(const_cast<int *>(quota), 3, 50);
    cout << quota[0] << " " << quota[1] << " " << quota[2] << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
writable array {100, 200, 300}, amount 50
```
the expected output is:
```text
150 250 350
```

For:
```text
const array {100, 200, 300}, amount 50
```
the expected output is:
```text
100 200 300
```

(the buggy code prints the first line and then crashes — or corrupts memory — because it writes to a const object)

---

## Question 19

### Difficulty
Medium

### Bug Type
Returning a Pointer to a Local Variable

### Problem
The function `findValue` searches a prices table for a target and should return the matching price. When the target is missing it should signal that fact without breaking. The program looks up a price that exists and then a price (999) that does not exist, printing both results.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int *findValue(int target, int table[], int size) {
    for (int i = 0; i < size; i++)
        if (table[i] == target)
            return &table[i];
    int notFound = -1;
    return &notFound;
}

int main() {
    int prices[] = {100, 250, 400};
    cout << *findValue(250, prices, 3) << endl;
    int *missing = findValue(999, prices, 3);
    cout << *missing << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
target = 250
```
the expected output is:
```text
250
```

For:
```text
target = 999 (not present)
```
the expected output is:
```text
-1
```

(modifying or reading the returned pointer in the buggy code after the function returns is undefined — it typically prints garbage or crashes)

---

## Question 20

### Difficulty
Hard

### Bug Type
Dangling Pointer Access After Scope

### Problem
`makePair` creates a two-element local array and returns it so the caller can read the pair. In `main`, another local array is declared after the call and then the returned pointer is read. The intended output is the original pair 10 20.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int *makePair() {
    int pair[2] = {10, 20};
    return pair;
}

int main() {
    int *p = makePair();
    int filler[4] = {1, 2, 3, 4};
    cout << p[0] << " " << p[1] << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
makePair returns {10, 20}
```
the expected output is:
```text
10 20
```

For:
```text
makePair returns {5, 9}
```
the expected output is:
```text
5 9
```

(reading through the returned pointer in the buggy code is undefined — the local array has gone out of scope, so garbage values such as 1 2 are produced on typical implementations)

---

## Question 21

### Difficulty
Hard

### Bug Type
Reference Alias Bound to Wrong Target

### Problem
The program wants `ref` to be an alias for the variable `b` (so that later writes through `ref` change `b`). After binding, `ref` is increased by 10. The intended result is that `a` stays 5 and `b` becomes 30.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 5, b = 20;
    int &ref = a;
    cout << ref << endl;
    ref = b;
    ref += 10;
    cout << a << " " << b << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
a = 5, b = 20
```
the expected output is:
```text
5
5 30
```

For:
```text
a = 0, b = 100
```
the expected output is:
```text
0
0 110
```

---

## Question 22

### Difficulty
Hard

### Bug Type
Comparing Pointers Instead of the Values They Point To

### Problem
The function `checkEquality` is meant to report whether two integers hold the same value. It is called once with two distinct variables that both hold 7, and once with the very same variable passed twice.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

void checkEquality(int *u, int *v) {
    if (u == v)
        cout << "equal" << endl;
    else
        cout << "different" << endl;
}

int main() {
    int a = 7, b = 7;
    checkEquality(&a, &b);
    checkEquality(&a, &a);
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
u and v are distinct variables, both value 7
```
the expected output is:
```text
equal
```

For:
```text
u and v refer to the same variable
```
the expected output is:
```text
equal
```

For:
```text
u = 3, v = 9 (distinct addresses)
```
the expected output is:
```text
different
```

---

## Question 23

### Difficulty
Hard

### Bug Type
Two Related Bugs (null + arithmetic)

### Problem
`chainSum` is meant to return the sum of all `count` elements of `scores`, and -1 if `scores` is NULL. It is tested on a three-element list whose first value is 0, a four-element list summing to 50, and a NULL list that must be handled gracefully.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int chainSum(int *scores, int count) {
    int total = 0;
    for (int i = 1; i < count; i++)
        total += scores[i];
    if (scores == NULL)
        return -1;
    return total;
}

int main() {
    int listA[] = {0, 4, 6};
    cout << chainSum(listA, 3) << endl;
    int listB[] = {5, 10, 15, 20};
    cout << chainSum(listB, 4) << endl;
    int *nothing = NULL;
    cout << chainSum(nothing, 2) << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
listA = {0, 4, 6}
```
the expected output is:
```text
10
```

For:
```text
listB = {5, 10, 15, 20}
```
the expected output is:
```text
50
```

For:
```text
scores = NULL
```
the expected output is:
```text
-1
```

(the buggy code prints 10, prints 45, and then crashes by dereferencing NULL)

---

## Question 24

### Difficulty
Hard

### Bug Type
Missing & in a Reference Parameter

### Problem
The function `updateTotal` must add `amount` to the *caller's* `running` variable. The main function calls it once with 0 (a sanity check) and then with 50 and 10, printing `running` after the sanity check and again after the two updates.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

void updateTotal(int amount, int total) {
    total += amount;
}

int main() {
    int running = 100;
    updateTotal(0, running);
    cout << running << endl;
    updateTotal(50, running);
    updateTotal(10, running);
    cout << running << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
start = 100, then 0, 50, 10
```
the expected output is:
```text
100
160
```

For:
```text
start = 0, then 0, 0
```
the expected output is:
```text
0
0
```

For:
```text
start = 40, then 5, 15
```
the expected output is:
```text
40
60
```

---

## Question 25

### Difficulty
Hard

### Bug Type
Updating the Pointer Itself Through Pointer-to-Pointer

### Problem
`redirect` should make the caller's pointer `current` point at `spare` by updating the pointer through the pointer-to-pointer parameter. After the redirect, `*current = 100` must write into `spare`, leaving `primary` untouched. The three printed values should be 90 100 100.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

void redirect(int **slot, int *newTarget) {
    slot = &newTarget;
}

int main() {
    int primary = 90, spare = 60;
    int *current = &primary;
    redirect(&current, &spare);
    *current = 100;
    cout << primary << " " << spare << " " << *current << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
primary = 90, spare = 60
```
the expected output is:
```text
90 100 100
```

For:
```text
primary = 5, spare = 5
```
the expected output is:
```text
5 100 100
```

---

## Question 26

### Difficulty
Hard

### Bug Type
Recursive Function Decrements Twice

### Problem
`sumUp(n)` should return the sum 1 + 2 + ... + n by recursing one step at a time. The program first prints the trivial cases (0 and 1), then the sums for 5 and 4. The expected sums are 15 and 10.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int sumUp(int n) {
    if (n <= 0)
        return 0;
    return n + sumUp(n - 2);
}

int main() {
    cout << sumUp(0) << " " << sumUp(1) << endl;
    cout << sumUp(5) << endl;
    cout << sumUp(4) << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
n = 0 and n = 1
```
the expected output is:
```text
0 1
```

For:
```text
n = 5
```
the expected output is:
```text
15
```

For:
```text
n = 4
```
the expected output is:
```text
10
```

---

## Question 27

### Difficulty
Hard

### Bug Type
Owning-Pointer Mistake (double delete)

### Problem
`main` allocates an integer on the heap, prints its value, then hands it to `cleanup` to be freed and prints "done" afterward. The heap object must be released exactly once.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

void cleanup(int *p) {
    delete p;
    delete p;
}

int main() {
    int *score = new int(42);
    cout << *score << endl;
    cleanup(score);
    cout << "done" << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
heap value 42
```
the expected output is:
```text
42
done
```

For:
```text
heap value 7
```
the expected output is:
```text
7
done
```

(the buggy code prints the value and then aborts/crashes on the double free, so "done" is never printed reliably)

---

## Question 28

### Difficulty
Hard

### Bug Type
Array of Pointers Wrong Access

### Problem
Three integers are pointed to by the pointer array `cells`. The program is supposed to add the values behind all three pointers (10 + 20 + 30 = 60), respecting the loop index `i`.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 10, b = 20, c = 30;
    int *cells[] = {&a, &b, &c};
    int total = 0;
    for (int i = 0; i < 3; i++)
        total += *cells[0];
    cout << total << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
a = 10, b = 20, c = 30
```
the expected output is:
```text
60
```

For:
```text
a = 5, b = 5, c = 5
```
the expected output is:
```text
15
```

For:
```text
a = 4, b = 6, c = 7
```
the expected output is:
```text
17
```

---

## Question 29

### Difficulty
Hard

### Bug Type
Sum Written to the Wrong Target Through a Pointer

### Problem
`mergeSum` adds each element of `extra` into the corresponding element of `dest` (dest[i] = dest[i] + extra[i]). The program merges two triplets and then a pair of all-zero triplets, printing all six values each time.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

void mergeSum(int dest[], int extra[], int count) {
    for (int i = 0; i < count; i++)
        extra[i] += dest[i];
}

void show(int d[3], int e[3]) {
    for (int i = 0; i < 3; i++) cout << d[i] << " ";
    for (int i = 0; i < 3; i++) cout << e[i] << " ";
    cout << endl;
}

int main() {
    int d1[3] = {1, 2, 3}, e1[3] = {10, 20, 30};
    mergeSum(d1, e1, 3);
    show(d1, e1);

    int d2[3] = {0, 0, 0}, e2[3] = {0, 0, 0};
    mergeSum(d2, e2, 3);
    show(d2, e2);
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
dest = {1, 2, 3}, extra = {10, 20, 30}
```
the expected output is:
```text
11 22 33 10 20 30
```

For:
```text
dest = {0, 0, 0}, extra = {0, 0, 0}
```
the expected output is:
```text
0 0 0 0 0 0
```

For:
```text
dest = {5, 6, 7}, extra = {0, 1, 2}
```
the expected output is:
```text
5 7 9 0 1 2
```

---

## Question 30

### Difficulty
Hard

### Bug Type
Const-Correctness + Pointer Two-Bug Combo

### Problem
`trim` must clamp `*value` so it never exceeds `*cap`. The cap is a const parameter that must never be modified. For a value of 250 and a cap of 100, the result should be that `value` becomes 100 while `cap` stays 100.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

void trim(int *value, const int *cap) {
    int *writableCap = (int *)cap;
    if (*value > *writableCap)
        *writableCap = *value;
}

int main() {
    int val = 250;
    int limit = 100;
    trim(&val, &limit);
    cout << val << " " << limit << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
value = 250, cap = 100
```
the expected output is:
```text
100 100
```

For:
```text
value = 50, cap = 100
```
the expected output is:
```text
50 100
```

For:
```text
value = 300, cap = 250
```
the expected output is:
```text
250 250
```

---

# Solutions

## Solution 1

### Bug
`swapValues` takes its parameters by value, so it swaps copies and never changes `x` and `y` in `main`. The callers' variables keep their original values.

### Explanation
In C++, function parameters are passed by value unless a reference (`&`) or pointer is used. Here `a` and `b` are fresh local copies: swapping them has no effect on `x` and `y`. For input `5 10` the buggy program prints `5 10`; the expected output is `10 5`. Passing the parameters by reference lets the function operate on the actual arguments.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

void swapValues(int &a, int &b) {
    int temp = a;
    a = b;
    b = temp;
}

int main() {
    int x, y;
    cin >> x >> y;
    swapValues(x, y);
    cout << x << " " << y << endl;
    return 0;
}
```

---

## Solution 2

### Bug
`bump` increments the pointer itself (`value++`) instead of the integer it points to. The variable `score` is never changed, so it stays 95 instead of 97.

### Explanation
`value++` moves the pointer to the next `int`, leaving the target int untouched. The increment must be applied to the pointed-to object, which requires dereferencing first (`(*value)++` or `*value += 1`). Never forget the `*` when the work is meant for the pointee and not the pointer.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

void bump(int *value) {
    (*value)++;
}

int main() {
    int score = 95;
    bump(&score);
    bump(&score);
    cout << score << endl;
    return 0;
}
```

---

## Solution 3

### Bug
`getMax` returns the wrong branch: when `a > b` it returns `b` (the smaller), otherwise it returns `a` (again the smaller or equal). It should return the argument in the correct branch.

### Explanation
The condition is correct but the returned value is flipped. For `5 9` and `9 5` the function prints `5` instead of `9`. The fix returns `a` inside the `a > b` branch (and `b` otherwise), or, equivalently, `a > b ? a : b`. Equal inputs `5 5` happen to work, which makes the bug easy to miss in testing.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int getMax(int a, int b) {
    if (a > b)
        return a;
    return b;
}

int main() {
    int p, q;
    cin >> p >> q;
    cout << getMax(p, q) << endl;
    return 0;
}
```

---

## Solution 4

### Bug
Inside `addMoney`, a local variable also named `balance` shadows the global `balance`. All of the work is done on the local, so the global is never updated.

### Explanation
The local `int balance = 100;` hides the global one inside the function, so `balance += amount` modifies the local and the result is discarded when the function returns. For input `50` the buggy program prints `100`; the expected output is `150`. Removing the local declaration makes `balance += amount` refer to the global variable.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int balance = 100;

void addMoney(int amount) {
    balance += amount;
}

int main() {
    int choice;
    cin >> choice;
    addMoney(choice);
    cout << balance << endl;
    return 0;
}
```

---

## Solution 5

### Bug
For an unknown zone, `zonePrice` falls through to `return 100;` — an explicit wrong fallback that charges zone-1 fares. The else-return (the "unknown zone" return) was never written correctly.

### Explanation
The two checks handle zone 1 and zone 2, but the third return is intended to serve as the "else" case for any other zone. Reusing 100 silently overcharges the caller, e.g. input `5` prints `100` instead of the required `0`. The fix replaces that fallback with the true default value 0.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int zonePrice(int zone) {
    if (zone == 1)
        return 100;
    if (zone == 2)
        return 200;
    return 0;
}

int main() {
    int z;
    cin >> z;
    cout << zonePrice(z) << endl;
    return 0;
}
```

---

## Solution 6

### Bug
`bump` performs both increments on `a` (`a += amt` twice) and never touches `b`. Both reference parameters must be updated once.

### Explanation
The function is documented to add the amount to both arguments, but the second c-style line `a += amt;` repeats the same target instead of `b`. For input `7 3 5` the buggy program prints `17 3`; the expected output is `12 8`. The baseline input `7 3 0` masks the problem because adding 0 does not change either value.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

void bump(int &a, int &b, int amt) {
    a += amt;
    b += amt;
}

int main() {
    int p, q, amt;
    cin >> p >> q >> amt;
    bump(p, q, amt);
    cout << p << " " << q << endl;
    return 0;
}
```

---

## Solution 7

### Bug
`p[i]` is used (indexing) at the same time as the pointer is advanced with `p++`. Because `p` moves after every read, elements are skipped: 40, then 80, then 120 — not 40, 60, 80.

### Explanation
Combining two traversal styles corrupts the addresses. `p[i]` means `*(p + i)`, and since `p` itself already advanced by 1 each loop, iteration reads offsets 0, 2 and 4 from the original array (40 + 80 + 120 = 240 instead of 180). Choose one style: index the original array (`marks[i]`) or walk with the pointer (`*p` + `p++`).

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int marks[] = {40, 60, 80, 100, 120};
    int *p = marks;
    int total = 0;
    for (int i = 0; i < 3; i++) {
        total += *p;
        p++;
    }
    cout << total << endl;
    return 0;
}
```

---

## Solution 8

### Bug
`head` dereferences `nums` without first checking whether it is NULL. The first call works, but the second call (with NULL) crashes.

### Explanation
A pointer can legally be NULL, and dereferencing NULL is undefined behavior — here a clean access violation. The fix is a basic guard: if `nums` is NULL, return a sentinel (`-1`) immediately without touching the array. Note that an array parameter decays to a pointer, so it too can be NULL.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int head(int nums[]) {
    if (nums == NULL)
        return -1;
    return nums[0];
}

int main() {
    int values[] = {7, 8, 9};
    cout << head(values) << endl;
    int *empty = NULL;
    cout << head(empty) << endl;
    return 0;
}
```

---

## Solution 9

### Bug
Inside `reportSize`, `sizeof(data)` measures a pointer, not the array, because array parameters decay to pointers. The helper prints 2 (on 64-bit) regardless of the true element count.

### Explanation
In `main`, `numbers` is a true array, so `sizeof(numbers)/sizeof(numbers[0])` gives 5. But as a parameter, `data` is just an `int*`, and `sizeof(int*)` is the pointer size (e.g. 8), giving 8/4 = 2. The array size is no longer known at the call site inside the function — it must be passed explicitly.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

void reportSize(int data[], int size) {
    cout << size << endl;
}

int main() {
    int numbers[] = {1, 2, 3, 4, 5};
    cout << sizeof(numbers) / sizeof(numbers[0]) << endl;
    reportSize(numbers, 5);
    return 0;
}
```

---

## Solution 10

### Bug
`reset` copies `arr[0]` into a local `first` and then zeros the copy. The real first element of the array is never changed, so the second print shows 42 again.

### Explanation
`int first = arr[0];` creates an independent local copy. Assigning `first = 0;` writes to the copy. To change the caller's data, write directly through the array: `arr[0] = 0;`. The trivial-looking fix is meaningful because arrays are passed as pointers, so `arr[]` in a parameter list is the actual array.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

void reset(int arr[]) {
    arr[0] = 0;
}

int main() {
    int data[] = {42, 7, 7};
    cout << data[0] << endl;
    reset(data);
    cout << data[0] << endl;
    return 0;
}
```

---

## Solution 11

### Bug
`assignValue` writes one level too shallow: `*holder = newPointer;` rebinds the pointer `p` to `&b` instead of copying `b`'s value into `a`. The intended write was `**holder = *newPointer;`.

### Explanation
`holder` is an `int**` — `*holder` is the pointer `p`, and `**holder` is the int it points to (here `a`). Because the function only swaps which int `p` refers to, `a` keeps its old value 50 and the output is `50 60` instead of `60 60`. When a value > 50 duplicates the target (input `a = 50, b = 50`), both versions agree — a sneaky baseline that masks the bug.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

void assignValue(int **holder, int *newPointer) {
    **holder = *newPointer;
}

int main() {
    int a = 50, b = 60;
    int *p = &a;
    int **pp = &p;
    assignValue(pp, &b);
    cout << a << " " << *p << endl;
    return 0;
}
```

---

## Solution 12

### Bug
A local `int step = 2;` shadows the global `step = 1` inside `seriesSum`, so every recursive call drops by 2 instead of 1: 5 + 3 + 1 = 9 rather than 15.

### Explanation
Name shadowing: the function's local `step` hides the global of the same name, so `n - step` uses the local 2. Removing the local declaration makes `seriesSum(n - step)` use the global step 1, summing every integer. The stale-value inputs 0 (and generally n ≤ 0) fall into the base case and obfuscate the recursion depth issue.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int step = 1;

int seriesSum(int n) {
    if (n <= 0)
        return 0;
    return n + seriesSum(n - step);
}

int main() {
    int input;
    cin >> input;
    cout << seriesSum(input) << endl;
    return 0;
}
```

---

## Solution 13

### Bug
The pointer is advanced by `p += 2` each iteration, so every other element is skipped: 1 + 3 + 5 = 9 instead of 1 + 2 + 3 = 6.

### Explanation
`p += 2` moves the pointer two `int`s per loop (elements 0, 2, 4). The intended walk is one element at a time (`p++` or `p += 1`). The loop reads only elements that are still in bounds, so the wrong sum is silently produced rather than crashing. A uniform array like `{1, 1, 1}` gives the same total either way and would hide the bug.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int nums[] = {1, 2, 3, 4, 5};
    int *p = nums;
    int sum = 0;
    for (int i = 0; i < 3; i++) {
        sum += *p;
        p++;
    }
    cout << sum << endl;
    return 0;
}
```

---

## Solution 14

### Bug
The second bracket uses `weight <= 9` instead of `weight <= 10`, so a 10 kg package is routed to the "over 10" branch and charged 500 instead of 200.

### Explanation
`shippingCost` is a tier-dispatch function. With the boundary shifted down by one, the input `10` selects the wrong price band. The baseline inputs `3` (-> 100) and `12` (-> 500) still hit the right branches, so only the boundary value exposes the error (`10` prints 500; correctly it prints 200).

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int shippingCost(int weight) {
    if (weight <= 2)
        return 50;
    if (weight <= 5)
        return 100;
    if (weight <= 10)
        return 200;
    return 500;
}

int main() {
    int w;
    cin >> w;
    cout << shippingCost(w) << endl;
    return 0;
}
```

---

## Solution 15

### Bug
When the default rate (10) is in effect, the "promo" logic zeroes the rate before computing, so the default tax of 10% is never actually applied — 1000 is printed as 1000 instead of 1100.

### Explanation
The default argument works correctly (rate becomes 10), but the body mistakes "rate equal to the default" for "tax-free" and forces the rate to 0. Detecting the default by comparing values is fragile and wrong here. The fix simply computes with the rate the caller provided. Explicit rates (20%) are unaffected, and a zero-order gives 0 either way — both mask the fault.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int applyTax(int amount, int rate = 10) {
    return amount + amount * rate / 100;
}

int main() {
    cout << applyTax(1000) << endl;
    cout << applyTax(1000, 20) << endl;
    return 0;
}
```

---

## Solution 16

### Bug
`recordSale` computes the new total into `updated` but writes it into the local parameter `amount` instead of the reference `runningTotal`. The running total is never advanced, so it stays 0 after both sales.

### Explanation
`double updated = runningTotal + amount;` is correct; the failure is the write-back: `amount = updated;` only changes the function's own copy of the sale value. Assigning `runningTotal = updated;` (or, simpler, `runningTotal += amount;`) updates the caller's accumulator for later calls. Zero-value sales make the two behaviors identical and hide the defect.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

void recordSale(double amount, double &runningTotal) {
    runningTotal += amount;
}

int main() {
    double total = 0.0;
    recordSale(25.0, total);
    recordSale(10.0, total);
    cout << total << endl;
    return 0;
}
```

---

## Solution 17

### Bug
`combine` only guards `x`. When `y` is NULL the guard misses and `*y` is dereferenced, crashing the program (prints `42` from the first call, then an access violation).

### Explanation
The null check is present but placed on the wrong pointer/x-parameter only. Both pointer arguments can be NULL, so both must be validated — combined with `||` in one condition — before any dereference. The crash only occurs for the `y == NULL` input; the `x == NULL` input works correctly, which makes the bug look inconsistent and easy to misdiagnose.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int combine(int *x, int *y) {
    if (x == NULL || y == NULL) {
        cout << "invalid" << endl;
        return -1;
    }
    return *x + *y;
}

int main() {
    int v1 = 30, v2 = 12;
    cout << combine(&v1, &v2) << endl;
    int *nothing = NULL;
    cout << combine(&v1, nothing) << endl;
    cout << combine(nothing, &v2) << endl;
    return 0;
}
```

---

## Solution 18

### Bug
`const_cast<int *>(quota)` casts away `const` from a genuinely const object so that `raiseAll` can write into read-only data. Writing to a const object is undefined behavior — here it crashes (or corrupts memory) instead of printing `100 200 300`.

### Explanation
`raiseAll` is fine for writable arrays, but the second call drags a const object into a mutating function. Casting away const to *write* is almost always a design error. The correct approach is to keep the const object untouched: raise only writable data, or copy the const values into a fresh array first as shown below.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

const int quota[3] = {100, 200, 300};

void raiseAll(int *data, int size, int amount) {
    for (int i = 0; i < size; i++)
        data[i] += amount;
}

int main() {
    int budget[3] = {100, 200, 300};
    raiseAll(budget, 3, 50);
    cout << budget[0] << " " << budget[1] << " " << budget[2] << endl;

    int copy[3] = {100, 200, 300};
    raiseAll(copy, 3, 50);
    cout << copy[0] << " " << copy[1] << " " << copy[2] << endl;
    return 0;
}
```

---

## Solution 19

### Bug
When the target is missing, `findValue` returns the address of the local `notFound` variable. That local dies when the function returns, so dereferencing the returned pointer in `main` is undefined behavior — the expected -1 becomes garbage or a crash.

### Explanation
Returning the address of a local (stack) variable is always wrong: the housing memory is freed when the function exits. Here the "found" path is fine (it returns pointers into the caller's table), which keeps the first output 250 correct and isolates the fault to missing keys. The fix returns a plain value instead: found → the matching price, not found → -1. No pointer, no dangling access.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int findValue(int target, int table[], int size) {
    for (int i = 0; i < size; i++)
        if (table[i] == target)
            return table[i];
    return -1;
}

int main() {
    int prices[] = {100, 250, 400};
    cout << findValue(250, prices, 3) << endl;
    cout << findValue(999, prices, 3) << endl;
    return 0;
}
```

---

## Solution 20

### Bug
`makePair` returns a pointer to its local stack array. The array is destroyed when the function returns; the caller's pointer dangles, and reading it (after the `filler` array reuses the stack) gives garbage like `1 2` instead of `10 20`.

### Explanation
A local array "leaves scope" at every `return` statement — the returned address no longer owns the data. Using `new[]` keeps the ints alive in the heap until the caller deletes them, which is the standard owning behavior. Reading the returned pointer in the buggy code is undefined: a clean crash or silent garbage can result.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int *makePair() {
    int *pair = new int[2];
    pair[0] = 10;
    pair[1] = 20;
    return pair;
}

int main() {
    int *p = makePair();
    cout << p[0] << " " << p[1] << endl;
    delete[] p;
    return 0;
}
```

---

## Solution 21

### Bug
References cannot be "rebound" — `ref = b;` copies the value 20 into `a` instead of making `ref` an alias for `b`. The later `ref += 10` therefore raises `a` to 30, giving `30 20` instead of `5 30`.

### Explanation
A reference is an alias: once bound (`int &ref = a;`) it always refers to `a`. Assignment through it stores into `a`. To retarget which variable is modified, use a pointer (`int *ref = &b;`) and assign `*ref += 10;`. The first printed line (5) is correct in both versions, hiding the rebind mistake until the final output.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 5, b = 20;
    int *ref = &a;
    cout << *ref << endl;
    ref = &b;
    *ref += 10;
    cout << a << " " << b << endl;
    return 0;
}
```

---

## Solution 22

### Bug
`checkEquality` compares the pointers (`u == v`) instead of the values behind them (`*u == *v`). Two distinct variables holding the same value 7 are reported "different".

### Explanation
`u` and `v` are addresses. Comparing them checks whether both parameters point at the same object, not whether the values are equal. The "same variable twice" input passes (both addresses equal), which makes the bug seem input-dependent even though every two-variable case fails. Dereferencing before `==` compares the actual integers.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

void checkEquality(int *u, int *v) {
    if (*u == *v)
        cout << "equal" << endl;
    else
        cout << "different" << endl;
}

int main() {
    int a = 7, b = 7;
    checkEquality(&a, &b);
    checkEquality(&a, &a);
    return 0;
}
```

---

## Solution 23

### Bug
Two related defects: (1) the loop starts at index 1, skipping `scores[0]`, and (2) the NULL guard sits *after* the dereferencing loop, so a NULL `scores` crashes before the guard is ever reached. Output 10 → then 45 → then a crash, instead of 10 / 50 / -1.

### Explanation
Both bugs concern traversal safety. The index-1 start drops the first element (45 instead of 50 for `{5,10,15,20}`); the first test passes only because its first element is 0, which is exactly the sort of accident that hides bug (1). The misplaced guard also reveals why the order matters: dereferences must never precede the null test. Move the check to the top and iterate from index 0.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int chainSum(int *scores, int count) {
    if (scores == NULL)
        return -1;
    int total = 0;
    for (int i = 0; i < count; i++)
        total += scores[i];
    return total;
}

int main() {
    int listA[] = {0, 4, 6};
    cout << chainSum(listA, 3) << endl;
    int listB[] = {5, 10, 15, 20};
    cout << chainSum(listB, 4) << endl;
    int *nothing = NULL;
    cout << chainSum(nothing, 2) << endl;
    return 0;
}
```

---

## Solution 24

### Bug
`updateTotal` is declared with `int total` instead of `int &total`, so the caller's `running` is passed by value. Every update is lost; `running` remains 100 instead of becoming 160.

### Explanation
Missing the `&` silently turns a reference parameter into a by-value one: `total += amount;` adjusts a local copy. `running` is never modified, so both prints show 100. The sanity call with amount 0 is "correct" in both versions (no change expected), which obscures the defect. Adding `&` makes the function operate on the caller's variable.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

void updateTotal(int amount, int &total) {
    total += amount;
}

int main() {
    int running = 100;
    updateTotal(0, running);
    cout << running << endl;
    updateTotal(50, running);
    updateTotal(10, running);
    cout << running << endl;
    return 0;
}
```

---

## Solution 25

### Bug
`redirect` assigns `slot = &newTarget;` — writing into the *local copy* of the pointer-to-pointer. The caller's `current` is never updated, so `*current = 100` writes into `primary`, giving `100 60 100` instead of `90 100 100`.

### Explanation
`slot` is an `int**`; it receives a copy of the address of `current`. Reassigning `slot` only changes which two pointers this copy holds. To modify the caller's pointer you must dereference through the pointer-to-pointer: `*slot = newTarget;`. Only then does `current` point at `spare`, and the write `*current = 100` lands in `spare`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

void redirect(int **slot, int *newTarget) {
    *slot = newTarget;
}

int main() {
    int primary = 90, spare = 60;
    int *current = &primary;
    redirect(&current, &spare);
    *current = 100;
    cout << primary << " " << spare << " " << *current << endl;
    return 0;
}
```

---

## Solution 26

### Bug
The recursion steps by `n - 2` instead of `n - 1`, so `sumUp` visits only every other integer: 5 + 3 + 1 = 9 instead of 5 + 4 + 3 + 2 + 1 = 15 (and 4 + 2 = 6 instead of 10).

### Explanation
`sumUp(n - 2)` skips a whole level on every call. The trivial cases 0 and 1 still give 0 and 1 (correct), which is what lets the faulty stepping hide: the discrepancy only appears once `n >= 2`. Reverting to `n - 1` yields the contiguous sum. This style of off-by-stride bug is common when recursive counters are "reduced" aggressively.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int sumUp(int n) {
    if (n <= 0)
        return 0;
    return n + sumUp(n - 1);
}

int main() {
    cout << sumUp(0) << " " << sumUp(1) << endl;
    cout << sumUp(5) << endl;
    cout << sumUp(4) << endl;
    return 0;
}
```

---

## Solution 27

### Bug
`cleanup` deletes the same heap object twice (`delete p;` twice). The second delete is a double free — undefined behavior that typically aborts with a heap-corruption error, so "done" is never printed.

### Explanation
Memory ownership lesson: exactly one `new` must be matched by exactly one `delete`. Deleting the same pointer twice corrupts the heap bookkeeping even though the address still "looks like" a live pointer (shallow-copying pointers into helper functions is a classic cause). Free the object once; after a delete, the pointer is stale and must not be used or deleted again.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

void cleanup(int *p) {
    delete p;
}

int main() {
    int *score = new int(42);
    cout << *score << endl;
    cleanup(score);
    cout << "done" << endl;
    return 0;
}
```

---

## Solution 28

### Bug
The loop body always dereferences `cells[0]`, so `total` accumulates `*cells[0]` = 10 three times (30) instead of honoring the loop index: 10 + 20 + 30 = 60.

### Explanation
`total += *cells[0];` ignores `i` entirely. The pointer array must be visited with the running index — `*cells[i]` means "the int pointed to by the i-th pointer." When all three ints hold the same value (5, 5, 5) the wrong expression still adds up to the right total, a common masked-input trap. There is no out-of-bounds risk because the wrong element (0) is always a valid one — the error is purely a wrong result.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 10, b = 20, c = 30;
    int *cells[] = {&a, &b, &c};
    int total = 0;
    for (int i = 0; i < 3; i++)
        total += *cells[i];
    cout << total << endl;
    return 0;
}
```

---

## Solution 29

### Bug
The accumulation is written to the wrong target: `extra[i] += dest[i];` adds into `extra` instead of into `dest`. The caller expects `dest` to grow: `11 22 33 ...` rather than `... 11 22 33`.

### Explanation
The rule was "dest[i] = dest[i] + extra[i]", but the code reversed which array is the accumulator. Since neither array is const, the correction is a one-line swap of roles. The all-zero input `{0,0,0} + {0,0,0}` yields `0 0 0 0 0 0` in both versions — from now on, be suspicious of a zero-data test that passes: it can certify nothing.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

void mergeSum(int dest[], int extra[], int count) {
    for (int i = 0; i < count; i++)
        dest[i] += extra[i];
}

void show(int d[3], int e[3]) {
    for (int i = 0; i < 3; i++) cout << d[i] << " ";
    for (int i = 0; i < 3; i++) cout << e[i] << " ";
    cout << endl;
}

int main() {
    int d1[3] = {1, 2, 3}, e1[3] = {10, 20, 30};
    mergeSum(d1, e1, 3);
    show(d1, e1);

    int d2[3] = {0, 0, 0}, e2[3] = {0, 0, 0};
    mergeSum(d2, e2, 3);
    show(d2, e2);
    return 0;
}
```

---

## Solution 30

### Bug
Two related defects cooperate: (1) the function mutates the *cap* instead of the *value* — `*writableCap = *value;` overwrites the limit with 250, and (2) it got away with that only by casting away const (`(int *)cap`), violating the const contract on the parameter. The outcome is `250 250` instead of `100 100`.

### Explanation
`cap` is declared `const int *` to promise it is read-only; casting away const and writing through it is both a contract violation and the mechanism of the wrong-target bug. The fix needs neither: compare `*value` against `*cap` and clamp the value itself (`*value = *cap;`). The un-cast path also clears up the `value ≤ cap` input (50/100 → `50 100`), which works by accident in both versions.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

void trim(int *value, const int *cap) {
    if (*value > *cap)
        *value = *cap;
}

int main() {
    int val = 250;
    int limit = 100;
    trim(&val, &limit);
    cout << val << " " << limit << endl;
    return 0;
}
```

---