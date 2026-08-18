# Insertion Sort — Beginner-Friendly Explanation

## 1. What is Insertion Sort?

Imagine you are holding a set of **playing cards**.

You pick up the cards one by one and keep the cards in your hand sorted.

For example, suppose you already have:

```text
[25, 64]
```

Now you pick up:

```text
12
```

You look at the sorted cards:

```text
25  64
```

`12` is smaller than both, so you move the other cards to the right and insert `12` at the beginning:

```text
[12, 25, 64]
```

This is the basic idea behind **Insertion Sort**.

> **Insertion Sort takes one element at a time and inserts it into the correct position in the already-sorted part of the array.**

---

# 2. The Basic Idea

Consider:

```text
[64, 25, 12, 22, 11]
```

We start by considering the first element as already sorted:

```text
[64] | [25, 12, 22, 11]
```

Then we take `25` and insert it into the correct position:

```text
[25, 64] | [12, 22, 11]
```

Then take `12`:

```text
[12, 25, 64] | [22, 11]
```

Then take `22`:

```text
[12, 22, 25, 64] | [11]
```

Finally, take `11`:

```text
[11, 12, 22, 25, 64]
```

So the sorted portion keeps growing:

```text
[64] | [25, 12, 22, 11]

[25, 64] | [12, 22, 11]

[12, 25, 64] | [22, 11]

[12, 22, 25, 64] | [11]

[11, 12, 22, 25, 64]
```

---

# 3. Why Is It Called "Insertion" Sort?

Because every time we take an element, we **insert** it into its correct location.

For example:

```text
[12, 25, 64] | [22]
```

We take:

```text
22
```

and insert it into:

```text
[12, 25, 64]
```

The result is:

```text
[12, 22, 25, 64]
```

So:

```text
Insertion Sort
      ↓
Take an element
      ↓
Find where it belongs
      ↓
Make space for it
      ↓
Insert it
```

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

Insertion Sort uses two important loop variables:

```text
i
j
```

There is also another important variable:

```text
key
```

The three variables have different jobs.

| Variable | Purpose |
|---|---|
| `i` | Selects the element that we want to insert |
| `j` | Moves backward through the sorted portion |
| `key` | Temporarily stores the element we are inserting |

Think of them like this:

```text
i     → Which element am I inserting?

j     → Where am I currently looking?

key   → What element am I trying to insert?
```

---

# 7. `i` — Outer Loop Pointer

`i` moves from left to right.

For example:

```text
i = 1
i = 2
i = 3
i = 4
```

At each `i`, we select the element at that index.

For example:

```text
Index:      0    1    2    3    4
            ↓
            i
Array:     64   25   12   22   11
```

Here:

```text
i = 1
```

So we are going to take:

```text
array[i] = 25
```

and insert it into the sorted portion.

---

# 8. `key` — The Element We Want to Insert

Once `i` selects an element, we temporarily store that element in:

```text
key
```

For example:

```text
i = 1
```

and:

```text
array[1] = 25
```

Therefore:

```text
key = 25
```

Why do we need `key`?

Because while inserting the element, we may need to **move other elements to the right**.

We don't want to lose the element we are trying to insert.

So we temporarily keep it safe:

```text
key = array[i]
```

---

# 9. `j` — Inner Loop Pointer

`j` starts just before `i`.

So:

```text
j = i - 1
```

Then `j` moves **backward**.

This is an important difference from Selection Sort and Bubble Sort.

In Insertion Sort:

```text
i → moves forward
j → moves backward
```

For example:

```text
Index:      0    1    2    3    4
            ↑    ↑
            j    i
```

When:

```text
i = 2
```

`j` can move like this:

```text
j = 1

Index:      0    1    2    3    4
                 ↓    ↓
                 j    i
```

Then:

```text
j = 0

Index:      0    1    2    3    4
            ↓         ↓
            j         i
```

Then `j` can become:

```text
j = -1
```

which means we have moved past the beginning of the array.

---

# 10. The Main Rule of Insertion Sort

This is the most important rule:

> **If the element at `j` is greater than the `key`, move the element at `j` one index to the right.**

For example:

```text
key = 12

Sorted portion:

[25, 64]
  ↑
  j
```

Since:

```text
25 > 12
```

we move `25` one index to the right:

```text
[25, 25, 64]
```

Then we check the previous element.

Since there is no smaller element before `25`, we put `12` at the beginning:

```text
[12, 25, 64]
```

---

# 11. Important Difference — Insertion Sort Does Not Mainly Swap

This is an important difference from Bubble Sort and Selection Sort.

### Selection Sort

```text
Find minimum
    ↓
SWAP
```

### Bubble Sort

```text
Compare neighbors
    ↓
SWAP
```

### Insertion Sort

```text
Take key
    ↓
SHIFT larger elements
    ↓
INSERT key
```

For example:

```text
[25, 64] | [12]
```

Take:

```text
key = 12
```

Shift larger elements:

```text
[25, 64, 64]
[25, 25, 64]
```

Then insert:

```text
[12, 25, 64]
```

So the key idea is:

> **Insertion Sort shifts elements to make space for the key.**

---

# 12. Step 1 — Start With `i = 1`

Why do we start with `i = 1` instead of `i = 0`?

Because we consider the first element to already be sorted.

Our array:

```text
[64, 25, 12, 22, 11]
```

We can think of it as:

```text
[64] | [25, 12, 22, 11]
```

The sorted portion is:

```text
[64]
```

The unsorted portion is:

```text
[25, 12, 22, 11]
```

So:

```text
i = 1
```

Visual:

```text
Index:      0    1    2    3    4
            ↓
            i
Array:     64   25   12   22   11
            ↑
          sorted
```

---

# 13. Step 1 — Select the `key`

We take:

```text
key = array[i]
```

Since:

```text
i = 1
```

we get:

```text
key = 25
```

Current values:

```text
i = 1
key = 25
```

Visual:

```text
Index:      0    1    2    3    4
            ↓    ↓
          sorted  i
Array:     64   25   12   22   11
                 ↓
                key
```

We now need to insert `25` into:

```text
[64]
```

---

# 14. Step 1 — Set `j`

We start `j` one index before `i`.

```text
j = i - 1
```

Therefore:

```text
j = 0
```

Current values:

```text
i = 1
j = 0
key = 25
```

Visual:

```text
Index:      0    1    2    3    4
            ↓    ↓
            j    i
            ↑
          sorted
Array:     64   25   12   22   11
                 ↑
                key
```

---

# 15. Step 1 — Compare `array[j]` and `key`

We compare:

```text
array[j] = 64
key      = 25
```

So:

```text
64 > 25
```

The element at `j` is larger than the key.

Therefore, we need to move `64` one index to the right.

---

# 16. Step 1 — Shift 64

Before shifting:

```text
Index:      0    1    2    3    4
            ↓    ↓
            j    i
Array:     64   25   12   22   11
            ↑
          larger
```

Move `64` to index `1`:

```text
64 → one index to the right
```

The array now temporarily looks like:

```text
[64, 64, 12, 22, 11]
```

Don't worry about the duplicate `64`.

We still have:

```text
key = 25
```

stored safely.

---

# 17. Step 1 — Move `j` Backward

Now:

```text
j = j - 1
```

So:

```text
j = -1
```

Current values:

```text
i = 1
j = -1
key = 25
```

Since `j` is now outside the array on the left, we stop searching.

Now we insert:

```text
key = 25
```

at:

```text
j + 1 = 0
```

Result:

```text
[25, 64, 12, 22, 11]
```

---

# 18. End of Step 1

We started with:

```text
[64, 25, 12, 22, 11]
```

After inserting `25`:

```text
[25, 64, 12, 22, 11]
```

Now the sorted portion has grown:

```text
[25, 64] | [12, 22, 11]
```

Notice:

```text
[25, 64]
```

is sorted.

---

# 19. Step 2 — `i = 2`

Move `i` forward:

```text
i = 2
```

Array:

```text
[25, 64, 12, 22, 11]
```

Visual:

```text
Index:      0    1    2    3    4
                      ↓
                      i
Array:     25   64   12   22   11
            ← sorted →
```

The sorted portion is:

```text
[25, 64]
```

The unsorted portion is:

```text
[12, 22, 11]
```

---

# 20. Step 2 — Select the `key`

Since:

```text
i = 2
```

we take:

```text
key = array[2]
```

Therefore:

```text
key = 12
```

Current values:

```text
i = 2
key = 12
```

Visual:

```text
Index:      0    1    2    3    4
                      ↓
                      i
Array:     25   64   12   22   11
            ← sorted →   ↑
                         key
```

---

# 21. Step 2 — Set `j`

Set:

```text
j = i - 1
```

Therefore:

```text
j = 1
```

Current values:

```text
i = 2
j = 1
key = 12
```

Visual:

```text
Index:      0    1    2    3    4
                 ↓    ↓
                 j    i
Array:     25   64   12   22   11
            ← sorted →   ↑
                         key
```

---

# 22. Step 2 — Compare 64 and 12

We compare:

```text
array[j] = 64
key = 12
```

Since:

```text
64 > 12
```

we shift `64` to the right.

Before:

```text
[25, 64, 12, 22, 11]
      ↑   ↑
      j   key
```

After shifting:

```text
[25, 64, 64, 22, 11]
```

The key is still safe:

```text
key = 12
```

---

# 23. Step 2 — Move `j` Backward

Now:

```text
j = j - 1
```

Therefore:

```text
j = 0
```

Current values:

```text
i = 2
j = 0
key = 12
```

Visual:

```text
Index:      0    1    2    3    4
            ↓         ↓
            j         i
Array:     25   64   64   22   11
                       ↑
                      key
```

Now compare:

```text
array[j] = 25
key = 12
```

Since:

```text
25 > 12
```

we shift `25` one index to the right.

---

# 24. Step 2 — Shift 25

Before:

```text
[25, 64, 64, 22, 11]
 ↑
 j
```

Shift:

```text
25 → index 1
```

Array temporarily becomes:

```text
[25, 25, 64, 22, 11]
```

Again, don't worry about the duplicate.

The `key` is safely stored:

```text
key = 12
```

---

# 25. Step 2 — Move `j` Again

Now:

```text
j = j - 1
```

Therefore:

```text
j = -1
```

Current values:

```text
i = 2
j = -1
key = 12
```

We've reached before the beginning of the array.

Therefore, insert the key at:

```text
j + 1 = 0
```

Result:

```text
[12, 25, 64, 22, 11]
```

---

# 26. End of Step 2

The sorted portion is now:

```text
[12, 25, 64]
```

The unsorted portion is:

```text
[22, 11]
```

So:

```text
[12, 25, 64] | [22, 11]
```

Notice how the sorted portion grows.

---

# 27. Step 3 — `i = 3`

Move `i`:

```text
i = 3
```

Array:

```text
[12, 25, 64, 22, 11]
```

Visual:

```text
Index:      0    1    2    3    4
                           ↓
                           i
Array:     12   25   64   22   11
            ← sorted →     ↑
```

The sorted portion is:

```text
[12, 25, 64]
```

---

# 28. Step 3 — Select the `key`

Since:

```text
i = 3
```

we take:

```text
key = array[3]
```

Therefore:

```text
key = 22
```

Current values:

```text
i = 3
key = 22
```

---

# 29. Step 3 — Set `j`

Set:

```text
j = i - 1
```

Therefore:

```text
j = 2
```

Current values:

```text
i = 3
j = 2
key = 22
```

Visual:

```text
Index:      0    1    2    3    4
                      ↓    ↓
                      j    i
Array:     12   25   64   22   11
            ← sorted →     ↑
                          key
```

---

# 30. Step 3 — Compare 64 and 22

We compare:

```text
array[j] = 64
key = 22
```

Since:

```text
64 > 22
```

shift `64` right.

Before:

```text
[12, 25, 64, 22, 11]
          ↑   ↑
          j  key
```

After:

```text
[12, 25, 64, 64, 11]
```

Now move `j` backward:

```text
j = 1
```

---

# 31. Step 3 — Compare 25 and 22

Current values:

```text
i = 3
j = 1
key = 22
```

Visual:

```text
Index:      0    1    2    3    4
                 ↓         ↓
                 j         i
Array:     12   25   64   64   11
```

Compare:

```text
25 > 22
```

So shift `25` right:

```text
[12, 25, 25, 64, 11]
```

Move `j` backward:

```text
j = 0
```

---

# 32. Step 3 — Compare 12 and 22

Current values:

```text
i = 3
j = 0
key = 22
```

Compare:

```text
array[j] = 12
key = 22
```

Now:

```text
12 > 22
```

is **false**.

That means:

> We found the correct place for `22`.

The element before this location is already smaller than `22`.

So we stop shifting.

---

# 33. Step 3 — Insert 22

We insert:

```text
key = 22
```

at:

```text
j + 1 = 1
```

Result:

```text
[12, 22, 25, 64, 11]
```

Now:

```text
[12, 22, 25, 64] | [11]
```

The first four elements are sorted.

---

# 34. Step 4 — `i = 4`

Move `i`:

```text
i = 4
```

Array:

```text
[12, 22, 25, 64, 11]
```

The sorted portion is:

```text
[12, 22, 25, 64]
```

The unsorted portion contains only:

```text
[11]
```

Visual:

```text
Index:      0    1    2    3    4
                                ↓
                                i
Array:     12   22   25   64   11
            ←--- sorted ---→
```

---

# 35. Step 4 — Select the `key`

Since:

```text
i = 4
```

we take:

```text
key = array[4]
```

Therefore:

```text
key = 11
```

Current values:

```text
i = 4
key = 11
```

---

# 36. Step 4 — Set `j`

Set:

```text
j = i - 1
```

Therefore:

```text
j = 3
```

Current values:

```text
i = 4
j = 3
key = 11
```

Visual:

```text
Index:      0    1    2    3    4
                           ↓    ↓
                           j    i
Array:     12   22   25   64   11
                           ↑
                          key
```

---

# 37. Step 4 — Compare 64 and 11

```text
64 > 11
```

So shift `64`:

```text
[12, 22, 25, 64, 64]
```

Move:

```text
j = 2
```

---

# 38. Step 4 — Compare 25 and 11

Current values:

```text
i = 4
j = 2
key = 11
```

Compare:

```text
25 > 11
```

So shift:

```text
[12, 22, 25, 25, 64]
```

Move:

```text
j = 1
```

---

# 39. Step 4 — Compare 22 and 11

Compare:

```text
22 > 11
```

So shift:

```text
[12, 22, 22, 25, 64]
```

Move:

```text
j = 0
```

---

# 40. Step 4 — Compare 12 and 11

Compare:

```text
12 > 11
```

So shift:

```text
[12, 12, 22, 25, 64]
```

Move:

```text
j = -1
```

We have reached the beginning of the array.

So insert:

```text
key = 11
```

at:

```text
j + 1 = 0
```

Result:

```text
[11, 12, 22, 25, 64]
```

The array is sorted!

---

# 41. Complete Sorting Process

Let's see the complete process without every individual comparison.

## Starting Array

```text
[64, 25, 12, 22, 11]
```

## Step 1 — `i = 1`

Take:

```text
key = 25
```

Sorted portion:

```text
[64]
```

`64 > 25`, so shift `64`:

```text
[64, 64, 12, 22, 11]
```

Insert `25`:

```text
[25, 64, 12, 22, 11]
```

Sorted portion:

```text
[25, 64] | [12, 22, 11]
```

## Step 2 — `i = 2`

Take:

```text
key = 12
```

Compare with `64`:

```text
64 > 12
```

Shift:

```text
[25, 64, 64, 22, 11]
```

Compare with `25`:

```text
25 > 12
```

Shift:

```text
[25, 25, 64, 22, 11]
```

Insert `12`:

```text
[12, 25, 64, 22, 11]
```

Sorted portion:

```text
[12, 25, 64] | [22, 11]
```

## Step 3 — `i = 3`

Take:

```text
key = 22
```

Compare with `64`:

```text
64 > 22
```

Shift:

```text
[12, 25, 64, 64, 11]
```

Compare with `25`:

```text
25 > 22
```

Shift:

```text
[12, 25, 25, 64, 11]
```

Compare with `12`:

```text
12 > 22
```

False.

Insert `22`:

```text
[12, 22, 25, 64, 11]
```

Sorted portion:

```text
[12, 22, 25, 64] | [11]
```

## Step 4 — `i = 4`

Take:

```text
key = 11
```

Shift `64`:

```text
[12, 22, 25, 64, 64]
```

Shift `25`:

```text
[12, 22, 25, 25, 64]
```

Shift `22`:

```text
[12, 22, 22, 25, 64]
```

Shift `12`:

```text
[12, 12, 22, 25, 64]
```

Insert `11`:

```text
[11, 12, 22, 25, 64]
```

Done!

---

# 42. The Most Important Visual

The easiest way to understand Insertion Sort is to imagine a **sorted section growing from left to right**.

Start:

```text
[64] | [25, 12, 22, 11]
 ↑
sorted
```

After inserting `25`:

```text
[25, 64] | [12, 22, 11]
    ↑
  sorted
```

After inserting `12`:

```text
[12, 25, 64] | [22, 11]
       ↑
     sorted
```

After inserting `22`:

```text
[12, 22, 25, 64] | [11]
          ↑
        sorted
```

After inserting `11`:

```text
[11, 12, 22, 25, 64]
```

The sorted section keeps growing:

```text
1 element
    ↓
2 elements
    ↓
3 elements
    ↓
4 elements
    ↓
5 elements
```

---

# 43. What Are `i`, `j`, and `key` Doing?

Let's summarize the three important variables.

## `i`

`i` selects the next element that we want to insert.

```text
i → SELECT
```

It moves:

```text
1 → 2 → 3 → 4
```

## `key`

`key` stores the element that we are currently inserting.

```text
key → WHAT AM I INSERTING?
```

For example:

```text
i = 3

array[3] = 22

key = 22
```

## `j`

`j` moves backward through the sorted portion.

```text
j → SEARCH BACKWARD
```

For example:

```text
i = 4

j = 3
j = 2
j = 1
j = 0
j = -1
```

---

# 44. The Three Variables Together

Suppose:

```text
[12, 25, 64, 22, 11]
```

and:

```text
i = 3
```

Then:

```text
key = 22
```

and:

```text
j = 2
```

Visual:

```text
Index:      0    1    2    3    4
                      ↓    ↓
                      j    i
Array:     12   25   64   22   11
                      ↑
                     j
                           ↑
                          key
```

Now:

```text
64 > 22
```

so move `64` right:

```text
[12, 25, 64, 64, 11]
```

Then:

```text
j = 1
```

Compare:

```text
25 > 22
```

Shift:

```text
[12, 25, 25, 64, 11]
```

Then:

```text
j = 0
```

Compare:

```text
12 > 22
```

False.

So we stop.

Insert `22` at:

```text
j + 1 = 1
```

Result:

```text
[12, 22, 25, 64, 11]
```

---

# 45. Why Do We Shift Instead of Swap?

This is one of the most important concepts in Insertion Sort.

Suppose:

```text
[12, 25, 64] | [22]
```

We want to insert `22`.

We could think about swapping:

```text
64 ↔ 22
```

giving:

```text
[12, 25, 22, 64]
```

But `22` still needs to move before `25`.

So we would need another swap:

```text
25 ↔ 22
```

giving:

```text
[12, 22, 25, 64]
```

Instead, Insertion Sort thinks:

> "I already know `22` needs to go somewhere before these larger elements. I'll shift those larger elements to the right and then insert `22`."

So:

```text
[12, 25, 64] | [22]
```

Take:

```text
key = 22
```

Shift `64`:

```text
[12, 25, 64, 64]
```

Shift `25`:

```text
[12, 25, 25, 64]
```

Insert `22`:

```text
[12, 22, 25, 64]
```

This is the key operation of Insertion Sort.

---

# 46. Insertion Sort vs Bubble Sort

## Bubble Sort

Bubble Sort repeatedly compares neighbors:

```text
[64, 25, 12, 22, 11]

64 25 → swap
25 12 → swap
12 22 → no swap
22 11 → swap
```

Its main operation is:

```text
COMPARE → SWAP
```

## Insertion Sort

Insertion Sort takes one element and inserts it:

```text
[25, 64] | [12]
```

Take:

```text
key = 12
```

Shift larger elements:

```text
[25, 64, 64]
[25, 25, 64]
```

Insert:

```text
[12, 25, 64]
```

Its main operation is:

```text
SELECT → SHIFT → INSERT
```

---

# 47. Insertion Sort vs Selection Sort

Selection Sort:

```text
Find the smallest
        ↓
Swap with current element
```

Insertion Sort:

```text
Take current element
        ↓
Move larger elements
        ↓
Insert current element
```

So:

```text
Selection Sort → Find minimum

Insertion Sort → Insert current element
```

---

# 48. Time Complexity

Insertion Sort has two loops in the worst case.

The outer loop selects each element.

The inner loop may move backward through the sorted portion.

For example:

```text
[5, 4, 3, 2, 1]
```

the array is in reverse order.

When inserting `1`, we may have to move:

```text
5
4
3
2
```

When inserting `2`, we may have to move:

```text
5
4
3
```

And so on.

So the number of operations can grow approximately like:

```text
n²
```

Therefore:

```text
Average Case = O(n²)
Worst Case   = O(n²)
```

---

# 49. Best Case

Now consider an already sorted array:

```text
[11, 12, 22, 25, 64]
```

What happens?

Take `12`.

Compare:

```text
11 < 12
```

No shifting is required.

Take `22`.

Compare:

```text
12 < 22
```

No shifting is required.

Take `25`.

```text
22 < 25
```

No shifting.

Take `64`.

```text
25 < 64
```

No shifting.

We only need to make approximately one comparison for each element.

Therefore:

```text
Best Case = O(n)
```

This is an important advantage of Insertion Sort.

---

# 50. Time Complexity Summary

| Case | Time Complexity |
|---|---|
| Best Case | O(n) |
| Average Case | O(n²) |
| Worst Case | O(n²) |

The best case happens when the array is already sorted or nearly sorted.

---

# 51. Space Complexity

Insertion Sort works directly on the original array.

It does not create another array.

We only need a few variables:

```text
i
j
key
```

The amount of extra memory stays constant.

Therefore:

```text
Space Complexity = O(1)
```

Insertion Sort is an **in-place sorting algorithm**.

---

# 52. Is Insertion Sort Stable?

Yes.

Insertion Sort can be implemented as a **stable sorting algorithm**.

Suppose we have:

```text
(Alex, 80)
(John, 80)
```

If Alex comes before John originally, Insertion Sort can preserve:

```text
Alex → John
```

because we only shift an element when it is **greater than** the key.

We don't move equal elements unnecessarily.

Therefore:

```text
Stable = Yes
```

---

# 53. Why Is Insertion Sort Useful?

Insertion Sort is more useful than Bubble Sort and Selection Sort in certain situations.

## Advantage 1 — Very Good for Small Arrays

For small arrays, Insertion Sort is simple and often performs well.

For example:

```text
[5, 2, 4, 1]
```

The overhead of using a more complicated sorting algorithm may not be worthwhile.

---

# 54. Advantage 2 — Excellent for Nearly Sorted Arrays

This is one of the biggest advantages.

Consider:

```text
[10, 20, 30, 40, 35, 50]
```

The array is almost sorted.

Only `35` is out of place.

Insertion Sort can quickly move `35` into the correct location:

```text
[10, 20, 30, 35, 40, 50]
```

It doesn't need to do a huge amount of work.

Its best-case complexity is:

```text
O(n)
```

and it performs very well when the array is **already sorted or nearly sorted**.

---

# 55. Advantage 3 — In-Place

Insertion Sort requires:

```text
O(1)
```

extra space.

It doesn't need another array.

---

# 56. Advantage 4 — Stable

Insertion Sort can maintain the order of equal elements.

Therefore it is useful when the order of equal elements matters.

---

# 57. Advantage 5 — Can Sort Data As It Arrives

Insertion Sort has another interesting use.

Imagine numbers arrive one at a time:

```text
First number:
10
```

Then:

```text
20
```

Then:

```text
15
```

We can maintain a sorted collection:

```text
[10]

[10, 20]

[10, 15, 20]
```

This is similar to how you might keep a hand of playing cards sorted while receiving cards one at a time.

This makes the basic idea of Insertion Sort useful when data arrives incrementally.

---

# 58. When Should You NOT Use Insertion Sort?

## 1. Large Random Arrays

For a large randomly ordered array, Insertion Sort generally takes:

```text
O(n²)
```

time.

That can be slow.

For large datasets, algorithms such as:

```text
Merge Sort
Quick Sort
Heap Sort
```

are generally more appropriate.

---

## 2. Reverse-Sorted Arrays

Consider:

```text
[5, 4, 3, 2, 1]
```

This is one of the worst situations for Insertion Sort.

Every new element needs to move almost all the way to the beginning.

Therefore:

```text
Worst Case = O(n²)
```

---

# 59. Selection vs Bubble vs Insertion Sort

| Property | Selection Sort | Bubble Sort | Insertion Sort |
|---|---|---|---|
| Best Case | O(n²) | O(n)* | O(n) |
| Average Case | O(n²) | O(n²) | O(n²) |
| Worst Case | O(n²) | O(n²) | O(n²) |
| Extra Space | O(1) | O(1) | O(1) |
| In-place | Yes | Yes | Yes |
| Stable | Usually No | Yes | Yes |
| Main Idea | Find minimum | Compare neighbors | Insert element |
| Main Operation | Swap | Swap | Shift |
| Nearly Sorted Data | Not especially good | Can improve | **Very good** |
| Small Data | Good | Good | **Very good** |
| Large Data | No | No | No |

\* `O(n)` for Bubble Sort when using the early-termination `swapped` optimization.

---

# 60. The Three Algorithms in One Picture

## Selection Sort

```text
Find smallest
      ↓
Swap
      ↓
Move forward
```

```text
[64, 25, 12, 22, 11]
 ↓
find 11
 ↓
swap
 ↓
[11, 25, 12, 22, 64]
```

## Bubble Sort

```text
Compare neighbors
      ↓
Swap if needed
      ↓
Move forward
```

```text
64 25 → swap
25 12 → swap
12 22 → no swap
22 11 → swap
```

## Insertion Sort

```text
Take element
      ↓
Shift larger elements
      ↓
Insert element
```

```text
[25, 64] | [12]

key = 12

[25, 64, 64]
[25, 25, 64]
[12, 25, 64]
```

---

# 61. Insertion Sort Mental Model

If you remember only one thing, remember this:

```text
                 ARRAY
                   |
                   ↓
             Select array[i]
                   |
                   ↓
               Store as key
                   |
                   ↓
             j = i - 1
                   |
                   ↓
        Look backward through
          sorted portion
                   |
                   ↓
       Is array[j] > key?
              /       \
            YES        NO
             ↓          ↓
       Shift array[j]   Stop
       one step right
             |
             ↓
        Move j backward
             |
             ↓
            Repeat
             |
             ↓
      Insert key at j + 1
             |
             ↓
       Move i forward
             |
             ↓
           Repeat
```

---

# 62. The Complete Algorithm in Plain English

You can explain Insertion Sort to a beginner using these steps:

```text
1. Consider the first element as sorted.

2. Start i from index 1.

3. Take the element at index i.
   Store it in key.

4. Start j one index before i.

5. Compare the element at j with key.

6. If the element at j is greater than key,
   move it one index to the right.

7. Move j one index backward.

8. Continue until you find an element
   smaller than or equal to key,
   or reach the beginning of the array.

9. Insert key at index j + 1.

10. Move i to the next index.

11. Repeat until the entire array is sorted.
```

The easiest way to remember it is:

```text
SELECT → SHIFT → INSERT → REPEAT
```

---

# 63. Java-Style Pseudocode

The following is **Java-style pseudocode**.

The class and method structure resemble Java, but the method contains pseudocode instead of actual Java implementation.

```text
BEGIN InsertionSort

    CLASS InsertionSort

        METHOD insertionSort(array)

            FOR i FROM 1 TO array.length - 1

                // Select the element that
                // needs to be inserted.

                key = array[i]

                // Start searching from the
                // element immediately before key.

                j = i - 1

                // Move larger elements one index
                // to the right to make space for key.

                WHILE j >= 0 AND array[j] > key

                    array[j + 1] = array[j]

                    j = j - 1

                END WHILE

                // Insert key into the empty location.

                array[j + 1] = key

            END FOR

        END METHOD

    END CLASS

END InsertionSort
```

---

# 64. Pseudocode Explained

## Start the algorithm

```text
BEGIN InsertionSort
```

This means:

> Start the Insertion Sort algorithm.

## Create the class

```text
CLASS InsertionSort
```

This represents our Java class.

## Create the method

```text
METHOD insertionSort(array)
```

The method receives the array that needs to be sorted.

## Outer loop

```text
FOR i FROM 1 TO array.length - 1
```

We start `i` at `1`.

Why?

Because:

```text
index 0
```

is considered already sorted.

## Store the element in `key`

```text
key = array[i]
```

We temporarily save the element we want to insert.

## Move `j` backward

```text
j = i - 1
```

The element immediately before `key` is where we start comparing.

## Shift larger elements

```text
WHILE j >= 0 AND array[j] > key
```

This means:

> Keep moving backward while we are still inside the array and the current element is larger than the key.

Then:

```text
array[j + 1] = array[j]
```

means:

> Move the larger element one index to the right.

Then:

```text
j = j - 1
```

means:

> Move `j` one index backward.

## Insert the key

Once we find the correct location:

```text
array[j + 1] = key
```

We insert the key there.

---

# 65. Final Pointer Visualization

For Insertion Sort, remember:

```text
i → selects the element

key → stores the selected element

j → moves backward through the sorted section
```

For example:

```text
[12, 25, 64, 22, 11]
```

When:

```text
i = 3
```

we select:

```text
key = 22
```

Then:

```text
j = 2
```

Visual:

```text
Index:      0    1    2    3    4
                      ↓    ↓
                      j    i
Array:     12   25   64   22   11
                      ↑
                     j
                           ↑
                          key
```

Compare:

```text
64 > 22
```

Shift:

```text
[12, 25, 64, 64, 11]
```

Move `j`:

```text
j = 1
```

Compare:

```text
25 > 22
```

Shift:

```text
[12, 25, 25, 64, 11]
```

Move `j`:

```text
j = 0
```

Compare:

```text
12 > 22
```

False.

So insert:

```text
key = 22
```

at:

```text
j + 1 = 1
```

Result:

```text
[12, 22, 25, 64, 11]
```

---

# 66. Final Concept to Remember

Insertion Sort has:

```text
OUTER LOOP
    i
    ↓
    Select the next element

    key
    ↓
    Remember the element

    INNER LOOP
        j
        ↓
        Move backward

        Compare:

        array[j] > key
              ↓
           SHIFT
              ↓
        j moves backward
              ↓
            REPEAT

    Insert key at j + 1
```

The complete mental model is:

```text
             INSERTION SORT

                  i
                  ↓
          Select an element
                  |
                  ↓
             Store as key
                  |
                  ↓
              j = i - 1
                  |
                  ↓
       Look backward through
        sorted portion
                  |
                  ↓
          Is array[j] > key?
             /          \
           YES           NO
            ↓             ↓
        SHIFT RIGHT       STOP
            |
            ↓
        Move j backward
            |
            ↓
          REPEAT
            |
            ↓
       Insert key at j + 1
            |
            ↓
        Move i forward
            |
            ↓
          REPEAT
```

The easiest way to remember Insertion Sort is:

```text
SELECT → SHIFT → INSERT → REPEAT
```

And the key complexities are:

```text
Time Complexity:

Best    → O(n)
Average → O(n²)
Worst   → O(n²)

Space Complexity:

O(1)
```

### One-sentence definition

> **Insertion Sort takes one element at a time, shifts larger elements in the sorted portion to the right, and inserts the selected element into its correct position.**

### Best situation to use it

> **Small or nearly sorted arrays**, where its `O(n)` best-case behavior and low overhead can make it very effective.

### When to avoid it

> **Large, randomly ordered datasets**, where `O(n²)` average and worst-case performance becomes too slow.
