27 Apr 2022

 # Algorithms and Problem Solving

<img src="images/image-20220503012400093.png" alt="image-20220503012400093" style="zoom:25%;" />

## Common Types of Algorithms

<img src="images/image-20220503012552948.png" alt="image-20220503012552948" style="zoom:25%;" />

## Greedy Algorithms

<img src="images/image-20220503012746143.png" alt="image-20220503012746143" style="zoom:25%;" />

 ### New Example of Greedy Algorithm: Huffman Coding

- Compression scheme for text data

- Usually text is stored as ASCII encoding

  <img src="images/image-20220503012840980.png" alt="image-20220503012840980" style="zoom:25%;" />

- Since some letters might be used more often, it would be more efficient to have a shorter code to represent these more frequent letters

- Example: A 5-character alphabet:

  <img src="images/image-20220503013018161.png" alt="image-20220503013018161" style="zoom:25%;" />

  - Note: 111 is not occupied

    <img src="images/image-20220503013414830.png" alt="image-20220503013414830" style="zoom:25%;" />

- Can encode these bits in a **Trie/Prefix Tree**

  <img src="images/image-20220503013612526.png" alt="image-20220503013612526" style="zoom:25%;" />

- Idea of **Huffman Coding** is that characters that occur frequently can be assigned higher in the prefix tree, resulting in a shorter code/storage space

  - Prefix “11” is not used for any other character than *nl*

  - Can move it higher to 11

    <img src="images/image-20220503013904901.png" alt="image-20220503013904901" style="zoom:25%;" />

    <img src="images/image-20220503013922951.png" alt="image-20220503013922951" style="zoom:25%;" />

    - ie. 000110 is ambiguous:

      Could be: <img src="images/image-20220503014008781.png" alt="image-20220503014008781" style="zoom:25%;" />, <img src="images/image-20220503014021996.png" alt="image-20220503014021996" style="zoom:25%;" />, etc

    - So characters are only allowed to appear in the leaf nodes

  ### Huffman Code

  <img src="images/image-20220503014143671.png" alt="image-20220503014143671" style="zoom:25%;" />

  <img src="images/image-20220503014303643.png" alt="image-20220503014303643" style="zoom:25%;" />

  - would correspond to s e a t nl
  - 146 bits vs 175 from previously when all codes where 5 bits



How do we implement this?

<img src="images/image-20220503014502195.png" alt="image-20220503014502195" style="zoom:25%;" />

Entering in the greedy algorithm:

<img src="images/image-20220503014533456.png" alt="image-20220503014533456" style="zoom:25%;" />

- s is at 0 position, nl is in 1 position

<img src="images/image-20220503014627096.png" alt="image-20220503014627096" style="zoom:25%;" />

<img src="images/image-20220503014650144.png" alt="image-20220503014650144" style="zoom:25%;" />

<img src="images/image-20220503014717095.png" alt="image-20220503014717095" style="zoom:25%;" />

<img src="images/image-20220503014731176.png" alt="image-20220503014731176" style="zoom:25%;" />

- Weight of T4 should be 25

Result:

<img src="images/image-20220503014746493.png" alt="image-20220503014746493" style="zoom:25%;" />

<img src="images/image-20220503014815405.png" alt="image-20220503014815405" style="zoom:25%;" />

- All trees in heap
- Deleting min takes log N
- N = number of characters = max elements that end up on heap
- Also a pre-processing step of computing the frequencies of characters



## Divide and Conquer Algorithms

<img src="images/image-20220503015200164.png" alt="image-20220503015200164" style="zoom:25%;" />

Examples:

<img src="images/image-20220503015242868.png" alt="image-20220503015242868" style="zoom:25%;" />

- efficient when subproblems have no overlap

### Merge Sort

<img src="images/image-20220503015400586.png" alt="image-20220503015400586" style="zoom:25%;" />

<img src="images/image-20220503015412193.png" alt="image-20220503015412193" style="zoom:25%;" />

<img src="images/image-20220503015423510.png" alt="image-20220503015423510" style="zoom:25%;" />

<img src="images/image-20220503015435184.png" alt="image-20220503015435184" style="zoom:25%;" />

<img src="images/image-20220503015446459.png" alt="image-20220503015446459" style="zoom:25%;" />

<img src="images/image-20220503015458860.png" alt="image-20220503015458860" style="zoom:25%;" />

#### Running Time

<img src="images/image-20220503015517804.png" alt="image-20220503015517804" style="zoom:25%;" />

Analysis for merge sort and quick sort with perfect pivot by unrolling the recursion:

<img src="images/image-20220503015616774.png" alt="image-20220503015616774" style="zoom:25%;" />

Because most of the runtimes of divide and conquer algorithms are similar, we have a standard formula for them:

**Master Theorem:**

<img src="images/image-20220503015806191.png" alt="image-20220503015806191" style="zoom:25%;" />

<img src="images/image-20220503015859547.png" alt="image-20220503015859547" style="zoom:25%;" />

- a = number of subproblems to solve
- b = how small the different subproblems are relative to overall n
- $\Theta$(N^k^) = time incurred to merge solutions back together

<img src="images/image-20220503020051099.png" alt="image-20220503020051099" style="zoom:25%;" />

*Example: Binary Search*

a = 1, b = 2, k = 0 <– merging solutions back together takes constant time

- Case 2: 1 = 2^0^
- Total runtime : O(N^0^ log N) = O(log N)

**ANALYSE TOWERS OF HANOI PROBLEM USING MASTER THEOREM**



## Dynamic Programming Algorithms

<img src="images/image-20220503020749309.png" alt="image-20220503020749309" style="zoom:25%;" />

- ie. solve from k = 1 up to N
- ie. Recursive doesn’t work efficiently for fibonacci because we are duplicating work



Example:

Broken Fibonacci:

<img src="images/image-20220503020918092.png" alt="image-20220503020918092" style="zoom:25%;" />

<img src="images/image-20220503020934259.png" alt="image-20220503020934259" style="zoom:25%;" />

Analysing the recursive fibonacci solutions:

<img src="images/image-20220503021016382.png" alt="image-20220503021016382" style="zoom:25%;" />

- Approx O(2^N^)

Dynamic Programming Fibonacci:

<img src="images/image-20220503021103787.png" alt="image-20220503021103787" style="zoom:35%;" />

- No recursion, computing the fibonacci numbers incrementally
- T(N) = O(N)



Example:

All-pairs shortest paths:

<img src="images/image-20220503021201977.png" alt="image-20220503021201977" style="zoom:25%;" />

- If graph is not sparse, T(N) > O(|V|^3^)
- **Floyd-Warshall** better if graph is dense



<img src="images/image-20220503021414955.png" alt="image-20220503021414955" style="zoom:25%;" />

- u now has to be on the shortest path from s to v

<img src="images/image-20220503021536480.png" alt="image-20220503021536480" style="zoom:25%;" />

- rows represent source vertex and columns represent target vertex

- looks a little like the adjacency matrix

<img src="images/image-20220503022307429.png" alt="image-20220503022307429" style="zoom:25%;" />

- In this case, d~k~[u] [v] gets updated from 7 to 5 since it’s cheaper to go from u to v via k

- Vertices are integers, and we visit them in ascending order of the integers
  - Arbritrary naming scheme



<img src="images/image-20220503022725099.png" alt="image-20220503022725099" style="zoom:50%;" />

- Dynamic programming because the table of d is not computed recursively, but is incrementally updated step by step as k increases



Runtime:

O(|V|^3^)



Example:

**Longest Increasing Subsequence** : Recursive Solution

<img src="images/image-20220503023038400.png" alt="image-20220503023038400" style="zoom:25%;" />

<img src="images/image-20220503023125408.png" alt="image-20220503023125408" style="zoom:25%;" />

<img src="images/image-20220503023159289.png" alt="image-20220503023159289" style="zoom:25%;" />

- Edges missing in diagram from two

<img src="images/image-20220503023526880.png" alt="image-20220503023526880" style="zoom:25%;" />

- Recursively compute the longest sub-sequence from index 0 to i - 1
- Longest sub-sequence from index 0 to 7 (value 7) for example, is the longest sub-sequence from index 0 - 6 that ends with a value less than 7 + 1 (value 7)

<img src="images/image-20220503023930191.png" alt="image-20220503023930191" style="zoom:25%;" />

- overlapping subsolutions

Dynamic Programming solution:

<img src="images/image-20220503024117798.png" alt="image-20220503024117798" style="zoom:25%;" />



<img src="images/image-20220503024538817.png" alt="image-20220503024538817" style="zoom:25%;" />

- Only gives length of increasing subsequence
- To keep track of the actual subsequence, can store a backpointer



Runtime: O(N^2^)



*Example:*

**Minimum Edit Distance:**

<img src="images/image-20220503024902471.png" alt="image-20220503024902471" style="zoom:25%;" />

<img src="images/image-20220503025254461.png" alt="image-20220503025254461" style="zoom:25%;" />



Edit distance as search:

<img src="images/image-20220503025337125.png" alt="image-20220503025337125" style="zoom:25%;" />

- Subs for SATURDAY is wrong; or could be replacing S with S



Dynamic Programming Algorithm for Edit Distance:

<img src="images/image-20220503025512999.png" alt="image-20220503025512999" style="zoom:25%;" />

- i = length of prefix in s, j = length of prefix in t
- Eventually, D(i, j) will give the minimum edit distance of both entire words

<img src="images/image-20220503025823048.png" alt="image-20220503025823048" style="zoom:25%;" />

- Filling up table diagonally from bottom left corner

Recursive definition:

<img src="images/image-20220503025926070.png" alt="image-20220503025926070" style="zoom:25%;" />

- if one word is empty the other has a prefix of i chars, the only way to get from the empty word to the other is with i insertions
- For D(i - 1, j) and D(i, j - 1), we do one insertion
- For D(i - 1, j - 1)
  - if s~i~ != s~j~, we replace one character
  - if s~i~ = s~j~, we don’t have to do anything since they’re identical



<img src="images/image-20220503030333046.png" alt="image-20220503030333046" style="zoom:25%;" />

- For SATURDAY, - to S costs 1 insertion, - to SA costs 2 insertions, etc

<img src="images/image-20220503030440708.png" alt="image-20220503030440708" style="zoom:25%;" />

- Looking at D(i - 1, j - 1), s~i~ = s~j~, so we do nothing

<img src="images/image-20220503030626569.png" alt="image-20220503030626569" style="zoom:25%;" />

<img src="images/image-20220503030653235.png" alt="image-20220503030653235" style="zoom:25%;" />

- Looking at D(i - 1, j - 1), s~i~ != s~j~, so we add 1 since S and U are different

<img src="images/image-20220503030855777.png" alt="image-20220503030855777" style="zoom:25%;" />

<img src="images/image-20220503030941103.png" alt="image-20220503030941103" style="zoom: 25%;" />

<img src="images/image-20220503030950486.png" alt="image-20220503030950486" style="zoom:25%;" />

Result: - 3 on upper right cell is the total minimum edit from SUNDAY to SATURDAY

<img src="images/image-20220503031037332.png" alt="image-20220503031037332" style="zoom:25%;" /><img src="images/image-20220503031152643.png" alt="image-20220503031152643" style="zoom: 50%;" />



