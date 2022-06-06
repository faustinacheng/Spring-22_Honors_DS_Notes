# COMS W3137 - Honors Data Structures Midterm Review - Spring 22

**Notes:**

- BRING SCRATCH PAPER
- SEND EMAIL TO BAUER IF TAKING REMOTE
- Allowed calculator
- Final grade curved rather than exam



- Multiple choice + short answer questions + two programming questions typed into textbox (java code given and write one method or copy/paste/modify slightly) RECURSIVE BINARY TREE TRAVERSAL + MIGHT BE ABOUT LINKED LIST (no scala programming, only reading scala code)
- More interested in algorithms rather than syntax for programming questions
- Also proof by structural induction
- Questions about runtime analysis
- Around 8 or 9 Questions in 60 Minutes



- Review THEORY + programming homework 1 and 2, know how to do questions
- No questions about amortized analysis



Topics marked with * will not be tested on the midterm.

**Weiss Textbook Chapters**

 • Chapter 1 (entirely)
 • Chapter 2 (entirely)
 • Chapter 3 (entirely)
 • Chapter 4.1, 4.2, 4.3, 4.4, and 4.6 (and 4.7∗)

NB: Only material covered in class will be tested



**Material from Outside the Textbook**

- Towers of Hanoi.
- Amortized Analysis (the Weiss textbook discusses Amortized Analysis in chapter 11, but using data structures we did not yet discuss in class. Instead, please refer to the chapter from the Cormen, Leiserson, Rivest, and Stein Algorithms textbook, which you can find as a PDF on Courseworks).
- Immutable data structures.
- Scala (see below, please refer to the recitation nodes).



**General Concepts**

 • Abstract Data Types vs. Data Structures.

Foundational to knowledge

 • Recursion.

Also know how it’s implemented in JVM (method call stacks and stack frames)

 • Basic proofs by structural induction.



**Java Concepts**

 • Basic Java OOP: Classes / Methods / Fields. Visibility modifiers.

 • Generics.
 • Inner classes (static vs. non-static).

Non-static inner class can access instance variables of surrounding class

​	ie. Iterator class needs access to data surrounding it

Static inner class (Nested class) cannot access those variables

​	ie. Node in BST class

 • Interfaces.

 • Iterator/ Iterable.

Iterable interface requires that there is a method called Iterator that returns an instance of type iterator that is typically an inner class implemented whatever data structure it is

 • Comparable.

Gives objects a way to be compared against objects of the same type; gives them a natural order



**Scala Concepts**

There will not be a Scala programming problem on the midterm, but should be familiar

- REPL vs. compiled scala code.
- var vs. val.

val can never be modified once defined; var can be changed

- Everything is an expression.

There are no statements. Everything you type in including a print statement will evaluate to some value (ie. Unit() ).

- Basic functional programming: First class and higher-order functions, function literals (vs. methods defined with def).

First class defined using functional literals (that uses double right arrow notation with variable to the left and some expression to the right that is evaluated)

Higher order functions are ones which either take in a first class function as a parameter or returns a first class function as a return value

Anything with def in front is technically a method

- Basic OOP in Scala (classes, methods, fields/instance variables).

Basically same in Java, but should be familiar in differences of syntax

- Singleton object and Companion object

Object that has the same name as class

What would be static methods in Java probably will become a method of a companion object of a class in Scala

Can write apply method in companion object, can instantiate a new instance of the class without using new keyword.

- Case classes and pattern matching.

allows you to take a value and make a branching decision in your program based on the format of the value. Can be used to unpack information in a case class

- Multiple return values with tuples.

Many situations where you would want to return a pair of objects rather than one. Ie. in the immutable stack, methods like pop return both the popped item and the new stack

- Immutable lists in scala (and using them as stacks).

Know how :: works, what Nil means, prepending and appending

Know how it differs from linked lists in Java

- map, and folds.

Allow us to recursively traverse a list and do something to the list.

Map - Applying operation to each element in list and returning new list

Fold - Collapsing elements of list in some way to compute an aggregate value

- Banker’s queue.

- Binary tree implementation and tree traversals.

  ie. ExpressionTree in homework

   

**Analysis of Algorithms**

- Big-O notation for asymptotic running time: O(f(n)), Θ(f(n)), Ω(f(n)).

Know the difference, what they mean

Know formal definitions (no need to do proofs like in hw1)

- Typical growth functions for algorithms.

Linear time/logarithmic time/exponential time/2^n^ time

-  Worst case, best case, average case.

Know the distinction, be familiar with concepts

Typically when talking about runtime, we’re talking about worst case

Average case can come up ie. average height of a search tree

Best case runtime ie. in sorting algorithms is n log n

- Recursion (Towers of Hanoi, recursive Fibonacci implementation, Binary Search) and runtime behavior of recursive programs. Logarithms in the runtime. Tail recursion.

Recursion tree method (draw out tree structure and reason over how many leaf nodes there are)

Unrolling the recurrent relation (keep rewriting the recurrent relation) until base case reached. Argue about how often the unrolling is done.

No need to analyse formally like this in midterm but there might be a fragment of a recursive algorithm and need to know runtime (many times can see without doing proof)

- Skills: Compare growth of functions using big-O notation. Given an algorithm (written in Java or Scala), estimate the asymptotic run time (including nested loops and simple recursive calls).

- Basic understanding of amortized analysis (Aggregate method, Banker’s method, Physicists/Potential method). ∗

  

**Lists**

- List ADT, including typical List operations.

Adding to list at end/beginning, adding at index, setting at index, retrieving at index

- ArrayList:

  - –  Running time for insert, remove, get, contains at different positions in the list.
  - –  Increasing the array capacity when the array is full.
  - Better than linkedlist when need to access items at a particular index

- LinkedList:

  - –  Single vs. doubly linked list.
  - –  Running time for insert, remove, get, contains at different positions in the list.
  - –  Sentinel (beginMarker/head and endMarker/tail) nodes.

- Scala head::tail list

- Skills: Implement iterators. Implement additional list operations (such as reversal,

  but think of others, such as removing duplicates etc.). to the degree that you could implement an iterator on a linkedlist/arraylist

  Should know in linkedlist case the issue of setting next/prev references (can look at hw with flippairs/reverse list, might be a question about changing these references in some way)

- Lists in the Java Collections API ∗

  - Java API classes (java.util.collections) questions won’t be asked

  

**Stacks and Queues**

- Stack ADT and operations (push, pop, peek). LIFO - Last in first out
- Queue ADT and operations (enqueue, dequeue). FIFO - First in first out
- All operations should run in O(1)

Part of the appeal of using stack, limit yourself to these methods but get guarantee that each operation will be in constant time

- Stack implementation using List data structures, directly on an array, or using immutable lists.

If implementing a queue on an array, for the circular array, theres an issue where you enqueue/dequeue and emptying space at the beginning of the array which you recycle by having a wraparound of the index using the modulo operator.

Should also know how to implement stacks using immutable lists in Scala. Implementing queue using two stacks.

- Stack applications:
  - Symbol balancing, detecting palindromes.
  - Reordering sequences (in-order to post-order etc.).
  - Storing intermediate computations on a stack (evaluating post-order expressions).
  - Building expression trees.

- Method call stack, stack frames ∗, relation between stacks and recursion.

No need to know the exact structure of stack frames in JVM, just know how method call stack works and why you get stack overflow error when you have a runaway base case

- Tail recursion.

Last thing that happens in a function is a recursive call, no other computation afterwards.

In this case, there are some compilers that can turn this code into a loop (doesn’t use method call stack at all).

- Queue implementation using Linked List.

- Queue implementation using a Circular Array.

- Banker’s queue.

- Stacks and queues in the Java Collections API (java.util.LinkedList supports all

  stack operations) ∗

Just remember in the future in java, don’t use Stack, but use LinkedList if stack needed

- Skills: Implement stacks and queues. Use stacks and queues in applications.

  No need to know in exam how to implement stack with array

  

**Trees**

- Recursive definition of a tree.

Children are themselves trees (subtrees)

- Tree terminology (parent, children, root, leafs, path, depth, height)

Depth: property of the node, length of path from root to particular node

Height: property of the tree, maximum depth of the tree, max distance from any leaf node to the root

- Different tree implementations (one instance variable per child, ==list of children, siblings as linked list)==

Binary trees most important. Familiar with others

Structure where we had a first-child, next sibling type tree?

- Binary trees:

  - –  Full / complete/ perfect binary trees.
  - –  Tree traversals: in-order, pre-order, post-order.
  - –  Expression trees - pre-fix, post-fix (a.k.a. reverse Polish notation), and in-fix notation.
  - –  Constructing an expression tree using a stack.
  - –  Relation between number of nodes and height of a binary tree.

  In particular, in complete binary tree

  - –  Structural induction over binary trees (two versions: ==induction over height (growing tree up, adding root node), induction over number of nodes(cutting off 2 leaf nodes)==.

- Skills: Perform tree traversals on paper (ie. given pre and infix of tree, give postfix representation/draw tree). **Implement different tree traversals using recursion**. Use these traversals to implement operations on trees (for example, computing tree properties, such as height, summing together nodes in tree). Convert between in-fix, post-fix, pre- fix notation using a tree. Structural induction proofs for binary tree properties **(especially full binary tree theorem)**.

  

**Binary Search Trees**

- Map ADT.

put and get method, key/value, keys are unique, use key to get value

- BST property.

No duplicates in tree, left subtree is less than root, right subtree is more than root

- BST operations: contains, findMin, findMax, insert, remove (three cases for remove).

Remove: removing leaf, removing node with one child (remove node and pull child out), remove node with two children (replace key on node with min val on right subtree or max val on left subtree, then delete moved target node)

- Runtime performance of these operations, depending on the height of the tree.

What is this runtime of this operation on a general binary tree (ie. runtime of contains on BST)? A. Linear O(n) (because general binary tree is not balanced)

Runtime on AVL tree = O(log n)

- Lazy deletion ∗
- Skills: Perform BST operations (contains, insert, delete) on paper.

Understand how it all works (recursively and together)



**AVL Trees**

- Balanced BSTs. AVL balancing property.

In balanced BST, make sure the height of tree is approx log n O(log n)

AVL balancing property : max difference of height of right and left subtree is 1

- Maintaining AVL balance property on insert:

  – Outside imbalance, single rotation. RR/LL

  – Inside imbalance, double rotation. ==RL/LR==

  – **Verifying that a tree is balanced**. Finding the location of an imbalance (**bottom-up**).

- Skills: Perform AVL rotations on paper, detect imbalances.

Imbalance happens before if you determine its RR/RL/etc .

Detect imbalance by determining height of subtree as you come out of recursion from inserting/deleting an element (max of left/right subtree + 1 for insertion??)

Don’t have to compute height of non-modified subtrees

At some point, you’ll reach a node where because of insertion/deletion there is an imbalance.

If right child is higher, then check the left and right child of that child to see if it’s RR or RL

- Can try to reconstruct references that have to change in rotations to practice



**B-Trees ∗**