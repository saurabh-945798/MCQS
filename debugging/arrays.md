# C++ Debugging — Arrays

## Question 1

### Difficulty
Easy

### Bug Type
Wrong Maximum Initialization (fails on negatives)

### Problem
Given n integers, find the largest value in the array and print it. The array may contain negative numbers.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int maxVal = 0;
    for (int i = 0; i < n; i++)
        if (arr[i] > maxVal) maxVal = arr[i];

    cout << maxVal << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3
3 8 2
```
the expected output is:
```text
8
```

For:
```text
4
4 1 9 7
```
the expected output is:
```text
9
```

For:
```text
3
-4 -1 -9
```
the expected output is:
```text
-1
```

---

## Question 2

### Difficulty
Easy

### Bug Type
Wrong Minimum Initialization (fails on positives)

### Problem
Given n integers, find the smallest value in the array and print it. The array may contain negative numbers as well as positive numbers.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int minVal = 0;
    for (int i = 0; i < n; i++)
        if (arr[i] < minVal) minVal = arr[i];

    cout << minVal << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3
-3 -7 -1
```
the expected output is:
```text
-7
```

For:
```text
3
5 2 9
```
the expected output is:
```text
2
```

For:
```text
4
5 2 9 7
```
the expected output is:
```text
2
```

---

## Question 3

### Difficulty
Easy

### Bug Type
Sum Loop Boundary (`<=` instead of `<`)

### Problem
The first line contains n. The next line contains n+1 integers: the first n are data values and the final value is a separator that must be ignored. Print the sum of only the n data values.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i <= n; i++) cin >> arr[i];

    int sum = 0;
    for (int i = 0; i <= n; i++) sum += arr[i];

    cout << sum << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3
4 8 2 0
```
the expected output is:
```text
14
```

For:
```text
3
4 8 2 99
```
the expected output is:
```text
14
```

For:
```text
2
6 3 0
```
the expected output is:
```text
9
```

---

## Question 4

### Difficulty
Easy

### Bug Type
Reverse Print Missing First Element (`i > 0`)

### Problem
Given n integers, print the array reversed: the last element first and the first element last.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100], rev[100] = {};
    for (int i = 0; i < n; i++) cin >> arr[i];

    int k = 0;
    for (int i = n - 1; i > 0; i--) {
        rev[k] = arr[i];
        k++;
    }

    for (int i = 0; i < n; i++) cout << rev[i] << " ";
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
0 8 2 5
```
the expected output is:
```text
5 2 8 0
```

For:
```text
4
3 8 2 5
```
the expected output is:
```text
5 2 8 3
```

For:
```text
1
7
```
the expected output is:
```text
7
```

---

## Question 5

### Difficulty
Easy

### Bug Type
Wrong Starting Index (skips arr[0], starts at 1)

### Problem
Given n integers, print the sum of all of them, including the very first element.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int sum = 0;
    for (int i = 1; i < n; i++) sum += arr[i];

    cout << sum << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
0 4 8 2
```
the expected output is:
```text
14
```

For:
```text
4
5 4 8 2
```
the expected output is:
```text
19
```

For:
```text
1
6
```
the expected output is:
```text
6
```

---

## Question 6

### Difficulty
Easy

### Bug Type
Sum Skips Last Element (`i < n-1`)

### Problem
Given n integers, print the total sum of the whole array, including the last element.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int sum = 0;
    for (int i = 0; i < n - 1; i++) sum += arr[i];

    cout << sum << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
4 8 2 0
```
the expected output is:
```text
14
```

For:
```text
4
4 8 2 5
```
the expected output is:
```text
19
```

For:
```text
1
7
```
the expected output is:
```text
7
```

---

## Question 7

### Difficulty
Easy

### Bug Type
Integer Division Average (truncation)

### Problem
Given n integers, print their average as a real number, keeping the fractional part.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    int sum = 0;
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
        sum += arr[i];
    }

    int avg = sum / n;
    cout << avg << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
4 8 2 6
```
the expected output is:
```text
5
```

For:
```text
3
4 9 1
```
the expected output is:
```text
4.66667
```

For:
```text
2
5 8
```
the expected output is:
```text
6.5
```

---

## Question 8

### Difficulty
Easy

### Bug Type
Index Compared Instead of Value (i == target)

### Problem
Given n integers followed by a target integer, print "Found" if the target value appears in the array, otherwise print "Not Found".

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, target;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];
    cin >> target;

    bool found = false;
    for (int i = 0; i < n; i++)
        if (i == target) found = true;

    cout << (found ? "Found" : "Not Found") << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
0 1 2 3
2
```
the expected output is:
```text
Found
```

For:
```text
4
5 1 9 8
2
```
the expected output is:
```text
Not Found
```

For:
```text
5
10 20 30 40 50
1
```
the expected output is:
```text
Not Found
```

---

## Question 9

### Difficulty
Easy

### Bug Type
Double-Swap Reverse Restores Array (full sweep)

### Problem
Given n integers, reverse the array in place so that the first element and the last element swap, the second and the second-last swap, and so on. Then print the reversed array.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    for (int i = 0; i < n; i++) {
        int tmp = arr[i];
        arr[i] = arr[n - 1 - i];
        arr[n - 1 - i] = tmp;
    }

    for (int i = 0; i < n; i++) cout << arr[i] << " ";
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
1 2 3 4
```
the expected output is:
```text
4 3 2 1
```

For:
```text
4
1 2 2 1
```
the expected output is:
```text
1 2 2 1
```

For:
```text
3
7 8 9
```
the expected output is:
```text
9 8 7
```

---

## Question 10

### Difficulty
Easy

### Bug Type
Linear Search Misses Last Element

### Problem
Given n integers followed by a target integer, print the index of the first occurrence of the target, or -1 if the target is not present. The target may be anywhere, including the last position.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, target;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];
    cin >> target;

    int pos = -1;
    for (int i = 0; i < n - 1; i++)
        if (arr[i] == target) {
            pos = i;
            break;
        }

    cout << pos << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3
5 9 3
9
```
the expected output is:
```text
1
```

For:
```text
3
5 9 3
3
```
the expected output is:
```text
2
```

For:
```text
1
7
7
```
the expected output is:
```text
0
```

---

## Question 11

### Difficulty
Easy

### Bug Type
Wrong Variable in Max Comparison

### Problem
Given n integers, find and print the largest value in the array.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int maxVal = arr[0];
    for (int i = 1; i < n; i++)
        if (arr[i] > arr[0]) maxVal = arr[i];

    cout << maxVal << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3
3 8 2
```
the expected output is:
```text
8
```

For:
```text
4
5 4 9 6
```
the expected output is:
```text
9
```

For:
```text
3
7 10 9
```
the expected output is:
```text
10
```

---

## Question 12

### Difficulty
Easy

### Bug Type
Frequency Count Wrong Update

### Problem
Given n integers followed by a target integer, count how many times the target appears in the array and print the count.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, target;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];
    cin >> target;

    int count = 0;
    for (int i = 0; i < n; i++)
        if (arr[i] == target) count = i;

    cout << count << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3
5 8 2
8
```
the expected output is:
```text
1
```

For:
```text
3
8 5 2
8
```
the expected output is:
```text
1
```

For:
```text
3
8 8 8
8
```
the expected output is:
```text
3
```

---

## Question 13

### Difficulty
Easy

### Bug Type
Count Evens Boundary Error

### Problem
Given n integers, count how many of them are even and print the count. Every element, including the last one, must be examined.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int count = 0;
    for (int i = 0; i < n - 1; i++)
        if (arr[i] % 2 == 0) count++;

    cout << count << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3
4 6 3
```
the expected output is:
```text
2
```

For:
```text
4
4 6 3 8
```
the expected output is:
```text
3
```

For:
```text
2
1 2
```
the expected output is:
```text
1
```

---

## Question 14

### Difficulty
Easy

### Bug Type
Array Print Boundary (`i <= n`)

### Problem
Given n integers, print exactly those n integers, separated by single spaces, on one line. No extra number may appear in the output.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100] = {};
    for (int i = 0; i < n; i++) cin >> arr[i];

    for (int i = 0; i <= n; i++)
        cout << arr[i] << (i < n ? " " : "");
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
3 8 2
```
the expected output is:
```text
3 8 2
```

For:
```text
4
5 1 6 0
```
the expected output is:
```text
5 1 6 0
```

For:
```text
2
10 20
```
the expected output is:
```text
10 20
```

---

## Question 15

### Difficulty
Easy

### Bug Type
Product of Elements Initialized to 0

### Problem
Given n integers, print the product of all of them. When one of the values is zero the product is zero, otherwise multiply every element.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int prod = 0;
    for (int i = 0; i < n; i++) prod *= arr[i];

    cout << prod << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
1 2 0 5
```
the expected output is:
```text
0
```

For:
```text
3
2 3 4
```
the expected output is:
```text
24
```

For:
```text
3
3 4 5
```
the expected output is:
```text
60
```

---

## Question 16

### Difficulty
Medium

### Bug Type
Second Largest Wrong Initialization

### Problem
Given at least two integers, print the second largest value in the array. For example, for `arr = {7, 9, 6}` the second largest is 7.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int largest = arr[0];
    int second = arr[0];
    for (int i = 1; i < n; i++) {
        if (arr[i] > largest) {
            second = largest;
            largest = arr[i];
        }
    }

    cout << second << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3
7 9 6
```
the expected output is:
```text
7
```

For:
```text
3
8 3 5
```
the expected output is:
```text
5
```

For:
```text
4
9 4 6 7
```
the expected output is:
```text
7
```

---

## Question 17

### Difficulty
Medium

### Bug Type
Left Rotation Overwrites First Element

### Problem
Given n integers, rotate the array left by one position: every element moves one slot to the left and the first element wraps around to the last position. Then print the array.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    for (int i = 0; i < n - 1; i++)
        arr[i] = arr[i + 1];

    for (int i = 0; i < n; i++) cout << arr[i] << " ";
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
1 2 3 1
```
the expected output is:
```text
2 3 1 1
```

For:
```text
4
1 2 3 4
```
the expected output is:
```text
2 3 4 1
```

For:
```text
3
7 1 2
```
the expected output is:
```text
1 2 7
```

---

## Question 18

### Difficulty
Medium

### Bug Type
Remove Duplicates Wrong Shift

### Problem
Given n integers followed by a target value, remove every occurrence of the target from the array by shifting the remaining elements left, then print the array without the target. Consecutive occurrences must all be removed.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, target;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];
    cin >> target;

    for (int i = 0; i < n; i++) {
        if (arr[i] == target) {
            for (int j = i; j < n - 1; j++)
                arr[j] = arr[j + 1];
            n--;
        }
    }

    for (int i = 0; i < n; i++) cout << arr[i] << " ";
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
4 8 4 2
4
```
the expected output is:
```text
8 2
```

For:
```text
3
4 4 8
4
```
the expected output is:
```text
8
```

For:
```text
4
4 8 4 4
4
```
the expected output is:
```text
8
```

---

## Question 19

### Difficulty
Medium

### Bug Type
2D Row Sum Wrong Inner Boundary

### Problem
Given a matrix with r rows and c columns, print the sum of each row. The matrix may be rectangular, so the number of rows and the number of columns can differ.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int r, c;
    cin >> r >> c;
    int mat[10][10];
    for (int i = 0; i < r; i++)
        for (int j = 0; j < c; j++) cin >> mat[i][j];

    for (int i = 0; i < r; i++) {
        int s = 0;
        for (int j = 0; j < r; j++)
            s += mat[i][j];
        cout << "Row " << i << ": " << s << endl;
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
2 2
1 2
3 4
```
the expected output is:
```text
Row 0: 3
Row 1: 7
```

For:
```text
2 3
1 2 3
4 5 6
```
the expected output is:
```text
Row 0: 6
Row 1: 15
```

For:
```text
2 3
1 0 2
3 4 5
```
the expected output is:
```text
Row 0: 3
Row 1: 12
```

---

## Question 20

### Difficulty
Medium

### Bug Type
2D Diagonal Sum Wrong Condition

### Problem
Given a square matrix of size n, print the sum of the elements on the main diagonal (top-left to bottom-right).

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int mat[10][10];
    for (int i = 0; i < n; i++)
        for (int j = 0; j < n; j++) cin >> mat[i][j];

    int s = 0;
    for (int i = 0; i < n; i++)
        for (int j = 0; j < n; j++)
            if (i + j == n - 1) s += mat[i][j];

    cout << s << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3
1 1 1
1 1 1
1 1 1
```
the expected output is:
```text
3
```

For:
```text
3
1 2 3
4 5 6
7 8 1
```
the expected output is:
```text
7
```

For:
```text
2
2 7
4 5
```
the expected output is:
```text
7
```

---

## Question 21

### Difficulty
Medium

### Bug Type
Transpose Swaps Twice

### Problem
Given a square matrix of size n, transpose it in place (mirror across the main diagonal) and print the resulting matrix row by row.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int mat[10][10];
    for (int i = 0; i < n; i++)
        for (int j = 0; j < n; j++) cin >> mat[i][j];

    for (int i = 0; i < n; i++)
        for (int j = 0; j < n; j++)
            if (i != j) {
                int t = mat[i][j];
                mat[i][j] = mat[j][i];
                mat[j][i] = t;
            }

    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) cout << mat[i][j] << " ";
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
2
1 2
2 1
```
the expected output is:
```text
1 2
2 1
```

For:
```text
2
1 2
3 4
```
the expected output is:
```text
1 3
2 4
```

For:
```text
3
1 2 3
4 5 6
7 8 9
```
the expected output is:
```text
1 4 7
2 5 8
3 6 9
```

---

## Question 22

### Difficulty
Medium

### Bug Type
Column Traversal Wrong Indexing

### Problem
Given a matrix with r rows and c columns, print all its values in row-major order (row by row, left to right). The matrix may be rectangular.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int r, c;
    cin >> r >> c;
    int mat[10][10];
    for (int i = 0; i < r; i++)
        for (int j = 0; j < c; j++) cin >> mat[i][j];

    for (int j = 0; j < c; j++)
        for (int i = 0; i < r; i++)
            cout << mat[i][j] << " ";
    cout << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
2 2
1 2
3 4
```
the expected output is:
```text
1 2 3 4
```

For:
```text
2 3
1 2 3
4 5 6
```
the expected output is:
```text
1 2 3 4 5 6
```

For:
```text
3 2
1 2
3 4
5 6
```
the expected output is:
```text
1 2 3 4 5 6
```

---

## Question 23

### Difficulty
Medium

### Bug Type
k-Rotation Index Arithmetic Off-by-One

### Problem
Given n integers and an integer k, print the array rotated to the right by k positions. Each element moves forward k slots and wraps around.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, k;
    cin >> n;
    int a[100];
    for (int i = 0; i < n; i++) cin >> a[i];
    cin >> k;

    int b[100];
    for (int i = 0; i < n; i++)
        b[(i + k - 1) % n] = a[i];

    for (int i = 0; i < n; i++) cout << b[i] << " ";
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
5 5 5
1
```
the expected output is:
```text
5 5 5
```

For:
```text
4
1 2 3 4
2
```
the expected output is:
```text
3 4 1 2
```

For:
```text
4
1 2 3 4
1
```
the expected output is:
```text
4 1 2 3
```

---

## Question 24

### Difficulty
Medium

### Bug Type
Prefix Sum Wrong Accumulator

### Problem
Given n integers, print the running (prefix) sums: after the first element, after the first two, and so on.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int sum = 0;
    for (int i = 0; i < n; i++) {
        sum += arr[i];
        cout << arr[i] << " ";
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
1
7
```
the expected output is:
```text
7
```

For:
```text
4
1 2 3 4
```
the expected output is:
```text
1 3 6 10
```

For:
```text
3
5 1 2
```
the expected output is:
```text
5 6 8
```

---

## Question 25

### Difficulty
Medium

### Bug Type
Two-Pointer Reverse Wrong Update

### Problem
Given n integers, reverse the array in place using two moving pointers (one from the front, one from the back) and print the result.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int i = 0, j = n - 1;
    while (i < j) {
        int t = arr[i];
        arr[i] = arr[j];
        arr[j] = t;
        i++;
    }

    for (int i = 0; i < n; i++) cout << arr[i] << " ";
    cout << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
2
1 2
```
the expected output is:
```text
2 1
```

For:
```text
3
1 2 3
```
the expected output is:
```text
3 2 1
```

For:
```text
5
1 2 3 4 5
```
the expected output is:
```text
5 4 3 2 1
```

---

## Question 26

### Difficulty
Medium

### Bug Type
Subarray Sum Runs Out of Bounds

### Problem
Given n integers followed by a target integer, print "Found" if some non-empty contiguous subarray (any length from 1 to n) sums to the target, otherwise print "Not Found".

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, target;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];
    cin >> target;

    bool found = false;
    for (int i = 0; i < n && !found; i++) {
        int sum = arr[i];
        for (int j = i + 1; j < n; j++) {
            sum += arr[j];
            if (sum == target) found = true;
        }
    }

    cout << (found ? "Found" : "Not Found") << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
1 4 2 8
5
```
the expected output is:
```text
Found
```

For:
```text
3
5 2 3
5
```
the expected output is:
```text
Found
```

For:
```text
3
5 2 3
2
```
the expected output is:
```text
Found
```

---

## Question 27

### Difficulty
Medium

### Bug Type
Count Above Average Uses Integer Division

### Problem
Given n integers, count how many of them are strictly greater than the array's true (real-valued) average and print the count.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    int sum = 0;
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
        sum += arr[i];
    }

    int avg = sum / n;
    int count = 0;
    for (int i = 0; i < n; i++)
        if (arr[i] > avg) count++;

    cout << count << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
4 8 2 6
```
the expected output is:
```text
2
```

For:
```text
4
4 9 5 1
```
the expected output is:
```text
1
```

For:
```text
3
10 10 4
```
the expected output is:
```text
0
```

---

## Question 28

### Difficulty
Medium

### Bug Type
Kadane's Algorithm Wrong Initialization

### Problem
Given n integers, find the maximum sum that can be obtained from a contiguous subarray and print it. The array may contain only negative numbers.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int sum = 0, best = 0;
    for (int i = 0; i < n; i++) {
        sum += arr[i];
        if (sum > best) best = sum;
        if (sum < 0) sum = 0;
    }

    cout << best << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
2 -1 3 -2
```
the expected output is:
```text
4
```

For:
```text
3
-5 -1 -8
```
the expected output is:
```text
-1
```

For:
```text
3
5 -2 4
```
the expected output is:
```text
7
```

---

## Question 29

### Difficulty
Medium

### Bug Type
Majority Element Count Reset

### Problem
Given n integers, print the value of any element that appears more than n/2 times (the majority element), or print "None" if no such element exists.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int count = 0;
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++)
            if (arr[j] == arr[i]) count++;
        if (count > n / 2) {
            cout << arr[i] << endl;
            return 0;
        }
    }
    cout << "None" << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3
2 2 2
```
the expected output is:
```text
2
```

For:
```text
3
2 3 4
```
the expected output is:
```text
None
```

For:
```text
5
3 3 4 3 3
```
the expected output is:
```text
3
```

---

## Question 30

### Difficulty
Medium

### Bug Type
Most Frequent Element Wrong Compare

### Problem
Given n integers, find and print the element that occurs most frequently. If several values tie, any of them is acceptable.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int best = arr[0], maxCount = 0;
    for (int i = 0; i < n; i++) {
        int count = 0;
        for (int j = 0; j < n; j++)
            if (arr[j] == arr[i]) count++;
        if (count < maxCount) {
            maxCount = count;
            best = arr[i];
        }
    }

    cout << best << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
3 1 3 2
```
the expected output is:
```text
3
```

For:
```text
5
2 3 1 3 1
```
the expected output is:
```text
3
```

For:
```text
4
7 7 7 7
```
the expected output is:
```text
7
```

---

## Question 31

### Difficulty
Medium

### Bug Type
Pair-Sum Count Boundary

### Problem
Given n integers followed by a target integer, count how many pairs of different positions (i, j) with i < j have a sum equal to the target. Print the count.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, target;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];
    cin >> target;

    int pairs = 0;
    for (int i = 0; i < n; i++)
        for (int j = 0; j < n; j++)
            if (i != j && arr[i] + arr[j] == target) pairs++;

    cout << pairs << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3
1 2 3
10
```
the expected output is:
```text
0
```

For:
```text
3
1 2 3
3
```
the expected output is:
```text
1
```

For:
```text
4
1 3 2 2
4
```
the expected output is:
```text
2
```

---

## Question 32

### Difficulty
Medium

### Bug Type
Absolute Values Wrong Sum

### Problem
Given n integers, print the sum of their absolute values (all values are taken as positive magnitudes).

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int sum = 0;
    for (int i = 0; i < n; i++) sum += arr[i];

    cout << sum << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3
2 5 3
```
the expected output is:
```text
10
```

For:
```text
3
-2 5 -3
```
the expected output is:
```text
10
```

For:
```text
4
-1 -2 -3 -4
```
the expected output is:
```text
10
```

---

## Question 33

### Difficulty
Medium

### Bug Type
Wrong Product Update (accidental += vs *=)

### Problem
Given n integers, print the product of all of them.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int prod = 1;
    for (int i = 0; i < n; i++) prod += arr[i];

    cout << prod << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
1
7
```
the expected output is:
```text
7
```

For:
```text
3
2 3 4
```
the expected output is:
```text
24
```

For:
```text
2
2 2
```
the expected output is:
```text
4
```

---

## Question 34

### Difficulty
Medium

### Bug Type
Array Size m vs n Confusion

### Problem
Given two arrays A of size n and B of size m, print "Yes" if any element of A equals any element of B, otherwise print "No". Every element of A must be checked.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, m;
    cin >> n;
    int a[100];
    for (int i = 0; i < n; i++) cin >> a[i];
    cin >> m;
    int b[100];
    for (int i = 0; i < m; i++) cin >> b[i];

    for (int i = 0; i < m; i++)
        for (int j = 0; j < m; j++)
            if (a[i] == b[j]) {
                cout << "Yes" << endl;
                return 0;
            }
    cout << "No" << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
2
7 8
2
8 9
```
the expected output is:
```text
Yes
```

For:
```text
4
5 6 7 8
2
9 8
```
the expected output is:
```text
Yes
```

For:
```text
3
1 2 3
3
4 5 6
```
the expected output is:
```text
No
```

---

## Question 35

### Difficulty
Medium

### Bug Type
Merge Two Arrays Wrong Write Index

### Problem
Given array A of size n followed by array B of size m, merge them into one array that holds all of A and then all of B, and print the merged result.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, m;
    cin >> n;
    int a[100];
    for (int i = 0; i < n; i++) cin >> a[i];
    cin >> m;
    int b[100];
    for (int i = 0; i < m; i++) cin >> b[i];

    int c[200];
    int k = 0;
    for (int i = 0; i < n; i++) {
        c[k] = a[i];
        k++;
    }
    for (int i = 0; i < m; i++) c[k] = b[i];

    for (int i = 0; i < n + m; i++) cout << c[i] << " ";
    cout << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
2
1 2
1
9
```
the expected output is:
```text
1 2 9
```

For:
```text
2
1 2
3
8 9 7
```
the expected output is:
```text
1 2 8 9 7
```

For:
```text
3
5 5 5
2
6 7
```
the expected output is:
```text
5 5 5 6 7
```

---

## Question 36

### Difficulty
Hard

### Bug Type
Two Related Bugs (index + initialization)

### Problem
Given n integers, print the index of the last occurrence of the largest value in the array. The array may contain only negative numbers.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int maxVal = 0;
    int maxIdx = -1;
    for (int i = 0; i < n; i++)
        if (arr[i] > maxVal) {
            maxVal = arr[i];
            maxIdx++;
        }

    cout << maxIdx << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3
1 2 3
```
the expected output is:
```text
2
```

For:
```text
3
2 1 3
```
the expected output is:
```text
2
```

For:
```text
3
-5 -2 -7
```
the expected output is:
```text
1
```

---

## Question 37

### Difficulty
Hard

### Bug Type
All-Equal Array Edge (max/min duplicates)

### Problem
Given n integers, print the index of the first element that is strictly greater than the first element of the array, or -1 if no such element exists. Values equal to the first element must not be reported.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int pos = -1;
    for (int i = 1; i < n; i++)
        if (arr[i] >= arr[0]) {
            pos = i;
            break;
        }

    cout << pos << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3
3 2 5
```
the expected output is:
```text
2
```

For:
```text
3
5 5 5
```
the expected output is:
```text
-1
```

For:
```text
3
3 3 1
```
the expected output is:
```text
-1
```

---

## Question 38

### Difficulty
Hard

### Bug Type
Negative-Heavy Array Maximum

### Problem
Given n integers, print the element whose magnitude (absolute value) is the largest. In other words, find the value furthest from zero and print that signed value.

### Buggy Code

```cpp
#include <iostream>
#include <cstdlib>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int peak = arr[0];
    for (int i = 1; i < n; i++)
        if (abs(arr[i]) > peak) peak = arr[i];

    cout << peak << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3
-5 -2 -9
```
the expected output is:
```text
-9
```

For:
```text
4
-10 3 -4 8
```
the expected output is:
```text
-10
```

For:
```text
3
5 -8 3
```
the expected output is:
```text
-8
```

---

## Question 39

### Difficulty
Hard

### Bug Type
Single-Element / Empty Array Handling

### Problem
Given n integers, print the largest value in the array. If n is 0 the program should print 0. Every element, including a lone element or an element at an odd position, must be examined.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int maxVal = 0;
    for (int i = 0; i + 1 < n; i += 2) {
        if (arr[i] > maxVal) maxVal = arr[i];
        if (arr[i + 1] > maxVal) maxVal = arr[i + 1];
    }

    cout << maxVal << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
3 8 2 5
```
the expected output is:
```text
8
```

For:
```text
1
7
```
the expected output is:
```text
7
```

For:
```text
3
1 2 9
```
the expected output is:
```text
9
```

---

## Question 40

### Difficulty
Hard

### Bug Type
k-Rotation With Negative or Oversized k

### Problem
Given n integers and an integer k, rotate the array to the right by k positions. If k is negative, rotate to the left by |k| positions. Values of k larger than n are treated modulo n.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, k;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];
    cin >> k;

    k %= n;
    if (k < 0) k = -k;

    for (int r = 0; r < k; r++) {
        int last = arr[n - 1];
        for (int i = n - 1; i > 0; i--) arr[i] = arr[i - 1];
        arr[0] = last;
    }

    for (int i = 0; i < n; i++) cout << arr[i] << " ";
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
1 2 3 4
0
```
the expected output is:
```text
1 2 3 4
```

For:
```text
4
1 2 3 4
6
```
the expected output is:
```text
3 4 1 2
```

For:
```text
4
1 2 3 4
-1
```
the expected output is:
```text
2 3 4 1
```

---

## Question 41

### Difficulty
Hard

### Bug Type
Subarray Comparison Boundary

### Problem
Given array A of n integers and array B of m integers, print "Equal" if B is a prefix of A (that is, the first m values of A equal B), otherwise print "Different". The comparison must only cover the first min(n, m) positions.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int a[100] = {};
    int b[100] = {};
    int n, m;
    cin >> n;
    for (int i = 0; i < n; i++) cin >> a[i];
    cin >> m;
    for (int i = 0; i < m; i++) cin >> b[i];

    bool ok = true;
    for (int i = 0; i < m; i++)
        if (a[i] != b[i]) ok = false;

    cout << (ok ? "Equal" : "Different") << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
5
1 2 3 9 9
3
1 2 3
```
the expected output is:
```text
Equal
```

For:
```text
3
1 2 3
5
1 2 3 4 4
```
the expected output is:
```text
Equal
```

For:
```text
3
1 2 3
3
1 0 3
```
the expected output is:
```text
Different
```

---

## Question 42

### Difficulty
Hard

### Bug Type
Sliding-Window Sum / Average Boundary

### Problem
Given n integers and a window size k, compute the sum of every contiguous window of exactly k elements and print the largest window sum. Windows start at every index from 0 up to and including n-k.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, k;
    cin >> n >> k;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int best = 0;
    for (int i = 0; i < n - k; i++) {
        int sum = 0;
        for (int j = i; j < i + k; j++) sum += arr[j];
        if (sum > best) best = sum;
    }

    cout << best << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
5 2
10 1 1 1 0
```
the expected output is:
```text
11
```

For:
```text
5 2
1 1 1 9 9
```
the expected output is:
```text
18
```

For:
```text
4 3
1 2 3 4
```
the expected output is:
```text
9
```

---

## Question 43

### Difficulty
Hard

### Bug Type
Reverse a Range of Indices Wrong Bounds

### Problem
Given n integers, reverse the entire array from index 0 to index n-1 (swap first with last, and so on) using a helper function, then print the result.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

void rev(int a[], int l, int r) {
    while (l < r) {
        int t = a[l];
        a[l] = a[r];
        a[r] = t;
        l++;
        r--;
    }
}

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    rev(arr, 0, n - 2);

    for (int i = 0; i < n; i++) cout << arr[i] << " ";
    cout << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
1
7
```
the expected output is:
```text
7
```

For:
```text
4
1 2 3 4
```
the expected output is:
```text
4 3 2 1
```

For:
```text
5
1 2 3 4 5
```
the expected output is:
```text
5 4 3 2 1
```

---

## Question 44

### Difficulty
Hard

### Bug Type
Duplicate-Count Nested Loop Boundary

### Problem
Given n integers, count the number of pairs (i, j) with i < j such that the values at those two positions are equal, and print the count.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int count = 0;
    for (int i = 0; i < n; i++)
        for (int j = i; j < n; j++)
            if (arr[i] == arr[j]) count++;

    cout << count << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3
1 2 3
```
the expected output is:
```text
0
```

For:
```text
3
1 1 2
```
the expected output is:
```text
1
```

For:
```text
3
5 5 5
```
the expected output is:
```text
3
```

---

## Question 45

### Difficulty
Hard

### Bug Type
Backwards Merge of Two Sorted Arrays

### Problem
Given two arrays that are each sorted in ascending order, merge them into one ascending array that contains all elements of both, and print it. The merge is implemented by filling the result from the back.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, m;
    cin >> n;
    int a[100];
    for (int i = 0; i < n; i++) cin >> a[i];
    cin >> m;
    int b[100];
    for (int i = 0; i < m; i++) cin >> b[i];

    int res[200] = {};
    int i = n - 1, j = m - 1, k = n + m;
    while (i >= 0 && j >= 0) {
        if (a[i] < b[j]) res[--k] = a[i--];
        else res[--k] = b[j--];
    }
    while (i >= 0) res[--k] = a[i--];
    while (j >= 0) res[--k] = b[j--];

    for (int i = 0; i < n + m; i++) cout << res[i] << " ";
    cout << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
1
7
1
7
```
the expected output is:
```text
7 7
```

For:
```text
2
1 300
2
100 200
```
the expected output is:
```text
1 100 200 300
```

For:
```text
3
1 3 5
3
2 4 6
```
the expected output is:
```text
1 2 3 4 5 6
```

---

## Question 46

### Difficulty
Hard

### Bug Type
Longest Increasing Run Boundary

### Problem
Given n integers, find the length of the longest run of consecutive elements that are strictly increasing, and print it. The longest run may end at the very last element.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int cur = 1, best = 1;
    for (int i = 1; i < n; i++) {
        if (arr[i] > arr[i - 1]) cur++;
        else {
            if (cur > best) best = cur;
            cur = 1;
        }
    }

    cout << best << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
6
1 2 3 1 0 5
```
the expected output is:
```text
3
```

For:
```text
3
4 5 6
```
the expected output is:
```text
3
```

For:
```text
4
3 1 2 4
```
the expected output is:
```text
3
```

---

## Question 47

### Difficulty
Hard

### Bug Type
Missing Number in 1..n Formula Bug

### Problem
You are given the integers 1 to n with exactly one value missing. After n, the input lists the remaining n-1 numbers in any order. Print the missing value.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int sum = 0;
    for (int i = 0; i < n - 1; i++) {
        int x;
        cin >> x;
        sum += x;
    }

    int total = (n / 2) * (n + 1);
    cout << total - sum << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
1 2 4
```
the expected output is:
```text
3
```

For:
```text
5
1 2 4 5
```
the expected output is:
```text
3
```

For:
```text
3
1 3
```
the expected output is:
```text
2
```

---

## Question 48

### Difficulty
Hard

### Bug Type
Insert Position Boundary

### Problem
Given n integers, then a position p (0 <= p <= n) and a value x, insert x at position p of the array (shifting later elements right) and print all n+1 values.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100] = {};
    for (int i = 0; i < n; i++) cin >> arr[i];

    int p, x;
    cin >> p >> x;

    for (int i = n - 1; i > p; i--)
        arr[i + 1] = arr[i];
    arr[p] = x;

    for (int i = 0; i <= n; i++) cout << arr[i] << " ";
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
10 20 30
3 99
```
the expected output is:
```text
10 20 30 99
```

For:
```text
4
10 20 30 40
2 99
```
the expected output is:
```text
10 20 99 30 40
```

For:
```text
3
5 6 7
1 8
```
the expected output is:
```text
5 8 6 7
```

---

## Question 49

### Difficulty
Hard

### Bug Type
Rotated Array Traversal Off-by-One

### Problem
Given a sorted array that was rotated at some pivot (so it now consists of two increasing segments), print the index of the smallest element, which is the index where the second segment begins. A non-rotated array is a special case where that index is 0.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int pivot = 0;
    for (int i = 0; i < n - 1; i++)
        if (arr[i] > arr[i + 1]) pivot = i;

    cout << pivot << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
1 2 3 4
```
the expected output is:
```text
0
```

For:
```text
5
3 4 0 1 2
```
the expected output is:
```text
2
```

For:
```text
4
4 1 2 3
```
the expected output is:
```text
1
```

---

## Question 50

### Difficulty
Hard

### Bug Type
Circular Array Indexing Bug

### Problem
Given n integers, a start index s and a step k, walk around the array in a circle: print the element at s, then advance by k positions (mod n), and repeat until n elements are printed.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, s, k;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];
    cin >> s >> k;

    int idx = s;
    for (int c = 0; c < n; c++) {
        cout << arr[idx] << " ";
        idx = (idx + k + 1) % n;
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
7 7 7 7
1 2
```
the expected output is:
```text
7 7 7 7
```

For:
```text
4
1 2 3 4
0 1
```
the expected output is:
```text
1 2 3 4
```

For:
```text
5
1 2 3 4 5
1 2
```
the expected output is:
```text
2 4 1 3 5
```

---

# Solutions

## Solution 1

### Bug
The maximum is initialized to `0` instead of to the first array element.

### Explanation
The loop only raises `maxVal` when a bigger element is found. When every element is negative, no update ever happens and the program prints `0`. For `arr = {-4, -1, -9}` the expected answer is `-1` but the buggy program prints `0`. Initialize `maxVal = arr[0]` and start the loop at index `1`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int maxVal = arr[0];
    for (int i = 1; i < n; i++)
        if (arr[i] > maxVal) maxVal = arr[i];

    cout << maxVal << endl;
    return 0;
}
```

---

## Solution 2

### Bug
The minimum is initialized to `0` instead of to the first array element.

### Explanation
The loop only lowers `minVal` when a smaller element is found. For a positive-only array nothing is ever smaller than `0`, so the program prints `0`. For `arr = {5, 2, 9}` the expected answer is `2` but the buggy program prints `0`. Initialize `minVal = arr[0]` and start the loop at index `1`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int minVal = arr[0];
    for (int i = 1; i < n; i++)
        if (arr[i] < minVal) minVal = arr[i];

    cout << minVal << endl;
    return 0;
}
```

---

## Solution 3

### Bug
The summing loop runs `for (int i = 0; i <= n; i++)` and therefore also adds the separator value stored at index `n`.

### Explanation
The input deliberately contains one extra terminating value, so the storage is safe (indices `0..n` exist). The summing loop must stop one slot earlier. With `arr = {4, 8, 2, 99}` and `n = 3` the expected sum is `14`, but the buggy loop computes `4 + 8 + 2 + 99 = 113`. Change the second loop to `i < n`; the reading loop keeps `i <= n` so the separator is still consumed.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i <= n; i++) cin >> arr[i];

    int sum = 0;
    for (int i = 0; i < n; i++) sum += arr[i];

    cout << sum << endl;
    return 0;
}
```

---

## Solution 4

### Bug
The reverse-copy loop uses `i > 0`, so the element at index `0` is never copied and `rev[n-1]` stays at its initial value `0`.

### Explanation
Because `rev` is zero-initialized, the gap is filled with a `0`. For `arr = {3, 8, 2, 5}` the expected output `5 2 8 3` becomes `5 2 8 0`. The loop must also include index `0`, so use `for (int i = n - 1; i >= 0; i--)`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100], rev[100] = {};
    for (int i = 0; i < n; i++) cin >> arr[i];

    int k = 0;
    for (int i = n - 1; i >= 0; i--) {
        rev[k] = arr[i];
        k++;
    }

    for (int i = 0; i < n; i++) cout << rev[i] << " ";
    cout << endl;
    return 0;
}
```

---

## Solution 5

### Bug
The summing loop starts at index `1`, silently skipping `arr[0]`.

### Explanation
For `arr = {5, 4, 8, 2}` the expected sum is `19`, but the buggy loop adds only `4 + 8 + 2 = 14`. Start the loop at index `0`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int sum = 0;
    for (int i = 0; i < n; i++) sum += arr[i];

    cout << sum << endl;
    return 0;
}
```

---

## Solution 6

### Bug
The summing loop uses `i < n - 1`, so the last element is never added.

### Explanation
For `arr = {4, 8, 2, 5}` the expected sum is `19`, but the buggy loop adds only `4 + 8 + 2 = 14`. Change the condition to `i < n`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int sum = 0;
    for (int i = 0; i < n; i++) sum += arr[i];

    cout << sum << endl;
    return 0;
}
```

---

## Solution 7

### Bug
The average is computed with integer division, `int avg = sum / n`, which truncates the fractional part.

### Explanation
For `arr = {4, 9, 1}` the true average of `14 / 3` is `4.66667`, but the buggy program prints `4`. Convert to a floating-point division: `double avg = (double)sum / n;`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    int sum = 0;
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
        sum += arr[i];
    }

    double avg = (double)sum / n;
    cout << avg << endl;
    return 0;
}
```

---

## Solution 8

### Bug
The search compares the loop index with the target (`i == target`) instead of comparing the array value with the target (`arr[i] == target`).

### Explanation
The loop reports "Found" simply because an index equals the target value, not because the value exists. For `arr = {5, 1, 9, 8}` with `target = 2` the expected answer is `Not Found`, but the buggy program prints `Found` (index 2 exists). Compare `arr[i]` instead.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, target;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];
    cin >> target;

    bool found = false;
    for (int i = 0; i < n; i++)
        if (arr[i] == target) found = true;

    cout << (found ? "Found" : "Not Found") << endl;
    return 0;
}
```

---

## Solution 9

### Bug
The swapping loop runs over the whole array (`i < n`), so each pair `(i, n-1-i)` is swapped twice and the array is restored to its original order.

### Explanation
When `i` reaches the second half it re-swaps the same pairs. For `arr = {1, 2, 3, 4}` the expected output `4 3 2 1` comes out as `1 2 3 4`. Limit the loop to half the array: `i < n / 2`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    for (int i = 0; i < n / 2; i++) {
        int tmp = arr[i];
        arr[i] = arr[n - 1 - i];
        arr[n - 1 - i] = tmp;
    }

    for (int i = 0; i < n; i++) cout << arr[i] << " ";
    cout << endl;
    return 0;
}
```

---

## Solution 10

### Bug
The search loop runs only while `i < n - 1`, so the last element is never examined.

### Explanation
When the target is the last element the loop cannot find it. For `arr = {5, 9, 3}` with `target = 3` the expected index is `2`, but the buggy program prints `-1`. Use `i < n`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, target;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];
    cin >> target;

    int pos = -1;
    for (int i = 0; i < n; i++)
        if (arr[i] == target) {
            pos = i;
            break;
        }

    cout << pos << endl;
    return 0;
}
```

---

## Solution 11

### Bug
The comparison uses `arr[0]` instead of the running maximum `maxVal`.

### Explanation
Every element larger than the first element replaces `maxVal`, even if it is smaller than the current `maxVal`. For `arr = {5, 4, 9, 6}` the last update comes from `6`, so the buggy program prints `6` instead of `9`. Compare against `maxVal`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int maxVal = arr[0];
    for (int i = 1; i < n; i++)
        if (arr[i] > maxVal) maxVal = arr[i];

    cout << maxVal << endl;
    return 0;
}
```

---

## Solution 12

### Bug
The frequency counter is assigned `count = i` (the index) instead of being incremented.

### Explanation
The final value printed is the index of the last match, not the number of matches. For `arr = {8, 8, 8}` with `target = 8` the expected count is `3`, but the buggy program prints `2` (the last index). Use `count++`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, target;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];
    cin >> target;

    int count = 0;
    for (int i = 0; i < n; i++)
        if (arr[i] == target) count++;

    cout << count << endl;
    return 0;
}
```

---

## Solution 13

### Bug
The even-counting loop uses `i < n - 1` and never inspects the final element.

### Explanation
If the last element is even it is missed. For `arr = {4, 6, 3, 8}` the expected count is `3` (4, 6 and 8), but the buggy program counts only `2`. Use `i < n`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int count = 0;
    for (int i = 0; i < n; i++)
        if (arr[i] % 2 == 0) count++;

    cout << count << endl;
    return 0;
}
```

---

## Solution 14

### Bug
The printing loop uses `i <= n`, so it prints the extra zero stored in `arr[n]`.

### Explanation
`arr` is zero-initialized, so the output gets a trailing `0`. For `arr = {3, 8, 2}` the expected output `3 8 2` comes out as `3 8 2 0`. Change the condition to `i < n`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100] = {};
    for (int i = 0; i < n; i++) cin >> arr[i];

    for (int i = 0; i < n; i++)
        cout << arr[i] << (i < n - 1 ? " " : "");
    cout << endl;
    return 0;
}
```

---

## Solution 15

### Bug
The product is initialized to `0`, so every multiplication result is `0`.

### Explanation
For `arr = {2, 3, 4}` the expected product is `24`, but the buggy program prints `0`. Initialize the accumulator to `1`, the multiplicative identity. (The case that contains a genuine `0` still prints `0` correctly.)

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int prod = 1;
    for (int i = 0; i < n; i++) prod *= arr[i];

    cout << prod << endl;
    return 0;
}
```

---

## Solution 16

### Bug
The "second largest" is initialized to `arr[0]`, the same value as the largest.

### Explanation
If the true second largest is never promoted by the `if (arr[i] > largest)` branch it is never discovered. For `arr = {8, 3, 5}` the largest is `8` and the second largest is `5`, but the buggy program prints `8`. Initialize with a value known to be smaller, such as the smaller of `arr[0]` and `arr[1]`, or `arr[1]` with a swap.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int largest = arr[0], second = arr[1];
    if (largest < second) {
        int t = largest;
        largest = second;
        second = t;
    }
    for (int i = 2; i < n; i++) {
        if (arr[i] > largest) {
            second = largest;
            largest = arr[i];
        } else if (arr[i] > second) {
            second = arr[i];
        }
    }

    cout << second << endl;
    return 0;
}
```

---

## Solution 17

### Bug
The shift loop moves elements left but never saves `arr[0]`, so the original first value is lost and `arr[n-1]` keeps its old value instead of the wrapped-around first element.

### Explanation
For `arr = {1, 2, 3, 4}` the expected rotated array is `2 3 4 1`, but the buggy program prints `2 3 4 4`. Save `int first = arr[0];` before shifting, then assign `arr[n - 1] = first;` after the loop.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int first = arr[0];
    for (int i = 0; i < n - 1; i++)
        arr[i] = arr[i + 1];
    arr[n - 1] = first;

    for (int i = 0; i < n; i++) cout << arr[i] << " ";
    cout << endl;
    return 0;
}
```

---

## Solution 18

### Bug
After removing an element the loop index is not adjusted, so when two target values are adjacent the second one is slipped past and never checked.

### Explanation
After a removal, all later values shift left into position `i`, so the next iteration must re-check the same index. For `arr = {4, 4, 8}` with target `4` the expected result is `8`, but the buggy program prints `4 8`. Add `i--;` after `n--;` inside the removal branch.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, target;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];
    cin >> target;

    for (int i = 0; i < n; i++) {
        if (arr[i] == target) {
            for (int j = i; j < n - 1; j++)
                arr[j] = arr[j + 1];
            n--;
            i--;
        }
    }

    for (int i = 0; i < n; i++) cout << arr[i] << " ";
    cout << endl;
    return 0;
}
```

---

## Solution 19

### Bug
The inner row-summing loop runs `for (int j = 0; j < r; j++)`, using the row count for the column bound.

### Explanation
For a `2 x 3` matrix each row has 3 columns, so only the first 2 columns are summed. Row 0 of `{1, 2, 3}` gives `3` instead of `6`. The inner loop must use the column count: `j < c`. (When `r == c` the bug is invisible, which is why square test cases pass.)

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int r, c;
    cin >> r >> c;
    int mat[10][10];
    for (int i = 0; i < r; i++)
        for (int j = 0; j < c; j++) cin >> mat[i][j];

    for (int i = 0; i < r; i++) {
        int s = 0;
        for (int j = 0; j < c; j++)
            s += mat[i][j];
        cout << "Row " << i << ": " << s << endl;
    }
    return 0;
}
```

---

## Solution 20

### Bug
The condition `i + j == n - 1` selects the anti-diagonal instead of the main diagonal.

### Explanation
The main diagonal consists of the cells where the row index equals the column index. For the matrix
```
1 2 3
4 5 6
7 8 1
```
the main diagonal sums to `1 + 5 + 1 = 7`, but the anti-diagonal (`3 + 5 + 7`) equals `15`. Use `if (i == j)`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int mat[10][10];
    for (int i = 0; i < n; i++)
        for (int j = 0; j < n; j++) cin >> mat[i][j];

    int s = 0;
    for (int i = 0; i < n; i++)
        for (int j = 0; j < n; j++)
            if (i == j) s += mat[i][j];

    cout << s << endl;
    return 0;
}
```

---

## Solution 21

### Bug
The double loop visits every cell, so the pair `(i, j)` is swapped once and then swapped back when the loop reaches `(j, i)`, leaving the matrix unchanged.

### Explanation
For the matrix
```
1 2
3 4
```
the expected transpose is
```
1 3
2 4
```
but the buggy program prints the original matrix. The inner loop must start at `j = i + 1` so each pair is swapped exactly once.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int mat[10][10];
    for (int i = 0; i < n; i++)
        for (int j = 0; j < n; j++) cin >> mat[i][j];

    for (int i = 0; i < n; i++)
        for (int j = i + 1; j < n; j++) {
            int t = mat[i][j];
            mat[i][j] = mat[j][i];
            mat[j][i] = t;
        }

    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) cout << mat[i][j] << " ";
        cout << endl;
    }
    return 0;
}
```

---

## Solution 22

### Bug
The loops are ordered column-major: `j` (column) drives the outer loop and `i` (row) drives the inner loop, so the matrix is printed column by column instead of row by row.

### Explanation
For a `2 x 3` matrix the expected row-major output is `1 2 3 4 5 6`, but the buggy program prints `1 4 2 5 3 6`. Swap the loop roles: the outer loop must iterate rows and the inner loop columns.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int r, c;
    cin >> r >> c;
    int mat[10][10];
    for (int i = 0; i < r; i++)
        for (int j = 0; j < c; j++) cin >> mat[i][j];

    for (int i = 0; i < r; i++)
        for (int j = 0; j < c; j++)
            cout << mat[i][j] << " ";
    cout << endl;
    return 0;
}
```

---

## Solution 23

### Bug
The destination index is `(i + k - 1) % n` instead of `(i + k) % n`, so every element lands one slot too far left.

### Explanation
With `k = 1` the buggy formula is `(i + 0) % n`, which is the identity — the array is not rotated at all instead of being rotated by one. For `arr = {1, 2, 3, 4}` and `k = 2` the expected output `3 4 1 2` comes out as `4 1 2 3`. Remove the stray `- 1`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, k;
    cin >> n;
    int a[100];
    for (int i = 0; i < n; i++) cin >> a[i];
    cin >> k;

    int b[100];
    for (int i = 0; i < n; i++)
        b[(i + k) % n] = a[i];

    for (int i = 0; i < n; i++) cout << b[i] << " ";
    cout << endl;
    return 0;
}
```

---

## Solution 24

### Bug
The loop prints the current array value `arr[i]` instead of the accumulated sum `sum`.

### Explanation
For `arr = {1, 2, 3, 4}` the expected prefix sums are `1 3 6 10`, but the buggy program prints `1 2 3 4`. To compute prefix sums, the accumulator must be updated first and then printed.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int sum = 0;
    for (int i = 0; i < n; i++) {
        sum += arr[i];
        cout << sum << " ";
    }
    cout << endl;
    return 0;
}
```

---

## Solution 25

### Bug
Only the front pointer `i` is incremented; the back pointer `j` is never decremented.

### Explanation
The back pointer stays fixed at `n - 1`, so elements are repeatedly swapped with the last slot instead of producing a true reverse. For `arr = {1, 2, 3}` the expected output `3 2 1` comes out as `3 1 2`. Add `j--;` next to `i++;`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int i = 0, j = n - 1;
    while (i < j) {
        int t = arr[i];
        arr[i] = arr[j];
        arr[j] = t;
        i++;
        j--;
    }

    for (int i = 0; i < n; i++) cout << arr[i] << " ";
    cout << endl;
    return 0;
}
```

---

## Solution 26

### Bug
The inner loop starts at `j = i + 1`, so single-element subarrays are never tested.

### Explanation
When the target equals the value of a lone element it is missed. For `arr = {5, 2, 3}` with `target = 5` the expected answer is `Found`, but the buggy program prints `Not Found`. Start the inner loop at `j = i` and add `arr[i]` only once (move `sum = arr[i];` inside the inner iteration or initialize before the loop).

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, target;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];
    cin >> target;

    bool found = false;
    for (int i = 0; i < n && !found; i++) {
        int sum = 0;
        for (int j = i; j < n; j++) {
            sum += arr[j];
            if (sum == target) found = true;
        }
    }

    cout << (found ? "Found" : "Not Found") << endl;
    return 0;
}
```

---

## Solution 27

### Bug
The average is computed with integer division, `int avg = sum / n`, so the comparison uses a truncated average.

### Explanation
For `arr = {4, 9, 5, 1}` the true average is `4.75`; only `9` is greater, so the expected count is `1`. The truncated average `4` also marks `5` as greater, giving `2`. Use a floating-point average for the comparison.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    int sum = 0;
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
        sum += arr[i];
    }

    double avg = (double)sum / n;
    int count = 0;
    for (int i = 0; i < n; i++)
        if ((double)arr[i] > avg) count++;

    cout << count << endl;
    return 0;
}
```

---

## Solution 28

### Bug
The best-sum tracker is initialized to `0`, so for all-negative arrays the answer is always `0` instead of the largest element.

### Explanation
For `arr = {-5, -1, -8}` the maximum subarray sum is `-1`, but the buggy program prints `0`. Initialize `best` with the first element (`arr[0]`) and run the loop from index `1`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int sum = arr[0], best = arr[0];
    for (int i = 1; i < n; i++) {
        if (sum < 0) sum = 0;
        sum += arr[i];
        if (sum > best) best = sum;
    }

    cout << best << endl;
    return 0;
}
```

---

## Solution 29

### Bug
The counter `count` is declared outside the outer loop, so it is never reset between candidates and keeps accumulating across elements.

### Explanation
The accumulated count quickly exceeds `n / 2` even when no majority exists. For `arr = {2, 3, 4}` the buggy program prints `3` instead of `None`. Move the declaration `int count = 0;` inside the outer loop.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    for (int i = 0; i < n; i++) {
        int count = 0;
        for (int j = 0; j < n; j++)
            if (arr[j] == arr[i]) count++;
        if (count > n / 2) {
            cout << arr[i] << endl;
            return 0;
        }
    }
    cout << "None" << endl;
    return 0;
}
```

---

## Solution 30

### Bug
The comparison is `count < maxCount` instead of `count > maxCount`, and the update condition never triggers, so `best` always stays `arr[0]`.

### Explanation
With `maxCount` starting at `0`, `count` (always at least 1) is never smaller, so the "best" value is never updated. For `arr = {2, 3, 1, 3, 1}` the most frequent value is `3` and the tie is broken to `3`, but the buggy program prints `2`. Use `>` and update both `maxCount` and `best`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int best = arr[0], maxCount = 0;
    for (int i = 0; i < n; i++) {
        int count = 0;
        for (int j = 0; j < n; j++)
            if (arr[j] == arr[i]) count++;
        if (count > maxCount) {
            maxCount = count;
            best = arr[i];
        }
    }

    cout << best << endl;
    return 0;
}
```

---

## Solution 31

### Bug
The nested loops visit every ordered pair with `i != j`, counting both `(i, j)` and `(j, i)`, so every matching pair is counted twice.

### Explanation
For `arr = {1, 2, 3}` with `target = 3` exactly one pair (`1 + 2`) matches, but the buggy program prints `2`. Restrict the inner loop to `j = i + 1` so each unordered pair is counted once.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, target;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];
    cin >> target;

    int pairs = 0;
    for (int i = 0; i < n; i++)
        for (int j = i + 1; j < n; j++)
            if (arr[i] + arr[j] == target) pairs++;

    cout << pairs << endl;
    return 0;
}
```

---

## Solution 32

### Bug
The sum adds the raw values instead of their absolute values.

### Explanation
Negative values reduce the total. For `arr = {-2, 5, -3}` the expected sum of magnitudes is `10`, but the buggy program prints `0`. Use `abs(arr[i])` from `<cstdlib>`.

### Corrected Code

```cpp
#include <iostream>
#include <cstdlib>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int sum = 0;
    for (int i = 0; i < n; i++) sum += abs(arr[i]);

    cout << sum << endl;
    return 0;
}
```

---

## Solution 33

### Bug
The update uses `prod += arr[i]`, accidentally adding instead of multiplying.

### Explanation
For `arr = {2, 3, 4}` the expected product is `24`, but the buggy program computes `1 + 2 + 3 + 4 = 10`. Use `prod *= arr[i];`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int prod = 1;
    for (int i = 0; i < n; i++) prod *= arr[i];

    cout << prod << endl;
    return 0;
}
```

---

## Solution 34

### Bug
The outer loop iterates `i < m` (the size of the second array) while indexing the first array `a[i]`.

### Explanation
When A is longer than B, the trailing elements of A are never compared. For `A = {5, 6, 7, 8}` and `B = {9, 8}` there is a match (`8`), but the buggy program prints `No` because `8` sits at `a[3]` and the loop stops at index `1`. The outer loop must use `i < n`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, m;
    cin >> n;
    int a[100];
    for (int i = 0; i < n; i++) cin >> a[i];
    cin >> m;
    int b[100];
    for (int i = 0; i < m; i++) cin >> b[i];

    for (int i = 0; i < n; i++)
        for (int j = 0; j < m; j++)
            if (a[i] == b[j]) {
                cout << "Yes" << endl;
                return 0;
            }
    cout << "No" << endl;
    return 0;
}
```

---

## Solution 35

### Bug
The second copying loop never increments the write index `k`, so every element of B overwrites `c[n]`.

### Explanation
Only the last element of B survives. For `A = {1, 2}` and `B = {8, 9, 7}` the expected merge is `1 2 8 9 7`, but the buggy program prints `1 2 7`. Add `k++;` inside the loop that copies B.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, m;
    cin >> n;
    int a[100];
    for (int i = 0; i < n; i++) cin >> a[i];
    cin >> m;
    int b[100];
    for (int i = 0; i < m; i++) cin >> b[i];

    int c[200];
    int k = 0;
    for (int i = 0; i < n; i++) {
        c[k] = a[i];
        k++;
    }
    for (int i = 0; i < m; i++) {
        c[k] = b[i];
        k++;
    }

    for (int i = 0; i < n + m; i++) cout << c[i] << " ";
    cout << endl;
    return 0;
}
```

---

## Solution 36

### Bug
Two related problems: `maxVal` is initialized to `0` (wrong for all-negative arrays), and `maxIdx` is incremented (`maxIdx++`) instead of being set to the current index `i`.

### Explanation
The counter approach only works while new maxima keep appearing at consecutive positions. For `arr = {2, 1, 3}` the maximum is at index `2`, but the buggy program prints `1`. For `arr = {-5, -2, -7}` nothing beats `0`, so the buggy program prints `-1` instead of `1`. Initialize `maxVal = arr[0]`, loop from index `1`, and always write `maxIdx = i;`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int maxVal = arr[0];
    int maxIdx = 0;
    for (int i = 1; i < n; i++)
        if (arr[i] > maxVal) {
            maxVal = arr[i];
            maxIdx = i;
        }

    cout << maxIdx << endl;
    return 0;
}
```

---

## Solution 37

### Bug
The condition `arr[i] >= arr[0]` treats elements equal to the first element as acceptable, and index `1` is found first for equal values.

### Explanation
The problem requires strictly greater values. For `arr = {5, 5, 5}` no element is strictly greater, so the expected answer is `-1`, but the buggy program reports index `1`. Use `>` instead of `>=`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int pos = -1;
    for (int i = 1; i < n; i++)
        if (arr[i] > arr[0]) {
            pos = i;
            break;
        }

    cout << pos << endl;
    return 0;
}
```

---

## Solution 38

### Bug
The comparison `abs(arr[i]) > peak` compares a magnitude against the signed value `peak`, so a negative peak can be replaced by a much smaller positive value.

### Explanation
For `arr = {-10, 3, -4, 8}` the element farthest from zero is `-10` (magnitude 10), but once `peak` becomes negative, small positives like `3` or `8` pass the comparison and the program prints `8`. Compare magnitudes on both sides: `abs(arr[i]) > abs(peak)`.

### Corrected Code

```cpp
#include <iostream>
#include <cstdlib>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int peak = arr[0];
    for (int i = 1; i < n; i++)
        if (abs(arr[i]) > abs(peak)) peak = arr[i];

    cout << peak << endl;
    return 0;
}
```

---

## Solution 39

### Bug
The comparison loop visits pairs `(0,1)`, `(2,3)`, ... and skips a final lone element (or an empty traversal entirely).

### Explanation
For an odd-sized array the last element is never examined, and for a single-element array nothing is examined at all. For `arr = {7}` the expected maximum is `7`, but the buggy program prints `0`. Use a simple full loop over `i < n`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int maxVal = 0;
    for (int i = 0; i < n; i++)
        if (arr[i] > maxVal) maxVal = arr[i];

    cout << maxVal << endl;
    return 0;
}
```

---

## Solution 40

### Bug
Negative values of k are converted with `k = -k`, which produces a right rotation of |k| steps instead of the required left rotation.

### Explanation
For `arr = {1, 2, 3, 4}` and `k = -1` a left rotation by 1 gives `2 3 4 1`, but the buggy program prints `4 1 2 3` (a right rotation). A negative k must be normalized by adding `n` once, e.g. `if (k < 0) k += n;`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, k;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];
    cin >> k;

    k %= n;
    if (k < 0) k += n;

    for (int r = 0; r < k; r++) {
        int last = arr[n - 1];
        for (int i = n - 1; i > 0; i--) arr[i] = arr[i - 1];
        arr[0] = last;
    }

    for (int i = 0; i < n; i++) cout << arr[i] << " ";
    cout << endl;
    return 0;
}
```

---

## Solution 41

### Bug
The comparison loop always runs `i < m`, even when `m > n`, so it reads past A's meaningful values (extra slots are zero-initialized) and reports spurious mismatches.

### Explanation
Only the first min(n, m) positions should be compared. For `A = {1, 2, 3}` and `B = {1, 2, 3, 4, 4}` the prefix of length 3 matches, so the expected answer is `Equal`, but the buggy loop compares `a[3] == 0` against `b[3] == 4` and prints `Different`. Bound the loop by `min(n, m)`.

### Corrected Code

```cpp
#include <iostream>
#include <algorithm>
using namespace std;

int main() {
    int a[100] = {};
    int b[100] = {};
    int n, m;
    cin >> n;
    for (int i = 0; i < n; i++) cin >> a[i];
    cin >> m;
    for (int i = 0; i < m; i++) cin >> b[i];

    int lim = min(n, m);
    bool ok = true;
    for (int i = 0; i < lim; i++)
        if (a[i] != b[i]) ok = false;

    cout << (ok ? "Equal" : "Different") << endl;
    return 0;
}
```

---

## Solution 42

### Bug
Two related problems: the sliding loop stops at `i < n - k` (missing the last valid window that starts at `n - k`), and the best-sum tracker is initialized to `0` (wrong when all window sums are negative).

### Explanation
For `arr = {1, 1, 1, 9, 9}` with `k = 2` the last window `{9, 9}` sums to `18` and is the largest, but the buggy program's last window is `{1, 9}` and it prints `10`. Use `i <= n - k` and initialize `best` with the first window's sum.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, k;
    cin >> n >> k;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int best = 0;
    for (int i = 0; i < k; i++) best += arr[i];

    for (int i = 0; i <= n - k; i++) {
        int sum = 0;
        for (int j = i; j < i + k; j++) sum += arr[j];
        if (sum > best) best = sum;
    }

    cout << best << endl;
    return 0;
}
```

---

## Solution 43

### Bug
The helper is called with `n - 2` as the right bound, so the last element is never included in the reversal.

### Explanation
For `arr = {1, 2, 3, 4}` the whole array should be reversed to `4 3 2 1`, but the call `rev(arr, 0, n - 2)` reverses only indices `0..2`, producing `3 2 1 4`. The right bound must be `n - 1`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

void rev(int a[], int l, int r) {
    while (l < r) {
        int t = a[l];
        a[l] = a[r];
        a[r] = t;
        l++;
        r--;
    }
}

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    rev(arr, 0, n - 1);

    for (int i = 0; i < n; i++) cout << arr[i] << " ";
    cout << endl;
    return 0;
}
```

---

## Solution 44

### Bug
The inner loop starts at `j = i` instead of `j = i + 1`, so every position "matches itself" and the count includes all n self-pairs.

### Explanation
For `arr = {5, 5, 5}` the pairs with `i < j` number `3`, but the buggy program also counts the diagonal pairs `(0,0)`, `(1,1)`, `(2,2)` and prints `6`. Use `j = i + 1`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int count = 0;
    for (int i = 0; i < n; i++)
        for (int j = i + 1; j < n; j++)
            if (arr[i] == arr[j]) count++;

    cout << count << endl;
    return 0;
}
```

---

## Solution 45

### Bug
The tie-breaking comparison is reversed: `a[i] < b[j]` picks the smaller tail element while filling from the back, which destroys the ascending order.

### Explanation
When filling the result from the last position, each slot must receive the larger of the two remaining tail values. For `A = {1, 300}` and `B = {100, 200}` the expected merge is `1 100 200 300`, but the buggy program prints `1 300 100 200`. Compare with `>`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, m;
    cin >> n;
    int a[100];
    for (int i = 0; i < n; i++) cin >> a[i];
    cin >> m;
    int b[100];
    for (int i = 0; i < m; i++) cin >> b[i];

    int res[200] = {};
    int i = n - 1, j = m - 1, k = n + m;
    while (i >= 0 && j >= 0) {
        if (a[i] > b[j]) res[--k] = a[i--];
        else res[--k] = b[j--];
    }
    while (i >= 0) res[--k] = a[i--];
    while (j >= 0) res[--k] = b[j--];

    for (int i = 0; i < n + m; i++) cout << res[i] << " ";
    cout << endl;
    return 0;
}
```

---

## Solution 46

### Bug
The best-run length is updated only inside the `else` branch, so a strictly increasing run that extends to the last element is never recorded.

### Explanation
For `arr = {4, 5, 6}` the whole array is one run of length `3`, but the buggy program prints `1` because no `else` ever fires. Update `best` after the loop as well (or compare at every step).

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int cur = 1, best = 1;
    for (int i = 1; i < n; i++) {
        if (arr[i] > arr[i - 1]) cur++;
        else {
            if (cur > best) best = cur;
            cur = 1;
        }
    }
    if (cur > best) best = cur;

    cout << best << endl;
    return 0;
}
```

---

## Solution 47

### Bug
The total is computed as `(n / 2) * (n + 1)`, which is correct only when n is even; for odd n the truncating integer division makes the total too small.

### Explanation
The true sum of `1..n` is `n * (n + 1) / 2`. For `n = 5` this is `15`; the buggy formula gives `12`. With the input `1 2 4 5` (sum `12`) the expected missing number is `3`, but the buggy program prints `0`. Compute `n * (n + 1) / 2` (with integer arithmetic the multiplication must come first).

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int sum = 0;
    for (int i = 0; i < n - 1; i++) {
        int x;
        cin >> x;
        sum += x;
    }

    int total = n * (n + 1) / 2;
    cout << total - sum << endl;
    return 0;
}
```

---

## Solution 48

### Bug
The shift loop runs `for (int i = n - 1; i > p; i--)`, stopping one index too early, so the element currently at position `p` is never shifted and gets overwritten.

### Explanation
For `arr = {10, 20, 30, 40}` with `p = 2` and `x = 99` the expected array is `10 20 99 30 40`, but the buggy program prints `10 20 99 40 40`. The loop must continue while `i >= p` so the value at position `p` moves to `p + 1` first.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100] = {};
    for (int i = 0; i < n; i++) cin >> arr[i];

    int p, x;
    cin >> p >> x;

    for (int i = n - 1; i >= p; i--)
        arr[i + 1] = arr[i];
    arr[p] = x;

    for (int i = 0; i <= n; i++) cout << arr[i] << " ";
    cout << endl;
    return 0;
}
```

---

## Solution 49

### Bug
The pivot index is recorded as `i` (the position of the larger element) instead of `i + 1` (the position where the smaller segment starts).

### Explanation
For `arr = {3, 4, 0, 1, 2}` the drop happens at `arr[1] > arr[2]`, so the pivot (index of the minimum) is `2`. The buggy program records `1` and reports the wrong index. Store `pivot = i + 1;`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int pivot = 0;
    for (int i = 0; i < n - 1; i++)
        if (arr[i] > arr[i + 1]) pivot = i + 1;

    cout << pivot << endl;
    return 0;
}
```

---

## Solution 50

### Bug
The next index is computed as `(idx + k + 1) % n`, an extra `+1` that advances by `k + 1` steps instead of `k`.

### Explanation
For `arr = {1, 2, 3, 4}` with `s = 0` and `k = 1` the expected walk is `1 2 3 4`, but the buggy program advances by `2` and prints `1 3 1 3`. Use `(idx + k) % n`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, s, k;
    cin >> n;
    int arr[100];
    for (int i = 0; i < n; i++) cin >> arr[i];
    cin >> s >> k;

    int idx = s;
    for (int c = 0; c < n; c++) {
        cout << arr[idx] << " ";
        idx = (idx + k) % n;
    }

    cout << endl;
    return 0;
}
```