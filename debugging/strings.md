# C++ Debugging — Strings

40 standalone C++ debugging questions about `std::string`, ordered Easy → Medium → Hard. Each question is self-contained (a complete program with `main()`). After all 40 questions you will find a full Solutions section.

## Question 1

### Difficulty
Easy

### Bug Type
Count Vowels Missing 'u' in Condition

### Problem
The program counts the number of vowels (a, e, i, o, u) in a single line of lowercase text and prints the total. Every vowel in the input must be counted, regardless of its position.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter text: ";
    getline(cin, s);
    int vowels = 0;
    for (char c : s) {
        if (c == 'a' || c == 'e' || c == 'i' || c == 'o') {
            vowels++;
        }
    }
    cout << vowels << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
hello
```
the expected output is:
```text
2
```

For:
```text
aurora
```
the expected output is:
```text
4
```

For:
```text
quiz
```
the expected output is:
```text
2
```

---

## Question 2

### Difficulty
Easy

### Bug Type
Palindrome Wrong Mirror Index (`n - i` vs `n - 1 - i`)

### Problem
The program decides whether a word is a palindrome (reads the same forwards and backwards) and prints either "Palindrome" or "Not a palindrome". A palindrome must compare each character with its mirror on the other side of the middle.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    bool palindrome = true;
    for (int i = 0; i < s.length() / 2; i++) {
        if (s[i] != s[s.length() - i]) {
            palindrome = false;
        }
    }
    if (palindrome) {
        cout << "Palindrome" << endl;
    } else {
        cout << "Not a palindrome" << endl;
    }
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
Palindrome
```

For:
```text
madam
```
the expected output is:
```text
Palindrome
```

For:
```text
noon
```
the expected output is:
```text
Palindrome
```

---

## Question 3

### Difficulty
Easy

### Bug Type
Case Conversion Loop Starts at Index 1

### Problem
The program converts every lowercase letter in a word to uppercase and prints the result. All letters must be converted, starting from the very first character.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    for (int i = 1; i < s.length(); i++) {
        if (s[i] >= 'a' && s[i] <= 'z') {
            s[i] = s[i] - 32;
        }
    }
    cout << s << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
Python
```
the expected output is:
```text
PYTHON
```

For:
```text
hello
```
the expected output is:
```text
HELLO
```

For:
```text
day
```
the expected output is:
```text
DAY
```

---

## Question 4

### Difficulty
Easy

### Bug Type
Character Frequency Missing Update

### Problem
The program counts how many times a given character appears in a string and prints that count. Each matching character must increase the running total by exactly one.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    char ch;
    cout << "Enter a string and a character: ";
    cin >> s >> ch;
    int count = 0;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] == ch) {
            count += 0;
        }
    }
    cout << ch << " appears " << count << " times." << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
hello z
```
the expected output is:
```text
z appears 0 times.
```

For:
```text
hello l
```
the expected output is:
```text
l appears 2 times.
```

For:
```text
banana a
```
the expected output is:
```text
a appears 3 times.
```

---

## Question 5

### Difficulty
Easy

### Bug Type
Count Consonants Loop Boundary

### Problem
The program counts the consonants in a lowercase word (letters that are not a, e, i, o or u) and prints the total. Every character of the word must be examined.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    int consonants = 0;
    for (int i = 0; i < s.length() - 1; i++) {
        char c = s[i];
        if (c >= 'a' && c <= 'z' &&
            c != 'a' && c != 'e' && c != 'i' && c != 'o' && c != 'u') {
            consonants++;
        }
    }
    cout << "Consonants: " << consonants << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
bee
```
the expected output is:
```text
Consonants: 1
```

For:
```text
cat
```
the expected output is:
```text
Consonants: 2
```

For:
```text
b
```
the expected output is:
```text
Consonants: 1
```

---

## Question 6

### Difficulty
Easy

### Bug Type
Count Spaces Reads Past End

### Problem
The program counts the number of space characters in a sentence and prints the total. Each space should be counted exactly once.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a sentence: ";
    getline(cin, s);
    int spaces = 0;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] == ' ' || s[i + 1] == ' ') {
            spaces++;
        }
    }
    cout << "Spaces: " << spaces << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
hello
```
the expected output is:
```text
Spaces: 0
```

For:
```text
a b
```
the expected output is:
```text
Spaces: 1
```

For:
```text
a  b
```
the expected output is:
```text
Spaces: 2
```

---

## Question 7

### Difficulty
Easy

### Bug Type
Using str.length() as Loop Bound (`<=`)

### Problem
The program prints each character of a word together with its position, one line per character ("index: ASCII value"). Exactly one line must be printed for each real character of the word.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    for (int i = 0; i <= s.length(); i++) {
        cout << i << ": " << (int)s[i] << endl;
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
cat
```
the expected output is:
```text
0: 99
1: 97
2: 116
```

For:
```text
hi
```
the expected output is:
```text
0: 104
1: 105
```

---

## Question 8

### Difficulty
Easy

### Bug Type
Character Comparison Case-Sensitivity Error

### Problem
The program checks whether a given letter appears inside a word. The search must ignore case, so "P" matches both "p" and "P".

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    char ch;
    cout << "Enter a word and a letter: ";
    cin >> s >> ch;
    bool found = false;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] == ch) {
            found = true;
        }
    }
    if (found) {
        cout << "Found" << endl;
    } else {
        cout << "Not found" << endl;
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
python y
```
the expected output is:
```text
Found
```

For:
```text
PYTHON p
```
the expected output is:
```text
Found
```

For:
```text
python P
```
the expected output is:
```text
Found
```

---

## Question 9

### Difficulty
Easy

### Bug Type
Replace Character Wrong Target

### Problem
The program replaces every lowercase letter 't' in a line of text with the digit '7'. All other characters must remain unchanged.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter text: ";
    getline(cin, s);
    for (int i = 0; i < s.length(); i++) {
        if (s[i] == 's') {
            s[i] = '7';
        }
    }
    cout << s << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
xyz
```
the expected output is:
```text
xyz
```

For:
```text
txt
```
the expected output is:
```text
7x7
```

For:
```text
sat
```
the expected output is:
```text
sa7
```

---

## Question 10

### Difficulty
Easy

### Bug Type
Sum of Digits in a Numeric String

### Problem
The program computes the sum of the digits inside a string and prints the total. Non-digit characters must be ignored completely.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a number: ";
    cin >> s;
    int sum = 0;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] >= '0' && s[i] <= '9') {
            sum += s[i] - '0';
        } else {
            sum += s[i];
        }
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
231
```
the expected output is:
```text
Sum of digits: 6
```

For:
```text
2a1
```
the expected output is:
```text
Sum of digits: 3
```

For:
```text
1b2c
```
the expected output is:
```text
Sum of digits: 3
```

---

## Question 11

### Difficulty
Easy

### Bug Type
Converting First Character Only (wrong target)

### Problem
The program capitalizes the first letter of a word (converts it to uppercase) and prints the result. Only the first character may change.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    if (s.length() > 0) {
        int last = s.length() - 1;
        if (s[last] >= 'a' && s[last] <= 'z') {
            s[last] = s[last] - 32;
        }
    }
    cout << s << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
b
```
the expected output is:
```text
B
```

For:
```text
cat
```
the expected output is:
```text
Cat
```

For:
```text
apple
```
the expected output is:
```text
Apple
```

---

## Question 12

### Difficulty
Easy

### Bug Type
String Reversal Wrong Swap Bound

### Problem
The program reverses a string in place by swapping characters and prints the reversed string. After the algorithm finishes, the original order must be completely reversed.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a string: ";
    cin >> s;
    int n = s.length();
    for (int i = 0; i < n; i++) {
        char ch = s[i];
        s[i] = s[n - 1 - i];
        s[n - 1 - i] = ch;
    }
    cout << s << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
madam
```
the expected output is:
```text
madam
```

For:
```text
abc
```
the expected output is:
```text
cba
```

For:
```text
hello
```
the expected output is:
```text
olleh
```

---

## Question 13

### Difficulty
Medium

### Bug Type
Reverse Words Wrong Order

### Problem
The program splits a sentence into words and prints the words in reverse order. The words themselves must keep their original spelling, but their sequence must be flipped.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a sentence: ";
    getline(cin, s);
    string words[100];
    int n = 0;
    string w = "";
    for (int i = 0; i <= s.length(); i++) {
        if (i == s.length() || s[i] == ' ') {
            words[n++] = w;
            w = "";
        } else {
            w += s[i];
        }
    }
    for (int i = 0; i < n; i++) {
        if (i > 0) cout << " ";
        cout << words[i];
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
one
```
the expected output is:
```text
one
```

For:
```text
a b c
```
the expected output is:
```text
c b a
```

For:
```text
we love coding
```
the expected output is:
```text
coding love we
```

---

## Question 14

### Difficulty
Medium

### Bug Type
Anagram Wrong Length Check

### Problem
The program checks whether two words are anagrams (built from exactly the same letters) and prints "Anagrams" or "Not anagrams". Two words with the same letters but a different arrangement must be recognized as anagrams.

### Buggy Code

```cpp
#include <iostream>
#include <string>
#include <algorithm>
using namespace std;

int main() {
    string a, b;
    cout << "Enter two words: ";
    cin >> a >> b;
    if (a.length() == b.length()) {
        cout << "Not anagrams" << endl;
        return 0;
    }
    sort(a.begin(), a.end());
    sort(b.begin(), b.end());
    if (a == b) {
        cout << "Anagrams" << endl;
    } else {
        cout << "Not anagrams" << endl;
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
hat hats
```
the expected output is:
```text
Not anagrams
```

For:
```text
listen silent
```
the expected output is:
```text
Anagrams
```

For:
```text
aab aba
```
the expected output is:
```text
Anagrams
```

---

## Question 15

### Difficulty
Medium

### Bug Type
Substring Search Loop Boundary

### Problem
The program searches for a pattern inside a longer text using manual character-by-character matching and prints "Found" or "Not found". Any occurrence of the pattern anywhere inside the text must be reported, including in the middle of the text.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s, pat;
    cout << "Enter text and pattern: ";
    cin >> s >> pat;
    bool found = false;
    for (int i = 0; i <= s.length() - pat.length(); i++) {
        bool match = true;
        for (int j = 0; j <= pat.length(); j++) {
            if (s[i + j] != pat[j]) {
                match = false;
            }
        }
        if (match) {
            found = true;
        }
    }
    if (found) {
        cout << "Found" << endl;
    } else {
        cout << "Not found" << endl;
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
hello o
```
the expected output is:
```text
Found
```

For:
```text
hello l
```
the expected output is:
```text
Found
```

For:
```text
apple l
```
the expected output is:
```text
Found
```

---

## Question 16

### Difficulty
Medium

### Bug Type
Wrong substring Length / Boundary

### Problem
The program reads a string, a start index and a length, then prints the substring of exactly that many characters beginning at that index. It must not include any extra characters.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    int start, len;
    cout << "Enter a string, start index and length: ";
    cin >> s >> start >> len;
    cout << s.substr(start, len + 1) << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
abcdef 4 2
```
the expected output is:
```text
ef
```

For:
```text
abcdef 1 3
```
the expected output is:
```text
bcd
```

For:
```text
abcdef 2 1
```
the expected output is:
```text
c
```

---

## Question 17

### Difficulty
Medium

### Bug Type
Remove Spaces Wrong Overwrite Index

### Problem
The program removes every space from a sentence in place by copying the non-space characters to the left, then prints the result (after resizing the string to the compacted length).

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a sentence: ";
    getline(cin, s);
    int j = 0;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] != ' ') {
            s[j] = s[i];
        }
        j++;
    }
    s.resize(j);
    cout << s << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
ab
```
the expected output is:
```text
ab
```

For:
```text
a b
```
the expected output is:
```text
ab
```

For:
```text
a  b
```
the expected output is:
```text
ab
```

---

## Question 18

### Difficulty
Medium

### Bug Type
Toggle Case Arithmetic Error

### Problem
The program toggles the case of every letter in a word: lowercase letters become uppercase and uppercase letters become lowercase. Non-letter characters are left untouched.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] >= 'a' && s[i] <= 'z') {
            s[i] = s[i] - 32;
        } else if (s[i] >= 'A' && s[i] <= 'Z') {
            s[i] = s[i] - 32;
        }
    }
    cout << s << endl;
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
ABC
```

For:
```text
ABC
```
the expected output is:
```text
abc
```

For:
```text
Zoom
```
the expected output is:
```text
zOOM
```

---

## Question 19

### Difficulty
Medium

### Bug Type
First Non-Repeating Character Wrong Frequency Check

### Problem
The program finds the first character in a word that appears exactly once and prints it. If every character repeats, it prints "None".

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    int freq[26] = {0};
    for (int i = 0; i < s.length(); i++) {
        for (int j = 0; j < s.length(); j++) {
            if (i != j && s[i] == s[j]) {
                freq[s[i] - 'a']++;
            }
        }
    }
    for (int i = 0; i < s.length(); i++) {
        if (freq[s[i] - 'a'] <= 1) {
            cout << s[i] << endl;
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
abc
```
the expected output is:
```text
a
```

For:
```text
banana
```
the expected output is:
```text
b
```

For:
```text
aabc
```
the expected output is:
```text
b
```

For:
```text
aabbc
```
the expected output is:
```text
c
```

---

## Question 20

### Difficulty
Medium

### Bug Type
Word Count With Leading/Trailing Spaces

### Problem
The program counts the number of words in a sentence and prints the total. A word is any run of non-space characters, so the sentence may contain leading, trailing or consecutive spaces without affecting the true count.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a sentence: ";
    getline(cin, s);
    int words = 1;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] == ' ') {
            words++;
        }
    }
    cout << "Words: " << words << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
one two three
```
the expected output is:
```text
Words: 3
```

For:
```text
 hello world
```
the expected output is:
```text
Words: 2
```

For:
```text
a  b
```
the expected output is:
```text
Words: 2
```

---

## Question 21

### Difficulty
Medium

### Bug Type
Remove Duplicate Characters Shift Bug

### Problem
The program removes duplicate letters from a word, keeping only the first occurrence of each distinct letter, and prints the compacted result.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    string result = "";
    for (int i = 0; i < s.length(); i++) {
        bool later = false;
        for (int j = i + 1; j < s.length(); j++) {
            if (s[j] == s[i]) {
                later = true;
            }
        }
        if (!later) {
            result += s[i];
        }
    }
    cout << result << endl;
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
abc
```

For:
```text
banana
```
the expected output is:
```text
ban
```

For:
```text
aabb
```
the expected output is:
```text
ab
```

---

## Question 22

### Difficulty
Medium

### Bug Type
Compress Multiple Spaces Wrong Index

### Problem
The program collapses every run of one or more spaces in a sentence into a single space and prints the compressed result. A single space between words must be preserved.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a sentence: ";
    getline(cin, s);
    int j = 0;
    for (int i = 0; i < s.length(); i++) {
        if (i > 0 && s[i] == ' ' && s[i - 1] != ' ') {
            continue;
        }
        s[j++] = s[i];
    }
    s.resize(j);
    cout << s << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
abcdef
```
the expected output is:
```text
abcdef
```

For:
```text
a b
```
the expected output is:
```text
a b
```

For:
```text
a   b
```
the expected output is:
```text
a b
```

---

## Question 23

### Difficulty
Medium

### Bug Type
Case-Insensitive Compare Missing tolower

### Problem
The program reads two words and prints "Same" when they are equal ignoring case, otherwise it prints "Different".

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string a, b;
    cout << "Enter two words: ";
    cin >> a >> b;
    if (a == b) {
        cout << "Same" << endl;
    } else {
        cout << "Different" << endl;
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
Cat Cat
```
the expected output is:
```text
Same
```

For:
```text
Cat cat
```
the expected output is:
```text
Same
```

For:
```text
HELLO hello
```
the expected output is:
```text
Same
```

---

## Question 24

### Difficulty
Medium

### Bug Type
Character Shift Without Wrap

### Problem
The program shifts every lowercase letter one position forward in the alphabet and prints the result. The alphabet must wrap around, so 'z' becomes 'a'.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] >= 'a' && s[i] <= 'z') {
            s[i] = s[i] + 1;
        }
    }
    cout << s << endl;
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
bcd
```

For:
```text
xyz
```
the expected output is:
```text
yza
```

For:
```text
zebra
```
the expected output is:
```text
afcsb
```

---

## Question 25

### Difficulty
Medium

### Bug Type
Overlapping Substring Count Index Advance

### Problem
The program counts how many times a pattern occurs inside a text, allowing occurrences to overlap. For example, "aa" occurs twice inside "aaa" (at positions 0 and 1).

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s, pat;
    cout << "Enter text and pattern: ";
    cin >> s >> pat;
    int count = 0;
    for (int i = 0; i <= s.length() - pat.length(); i++) {
        bool match = true;
        for (int j = 0; j < pat.length(); j++) {
            if (s[i + j] != pat[j]) {
                match = false;
            }
        }
        if (match) {
            count++;
            i += pat.length() - 1;
        }
    }
    cout << count << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
abcabc abc
```
the expected output is:
```text
2
```

For:
```text
aaaa aa
```
the expected output is:
```text
3
```

For:
```text
aaa aa
```
the expected output is:
```text
2
```

---

## Question 26

### Difficulty
Medium

### Bug Type
Most Frequent Character Wrong Compare

### Problem
The program prints the most frequent letter in a lowercase word. When more than one letter shares the highest frequency, the one that appears earliest in the word must be chosen.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    int freq[26] = {0};
    for (int i = 0; i < s.length(); i++) {
        if (s[i] >= 'a' && s[i] <= 'z') {
            freq[s[i] - 'a']++;
        }
    }
    char best = s[0];
    int bestFreq = 0;
    for (int i = 0; i < s.length(); i++) {
        if (freq[s[i] - 'a'] >= bestFreq) {
            bestFreq = freq[s[i] - 'a'];
            best = s[i];
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
banana
```
the expected output is:
```text
a
```

For:
```text
aabb
```
the expected output is:
```text
a
```

For:
```text
zzww
```
the expected output is:
```text
z
```

---

## Question 27

### Difficulty
Hard

### Bug Type
Two Related Bugs (loop + case)

### Problem
The program counts the vowels (a, e, i, o, u) in a word, ignoring case, and prints the total. The entire word must be scanned and uppercase vowels such as 'A', 'E' and 'U' must also be counted.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    int vowels = 0;
    for (int i = 0; i < s.length() - 1; i++) {
        char c = s[i];
        if (c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u') {
            vowels++;
        }
    }
    cout << "Vowels: " << vowels << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
bird
```
the expected output is:
```text
Vowels: 1
```

For:
```text
APPLE
```
the expected output is:
```text
Vowels: 2
```

For:
```text
upstate
```
the expected output is:
```text
Vowels: 3
```

---

## Question 28

### Difficulty
Hard

### Bug Type
Longest Palindrome Substring Boundary

### Problem
The program finds the longest substring of a word that is a palindrome (reading the same forwards and backwards) and prints it. Both odd-length and even-length palindromes must be considered, e.g. "racecar" and "abba".

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    string longest = "";
    for (int c = 0; c < s.length(); c++) {
        int lo = c, hi = c;
        while (lo - 1 >= 0 && hi + 1 < s.length() && s[lo - 1] == s[hi + 1]) {
            lo--;
            hi++;
        }
        int len = hi - lo + 1;
        if (longest.length() < len) {
            longest = s.substr(lo, len);
        }
    }
    cout << longest << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
racecar
```
the expected output is:
```text
racecar
```

For:
```text
abba
```
the expected output is:
```text
abba
```

For:
```text
noon
```
the expected output is:
```text
noon
```

---

## Question 29

### Difficulty
Hard

### Bug Type
Reverse Words In Place Inner-Loop Error

### Problem
The program reverses the word order of a sentence in place by first reversing the whole string and then reversing the letters of every individual word again. The printed result must have the words in reverse order with correct spelling.

### Buggy Code

```cpp
#include <iostream>
#include <string>
#include <algorithm>
using namespace std;

int main() {
    string s;
    cout << "Enter a sentence: ";
    getline(cin, s);
    reverse(s.begin(), s.end());
    int start = 0;
    for (int i = 0; i <= s.length(); i++) {
        if (i == s.length() || s[i] == ' ') {
            for (int k = start; k < i; k++) {
                char ch = s[k];
                s[k] = s[i - 1 - (k - start)];
                s[i - 1 - (k - start)] = ch;
            }
            start = i + 1;
        }
    }
    cout << s << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
a b c
```
the expected output is:
```text
c b a
```

For:
```text
one two
```
the expected output is:
```text
two one
```

For:
```text
hello world
```
the expected output is:
```text
world hello
```

---

## Question 30

### Difficulty
Hard

### Bug Type
Caesar Cipher Wrap Condition

### Problem
The program performs a Caesar cipher with a shift of 3: every lowercase letter is moved 3 letters forward in the alphabet, wrapping from 'z' back to 'a'. The encrypted word is printed.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    int shift = 3;
    cout << "Enter a word: ";
    cin >> s;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] >= 'a' && s[i] <= 'z') {
            s[i] = s[i] + shift;
            if (s[i] > 'z') {
                s[i] = s[i] - 25;
            }
        }
    }
    cout << s << endl;
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
def
```

For:
```text
xyz
```
the expected output is:
```text
abc
```

For:
```text
taxi
```
the expected output is:
```text
wdal
```

---

## Question 31

### Difficulty
Hard

### Bug Type
String Rotation Check Wrong

### Problem
The program checks whether the second word is a rotation of the first, for example "bcda" is a rotation of "abcd". A rotation keeps all characters but cycles their order, so the two words must have the same length.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string a, b;
    cout << "Enter two words: ";
    cin >> a >> b;
    string doubled = a + a;
    if (doubled.find(b) != string::npos) {
        cout << "Rotation" << endl;
    } else {
        cout << "Not a rotation" << endl;
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
abcd bcda
```
the expected output is:
```text
Rotation
```

For:
```text
ab abab
```
the expected output is:
```text
Not a rotation
```

For:
```text
aba ba
```
the expected output is:
```text
Not a rotation
```

---

## Question 32

### Difficulty
Hard

### Bug Type
Longest Common Prefix Boundary

### Problem
The program finds the longest common prefix of two words (the longest string that is a prefix of both) and prints it between brackets. Only the shared prefix may be shown.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string a, b;
    cout << "Enter two words: ";
    cin >> a >> b;
    int count = 0;
    int limit = a.length() < b.length() ? a.length() : b.length();
    while (count < limit && a[count] == b[count]) {
        count++;
    }
    cout << "[" << a.substr(0, count + 1) << "]" << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
hello hello
```
the expected output is:
```text
[hello]
```

For:
```text
hello hey
```
the expected output is:
```text
[he]
```

For:
```text
abcdef abcxyz
```
the expected output is:
```text
[abc]
```

---

## Question 33

### Difficulty
Hard

### Bug Type
String-to-Int Parsing Sign/Overflow Bug

### Problem
The program converts a numeric string (possibly with a leading minus sign) into an integer using only arithmetic loops, then prints the integer. A string such as "-123" must produce the integer -123.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter an integer: ";
    cin >> s;
    int sign = 1;
    int i = 0;
    if (s[0] == '-') {
        sign = -1;
        i = 1;
    }
    int result = 0;
    for (; i < s.length(); i++) {
        int digit = s[i] - '0';
        result = result * 10 + sign * digit;
    }
    result = result * sign;
    cout << result << endl;
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
123
```

For:
```text
-123
```
the expected output is:
```text
-123
```

For:
```text
-56
```
the expected output is:
```text
-56
```

---

## Question 34

### Difficulty
Hard

### Bug Type
Distinct Substring Counting Bug

### Problem
The program counts the number of distinct substrings of a word and prints the count. For example, "abc" has 6 distinct substrings: "a", "b", "c", "ab", "bc", "abc".

### Buggy Code

```cpp
#include <iostream>
#include <string>
#include <set>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    set<string> subs;
    for (int i = 0; i < s.length(); i++) {
        for (int j = i; j < s.length(); j++) {
            subs.insert(s.substr(i, j - i));
        }
    }
    cout << subs.size() << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
aaa
```
the expected output is:
```text
3
```

For:
```text
ab
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
6
```

---

## Question 35

### Difficulty
Hard

### Bug Type
Anagram Grouping/Frequency Count Bug

### Problem
The program reads a base word and a list of words, then prints how many of those words are anagrams of the base word. An anagram uses exactly the same letters, so letters such as 'z' must be checked exactly like all others.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string base;
    int n;
    cout << "Enter base word and how many words to test: ";
    cin >> base >> n;
    int matches = 0;
    for (int k = 0; k < n; k++) {
        string w;
        cin >> w;
        int freq[26] = {0};
        for (int i = 0; i < base.length(); i++) {
            freq[base[i] - 'a']++;
        }
        for (int i = 0; i < w.length(); i++) {
            freq[w[i] - 'a']--;
        }
        bool same = true;
        for (int i = 0; i < 25; i++) {
            if (freq[i] != 0) {
                same = false;
            }
        }
        if (same) {
            matches++;
        }
    }
    cout << matches << endl;
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
cat
1
tac
```
the expected output is:
```text
1
```

For:
```text
paz
2
pa
azp
```
the expected output is:
```text
1
```

---

## Question 36

### Difficulty
Hard

### Bug Type
Palindrome Ignoring Spaces Boundary

### Problem
The program decides whether a phrase is a palindrome after removing all spaces, and prints "Palindrome" or "Not a palindrome". The decision must be based on the full cleaned-up string, including its innermost characters.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a phrase: ";
    getline(cin, s);
    string clean = "";
    for (int i = 0; i < s.length(); i++) {
        if (s[i] != ' ') {
            clean += s[i];
        }
    }
    bool palindrome = true;
    for (int i = 0; i < clean.length() / 2 - 1; i++) {
        if (clean[i] != clean[clean.length() - 1 - i]) {
            palindrome = false;
        }
    }
    if (palindrome) {
        cout << "Palindrome" << endl;
    } else {
        cout << "Not a palindrome" << endl;
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
no on
```
the expected output is:
```text
Palindrome
```

For:
```text
n aon
```
the expected output is:
```text
Not a palindrome
```

For:
```text
ta cot
```
the expected output is:
```text
Not a palindrome
```

---

## Question 37

### Difficulty
Hard

### Bug Type
Character Replacement With Frequency Limit

### Problem
The program masks a phone number by replacing every digit with 'X', except the last four digits, which stay visible. The result is printed.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a phone number: ";
    cin >> s;
    int total = 0;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] >= '0' && s[i] <= '9') {
            total++;
        }
    }
    int masked = 0;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] >= '0' && s[i] <= '9') {
            masked++;
            if (masked < total - 4) {
                s[i] = 'X';
            }
        }
    }
    cout << s << endl;
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
1234
```

For:
```text
1234567890
```
the expected output is:
```text
XXXXXX7890
```

For:
```text
12345
```
the expected output is:
```text
X2345
```

---

## Question 38

### Difficulty
Hard

### Bug Type
Repeating Pattern Detection Bug

### Problem
The program checks whether a string is made by repeating a shorter substring (e.g. "abab" is "ab" repeated twice) and prints "Repeated" or "Not repeated". Every one of the repeated blocks must be verified.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a string: ";
    cin >> s;
    bool repeated = false;
    for (int k = 1; k <= s.length() / 2; k++) {
        if (s.length() % k != 0) continue;
        bool ok = true;
        for (int j = k; j < s.length() - k; j += k) {
            if (s.substr(0, k) != s.substr(j, k)) {
                ok = false;
            }
        }
        if (ok) {
            repeated = true;
            break;
        }
    }
    if (repeated) {
        cout << "Repeated" << endl;
    } else {
        cout << "Not repeated" << endl;
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
abab
```
the expected output is:
```text
Repeated
```

For:
```text
abcabcabd
```
the expected output is:
```text
Not repeated
```

For:
```text
abxaby
```
the expected output is:
```text
Not repeated
```

---

## Question 39

### Difficulty
Hard

### Bug Type
Compare Strings by Length First (precedence bug)

### Problem
The program classifies a password and prints "Strong" or "Weak". A password is strong only when it has at least 8 characters AND contains either the letter 'A' or the letter 'B'. Both requirements are mandatory.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a password: ";
    cin >> s;
    bool hasA = false, hasB = false;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] == 'A') hasA = true;
        if (s[i] == 'B') hasB = true;
    }
    if (s.length() >= 8 && hasA || hasB) {
        cout << "Strong" << endl;
    } else {
        cout << "Weak" << endl;
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
abcdef12
```
the expected output is:
```text
Weak
```

For:
```text
B
```
the expected output is:
```text
Weak
```

For:
```text
123456B
```
the expected output is:
```text
Weak
```

---

## Question 40

### Difficulty
Hard

### Bug Type
Trim Leading/Trailing Whitespace Boundary

### Problem
The program trims all leading and trailing spaces from a line of text, then prints the trimmed result between brackets. No leading or trailing space may survive.

### Buggy Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a string: ";
    getline(cin, s);
    int start = 0;
    while (start < s.length() && s[start] == ' ') start++;
    int end = s.length();
    while (end > 0 && s[end] == ' ') end--;
    if (start <= end) {
        cout << "[" << s.substr(start, end - start + 1) << "]" << endl;
    } else {
        cout << "[]" << endl;
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
hello
```
the expected output is:
```text
[hello]
```

For:
```text
hello  
```
the expected output is:
```text
[hello]
```

For:
```text
  a  
```
the expected output is:
```text
[a]
```

---

# Solutions

## Solution 1

### Bug
The vowel condition never checks for the letter 'u'.

### Explanation
Only 'a', 'e', 'i' and 'o' are tested, so any word containing 'u' is under-counted. For "quiz" the code counts just the 'i' and prints 1 instead of 2; for "aurora" it prints 3 instead of 4 (the 'u' is skipped). Adding `c == 'u'` to the condition fixes it.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter text: ";
    getline(cin, s);
    int vowels = 0;
    for (char c : s) {
        if (c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u') {
            vowels++;
        }
    }
    cout << vowels << endl;
    return 0;
}
```

## Solution 2

### Bug
The mirror index uses `s.length() - i` instead of `s.length() - 1 - i`.

### Explanation
For i = 0 the program compares `s[0]` with `s[n]`, which is the terminating null character, never with the real last character. That means every palindrome longer than one character is rejected ("madam" and "noon" both print "Not a palindrome" instead of "Palindrome"). The correct mirror of index i is n-1-i.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    bool palindrome = true;
    for (int i = 0; i < s.length() / 2; i++) {
        if (s[i] != s[s.length() - 1 - i]) {
            palindrome = false;
        }
    }
    if (palindrome) {
        cout << "Palindrome" << endl;
    } else {
        cout << "Not a palindrome" << endl;
    }
    return 0;
}
```

## Solution 3

### Bug
The loop starts at index 1, so the first character is never converted.

### Explanation
Index 0 is skipped entirely. "hello" becomes "hELLO" instead of "HELLO" and "day" becomes "dAY" instead of "DAY". Starting the loop at `i = 0` converts every lowercase letter.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] >= 'a' && s[i] <= 'z') {
            s[i] = s[i] - 32;
        }
    }
    cout << s << endl;
    return 0;
}
```

## Solution 4

### Bug
The line `count += 0;` never changes the value of `count`.

### Explanation
The counting update is effectively a no-op, so the total stays 0 forever. For "hello l" the program prints "l appears 0 times." instead of "l appears 2 times.". Replacing the statement with `count++;` fixes the missing update.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    char ch;
    cout << "Enter a string and a character: ";
    cin >> s >> ch;
    int count = 0;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] == ch) {
            count++;
        }
    }
    cout << ch << " appears " << count << " times." << endl;
    return 0;
}
```

## Solution 5

### Bug
The loop bound `i < s.length() - 1` makes the last character invisible.

### Explanation
For "cat" the loop only inspects 'c' and 'a', so the final 't' is never counted: the program prints "Consonants: 1" instead of 2. A single-consonant word like "b" prints 0. Removing the `- 1` scans every character.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    int consonants = 0;
    for (int i = 0; i < s.length(); i++) {
        char c = s[i];
        if (c >= 'a' && c <= 'z' &&
            c != 'a' && c != 'e' && c != 'i' && c != 'o' && c != 'u') {
            consonants++;
        }
    }
    cout << "Consonants: " << consonants << endl;
    return 0;
}
```

## Solution 6

### Bug
The condition also tests `s[i + 1]`, so every space that is not the very last character is counted twice.

### Explanation
A space at position i is counted once for `s[i] == ' '` and again on the previous iteration when it was `s[i + 1]`. For "a b" the single space is counted twice (the loop also reads the harmless null character at `s[s.length()]`, but that never equals a space). Dropping the `|| s[i + 1] == ' '` part counts each space exactly once.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a sentence: ";
    getline(cin, s);
    int spaces = 0;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] == ' ') {
            spaces++;
        }
    }
    cout << "Spaces: " << spaces << endl;
    return 0;
}
```

## Solution 7

### Bug
The loop bound `i <= s.length()` reads the null terminator at `s[s.length()]` as an extra iteration.

### Explanation
For "cat" the loop also prints `3: 0` (the ASCII code of the terminating null character), adding a line the program should not produce. Reading `s[s.length()]` is well-defined (it returns '\0'), but the loop must stop at `i < s.length()` so each real character is printed exactly once.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    for (int i = 0; i < s.length(); i++) {
        cout << i << ": " << (int)s[i] << endl;
    }
    return 0;
}
```

## Solution 8

### Bug
The character test `s[i] == ch` is case-sensitive, but the task requires a case-insensitive search.

### Explanation
"PYTHON p" contains 'P', but 'p' never matches an uppercase letter, so the program prints "Not found" instead of "Found". Comparing both characters after converting them to lowercase (for example with `tolower`) makes the match case-insensitive.

### Corrected Code

```cpp
#include <iostream>
#include <string>
#include <cctype>
using namespace std;

int main() {
    string s;
    char ch;
    cout << "Enter a word and a letter: ";
    cin >> s >> ch;
    bool found = false;
    for (int i = 0; i < s.length(); i++) {
        if (tolower(s[i]) == tolower(ch)) {
            found = true;
        }
    }
    if (found) {
        cout << "Found" << endl;
    } else {
        cout << "Not found" << endl;
    }
    return 0;
}
```

## Solution 9

### Bug
The condition tests the wrong target character: `s[i] == 's'` instead of `s[i] == 't'`.

### Explanation
The task is to replace every 't' with '7'. For "txt" no 's' is present, so the text is returned unchanged ("txt") instead of "7x7". Changing the condition to test 't' replaces exactly the intended characters.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter text: ";
    getline(cin, s);
    for (int i = 0; i < s.length(); i++) {
        if (s[i] == 't') {
            s[i] = '7';
        }
    }
    cout << s << endl;
    return 0;
}
```

## Solution 10

### Bug
Non-digit characters are added to the sum with their raw ASCII value in the else branch.

### Explanation
Digits are converted correctly with `s[i] - '0'`, but a letter such as 'a' (ASCII 97) is added directly. For "2a1" the code computes 2 + 97 + 1 = 100 instead of 3. Deleting the else branch makes non-digits contribute nothing.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a number: ";
    cin >> s;
    int sum = 0;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] >= '0' && s[i] <= '9') {
            sum += s[i] - '0';
        }
    }
    cout << "Sum of digits: " << sum << endl;
    return 0;
}
```

## Solution 11

### Bug
The program capitalizes the last character (`s.length() - 1`) instead of the first one.

### Explanation
For "cat" the code changes the final 't' and prints "caT" instead of "Cat". Index 0 is the first character; capitalizing `s[0]` fulfills the requirement while leaving every other character untouched.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    if (s.length() > 0) {
        if (s[0] >= 'a' && s[0] <= 'z') {
            s[0] = s[0] - 32;
        }
    }
    cout << s << endl;
    return 0;
}
```

## Solution 12

### Bug
The swap loop runs over the whole string instead of only the first half.

### Explanation
Swapping every position with its mirror swaps the string at the start, then swaps it back on the second half of the loop. "abc" is printed as "abc" instead of "cba". Stopping at `i < n / 2` performs every swap exactly once.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a string: ";
    cin >> s;
    int n = s.length();
    for (int i = 0; i < n / 2; i++) {
        char ch = s[i];
        s[i] = s[n - 1 - i];
        s[n - 1 - i] = ch;
    }
    cout << s << endl;
    return 0;
}
```

## Solution 13

### Bug
The words are printed in the original order instead of reversed.

### Explanation
Splitting the sentence works, but the final loop walks the array from index 0 upwards, so "a b c" is printed as "a b c" rather than "c b a". Iterating from `n - 1` down to `0` prints the stored words in reverse order.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a sentence: ";
    getline(cin, s);
    string words[100];
    int n = 0;
    string w = "";
    for (int i = 0; i <= s.length(); i++) {
        if (i == s.length() || s[i] == ' ') {
            words[n++] = w;
            w = "";
        } else {
            w += s[i];
        }
    }
    for (int i = n - 1; i >= 0; i--) {
        if (i < n - 1) cout << " ";
        cout << words[i];
    }
    cout << endl;
    return 0;
}
```

## Solution 14

### Bug
The early length check is inverted, so words of equal length are immediately rejected.

### Explanation
The program returns "Not anagrams" whenever the lengths match, which is exactly when an anagram is possible. "listen"/"silent" print "Not anagrams" instead of "Anagrams". Using `!=` makes the shortcut apply only to lengths that cannot produce an anagram.

### Corrected Code

```cpp
#include <iostream>
#include <string>
#include <algorithm>
using namespace std;

int main() {
    string a, b;
    cout << "Enter two words: ";
    cin >> a >> b;
    if (a.length() != b.length()) {
        cout << "Not anagrams" << endl;
        return 0;
    }
    sort(a.begin(), a.end());
    sort(b.begin(), b.end());
    if (a == b) {
        cout << "Anagrams" << endl;
    } else {
        cout << "Not anagrams" << endl;
    }
    return 0;
}
```

## Solution 15

### Bug
The inner match loop uses `j <= pat.length()`, which also compares against the pattern's terminating null character.

### Explanation
The extra comparison requires `s[i + j]` to equal '\0', which only happens when the candidate match reaches the very end of the text. As a result, "l" in the middle of "hello" is not found (the program prints "Not found"), even though it clearly occurs at position 2. Limiting the inner loop to `j < pat.length()` compares exactly the pattern's characters.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s, pat;
    cout << "Enter text and pattern: ";
    cin >> s >> pat;
    bool found = false;
    for (int i = 0; i <= s.length() - pat.length(); i++) {
        bool match = true;
        for (int j = 0; j < pat.length(); j++) {
            if (s[i + j] != pat[j]) {
                match = false;
            }
        }
        if (match) {
            found = true;
        }
    }
    if (found) {
        cout << "Found" << endl;
    } else {
        cout << "Not found" << endl;
    }
    return 0;
}
```

## Solution 16

### Bug
The substring length passed to `substr` is `len + 1` instead of `len`.

### Explanation
`substr(start, len + 1)` returns one more character than requested. For "abcdef" at start 1, length 3, the program prints "bcde" instead of "bcd". When the requested slice reaches the end of the string the extra character is clamped away, which is why a trailing slice still works. Passing exactly `len` fixes the boundary.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    int start, len;
    cout << "Enter a string, start index and length: ";
    cin >> s >> start >> len;
    cout << s.substr(start, len) << endl;
    return 0;
}
```

## Solution 17

### Bug
The overwrite cursor `j` is incremented for space characters too, so spaces are never squeezed out.

### Explanation
Every non-space writes at `s[j]`, but `j` also advances on the space iterations. For "a b" the write cursor ends at 3, so the resized string still contains the original space ("a b") instead of "ab". Moving `j++` inside the `if` makes the compacted length correct.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a sentence: ";
    getline(cin, s);
    int j = 0;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] != ' ') {
            s[j++] = s[i];
        }
    }
    s.resize(j);
    cout << s << endl;
    return 0;
}
```

## Solution 18

### Bug
The uppercase branch subtracts 32 (instead of adding 32), corrupting capital letters into punctuation.

### Explanation
Lowercase letters are converted upward correctly, but an uppercase letter such as 'A' (65) minus 32 is '!' (33). "ABC" becomes `!"#` and "Zoom" becomes `*OOM` instead of "zOOM". The uppercase branch must add 32.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] >= 'a' && s[i] <= 'z') {
            s[i] = s[i] - 32;
        } else if (s[i] >= 'A' && s[i] <= 'Z') {
            s[i] = s[i] + 32;
        }
    }
    cout << s << endl;
    return 0;
}
```

## Solution 19

### Bug
The frequency table stores how many OTHER identical characters exist, and the scan accepts any count of 0 or 1. That also selects characters that appear twice.

### Explanation
A letter appearing twice has 1 "other" occurrence, so the `<= 1` check accepts it. For "aabc" the program prints 'a' (which repeats) instead of the first truly unique character 'b'. Because a unique character has exactly 0 other occurrences, the check must be `freq[s[i] - 'a'] == 0`.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    int freq[26] = {0};
    for (int i = 0; i < s.length(); i++) {
        for (int j = 0; j < s.length(); j++) {
            if (i != j && s[i] == s[j]) {
                freq[s[i] - 'a']++;
            }
        }
    }
    for (int i = 0; i < s.length(); i++) {
        if (freq[s[i] - 'a'] == 0) {
            cout << s[i] << endl;
            return 0;
        }
    }
    cout << "None" << endl;
    return 0;
}
```

## Solution 20

### Bug
The program simply adds 1 per space (starting at 1), which assumes a normal word can never be preceded or followed by extra spaces.

### Explanation
Leading, trailing or consecutive spaces all inflate the count. " hello world" has two spaces but only two words, yet the program prints 3. The corrected version tracks whether the previous character was already part of a word, incrementing once per transition from space to non-space.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a sentence: ";
    getline(cin, s);
    int words = 0;
    bool inWord = false;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] != ' ') {
            if (!inWord) {
                words++;
                inWord = true;
            }
        } else {
            inWord = false;
        }
    }
    cout << "Words: " << words << endl;
    return 0;
}
```

## Solution 21

### Bug
The inner scan looks AHEAD for the same letter and drops the letter when it repeats later, which keeps the last occurrence of each letter instead of the first.

### Explanation
For "banana" the program keeps 'b' (index 0), then the later 'n' and 'a', producing "bna" instead of "ban". A keep-first algorithm must look BACKWARD: a letter is kept only when no earlier position already contains it.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    string result = "";
    for (int i = 0; i < s.length(); i++) {
        bool earlier = false;
        for (int j = 0; j < i; j++) {
            if (s[j] == s[i]) {
                earlier = true;
            }
        }
        if (!earlier) {
            result += s[i];
        }
    }
    cout << result << endl;
    return 0;
}
```

## Solution 22

### Bug
The skip condition is inverted: a space is dropped only when the previous character is NOT a space.

### Explanation
A run of spaces should skip every space except the first one (when the previous character is a space). The condition currently deletes the first space of each run and keeps the rest, so "a b" becomes "ab" and "a   b" becomes "a  b". Reversing the test to `s[i - 1] == ' '` keeps exactly one space per run.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a sentence: ";
    getline(cin, s);
    int j = 0;
    for (int i = 0; i < s.length(); i++) {
        if (i > 0 && s[i] == ' ' && s[i - 1] == ' ') {
            continue;
        }
        s[j++] = s[i];
    }
    s.resize(j);
    cout << s << endl;
    return 0;
}
```

## Solution 23

### Bug
The comparison `a == b` is case-sensitive, but the task demands a case-insensitive equality check.

### Explanation
"Cat" and "cat" differ only by case, yet the program prints "Different" instead of "Same". The corrected code compares each character after conversion to lowercase (via `tolower`), which also rejects strings of unequal length.

### Corrected Code

```cpp
#include <iostream>
#include <string>
#include <cctype>
using namespace std;

int main() {
    string a, b;
    cout << "Enter two words: ";
    cin >> a >> b;
    bool same = a.length() == b.length();
    for (int i = 0; i < (int)a.length() && same; i++) {
        if (tolower(a[i]) != tolower(b[i])) {
            same = false;
        }
    }
    if (same) {
        cout << "Same" << endl;
    } else {
        cout << "Different" << endl;
    }
    return 0;
}
```

## Solution 24

### Bug
Letters are shifted without wrapping, so 'z' (and everything past it) is replaced by the next ASCII symbol.

### Explanation
'z' + 1 is '{', not 'a'. "xyz" becomes "yz{" instead of "yza" and "zebra" becomes "{fcsb" instead of "afcsb". The corrected code maps each letter to the range 0-25, adds 1, takes the modulo 26, then maps back, so the shift wraps cleanly.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] >= 'a' && s[i] <= 'z') {
            s[i] = (s[i] - 'a' + 1) % 26 + 'a';
        }
    }
    cout << s << endl;
    return 0;
}
```

## Solution 25

### Bug
After a successful match the code jumps the search index forward over the whole match (`i += pat.length() - 1` plus the loop increment), so overlapping occurrences are never counted.

### Explanation
The task counts overlapping matches. For "aaaa" / "aa" the correct answer is 3 (positions 0, 1, 2), but the program advances past each match and counts only 2. Removing the index jump lets the loop test every starting position.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s, pat;
    cout << "Enter text and pattern: ";
    cin >> s >> pat;
    int count = 0;
    for (int i = 0; i <= s.length() - pat.length(); i++) {
        bool match = true;
        for (int j = 0; j < pat.length(); j++) {
            if (s[i + j] != pat[j]) {
                match = false;
            }
        }
        if (match) {
            count++;
        }
    }
    cout << count << endl;
    return 0;
}
```

## Solution 26

### Bug
The comparison `>=` overwrites the best answer whenever a later character ties the current frequency, so the earliest tied character is lost.

### Explanation
The rule is: on a tie, print the character that appears earliest. For "aabb" both 'a' and 'b' appear twice; the scan meets 'b' later and `>=` replaces 'a', printing 'b' instead of 'a'. Using a strict `>` keeps the first character that reaches the maximum.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    int freq[26] = {0};
    for (int i = 0; i < s.length(); i++) {
        if (s[i] >= 'a' && s[i] <= 'z') {
            freq[s[i] - 'a']++;
        }
    }
    char best = s[0];
    int bestFreq = 0;
    for (int i = 0; i < s.length(); i++) {
        if (freq[s[i] - 'a'] > bestFreq) {
            bestFreq = freq[s[i] - 'a'];
            best = s[i];
        }
    }
    cout << best << endl;
    return 0;
}
```

## Solution 27

### Bug
There are two related defects: (1) the loop runs only while `i < s.length() - 1`, hiding the last character, and (2) only lowercase vowels are checked, so uppercase vowels are not counted.

### Explanation
"APPLE" counts 0 because uppercase 'A' and 'E' are ignored. "upstate" counts 2 instead of 3 because the final 'e' is skipped. The corrected version scans the full range and normalizes each letter to lowercase before the vowel test.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    int vowels = 0;
    for (int i = 0; i < s.length(); i++) {
        char c = s[i];
        if (c >= 'A' && c <= 'Z') {
            c = c + 32;
        }
        if (c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u') {
            vowels++;
        }
    }
    cout << "Vowels: " << vowels << endl;
    return 0;
}
```

## Solution 28

### Bug
The expansion only starts from a center of length 1, so even-length palindromes (a pair of equal middle letters) are never examined.

### Explanation
"racecar" is odd-length and is found correctly. "abba" and "noon" are even-length; their centers are the pairs 'bb' / 'oo', which the code never expands, so it prints a one-letter substring instead of the full palindrome. Adding a second expansion pass that starts with two equal center characters (at `c` and `c + 1`) covers even palindromes.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    string longest = "";
    for (int c = 0; c < s.length(); c++) {
        for (int t = 0; t < 2; t++) {
            int lo = c, hi = c + t;
            while (lo >= 0 && hi < s.length() && s[lo] == s[hi]) {
                int len = hi - lo + 1;
                if (longest.length() < len) {
                    longest = s.substr(lo, len);
                }
                lo--;
                hi++;
            }
        }
    }
    cout << longest << endl;
    return 0;
}
```

## Solution 29

### Bug
The inner loop swaps a whole word from end to end, so every pair is swapped twice and the word ends up exactly as it was after the global reversal.

### Explanation
After the global reversal, "one two" becomes "owt eno". The per-word reversal is supposed to restore the spelling of each word, but because the loop runs `k < i`, each letter is swapped there and back again: the output stays "owt eno" instead of "two one". Reversing only the first half of each word (`k < (start + i) / 2`) does each swap once.

### Corrected Code

```cpp
#include <iostream>
#include <string>
#include <algorithm>
using namespace std;

int main() {
    string s;
    cout << "Enter a sentence: ";
    getline(cin, s);
    reverse(s.begin(), s.end());
    int start = 0;
    for (int i = 0; i <= s.length(); i++) {
        if (i == s.length() || s[i] == ' ') {
            for (int k = start; k < (start + i) / 2; k++) {
                char ch = s[k];
                s[k] = s[i - 1 - (k - start)];
                s[i - 1 - (k - start)] = ch;
            }
            start = i + 1;
        }
    }
    cout << s << endl;
    return 0;
}
```

## Solution 30

### Bug
The wrap subtracts 25 instead of 26, so wrapped letters land one step too far.

### Explanation
After adding the shift, letters beyond 'z' must be reduced by a full alphabet of 26. 'x', 'y', 'z' with shift 3 become '{','|','}', and subtracting 25 yields 'b','c','d' instead of 'a','b','c'. "xyz" prints "bcd" instead of "abc"; subtracting 26 fixes every wrap.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    int shift = 3;
    cout << "Enter a word: ";
    cin >> s;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] >= 'a' && s[i] <= 'z') {
            s[i] = s[i] + shift;
            if (s[i] > 'z') {
                s[i] = s[i] - 26;
            }
        }
    }
    cout << s << endl;
    return 0;
}
```

## Solution 31

### Bug
The rotation check only tests whether `b` appears inside `a + a`; it never verifies that the strings have the same length.

### Explanation
A rotation must preserve length. "ab" is length 2 while "abab" is length 4, yet "abab" appears inside "ab" + "ab" and the program prints "Rotation". Adding the length equality condition to the `find` test rejects those false positives.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string a, b;
    cout << "Enter two words: ";
    cin >> a >> b;
    string doubled = a + a;
    if (a.length() == b.length() && doubled.find(b) != string::npos) {
        cout << "Rotation" << endl;
    } else {
        cout << "Not a rotation" << endl;
    }
    return 0;
}
```

## Solution 32

### Bug
The printed slice uses `count + 1` as its length, so one character beyond the common prefix is included.

### Explanation
When the whole word matches (count equals the full length) `substr` clamps and the output is still correct, but for a partial match an extra character leaks out: "hello" / "hey" should print "[he]" but the program prints "[hel]". Using `a.substr(0, count)` yields exactly the shared prefix.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string a, b;
    cout << "Enter two words: ";
    cin >> a >> b;
    int count = 0;
    int limit = a.length() < b.length() ? a.length() : b.length();
    while (count < limit && a[count] == b[count]) {
        count++;
    }
    cout << "[" << a.substr(0, count) << "]" << endl;
    return 0;
}
```

## Solution 33

### Bug
The sign is applied twice: it is folded into every digit while accumulating AND multiplied once more at the end, so negative numbers come out positive.

### Explanation
For "-123" the running value is -1, -12, -123, and then `result * sign` makes it +123. The corrected build-up uses plain digits; the sign is applied exactly once, at the very end.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter an integer: ";
    cin >> s;
    int sign = 1;
    int i = 0;
    if (s[0] == '-') {
        sign = -1;
        i = 1;
    }
    int result = 0;
    for (; i < s.length(); i++) {
        int digit = s[i] - '0';
        result = result * 10 + digit;
    }
    result = result * sign;
    cout << result << endl;
    return 0;
}
```

## Solution 34

### Bug
The substring length `j - i` drops the final character of every substring (an empty string is inserted instead).

### Explanation
A substring from i to j should contain `j - i + 1` characters. With the bug, "ab" only builds "" and "a" for the first position, so its distinct set has size 2 instead of 3, and "abc" gives 4 instead of 6. Fixing the length to `j - i + 1` builds each substring completely.

### Corrected Code

```cpp
#include <iostream>
#include <string>
#include <set>
using namespace std;

int main() {
    string s;
    cout << "Enter a word: ";
    cin >> s;
    set<string> subs;
    for (int i = 0; i < s.length(); i++) {
        for (int j = i; j < s.length(); j++) {
            subs.insert(s.substr(i, j - i + 1));
        }
    }
    cout << subs.size() << endl;
    return 0;
}
```

## Solution 35

### Bug
The final frequency verification loop only runs to index 25, so the 'z' slot (index 25) is never inspected.

### Explanation
A mismatch that affects only the letter 'z' goes unnoticed. For the base word "paz" and the test word "pa", the 'z' leftover sits at index 25, so the program wrongly counts it as a match (2 matches instead of 1). Iterating over all 26 letters makes the test exact.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string base;
    int n;
    cout << "Enter base word and how many words to test: ";
    cin >> base >> n;
    int matches = 0;
    for (int k = 0; k < n; k++) {
        string w;
        cin >> w;
        int freq[26] = {0};
        for (int i = 0; i < base.length(); i++) {
            freq[base[i] - 'a']++;
        }
        for (int i = 0; i < w.length(); i++) {
            freq[w[i] - 'a']--;
        }
        bool same = true;
        for (int i = 0; i < 26; i++) {
            if (freq[i] != 0) {
                same = false;
            }
        }
        if (same) {
            matches++;
        }
    }
    cout << matches << endl;
    return 0;
}
```

## Solution 36

### Bug
The palindrome loop stops at `clean.length() / 2 - 1`, which skips the innermost character pair for even-length strings (and the middle itself for odd-length ones).

### Explanation
For "no on" the cleaned text is "noon"; the pair (1, 2) is never compared, but since it matches, the result is still correct. For "n aon" the cleaned text is "naon", whose inner pair 'a' and 'o' differ — yet that pair is skipped and the program wrongly prints "Palindrome". Comparing while `i < clean.length() / 2` visits every required pair.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a phrase: ";
    getline(cin, s);
    string clean = "";
    for (int i = 0; i < s.length(); i++) {
        if (s[i] != ' ') {
            clean += s[i];
        }
    }
    bool palindrome = true;
    for (int i = 0; i < clean.length() / 2; i++) {
        if (clean[i] != clean[clean.length() - 1 - i]) {
            palindrome = false;
        }
    }
    if (palindrome) {
        cout << "Palindrome" << endl;
    } else {
        cout << "Not a palindrome" << endl;
    }
    return 0;
}
```

## Solution 37

### Bug
The masking condition `masked < total - 4` leaves one extra digit visible in the middle.

### Explanation
Exactly `total - 4` digits must be hidden. For "1234567890" the first six digits must become 'X', but the condition stops after five, printing "XXXXX67890" instead of "XXXXXX7890". Changing `<` to `<=` masks all digits up to and including the `total - 4` th one.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a phone number: ";
    cin >> s;
    int total = 0;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] >= '0' && s[i] <= '9') {
            total++;
        }
    }
    int masked = 0;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] >= '0' && s[i] <= '9') {
            masked++;
            if (masked <= total - 4) {
                s[i] = 'X';
            }
        }
    }
    cout << s << endl;
    return 0;
}
```

## Solution 38

### Bug
The inner loop stops at `s.length() - k`, so the final repeating block is never checked against the first block.

### Explanation
For "abcabcabd" the candidate period 3 checks block 2 but never verifies the last block "abd" against "abc", so it wrongly prints "Repeated". Extending the loop to run while `j < s.length()` compares every full block, including the last one.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a string: ";
    cin >> s;
    bool repeated = false;
    for (int k = 1; k <= s.length() / 2; k++) {
        if (s.length() % k != 0) continue;
        bool ok = true;
        for (int j = k; j < s.length(); j += k) {
            if (s.substr(0, k) != s.substr(j, k)) {
                ok = false;
            }
        }
        if (ok) {
            repeated = true;
            break;
        }
    }
    if (repeated) {
        cout << "Repeated" << endl;
    } else {
        cout << "Not repeated" << endl;
    }
    return 0;
}
```

## Solution 39

### Bug
Missing parentheses make `&&` bind tighter than `||`, so the condition is evaluated as `(length >= 8 && hasA) || hasB`.

### Explanation
Because of operator precedence, the presence of a single 'B' satisfies the whole condition regardless of length: "B" is reported as "Strong" and "123456B" as well, though both should be "Weak". Both sides of the length requirement must be grouped: length 8 or more AND (has 'A' OR has 'B').

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a password: ";
    cin >> s;
    bool hasA = false, hasB = false;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] == 'A') hasA = true;
        if (s[i] == 'B') hasB = true;
    }
    if (s.length() >= 8 && (hasA || hasB)) {
        cout << "Strong" << endl;
    } else {
        cout << "Weak" << endl;
    }
    return 0;
}
```

## Solution 40

### Bug
The end index is initialized to `s.length()` instead of `s.length() - 1`, so the trailing-trim loop first inspects the null terminator at `s[s.length()]`, decides it is not a space, and stops immediately.

### Explanation
Because the backwards scan never moves, every trailing space survives: "hello  " prints "[hello  ]" instead of "[hello]" and "  a  " prints "[a  ]" instead of "[a]". Starting `end` at `s.length() - 1` (plus the existing `end > 0` guard) trims the whole run of spaces at the end.

### Corrected Code

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;
    cout << "Enter a string: ";
    getline(cin, s);
    int start = 0;
    while (start < s.length() && s[start] == ' ') start++;
    int end = s.length() - 1;
    while (end > 0 && s[end] == ' ') end--;
    if (start <= end) {
        cout << "[" << s.substr(start, end - start + 1) << "]" << endl;
    } else {
        cout << "[]" << endl;
    }
    return 0;
}
```