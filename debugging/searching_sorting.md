# C++ Debugging — Searching & Sorting

## Question 1

### Difficulty
Easy

### Bug Type
Linear Search Misses Last Element

### Problem
Write a function that finds the position of a given key in an unsorted array using linear search. The function should return the index of the first match, or -1 if the key is not present.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int linearSearch(const vector<int>& arr, int key) {
    for (int i = 0; i < (int)arr.size() - 1; ++i) {
        if (arr[i] == key) return i;
    }
    return -1;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << linearSearch(arr, key) << endl;
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
2
```
the expected output is:
```text
1
```

---
For:
```text
3
1 2 3
3
```
the expected output is:
```text
2
```

---
For:
```text
4
4 5 6 7
7
```
the expected output is:
```text
3
```

## Question 2

### Difficulty
Easy

### Bug Type
Bubble Sort Wrong Direction (descending output)

### Problem
Implement bubble sort to arrange an array of integers in ascending order. The final array must be sorted smallest to largest.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

void bubbleSort(vector<int>& arr) {
    int n = arr.size();
    for (int i = 0; i < n - 1; ++i) {
        for (int j = 0; j < n - i - 1; ++j) {
            if (arr[j] < arr[j + 1]) swap(arr[j], arr[j + 1]);
        }
    }
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    bubbleSort(arr);
    for (int i = 0; i < n; ++i) cout << arr[i] << " ";
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
9
```
the expected output is:
```text
9
```

---
For:
```text
3
3 1 2
```
the expected output is:
```text
1 2 3
```

---
For:
```text
4
1 5 3 2
```
the expected output is:
```text
1 2 3 5
```

## Question 3

### Difficulty
Easy

### Bug Type
Selection Sort Wrong Comparison Direction

### Problem
Implement selection sort so that the array ends up sorted in ascending order. Each pass must pick the smallest remaining element and place it at the front.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

void selectionSort(vector<int>& arr) {
    int n = arr.size();
    for (int i = 0; i < n - 1; ++i) {
        int idx = i;
        for (int j = i + 1; j < n; ++j) {
            if (arr[j] > arr[idx]) idx = j;
        }
        swap(arr[i], arr[idx]);
    }
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    selectionSort(arr);
    for (int i = 0; i < n; ++i) cout << arr[i] << " ";
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
5
```
the expected output is:
```text
5
```

---
For:
```text
3
3 1 2
```
the expected output is:
```text
1 2 3
```

---
For:
```text
4
4 2 5 1
```
the expected output is:
```text
1 2 4 5
```

## Question 4

### Difficulty
Easy

### Bug Type
Binary Search Wrong Midpoint Calculation

### Problem
Write a binary search over a sorted ascending array that returns the index of the key, or -1 if it is missing. The midpoint must divide the active range evenly.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int binarySearch(const vector<int>& arr, int key) {
    int low = 0, high = (int)arr.size() - 1;
    while (low <= high) {
        int mid = low + high / 2;
        if (arr[mid] == key) return mid;
        if (arr[mid] < key) low = mid + 1;
        else high = mid - 1;
    }
    return -1;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << binarySearch(arr, key) << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
1 3 5 7
3
```
the expected output is:
```text
1
```

---
For:
```text
4
1 3 5 7
5
```
the expected output is:
```text
2
```

---
For:
```text
4
2 4 6 8
6
```
the expected output is:
```text
2
```

## Question 5

### Difficulty
Easy

### Bug Type
Linear Search Stores Wrong Index Variable

### Problem
Write a linear search that returns the index of the first occurrence of the key. The index being searched for must be preserved until it is returned.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int linearSearch(const vector<int>& arr, int key) {
    int index = -1;
    for (int i = 0; i < (int)arr.size(); ++i) {
        if (arr[i] == key) index = i;
        else index = -1;
    }
    return index;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << linearSearch(arr, key) << endl;
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
30
```
the expected output is:
```text
2
```

---
For:
```text
3
10 20 30
20
```
the expected output is:
```text
1
```

---
For:
```text
3
10 20 30
10
```
the expected output is:
```text
0
```

## Question 6

### Difficulty
Easy

### Bug Type
Search Returns -1 Even Though Present (boundary)

### Problem
Write a binary search over a sorted array that finds the key and returns its index. The element at the final remaining position must still be checked.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int search(const vector<int>& arr, int key) {
    int low = 0, high = (int)arr.size() - 1;
    while (low < high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == key) return mid;
        if (arr[mid] < key) low = mid + 1;
        else high = mid - 1;
    }
    return -1;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << search(arr, key) << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3
5 10 15
10
```
the expected output is:
```text
1
```

---
For:
```text
3
5 10 15
5
```
the expected output is:
```text
0
```

---
For:
```text
3
5 10 15
15
```
the expected output is:
```text
2
```

## Question 7

### Difficulty
Easy

### Bug Type
Insertion Sort Wrong Inner-Loop Direction

### Problem
Implement insertion sort so that each new element is placed into its correct position among the already-sorted elements on its left.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

void insertionSort(vector<int>& arr) {
    for (int i = 1; i < (int)arr.size(); ++i) {
        int j = i;
        while (j < (int)arr.size() - 1 && arr[j - 1] > arr[j]) {
            swap(arr[j - 1], arr[j]);
            ++j;
        }
    }
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    insertionSort(arr);
    for (int i = 0; i < n; ++i) cout << arr[i] << " ";
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
1 2 3
```
the expected output is:
```text
1 2 3
```

---
For:
```text
3
3 1 2
```
the expected output is:
```text
1 2 3
```

---
For:
```text
4
4 3 2 1
```
the expected output is:
```text
1 2 3 4
```

## Question 8

### Difficulty
Easy

### Bug Type
First Occurrence Never Breaks (returns last)

### Problem
Write a search that returns the index of the FIRST occurrence of the key in the array. Even if the key appears several times, the earliest index is wanted.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int firstOccurrence(const vector<int>& arr, int key) {
    int pos = -1;
    for (int i = 0; i < (int)arr.size(); ++i) {
        if (arr[i] == key) pos = i;
    }
    return pos;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << firstOccurrence(arr, key) << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3
1 4 5
4
```
the expected output is:
```text
1
```

---
For:
```text
4
1 4 4 5
4
```
the expected output is:
```text
1
```

---
For:
```text
4
2 2 9 2
2
```
the expected output is:
```text
0
```

## Question 9

### Difficulty
Easy

### Bug Type
Bubble Sort Runs Only One Pass

### Problem
Implement bubble sort correctly. Elements must keep bubbling to their final positions over repeated passes until the whole array is sorted.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

void bubbleSort(vector<int>& arr) {
    int n = arr.size();
    for (int i = 0; i < 1; ++i) {
        for (int j = 0; j < n - 1; ++j) {
            if (arr[j] > arr[j + 1]) swap(arr[j], arr[j + 1]);
        }
    }
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    bubbleSort(arr);
    for (int i = 0; i < n; ++i) cout << arr[i] << " ";
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
2 1 3
```
the expected output is:
```text
1 2 3
```

---
For:
```text
3
3 2 1
```
the expected output is:
```text
1 2 3
```

---
For:
```text
4
4 3 2 1
```
the expected output is:
```text
1 2 3 4
```

## Question 10

### Difficulty
Easy

### Bug Type
Selection Sort Tracks Min Value Instead of Index

### Problem
Implement selection sort. Each pass must remember the INDEX of the smallest element so it can be swapped into place.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

void selectionSort(vector<int>& arr) {
    int n = arr.size();
    for (int i = 0; i < n - 1; ++i) {
        int minVal = arr[i];
        int minIdx = i;
        for (int j = i + 1; j < n; ++j) {
            if (arr[j] < minVal) minVal = arr[j];
        }
        swap(arr[i], arr[minIdx]);
    }
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    selectionSort(arr);
    for (int i = 0; i < n; ++i) cout << arr[i] << " ";
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
1 2 3
```
the expected output is:
```text
1 2 3
```

---
For:
```text
3
3 1 2
```
the expected output is:
```text
1 2 3
```

---
For:
```text
5
5 2 4 1 3
```
the expected output is:
```text
1 2 3 4 5
```

## Question 11

### Difficulty
Medium

### Bug Type
Binary Search High Update Causes Infinite Loop

### Problem
Write a binary search over a sorted array. When the key is smaller than the middle element, the upper bound must move strictly below the midpoint so the range always shrinks.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int binarySearch(const vector<int>& arr, int key) {
    int low = 0, high = (int)arr.size() - 1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == key) return mid;
        if (arr[mid] < key) low = mid + 1;
        else high = mid;
    }
    return -1;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << binarySearch(arr, key) << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
10 20 30 40
20
```
the expected output is:
```text
1
```

---
For:
```text
4
10 20 30 40
25
```
the expected output is:
```text
-1
```
(Note: the buggy code enters an infinite loop on this input.)

---
For:
```text
4
10 20 30 40
5
```
the expected output is:
```text
-1
```
(Note: the buggy code enters an infinite loop on this input.)

## Question 12

### Difficulty
Medium

### Bug Type
Binary Search Low Update (`low = mid`) Infinite Loop

### Problem
Write a binary search over a sorted array. When the key is larger than the middle element, the lower bound must advance past the midpoint.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int binarySearch(const vector<int>& arr, int key) {
    int low = 0, high = (int)arr.size() - 1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == key) return mid;
        if (arr[mid] < key) low = mid;
        else high = mid - 1;
    }
    return -1;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << binarySearch(arr, key) << endl;
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
20
```
the expected output is:
```text
1
```

---
For:
```text
3
10 20 30
30
```
the expected output is:
```text
2
```
(Note: the buggy code enters an infinite loop on this input.)

---
For:
```text
3
20 40 60
60
```
the expected output is:
```text
2
```
(Note: the buggy code enters an infinite loop on this input.)

## Question 13

### Difficulty
Medium

### Bug Type
Count of Key in Sorted Array Wrong Bounds

### Problem
Count how many times a key appears in a sorted array by locating its first and last occurrence. If the key is absent, the count must be 0.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int countKey(const vector<int>& arr, int key) {
    int first = -1, last = -1;
    for (int i = 0; i < (int)arr.size(); ++i) {
        if (arr[i] == key && first == -1) first = i;
        if (arr[i] == key) last = i;
    }
    return last - first + 1;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << countKey(arr, key) << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
1 2 2 3
2
```
the expected output is:
```text
2
```

---
For:
```text
3
1 2 3
5
```
the expected output is:
```text
0
```

---
For:
```text
3
1 2 3
4
```
the expected output is:
```text
0
```

## Question 14

### Difficulty
Medium

### Bug Type
First/Last Occurrence Binary Search Off-by-One

### Problem
Find the FIRST occurrence of a key in a sorted array using binary search. The check that decides whether the current match is the first must look at the element on its left, not on its right.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int firstOccurrence(const vector<int>& arr, int key) {
    int low = 0, high = (int)arr.size() - 1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == key &&
            (mid == (int)arr.size() - 1 || arr[mid + 1] > key))
            return mid;
        if (arr[mid] < key) low = mid + 1;
        else high = mid - 1;
    }
    return -1;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << firstOccurrence(arr, key) << endl;
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
2
```
the expected output is:
```text
1
```

---
For:
```text
4
1 2 2 3
2
```
the expected output is:
```text
1
```

---
For:
```text
4
2 2 2 3
2
```
the expected output is:
```text
0
```

## Question 15

### Difficulty
Medium

### Bug Type
Rotated Sorted Array Search Wrong Condition

### Problem
Write a search that works on a rotated sorted array. When the left half is sorted and the key lies inside it, the search must narrow to that left half.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int search(const vector<int>& arr, int key) {
    int low = 0, high = (int)arr.size() - 1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == key) return mid;
        if (arr[low] <= arr[mid]) {
            if (key >= arr[low] && key < arr[mid]) low = mid + 1;
            else high = mid - 1;
        } else {
            if (key > arr[mid] && key <= arr[high]) low = mid + 1;
            else high = mid - 1;
        }
    }
    return -1;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << search(arr, key) << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
7
4 5 6 7 0 1 2
7
```
the expected output is:
```text
3
```

---
For:
```text
7
4 5 6 7 0 1 2
5
```
the expected output is:
```text
1
```

---
For:
```text
7
4 5 6 7 0 1 2
0
```
the expected output is:
```text
4
```

## Question 16

### Difficulty
Medium

### Bug Type
Sorted Matrix Search Wrong Decision

### Problem
Write a search over a matrix where every row is ascending and every column is ascending. Starting at the top-right corner, the search must move LEFT when the current cell is too large and DOWN when it is too small.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

bool searchMatrix(const vector<vector<int>>& m, int key) {
    int row = 0, col = (int)m[0].size() - 1;
    while (row < (int)m.size() && col >= 0) {
        int v = m[row][col];
        if (v == key) return true;
        if (v > key) ++row;
        else --col;
    }
    return false;
}

int main() {
    int rows, cols;
    cin >> rows >> cols;
    vector<vector<int>> m(rows, vector<int>(cols));
    for (int i = 0; i < rows; ++i)
        for (int j = 0; j < cols; ++j)
            cin >> m[i][j];
    int key;
    cin >> key;
    cout << (searchMatrix(m, key) ? "true" : "false") << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
2 3
1 3 5
2 4 6
5
```
the expected output is:
```text
true
```

---
For:
```text
2 3
1 3 5
2 4 6
4
```
the expected output is:
```text
true
```

---
For:
```text
2 3
1 3 5
2 4 6
1
```
the expected output is:
```text
true
```

## Question 17

### Difficulty
Medium

### Bug Type
Lower-Bound Insertion Position Bug

### Problem
Write a function that returns the first index where a key could be inserted in a sorted array without breaking the order (lower bound). The upper bound must never skip below the confirmed insertion range.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int lowerBound(const vector<int>& arr, int key) {
    int low = 0, high = (int)arr.size();
    while (low < high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] < key) low = mid + 1;
        else high = mid - 1;
    }
    return low;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << lowerBound(arr, key) << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
5
1 3 3 5 7
3
```
the expected output is:
```text
1
```

---
For:
```text
5
1 3 3 5 7
7
```
the expected output is:
```text
4
```

---
For:
```text
5
1 2 3 4 5
5
```
the expected output is:
```text
4
```

## Question 18

### Difficulty
Medium

### Bug Type
Peak Element Wrong Neighbor Comparison

### Problem
Find a peak element: an index whose value is not smaller than both of its neighbors (edges only need one neighbor). The search must keep looking when the array is still strictly increasing.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int findPeak(const vector<int>& arr) {
    int n = (int)arr.size();
    for (int i = 0; i < n - 1; ++i) {
        if (arr[i] > arr[i + 1]) return i;
    }
    return -1;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    cout << findPeak(arr) << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3
1 3 2
```
the expected output is:
```text
1
```

---
For:
```text
3
1 2 3
```
the expected output is:
```text
2
```

---
For:
```text
4
1 2 3 4
```
the expected output is:
```text
3
```

## Question 19

### Difficulty
Medium

### Bug Type
Ascending vs Descending Binary Search Confusion

### Problem
Write a binary search for an ascending sorted array. When the middle element is smaller than the key, the search must continue in the right half.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int binarySearch(const vector<int>& arr, int key) {
    int low = 0, high = (int)arr.size() - 1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == key) return mid;
        if (arr[mid] < key) high = mid - 1;
        else low = mid + 1;
    }
    return -1;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << binarySearch(arr, key) << endl;
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
20
```
the expected output is:
```text
1
```

---
For:
```text
3
10 20 30
30
```
the expected output is:
```text
2
```

---
For:
```text
3
10 20 30
10
```
the expected output is:
```text
0
```

## Question 20

### Difficulty
Medium

### Bug Type
Sort by Absolute Value Wrong Modifier/Comparator

### Problem
Sort an array of integers in ascending order of their ABSOLUTE values. When two values tie on absolute value, either order is acceptable.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    sort(arr.begin(), arr.end(), [](int a, int b) { return a < b; });
    for (int i = 0; i < n; ++i) cout << arr[i] << " ";
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
4 1 3
```
the expected output is:
```text
1 3 4
```

---
For:
```text
4
-5 2 -1 4
```
the expected output is:
```text
-1 2 4 -5
```

---
For:
```text
3
-3 1 -2
```
the expected output is:
```text
1 -2 -3
```

## Question 21

### Difficulty
Medium

### Bug Type
Kth Smallest Counting Boundary

### Problem
Find the k-th smallest value in an array using counting. Every element, including the last one, must contribute to the counts.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

const int MAXV = 100;

int kthSmallest(const vector<int>& arr, int k) {
    for (int i = 1; i <= MAXV; ++i) {
        int cnt = 0;
        for (int j = 0; j < (int)arr.size() - 1; ++j)
            if (arr[j] <= i) ++cnt;
        if (cnt >= k) return i;
    }
    return -1;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int k;
    cin >> k;
    cout << kthSmallest(arr, k) << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3
1 1 2
2
```
the expected output is:
```text
1
```

---
For:
```text
3
1 1 2
3
```
the expected output is:
```text
2
```

---
For:
```text
1
5
1
```
the expected output is:
```text
5
```

## Question 22

### Difficulty
Medium

### Bug Type
Duplicate Counting Inner-Loop Boundary

### Problem
Count how many pairs (i, j) with i < j hold arr[i] == arr[j]. Every pair where the second element sits at the last index must be counted too.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int countDuplicatePairs(const vector<int>& arr) {
    int pairs = 0;
    for (int i = 0; i < (int)arr.size() - 1; ++i) {
        for (int j = i + 1; j < (int)arr.size() - 1; ++j) {
            if (arr[i] == arr[j]) ++pairs;
        }
    }
    return pairs;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    cout << countDuplicatePairs(arr) << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
3 1 3 5
```
the expected output is:
```text
1
```

---
For:
```text
4
2 2 3 2
```
the expected output is:
```text
3
```

---
For:
```text
4
1 2 2 2
```
the expected output is:
```text
3
```

## Question 23

### Difficulty
Medium

### Bug Type
Merge Two Sorted Arrays Wrong Write Index

### Problem
Merge two sorted arrays into one sorted array. Every element written into the result must advance the write cursor exactly once.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

vector<int> mergeSorted(const vector<int>& a, const vector<int>& b) {
    int i = 0, j = 0, k = 0;
    vector<int> c(a.size() + b.size());
    while (i < (int)a.size() && j < (int)b.size()) {
        if (a[i] <= b[j]) c[k++] = a[i++];
        else c[++k] = b[j++];
    }
    while (i < (int)a.size()) c[k++] = a[i++];
    while (j < (int)b.size()) c[k++] = b[j++];
    return c;
}

int main() {
    int m, n;
    cin >> m >> n;
    vector<int> a(m), b(n);
    for (int i = 0; i < m; ++i) cin >> a[i];
    for (int i = 0; i < n; ++i) cin >> b[i];
    vector<int> c = mergeSorted(a, b);
    for (int i = 0; i < (int)c.size(); ++i) cout << c[i] << " ";
    cout << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
1 1
1
2
```
the expected output is:
```text
1 2
```

---
For:
```text
2 2
1 3
2 4
```
the expected output is:
```text
1 2 3 4
```

---
For:
```text
2 2
1 4
2 3
```
the expected output is:
```text
1 2 3 4
```

## Question 24

### Difficulty
Medium

### Bug Type
Binary Search Termination (`low <= high` vs `low < high`)

### Problem
Write a binary search that returns the key's index, or -1 when it is missing. When the range collapses to one element that is not the key, -1 must be returned.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int search(const vector<int>& arr, int key) {
    int low = 0, high = (int)arr.size() - 1;
    while (low < high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == key) return mid;
        if (arr[mid] < key) low = mid + 1;
        else high = mid - 1;
    }
    return low;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << search(arr, key) << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3
10 30 50
10
```
the expected output is:
```text
0
```

---
For:
```text
3
10 30 50
20
```
the expected output is:
```text
-1
```

---
For:
```text
3
10 30 50
40
```
the expected output is:
```text
-1
```

## Question 25

### Difficulty
Hard

### Bug Type
Binary Search First Occurrence Wrong Low Update

### Problem
Find the FIRST occurrence of a key in a sorted array using a binary search that records candidate answers. Once a match is recorded, the search must keep probing toward earlier occurrences, not toward later ones.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int firstOccurrence(const vector<int>& arr, int key) {
    int low = 0, high = (int)arr.size() - 1, ans = -1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == key) {
            ans = mid;
            low = mid + 1;
            high = mid - 1;
        } else if (arr[mid] < key) {
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }
    return ans;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << firstOccurrence(arr, key) << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
1 2 2 3
2
```
the expected output is:
```text
1
```

---
For:
```text
4
2 2 2 2
2
```
the expected output is:
```text
0
```

---
For:
```text
4
1 1 2 2
1
```
the expected output is:
```text
0
```

## Question 26

### Difficulty
Hard

### Bug Type
Median of Two Sorted Arrays Boundary Error

### Problem
Compute the median of two sorted arrays. For an even total size, the median is the average of the two middle elements.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int kthSmallest(const vector<int>& a, const vector<int>& b, int k) {
    int i = 0, j = 0;
    while (i + j < k) {
        if (j == (int)b.size() || (i < (int)a.size() && a[i] < b[j])) ++i;
        else ++j;
    }
    if (j == (int)b.size() || (i < (int)a.size() && a[i] < b[j])) return a[i];
    return b[j];
}

double findMedian(const vector<int>& a, const vector<int>& b) {
    int total = (int)a.size() + (int)b.size();
    if (total % 2 == 1) return kthSmallest(a, b, total / 2);
    int x = kthSmallest(a, b, total / 2);
    return (x + x) / 2.0;
}

int main() {
    int m, n;
    cin >> m >> n;
    vector<int> a(m), b(n);
    for (int i = 0; i < m; ++i) cin >> a[i];
    for (int i = 0; i < n; ++i) cin >> b[i];
    cout << findMedian(a, b) << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
2 1
1 3
2
```
the expected output is:
```text
2
```

---
For:
```text
2 2
1 2
3 4
```
the expected output is:
```text
2.5
```

---
For:
```text
0 4

1 2 3 4
```
the expected output is:
```text
2.5
```

## Question 27

### Difficulty
Hard

### Bug Type
Binary Search Midpoint Overflow `(low + high) / 2`

### Problem
Using binary search over a large numeric range, decide whether any perfect square lies between a and b (inclusive). The midpoint must be computed without overflowing the integer range.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

bool hasPerfectSquare(int a, int b) {
    int low = a, high = b;
    while (low <= high) {
        int mid = (low + high) / 2;
        long long sq = 1LL * mid * mid;
        if (sq < (long long)a) low = mid + 1;
        else if (sq > (long long)b) high = mid - 1;
        else return true;
    }
    return false;
}

int main() {
    int a, b;
    cin >> a >> b;
    cout << (hasPerfectSquare(a, b) ? "true" : "false") << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4 9
```
the expected output is:
```text
true
```

---
For:
```text
1200000000 1700000000
```
the expected output is:
```text
true
```

---
For:
```text
1500000000 1500000000
```
the expected output is:
```text
false
```

## Question 28

### Difficulty
Hard

### Bug Type
Bubble Sort Skipped Final Pass (n-2 vs n-1)

### Problem
Implement bubble sort so the whole array becomes sorted. An array of n elements may need up to n-1 sorting passes.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

void bubbleSort(vector<int>& arr) {
    int n = arr.size();
    for (int i = 0; i < n - 2; ++i) {
        for (int j = 0; j < n - 1; ++j) {
            if (arr[j] > arr[j + 1]) swap(arr[j], arr[j + 1]);
        }
    }
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    bubbleSort(arr);
    for (int i = 0; i < n; ++i) cout << arr[i] << " ";
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
2 1 3
```
the expected output is:
```text
1 2 3
```

---
For:
```text
3
3 2 1
```
the expected output is:
```text
1 2 3
```

---
For:
```text
4
4 3 2 1
```
the expected output is:
```text
1 2 3 4
```

## Question 29

### Difficulty
Hard

### Bug Type
Insertion Sort Overwrites Element

### Problem
Implement insertion sort. Before shifting larger elements right to make room for the current element, the current element must be saved in a separate variable so it is not lost.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

void insertionSort(vector<int>& arr) {
    for (int i = 1; i < (int)arr.size(); ++i) {
        int j = i - 1;
        while (j >= 0 && arr[j] > arr[i]) {
            arr[j + 1] = arr[j];
            --j;
        }
        arr[j + 1] = arr[i];
    }
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    insertionSort(arr);
    for (int i = 0; i < n; ++i) cout << arr[i] << " ";
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
1 2 3
```
the expected output is:
```text
1 2 3
```

---
For:
```text
3
5 3 4
```
the expected output is:
```text
3 4 5
```

---
For:
```text
3
3 1 2
```
the expected output is:
```text
1 2 3
```

## Question 30

### Difficulty
Hard

### Bug Type
Merge Sort Merge-Step Index Error

### Problem
Implement merge sort. During the merge step, elements copied back from the temporary buffer must be written to the same positions they came from in the original range.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

void merge(vector<int>& arr, int low, int mid, int high) {
    vector<int> temp(high - low + 1);
    int i = low, j = mid + 1, k = 0;
    while (i <= mid && j <= high) {
        if (arr[i] <= arr[j]) temp[k++] = arr[i++];
        else temp[k++] = arr[j++];
    }
    while (i <= mid) temp[k++] = arr[i++];
    while (j <= high) temp[k++] = arr[j++];
    for (int t = low; t <= high; ++t)
        arr[t] = temp[t];
}

void mergeSort(vector<int>& arr, int low, int high) {
    if (low >= high) return;
    int mid = low + (high - low) / 2;
    mergeSort(arr, low, mid);
    mergeSort(arr, mid + 1, high);
    merge(arr, low, mid, high);
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    mergeSort(arr, 0, n - 1);
    for (int i = 0; i < n; ++i) cout << arr[i] << " ";
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
2 1
```
the expected output is:
```text
1 2
```

---
For:
```text
4
4 3 2 1
```
the expected output is:
```text
1 2 3 4
```

---
For:
```text
5
7 2 9 1 5
```
the expected output is:
```text
1 2 5 7 9
```

## Question 31

### Difficulty
Hard

### Bug Type
Quick Sort Partition Pivot Swap Bug

### Problem
Implement quicksort using a Hoare-style partition. The inner comparisons must send elements smaller than the pivot to the left and larger elements to the right, then recurse on both sides.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int partition(vector<int>& arr, int low, int high) {
    int pivot = arr[low + (high - low) / 2];
    int i = low, j = high;
    while (i <= j) {
        while (arr[i] > pivot) ++i;
        while (arr[j] < pivot) --j;
        if (i <= j) {
            swap(arr[i], arr[j]);
            ++i;
            --j;
        }
    }
    return i;
}

void quickSort(vector<int>& arr, int low, int high) {
    if (low < high) {
        int p = partition(arr, low, high);
        quickSort(arr, low, p - 1);
        quickSort(arr, p, high);
    }
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    quickSort(arr, 0, n - 1);
    for (int i = 0; i < n; ++i) cout << arr[i] << " ";
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

---
For:
```text
5
5 3 8 1 6
```
the expected output is:
```text
1 3 5 6 8
```

---
For:
```text
3
3 1 2
```
the expected output is:
```text
1 2 3
```

## Question 32

### Difficulty
Hard

### Bug Type
Comparator Returns Wrong Sign (swap semantics)

### Problem
Sort students in DESCENDING order of score. If two scores are equal, sort by name in ascending order. The comparator must return true only when the first record should come before the second.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <string>
using namespace std;

struct Student {
    string name;
    int score;
};

int main() {
    int n;
    cin >> n;
    vector<Student> v(n);
    for (int i = 0; i < n; ++i) cin >> v[i].name >> v[i].score;
    sort(v.begin(), v.end(), [](const Student& x, const Student& y) {
        if (x.score != y.score) return x.score < y.score;
        return x.name < y.name;
    });
    for (int i = 0; i < n; ++i)
        cout << v[i].name << " " << v[i].score << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
2
Carla 90
Ana 90
```
the expected output is:
```text
Ana 90
Carla 90
```

---
For:
```text
2
Ana 85
Bob 95
```
the expected output is:
```text
Bob 95
Ana 85
```

---
For:
```text
3
Ana 90
Carla 90
Bob 95
```
the expected output is:
```text
Bob 95
Ana 90
Carla 90
```

## Question 33

### Difficulty
Hard

### Bug Type
2D Sorted Array Row Selection Bug

### Problem
Search a matrix where every row is sorted ascending (rows are not necessarily contiguous). Find the row that could contain the key by checking the key against BOTH the row's first and last element, then linear-search inside that row.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int searchMatrix(const vector<vector<int>>& m, int key) {
    int rows = (int)m.size(), cols = (int)m[0].size();
    int low = 0, high = rows - 1, row = -1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (key < m[mid][0]) high = mid - 1;
        else if (key > m[mid][0]) low = mid + 1;
        else { row = mid; break; }
    }
    if (row == -1) return -1;
    for (int c = 0; c < cols; ++c)
        if (m[row][c] == key) return row * cols + c;
    return -1;
}

int main() {
    int r, c;
    cin >> r >> c;
    vector<vector<int>> m(r, vector<int>(c));
    for (int i = 0; i < r; ++i)
        for (int j = 0; j < c; ++j)
            cin >> m[i][j];
    int key;
    cin >> key;
    cout << searchMatrix(m, key) << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
2 3
1 3 5
2 4 6
1
```
the expected output is:
```text
0
```

---
For:
```text
2 3
1 3 5
2 4 6
3
```
the expected output is:
```text
1
```

---
For:
```text
2 3
1 3 5
2 4 6
4
```
the expected output is:
```text
4
```

## Question 34

### Difficulty
Hard

### Bug Type
Search Where Key Equals Adjacent Values

### Problem
Write a function that reports true if the array contains two adjacent positions with equal values anywhere. The check must keep scanning after the first non-matching adjacent pair.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

bool hasAdjacentEqual(const vector<int>& arr) {
    for (int i = 0; i < (int)arr.size() - 1; ++i) {
        if (arr[i] != arr[i + 1]) return false;
    }
    return true;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    cout << (hasAdjacentEqual(arr) ? "true" : "false") << endl;
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
true
```

---
For:
```text
3
1 2 2
```
the expected output is:
```text
true
```

---
For:
```text
4
2 2 3 3
```
the expected output is:
```text
true
```

## Question 35

### Difficulty
Hard

### Bug Type
Two Related Bugs (bounds + comparison direction)

### Problem
Write a single pass that finds both the minimum and maximum of an array. Both values must be reported, and an element that improves one candidate must never stop the other candidate from being updated.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];

    int mn = 0, mx = 0;
    for (int i = 0; i < (int)arr.size(); ++i) {
        if (arr[i] < mn) mn = arr[i];
        else if (arr[i] > mx) mx = arr[i];
    }
    cout << mn << " " << mx << endl;
    return 0;
}
```

### Task
Find the bug(s) and correct the code.

### Expected Behavior

For:
```text
3
0 3 5
```
the expected output is:
```text
0 5
```

---
For:
```text
3
3 5 1
```
the expected output is:
```text
1 5
```

---
For:
```text
3
-5 -2 -9
```
the expected output is:
```text
-9 -2
```

# Solutions

## Solution 1

### Bug
The loop condition `i < (int)arr.size() - 1` stops one element before the end, so the last element is never examined.

### Explanation
For `arr = {1 2 3}` with key `3`, the loop tests only indices 0 and 1, returns -1 instead of 2. When the key sits at index 1 or earlier, it still works, which is why some inputs pass. Fix the loop to run while `i < arr.size()`.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int linearSearch(const vector<int>& arr, int key) {
    for (int i = 0; i < (int)arr.size(); ++i) {
        if (arr[i] == key) return i;
    }
    return -1;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << linearSearch(arr, key) << endl;
    return 0;
}
```

## Solution 2

### Bug
The swap condition `arr[j] < arr[j + 1]` bubbles the LARGER element to the front, producing descending order.

### Explanation
Every pass moves the largest value toward the left, so `{3 1 2}` becomes `{3 2 1}` instead of `{1 2 3}`. Single-element input like `{9}` is unaffected, which hides the fault. Swap when `arr[j] > arr[j + 1]`.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

void bubbleSort(vector<int>& arr) {
    int n = arr.size();
    for (int i = 0; i < n - 1; ++i) {
        for (int j = 0; j < n - i - 1; ++j) {
            if (arr[j] > arr[j + 1]) swap(arr[j], arr[j + 1]);
        }
    }
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    bubbleSort(arr);
    for (int i = 0; i < n; ++i) cout << arr[i] << " ";
    cout << endl;
    return 0;
}
```

## Solution 3

### Bug
Selection sort picks the index of the LARGEST element each pass (`arr[j] > arr[idx]`) instead of the smallest.

### Explanation
The wrong comparison direction means every pass places the biggest remaining value at the front, so the array ends up descending. `{4 2 5 1}` becomes `{5 4 2 1}` instead of `{1 2 4 5}`. Use `arr[j] < arr[idx]`.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

void selectionSort(vector<int>& arr) {
    int n = arr.size();
    for (int i = 0; i < n - 1; ++i) {
        int idx = i;
        for (int j = i + 1; j < n; ++j) {
            if (arr[j] < arr[idx]) idx = j;
        }
        swap(arr[i], arr[idx]);
    }
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    selectionSort(arr);
    for (int i = 0; i < n; ++i) cout << arr[i] << " ";
    cout << endl;
    return 0;
}
```

## Solution 4

### Bug
Operator precedence makes `mid = low + high / 2` compute `low + (high / 2)` instead of `(low + high) / 2`.

### Explanation
Because `/` binds tighter than `+`, the midpoint is skewed toward `low`. For `{1 3 5 7}` key `5`: mid is 1, then 3, and the search converges to -1 even though 5 is at index 2. Keys near the front (key `3`) still work. Use `mid = low + (high - low) / 2`.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int binarySearch(const vector<int>& arr, int key) {
    int low = 0, high = (int)arr.size() - 1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == key) return mid;
        if (arr[mid] < key) low = mid + 1;
        else high = mid - 1;
    }
    return -1;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << binarySearch(arr, key) << endl;
    return 0;
}
```

## Solution 5

### Bug
The `else index = -1;` branch erases the stored match whenever a later element differs from the key.

### Explanation
Only a match on the very last element survives; any earlier match is reset to -1. `{10 20 30}` key `20` returns -1 because index 2 overwrites it. Return immediately (or break) when a match is found.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int linearSearch(const vector<int>& arr, int key) {
    int index = -1;
    for (int i = 0; i < (int)arr.size(); ++i) {
        if (arr[i] == key) {
            index = i;
            break;
        }
    }
    return index;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << linearSearch(arr, key) << endl;
    return 0;
}
```

## Solution 6

### Bug
The loop runs `while (low < high)` and there is no final check on the single remaining element, so `search` returns -1 even when the key is present.

### Explanation
When the range collapses to `low == high`, the loop exits without inspecting that position. `{5 10 15}` key `5`: mid = 1, high becomes 0, then the loop ends and -1 is returned even though arr[0] holds 5. Either loop with `low <= high` or add `if (arr[low] == key) return low;` before returning -1.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int search(const vector<int>& arr, int key) {
    int low = 0, high = (int)arr.size() - 1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == key) return mid;
        if (arr[mid] < key) low = mid + 1;
        else high = mid - 1;
    }
    return -1;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << search(arr, key) << endl;
    return 0;
}
```

## Solution 7

### Bug
The inner loop bubbles the current element toward the RIGHT (`++j`, bounded by `n - 2`) instead of shifting it LEFT toward its sorted position.

### Explanation
Insertion sort must pull the new element down into the already-sorted prefix, but this code swaps it forward. `{4 3 2 1}` becomes `{3 2 4 1}`. Already-sorted input such as `{1 2 3}` is untouched, hiding the fault. The inner walk must go `j = i - 1` while `j >= 0` and `--j` after each shift.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

void insertionSort(vector<int>& arr) {
    for (int i = 1; i < (int)arr.size(); ++i) {
        int key = arr[i];
        int j = i - 1;
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            --j;
        }
        arr[j + 1] = key;
    }
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    insertionSort(arr);
    for (int i = 0; i < n; ++i) cout << arr[i] << " ";
    cout << endl;
    return 0;
}
```

## Solution 8

### Bug
`pos` keeps being overwritten on every matching element because there is no `break`, so the LAST occurrence index is returned.

### Explanation
With a single occurrence, early and late indexing coincide and the result looks correct `({1 4 5}` key `4` -> 1). With duplicates, `{1 4 4 5}` key `4` returns 2 instead of 1. Stop searching after the first match.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int firstOccurrence(const vector<int>& arr, int key) {
    for (int i = 0; i < (int)arr.size(); ++i) {
        if (arr[i] == key) return i;
    }
    return -1;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << firstOccurrence(arr, key) << endl;
    return 0;
}
```

## Solution 9

### Bug
The outer loop runs exactly once (`for (int i = 0; i < 1; ++i)`), so only a single bubble pass is performed.

### Explanation
One pass moves only the largest element to the end. `{3 2 1}` becomes `{2 1 3}` after a single pass; n-1 passes are needed. Input like `{2 1 3}` is coincidentally sorted after one pass, hiding the fault. Loop `i` from 0 to `n - 2`.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

void bubbleSort(vector<int>& arr) {
    int n = arr.size();
    for (int i = 0; i < n - 1; ++i) {
        for (int j = 0; j < n - 1; ++j) {
            if (arr[j] > arr[j + 1]) swap(arr[j], arr[j + 1]);
        }
    }
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    bubbleSort(arr);
    for (int i = 0; i < n; ++i) cout << arr[i] << " ";
    cout << endl;
    return 0;
}
```

## Solution 10

### Bug
The loop updates `minVal`, but `minIdx` is never changed, so the swap exchanges `arr[i]` with itself.

### Explanation
The code records the value but not where it lives, so selection sort performs no useful swaps. Already-sorted input `{1 2 3}` looks correct; `{3 1 2}` stays `{3 1 2}`. Update `minIdx = j` inside the condition, exactly as `minVal` is updated.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

void selectionSort(vector<int>& arr) {
    int n = arr.size();
    for (int i = 0; i < n - 1; ++i) {
        int minIdx = i;
        for (int j = i + 1; j < n; ++j) {
            if (arr[j] < arr[minIdx]) minIdx = j;
        }
        swap(arr[i], arr[minIdx]);
    }
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    selectionSort(arr);
    for (int i = 0; i < n; ++i) cout << arr[i] << " ";
    cout << endl;
    return 0;
}
```

## Solution 11

### Bug
On the `else` side the update is `high = mid` instead of `high = mid - 1`, so the upper bound never moves below the midpoint when the key is absent.

### Explanation
Highlighting an absent key such as 25 in `{10 20 30 40}`: mid stays 2 with `low = 2, high = 2`, and because `high = mid` keeps the same pair, the loop spins forever. Present keys still terminate, so a happy-path test passes. Use `high = mid - 1`.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int binarySearch(const vector<int>& arr, int key) {
    int low = 0, high = (int)arr.size() - 1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == key) return mid;
        if (arr[mid] < key) low = mid + 1;
        else high = mid - 1;
    }
    return -1;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << binarySearch(arr, key) << endl;
    return 0;
}
```

## Solution 12

### Bug
On the `else` side the update is `low = mid` instead of `low = mid + 1`.

### Explanation
For `{10 20 30}` key `30`: mid = 1, `20 < 30` so `low = mid = 1`, and mid is recomputed as 1 repeatedly, so the range never shrinks and the loop never terminates even though 30 is present. The key 20 sits exactly on the first midpoint and hides the bug. Advance past the midpoint with `low = mid + 1`.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int binarySearch(const vector<int>& arr, int key) {
    int low = 0, high = (int)arr.size() - 1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == key) return mid;
        if (arr[mid] < key) low = mid + 1;
        else high = mid - 1;
    }
    return -1;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << binarySearch(arr, key) << endl;
    return 0;
}
```

## Solution 13

### Bug
When the key never appears, both `first` and `last` stay -1 and `last - first + 1` evaluates to `-1 - (-1) + 1 = 1`.

### Explanation
The formula assumes a match always exists. For `{1 2 3}` key `5`, the correct answer is 0 but the code prints 1. Present keys like `2` in `{1 2 2 3}` print the right count and hide the fault. Return 0 when `first` is still -1.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int countKey(const vector<int>& arr, int key) {
    int first = -1, last = -1;
    for (int i = 0; i < (int)arr.size(); ++i) {
        if (arr[i] == key && first == -1) first = i;
        if (arr[i] == key) last = i;
    }
    if (first == -1) return 0;
    return last - first + 1;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << countKey(arr, key) << endl;
    return 0;
}
```

## Solution 14

### Bug
The first-occurrence check tests the element on the RIGHT (``arr[mid + 1] > key``) instead of the one on the LEFT, which is the last-occurrence rule.

### Explanation
To confirm a match at `mid` is the FIRST occurrence you must verify no copy exists before it (`mid == 0 || arr[mid - 1] < key`). With the right-side test, `{1 2 2 3}` key `2`: mid = 1 matches, arr[2] is also 2 and not greater, so the search discards the left half and returns -1. When the key appears once the two rules coincide and the test passes.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int firstOccurrence(const vector<int>& arr, int key) {
    int low = 0, high = (int)arr.size() - 1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == key &&
            (mid == 0 || arr[mid - 1] < key))
            return mid;
        if (arr[mid] < key) low = mid + 1;
        else high = mid - 1;
    }
    return -1;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << firstOccurrence(arr, key) << endl;
    return 0;
}
```

## Solution 15

### Bug
When the left half is sorted and the key belongs inside it, the code sets `low = mid + 1`, pushing the search OUT of the only half containing the key.

### Explanation
Narrowing toward the left half requires `high = mid - 1`. As written, `{4 5 6 7 0 1 2}` key `5` keeps shifting the window right into `{0 1 2}` and returns -1 instead of 1. A key that lands exactly on a midpoint, like 7, still returns correct.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int search(const vector<int>& arr, int key) {
    int low = 0, high = (int)arr.size() - 1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == key) return mid;
        if (arr[low] <= arr[mid]) {
            if (key >= arr[low] && key < arr[mid]) high = mid - 1;
            else low = mid + 1;
        } else {
            if (key > arr[mid] && key <= arr[high]) low = mid + 1;
            else high = mid - 1;
        }
    }
    return -1;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << search(arr, key) << endl;
    return 0;
}
```

## Solution 16

### Bug
The two moves are swapped: when the cell is too large the code goes DOWN (`++row`) and when it is too small it goes LEFT (`--col`), instead of left and down respectively.

### Explanation
A cell bigger than the key means the entire column below is bigger, so we must move left; a smaller cell means the whole row to the left is smaller, so we must move down. With the swapped logic, `{1 3 5},{2 4 6}` key `4` walks off the bottom and reports false. Key `5` is reached immediately and hides the fault.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

bool searchMatrix(const vector<vector<int>>& m, int key) {
    int row = 0, col = (int)m[0].size() - 1;
    while (row < (int)m.size() && col >= 0) {
        int v = m[row][col];
        if (v == key) return true;
        if (v > key) --col;
        else ++row;
    }
    return false;
}

int main() {
    int rows, cols;
    cin >> rows >> cols;
    vector<vector<int>> m(rows, vector<int>(cols));
    for (int i = 0; i < rows; ++i)
        for (int j = 0; j < cols; ++j)
            cin >> m[i][j];
    int key;
    cin >> key;
    cout << (searchMatrix(m, key) ? "true" : "false") << endl;
    return 0;
}
```

## Solution 17

### Bug
The branch `else high = mid - 1;` reduces the upper bound below the midpoint, but lower-bound logic must keep every `>= key` element in range, i.e. `high = mid`.

### Explanation
For `{1 3 3 5 7}` key `7`: mid = 4 holds 7, and `arr[4] < 7` is false, so `high = 3` — the only valid insertion position 4 is cut out, giving 3. Duplicated keys such as `3` land behind the fix's working midpoint in early iterations but still pass, so happy-path runs look fine.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int lowerBound(const vector<int>& arr, int key) {
    int low = 0, high = (int)arr.size();
    while (low < high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] < key) low = mid + 1;
        else high = mid;
    }
    return low;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << lowerBound(arr, key) << endl;
    return 0;
}
```

## Solution 18

### Bug
The scan returns `i` at the first position with `arr[i] > arr[i + 1]` and never inspects the last element, so a strictly increasing array reports no peak.

### Explanation
`{1 2 3}` has a peak at index 2 (edge rule), but the loop only covers indices 0 and 1 and ends in -1. `{1 3 2}` returns 1 correctly because the first descent happens at a real peak. The loop should also test the final element, e.g. a full scan checking both neighbors.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int findPeak(const vector<int>& arr) {
    int n = (int)arr.size();
    for (int i = 0; i < n; ++i) {
        bool leftOk = (i == 0) || (arr[i] >= arr[i - 1]);
        bool rightOk = (i == n - 1) || (arr[i] >= arr[i + 1]);
        if (leftOk && rightOk) return i;
    }
    return -1;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    cout << findPeak(arr) << endl;
    return 0;
}
```

## Solution 19

### Bug
For an ascending array the branch `if (arr[mid] < key)` must move the LOWER bound up (`low = mid + 1`), but the code moves the upper bound down as if the data were sorted descending.

### Explanation
`{10 20 30}` key `30`: mid = 1, `20 < 30` so high collapses to -1 and the search reports -1 instead of 2; key `10` similarly reports -1 instead of 0. The key 20 equals the first midpoint, so a single happy-path test passes.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int binarySearch(const vector<int>& arr, int key) {
    int low = 0, high = (int)arr.size() - 1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == key) return mid;
        if (arr[mid] < key) low = mid + 1;
        else high = mid - 1;
    }
    return -1;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << binarySearch(arr, key) << endl;
    return 0;
}
```

## Solution 20

### Bug
The comparator `return a < b;` sorts by numeric value, ignoring the absolute-value modifier entirely.

### Explanation
Ascending numeric order differs from ascending |x| order as soon as negatives appear. `{-5 2 -1 4}` sorts to `{-5 -1 2 4}` but should be `{-1 2 4 -5}` (absolute values 1, 2, 4, 5). All-positive input matches the intended order, so it hides the fault. Compare `std::abs(a)` against `std::abs(b)`.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <cstdlib>
using namespace std;

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    sort(arr.begin(), arr.end(),
         [](int a, int b) { return abs(a) < abs(b); });
    for (int i = 0; i < n; ++i) cout << arr[i] << " ";
    cout << endl;
    return 0;
}
```

## Solution 21

### Bug
The inner counting loop runs `j < (int)arr.size() - 1`, so the last element never contributes to any count.

### Explanation
`{1 1 2}` with k = 3 should be 2, but every pass counts only the first two elements, so the loop exhausts MAXV and returns -1; a single-element array `{5}` returns -1 for any k because the inner loop never executes. Small k values hit the return before the missing element matters, which is why k = 2 passes.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

const int MAXV = 100;

int kthSmallest(const vector<int>& arr, int k) {
    for (int i = 1; i <= MAXV; ++i) {
        int cnt = 0;
        for (int j = 0; j < (int)arr.size(); ++j)
            if (arr[j] <= i) ++cnt;
        if (cnt >= k) return i;
    }
    return -1;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int k;
    cin >> k;
    cout << kthSmallest(arr, k) << endl;
    return 0;
}
```

## Solution 22

### Bug
The inner loop stops at `j < (int)arr.size() - 1`, so no pair whose second element is the last array entry is ever counted.

### Explanation
`{2 2 3 2}` has three duplicate pairs ((0,1), (0,3), (1,3)) but the code counts only 1 because j never reaches index 3. When the last element is irrelevant to the duplicates, e.g. `{3 1 3 5}`, the count is correct and hides the fault. Run j up to `arr.size()`.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int countDuplicatePairs(const vector<int>& arr) {
    int pairs = 0;
    for (int i = 0; i < (int)arr.size(); ++i) {
        for (int j = i + 1; j < (int)arr.size(); ++j) {
            if (arr[i] == arr[j]) ++pairs;
        }
    }
    return pairs;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    cout << countDuplicatePairs(arr) << endl;
    return 0;
}
```

## Solution 23

### Bug
Writing an element from the second array uses `c[++k]`, so the write cursor jumps over position `k` on that store.

### Explanation
Each store must advance the cursor exactly once; `c[++k]` pre-increments, leaving an unwritten slot. For `{1 3}` and `{2 4}` the merged array becomes `{1 0 3 4}` instead of `{1 2 3 4}`. When fewer than two elements cross the boundary (e.g. `{1}` and `{2}`), no slot is skipped and the output is correct.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

vector<int> mergeSorted(const vector<int>& a, const vector<int>& b) {
    int i = 0, j = 0, k = 0;
    vector<int> c(a.size() + b.size());
    while (i < (int)a.size() && j < (int)b.size()) {
        if (a[i] <= b[j]) c[k++] = a[i++];
        else c[k++] = b[j++];
    }
    while (i < (int)a.size()) c[k++] = a[i++];
    while (j < (int)b.size()) c[k++] = b[j++];
    return c;
}

int main() {
    int m, n;
    cin >> m >> n;
    vector<int> a(m), b(n);
    for (int i = 0; i < m; ++i) cin >> a[i];
    for (int i = 0; i < n; ++i) cin >> b[i];
    vector<int> c = mergeSorted(a, b);
    for (int i = 0; i < (int)c.size(); ++i) cout << c[i] << " ";
    cout << endl;
    return 0;
}
```

## Solution 24

### Bug
The loop terminates with `low < high` and, on exit, blindly returns `low` without verifying that `arr[low] == key`.

### Explanation
Because the loop never re-tests the single remaining cell, a missing key is reported as its would-be insertion point. For `{10 30 50}` key `20`, the code returns 0; key `40` returns 2. Present keys that happen to end in that cell (e.g. key `10` in the example) come out correct. Return -1 unless `arr[low] == key`.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int search(const vector<int>& arr, int key) {
    int low = 0, high = (int)arr.size() - 1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == key) return mid;
        if (arr[mid] < key) low = mid + 1;
        else high = mid - 1;
    }
    return -1;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << search(arr, key) << endl;
    return 0;
}
```

## Solution 25

### Bug
After recording a match (`ans = mid`) the code does `low = mid + 1`, which steers the search toward LATER occurrences instead of earlier ones.

### Explanation
After a match, first-occurrence logic must probe LEFT by setting `high = mid - 1`, leaving low alone. Advancing low makes `{2 2 2 2}` return index 1 rather than 0. When duplicates are few and asymmetric, e.g. `{1 2 2 3}`, the naturally-hit midpoint is already the first occurrence, so the test passes.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int firstOccurrence(const vector<int>& arr, int key) {
    int low = 0, high = (int)arr.size() - 1, ans = -1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == key) {
            ans = mid;
            high = mid - 1;
        } else if (arr[mid] < key) {
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }
    return ans;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    int key;
    cin >> key;
    cout << firstOccurrence(arr, key) << endl;
    return 0;
}
```

## Solution 26

### Bug
For an even total, the median must average the elements at `total/2 - 1` and `total/2`; the code fetches `total/2` twice.

### Explanation
`{1 2}` and `{3 4}` should give (2 + 3) / 2 = 2.5, but the code returns 3.0. Odd-size inputs use only the middle element, so the median is still right and the boundary bug stays hidden. Fetch both middle elements, or use k = `total/2 - 1` and k = `total/2`.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int kthSmallest(const vector<int>& a, const vector<int>& b, int k) {
    int i = 0, j = 0;
    while (i + j < k) {
        if (j == (int)b.size() || (i < (int)a.size() && a[i] < b[j])) ++i;
        else ++j;
    }
    if (j == (int)b.size() || (i < (int)a.size() && a[i] < b[j])) return a[i];
    return b[j];
}

double findMedian(const vector<int>& a, const vector<int>& b) {
    int total = (int)a.size() + (int)b.size();
    if (total == 0) return 0;
    if (total % 2 == 1) return kthSmallest(a, b, total / 2);
    int x = kthSmallest(a, b, total / 2 - 1);
    int y = kthSmallest(a, b, total / 2);
    return (x + y) / 2.0;
}

int main() {
    int m, n;
    cin >> m >> n;
    vector<int> a(m), b(n);
    for (int i = 0; i < m; ++i) cin >> a[i];
    for (int i = 0; i < n; ++i) cin >> b[i];
    cout << findMedian(a, b) << endl;
    return 0;
}
```

## Solution 27

### Bug
`int mid = (low + high) / 2;` can overflow when `low + high` exceeds `INT_MAX`, producing a wrapped negative midpoint.

### Explanation
For `a = 1200000000, b = 1700000000`, the sum 2,900,000,000 exceeds INT_MAX (2,147,483,647), wraps negative, and the search collapses instantly to false even though 34642^2 = 1,200,068,164 lies in range. Small ranges such as `4 9` never overflow and hide the fault. Compute the midpoint as `low + (high - low) / 2`, which cannot overflow.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

bool hasPerfectSquare(int a, int b) {
    int low = a, high = b;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        long long sq = 1LL * mid * mid;
        if (sq < (long long)a) low = mid + 1;
        else if (sq > (long long)b) high = mid - 1;
        else return true;
    }
    return false;
}

int main() {
    int a, b;
    cin >> a >> b;
    cout << (hasPerfectSquare(a, b) ? "true" : "false") << endl;
    return 0;
}
```

## Solution 28

### Bug
The outer loop runs `for (int i = 0; i < n - 2; ++i)`, executing only n - 2 passes instead of the n - 1 passes bubble sort may need.

### Explanation
Bubble sort guarantees completion only after n - 1 passes. With the last pass skipped, `{3 2 1}` settles at `{2 1 3}` and `{4 3 2 1}` at `{2 1 3 4}`. Input where one pass suffices, like `{2 1 3}`, comes out sorted. Use `i < n - 1`.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

void bubbleSort(vector<int>& arr) {
    int n = arr.size();
    for (int i = 0; i < n - 1; ++i) {
        for (int j = 0; j < n - 1; ++j) {
            if (arr[j] > arr[j + 1]) swap(arr[j], arr[j + 1]);
        }
    }
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    bubbleSort(arr);
    for (int i = 0; i < n; ++i) cout << arr[i] << " ";
    cout << endl;
    return 0;
}
```

## Solution 29

### Bug
The current element is never saved; `arr[i]` is read again after shifting has already overwritten it.

### Explanation
The first shift `arr[j + 1] = arr[j]` with `j = i - 1` destroys `arr[i]` before it can be re-inserted. `{5 3 4}` degrades to `{5 5 5}` and `{3 1 2}` to `{3 3 3}`. When no shift is needed (already-sorted input), `arr[i]` is untouched and the output is still correct. Cache the element in `int key = arr[i]` before the inner loop.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

void insertionSort(vector<int>& arr) {
    for (int i = 1; i < (int)arr.size(); ++i) {
        int key = arr[i];
        int j = i - 1;
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            --j;
        }
        arr[j + 1] = key;
    }
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    insertionSort(arr);
    for (int i = 0; i < n; ++i) cout << arr[i] << " ";
    cout << endl;
    return 0;
}
```

## Solution 30

### Bug
During the copy-back the code uses `arr[t] = temp[t]`, but `temp` is indexed from 0 while the range starts at `low`; it should be `temp[t - low]`.

### Explanation
Pooled regions whose `low` is not 0 (any right-half merge) read uninitialized zeroes from `temp`. `{4 3 2 1}` becomes `{0 0 3 4}` and `{7 2 9 1 5}` becomes `{0 0 5 0 7}`. A two-element array merges with `low = 0`, so the indices line up and the output is correct. Copy with offset `temp[t - low]`.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

void merge(vector<int>& arr, int low, int mid, int high) {
    vector<int> temp(high - low + 1);
    int i = low, j = mid + 1, k = 0;
    while (i <= mid && j <= high) {
        if (arr[i] <= arr[j]) temp[k++] = arr[i++];
        else temp[k++] = arr[j++];
    }
    while (i <= mid) temp[k++] = arr[i++];
    while (j <= high) temp[k++] = arr[j++];
    for (int t = low; t <= high; ++t)
        arr[t] = temp[t - low];
}

void mergeSort(vector<int>& arr, int low, int high) {
    if (low >= high) return;
    int mid = low + (high - low) / 2;
    mergeSort(arr, low, mid);
    mergeSort(arr, mid + 1, high);
    merge(arr, low, mid, high);
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    mergeSort(arr, 0, n - 1);
    for (int i = 0; i < n; ++i) cout << arr[i] << " ";
    cout << endl;
    return 0;
}
```

## Solution 31

### Bug
The Hoare partition inner loops use the reversed relations (`arr[i] > pivot` and `arr[j] < pivot`), so the split order is backwards; the fix must also use `quickSort(arr, low, p - 1)` on the left half.

### Explanation
Correct Hoare partition advances `i` while `arr[i] < pivot` and `j` while `arr[j] > pivot`. With the relations flipped, `{5 3 8 1 6}` comes out as `{8 6 5 3 1}` (essentially descending) instead of `{1 3 5 6 8}`; a single-element input bypasses all recursion, so that trivial test passes. Swap the comparison directions and recurse left on `p - 1`.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int partition(vector<int>& arr, int low, int high) {
    int pivot = arr[low + (high - low) / 2];
    int i = low, j = high;
    while (i <= j) {
        while (arr[i] < pivot) ++i;
        while (arr[j] > pivot) --j;
        if (i <= j) {
            swap(arr[i], arr[j]);
            ++i;
            --j;
        }
    }
    return i;
}

void quickSort(vector<int>& arr, int low, int high) {
    if (low < high) {
        int p = partition(arr, low, high);
        quickSort(arr, low, p - 1);
        quickSort(arr, p, high);
    }
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    quickSort(arr, 0, n - 1);
    for (int i = 0; i < n; ++i) cout << arr[i] << " ";
    cout << endl;
    return 0;
}
```

## Solution 32

### Bug
The comparator returns `x.score < y.score`, which sorts ascending by score, but the required order is descending.

### Explanation
For `Ana 85` and `Bob 95` the correct output is Bob first (95 > 85), yet the code prints Ana first. When the two scores are equal (both 90), only the name tie-break applies and both the intended and actual orders agree, so that test passes. Return `x.score > y.score`.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <string>
using namespace std;

struct Student {
    string name;
    int score;
};

int main() {
    int n;
    cin >> n;
    vector<Student> v(n);
    for (int i = 0; i < n; ++i) cin >> v[i].name >> v[i].score;
    sort(v.begin(), v.end(), [](const Student& x, const Student& y) {
        if (x.score != y.score) return x.score > y.score;
        return x.name < y.name;
    });
    for (int i = 0; i < n; ++i)
        cout << v[i].name << " " << v[i].score << endl;
    return 0;
}
```

## Solution 33

### Bug
The row-selection binary search compares `key` against `m[mid][0]` on both sides, so it can only ever lock onto a row whose FIRST element equals the key.

### Explanation
Testing `key > m[mid][0]` again is not a containment test; the correct second comparison is against the row's last element, `m[mid][cols - 1]`. For `{1 3 5},{2 4 6}` key `3` lives in row 0 but lies between rows' first elements, so `row` never gets set and the code returns -1 (expected 1). A key at a row start, like 1, matches and hides the bug.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int searchMatrix(const vector<vector<int>>& m, int key) {
    int rows = (int)m.size(), cols = (int)m[0].size();
    int low = 0, high = rows - 1, row = -1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (key < m[mid][0]) high = mid - 1;
        else if (key > m[mid][cols - 1]) low = mid + 1;
        else { row = mid; break; }
    }
    if (row == -1) return -1;
    for (int c = 0; c < cols; ++c)
        if (m[row][c] == key) return row * cols + c;
    return -1;
}

int main() {
    int r, c;
    cin >> r >> c;
    vector<vector<int>> m(r, vector<int>(c));
    for (int i = 0; i < r; ++i)
        for (int j = 0; j < c; ++j)
            cin >> m[i][j];
    int key;
    cin >> key;
    cout << searchMatrix(m, key) << endl;
    return 0;
}
```

## Solution 34

### Bug
`if (arr[i] != arr[i + 1]) return false;` aborts the scan at the FIRST unequal adjacent pair, so later equal pairs are never seen.

### Explanation
`{1 2 2}` has an equal pair at indices 1 and 2, but the scan returns false at the (0,1) difference. The function only reports true when the WHOLE array is homogeneous (`{2 2 2}`), which is exactly the case that hides the fault. Return true as soon as an equal pair is found.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

bool hasAdjacentEqual(const vector<int>& arr) {
    for (int i = 0; i < (int)arr.size() - 1; ++i) {
        if (arr[i] == arr[i + 1]) return true;
    }
    return false;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];
    cout << (hasAdjacentEqual(arr) ? "true" : "false") << endl;
    return 0;
}
```

## Solution 35

### Bug
Two related bugs: (1) `mn` and `mx` seed incorrectly on 0 instead of `arr[0]`, so values below/above 0 are never candidates; (2) `else if` means an element that updates the min can never also update the max on the same iteration.

### Explanation
Bug (1) makes all-negative `{-5 -2 -9}` report min -9 but "max" 0 (no element exceeds 0). Bug (2) is masked here because max already stuck at 0, but it surfaces in `{3 5 1}` where the true min 1 never beats the seed 0, and the else-if blocks any comparison chain on the same element. Seed both candidates from `arr[0]` and use two independent `if` statements so both candidates can update.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) cin >> arr[i];

    int mn = arr[0], mx = arr[0];
    for (int i = 1; i < (int)arr.size(); ++i) {
        if (arr[i] < mn) mn = arr[i];
        if (arr[i] > mx) mx = arr[i];
    }
    cout << mn << " " << mx << endl;
    return 0;
}
```