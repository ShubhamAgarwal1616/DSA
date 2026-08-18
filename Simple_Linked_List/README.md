# Singly Linked List --- Beginner-Friendly Explanation

## 1. What Is a Linked List?

Before learning a Linked List, let's understand the problem it solves.

Suppose we have an array:

``` text
[10, 20, 30, 40, 50]
```

The elements are stored next to each other in memory conceptually:

``` text
10   20   30   40   50
```

An array is useful, but inserting or deleting elements in the middle can
require shifting many elements.

A Linked List uses a different idea.

Instead of storing only the value, each element stores:

1.  The value
2.  A reference to the next element

For example:

``` text
10 → 20 → 30 → 40 → 50 → null
```

Each box is called a **Node**.

The basic idea is:

``` text
[DATA | NEXT]
```

For example:

``` text
[10 | address of 20]
```

The `NEXT` part tells us where the next node is located.

------------------------------------------------------------------------

# 2. What Is a Node?

A Linked List is made up of nodes.

A node contains two important pieces of information:

``` text
+---------+---------+
|  data   |  next   |
+---------+---------+
```

For example:

``` text
+---------+---------+
|   10    |   •─────┼──→ next node
+---------+---------+
```

In Java-style pseudocode:

``` text
CLASS Node

    data
    next

END CLASS
```

For an integer Linked List:

``` text
CLASS Node

    INTEGER data
    Node next

END CLASS
```

Notice that:

``` text
Node next
```

means the node stores a reference to another `Node`.

------------------------------------------------------------------------

# 3. Understanding the `next` Reference

Suppose we have three nodes:

``` text
Node A
data = 10

Node B
data = 20

Node C
data = 30
```

We connect them:

``` text
A → B → C → null
```

Visually:

``` text
+------+-------+      +------+-------+      +------+-------+
|  10  |   •───┼─────→|  20  |   •───┼─────→|  30  | null  |
+------+-------+      +------+-------+      +------+-------+
```

The `next` reference of the first node points to the second node.

The `next` reference of the second node points to the third node.

The `next` reference of the third node is:

``` text
null
```

because there is no next node.

------------------------------------------------------------------------

# 4. What Is a Singly Linked List?

There are different types of Linked Lists.

The simplest one is the:

> **Singly Linked List**

In a Singly Linked List, every node points only to the **next** node.

``` text
10 → 20 → 30 → 40 → null
```

The direction is only forward:

``` text
10 → 20 → 30 → 40
```

We cannot directly move backward from `40` to `30`.

That is one of the main differences between a Singly Linked List and a
Doubly Linked List.

------------------------------------------------------------------------

# 5. What Is `head`?

A Linked List needs a way to find its first node.

We use a variable called:

``` text
head
```

`head` points to the first node.

For example:

``` text
head
 ↓
10 → 20 → 30 → 40 → null
```

Think of `head` as the **starting point** of the Linked List.

If we lose `head`, we lose our direct way to reach the list.

------------------------------------------------------------------------

# 6. Empty Linked List

What does an empty Linked List look like?

There are no nodes.

Therefore:

``` text
head → null
```

In pseudocode:

``` text
head = null
```

This means:

> There is currently no first node.

------------------------------------------------------------------------

# 7. A Complete Linked List Example

Suppose we have:

``` text
10
20
30
40
```

The Linked List looks like:

``` text
head
 ↓
+----+------+    +----+------+    +----+------+    +----+------+
| 10 |  •───┼───→| 20 |  •───┼───→| 30 |  •───┼───→| 40 | null |
+----+------+    +----+------+    +----+------+    +----+------+
```

There are four nodes.

The important references are:

``` text
head → 10
10.next → 20
20.next → 30
30.next → 40
40.next → null
```

------------------------------------------------------------------------

# 8. Array vs Linked List

Let's compare the basic idea.

  Property              Array                             Singly Linked List
  --------------------- --------------------------------- -------------------------------
  Storage               Contiguous                        Nodes connected by references
  Access by index       Fast                              Requires traversal
  Insert at beginning   Usually expensive                 Easy
  Delete at beginning   Usually expensive                 Easy
  Dynamic size          Limited by array representation   Easy to grow
  Extra memory          Low                               Extra memory for `next`
  Random access         Yes                               No

The most important difference for beginners is:

``` text
Array:

index → element
```

while:

``` text
Linked List:

head → node → node → node
```

------------------------------------------------------------------------

# 9. Why Do We Need Linked Lists?

Consider this array:

``` text
[10, 20, 30, 40, 50]
```

Suppose we want to insert `5` at the beginning.

The array may need to shift everything:

``` text
[10, 20, 30, 40, 50]

        ↓ shift

[5, 10, 20, 30, 40, 50]
```

A Linked List can simply create a new node and make it point to the
current first node:

``` text
Before:

head
 ↓
10 → 20 → 30 → null
```

Create `5`:

``` text
5
```

Connect it:

``` text
5 → 10 → 20 → 30 → null
```

Move `head`:

``` text
head
 ↓
5 → 10 → 20 → 30 → null
```

No shifting is required.

------------------------------------------------------------------------

# 10. The Linked List Class

A simple Linked List needs a `Node` class and a `head` reference.

Java-style pseudocode:

``` text
BEGIN SinglyLinkedList

    CLASS Node

        INTEGER data
        Node next

    END CLASS


    CLASS LinkedList

        Node head

    END CLASS

END SinglyLinkedList
```

Initially:

``` text
head = null
```

------------------------------------------------------------------------

# 11. Creating a Node

Suppose we want to create a node containing `10`.

Java-style pseudocode:

``` text
BEGIN CreateNode

    CLASS Node

        INTEGER data
        Node next

        CONSTRUCTOR Node(value)

            data = value
            next = null

        END CONSTRUCTOR

    END CLASS

END CreateNode
```

After creating:

``` text
Node node = new Node(10)
```

the node looks like:

``` text
+------+------+
|  10  | null |
+------+------+
```

------------------------------------------------------------------------

# 12. Operation 1 --- Check If the List Is Empty

Before performing many operations, it is useful to know whether the list
contains any nodes.

The list is empty when:

``` text
head == null
```

## Example

``` text
head
 ↓
null
```

Therefore:

``` text
isEmpty = true
```

## Java-Style Pseudocode

``` text
BEGIN IsEmpty

    METHOD isEmpty()

        IF head == null THEN
            RETURN true
        END IF

        RETURN false

    END METHOD

END IsEmpty
```

A shorter version can be:

``` text
BEGIN IsEmpty

    METHOD isEmpty()

        RETURN head == null

    END METHOD

END IsEmpty
```

------------------------------------------------------------------------

# 13. Operation 2 --- Insert at the Beginning

This is one of the easiest Linked List operations.

Suppose we have:

``` text
head
 ↓
10 → 20 → 30 → null
```

We want to insert:

``` text
5
```

## Step 1 --- Create a new node

``` text
newNode
   ↓
   5
```

## Step 2 --- Connect the new node to the current head

``` text
newNode
   ↓
   5 ─────→ 10 → 20 → 30 → null
             ↑
            head
```

In other words:

``` text
newNode.next = head
```

## Step 3 --- Move head to the new node

``` text
head
 ↓
5 → 10 → 20 → 30 → null
```

The important two statements are:

``` text
newNode.next = head
head = newNode
```

## Java-Style Pseudocode

``` text
BEGIN InsertAtBeginning

    METHOD insertAtBeginning(value)

        newNode = new Node(value)

        newNode.next = head

        head = newNode

    END METHOD

END InsertAtBeginning
```

## Time Complexity

``` text
O(1)
```

We don't need to traverse the list.

------------------------------------------------------------------------

# 14. Operation 3 --- Insert at the End

Suppose:

``` text
head
 ↓
10 → 20 → 30 → null
```

We want to insert:

``` text
40
```

We first create:

``` text
newNode
   ↓
+----+------+
| 40 | null |
+----+------+
```

The new node should become the last node.

## Step 1 --- Handle an Empty List

If:

``` text
head == null
```

then the new node becomes the head:

``` text
head
 ↓
40 → null
```

## Step 2 --- Traverse to the Last Node

Start at:

``` text
current = head
```

Then move:

``` text
10 → 20 → 30
```

We stop when:

``` text
current.next == null
```

That means we are at the last node.

## Step 3 --- Connect the New Node

Before:

``` text
10 → 20 → 30 → null
```

After:

``` text
10 → 20 → 30 → 40 → null
```

We perform:

``` text
current.next = newNode
```

## Java-Style Pseudocode

``` text
BEGIN InsertAtEnd

    METHOD insertAtEnd(value)

        newNode = new Node(value)

        IF head == null THEN

            head = newNode

            RETURN

        END IF

        current = head

        WHILE current.next != null

            current = current.next

        END WHILE

        current.next = newNode

    END METHOD

END InsertAtEnd
```

## Time Complexity

Without a `tail` reference:

``` text
O(n)
```

because we may need to traverse the entire list.

------------------------------------------------------------------------

# 15. Operation 4 --- Insert at a Specific Position

Now let's insert a node at a particular position.

Suppose:

``` text
Position:
0    1    2    3

10 → 20 → 30 → 40 → null
```

We want to insert:

``` text
25
```

at position `2`.

The result should be:

``` text
10 → 20 → 25 → 30 → 40 → null
```

## Important Idea

To insert at position `2`, we need to reach the node at:

``` text
position - 1
```

which is:

``` text
position 1
```

That node is:

``` text
20
```

Before insertion:

``` text
10 → 20 → 30 → 40
     ↑
   previous
```

Create:

``` text
25
```

Then:

``` text
newNode.next = previous.next
```

So:

``` text
25 → 30
```

Then:

``` text
previous.next = newNode
```

Final:

``` text
10 → 20 → 25 → 30 → 40 → null
```

## Java-Style Pseudocode

``` text
BEGIN InsertAtPosition

    METHOD insertAtPosition(value, position)

        IF position < 0 THEN

            DISPLAY "Invalid position"

            RETURN

        END IF


        IF position == 0 THEN

            insertAtBeginning(value)

            RETURN

        END IF


        newNode = new Node(value)

        current = head

        FOR i FROM 0 TO position - 2

            IF current == null THEN

                DISPLAY "Invalid position"

                RETURN

            END IF

            current = current.next

        END FOR


        IF current == null THEN

            DISPLAY "Invalid position"

            RETURN

        END IF


        newNode.next = current.next

        current.next = newNode

    END METHOD

END InsertAtPosition
```

## Time Complexity

``` text
O(n)
```

because we may need to traverse the list to reach the required position.

------------------------------------------------------------------------

# 16. Operation 5 --- Traverse the Linked List

Traversal means:

> Visit every node in the Linked List.

Suppose:

``` text
head
 ↓
10 → 20 → 30 → 40 → null
```

We start from `head`.

``` text
current = head
```

Then:

``` text
current = current.next
```

again and again.

The movement is:

``` text
10
 ↓
20
 ↓
30
 ↓
40
 ↓
null
```

## Java-Style Pseudocode

``` text
BEGIN Traverse

    METHOD display()

        current = head

        WHILE current != null

            DISPLAY current.data

            current = current.next

        END WHILE

    END METHOD

END Traverse
```

## Time Complexity

``` text
O(n)
```

because every node may be visited once.

------------------------------------------------------------------------

# 17. Understanding `current`

`current` is a temporary reference used to walk through the list.

Suppose:

``` text
head
 ↓
10 → 20 → 30 → null
```

Initially:

``` text
current = head
```

So:

``` text
current
   ↓
   10 → 20 → 30 → null
```

Then:

``` text
current = current.next
```

Now:

``` text
head
 ↓
10 → 20 → 30 → null
      ↑
    current
```

Again:

``` text
current = current.next
```

Now:

``` text
head
 ↓
10 → 20 → 30 → null
           ↑
         current
```

Again:

``` text
current = current.next
```

Now:

``` text
current = null
```

The traversal ends.

------------------------------------------------------------------------

# 18. Operation 6 --- Search for a Value

Suppose:

``` text
10 → 20 → 30 → 40 → null
```

We want to find:

``` text
30
```

We start from `head`.

At each node:

``` text
Is current.data equal to the target?
```

If yes:

``` text
FOUND
```

If no:

``` text
Move to current.next
```

## Java-Style Pseudocode

``` text
BEGIN Search

    METHOD search(target)

        current = head

        WHILE current != null

            IF current.data == target THEN

                RETURN true

            END IF

            current = current.next

        END WHILE

        RETURN false

    END METHOD

END Search
```

## Example

Searching for `30`:

``` text
10 → 20 → 30 → 40 → null
↑
check 10
```

Not found.

Move:

``` text
10 → 20 → 30 → 40 → null
     ↑
   check 20
```

Not found.

Move:

``` text
10 → 20 → 30 → 40 → null
          ↑
        check 30
```

Found.

## Time Complexity

``` text
O(n)
```

Worst case, we may have to inspect every node.

------------------------------------------------------------------------

# 19. Operation 7 --- Get Value at a Position

Arrays allow:

``` text
array[3]
```

to directly access an element.

A Singly Linked List does not have direct random access.

If we want position `3`, we must traverse the list.

Suppose:

``` text
Position:  0    1    2    3

           10 → 20 → 30 → 40 → null
```

To get position `3`, we move:

``` text
10 → 20 → 30 → 40
```

## Java-Style Pseudocode

``` text
BEGIN GetAtPosition

    METHOD get(position)

        IF position < 0 THEN

            DISPLAY "Invalid position"

            RETURN null

        END IF

        current = head

        FOR i FROM 0 TO position - 1

            IF current == null THEN

                DISPLAY "Position does not exist"

                RETURN null

            END IF

            current = current.next

        END FOR


        IF current == null THEN

            DISPLAY "Position does not exist"

            RETURN null

        END IF


        RETURN current.data

    END METHOD

END GetAtPosition
```

## Time Complexity

``` text
O(n)
```

------------------------------------------------------------------------

# 20. Operation 8 --- Update a Value

Suppose:

``` text
10 → 20 → 30 → 40 → null
```

We want to change `30` to `35`.

We first find the node.

``` text
10 → 20 → 30 → 40
          ↑
        current
```

Then:

``` text
current.data = 35
```

Result:

``` text
10 → 20 → 35 → 40 → null
```

## Java-Style Pseudocode

``` text
BEGIN UpdateValue

    METHOD update(position, newValue)

        IF position < 0 THEN

            DISPLAY "Invalid position"

            RETURN

        END IF

        current = head

        FOR i FROM 0 TO position - 1

            IF current == null THEN

                DISPLAY "Position does not exist"

                RETURN

            END IF

            current = current.next

        END FOR


        IF current == null THEN

            DISPLAY "Position does not exist"

            RETURN

        END IF


        current.data = newValue

    END METHOD

END UpdateValue
```

## Time Complexity

``` text
O(n)
```

------------------------------------------------------------------------

# 21. Operation 9 --- Delete from the Beginning

Suppose:

``` text
head
 ↓
10 → 20 → 30 → 40 → null
```

We want to delete `10`.

The solution is simple:

``` text
head = head.next
```

Before:

``` text
head
 ↓
10 → 20 → 30 → null
```

After:

``` text
      head
       ↓
10 → 20 → 30 → null
     ↑
   new first node
```

The node containing `10` is no longer reachable from `head`.

The list is now:

``` text
head
 ↓
20 → 30 → null
```

## Java-Style Pseudocode

``` text
BEGIN DeleteFromBeginning

    METHOD deleteFromBeginning()

        IF head == null THEN

            DISPLAY "List is empty"

            RETURN

        END IF

        head = head.next

    END METHOD

END DeleteFromBeginning
```

## Time Complexity

``` text
O(1)
```

------------------------------------------------------------------------

# 22. Operation 10 --- Delete from the End

Suppose:

``` text
head
 ↓
10 → 20 → 30 → 40 → null
```

We want to delete `40`.

The problem is that we need to reach the node **before** the last node.

That node is:

``` text
30
```

We need to find:

``` text
current.next.next == null
```

Then we can remove the last node by changing:

``` text
current.next = null
```

Before:

``` text
10 → 20 → 30 → 40 → null
          ↑
        current
```

After:

``` text
10 → 20 → 30 → null
```

## Java-Style Pseudocode

``` text
BEGIN DeleteFromEnd

    METHOD deleteFromEnd()

        IF head == null THEN

            DISPLAY "List is empty"

            RETURN

        END IF


        IF head.next == null THEN

            head = null

            RETURN

        END IF


        current = head

        WHILE current.next.next != null

            current = current.next

        END WHILE


        current.next = null

    END METHOD

END DeleteFromEnd
```

## Time Complexity

``` text
O(n)
```

because we need to find the second-last node.

------------------------------------------------------------------------

# 23. Operation 11 --- Delete from a Specific Position

Suppose:

``` text
Position:  0    1    2    3

           10 → 20 → 30 → 40 → null
```

We want to delete position `2`.

The node to delete is:

``` text
30
```

We first reach the node before it:

``` text
20
```

Before:

``` text
10 → 20 → 30 → 40
     ↑    ↑
 previous node
```

We want:

``` text
20 → 40
```

So we change:

``` text
previous.next = previous.next.next
```

Result:

``` text
10 → 20 → 40 → null
```

## Java-Style Pseudocode

``` text
BEGIN DeleteAtPosition

    METHOD deleteAtPosition(position)

        IF position < 0 THEN

            DISPLAY "Invalid position"

            RETURN

        END IF


        IF head == null THEN

            DISPLAY "List is empty"

            RETURN

        END IF


        IF position == 0 THEN

            head = head.next

            RETURN

        END IF


        current = head

        FOR i FROM 0 TO position - 2

            IF current == null OR current.next == null THEN

                DISPLAY "Invalid position"

                RETURN

            END IF

            current = current.next

        END FOR


        IF current.next == null THEN

            DISPLAY "Invalid position"

            RETURN

        END IF


        current.next = current.next.next

    END METHOD

END DeleteAtPosition
```

## Time Complexity

``` text
O(n)
```

------------------------------------------------------------------------

# 24. The Most Important Deletion Idea

When deleting a node from the middle, remember:

``` text
previous → nodeToDelete → next
```

We want:

``` text
previous → next
```

So:

``` text
previous.next = nodeToDelete.next
```

Or directly:

``` text
previous.next = previous.next.next
```

This is one of the most important Linked List concepts.

------------------------------------------------------------------------

# 25. Operation 12 --- Find the Length

Suppose:

``` text
10 → 20 → 30 → 40 → null
```

There are:

``` text
4 nodes
```

We can count them while traversing.

Start:

``` text
count = 0
current = head
```

Every time we visit a node:

``` text
count = count + 1
```

## Java-Style Pseudocode

``` text
BEGIN FindLength

    METHOD length()

        count = 0

        current = head

        WHILE current != null

            count = count + 1

            current = current.next

        END WHILE

        RETURN count

    END METHOD

END FindLength
```

## Time Complexity

``` text
O(n)
```

If the Linked List class maintains a separate `size` variable, length
can instead be `O(1)`.

------------------------------------------------------------------------

# 26. Operation 13 --- Reverse the Linked List

Reversing is one of the most important Linked List interview problems.

Suppose:

``` text
10 → 20 → 30 → 40 → null
```

We want:

``` text
40 → 30 → 20 → 10 → null
```

This requires changing the direction of every `next` reference.

------------------------------------------------------------------------

# 27. Understanding Reverse with Three References

The standard iterative solution uses:

``` text
previous
current
next
```

Initially:

``` text
previous = null
current = head
```

For:

``` text
10 → 20 → 30 → 40 → null
```

we have:

``` text
previous = null

current
   ↓
  10 → 20 → 30 → 40 → null
```

------------------------------------------------------------------------

# 28. Reverse Step 1

We must save the next node before changing the link.

``` text
next = current.next
```

Now:

``` text
previous = null

current
   ↓
  10 ─────→ 20 → 30 → 40 → null
             ↑
            next
```

Then reverse the current link:

``` text
current.next = previous
```

Now:

``` text
10 → null
```

Then move:

``` text
previous = current
current = next
```

So:

``` text
previous
   ↓
  10 → null

current
   ↓
  20 → 30 → 40 → null
```

------------------------------------------------------------------------

# 29. Reverse Step 2

Again:

``` text
next = current.next
```

So:

``` text
next
 ↓
30 → 40 → null
```

Reverse:

``` text
current.next = previous
```

Now:

``` text
20 → 10 → null
```

Move:

``` text
previous = current
current = next
```

Now:

``` text
previous
   ↓
20 → 10 → null

current
   ↓
30 → 40 → null
```

------------------------------------------------------------------------

# 30. Continue Reversing

Repeat the same process.

Eventually:

``` text
previous
   ↓
40 → 30 → 20 → 10 → null

current
   ↓
null
```

Now:

``` text
head = previous
```

Final:

``` text
head
 ↓
40 → 30 → 20 → 10 → null
```

------------------------------------------------------------------------

# 31. Java-Style Pseudocode for Reverse

``` text
BEGIN ReverseLinkedList

    METHOD reverse()

        previous = null

        current = head

        WHILE current != null

            next = current.next

            current.next = previous

            previous = current

            current = next

        END WHILE

        head = previous

    END METHOD

END ReverseLinkedList
```

## The Three Most Important Statements

Remember:

``` text
next = current.next

current.next = previous

previous = current
current = next
```

A useful mental model is:

``` text
SAVE → REVERSE → MOVE
```

------------------------------------------------------------------------

# 32. Why Do We Need `next`?

This is a very common beginner question.

Suppose:

``` text
10 → 20 → 30
```

If we immediately do:

``` text
10.next = null
```

we have lost the link to `20`.

So before changing the link, we save it:

``` text
next = current.next
```

Therefore:

``` text
SAVE the next node
↓
CHANGE the link
↓
MOVE forward
```

That is why `next` is necessary.

------------------------------------------------------------------------

# 33. Operation 14 --- Find the Middle Node

Finding the middle node is a very useful Linked List technique.

Suppose:

``` text
10 → 20 → 30 → 40 → 50 → null
```

The middle is:

``` text
30
```

A common approach uses two references:

``` text
slow
fast
```

The `slow` reference moves one node at a time.

The `fast` reference moves two nodes at a time.

------------------------------------------------------------------------

# 34. Slow and Fast Pointer Technique

Initially:

``` text
slow = head
fast = head
```

For:

``` text
10 → 20 → 30 → 40 → 50 → null
```

both start at `10`.

Then:

``` text
slow → 20
fast → 30
```

Next:

``` text
slow → 30
fast → 50
```

Next:

``` text
slow → 40
fast → null
```

Depending on the exact loop condition, we can return the desired middle
node.

For an odd-sized list, this approach naturally identifies the middle.

## Java-Style Pseudocode

``` text
BEGIN FindMiddle

    METHOD findMiddle()

        IF head == null THEN

            RETURN null

        END IF

        slow = head

        fast = head


        WHILE fast != null AND fast.next != null

            slow = slow.next

            fast = fast.next.next

        END WHILE


        RETURN slow

    END METHOD

END FindMiddle
```

## Time Complexity

``` text
O(n)
```

## Space Complexity

``` text
O(1)
```

------------------------------------------------------------------------

# 35. Operation 15 --- Delete by Value

Sometimes we don't know the position.

Suppose:

``` text
10 → 20 → 30 → 40 → null
```

We want to delete:

``` text
30
```

We search for the node containing `30`.

We also need to remember the previous node.

``` text
previous → current
```

When:

``` text
current.data == target
```

we change:

``` text
previous.next = current.next
```

Result:

``` text
10 → 20 → 40 → null
```

## Java-Style Pseudocode

``` text
BEGIN DeleteByValue

    METHOD deleteByValue(target)

        IF head == null THEN

            DISPLAY "List is empty"

            RETURN

        END IF


        IF head.data == target THEN

            head = head.next

            RETURN

        END IF


        previous = head

        current = head.next


        WHILE current != null

            IF current.data == target THEN

                previous.next = current.next

                RETURN

            END IF

            previous = current

            current = current.next

        END WHILE


        DISPLAY "Value not found"

    END METHOD

END DeleteByValue
```

## Time Complexity

``` text
O(n)
```

------------------------------------------------------------------------

# 36. Operation 16 --- Find the Position of a Value

Suppose:

``` text
10 → 20 → 30 → 40 → null
```

We want to find the position of `30`.

Positions:

``` text
10 → 20 → 30 → 40
0    1    2    3
```

So the answer is:

``` text
2
```

## Java-Style Pseudocode

``` text
BEGIN FindPosition

    METHOD findPosition(target)

        current = head

        position = 0


        WHILE current != null

            IF current.data == target THEN

                RETURN position

            END IF

            current = current.next

            position = position + 1

        END WHILE


        RETURN -1

    END METHOD

END FindPosition
```

Returning `-1` means:

``` text
Value not found
```

------------------------------------------------------------------------

# 37. Operation 17 --- Clear the Entire Linked List

Suppose:

``` text
head
 ↓
10 → 20 → 30 → 40 → null
```

To make the list empty, we can set:

``` text
head = null
```

Now:

``` text
head
 ↓
null
```

The nodes are no longer reachable through the Linked List.

## Java-Style Pseudocode

``` text
BEGIN ClearList

    METHOD clear()

        head = null

    END METHOD

END ClearList
```

## Time Complexity

For a basic reference-based implementation:

``` text
O(1)
```

because we only change `head`.

In languages with manual memory management, explicit node cleanup may
require additional work.

------------------------------------------------------------------------

# 38. Operation 18 --- Get the First Element

The first element is the node pointed to by `head`.

Suppose:

``` text
head
 ↓
10 → 20 → 30 → null
```

Then:

``` text
head.data = 10
```

## Java-Style Pseudocode

``` text
BEGIN GetFirst

    METHOD getFirst()

        IF head == null THEN

            DISPLAY "List is empty"

            RETURN null

        END IF

        RETURN head.data

    END METHOD

END GetFirst
```

## Time Complexity

``` text
O(1)
```

------------------------------------------------------------------------

# 39. Operation 19 --- Get the Last Element

To get the last element, we need to traverse until:

``` text
current.next == null
```

Suppose:

``` text
10 → 20 → 30 → 40 → null
```

We stop at:

``` text
40
```

## Java-Style Pseudocode

``` text
BEGIN GetLast

    METHOD getLast()

        IF head == null THEN

            DISPLAY "List is empty"

            RETURN null

        END IF


        current = head

        WHILE current.next != null

            current = current.next

        END WHILE


        RETURN current.data

    END METHOD

END GetLast
```

## Time Complexity

``` text
O(n)
```

------------------------------------------------------------------------

# 40. Operation 20 --- Count Occurrences of a Value

Suppose:

``` text
10 → 20 → 10 → 30 → 10 → null
```

How many times does `10` appear?

Answer:

``` text
3
```

We can traverse the list and maintain a counter.

## Java-Style Pseudocode

``` text
BEGIN CountOccurrences

    METHOD countOccurrences(target)

        count = 0

        current = head


        WHILE current != null

            IF current.data == target THEN

                count = count + 1

            END IF

            current = current.next

        END WHILE


        RETURN count

    END METHOD

END CountOccurrences
```

## Time Complexity

``` text
O(n)
```

------------------------------------------------------------------------

# 41. Operation 21 --- Find the Maximum Value

Suppose:

``` text
10 → 50 → 20 → 40 → 30 → null
```

The maximum is:

``` text
50
```

We can keep a variable:

``` text
maximum
```

Start with the first node.

Then compare every other node.

## Java-Style Pseudocode

``` text
BEGIN FindMaximum

    METHOD findMaximum()

        IF head == null THEN

            DISPLAY "List is empty"

            RETURN null

        END IF


        maximum = head.data

        current = head.next


        WHILE current != null

            IF current.data > maximum THEN

                maximum = current.data

            END IF

            current = current.next

        END WHILE


        RETURN maximum

    END METHOD

END FindMaximum
```

## Time Complexity

``` text
O(n)
```

------------------------------------------------------------------------

# 42. Operation 22 --- Find the Minimum Value

This is similar to finding the maximum.

Suppose:

``` text
10 → 50 → 20 → 40 → 30 → null
```

The minimum is:

``` text
10
```

## Java-Style Pseudocode

``` text
BEGIN FindMinimum

    METHOD findMinimum()

        IF head == null THEN

            DISPLAY "List is empty"

            RETURN null

        END IF


        minimum = head.data

        current = head.next


        WHILE current != null

            IF current.data < minimum THEN

                minimum = current.data

            END IF

            current = current.next

        END WHILE


        RETURN minimum

    END METHOD

END FindMinimum
```

## Time Complexity

``` text
O(n)
```

------------------------------------------------------------------------

# 43. Operation 23 --- Check Whether a Value Exists

This is essentially the same idea as search.

Suppose:

``` text
10 → 20 → 30 → null
```

Check:

``` text
Does 20 exist?
```

Yes.

## Java-Style Pseudocode

``` text
BEGIN Contains

    METHOD contains(target)

        current = head

        WHILE current != null

            IF current.data == target THEN

                RETURN true

            END IF

            current = current.next

        END WHILE

        RETURN false

    END METHOD

END Contains
```

------------------------------------------------------------------------

# 44. Complete List of Basic Operations

A beginner should know these operations:

  Operation             Purpose                         Typical Time
  --------------------- ----------------------------- --------------
  Create node           Create a new node                       O(1)
  Is Empty              Check whether list is empty             O(1)
  Insert at beginning   Add node at front                       O(1)
  Insert at end         Add node at end                         O(n)
  Insert at position    Add node at a position                  O(n)
  Traverse              Visit all nodes                         O(n)
  Search                Find a value                            O(n)
  Get by position       Get value at position                   O(n)
  Update                Change a value                          O(n)
  Delete beginning      Remove first node                       O(1)
  Delete end            Remove last node                        O(n)
  Delete by position    Remove node at position                 O(n)
  Delete by value       Remove matching node                    O(n)
  Length                Count nodes                             O(n)
  Reverse               Reverse links                           O(n)
  Find middle           Find middle node                        O(n)
  Find position         Find position of value                  O(n)
  Clear                 Empty the list                          O(1)
  Get first             Get first value                         O(1)
  Get last              Get last value                          O(n)
  Count occurrences     Count matching values                   O(n)
  Find maximum          Find largest value                      O(n)
  Find minimum          Find smallest value                     O(n)
  Contains              Check whether value exists              O(n)

------------------------------------------------------------------------

# 45. Why Is Insertion at the Beginning O(1)?

Consider:

``` text
10 → 20 → 30 → 40 → null
```

To insert `5`:

``` text
newNode.next = head
head = newNode
```

Only two references change.

We don't care how many nodes exist.

Even if the list contains:

``` text
1,000,000 nodes
```

we still only perform a constant number of operations.

Therefore:

``` text
O(1)
```

------------------------------------------------------------------------

# 46. Why Is Searching O(n)?

Suppose:

``` text
10 → 20 → 30 → 40 → 50
```

If we search for `50`, we have to check:

``` text
10
20
30
40
50
```

We may have to visit every node.

Therefore:

``` text
O(n)
```

------------------------------------------------------------------------

# 47. Why Can't We Do `list[3]`?

In an array:

``` text
array[3]
```

can directly access index `3`.

In a Singly Linked List, there is no direct index-based access.

We have:

``` text
head
 ↓
10 → 20 → 30 → 40
```

To reach `40`, we must follow:

``` text
head
 ↓
10
 ↓
20
 ↓
30
 ↓
40
```

Therefore, accessing an arbitrary position is:

``` text
O(n)
```

------------------------------------------------------------------------

# 48. Linked List Memory Model

A useful beginner mental model is:

``` text
head
 ↓
+------+------+
|  10  |  •───┼──────┐
+------+------+      |
                      ↓
                +------+------+
                |  20  |  •───┼──────┐
                +------+------+      |
                                      ↓
                                +------+------+
                                |  30  | null |
                                +------+------+
```

The nodes don't need to be physically next to each other.

The references connect them logically.

Think:

``` text
Node → Node → Node
```

rather than:

``` text
Array cell → Array cell → Array cell
```

------------------------------------------------------------------------

# 49. The Most Important Linked List Pointer

For beginners, this line is extremely important:

``` text
current = current.next
```

It means:

> Move from the current node to the next node.

For example:

``` text
current
   ↓
10 → 20 → 30 → null
```

After:

``` text
current = current.next
```

we have:

``` text
10 → 20 → 30 → null
      ↑
    current
```

This is the basic movement operation in a Singly Linked List.

------------------------------------------------------------------------

# 50. The Three Most Important Linked List Patterns

Most beginner Linked List problems are based on a few patterns.

## Pattern 1 --- Traverse

``` text
current = head

WHILE current != null

    DO something

    current = current.next

END WHILE
```

Remember:

``` text
VISIT → MOVE → REPEAT
```

------------------------------------------------------------------------

## Pattern 2 --- Insert

The important operation is changing links.

For insertion:

``` text
previous → next
```

becomes:

``` text
previous → newNode → next
```

The two important statements are:

``` text
newNode.next = previous.next
previous.next = newNode
```

------------------------------------------------------------------------

## Pattern 3 --- Delete

Before:

``` text
previous → nodeToDelete → next
```

After:

``` text
previous → next
```

The important statement is:

``` text
previous.next = previous.next.next
```

------------------------------------------------------------------------

# 51. Complete Java-Style Pseudocode Structure

Here is a clean structure you can use when teaching the complete Linked
List.

``` text
BEGIN SinglyLinkedList

    CLASS Node

        INTEGER data
        Node next

        CONSTRUCTOR Node(value)

            data = value
            next = null

        END CONSTRUCTOR

    END CLASS


    CLASS LinkedList

        Node head


        METHOD isEmpty()

            RETURN head == null

        END METHOD


        METHOD insertAtBeginning(value)

            newNode = new Node(value)

            newNode.next = head

            head = newNode

        END METHOD


        METHOD insertAtEnd(value)

            newNode = new Node(value)

            IF head == null THEN

                head = newNode

                RETURN

            END IF

            current = head

            WHILE current.next != null

                current = current.next

            END WHILE

            current.next = newNode

        END METHOD


        METHOD display()

            current = head

            WHILE current != null

                DISPLAY current.data

                current = current.next

            END WHILE

        END METHOD


        METHOD search(target)

            current = head

            WHILE current != null

                IF current.data == target THEN

                    RETURN true

                END IF

                current = current.next

            END WHILE

            RETURN false

        END METHOD


        METHOD deleteFromBeginning()

            IF head == null THEN

                RETURN

            END IF

            head = head.next

        END METHOD


        METHOD deleteFromEnd()

            IF head == null THEN

                RETURN

            END IF

            IF head.next == null THEN

                head = null

                RETURN

            END IF

            current = head

            WHILE current.next.next != null

                current = current.next

            END WHILE

            current.next = null

        END METHOD


        METHOD length()

            count = 0

            current = head

            WHILE current != null

                count = count + 1

                current = current.next

            END WHILE

            RETURN count

        END METHOD


        METHOD reverse()

            previous = null

            current = head

            WHILE current != null

                next = current.next

                current.next = previous

                previous = current

                current = next

            END WHILE

            head = previous

        END METHOD

    END CLASS

END SinglyLinkedList
```

------------------------------------------------------------------------

# 52. Building a Linked List Step by Step

Let's build this list:

``` text
10 → 20 → 30 → null
```

## Step 1 --- Start Empty

``` text
head → null
```

## Step 2 --- Insert 10

``` text
head
 ↓
10 → null
```

## Step 3 --- Insert 20

``` text
head
 ↓
10 → 20 → null
```

## Step 4 --- Insert 30

``` text
head
 ↓
10 → 20 → 30 → null
```

This is how a Linked List grows.

------------------------------------------------------------------------

# 53. Building the List Using Insert at Beginning

Suppose we perform:

``` text
insertAtBeginning(10)
insertAtBeginning(20)
insertAtBeginning(30)
```

After inserting `10`:

``` text
10 → null
```

After inserting `20`:

``` text
20 → 10 → null
```

After inserting `30`:

``` text
30 → 20 → 10 → null
```

Notice the order is reversed.

This happens because every new node becomes the new `head`.

------------------------------------------------------------------------

# 54. Building the List Using Insert at End

Now perform:

``` text
insertAtEnd(10)
insertAtEnd(20)
insertAtEnd(30)
```

After `10`:

``` text
10 → null
```

After `20`:

``` text
10 → 20 → null
```

After `30`:

``` text
10 → 20 → 30 → null
```

This preserves insertion order.

------------------------------------------------------------------------

# 55. Dry Run --- Insert at Beginning

Suppose:

``` text
head
 ↓
20 → 30 → 40 → null
```

We call:

``` text
insertAtBeginning(10)
```

### Step 1

Create:

``` text
newNode = 10
```

``` text
10 → null
```

### Step 2

``` text
newNode.next = head
```

Now:

``` text
10 → 20 → 30 → 40 → null
```

### Step 3

``` text
head = newNode
```

Final:

``` text
head
 ↓
10 → 20 → 30 → 40 → null
```

------------------------------------------------------------------------

# 56. Dry Run --- Delete from Beginning

Before:

``` text
head
 ↓
10 → 20 → 30 → null
```

Execute:

``` text
head = head.next
```

`head.next` is `20`.

Therefore:

``` text
head
 ↓
20 → 30 → null
```

The `10` node is no longer part of the list.

------------------------------------------------------------------------

# 57. Dry Run --- Delete from the Middle

Before:

``` text
10 → 20 → 30 → 40 → null
```

Delete `30`.

We find:

``` text
previous = 20
current = 30
```

Then:

``` text
previous.next = current.next
```

Since:

``` text
current.next = 40
```

we get:

``` text
20 → 40
```

Final:

``` text
10 → 20 → 40 → null
```

------------------------------------------------------------------------

# 58. Dry Run --- Reverse

Start:

``` text
10 → 20 → 30 → null
```

Initial:

``` text
previous = null
current = 10
```

### Step 1

Save next:

``` text
next = 20
```

Reverse:

``` text
10 → null
```

Move:

``` text
previous = 10
current = 20
```

### Step 2

Save:

``` text
next = 30
```

Reverse:

``` text
20 → 10 → null
```

Move:

``` text
previous = 20
current = 30
```

### Step 3

Save:

``` text
next = null
```

Reverse:

``` text
30 → 20 → 10 → null
```

Move:

``` text
previous = 30
current = null
```

Finally:

``` text
head = previous
```

Result:

``` text
head
 ↓
30 → 20 → 10 → null
```

------------------------------------------------------------------------

# 59. Common Beginner Mistakes

## Mistake 1 --- Forgetting to Update `head`

When inserting at the beginning:

Wrong:

``` text
newNode.next = head
```

and stopping there.

We also need:

``` text
head = newNode
```

------------------------------------------------------------------------

## Mistake 2 --- Losing the Remaining List

While reversing, don't change:

``` text
current.next
```

before saving:

``` text
next = current.next
```

Otherwise, you can lose access to the remaining nodes.

------------------------------------------------------------------------

## Mistake 3 --- Using `current.next` When `current` Is Null

Always be careful with:

``` text
current.next
```

If:

``` text
current == null
```

then accessing:

``` text
current.next
```

is invalid.

This is why conditions often look like:

``` text
WHILE current != null
```

or:

``` text
WHILE fast != null AND fast.next != null
```

------------------------------------------------------------------------

## Mistake 4 --- Confusing Node and Data

These are different:

``` text
current
```

means:

> the current Node reference

while:

``` text
current.data
```

means:

> the value stored inside the current node

And:

``` text
current.next
```

means:

> the reference to the next node

Remember:

``` text
current       → Node
current.data  → Value
current.next  → Next Node
```

------------------------------------------------------------------------

# 60. Linked List Mental Model

If you remember only one diagram, remember this:

``` text
                    head
                     ↓
              +------+------+
              |             |
              |    Node     |
              |             |
              +------+------+
                     |
                     ↓
              +------+------+
              |             |
              |    Node     |
              |             |
              +------+------+
                     |
                     ↓
              +------+------+
              |             |
              |    Node     |
              |             |
              +------+------+
                     |
                     ↓
                    null
```

Or simply:

``` text
head → Node → Node → Node → null
```

Every node contains:

``` text
data + next
```

------------------------------------------------------------------------

# 61. The Four Most Important References

When learning Linked Lists, understand these four things extremely well:

``` text
head
```

Points to the first node.

``` text
current
```

Used to traverse the list.

``` text
next
```

Stores the next node temporarily.

``` text
previous
```

Used when we need to connect the previous node to another node.

A lot of Linked List problems are just different combinations of these
references.

------------------------------------------------------------------------

# 62. Complexity Summary

For a basic Singly Linked List without a `tail` pointer:

  Operation               Time Complexity
  --------------------- -----------------
  Create node                        O(1)
  Is empty                           O(1)
  Insert at beginning                O(1)
  Insert at end                      O(n)
  Insert at position                 O(n)
  Get first                          O(1)
  Get last                           O(n)
  Get at position                    O(n)
  Search                             O(n)
  Update at position                 O(n)
  Delete beginning                   O(1)
  Delete end                         O(n)
  Delete at position                 O(n)
  Delete by value                    O(n)
  Traverse                           O(n)
  Length                             O(n)
  Reverse                            O(n)
  Find middle                        O(n)
  Find minimum                       O(n)
  Find maximum                       O(n)
  Count occurrences                  O(n)
  Clear                              O(1)

Space complexity for storing `n` nodes is:

``` text
O(n)
```

because every element requires a node.

Each node also needs extra memory for its `next` reference.

------------------------------------------------------------------------

# 63. What Changes If We Add a `tail` Reference?

A basic Linked List might have only:

``` text
head
```

We can also maintain:

``` text
tail
```

Then:

``` text
head                         tail
 ↓                             ↓
10 → 20 → 30 → 40 → null
```

Now we immediately know where the last node is.

Therefore, insertion at the end can become:

``` text
O(1)
```

instead of:

``` text
O(n)
```

The idea is:

``` text
tail.next = newNode
tail = newNode
```

## Java-Style Pseudocode

``` text
BEGIN InsertAtEndWithTail

    METHOD insertAtEnd(value)

        newNode = new Node(value)

        IF head == null THEN

            head = newNode

            tail = newNode

            RETURN

        END IF


        tail.next = newNode

        tail = newNode

    END METHOD

END InsertAtEndWithTail
```

This is an important optimization.

------------------------------------------------------------------------

# 64. Linked List with Both `head` and `tail`

A more complete representation is:

``` text
head                         tail
 ↓                             ↓
10 → 20 → 30 → 40 → null
```

The class can conceptually contain:

``` text
CLASS LinkedList

    Node head
    Node tail

END CLASS
```

When the list is empty:

``` text
head = null
tail = null
```

When there is one node:

``` text
head
 ↓
10
 ↑
tail
```

Both references point to the same node.

------------------------------------------------------------------------

# 65. Important Edge Cases

When implementing Linked Lists, always think about these cases.

## Case 1 --- Empty List

``` text
head → null
```

## Case 2 --- One Node

``` text
head
 ↓
10 → null
```

## Case 3 --- Two Nodes

``` text
10 → 20 → null
```

## Case 4 --- Insert at Position 0

This is equivalent to:

``` text
insertAtBeginning()
```

## Case 5 --- Delete Position 0

This is equivalent to:

``` text
deleteFromBeginning()
```

## Case 6 --- Delete the Last Node

If there is only one node:

``` text
10 → null
```

deleting it must result in:

``` text
head → null
```

If using a `tail`, then:

``` text
tail → null
```

too.

------------------------------------------------------------------------

# 66. Complete Beginner Learning Sequence

When teaching a beginner, a good order is:

``` text
1. What is a Node?
        ↓
2. What is `next`?
        ↓
3. What is `head`?
        ↓
4. Create a Node
        ↓
5. Create an empty Linked List
        ↓
6. Insert at beginning
        ↓
7. Traverse
        ↓
8. Insert at end
        ↓
9. Search
        ↓
10. Get by position
        ↓
11. Update
        ↓
12. Delete from beginning
        ↓
13. Delete from end
        ↓
14. Delete from position
        ↓
15. Delete by value
        ↓
16. Length
        ↓
17. Reverse
        ↓
18. Find middle
        ↓
19. Edge cases
        ↓
20. Time complexity
```

This order gradually introduces the pointer/reference concepts without
overwhelming the beginner.

------------------------------------------------------------------------

# 67. Beginner Practice Questions

After learning the operations above, practice these problems.

## Easy

1.  Create a Linked List with 5 nodes.
2.  Print all elements.
3.  Find the length.
4.  Search for a value.
5.  Insert at the beginning.
6.  Insert at the end.
7.  Delete the first node.
8.  Delete the last node.
9.  Find the maximum value.
10. Find the minimum value.

## Medium

11. Insert at a specific position.
12. Delete from a specific position.
13. Delete by value.
14. Find the position of a value.
15. Reverse the Linked List.
16. Find the middle node.
17. Count occurrences of a value.
18. Find the nth node.
19. Find the nth node from the end.
20. Remove duplicates from a sorted Linked List.

## Interview-Oriented Next Steps

After becoming comfortable with the basics, learn:

``` text
1. Reverse Linked List
2. Find Middle
3. Detect Cycle
4. Find Cycle Starting Point
5. Merge Two Sorted Lists
6. Remove Nth Node From End
7. Palindrome Linked List
8. Intersection of Two Linked Lists
9. Reverse Nodes in Groups
10. Sort a Linked List
```

These problems build directly on the fundamental pointer techniques
learned here.

------------------------------------------------------------------------

# 68. Final Mental Model

A Singly Linked List is simply:

``` text
head
 ↓
Node → Node → Node → Node → null
```

Each node contains:

``` text
data
next
```

The most important operations are:

``` text
INSERT
   ↓
Create node
Connect references
Update head/previous node


DELETE
   ↓
Find node
Skip it by changing a reference


TRAVERSE
   ↓
current = head
while current != null
    visit current
    current = current.next


REVERSE
   ↓
SAVE → REVERSE → MOVE
```

The most important lines to remember are:

``` text
current = current.next
```

for moving through the list,

``` text
newNode.next = head
head = newNode
```

for inserting at the beginning,

``` text
previous.next = current.next
```

for deleting a node,

and:

``` text
next = current.next
current.next = previous
previous = current
current = next
```

for reversing the list.

------------------------------------------------------------------------

# 69. One-Sentence Definition

> **A Singly Linked List is a linear data structure made of nodes, where
> each node stores data and a reference to the next node, with `head`
> pointing to the first node and the last node pointing to `null`.**

The easiest mental model is:

``` text
HEAD
 ↓
[DATA | NEXT] → [DATA | NEXT] → [DATA | NEXT] → null
```

Once you understand:

``` text
head
current
next
previous
```

you have the foundation needed to solve most beginner and intermediate
Singly Linked List problems.
