# C++ Debugging — Mixed Debugging

## Question 1

### Difficulty
Medium

### Bug Type
Mixed: array + loop (average divided by a fixed-sized denominator)

### Problem
Write a program that reads an array of integers and computes the average (mean) of only the even numbers present in the array. If the array is empty, the average is reported as 0.0. The result is printed as a single floating point value. The program must be able to handle multiple test cases until the input ends.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

double averageEven(const vector<int>& data) {
    if (data.empty()) return 0.0;
    long long sum = 0;
    int evenCount = 0;
    for (size_t i = 0; i < data.size(); ++i) {
        if (data[i] % 2 == 0) {
            sum += data[i];
            evenCount++;
        }
    }
    return static_cast<double>(sum) / data.size();
}

int main() {
    int n;
    while (cin >> n) {
        vector<int> data(n);
        for (int i = 0; i < n; ++i) cin >> data[i];
        cout << averageEven(data) << endl;
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
2 4 6
```
the expected output is:
```text
4
```

For:
```text
5
10 20 30 40 50
```
the expected output is:
```text
30
```

For:
```text
4
1 3 5 7
```
the expected output is:
```text
0
```

---

## Question 2

### Difficulty
Medium

### Bug Type
Mixed: string frequency array + mismatched-condition check

### Problem
Write a program that reads two lowercase strings and prints "yes" if they are anagrams of each other (contain exactly the same characters with the same frequencies), otherwise prints "no". The approach uses a fixed 26-slot frequency array: increment for every character of the first string, decrement for every character of the second, then verify that the array is all zero.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

bool isAnagram(const string& a, const string& b) {
    int freq[26] = {0};
    for (size_t i = 0; i < a.size(); ++i) freq[a[i] - 'a']++;
    for (size_t i = 0; i < b.size(); ++i) freq[b[i] - 'a']--;

    int mismatches = 0;
    for (int i = 0; i < 26; ++i)
        if (freq[i] > 0) mismatches++;

    return mismatches == 0;
}

int main() {
    string a, b;
    while (cin >> a >> b)
        cout << (isAnagram(a, b) ? "yes" : "no") << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
listen silent
```
the expected output is:
```text
yes
```

For:
```text
hello world
```
the expected output is:
```text
no
```

For:
```text
apple paple
```
the expected output is:
```text
yes
```

---

## Question 3

### Difficulty
Medium

### Bug Type
Mixed: sorting + comparison function tie-break error

### Problem
Write a program that reads a list of names and sorts them by length in descending order (longest first). Names of equal length must appear in alphabetical (lexicographic) ascending order among themselves. The sorted list is printed on a single line. The program uses a custom comparison function passed to `std::sort`.

### Buggy Code

```cpp
#include <iostream>
#include <string>
#include <vector>
#include <algorithm>
using namespace std;

bool lengthDesc(const string& x, const string& y) {
    if (x.size() != y.size()) return x.size() > y.size();
    return y < x;
}

int main() {
    int n;
    while (cin >> n) {
        vector<string> names(n);
        for (int i = 0; i < n; ++i) cin >> names[i];
        sort(names.begin(), names.end(), lengthDesc);
        for (size_t i = 0; i < names.size(); ++i) cout << names[i] << " ";
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
apple fig watermelon
```
the expected output is:
```text
watermelon apple fig 
```

For:
```text
2
hi programming
```
the expected output is:
```text
programming hi 
```

For:
```text
3
mango lime fig
```
the expected output is:
```text
mango lime fig 
```

---

## Question 4

### Difficulty
Medium

### Bug Type
Mixed: pointer arithmetic + loop bound error

### Problem
Write a program that reads an array of integers and reverses it in place using pointer arithmetic (the swap is performed through `*(arr + i)` and `*(arr + n - 1 - i)`). The reversed array is then printed. The program must handle multiple test cases.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

void reverseArray(int arr[], int n) {
    for (int i = 0; i <= n / 2; ++i) {
        int temp = *(arr + i);
        *(arr + i) = *(arr + n - 1 - i);
        *(arr + n - 1 - i) = temp;
    }
}

int main() {
    int n;
    while (cin >> n) {
        int arr[100];
        for (int i = 0; i < n; ++i) cin >> arr[i];
        reverseArray(arr, n);
        for (int i = 0; i < n; ++i) cout << arr[i] << " ";
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
1
42
```
the expected output is:
```text
42 
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

## Question 5

### Difficulty
Medium

### Bug Type
Mixed: linear search + loop boundary condition

### Problem
Write a program that reads an array and a target value, then prints the index of the first occurrence of the target followed by the index of its last occurrence. If the target is absent, both values are printed as -1. The first occurrence is located with a forward scan and the last occurrence with a backward scan.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int lastOccurrence(const vector<int>& a, int target) {
    for (int i = (int)a.size() - 1; i > 0; --i)
        if (a[i] == target) return i;
    return -1;
}

int main() {
    int n, target;
    while (cin >> n >> target) {
        vector<int> a(n);
        for (int i = 0; i < n; ++i) cin >> a[i];

        int first = -1;
        for (int i = 0; i < n; ++i)
            if (a[i] == target) { first = i; break; }

        int last = lastOccurrence(a, target);
        cout << first << " " << last << endl;
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
5 3
1 2 3 3 4
```
the expected output is:
```text
2 3
```

For:
```text
4 7
1 2 4 5
```
the expected output is:
```text
-1 -1
```

For:
```text
3 1
1 1 1
```
the expected output is:
```text
0 2
```

---

## Question 6

### Difficulty
Hard

### Bug Type
Mixed: recursion + incorrect base-case return value

### Problem
Write a program that reads an array of integers and prints the product of all of its elements. The product is computed with a recursive helper function that multiplies the current element by the result of processing the rest of the array. The recursion stops when the current index reaches the end of the array.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

long long product(const vector<int>& a, size_t i) {
    if (i == a.size()) return 0;
    return a[i] * product(a, i + 1);
}

int main() {
    int n;
    while (cin >> n) {
        vector<int> a(n);
        for (int i = 0; i < n; ++i) cin >> a[i];
        cout << product(a, 0) << endl;
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
2 0 4
```
the expected output is:
```text
0
```

For:
```text
2
0 9
```
the expected output is:
```text
0
```

For:
```text
1
0
```
the expected output is:
```text
0
```

---

## Question 7

### Difficulty
Hard

### Bug Type
Mixed: hashing + wrong scan direction for the frequency map

### Problem
Write a program that reads a lowercase string and returns the index of the first non-repeating character (a character that appears exactly once in the string). If every character repeats, the program prints -1. The frequency of each character is collected with an `unordered_map`, then the string is scanned to locate the first character whose count equals 1.

### Buggy Code

```cpp
#include <iostream>
#include <string>
#include <unordered_map>
using namespace std;

int firstUnique(const string& s) {
    unordered_map<char, int> count;
    for (size_t i = 0; i < s.size(); ++i) count[s[i]]++;

    for (int i = (int)s.size() - 1; i >= 0; --i)
        if (count[s[i]] == 1) return i;

    return -1;
}

int main() {
    string s;
    while (cin >> s)
        cout << firstUnique(s) << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
abcab
```
the expected output is:
```text
2
```

For:
```text
a
```
the expected output is:
```text
0
```

For:
```text
aaaaaa
```
the expected output is:
```text
-1
```

---

## Question 8

### Difficulty
Hard

### Bug Type
Mixed: linked list + node step-skipping in the duplicate-removal loop

### Problem
Write a program that reads a non-decreasing sorted linked list and removes all duplicate nodes so that every value appears exactly once. The program builds the list from the input values, calls a helper that removes duplicates in place, and then prints the resulting list as a space-separated line.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
    Node(int d) : data(d), next(nullptr) {}
};

Node* removeDuplicates(Node* head) {
    if (!head) return head;
    Node* cur = head;
    while (cur && cur->next) {
        if (cur->data == cur->next->data)
            cur->next = cur->next->next;
        cur = cur->next;
    }
    return head;
}

int main() {
    int n;
    while (cin >> n) {
        Node* head = nullptr;
        Node* tail = nullptr;
        for (int i = 0; i < n; ++i) {
            int x;
            cin >> x;
            Node* fresh = new Node(x);
            if (!head) head = tail = fresh;
            else { tail->next = fresh; tail = fresh; }
        }
        head = removeDuplicates(head);
        for (Node* p = head; p; p = p->next) cout << p->data << " ";
        cout << endl;
        while (head) { Node* t = head; head = head->next; delete t; }
    }
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

For:
```text
4
1 1 2 3
```
the expected output is:
```text
1 2 3 
```

For:
```text
3
1 2 2
```
the expected output is:
```text
1 2 
```

---

## Question 9

### Difficulty
Hard

### Bug Type
Mixed: matrix + accumulator initialization error

### Problem
Write a program that reads an R by C matrix of integers and prints the index of the row that has the maximum total sum. If two rows tie, the row with the smaller index wins. Each test case is introduced by its row and column counts.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int maxSumRow(int mat[][10], int rows, int cols) {
    int bestRow = 0, bestSum = 0;
    for (int r = 0; r < rows; ++r) {
        int s = 0;
        for (int c = 0; c < cols; ++c) s += mat[r][c];
        if (s > bestSum) { bestSum = s; bestRow = r; }
    }
    return bestRow;
}

int main() {
    int rows, cols;
    while (cin >> rows >> cols) {
        int mat[10][10];
        for (int i = 0; i < rows; ++i)
            for (int j = 0; j < cols; ++j) cin >> mat[i][j];
        cout << "Row " << maxSumRow(mat, rows, cols) << endl;
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
2 3
1 2 3
4 5 6
```
the expected output is:
```text
Row 1
```

For:
```text
3 2
10 20
1 1
5 5
```
the expected output is:
```text
Row 0
```

For:
```text
1 4
7 8 9 10
```
the expected output is:
```text
Row 0
```

---

## Question 10

### Difficulty
Hard

### Bug Type
Mixed: string validation + threshold condition error

### Problem
Write a program that reads a candidate password and prints "valid" if it satisfies every rule, otherwise "invalid". A password is valid only if it is at least 8 characters long, contains at least one uppercase letter, at least one lowercase letter, and at least one digit.

### Buggy Code

```cpp
#include <iostream>
#include <cctype>
#include <string>
using namespace std;

bool validPassword(const string& p) {
    if (p.size() < 6) return false;
    bool upper = false, lower = false, digit = false;
    for (size_t i = 0; i < p.size(); ++i) {
        if (isupper(p[i])) upper = true;
        else if (islower(p[i])) lower = true;
        else if (isdigit(p[i])) digit = true;
    }
    return upper && lower && digit;
}

int main() {
    string pwd;
    while (cin >> pwd)
        cout << (validPassword(pwd) ? "valid" : "invalid") << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
abc
```
the expected output is:
```text
invalid
```

For:
```text
Password1
```
the expected output is:
```text
valid
```

For:
```text
ABCDefg!
```
the expected output is:
```text
invalid
```

---

## Question 11

### Difficulty
Hard

### Bug Type
Mixed: subarray sum + accumulator initialization error

### Problem
Write a program that reads an array of integers (which may contain negatives) and prints the maximum subarray sum using an on-the-fly DP scan: accumulate a running sum that resets to the current element whenever that element alone is better than the running sum so far.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

long long maxSubarraySum(const vector<int>& a) {
    long long best = 0;
    long long current = 0;
    for (size_t i = 0; i < a.size(); ++i) {
        current = max(a[i], current + a[i]);
        if (current > best) best = current;
    }
    return best;
}

int main() {
    int n;
    while (cin >> n) {
        vector<int> a(n);
        for (int i = 0; i < n; ++i) cin >> a[i];
        cout << maxSubarraySum(a) << endl;
    }
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
10
```

For:
```text
5
-2 1 -3 4 -1 2 1 -5 4
```
the expected output is:
```text
6
```

For:
```text
3
-10 20 -5
```
the expected output is:
```text
20
```

---

## Question 12

### Difficulty
Hard

### Bug Type
Mixed: searching + half-selection condition missing the left-bound check

### Problem
Write a program that searches for a target value in a sorted array that was rotated (shifted) by some amount. A rotation can place smaller values to the right of larger ones. The search must decide at each step which half of the current range can still contain the target, taking the rotation into account.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int searchSorted(vector<int>& a, int target) {
    int lo = 0, hi = (int)a.size() - 1;
    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;
        if (a[mid] == target) return mid;
        if (target < a[mid]) hi = mid - 1;
        else lo = mid + 1;
    }
    return -1;
}

int main() {
    int n, target;
    while (cin >> n >> target) {
        vector<int> a(n);
        for (int i = 0; i < n; ++i) cin >> a[i];
        cout << searchSorted(a, target) << endl;
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4 3
1 2 3 4
```
the expected output is:
```text
2
```

For:
```text
4 1
1 2 3 4
```
the expected output is:
```text
0
```

For:
```text
3 9
1 2 3
```
the expected output is:
```text
-1
```

---

## Question 13

### Difficulty
Hard

### Bug Type
Mixed: pointer traversal + counting condition missing lower bound

### Problem
Write a program that reads a word (no spaces) and prints how many uppercase letters (A–Z) it contains, counting them by walking a character pointer through the C-string. Only the letters A through Z should be counted.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int countUpper(const char* s) {
    int cnt = 0;
    for (const char* p = s; *p != '\0'; ++p)
        if (*p <= 'Z') cnt++;
    return cnt;
}

int main() {
    char word[100];
    while (cin >> word)
        cout << countUpper(word) << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
Hello
```
the expected output is:
```text
1
```

For:
```text
XYZ
```
the expected output is:
```text
3
```

For:
```text
abc
```
the expected output is:
```text
0
```

---

## Question 14

### Difficulty
Hard

### Bug Type
Mixed: recursion + base-case termination order error

### Problem
Write a program that reads a word and prints "yes" if it is a palindrome (reads the same forward and backward), otherwise "no". A recursive helper compares the outer characters and recurses inward on the remaining substring. The helper stops when the two indices meet or cross.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

bool isPalindrome(const string& s, int l, int r) {
    if (l == r) return true;
    if (l > r) return false;
    if (s[l] != s[r]) return false;
    return isPalindrome(s, l + 1, r - 1);
}

int main() {
    string word;
    while (cin >> word)
        cout << (isPalindrome(word, 0, (int)word.size() - 1) ? "yes" : "no")
             << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
a
```
the expected output is:
```text
yes
```

For:
```text
racecar
```
the expected output is:
```text
yes
```

For:
```text
testing
```
the expected output is:
```text
no
```

---

## Question 15

### Difficulty
Hard

### Bug Type
Mixed: array scan + two largest values tracking (missing demotion update)

### Problem
Write a program that reads an array of non-negative integers and prints the second largest value in the array. If the array has fewer than two distinct values, the program prints -1. The scan keeps track of the largest value and the second largest value seen so far.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int secondLargest(int a[], int n) {
    if (n < 2) return -1;
    int max1 = a[0], max2 = -1;
    for (int i = 1; i < n; ++i) {
        if (a[i] > max1) {
            max1 = a[i];
        } else if (a[i] > max2 && a[i] != max1) {
            max2 = a[i];
        }
    }
    return max2;
}

int main() {
    int n;
    while (cin >> n) {
        int a[100];
        for (int i = 0; i < n; ++i) cin >> a[i];
        cout << secondLargest(a, n) << endl;
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
10 8 6
```
the expected output is:
```text
8
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
4
9 4 6 7
```
the expected output is:
```text
7
```

---

## Question 16

### Difficulty
Hard

### Bug Type
Mixed: binary search + duplicate-run boundary error

### Problem
Write a program that reads a sorted array and a target value, then prints how many times the target appears in the array. The count is derived from the first and last occurrence of the target, each located by binary search. If the target is absent, the program prints 0.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int firstOccurrence(const vector<int>& a, int t) {
    int lo = 0, hi = (int)a.size() - 1, ans = -1;
    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;
        if (a[mid] < t) lo = mid + 1;
        else { ans = mid; hi = mid - 1; }
    }
    return ans;
}

int lastOccurrence(const vector<int>& a, int t) {
    int lo = 0, hi = (int)a.size() - 1, ans = -1;
    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;
        if (a[mid] >= t) { ans = mid; hi = mid - 1; }
        else lo = mid + 1;
    }
    return ans;
}

int countOccurrences(const vector<int>& a, int t) {
    int first = firstOccurrence(a, t);
    if (first == -1 || a[first] != t) return 0;
    return lastOccurrence(a, t) - first + 1;
}

int main() {
    int n, target;
    while (cin >> n >> target) {
        vector<int> a(n);
        for (int i = 0; i < n; ++i) cin >> a[i];
        cout << countOccurrences(a, target) << endl;
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
5 3
1 2 3 4 5
```
the expected output is:
```text
1
```

For:
```text
4 9
1 2 3 4
```
the expected output is:
```text
0
```

For:
```text
1 7
7
```
the expected output is:
```text
1
```

---

## Question 17

### Difficulty
Hard

### Bug Type
Mixed: linked list + edge-case special-casing error

### Problem
Write a program that builds a linked list and prints the value of the k-th node from the end (k = 1 means the last node). The helper first counts the length of the list, then rewalks `len - k` steps from the head to reach the requested node. Note that when k equals the list length, the answer is simply the head node.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
    Node(int d) : data(d), next(nullptr) {}
};

int kthFromEnd(Node* head, int k) {
    int len = 0;
    for (Node* p = head; p; p = p->next) ++len;

    if (k == len) return head->next->data;

    Node* cur = head;
    for (int i = 0; i < len - k; ++i) cur = cur->next;
    return cur->data;
}

int main() {
    int n;
    while (cin >> n) {
        Node* head = nullptr;
        Node* tail = nullptr;
        for (int i = 0; i < n; ++i) {
            int x;
            cin >> x;
            Node* fresh = new Node(x);
            if (!head) head = tail = fresh;
            else { tail->next = fresh; tail = fresh; }
        }
        int k;
        cin >> k;
        cout << kthFromEnd(head, k) << endl;
        while (head) { Node* t = head; head = head->next; delete t; }
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
5
1 2 3 4 5
2
```
the expected output is:
```text
4
```

For:
```text
4
7 8 9 10
1
```
the expected output is:
```text
10
```

For:
```text
6
6 5 4 3 2 1
3
```
the expected output is:
```text
4
```

---

## Question 18

### Difficulty
Hard

### Bug Type
Mixed: stack + comparison operator bug in the monotonic stack

### Problem
Write a program that reads an array and prints the next greater element for each position: the nearest element to the right that is strictly larger, or -1 if none exists. The array is processed right-to-left with a monotonic stack that keeps only candidates for the "next greater" answer.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
#include <stack>
using namespace std;

vector<int> nextGreater(const vector<int>& a) {
    int n = (int)a.size();
    vector<int> res(n, -1);
    stack<int> st;
    for (int i = n - 1; i >= 0; --i) {
        while (!st.empty() && st.top() < a[i]) st.pop();
        res[i] = st.empty() ? -1 : st.top();
        st.push(a[i]);
    }
    return res;
}

int main() {
    int n;
    while (cin >> n) {
        vector<int> a(n);
        for (int i = 0; i < n; ++i) cin >> a[i];
        vector<int> g = nextGreater(a);
        for (int i = 0; i < n; ++i) cout << g[i] << " ";
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
4
4 5 2 25
```
the expected output is:
```text
5 25 25 -1 
```

For:
```text
3
2 1 3
```
the expected output is:
```text
3 3 -1 
```

For:
```text
5
13 7 6 12 10
```
the expected output is:
```text
-1 12 12 -1 -1 
```

---

## Question 19

### Difficulty
Hard

### Bug Type
Mixed: tree + recursion + leaf-detection condition error

### Problem
Write a program that builds a binary tree from a level-order array (-1 marks an absent child) and prints the number of leaf nodes, where a leaf is a node with no children. The count is computed recursively.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
#include <queue>
using namespace std;

struct Node {
    int val;
    Node* left;
    Node* right;
    Node(int v) : val(v), left(nullptr), right(nullptr) {}
};

Node* buildTree(const vector<int>& a) {
    if (a.empty() || a[0] == -1) return nullptr;
    Node* root = new Node(a[0]);
    queue<Node*> q;
    q.push(root);
    size_t i = 1;
    while (!q.empty() && i < a.size()) {
        Node* cur = q.front();
        q.pop();
        if (a[i] != -1) { cur->left = new Node(a[i]); q.push(cur->left); }
        ++i;
        if (i < a.size() && a[i] != -1) {
            cur->right = new Node(a[i]);
            q.push(cur->right);
        }
        ++i;
    }
    return root;
}

int countLeaves(Node* root) {
    if (!root) return 0;
    if (root->left == NULL || root->right == NULL) return 1;
    return countLeaves(root->left) + countLeaves(root->right);
}

int main() {
    int n;
    while (cin >> n) {
        vector<int> nodes(n);
        for (int i = 0; i < n; ++i) cin >> nodes[i];
        Node* root = buildTree(nodes);
        cout << countLeaves(root) << endl;
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
1 2 3
```
the expected output is:
```text
2
```

For:
```text
1
7
```
the expected output is:
```text
1
```

For:
```text
5
1 2 3 4 5
```
the expected output is:
```text
3
```

---

## Question 20

### Difficulty
Hard

### Bug Type
Mixed: string + word-splitting count condition error

### Problem
Write a program that reads a full line of text (with spaces) and prints the number of words in it after first stripping nothing (the line can contain leading/trailing or repeated spaces in hidden tests). Words are separated by single spaces; the program assumes words are separated by exactly one space, so it counts the spaces and adds one.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int countWords(const string& line) {
    if (line.empty()) return 0;
    int words = 1;
    for (size_t i = 0; i < line.size(); ++i)
        if (line[i] == ' ') words++;
    return words;
}

int main() {
    string line;
    while (getline(cin, line))
        cout << countWords(line) << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
hello world
```
the expected output is:
```text
2
```

For:
```text
a b c d
```
the expected output is:
```text
4
```

For:
```text
one
```
the expected output is:
```text
1
```

---

## Question 21

### Difficulty
Hard

### Bug Type
Mixed: array + presence-marking range bound error

### Problem
Write a program that reads an array of integers (values can be negative) and prints the smallest positive integer that does not exist in the array (the classic "first missing positive" problem). The approach uses a boolean table of size n+1 and marks only positive values up to n.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int firstMissingPositive(int a[], int n) {
    vector<bool> seen(n + 1, false);
    for (int i = 0; i < n; ++i)
        if (a[i] >= 1 && a[i] < n) seen[a[i]] = true;

    for (int x = 1; x <= n; ++x)
        if (!seen[x]) return x;

    return n + 1;
}

int main() {
    int n;
    while (cin >> n) {
        int a[100];
        for (int i = 0; i < n; ++i) cin >> a[i];
        cout << firstMissingPositive(a, n) << endl;
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
3 4 -1 1
```
the expected output is:
```text
2
```

For:
```text
3
1 2 0
```
the expected output is:
```text
3
```

For:
```text
2
-5 -8
```
the expected output is:
```text
1
```

---

## Question 22

### Difficulty
Hard

### Bug Type
Mixed: merge + wrong source array in the leftover-copy loop

### Problem
Write a program that reads two sorted arrays and prints their merged sorted result. The merge walks both arrays simultaneously, copying the smaller current value, and afterwards copies whichever array still has leftover elements. The merged array's length is n + m.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

void mergeSorted(int a[], int n, int b[], int m, int c[]) {
    int i = 0, j = 0, k = 0;
    while (i < n && j < m) {
        if (a[i] <= b[j]) c[k++] = a[i++];
        else c[k++] = b[j++];
    }
    while (i < n) c[k++] = a[i++];
    while (j < m) c[k++] = a[j++];
}

int main() {
    int n, m;
    while (cin >> n >> m) {
        int a[100], b[100], c[200];
        for (int i = 0; i < n; ++i) cin >> a[i];
        for (int i = 0; i < m; ++i) cin >> b[i];
        mergeSorted(a, n, b, m, c);
        for (int k = 0; k < n + m; ++k) cout << c[k] << " ";
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
2 0
5 6
```
the expected output is:
```text
5 6 
```

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

For:
```text
3 1
1 2 3
2
```
the expected output is:
```text
1 2 2 3 
```

---

## Question 23

### Difficulty
Hard

### Bug Type
Mixed: matrix search + wrong starting column index

### Problem
Write a program that reads a matrix in which every row and every column is sorted in ascending order, plus a target value, and prints "found" or "not found". The search follows the classic staircase walk starting from the top-right corner of the matrix.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

bool searchMatrix(int mat[][100], int rows, int cols, int target) {
    int r = 0, c = rows - 1;
    while (r < rows && c >= 0) {
        if (mat[r][c] == target) return true;
        if (mat[r][c] > target) c--;
        else r++;
    }
    return false;
}

int main() {
    int rows, cols, target;
    while (cin >> rows >> cols >> target) {
        int mat[100][100];
        for (int i = 0; i < rows; ++i)
            for (int j = 0; j < cols; ++j) cin >> mat[i][j];
        cout << (searchMatrix(mat, rows, cols, target) ? "found" : "not found")
             << endl;
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3 3 8
1 4 7
8 9 10
11 12 16
```
the expected output is:
```text
found
```

For:
```text
2 2 5
1 3
2 4
```
the expected output is:
```text
not found
```

For:
```text
3 3 1
1 2 3
4 5 6
7 8 9
```
the expected output is:
```text
found
```

---

## Question 24

### Difficulty
Hard

### Bug Type
Mixed: frequency signature + grouping logic error

### Problem
Write a program that reads a list of lowercase words and prints the number of anagram groups in it. Two words belong to the same group if one can be rearranged into the other. Each word is mapped to a signature that should capture the exact letter counts, and groups are keyed by that signature in an `unordered_map`.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <unordered_map>
using namespace std;

string signature(const string& w) {
    bool present[26] = {false};
    for (size_t i = 0; i < w.size(); ++i) present[w[i] - 'a'] = true;

    string sig;
    for (int i = 0; i < 26; ++i)
        if (present[i]) sig += char('a' + i);
    return sig;
}

int main() {
    int n;
    while (cin >> n) {
        vector<string> words(n);
        for (int i = 0; i < n; ++i) cin >> words[i];

        unordered_map<string, int> groups;
        for (size_t i = 0; i < words.size(); ++i)
            groups[signature(words[i])]++;

        cout << groups.size() << endl;
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4
tea
eat
dog
cat
```
the expected output is:
```text
3
```

For:
```text
3
ab
ba
xy
```
the expected output is:
```text
2
```

For:
```text
2
abc
cab
```
the expected output is:
```text
1
```

---

## Question 25

### Difficulty
Hard

### Bug Type
Mixed: rotation + shift direction error before a binary search

### Problem
Write a program that reads an array, a rotation count k, and a target value. It rotates the array to the left by k positions, then performs a binary search for the target in the rotated array and prints the found index (or -1). The array remains sorted after any rotation.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

void rotateLeft(int a[], int n, int k) {
    for (int step = 0; step < k; ++step) {
        int last = a[n - 1];
        for (int i = n - 2; i >= 0; --i) a[i + 1] = a[i];
        a[0] = last;
    }
}

int binarySearch(int a[], int n, int t) {
    int lo = 0, hi = n - 1;
    while (lo <= hi) {
        int mid = (lo + hi) / 2;
        if (a[mid] == t) return mid;
        if (a[mid] < t) lo = mid + 1;
        else hi = mid - 1;
    }
    return -1;
}

int main() {
    int n, k, target;
    while (cin >> n >> k >> target) {
        int a[100];
        for (int i = 0; i < n; ++i) cin >> a[i];
        rotateLeft(a, n, k);
        cout << binarySearch(a, n, target) << endl;
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
4 0 6
1 2 4 6
```
the expected output is:
```text
3
```

For:
```text
4 0 9
1 2 4 6
```
the expected output is:
```text
-1
```

For:
```text
4 2 5
5 5 5 5
```
the expected output is:
```text
1
```

---

# Solutions

## Solution 1

### Bug
In `averageEven`, the total sum is divided by `data.size()` (the size of the whole array) instead of `evenCount` (the number of even elements).

### Explanation
When every element is even, `evenCount` equals `data.size()`, so the bug is invisible. The moment odd numbers appear, the denominator stays larger than the count of even values and the reported average is wrong. For example, for input `4/2 4 1 3` the expected average is `(2+4)/2 = 3`, but the buggy code prints `10/4 = 2.5`.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

double averageEven(const vector<int>& data) {
    if (data.empty()) return 0.0;
    long long sum = 0;
    int evenCount = 0;
    for (size_t i = 0; i < data.size(); ++i) {
        if (data[i] % 2 == 0) {
            sum += data[i];
            evenCount++;
        }
    }
    return static_cast<double>(sum) / evenCount;
}

int main() {
    int n;
    while (cin >> n) {
        vector<int> data(n);
        for (int i = 0; i < n; ++i) cin >> data[i];
        cout << averageEven(data) << endl;
    }
    return 0;
}
```

---

## Solution 2

### Bug
The final verification loop counts mismatches only when `freq[i] > 0`. Negative residue entries (characters of the second word that lack a counterpart in the first word) are silently ignored.

### Explanation
A correct anagram check must treat any non-zero frequency as a mismatch. With `freq[i] > 0`, only leftover characters from the first word are noticed. When the first word is fully "covered" by the second and the extra characters come from the second word, the residue is negative and the check passes incorrectly. For example, `a` and `ab` produce frequencies `freq['a'-'a'] = 0` and `freq['b'-'a'] = -1`; no positive entry exists, so the buggy program prints "yes" although the correct answer is "no".

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

bool isAnagram(const string& a, const string& b) {
    int freq[26] = {0};
    for (size_t i = 0; i < a.size(); ++i) freq[a[i] - 'a']++;
    for (size_t i = 0; i < b.size(); ++i) freq[b[i] - 'a']--;

    int mismatches = 0;
    for (int i = 0; i < 26; ++i)
        if (freq[i] != 0) mismatches++;

    return mismatches == 0;
}

int main() {
    string a, b;
    while (cin >> a >> b)
        cout << (isAnagram(a, b) ? "yes" : "no") << endl;
    return 0;
}
```

---

## Solution 3

### Bug
The tie-break branch returns `y < x` instead of `x < y`, so names of equal length get sorted in *descending* alphabetical order instead of ascending.

### Explanation
As long as every name has a distinct length, the length comparison is enough and the bug never fires. The failure appears when two names share the same length: with `cat`, `bat`, `ant` the expected order is `ant bat cat`, but the buggy comparator reverses the equal-length tie to produce `cat bat ant`.

### Corrected Code

```cpp
#include <iostream>
#include <string>
#include <vector>
#include <algorithm>
using namespace std;

bool lengthDesc(const string& x, const string& y) {
    if (x.size() != y.size()) return x.size() > y.size();
    return x < y;
}

int main() {
    int n;
    while (cin >> n) {
        vector<string> names(n);
        for (int i = 0; i < n; ++i) cin >> names[i];
        sort(names.begin(), names.end(), lengthDesc);
        for (size_t i = 0; i < names.size(); ++i) cout << names[i] << " ";
        cout << endl;
    }
    return 0;
}
```

---

## Solution 4

### Bug
The reversal loop uses `i <= n / 2` where it must be `i < n / 2`. For an odd length the extra iteration self-swaps the middle element (harmless), but for an even length it re-swaps the central pair back, undoing the reversal of that pair.

### Explanation
With an odd-length array the midpoint is a single element, so the extra `i <= n/2` step only touches the middle element with itself. With an even length there is no single midpoint: the extra step swaps the two central elements a second time, restoring their original order. For `1 2 3 4` the expected result is `4 3 2 1`, but the buggy code produces `4 2 3 1`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

void reverseArray(int arr[], int n) {
    for (int i = 0; i < n / 2; ++i) {
        int temp = *(arr + i);
        *(arr + i) = *(arr + n - 1 - i);
        *(arr + n - 1 - i) = temp;
    }
}

int main() {
    int n;
    while (cin >> n) {
        int arr[100];
        for (int i = 0; i < n; ++i) cin >> arr[i];
        reverseArray(arr, n);
        for (int i = 0; i < n; ++i) cout << arr[i] << " ";
        cout << endl;
    }
    return 0;
}
```

---

## Solution 5

### Bug
The backward scan in `lastOccurrence` stops at index 1 (`i > 0`), so index 0 is never examined.

### Explanation
Whenever the target's last occurrence sits at index 0 the scan misses it and reports -1, while the forward scan still reports first occurrence 0. For the input `3 2 / 2 1 1` the expected output is `0 0`, but the buggy program prints `0 -1`. Any other target position is found correctly, which hides the defect until a value appears only at the very start of the array.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int lastOccurrence(const vector<int>& a, int target) {
    for (int i = (int)a.size() - 1; i >= 0; --i)
        if (a[i] == target) return i;
    return -1;
}

int main() {
    int n, target;
    while (cin >> n >> target) {
        vector<int> a(n);
        for (int i = 0; i < n; ++i) cin >> a[i];

        int first = -1;
        for (int i = 0; i < n; ++i)
            if (a[i] == target) { first = i; break; }

        int last = lastOccurrence(a, target);
        cout << first << " " << last << endl;
    }
    return 0;
}
```

---

## Solution 6

### Bug
The base case of the recursive product returns `0`; it must return `1` so that multiplying by it leaves the accumulated product unchanged.

### Explanation
Every recursive call climbs all the way to the end of the array, so the base value is always the final multiplier. With a base case of `0`, any product that contains a zero element is fine (it is genuinely zero), but a product of non-zero elements is silently zeroed too. For `2 3 4` the correct result is 24, while the buggy code prints 0.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

long long product(const vector<int>& a, size_t i) {
    if (i == a.size()) return 1;
    return a[i] * product(a, i + 1);
}

int main() {
    int n;
    while (cin >> n) {
        vector<int> a(n);
        for (int i = 0; i < n; ++i) cin >> a[i];
        cout << product(a, 0) << endl;
    }
    return 0;
}
```

---

## Solution 7

### Bug
The scan for the first unique character runs from the **end** of the string backwards (`i = size - 1` down to `0`) instead of from the front.

### Explanation
The frequency map itself is correct; only the direction of the second loop is wrong. The backward scan returns the *last* character that occurs exactly once. If the string has a single unique character, both directions agree and the bug is invisible. As soon as two characters are unique, the answer differs: for `abca` the expected index is 1 ('b'), but the backwards scan returns 2 ('c').

### Corrected Code

```cpp
#include <iostream>
#include <string>
#include <unordered_map>
using namespace std;

int firstUnique(const string& s) {
    unordered_map<char, int> count;
    for (size_t i = 0; i < s.size(); ++i) count[s[i]]++;

    for (size_t i = 0; i < s.size(); ++i)
        if (count[s[i]] == 1) return i;

    return -1;
}

int main() {
    string s;
    while (cin >> s)
        cout << firstUnique(s) << endl;
    return 0;
}
```

---

## Solution 8

### Bug
After removing a duplicate node the code still advances `cur = cur->next`, so when three or more equal values are consecutive, every alternate duplicate survives.

### Explanation
The fix requires moving to the next node *only* when no removal happened. With a single duplicated pair the removal and the advance land on the next distinct value, so the bug stays hidden. With three or more equal values, e.g. `1 1 1`, the first node discards the second node and then advances onto the (former third) value, which then has no further duplicate to see; the list remains two elements long — the correct result is a single `1`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
    Node(int d) : data(d), next(nullptr) {}
};

Node* removeDuplicates(Node* head) {
    if (!head) return head;
    Node* cur = head;
    while (cur && cur->next) {
        if (cur->data == cur->next->data)
            cur->next = cur->next->next;
        else
            cur = cur->next;
    }
    return head;
}

int main() {
    int n;
    while (cin >> n) {
        Node* head = nullptr;
        Node* tail = nullptr;
        for (int i = 0; i < n; ++i) {
            int x;
            cin >> x;
            Node* fresh = new Node(x);
            if (!head) head = tail = fresh;
            else { tail->next = fresh; tail = fresh; }
        }
        head = removeDuplicates(head);
        for (Node* p = head; p; p = p->next) cout << p->data << " ";
        cout << endl;
        while (head) { Node* t = head; head = head->next; delete t; }
    }
    return 0;
}
```

---

## Solution 9

### Bug
`bestSum` is initialized to `0`. Correctly it should be started at minus infinity (or the sum of the first row) so that even negative row sums can beat it.

### Explanation
The scan only raises the "best" when a row sum exceeds the current best. If every row sum is negative, none ever exceeds the initial `0`, so the answer stays glued to row 0 even when a later row has the largest (least negative) sum. For the matrix `-5 -5 / -1 -2`, row 1 (sum -3) is correct, but the program prints `Row 0`.

### Corrected Code

```cpp
#include <iostream>
#include <climits>
using namespace std;

int maxSumRow(int mat[][10], int rows, int cols) {
    int bestRow = 0, bestSum = INT_MIN;
    for (int r = 0; r < rows; ++r) {
        int s = 0;
        for (int c = 0; c < cols; ++c) s += mat[r][c];
        if (s > bestSum) { bestSum = s; bestRow = r; }
    }
    return bestRow;
}

int main() {
    int rows, cols;
    while (cin >> rows >> cols) {
        int mat[10][10];
        for (int i = 0; i < rows; ++i)
            for (int j = 0; j < cols; ++j) cin >> mat[i][j];
        cout << "Row " << maxSumRow(mat, rows, cols) << endl;
    }
    return 0;
}
```

---

## Solution 10

### Bug
The minimum-length rule uses `< 6` where the specification requires a minimum of 8 characters.

### Explanation
A 6 or 7 character password that satisfies the letter and digit rules is accepted even though it violates the length requirement. For example, `Abcdef1` (7 characters) is reported "valid" although it should be "invalid"; the shown test cases happen to use either shorter strings (already rejected) or strings of at least 8 characters, so the defect only appears on 6–7 character inputs.

### Corrected Code

```cpp
#include <iostream>
#include <cctype>
#include <string>
using namespace std;

bool validPassword(const string& p) {
    if (p.size() < 8) return false;
    bool upper = false, lower = false, digit = false;
    for (size_t i = 0; i < p.size(); ++i) {
        if (isupper(p[i])) upper = true;
        else if (islower(p[i])) lower = true;
        else if (isdigit(p[i])) digit = true;
    }
    return upper && lower && digit;
}

int main() {
    string pwd;
    while (cin >> pwd)
        cout << (validPassword(pwd) ? "valid" : "invalid") << endl;
    return 0;
}
```

---

## Solution 11

### Bug
The accumulator `best` is initialized to `0`. When the whole array is negative, the oracle value should be the largest (least negative) single element, but `0` is never beaten.

### Explanation
The running-sum update itself is correct (Kadane's algorithm). The only flaw is the initial value of the answer: because the best-so-far starts at 0, an all-negative array keeps answering 0. For example, `-3 -1 -7` should give -1, but the program prints 0. Any array containing at least one positive value produces the same result as the correct version, which hides the bug on ordinary tests.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

long long maxSubarraySum(const vector<int>& a) {
    if (a.empty()) return 0;
    long long best = a[0];
    long long current = 0;
    for (size_t i = 0; i < a.size(); ++i) {
        current = max(a[i], current + a[i]);
        if (current > best) best = current;
    }
    return best;
}

int main() {
    int n;
    while (cin >> n) {
        vector<int> a(n);
        for (int i = 0; i < n; ++i) cin >> a[i];
        cout << maxSubarraySum(a) << endl;
    }
    return 0;
}
```

---

## Solution 12

### Bug
The search narrows the range with `target < a[mid]` alone; it never verifies that the target actually lies inside the *left* half. On a rotated array, the plain condition sends the search into the wrong half.

### Explanation
The comparison `target < a[mid]` is valid only for a fully sorted (non-rotated) array. After a rotation there are two sorted runs, and a target can be smaller than `a[mid]` yet still lie to the right (because of the wrap-around run). For the rotated array `4 5 6 7 0 1 2` searching for `0`, the plain binary search keeps stepping left and returns -1, while the correct answer is index 4.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int searchSorted(vector<int>& a, int target) {
    int lo = 0, hi = (int)a.size() - 1;
    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;
        if (a[mid] == target) return mid;

        if (a[lo] <= a[mid]) {
            if (a[lo] <= target && target < a[mid]) hi = mid - 1;
            else lo = mid + 1;
        } else {
            if (a[mid] < target && target <= a[hi]) lo = mid + 1;
            else hi = mid - 1;
        }
    }
    return -1;
}

int main() {
    int n, target;
    while (cin >> n >> target) {
        vector<int> a(n);
        for (int i = 0; i < n; ++i) cin >> a[i];
        cout << searchSorted(a, target) << endl;
    }
    return 0;
}
```

---

## Solution 13

### Bug
The counting condition is `*p <= 'Z'`; it is missing the lower bound `*p >= 'A'`, so every ASCII character at or below 'Z' (digits, punctuation, uppercase letters) is counted as uppercase.

### Explanation
Lowercase letters have ASCII codes above 'Z' so they are still skipped correctly, which is why strings made only of letters look fine. Digits ('0'–'9'), however, are all below 'Z' and get miscounted. For `AbC123` the correct answer is 2, but the buggy code returns 5.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int countUpper(const char* s) {
    int cnt = 0;
    for (const char* p = s; *p != '\0'; ++p)
        if (*p >= 'A' && *p <= 'Z') cnt++;
    return cnt;
}

int main() {
    char word[100];
    while (cin >> word)
        cout << countUpper(word) << endl;
    return 0;
}
```

---

## Solution 14

### Bug
The base case treats an odd-length stop (`l == r`) as palindrome, but a crossing pair (`l > r`) returns false. Even-length palindromes always end in the crossing state, so they are rejected.

### Explanation
For a word with an odd number of characters the recursion converges on the single middle character, where `l == r` fires and the answer is true — correct. For an even-length palindrome, the pointers pass each other and hit the `l > r` branch, which wrongly answers false. `abba` is a palindrome but the buggy program prints "no".

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

bool isPalindrome(const string& s, int l, int r) {
    if (l >= r) return true;
    if (s[l] != s[r]) return false;
    return isPalindrome(s, l + 1, r - 1);
}

int main() {
    string word;
    while (cin >> word)
        cout << (isPalindrome(word, 0, (int)word.size() - 1) ? "yes" : "no")
             << endl;
    return 0;
}
```

---

## Solution 15

### Bug
When a new maximum is found (`a[i] > max1`), the old maximum is not demoted to `max2`. The previous largest value disappears from the bookkeeping.

### Explanation
The scan updates `max1` but never shifts the outgoing maximum into `max2`, so `max2` always comes from ordinary elements instead of from demoted maxima. When the overall maximum is not the first element, the old maximum (which is the true second largest) is lost. For `5 2 6` the correct second largest is 5, but the program returns 2. Arrays whose maximum is the first element behave correctly.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int secondLargest(int a[], int n) {
    if (n < 2) return -1;
    int max1 = a[0], max2 = -1;
    for (int i = 1; i < n; ++i) {
        if (a[i] > max1) {
            max2 = max1;
            max1 = a[i];
        } else if (a[i] > max2 && a[i] != max1) {
            max2 = a[i];
        }
    }
    return max2;
}

int main() {
    int n;
    while (cin >> n) {
        int a[100];
        for (int i = 0; i < n; ++i) cin >> a[i];
        cout << secondLargest(a, n) << endl;
    }
    return 0;
}
```

---

## Solution 16

### Bug
`lastOccurrence` uses the same condition as `firstOccurrence` — `a[mid] >= t` with `hi = mid - 1` — so it returns the *first* index of the run instead of the last.

### Explanation
The two "occurrence" searches must move in opposite directions at exclusions. Merging the exact same condition into both means `lastOccurrence` collapses onto the first occurrence. With a single occurrence (or an absent target) the two coincide and the count is right; with a run of duplicates, `first == last` yields a count of 1. For `1 2 2 2 3 4` and target `2`, the correct count is 3, but the buggy program prints 1.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int firstOccurrence(const vector<int>& a, int t) {
    int lo = 0, hi = (int)a.size() - 1, ans = -1;
    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;
        if (a[mid] < t) lo = mid + 1;
        else { ans = mid; hi = mid - 1; }
    }
    return ans;
}

int lastOccurrence(const vector<int>& a, int t) {
    int lo = 0, hi = (int)a.size() - 1, ans = -1;
    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;
        if (a[mid] <= t) { ans = mid; lo = mid + 1; }
        else hi = mid - 1;
    }
    return ans;
}

int countOccurrences(const vector<int>& a, int t) {
    int first = firstOccurrence(a, t);
    if (first == -1 || a[first] != t) return 0;
    return lastOccurrence(a, t) - first + 1;
}

int main() {
    int n, target;
    while (cin >> n >> target) {
        vector<int> a(n);
        for (int i = 0; i < n; ++i) cin >> a[i];
        cout << countOccurrences(a, target) << endl;
    }
    return 0;
}
```

---

## Solution 17

### Bug
The special case `k == len` returns `head->next->data` instead of `head->data`.

### Explanation
The generic re-walk loop is correct for every interior k, so the defect only becomes reachable when k equals the list length, where the answer must be the head node. On a list of length 5 with k = 5 the correct value is the head element, but the program returns the *second* element. On a single-node list the special case dereferences `head->next`, which is `nullptr`, causing a crash.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
    Node(int d) : data(d), next(nullptr) {}
};

int kthFromEnd(Node* head, int k) {
    int len = 0;
    for (Node* p = head; p; p = p->next) ++len;

    if (k == len) return head->data;

    Node* cur = head;
    for (int i = 0; i < len - k; ++i) cur = cur->next;
    return cur->data;
}

int main() {
    int n;
    while (cin >> n) {
        Node* head = nullptr;
        Node* tail = nullptr;
        for (int i = 0; i < n; ++i) {
            int x;
            cin >> x;
            Node* fresh = new Node(x);
            if (!head) head = tail = fresh;
            else { tail->next = fresh; tail = fresh; }
        }
        int k;
        cin >> k;
        cout << kthFromEnd(head, k) << endl;
        while (head) { Node* t = head; head = head->next; delete t; }
    }
    return 0;
}
```

---

## Solution 18

### Bug
The stack-clearing loop pops while `st.top() < a[i]` (strict). Equal values must also be popped; otherwise an equal element on the stack blocks the true next-greater answer behind it.

### Explanation
The definition of next greater requires a *strictly* larger value, and the stop-pop must discard everything smaller **or equal**. When duplicates exist, a kept duplicate sits on the stack and is handed out as the answer for the next position. For `4 4 5 2` the first 4 should get answer 5, but the buggy code finds the equal 4 on the stack and outputs 4. Arrays without duplicates never trigger the problem.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
#include <stack>
using namespace std;

vector<int> nextGreater(const vector<int>& a) {
    int n = (int)a.size();
    vector<int> res(n, -1);
    stack<int> st;
    for (int i = n - 1; i >= 0; --i) {
        while (!st.empty() && st.top() <= a[i]) st.pop();
        res[i] = st.empty() ? -1 : st.top();
        st.push(a[i]);
    }
    return res;
}

int main() {
    int n;
    while (cin >> n) {
        vector<int> a(n);
        for (int i = 0; i < n; ++i) cin >> a[i];
        vector<int> g = nextGreater(a);
        for (int i = 0; i < n; ++i) cout << g[i] << " ";
        cout << endl;
    }
    return 0;
}
```

---

## Solution 19

### Bug
The leaf test uses `root->left == NULL || root->right == NULL`; it must be `&&`. Any node with at least one missing child is wrongly declared a leaf.

### Explanation
A node with a single child is not a leaf, but the `||` condition treats it as one. Balanced trees (every internal node has both children) are unaffected, which is why typical inputs pass. When a node has only one child and that child has children of its own, the count is short. For the tree `1 2 -1 3 4` (node 2 has children 3 and 4, root has only a left child) the correct leaf count is 2, but the buggy code returns 1.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
#include <queue>
using namespace std;

struct Node {
    int val;
    Node* left;
    Node* right;
    Node(int v) : val(v), left(nullptr), right(nullptr) {}
};

Node* buildTree(const vector<int>& a) {
    if (a.empty() || a[0] == -1) return nullptr;
    Node* root = new Node(a[0]);
    queue<Node*> q;
    q.push(root);
    size_t i = 1;
    while (!q.empty() && i < a.size()) {
        Node* cur = q.front();
        q.pop();
        if (a[i] != -1) { cur->left = new Node(a[i]); q.push(cur->left); }
        ++i;
        if (i < a.size() && a[i] != -1) {
            cur->right = new Node(a[i]);
            q.push(cur->right);
        }
        ++i;
    }
    return root;
}

int countLeaves(Node* root) {
    if (!root) return 0;
    if (root->left == NULL && root->right == NULL) return 1;
    return countLeaves(root->left) + countLeaves(root->right);
}

int main() {
    int n;
    while (cin >> n) {
        vector<int> nodes(n);
        for (int i = 0; i < n; ++i) cin >> nodes[i];
        Node* root = buildTree(nodes);
        cout << countLeaves(root) << endl;
    }
    return 0;
}
```

---

## Solution 20

### Bug
The word count is computed as "one plus the number of spaces", which is only valid when words are separated by exactly one space.

### Explanation
The formula `words = spaces + 1` breaks with repeated spaces, or a leading/trailing space: `two  spaces` contains two spaces but only two words, yet the program reports 3. A robust counter should flip a "currently inside a word" flag only when entering a new word from whitespace.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int countWords(const string& line) {
    int words = 0;
    bool inWord = false;
    for (size_t i = 0; i < line.size(); ++i) {
        if (line[i] == ' ') inWord = false;
        else if (!inWord) {
            inWord = true;
            words++;
        }
    }
    return words;
}

int main() {
    string line;
    while (getline(cin, line))
        cout << countWords(line) << endl;
    return 0;
}
```

---

## Solution 21

### Bug
The presence-marking guard uses `a[i] < n`; it must be `a[i] <= n` so the value n itself can be marked.

### Explanation
Because n is a legal array value (index n fits the `seen` table of size n+1), `a[i] < n` silently drops it. A permutation like `1 2 3` (n = 3) leaves the table without slot 3, so the answer 3 is produced although all of 1..3 are present and the true first missing positive is 4. Inputs that never contain the exact value n behave correctly.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int firstMissingPositive(int a[], int n) {
    vector<bool> seen(n + 1, false);
    for (int i = 0; i < n; ++i)
        if (a[i] >= 1 && a[i] <= n) seen[a[i]] = true;

    for (int x = 1; x <= n; ++x)
        if (!seen[x]) return x;

    return n + 1;
}

int main() {
    int n;
    while (cin >> n) {
        int a[100];
        for (int i = 0; i < n; ++i) cin >> a[i];
        cout << firstMissingPositive(a, n) << endl;
    }
    return 0;
}
```

---

## Solution 22

### Bug
The second leftover loop copies from array `a` (`a[j++]`) where it must copy from array `b` (`b[j++]`).

### Explanation
When the merge runs out of `a` first, the remaining elements belong to `b`, but the buggy loop re-copies the head of `a` into those slots. The failure appears whenever the last element comes from `b`'s tail. For `a = 1 2` and `b = 3 4` the expected merge is `1 2 3 4`, but the program prints `1 2 1 2`. Whenever `b` is consumed entirely inside the main loop, no leftover copy runs and the output is correct.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

void mergeSorted(int a[], int n, int b[], int m, int c[]) {
    int i = 0, j = 0, k = 0;
    while (i < n && j < m) {
        if (a[i] <= b[j]) c[k++] = a[i++];
        else c[k++] = b[j++];
    }
    while (i < n) c[k++] = a[i++];
    while (j < m) c[k++] = b[j++];
}

int main() {
    int n, m;
    while (cin >> n >> m) {
        int a[100], b[100], c[200];
        for (int i = 0; i < n; ++i) cin >> a[i];
        for (int i = 0; i < m; ++i) cin >> b[i];
        mergeSorted(a, n, b, m, c);
        for (int k = 0; k < n + m; ++k) cout << c[k] << " ";
        cout << endl;
    }
    return 0;
}
```

---

## Solution 23

### Bug
The walk starts at column `rows - 1` instead of `cols - 1` (the top-right corner).

### Explanation
For a square matrix the two values coincide, so the search works. For a wide matrix (more columns than rows), the starting column is too far to the left and the right-most columns are never visited. In the 2 by 4 matrix with target `12` (bottom-right corner), the walk never reaches column 3 and reports "not found".

### Corrected Code

```cpp
#include <iostream>
using namespace std;

bool searchMatrix(int mat[][100], int rows, int cols, int target) {
    int r = 0, c = cols - 1;
    while (r < rows && c >= 0) {
        if (mat[r][c] == target) return true;
        if (mat[r][c] > target) c--;
        else r++;
    }
    return false;
}

int main() {
    int rows, cols, target;
    while (cin >> rows >> cols >> target) {
        int mat[100][100];
        for (int i = 0; i < rows; ++i)
            for (int j = 0; j < cols; ++j) cin >> mat[i][j];
        cout << (searchMatrix(mat, rows, cols, target) ? "found" : "not found")
             << endl;
    }
    return 0;
}
```

---

## Solution 24

### Bug
The word signature records only which letters are present, not how many times each occurs. Two words with the same letter set but different multiplicities collide into one group key.

### Explanation
A correct anagram signature must include letter counts (e.g., a sorted copy of the word). With a mere set of letters, `aab` and `abb` both map to `"ab"` and are merged into a single group, although they are not anagrams of each other. Words with fully distinct letter sets, and true anagrams, still group correctly, hiding the flaw on ordinary tests.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <unordered_map>
#include <algorithm>
using namespace std;

string signature(const string& w) {
    string sig = w;
    sort(sig.begin(), sig.end());
    return sig;
}

int main() {
    int n;
    while (cin >> n) {
        vector<string> words(n);
        for (int i = 0; i < n; ++i) cin >> words[i];

        unordered_map<string, int> groups;
        for (size_t i = 0; i < words.size(); ++i)
            groups[signature(words[i])]++;

        cout << groups.size() << endl;
    }
    return 0;
}
```

---

## Solution 25

### Bug
`rotateLeft` actually performs a **right** rotation: it saves the last element and shifts everything to the right. The left rotation must save the first element and shift everything to the left.

### Explanation
The shift loop runs from `n - 2` down to `0` writing `a[i + 1] = a[i]`, then places the saved tail at index 0 — that is exactly a right rotation by one. Rotating left by k and rotating right by k coincide only for k = 0, a single-element list, or an all-equal array, so the shown cases pass. For `1 2 3 4 5` with k = 2, the correct left-rotated array is `3 4 5 1 2` (target 3 at index 0), while the buggy program builds `4 5 1 2 3` and reports index 4.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

void rotateLeft(int a[], int n, int k) {
    for (int step = 0; step < k; ++step) {
        int first = a[0];
        for (int i = 0; i < n - 1; ++i) a[i] = a[i + 1];
        a[n - 1] = first;
    }
}

int binarySearch(int a[], int n, int t) {
    int lo = 0, hi = n - 1;
    while (lo <= hi) {
        int mid = (lo + hi) / 2;
        if (a[mid] == t) return mid;
        if (a[mid] < t) lo = mid + 1;
        else hi = mid - 1;
    }
    return -1;
}

int main() {
    int n, k, target;
    while (cin >> n >> k >> target) {
        int a[100];
        for (int i = 0; i < n; ++i) cin >> a[i];
        rotateLeft(a, n, k);
        cout << binarySearch(a, n, target) << endl;
    }
    return 0;
}
```