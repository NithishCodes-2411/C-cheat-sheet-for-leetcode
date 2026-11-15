# C++ Data Structures Cheat Sheet (LeetCode)

A beginner-friendly reference to common C++ data structures, their main functions, and what those functions do.

## 0. Setup

```cpp
#include <bits/stdc++.h>
using namespace std;
```

LeetCode usually provides the class and function wrapper. You normally write your solution inside the required function.

---

## 1. Vector (`vector`)

A **dynamic array**: stores elements in order, allows indexing, and can grow or shrink.

### Common vector types

| Declaration | Stores | Example |
|---|---|---|
| `vector<int> v;` | Integers | `{1, 2, 3}` |
| `vector<double> v;` | Decimal numbers | `{1.5, 2.7}` |
| `vector<char> v;` | Characters | `{'a', 'b', 'c'}` |
| `vector<string> v;` | Strings / words | `{"cat", "dog"}` |
| `vector<bool> v;` | Boolean values | `{true, false}` |
| `vector<vector<int>> grid;` | 2D integer data (matrix) | `{{1, 2}, {3, 4}}` |
| `vector<vector<string>> words;` | 2D string data | `{{"a", "b"}, {"c"}}` |

### Vector functions

| Function / syntax | What it does | Before → After / result |
|---|---|---|
| `v.push_back(x)` | Adds `x` to the end. | `[1, 2]` → `[1, 2, 3]` |
| `v.pop_back()` | Removes the last element. | `[1, 2, 3]` → `[1, 2]` |
| `v[i]` | Reads or changes the element at index `i` (starts at 0). | `[4, 8, 9]` → `v[1]` is `8` |
| `v.at(i)` | Accesses index `i` with bounds checking. | `[4, 8]` → `v.at(0)` is `4` |
| `v.front()` | Gets the first element. | `[4, 8, 9]` → `4` |
| `v.back()` | Gets the last element. | `[4, 8, 9]` → `9` |
| `v.size()` | Returns the number of elements. | `[4, 8, 9]` → `3` |
| `v.empty()` | Checks whether the vector has no elements. | `[]` → `true` |
| `v.clear()` | Removes all elements. | `[1, 2]` → `[]` |
| `v.insert(v.begin()+1, 7)` | Inserts `7` before index 1. | `[1, 2, 3]` → `[1, 7, 2, 3]` |
| `v.erase(v.begin()+1)` | Removes the element at index 1. | `[1, 2, 3]` → `[1, 3]` |
| `v.begin()` / `v.end()` | Gets iterators to the start / position after the end. Used by STL algorithms. | `[2, 4]` → range `[begin, end)` |
| `sort(v.begin(), v.end())` | Sorts ascending. | `[3, 1, 2]` → `[1, 2, 3]` |
| `reverse(v.begin(), v.end())` | Reverses the elements. | `[1, 2, 3]` → `[3, 2, 1]` |

### Creating vectors

```cpp
vector<int> a;             // empty vector
vector<int> b(5);          // 5 elements, each initialized to 0
vector<int> c(5, 9);       // 5 elements, each equal to 9
vector<int> d = {1, 2, 3}; // initialized with values

vector<vector<int>> grid(3, vector<int>(4, 0));
// 3 rows, 4 columns, all values are 0
```

### Loop through a vector

```cpp
for (int x : nums) {
    cout << x << " ";
}

// With indexes
for (int i = 0; i < nums.size(); i++) {
    cout << nums[i] << " ";
}
```

---

## 2. String (`string`)

A sequence of characters. C++ strings can grow and shrink.

| Function / syntax | What it does | Before → After / result |
|---|---|---|
| `s[i]` | Reads or changes the character at index `i`. | `"cat"` → `s[0]` is `'c'` |
| `s.size()` / `s.length()` | Returns the number of characters. | `"hello"` → `5` |
| `s.empty()` | Checks whether the string is empty. | `""` → `true` |
| `s.push_back('!')` | Adds one character to the end. | `"hi"` → `"hi!"` |
| `s.pop_back()` | Removes the last character. | `"hi!"` → `"hi"` |
| `s += "!"` | Appends text. | `"hello"` → `"hello!"` |
| `s.substr(1, 3)` | Gets 3 characters starting at index 1. | `"abcdef"` → `"bcd"` |
| `s.find("cd")` | Finds the first position of a substring; returns `string::npos` if absent. | `"abcdef"` → `2` |
| `s.erase(1, 2)` | Removes 2 characters starting at index 1. | `"abcdef"` → `"adef"` |
| `s.insert(1, "XY")` | Inserts text at index 1. | `"abc"` → `"aXYbc"` |
| `reverse(s.begin(), s.end())` | Reverses the string. | `"cat"` → `"tac"` |
| `sort(s.begin(), s.end())` | Sorts characters. | `"cab"` → `"abc"` |

**Important:** Use single quotes for one character (`'a'`) and double quotes for a string (`"apple"`).

---

## 3. Array (`array` and normal arrays)

An **array** stores a fixed number of elements. Unlike a vector, its size cannot grow or shrink.

| Declaration | What it means | Example |
|---|---|---|
| `int a[3] = {1, 2, 3};` | Fixed-size integer array. | `a[0]` is `1` |
| `char letters[3] = {'a', 'b', 'c'};` | Fixed-size character array. | `letters[1]` is `'b'` |
| `array<int, 3> a = {1, 2, 3};` | STL fixed-size array. | `a.size()` is `3` |

| Function / syntax | What it does | Before → After / result |
|---|---|---|
| `a[i]` | Reads or changes an element. | `[5, 6, 7]` → `a[1]` is `6` |
| `a.size()` | Returns the fixed number of elements (`std::array`). | `[5, 6, 7]` → `3` |
| `a.fill(0)` | Sets every element to the same value (`std::array`). | `[5, 6, 7]` → `[0, 0, 0]` |

---

## 4. Linked Lists (`list` and `forward_list`)

A linked list stores elements in separate nodes connected by links. It does not support indexing like `v[i]`.

### `list<int>` — doubly linked list

| Function | What it does | Before → After / result |
|---|---|---|
| `l.push_back(3)` | Adds to the end. | `[1, 2]` → `[1, 2, 3]` |
| `l.push_front(0)` | Adds to the beginning. | `[1, 2]` → `[0, 1, 2]` |
| `l.pop_back()` | Removes the last element. | `[1, 2, 3]` → `[1, 2]` |
| `l.pop_front()` | Removes the first element. | `[1, 2, 3]` → `[2, 3]` |
| `l.front()` / `l.back()` | Reads the first / last element. | `[1, 2, 3]` → `1` / `3` |
| `l.insert(it, x)` | Inserts `x` before iterator `it`. | `[1, 3]` → `[1, 2, 3]` |
| `l.erase(it)` | Removes the element at iterator `it`. | `[1, 2, 3]` → `[1, 3]` |
| `l.size()` / `l.empty()` | Gets count / checks if empty. | `[1, 2]` → `2` / `false` |
| `l.sort()` | Sorts the list. | `[3, 1, 2]` → `[1, 2, 3]` |
| `l.reverse()` | Reverses the list. | `[1, 2, 3]` → `[3, 2, 1]` |

### `forward_list<int>` — singly linked list

| Function | What it does | Before → After / result |
|---|---|---|
| `fl.push_front(x)` | Adds to the beginning. | `[2, 3]` → `[1, 2, 3]` |
| `fl.pop_front()` | Removes the first element. | `[1, 2, 3]` → `[2, 3]` |
| `fl.insert_after(it, x)` | Inserts after an iterator. | `[1, 3]` → `[1, 2, 3]` |
| `fl.erase_after(it)` | Removes the item after an iterator. | `[1, 2, 3]` → `[1, 3]` |

---

## 5. Deque (`deque`)

A **double-ended queue**: allows adding and removing elements at both the front and back. Supports indexing.

| Function | What it does | Before → After / result |
|---|---|---|
| `d.push_front(x)` | Adds to the front. | `[2, 3]` → `[1, 2, 3]` |
| `d.push_back(x)` | Adds to the back. | `[1, 2]` → `[1, 2, 3]` |
| `d.pop_front()` | Removes the front element. | `[1, 2, 3]` → `[2, 3]` |
| `d.pop_back()` | Removes the last element. | `[1, 2, 3]` → `[1, 2]` |
| `d.front()` / `d.back()` | Reads the first / last element. | `[1, 2, 3]` → `1` / `3` |
| `d[i]` | Accesses an element by index. | `[1, 2, 3]` → `d[1]` is `2` |

---

## 6. Stack (`stack`)

Follows **LIFO**: Last In, First Out. Think of a stack of plates.

| Function | What it does | Before → After / result |
|---|---|---|
| `st.push(x)` | Adds an item to the top. | `[1, 2]` → `[1, 2, 3]` |
| `st.top()` | Reads the top item. | `[1, 2, 3]` → `3` |
| `st.pop()` | Removes the top item. | `[1, 2, 3]` → `[1, 2]` |
| `st.size()` | Returns the number of items. | `[1, 2, 3]` → `3` |
| `st.empty()` | Checks whether the stack is empty. | `[]` → `true` |

```cpp
stack<int> st;
st.push(10);
st.push(20);
int x = st.top(); // 20
st.pop();         // removes 20
```

---

## 7. Queue (`queue`)

Follows **FIFO**: First In, First Out. Think of a line of people.

| Function | What it does | Before → After / result |
|---|---|---|
| `q.push(x)` | Adds an item to the back. | `[1, 2]` → `[1, 2, 3]` |
| `q.front()` | Reads the first item. | `[1, 2, 3]` → `1` |
| `q.back()` | Reads the last item. | `[1, 2, 3]` → `3` |
| `q.pop()` | Removes the first item. | `[1, 2, 3]` → `[2, 3]` |
| `q.size()` | Returns the number of items. | `[1, 2, 3]` → `3` |
| `q.empty()` | Checks whether the queue is empty. | `[]` → `true` |

---

## 8. Priority Queue (`priority_queue`)

A **heap**: gives quick access to the highest- or lowest-priority value.

### Max-heap (default)

The largest value is at the top.

| Function | What it does | Before → After / result |
|---|---|---|
| `pq.push(x)` | Adds a value. | `{2, 5}` + `3` → `{2, 3, 5}` |
| `pq.top()` | Reads the largest value. | `{2, 5, 3}` → `5` |
| `pq.pop()` | Removes the largest value. | `{2, 5, 3}` → top becomes `3` |
| `pq.size()` / `pq.empty()` | Gets count / checks if empty. | `{2, 5, 3}` → `3` / `false` |

```cpp
priority_queue<int> maxHeap;
```

### Min-heap

The smallest value is at the top.

```cpp
priority_queue<int, vector<int>, greater<int>> minHeap;
```

| Operation | Before → After / result |
|---|---|
| `minHeap.push(2); minHeap.push(5);` | Values: `{2, 5}` |
| `minHeap.top()` | `2` |
| `minHeap.pop()` | Removes `2`; next top is `5` |

---

## 9. Set (`set`, `multiset`, `unordered_set`)

A set stores values without using numeric indexes.

### `set<int>`

Stores **unique values in sorted order**.

| Function | What it does | Before → After / result |
|---|---|---|
| `s.insert(x)` | Adds a value if it is not already present. | `{1, 3}` → insert `2` → `{1, 2, 3}` |
| `s.erase(x)` | Removes the value. | `{1, 2, 3}` → erase `2` → `{1, 3}` |
| `s.count(x)` | Checks whether `x` exists (0 or 1). | `{1, 3}` → `count(3)` is `1` |
| `s.find(x)` | Returns an iterator to `x`, or `s.end()` if absent. | `{1, 3}` → find `3` gives iterator to `3` |
| `s.size()` / `s.empty()` | Gets count / checks if empty. | `{1, 3}` → `2` / `false` |

### Other set types

| Type | What makes it different | Example |
|---|---|---|
| `set<int>` | Unique values, sorted. | Insert `2, 1, 2` → `{1, 2}` |
| `multiset<int>` | Allows duplicates, sorted. | Insert `2, 1, 2` → `{1, 2, 2}` |
| `unordered_set<int>` | Unique values, no guaranteed order; average O(1) lookup. | Insert `2, 1, 2` → contains `1` and `2` |

---

## 10. Map (`map`, `multimap`, `unordered_map`)

A map stores **key-value pairs**. Use a key to find its value.

### `map<int, string>`

Stores unique keys in sorted order.

| Function | What it does | Before → After / result |
|---|---|---|
| `m[key] = value` | Inserts or updates a key-value pair. | `{}` → `m[1]="Sam"` → `{1:"Sam"}` |
| `m[key]` | Reads the value for a key; creates a default value if the key is missing. | `{1:"Sam"}` → `m[1]` is `"Sam"` |
| `m.count(key)` | Checks whether a key exists (0 or 1). | `{1:"Sam"}` → `count(1)` is `1` |
| `m.erase(key)` | Removes a key and its value. | `{1:"Sam", 2:"Ana"}` → erase `1` → `{2:"Ana"}` |
| `m.find(key)` | Finds a key; returns `m.end()` if absent. | `{1:"Sam"}` → find `1` gives iterator |
| `m.size()` / `m.empty()` | Gets pair count / checks if empty. | `{1:"Sam"}` → `1` / `false` |

### Other map types

| Type | What makes it different | Example |
|---|---|---|
| `map<int, string>` | Unique keys, sorted by key. | Keys `3, 1` → `1, 3` |
| `multimap<int, string>` | Allows duplicate keys, sorted by key. | Key `1` can map to `"A"` and `"B"` |
| `unordered_map<int, string>` | Unique keys, no guaranteed order; average O(1) lookup. | `m[1] = "A"` |

### Frequency counter example

```cpp
vector<int> nums = {2, 2, 3, 4, 2};
unordered_map<int, int> freq;

for (int x : nums) {
    freq[x]++;
}

// freq[2] = 3, freq[3] = 1, freq[4] = 1
```

---

## 11. Pair and Tuple

Useful for grouping multiple values together.

| Type / syntax | What it does | Example |
|---|---|---|
| `pair<int, string> p = {1, "Sam"};` | Stores two values. | `p.first` → `1`; `p.second` → `"Sam"` |
| `tuple<int, string, double> t = {1, "Sam", 2.5};` | Stores three or more values. | `get<1>(t)` → `"Sam"` |
| `make_pair(2, "cat")` | Creates a pair. | `{2, "cat"}` |

---

## 12. Common STL Algorithms

Include `<algorithm>` (already covered by `bits/stdc++.h`).

| Function | What it does | Before → After / result |
|---|---|---|
| `sort(v.begin(), v.end())` | Sorts ascending. | `[3, 1, 2]` → `[1, 2, 3]` |
| `sort(v.rbegin(), v.rend())` | Sorts descending. | `[1, 3, 2]` → `[3, 2, 1]` |
| `reverse(v.begin(), v.end())` | Reverses a range. | `[1, 2, 3]` → `[3, 2, 1]` |
| `find(v.begin(), v.end(), x)` | Finds `x`; returns `end()` if not found. | `[4, 7, 9]`, find `7` → iterator to `7` |
| `count(v.begin(), v.end(), x)` | Counts occurrences of `x`. | `[1, 2, 2, 3]` → `2` occurs twice |
| `min(a, b)` / `max(a, b)` | Returns the smaller / larger value. | `min(4, 9)` → `4` |
| `min_element(v.begin(), v.end())` | Finds an iterator to the smallest element. | `[4, 1, 7]` → iterator to `1` |
| `max_element(v.begin(), v.end())` | Finds an iterator to the largest element. | `[4, 1, 7]` → iterator to `7` |
| `lower_bound(v.begin(), v.end(), x)` | In a sorted range, finds first value `>= x`. | `[1, 3, 5]`, `x=4` → `5` |
| `upper_bound(v.begin(), v.end(), x)` | In a sorted range, finds first value `> x`. | `[1, 3, 3, 5]`, `x=3` → `5` |
| `accumulate(v.begin(), v.end(), 0)` | Adds all values (`<numeric>`). | `[1, 2, 3]` → `6` |
| `next_permutation(v.begin(), v.end())` | Changes to the next lexicographical order. | `[1, 2, 3]` → `[1, 3, 2]` |

To read a value from an iterator returned by `find`, `min_element`, or similar:

```cpp
auto it = find(v.begin(), v.end(), 7);
if (it != v.end()) {
    cout << *it; // prints 7
}
```

---

## 13. Quick comparison: which data structure should I use?

| Need | Use |
|---|---|
| A growable list with index access | `vector` |
| A fixed-size collection | `array` |
| Text / characters | `string` |
| Insert/remove at both ends | `deque` |
| Frequent insert/remove using list iterators | `list` |
| Last In, First Out (LIFO) | `stack` |
| First In, First Out (FIFO) | `queue` |
| Quickly get the largest or smallest item | `priority_queue` |
| Unique values in sorted order | `set` |
| Values with duplicates in sorted order | `multiset` |
| Fast average membership checks, no order needed | `unordered_set` |
| Key-value pairs with sorted keys | `map` |
| Key-value pairs with fast average lookup | `unordered_map` |
| Store two related values | `pair` |

## 14. Beginner reminders

- C++ indexes start at **0**. In a vector of 3 items, valid indexes are `0`, `1`, and `2`.
- `push_back()` adds; `pop_back()` removes the last vector element.
- `stack`, `queue`, and `priority_queue` do not support indexing like `v[i]`.
- `pop()` removes an item but does **not** return it. Read `top()` or `front()` first when needed.
- Check `empty()` before using `top()`, `front()`, or `back()` if the container might be empty.
- `set` and `map` keep values/keys sorted. Their common search, insert, and erase operations are O(log n).
- `unordered_set` and `unordered_map` do not keep a sorted order. Their common lookup/insert operations are average O(1).
- `lower_bound()` and `upper_bound()` need a sorted range for normal binary-search behavior.
- `vector<vector<int>>` is commonly used for matrices and graph adjacency lists.
- `map[key]` can insert a missing key. Use `find()` or `count()` when you only want to check whether it exists.
