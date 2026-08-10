# Selection Sort — Beginner-Friendly Explanation

## 1. What is Selection Sort?

Imagine you have a row of numbers:

```text
64  25  12  22  11
```

You want to arrange them from **smallest to largest**:

```text
11  12  22  25  64
```

Selection Sort works like this:

> **Find the smallest number from the unsorted part and put it at the beginning of that unsorted part.**

We repeat this until the entire array is sorted.

---

# 2. The Basic Idea

Let's divide the array into two parts:

```text
Sorted Part | Unsorted Part
------------|----------------
            | 64  25  12  22  11
```

Initially, nothing is sorted.

We look through the entire array and find the **smallest number**.

The smallest number is:

```text
11
```

We put `11` at the beginning:

```text
11 | 25  12  22  64
```

Now `11` is in its final position.

We don't need to look at it again.

Next, we look only at:

```text
25  12  22  64
```

The smallest number is `12`.

We put `12` at the beginning of this unsorted section:

```text
11  12 | 25  22  64
```

Then we repeat.

---

# 3. Our Example Array

We will use this array:

```text
[64, 25, 12, 22, 11]
```

Our goal is:

```text
[11, 12, 22, 25, 64]
```

Before we start, let's understand the **indexes**.

---

# 4. Understanding Array Indexes

Java arrays start from **index 0**.

For our array:

```text
Index:      0    1    2    3    4
            ↓    ↓    ↓    ↓    ↓
Array:     64   25   12   22   11
```

Therefore:

```text
64 → index 0
25 → index 1
12 → index 2
22 → index 3
11 → index 4
```

---

# 5. The Two `for` Loops

Selection Sort uses two important loops.

We can represent them using two variables:

```text
i
j
```

Think of them as **two pointers**.

## `i` — Outer Loop Pointer

`i` tells us:

> **Which index are we currently trying to fill with the smallest element?**

It moves from left to right:

```text
i = 0
i = 1
i = 2
i = 3
...
```

For example:

```text
Index:      0    1    2    3    4
            ↓
i           0
Array:     64   25   12   22   11
```

After the first round, `i` moves to:

```text
Index:      0    1    2    3    4
                 ↓
i                1
Array:     11   25   12   22   64
```

---

# 6. `j` — Inner Loop Pointer

`j` is used to **search for the smallest element**.

While `i` stays at one index, `j` moves through the remaining unsorted elements.

For example:

```text
Index:      0    1    2    3    4
            ↓    ↓    ↓    ↓    ↓
Array:     64   25   12   22   11
            ↑    ↑
            i    j
```

Then `j` moves:

```text
Index:      0    1    2    3    4
            ↓         ↓
Array:     64   25   12   22   11
            ↑         ↑
            i         j
```

Then:

```text
Index:      0    1    2    3    4
            ↓              ↓
Array:     64   25   12   22   11
            ↑              ↑
            i              j
```

So:

```text
i → tells us where we are placing the next smallest element

j → searches for the smallest element
```

---

# 7. What is `minimum`?

We also need one more variable:

```text
minimum
```

`minimum` stores the **index of the smallest element found so far**.

For example:

```text
Array:

[64, 25, 12, 22, 11]
```

Initially, we don't know which element is the smallest.

So we temporarily assume:

```text
minimum = i
```

If:

```text
i = 0
```

then:

```text
minimum = 0
```

This means:

> "For now, I think the element at index 0 is the smallest."

As `j` searches the array, `minimum` can change.

---

# 8. The Three Important Variables

So, Selection Sort mainly uses:

| Variable  | Purpose                                               |
| --------- | ----------------------------------------------------- |
| `i`       | Index where the next smallest element should go       |
| `j`       | Searches the remaining unsorted elements              |
| `minimum` | Stores the index of the smallest element found so far |

A useful way to remember them:

```text
i         → Where should the smallest element go?

j         → Where am I currently searching?

minimum   → Where is the smallest element I have found?
```

---

# 9. Step 1 — Start With `i = 0`

Our array:

```text
[64, 25, 12, 22, 11]
```

Initially:

```text
i = 0
```

The visual is:

```text
Index:      0    1    2    3    4
            ↓
            i
Array:     64   25   12   22   11
```

We set:

```text
minimum = i
```

Therefore:

```text
minimum = 0
```

Now:

```text
i = 0
minimum = 0
```

Visual:

```text
Index:      0    1    2    3    4
            ↓
            i
            ↓
        minimum
Array:     64   25   12   22   11
```

We are temporarily assuming:

```text
64
```

is the smallest element.

But we need to check the remaining elements.

---

# 10. Step 1 — `j = 1`

The inner loop starts after `i`.

Therefore:

```text
j = i + 1
```

Since:

```text
i = 0
```

we get:

```text
j = 1
```

Current values:

```text
i = 0
j = 1
minimum = 0
```

Visual:

```text
Index:      0    1    2    3    4
            ↓    ↓
            i    j
Array:     64   25   12   22   11
            ↑
         minimum
```

We compare:

```text
array[j] → 25
array[minimum] → 64
```

So:

```text
25 < 64
```

Therefore, `25` becomes the new smallest element found so far.

Update:

```text
minimum = 1
```

Now:

```text
i = 0
j = 1
minimum = 1
```

Visual:

```text
Index:      0    1    2    3    4
            ↓    ↓
            i    j
                 ↓
              minimum
Array:     64   25   12   22   11
```

---

# 11. Step 1 — `j = 2`

Move `j` to the next index:

```text
j = 2
```

Current values:

```text
i = 0
j = 2
minimum = 1
```

Visual:

```text
Index:      0    1    2    3    4
            ↓         ↓
            i         j
                 ↓
              minimum
Array:     64   25   12   22   11
```

We compare:

```text
array[j] → 12
array[minimum] → 25
```

Since:

```text
12 < 25
```

we update:

```text
minimum = 2
```

Now:

```text
i = 0
j = 2
minimum = 2
```

Visual:

```text
Index:      0    1    2    3    4
            ↓         ↓
            i         j
                      ↓
                   minimum
Array:     64   25   12   22   11
```

---

# 12. Step 1 — `j = 3`

Move `j` again:

```text
j = 3
```

Current values:

```text
i = 0
j = 3
minimum = 2
```

Visual:

```text
Index:      0    1    2    3    4
            ↓         ↓    ↓
            i      minimum  j
Array:     64   25   12   22   11
```

Compare:

```text
array[j] → 22
array[minimum] → 12
```

Since:

```text
22 > 12
```

`minimum` does not change.

So:

```text
i = 0
j = 3
minimum = 2
```

---

# 13. Step 1 — `j = 4`

Move `j` again:

```text
j = 4
```

Current values:

```text
i = 0
j = 4
minimum = 2
```

Visual:

```text
Index:      0    1    2    3    4
            ↓         ↓         ↓
            i      minimum      j
Array:     64   25   12   22   11
```

Compare:

```text
array[j] → 11
array[minimum] → 12
```

Since:

```text
11 < 12
```

we update:

```text
minimum = 4
```

Now:

```text
i = 0
j = 4
minimum = 4
```

Visual:

```text
Index:      0    1    2    3    4
            ↓                   ↓
            i                j / minimum
Array:     64   25   12   22   11
```

---

# 14. End of the First Search

The inner loop has now finished.

We searched:

```text
25
12
22
11
```

The smallest element is:

```text
11
```

And:

```text
minimum = 4
```

So we know:

```text
array[minimum] = 11
```

We want the smallest element at index `i`.

Currently:

```text
i = 0
```

So we need to swap:

```text
array[0] ↔ array[4]

64 ↔ 11
```

Before swapping:

```text
Index:      0    1    2    3    4
            ↓                   ↓
            i                minimum
Array:     64   25   12   22   11
```

Swap:

```text
64 ↔ 11
```

After swapping:

```text
[11, 25, 12, 22, 64]
```

Now index `0` is sorted.

```text
[11] | [25, 12, 22, 64]
  ↑          ↑
sorted     unsorted
```

---

# 15. Step 2 — Move `i` to Index 1

The first element is now sorted.

So:

```text
i = 1
```

Array:

```text
[11, 25, 12, 22, 64]
```

Visual:

```text
Index:      0    1    2    3    4
                 ↓
                 i
Array:     11   25   12   22   64
```

Everything before `i` is already sorted:

```text
[11] | [25, 12, 22, 64]
       ↑
       i
```

Now:

```text
minimum = i
```

Therefore:

```text
minimum = 1
```

Current values:

```text
i = 1
minimum = 1
```

---

# 16. Step 2 — `j = 2`

The inner loop starts at:

```text
j = i + 1
```

Therefore:

```text
j = 2
```

Current values:

```text
i = 1
j = 2
minimum = 1
```

Visual:

```text
Index:      0    1    2    3    4
                 ↓    ↓
                 i    j
                 ↓
              minimum
Array:     11   25   12   22   64
```

Compare:

```text
array[j] → 12
array[minimum] → 25
```

Since:

```text
12 < 25
```

update:

```text
minimum = 2
```

Now:

```text
i = 1
j = 2
minimum = 2
```

---

# 17. Step 2 — `j = 3`

Move `j`:

```text
j = 3
```

Current values:

```text
i = 1
j = 3
minimum = 2
```

Visual:

```text
Index:      0    1    2    3    4
                      ↓    ↓
                      ↑    j
                   minimum
                 i
                 ↓
Array:     11   25   12   22   64
```

Compare:

```text
array[j] → 22
array[minimum] → 12
```

Since:

```text
22 > 12
```

`minimum` does not change.

So:

```text
i = 1
j = 3
minimum = 2
```

---

# 18. Step 2 — `j = 4`

Move `j`:

```text
j = 4
```

Current values:

```text
i = 1
j = 4
minimum = 2
```

Visual:

```text
Index:      0    1    2    3    4
                 ↓    ↓         ↓
                 i minimum      j
Array:     11   25   12   22   64
```

Compare:

```text
array[j] → 64
array[minimum] → 12
```

Since:

```text
64 > 12
```

`minimum` remains:

```text
minimum = 2
```

---

# 19. Step 2 — Swap

The inner loop is complete.

We found:

```text
minimum = 2
```

So:

```text
array[minimum] = 12
```

We need to put `12` at:

```text
i = 1
```

So swap:

```text
25 ↔ 12
```

Before:

```text
Index:      0    1    2    3    4
                 ↓    ↓
                 i minimum
Array:     11   25   12   22   64
```

After:

```text
[11, 12, 25, 22, 64]
```

Now:

```text
[11, 12] | [25, 22, 64]
```

---

# 20. Step 3 — Move `i` to Index 2

Now:

```text
i = 2
```

Array:

```text
[11, 12, 25, 22, 64]
```

Visual:

```text
Index:      0    1    2    3    4
                      ↓
                      i
Array:     11   12   25   22   64
```

Set:

```text
minimum = i
```

Therefore:

```text
minimum = 2
```

---

# 21. Step 3 — `j = 3`

Start the inner loop:

```text
j = i + 1
j = 3
```

Current values:

```text
i = 2
j = 3
minimum = 2
```

Visual:

```text
Index:      0    1    2    3    4
                      ↓    ↓
                      i    j
                      ↓
                   minimum
Array:     11   12   25   22   64
```

Compare:

```text
array[j] → 22
array[minimum] → 25
```

Since:

```text
22 < 25
```

update:

```text
minimum = 3
```

Now:

```text
i = 2
j = 3
minimum = 3
```

---

# 22. Step 3 — `j = 4`

Move `j`:

```text
j = 4
```

Current values:

```text
i = 2
j = 4
minimum = 3
```

Visual:

```text
Index:      0    1    2    3    4
                      ↓    ↓    ↓
                      i minimum j
Array:     11   12   25   22   64
```

Compare:

```text
array[j] → 64
array[minimum] → 22
```

Since:

```text
64 > 22
```

`minimum` remains:

```text
minimum = 3
```

---

# 23. Step 3 — Swap

We found:

```text
minimum = 3
```

Therefore the smallest element is:

```text
22
```

We need to put it at:

```text
i = 2
```

So swap:

```text
25 ↔ 22
```

Before:

```text
[11, 12, 25, 22, 64]
          ↑   ↑
          i minimum
```

After:

```text
[11, 12, 22, 25, 64]
```

Now:

```text
[11, 12, 22] | [25, 64]
```

---

# 24. Step 4 — Move `i` to Index 3

Now:

```text
i = 3
```

Array:

```text
[11, 12, 22, 25, 64]
```

Set:

```text
minimum = i
```

Therefore:

```text
minimum = 3
```

Visual:

```text
Index:      0    1    2    3    4
                            ↓
                            i
                            ↓
                         minimum
Array:     11   12   22   25   64
```

---

# 25. Step 4 — `j = 4`

The inner loop starts:

```text
j = i + 1
```

Therefore:

```text
j = 4
```

Current values:

```text
i = 3
j = 4
minimum = 3
```

Visual:

```text
Index:      0    1    2    3    4
                            ↓    ↓
                            i    j
                            ↓
                         minimum
Array:     11   12   22   25   64
```

Compare:

```text
array[j] → 64
array[minimum] → 25
```

Since:

```text
64 > 25
```

`minimum` does not change.

So:

```text
i = 3
j = 4
minimum = 3
```

---

# 26. Step 4 — Swap

The smallest element is already at index `3`.

So:

```text
array[i] = 25
array[minimum] = 25
```

There is no meaningful change.

The array remains:

```text
[11, 12, 22, 25, 64]
```

Now:

```text
[11, 12, 22, 25] | [64]
```

---

# 27. Step 5 — Nothing More to Sort

We have reached the last element.

```text
[11, 12, 22, 25, 64]
```

There is nothing left to search.

The array is sorted.

---

# 28. Complete Sorting Process

Let's see the entire process without all the comparisons.

### Starting Array

```text
[64, 25, 12, 22, 11]
```

---

### Round 1

```text
i = 0

Find smallest in:

[64, 25, 12, 22, 11]

minimum = 4

Swap:

64 ↔ 11

Result:

[11, 25, 12, 22, 64]
```

---

### Round 2

```text
i = 1

Find smallest in:

[25, 12, 22, 64]

minimum = 2

Swap:

25 ↔ 12

Result:

[11, 12, 25, 22, 64]
```

---

### Round 3

```text
i = 2

Find smallest in:

[25, 22, 64]

minimum = 3

Swap:

25 ↔ 22

Result:

[11, 12, 22, 25, 64]
```

---

### Round 4

```text
i = 3

Find smallest in:

[25, 64]

minimum = 3

25 is already the smallest.

No meaningful swap.

Result:

[11, 12, 22, 25, 64]
```

---

# 29. Complete Pointer Visualization

This is the most important visual to understand the two loops.

```text
Starting:

Index:      0    1    2    3    4
            ↓
            i
Array:     64   25   12   22   11
```

`j` searches the remaining elements:

```text
Index:      0    1    2    3    4
            ↓    ↓
            i    j

Index:      0    1    2    3    4
            ↓         ↓
            i         j

Index:      0    1    2    3    4
            ↓              ↓
            i              j

Index:      0    1    2    3    4
            ↓                   ↓
            i                   j
```

After finding the smallest:

```text
minimum = 4
```

Swap:

```text
array[i] ↔ array[minimum]

64 ↔ 11
```

Result:

```text
[11, 25, 12, 22, 64]
```

Then `i` moves:

```text
Index:      0    1    2    3    4
                 ↓
                 i
```

And `j` starts searching again:

```text
Index:      0    1    2    3    4
                 ↓    ↓
                 i    j
```

This is why Selection Sort has **two loops**:

```text
Outer loop → i
Inner loop → j
```

The outer loop decides **where to place** the next smallest element.

The inner loop decides **which element is the smallest**.

---

# 30. The Role of `i`, `j`, and `minimum`

Let's summarize them one more time.

```text
i
↓
Controls the sorted/unsorted boundary.

j
↓
Searches through the unsorted portion.

minimum
↓
Remembers the index of the smallest element found so far.
```

For example:

```text
[11, 12 | 25, 22, 64]
         ↑
         i
```

Everything before `i` is sorted.

Everything from `i` onwards is unsorted.

Then `j` searches:

```text
[11, 12 | 25, 22, 64]
              ↑   ↑   ↑
              j   j   j
```

While `j` searches, `minimum` remembers the smallest element found.

---

# 31. The Algorithm in Plain English

Selection Sort can be explained using these steps:

```text
1. Start at index 0.

2. Assume the element at index i
   is the smallest.

3. Start another pointer j
   from index i + 1.

4. Move j through the remaining
   unsorted elements.

5. Whenever j finds an element
   smaller than the current minimum,
   update minimum.

6. When j finishes searching,
   minimum points to the smallest element.

7. Swap the element at i
   with the element at minimum.

8. Move i to the next index.

9. Repeat until the array is sorted.
```

The entire algorithm can be remembered as:

```text
FIND → SELECT → SWAP → MOVE → REPEAT
```

---

# 32. Why Is It Called "Selection Sort"?

Because during every round we **select one element**.

Specifically:

> We select the smallest element from the unsorted portion.

For example:

```text
[64, 25, 12, 22, 11]
                ↓
             select 11

[11, 25, 12, 22, 64]
```

Then:

```text
[11, 25, 12, 22, 64]
        ↓
     select 12

[11, 12, 25, 22, 64]
```

Then:

```text
[11, 12, 25, 22, 64]
            ↓
         select 22

[11, 12, 22, 25, 64]
```

So:

```text
Selection Sort
       ↓
Select the smallest
       ↓
Place it correctly
       ↓
Repeat
```

---

# 33. Time Complexity

Let's understand this without complicated mathematics.

For our array:

```text
[64, 25, 12, 22, 11]
```

During the first round, we search almost the entire array:

```text
5 elements
```

During the second round:

```text
4 elements
```

During the third:

```text
3 elements
```

During the fourth:

```text
2 elements
```

So the number of comparisons is approximately:

```text
5 + 4 + 3 + 2 + 1
```

For an array of `n` elements, this becomes roughly:

```text
n + (n - 1) + (n - 2) + ... + 1
```

This grows approximately as:

```text
n²
```

Therefore:

```text
Time Complexity = O(n²)
```

---

# 34. Best Case

What if the array is already sorted?

```text
[11, 12, 22, 25, 64]
```

You might think Selection Sort would finish very quickly.

However, Selection Sort still needs to search the remaining elements to make sure there isn't a smaller element.

Therefore:

```text
Best Case = O(n²)
```

---

# 35. Average Case

For a randomly arranged array:

```text
[64, 25, 12, 22, 11]
```

Selection Sort still performs roughly the same number of comparisons.

Therefore:

```text
Average Case = O(n²)
```

---

# 36. Worst Case

Even if the array is arranged in an unfavorable order:

```text
[64, 25, 12, 22, 11]
```

Selection Sort still performs roughly the same number of comparisons.

Therefore:

```text
Worst Case = O(n²)
```

So:

| Case    | Time Complexity |
| ------- | --------------- |
| Best    | O(n²)           |
| Average | O(n²)           |
| Worst   | O(n²)           |

This is an important characteristic of Selection Sort:

> **The input being already sorted does not significantly improve its running time.**

---

# 37. Space Complexity

Selection Sort does not require another array.

It modifies the original array.

For example:

```text
Original:

[64, 25, 12, 22, 11]
```

We rearrange these same elements.

We don't create:

```text
anotherArray = [11, 12, 22, 25, 64]
```

Instead, we swap elements inside the original array.

We only need a few variables:

```text
i
j
minimum
temporary
```

The number of variables stays the same regardless of the size of the array.

Therefore:

```text
Space Complexity = O(1)
```

This is called:

> **Constant extra space.**

---

# 38. Why Can Selection Sort Be Useful?

Even though Selection Sort is `O(n²)`, it has some useful properties.

## Advantage 1 — Very Simple

The algorithm is easy to understand:

```text
Find smallest
      ↓
Swap
      ↓
Move i
      ↓
Repeat
```

This makes Selection Sort excellent for learning the fundamentals of:

* Arrays
* Loops
* Nested loops
* Comparisons
* Swapping
* Indexes
* Searching

---

# 39. Advantage 2 — Uses Very Little Extra Memory

Selection Sort sorts the array **in-place**.

It doesn't need another array.

```text
Space = O(1)
```

This can be useful when memory is limited.

---

# 40. Advantage 3 — Few Swaps

One interesting advantage of Selection Sort is that it performs relatively few swaps.

For `n` elements, it performs at most approximately:

```text
n - 1 swaps
```

For example, with:

```text
1000 elements
```

Selection Sort performs at most approximately:

```text
999 swaps
```

It still performs many comparisons, but the number of swaps is low.

This can be useful when **writing or moving an element is expensive**.

---

# 41. When Should You NOT Use Selection Sort?

## 1. Large Arrays

For a large array:

```text
10,000 elements
```

the number of operations associated with `O(n²)` can become very large.

Conceptually:

```text
10,000 × 10,000
= 100,000,000
```

So Selection Sort is generally not suitable for large datasets.

---

## 2. When Performance Is Important

If you need to sort a large amount of data quickly, algorithms such as:

```text
Merge Sort
Quick Sort
Heap Sort
```

are generally more appropriate.

Many efficient comparison-based sorting algorithms can achieve:

```text
O(n log n)
```

compared with:

```text
O(n²)
```

for Selection Sort.

---

## 3. When You Need a Stable Sort

Selection Sort is generally **not stable** in its normal implementation.

A stable sorting algorithm preserves the relative order of equal elements.

For example:

```text
(John, 80)
(Alex, 80)
```

If John appeared before Alex originally, a stable sorting algorithm keeps:

```text
John → Alex
```

after sorting by score.

Selection Sort does not guarantee this in its typical implementation.

---

# 42. Selection Sort — Quick Summary

| Property             | Selection Sort |
| -------------------- | -------------- |
| Best Time            | O(n²)          |
| Average Time         | O(n²)          |
| Worst Time           | O(n²)          |
| Extra Space          | O(1)           |
| In-place             | Yes            |
| Stable               | Usually No     |
| Easy to Understand   | Yes            |
| Number of Swaps      | Low            |
| Good for Large Data? | No             |
| Good for Learning?   | Yes            |

---

# 43. Selection Sort Mental Model

If you remember only one thing, remember this:

```text
                 ARRAY
                   |
                   ↓
             i = current index
                   |
                   ↓
        Assume i has the minimum
                   |
                   ↓
             j = i + 1
                   |
                   ↓
       Search remaining elements
                   |
                   ↓
       Update minimum when needed
                   |
                   ↓
       Swap i with minimum
                   |
                   ↓
             Move i forward
                   |
                   ↓
                 Repeat
```

Or even shorter:

```text
SELECT → SWAP → MOVE → REPEAT
```

---

# 44. Java-Style Pseudocode

The following is **pseudocode written using Java-like structure**.

It is intentionally **not actual Java implementation**.

The goal is to understand the algorithm before worrying about Java syntax.


```text
BEGIN SelectionSort

    CLASS SelectionSort

        METHOD selectionSort(array)

            FOR i FROM 0 TO array.length - 2

                minimum = i

                FOR j FROM i + 1 TO array.length - 1

                    IF array[j] < array[minimum] THEN

                        minimum = j

                    END IF

                END FOR

                SWAP array[i] WITH array[minimum]

            END FOR

        END METHOD

    END CLASS

END SelectionSort
```

Notice that this is **pseudocode**, not Java code.

For example:

```text
FOR i FROM 0 TO array.length - 2
```

is pseudocode representing the idea of a Java `for` loop.

And:

```text
SWAP array[i] WITH array[minimum]
```

represents the swapping operation without writing the actual Java implementation.
