# Bubble Sort — Beginner-Friendly Explanation

## 1. What is Bubble Sort?

Imagine you have a row of numbers:

```text
[64, 25, 12, 22, 11]
```

You want to arrange them from **smallest to largest**:

```text
[11, 12, 22, 25, 64]
```

Bubble Sort works by repeatedly comparing **two neighboring elements**.

If they are in the wrong order, we **swap them**.

For example:

```text
64  25
↑   ↑
```

Since:

```text
64 > 25
```

they are in the wrong order.

So we swap them:

```text
25  64
```

Then we move one step forward and compare the next pair.

---

# 2. Why Is It Called "Bubble Sort"?

Imagine bubbles in water.

A bubble gradually moves toward the top.

In Bubble Sort, the **largest element gradually moves toward the end of the array** after every complete round.

For example:

```text
[64, 25, 12, 22, 11]
```

After one complete round:

```text
[25, 12, 22, 11, 64]
```

Notice:

```text
64
```

has moved all the way to the end.

The largest element has "bubbled" to the end.

That's why it is called:

> **Bubble Sort**

---

# 3. The Basic Idea

Bubble Sort repeatedly does this:

```text
Compare two neighboring elements
             ↓
Are they in the wrong order?
             ↓
          Yes
             ↓
           Swap
             ↓
Move to the next pair
             ↓
         Repeat
```

For example:

```text
64  25  12  22  11
```

Compare:

```text
64  25
```

Swap:

```text
25  64  12  22  11
```

Next pair:

```text
25  64
    ↑   ↑
```

These are already in the correct order.

Move forward:

```text
25  64  12
    ↑   ↑
```

`64` and `12` are in the wrong order.

Swap:

```text
25  12  64  22  11
```

And continue.

---

# 4. Our Example Array

We will use:

```text
[64, 25, 12, 22, 11]
```

Our goal is:

```text
[11, 12, 22, 25, 64]
```

Let's first understand the indexes.

---

# 5. Understanding Array Indexes

Java arrays start from **index 0**.

Our array looks like this:

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

# 6. The Two `for` Loop Pointers

Bubble Sort uses two important loop variables:

```text
i
j
```

They represent the two loops used by the algorithm.

But their roles are different from Selection Sort.

## `i` — Outer Loop Pointer

`i` represents the **number of passes** we have completed.

It controls how many times we go through the array.

Think of it as:

```text
i → Which round/pass are we performing?
```

For example:

```text
i = 0 → first pass
i = 1 → second pass
i = 2 → third pass
i = 3 → fourth pass
```

---

# 7. `j` — Inner Loop Pointer

`j` moves through the array and compares **neighboring elements**.

It compares:

```text
array[j]
```

with:

```text
array[j + 1]
```

So:

```text
j       → current element
j + 1   → next element
```

For example:

```text
Index:      0    1    2    3    4
            ↓    ↓
            j   j+1
Array:     64   25   12   22   11
```

Then `j` moves:

```text
Index:      0    1    2    3    4
                 ↓    ↓
                 j   j+1
Array:     64   25   12   22   11
```

Then:

```text
Index:      0    1    2    3    4
                      ↓    ↓
                      j   j+1
Array:     64   25   12   22   11
```

And so on.

---

# 8. The Important Difference From Selection Sort

In Selection Sort:

```text
i → where to put the smallest
j → search for the smallest
minimum → remembers smallest
```

In Bubble Sort:

```text
i → controls the passes
j → compares neighboring elements
```

Bubble Sort **does not need a `minimum` variable**.

Instead, it repeatedly compares:

```text
array[j]
```

and:

```text
array[j + 1]
```

and swaps them if necessary.

---

# 9. The Main Rule of Bubble Sort

This is the most important rule:

> **If the left element is greater than the right element, swap them.**

For example:

```text
64  25
↑   ↑
left right
```

Because:

```text
64 > 25
```

swap:

```text
25  64
```

But:

```text
25  64
```

is already correct because:

```text
25 < 64
```

So don't swap.

---

# 10. Pass 1 — Start With `i = 0`

Our array:

```text
[64, 25, 12, 22, 11]
```

We start the first pass:

```text
i = 0
```

Visual:

```text
Index:      0    1    2    3    4
            ↓
            i
Array:     64   25   12   22   11
```

Now `j` starts at index `0`.

```text
j = 0
```

Current values:

```text
i = 0
j = 0
```

Visual:

```text
Index:      0    1    2    3    4
            ↓    ↓
            j   j+1
Array:     64   25   12   22   11
```

We compare:

```text
array[j]     = 64
array[j + 1] = 25
```

Since:

```text
64 > 25
```

we swap them.

---

# 11. Pass 1 — Swap 64 and 25

Before:

```text
[64, 25, 12, 22, 11]
 ↑   ↑
 j  j+1
```

Swap:

```text
64 ↔ 25
```

After:

```text
[25, 64, 12, 22, 11]
```

Now:

```text
i = 0
j = 0
```

The important thing is that `j` will now move forward.

---

# 12. Pass 1 — Move `j` to Index 1

Now:

```text
j = 1
```

Current values:

```text
i = 0
j = 1
```

Visual:

```text
Index:      0    1    2    3    4
                 ↓    ↓
                 j   j+1
Array:     25   64   12   22   11
```

Compare:

```text
array[j]     = 64
array[j + 1] = 12
```

Since:

```text
64 > 12
```

swap them.

Before:

```text
[25, 64, 12, 22, 11]
      ↑   ↑
      j  j+1
```

After:

```text
[25, 12, 64, 22, 11]
```

---

# 13. Pass 1 — Move `j` to Index 2

Now:

```text
j = 2
```

Current values:

```text
i = 0
j = 2
```

Visual:

```text
Index:      0    1    2    3    4
                      ↓    ↓
                      j   j+1
Array:     25   12   64   22   11
```

Compare:

```text
64
22
```

Since:

```text
64 > 22
```

swap:

```text
64 ↔ 22
```

Before:

```text
[25, 12, 64, 22, 11]
          ↑   ↑
          j  j+1
```

After:

```text
[25, 12, 22, 64, 11]
```

---

# 14. Pass 1 — Move `j` to Index 3

Now:

```text
j = 3
```

Current values:

```text
i = 0
j = 3
```

Visual:

```text
Index:      0    1    2    3    4
                           ↓    ↓
                           j   j+1
Array:     25   12   22   64   11
```

Compare:

```text
64
11
```

Since:

```text
64 > 11
```

swap:

```text
64 ↔ 11
```

After:

```text
[25, 12, 22, 11, 64]
```

---

# 15. End of Pass 1

The first pass is complete.

We started with:

```text
[64, 25, 12, 22, 11]
```

After all the comparisons:

```text
[25, 12, 22, 11, 64]
```

Notice something important:

```text
[25, 12, 22, 11, 64]
                  ↑
               largest
```

The largest element, `64`, has reached the end.

This is the **bubble** effect.

So after the first pass:

```text
[25, 12, 22, 11] | [64]
                   ↑
                 sorted
```

---

# 16. Pass 2 — `i = 1`

Now we start the second pass.

```text
i = 1
```

Array:

```text
[25, 12, 22, 11, 64]
```

The last element is already sorted.

So we don't need to compare it again.

The unsorted part is:

```text
[25, 12, 22, 11]
```

Visual:

```text
[25, 12, 22, 11] | [64]
                    sorted
```

Now:

```text
j = 0
```

Current values:

```text
i = 1
j = 0
```

Visual:

```text
Index:      0    1    2    3    4
            ↓    ↓
            j   j+1
Array:     25   12   22   11   64
```

Compare:

```text
25 > 12
```

So swap.

After:

```text
[12, 25, 22, 11, 64]
```

---

# 17. Pass 2 — `j = 1`

Move `j`:

```text
j = 1
```

Current values:

```text
i = 1
j = 1
```

Visual:

```text
Index:      0    1    2    3    4
                 ↓    ↓
                 j   j+1
Array:     12   25   22   11   64
```

Compare:

```text
25 > 22
```

Swap:

```text
25 ↔ 22
```

Result:

```text
[12, 22, 25, 11, 64]
```

---

# 18. Pass 2 — `j = 2`

Move `j`:

```text
j = 2
```

Current values:

```text
i = 1
j = 2
```

Visual:

```text
Index:      0    1    2    3    4
                      ↓    ↓
                      j   j+1
Array:     12   22   25   11   64
```

Compare:

```text
25 > 11
```

Swap:

```text
25 ↔ 11
```

Result:

```text
[12, 22, 11, 25, 64]
```

---

# 19. End of Pass 2

The second pass is complete.

We have:

```text
[12, 22, 11, 25, 64]
```

Notice:

```text
[12, 22, 11] | [25, 64]
               ↑     ↑
             sorted sorted
```

The next largest element, `25`, has moved into its final location.

---

# 20. Pass 3 — `i = 2`

Start the third pass:

```text
i = 2
```

Array:

```text
[12, 22, 11, 25, 64]
```

The sorted section is:

```text
[25, 64]
```

The remaining unsorted section is:

```text
[12, 22, 11]
```

Now:

```text
j = 0
```

Current values:

```text
i = 2
j = 0
```

Compare:

```text
12 and 22
```

Since:

```text
12 < 22
```

they are already in the correct order.

No swap.

Array remains:

```text
[12, 22, 11, 25, 64]
```

---

# 21. Pass 3 — `j = 1`

Move `j`:

```text
j = 1
```

Current values:

```text
i = 2
j = 1
```

Visual:

```text
Index:      0    1    2    3    4
                 ↓    ↓
                 j   j+1
Array:     12   22   11   25   64
```

Compare:

```text
22 > 11
```

So swap:

```text
22 ↔ 11
```

Result:

```text
[12, 11, 22, 25, 64]
```

---

# 22. End of Pass 3

We now have:

```text
[12, 11, 22, 25, 64]
```

The sorted portion is:

```text
[22, 25, 64]
```

The unsorted portion is:

```text
[12, 11]
```

---

# 23. Pass 4 — `i = 3`

Start the fourth pass:

```text
i = 3
```

The array is:

```text
[12, 11, 22, 25, 64]
```

The only pair that needs to be checked is:

```text
12  11
↑   ↑
j  j+1
```

Current values:

```text
i = 3
j = 0
```

Compare:

```text
12 > 11
```

So swap:

```text
12 ↔ 11
```

Result:

```text
[11, 12, 22, 25, 64]
```

The array is now sorted.

---

# 24. Complete Sorting Process

Let's see all the important changes together.

### Starting Array

```text
[64, 25, 12, 22, 11]
```

---

## Pass 1 — `i = 0`

```text
64 25 → swap

[25, 64, 12, 22, 11]

64 12 → swap

[25, 12, 64, 22, 11]

64 22 → swap

[25, 12, 22, 64, 11]

64 11 → swap

[25, 12, 22, 11, 64]
```

Largest element is now at the end:

```text
[25, 12, 22, 11] | [64]
```

---

## Pass 2 — `i = 1`

```text
25 12 → swap

[12, 25, 22, 11, 64]

25 22 → swap

[12, 22, 25, 11, 64]

25 11 → swap

[12, 22, 11, 25, 64]
```

Now:

```text
[12, 22, 11] | [25, 64]
```

---

## Pass 3 — `i = 2`

```text
12 22 → no swap

[12, 22, 11, 25, 64]

22 11 → swap

[12, 11, 22, 25, 64]
```

Now:

```text
[12, 11] | [22, 25, 64]
```

---

## Pass 4 — `i = 3`

```text
12 11 → swap

[11, 12, 22, 25, 64]
```

Sorted!

---

# 25. The Two Loops Visually

This is the most important part for understanding why Bubble Sort has **two `for` loops**.

The outer loop uses `i`:

```text
i = 0 → Pass 1
i = 1 → Pass 2
i = 2 → Pass 3
i = 3 → Pass 4
```

Inside each pass, `j` moves through the array:

```text
Pass 1:

j = 0 → compare indexes 0 and 1
j = 1 → compare indexes 1 and 2
j = 2 → compare indexes 2 and 3
j = 3 → compare indexes 3 and 4
```

Then:

```text
Pass 2:

j = 0 → compare indexes 0 and 1
j = 1 → compare indexes 1 and 2
j = 2 → compare indexes 2 and 3
```

Then:

```text
Pass 3:

j = 0 → compare indexes 0 and 1
j = 1 → compare indexes 1 and 2
```

Then:

```text
Pass 4:

j = 0 → compare indexes 0 and 1
```

Notice that the inner loop gets shorter after every pass.

Why?

Because the largest element has already bubbled to the end.

---

# 26. Why Does the Inner Loop Get Smaller?

Look at the array after Pass 1:

```text
[25, 12, 22, 11] | [64]
```

`64` is already in its final location.

There is no reason to compare `64` again.

After Pass 2:

```text
[12, 22, 11] | [25, 64]
```

Now both `25` and `64` are sorted.

After Pass 3:

```text
[12, 11] | [22, 25, 64]
```

Now three elements are sorted.

So the sorted section grows:

```text
Pass 1:

[25, 12, 22, 11] | [64]
                    ↑
                  1 sorted


Pass 2:

[12, 22, 11] | [25, 64]
                ↑  ↑
              2 sorted


Pass 3:

[12, 11] | [22, 25, 64]
            ↑   ↑   ↑
          3 sorted


Pass 4:

[11, 12, 22, 25, 64]
 ↑   ↑   ↑   ↑   ↑
      sorted
```

---

# 27. `i` and `j` — Simple Explanation

Remember this:

```text
i → controls the passes

j → performs the comparisons
```

For example:

```text
i = 0
```

means:

> "We are performing the first pass."

Then:

```text
j = 0
j = 1
j = 2
j = 3
```

means:

> "Compare each pair of neighboring elements."

---

# 28. What Exactly Does `j` Compare?

This is very important.

`j` does **not** compare random elements.

It always compares:

```text
array[j]
```

with:

```text
array[j + 1]
```

For example, if:

```text
j = 2
```

then:

```text
array[j]
      ↓
array[2]

array[j + 1]
          ↓
array[3]
```

So we compare:

```text
array[2] and array[3]
```

For our array:

```text
Index:      0    1    2    3    4
                 ↓    ↓
Array:     11   12   25   22   64
                 ↑
                 j = 2
```

Actually, with `j = 2`:

```text
Index:      0    1    2    3    4
                      ↓    ↓
                      j   j+1
Array:     11   12   25   22   64
```

So:

```text
array[j]     = 25
array[j + 1] = 22
```

Since:

```text
25 > 22
```

we swap them.

---

# 29. Bubble Sort Without the Optimization

The basic Bubble Sort algorithm can simply repeat the passes.

But there is an important improvement we can make.

Imagine the array is already sorted:

```text
[11, 12, 22, 25, 64]
```

During the first pass:

```text
11 12 → no swap
12 22 → no swap
22 25 → no swap
25 64 → no swap
```

Nothing changed.

That means:

> **The array is already sorted.**

We don't need to perform more passes.

We can use a variable called:

```text
swapped
```

---

# 30. The `swapped` Variable

At the beginning of each pass:

```text
swapped = false
```

Whenever we perform a swap:

```text
swapped = true
```

After the pass finishes:

```text
IF swapped == false
    array is already sorted
```

Why?

Because if we went through the entire pass and **didn't perform even one swap**, every neighboring pair was already in the correct order.

Therefore, the entire array is sorted.

---

# 31. Example of the `swapped` Optimization

Suppose:

```text
[11, 12, 22, 25, 64]
```

Start:

```text
swapped = false
```

Compare:

```text
11 and 12
```

No swap.

Still:

```text
swapped = false
```

Compare:

```text
12 and 22
```

No swap.

Still:

```text
swapped = false
```

Compare:

```text
22 and 25
```

No swap.

Still:

```text
swapped = false
```

Compare:

```text
25 and 64
```

No swap.

Still:

```text
swapped = false
```

The pass ends.

Since:

```text
swapped = false
```

we know the array is already sorted.

We can stop immediately.

---

# 32. Why Is the `swapped` Optimization Useful?

Without the optimization, Bubble Sort always performs all passes.

With the optimization, Bubble Sort can finish early if the array becomes sorted.

For example:

```text
[11, 12, 22, 25, 64]
```

can be detected as sorted after one pass.

This improves the **best-case time complexity**.

Without early termination:

```text
Best Case = O(n²)
```

With the `swapped` optimization:

```text
Best Case = O(n)
```

Because we only need to make one pass through the array.

---

# 33. Time Complexity

Bubble Sort has two loops.

The outer loop performs multiple passes.

The inner loop performs multiple comparisons during each pass.

For example, with 5 elements:

```text
Pass 1 → 4 comparisons
Pass 2 → 3 comparisons
Pass 3 → 2 comparisons
Pass 4 → 1 comparison
```

Total:

```text
4 + 3 + 2 + 1
```

For `n` elements, this grows approximately as:

```text
n²
```

Therefore, the typical time complexity is:

```text
Average Case = O(n²)
Worst Case   = O(n²)
```

---

# 34. Best Case

There is an important distinction here.

## Without `swapped` optimization

Even if the array is already sorted:

```text
[11, 12, 22, 25, 64]
```

Bubble Sort still performs all its passes.

Therefore:

```text
Best Case = O(n²)
```

---

## With `swapped` optimization

If we use:

```text
swapped
```

we can detect that no swaps happened during the first pass.

Then we stop.

So:

```text
Best Case = O(n)
```

Therefore, the optimized version has:

| Case    | Time Complexity |
| ------- | --------------- |
| Best    | O(n)            |
| Average | O(n²)           |
| Worst   | O(n²)           |

This is one of the important differences between the basic and optimized versions of Bubble Sort.

---

# 35. Space Complexity

Bubble Sort sorts the original array.

It does not need another array.

For example:

```text
[64, 25, 12, 22, 11]
```

is modified directly.

We only need a few variables such as:

```text
i
j
temporary
swapped
```

The number of variables does not depend on the size of the array.

Therefore:

```text
Space Complexity = O(1)
```

Bubble Sort is therefore an **in-place sorting algorithm**.

---

# 36. Why Can Bubble Sort Be Useful?

Bubble Sort isn't usually used for large production datasets, but it has some advantages.

## Advantage 1 — Very Easy to Understand

The core idea is extremely simple:

```text
Compare neighbors
       ↓
Wrong order?
       ↓
Swap
       ↓
Move forward
       ↓
Repeat
```

This makes it excellent for beginners learning:

* Arrays
* Indexes
* Nested loops
* Comparisons
* Swapping
* Algorithm thinking

---

# 37. Advantage 2 — In-Place

Bubble Sort doesn't need another array.

Therefore:

```text
Space = O(1)
```

This means it uses very little additional memory.

---

# 38. Advantage 3 — Can Detect an Already Sorted Array

With the `swapped` optimization:

```text
swapped = false
```

we can detect when no swaps were performed.

For example:

```text
[11, 12, 22, 25, 64]
```

If no swaps occur during a pass, we can stop.

This gives optimized Bubble Sort a best-case complexity of:

```text
O(n)
```

---

# 39. Advantage 4 — Stable Sorting

Bubble Sort can be implemented as a **stable sorting algorithm**.

When comparing two elements, we only swap when:

```text
left > right
```

We don't swap when:

```text
left == right
```

Therefore, equal elements can maintain their original relative order.

For example:

```text
(Alex, 80)
(John, 80)
```

If Alex appears before John, Bubble Sort can keep:

```text
Alex → John
```

after sorting by score.

This makes Bubble Sort stable when implemented in the standard way.

---

# 40. When Should You NOT Use Bubble Sort?

## 1. Large Arrays

Bubble Sort has:

```text
Average = O(n²)
Worst   = O(n²)
```

This makes it inefficient for large datasets.

For example:

```text
10,000 elements
```

can result in a very large number of comparisons.

---

## 2. When Performance Is Important

If you need to sort a large amount of data quickly, algorithms such as:

```text
Merge Sort
Quick Sort
Heap Sort
```

are generally more appropriate.

Efficient comparison-based sorting algorithms can generally achieve:

```text
O(n log n)
```

while Bubble Sort generally requires:

```text
O(n²)
```

---

# 41. Selection Sort vs Bubble Sort

Since we have already learned Selection Sort, it is useful to compare them.

| Property            | Selection Sort      | Bubble Sort              |
| ------------------- | ------------------- | ------------------------ |
| Best Case           | O(n²)               | O(n), optimized          |
| Average Case        | O(n²)               | O(n²)                    |
| Worst Case          | O(n²)               | O(n²)                    |
| Extra Space         | O(1)                | O(1)                     |
| In-place            | Yes                 | Yes                      |
| Stable              | Usually No          | Yes                      |
| Easy to Understand  | Yes                 | Yes                      |
| Main Operation      | Find minimum + swap | Compare neighbors + swap |
| Number of Swaps     | Low                 | Can be high              |
| Good for Learning   | Yes                 | Yes                      |
| Good for Large Data | No                  | No                       |

---

# 42. Selection Sort vs Bubble Sort — The Main Difference

Selection Sort thinks:

```text
"Find the smallest element."
```

Bubble Sort thinks:

```text
"Compare neighboring elements."
```

Selection Sort:

```text
[64, 25, 12, 22, 11]
 ↓
Find 11
 ↓
Put 11 at the beginning
```

Bubble Sort:

```text
[64, 25, 12, 22, 11]

64 25 → swap
25 12 → swap
12 22 → no swap
22 11 → swap
```

So:

```text
Selection Sort → Select the smallest

Bubble Sort → Compare neighbors
```

---

# 43. Bubble Sort Mental Model

If you remember only one thing, remember this:

```text
             ARRAY
               |
               ↓
        Start a new pass
               |
               ↓
        j = 0
               |
               ↓
    Compare array[j] and
       array[j + 1]
               |
               ↓
     Are they in the wrong order?
            /       \
          YES        NO
           ↓          ↓
         SWAP       Don't swap
           \          /
            \        /
             ↓      ↓
             Move j forward
                  |
                  ↓
          Repeat comparison
                  |
                  ↓
           End of the pass
                  |
                  ↓
        Largest element has
          bubbled to the end
                  |
                  ↓
          Start next pass
                  |
                  ↓
                REPEAT
```

---

# 44. The Complete Algorithm in Plain English

You can explain Bubble Sort to a beginner using these steps:

```text
1. Start the first pass.

2. Start j at index 0.

3. Compare the element at index j
   with the element at index j + 1.

4. If the left element is greater
   than the right element,
   swap them.

5. Move j to the next index.

6. Continue until the end of
   the unsorted portion.

7. After the pass, the largest
   remaining element is at the end.

8. Start another pass.

9. Repeat until the array is sorted.

10. Optionally, use a swapped variable.
    If no swap happens during a pass,
    the array is already sorted.
```

The simplest version to remember is:

```text
COMPARE → SWAP → MOVE → REPEAT
```

---

# 45. Java-Style Pseudocode

The following is **Java-style pseudocode**, not actual Java implementation.

The class and method structure look like Java, but the contents describe the algorithm rather than implementing it.

```text
BEGIN BubbleSort

    CLASS BubbleSort

        METHOD bubbleSort(array)

            FOR i FROM 0 TO array.length - 2

                FOR j FROM 0 TO array.length - i - 2

                    IF array[j] > array[j + 1] THEN

                        SWAP array[j] WITH array[j + 1]

                    END IF

                END FOR

            END FOR

        END METHOD

    END CLASS

END BubbleSort
```

---

# 46. Why `array.length - i - 2`?

This is an important part of Bubble Sort.

Remember:

```text
j
```

compares:

```text
array[j]
```

with:

```text
array[j + 1]
```

So `j` cannot go all the way to the last index.

For example, with:

```text
[64, 25, 12, 22, 11]
```

the indexes are:

```text
0  1  2  3  4
```

If:

```text
j = 3
```

we compare:

```text
array[3]
```

with:

```text
array[4]
```

That's valid.

But if:

```text
j = 4
```

we would try:

```text
array[4]
array[5]
```

and index `5` doesn't exist.

Therefore, `j` must stop before the last index.

---

# 47. Why Does `i` Reduce the Number of Comparisons?

After every pass, one more element is already sorted at the end.

For example:

### First pass

```text
[25, 12, 22, 11] | [64]
```

Don't compare `64` again.

### Second pass

```text
[12, 22, 11] | [25, 64]
```

Don't compare `25` or `64` again.

### Third pass

```text
[12, 11] | [22, 25, 64]
```

Don't compare `22`, `25`, or `64` again.

That's why:

```text
array.length - i - 2
```

gets smaller as `i` increases.

---

# 48. Optimized Java-Style Pseudocode

Now let's add the `swapped` optimization.

```text
BEGIN BubbleSort

    CLASS BubbleSort

        METHOD bubbleSort(array)

            FOR i FROM 0 TO array.length - 2

                swapped = false

                FOR j FROM 0 TO array.length - i - 2

                    IF array[j] > array[j + 1] THEN

                        SWAP array[j] WITH array[j + 1]

                        swapped = true

                    END IF

                END FOR

                IF swapped == false THEN

                    BREAK

                END IF

            END FOR

        END METHOD

    END CLASS

END BubbleSort
```

---

# 49. Optimized Pseudocode Explained

At the beginning of every pass:

```text
swapped = false
```

This means:

> "So far, I haven't swapped anything."

Then we compare neighboring elements.

If we find elements in the wrong order:

```text
IF array[j] > array[j + 1] THEN
```

we swap them:

```text
SWAP array[j] WITH array[j + 1]
```

And set:

```text
swapped = true
```

This means:

> "At least one swap happened."

After the inner loop finishes:

```text
IF swapped == false THEN
    BREAK
END IF
```

means:

> "I went through the entire pass without making a single swap. Therefore, the array is already sorted."

---

# 50. Final Pointer Visualization

For Bubble Sort, remember:

```text
i
↓
Controls the passes
```

and:

```text
j       j + 1
↓          ↓
[25]      [12]
```

These two neighboring elements are compared.

If:

```text
array[j] > array[j + 1]
```

then:

```text
SWAP
```

For example:

```text
       j       j+1
       ↓        ↓
[11, 25, 12, 22, 64]

       25 > 12
           ↓
         SWAP
           ↓

[11, 12, 25, 22, 64]
```

Then `j` moves:

```text
           j       j+1
           ↓        ↓
[11, 12, 25, 22, 64]
```

Compare:

```text
25 > 22
```

Swap:

```text
[11, 12, 22, 25, 64]
```

---

# 51. Final Concept to Remember

Bubble Sort has **two loops**:

```text
OUTER LOOP
    i
    ↓
    Controls the number of passes.

        INNER LOOP
            j
            ↓
            Compares neighboring elements:
            
            array[j]
                ↕
            array[j + 1]
```

The key operation is:

```text
IF left element > right element

        ↓

     SWAP
```

After every complete pass:

```text
The largest remaining element
moves to the end.
```

So the complete mental model is:

```text
             BUBBLE SORT

                  i
                  ↓
           Start a new pass
                  |
                  ↓
                  j
                  ↓
        Compare j and j + 1
                  |
                  ↓
       Is left > right?
            /       \
          YES        NO
           ↓          ↓
         SWAP      Don't swap
           \          /
            \        /
             ↓      ↓
             Move j
                |
                ↓
          Continue pass
                |
                ↓
      Largest element reaches
            the end
                |
                ↓
          Start next pass
                |
                ↓
              REPEAT
```

The easiest way to remember Bubble Sort is:

```text
COMPARE → SWAP → MOVE → REPEAT
```

And the key complexities are:

```text
Time Complexity:

Best    → O(n)      with swapped optimization
Average → O(n²)
Worst   → O(n²)

Space Complexity:

O(1)
```

### One-sentence definition

> **Bubble Sort repeatedly compares neighboring elements and swaps them when they are in the wrong order, causing the largest unsorted element to bubble toward the end of the array after each pass.**
