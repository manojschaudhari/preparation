## NOTES
- DATA STRUCTURES

## DATA STRUCTURES
####  1. Core Data Structures
#####  Arrays & Strings
- **Array insert/delete**: Understand time complexity – insertion/deletion at end is O(1) amortized, but at arbitrary position requires shifting elements (O(n)). For dynamic arrays (e.g., ArrayList), resizing doubles capacity, leading to amortized O(1). In interviews, handle edge cases like full array, empty slots, and maintaining order.
- **Array reversal**: In-place reversal using two pointers (start, end) swapping elements until they meet – O(n) time, O(1) space. Can be extended to reverse subarrays or rotate arrays.
- **2D arrays**: Row-major vs column-major traversal. Common problems: spiral traversal, matrix rotation, set matrix zeroes. Understand memory layout and cache efficiency (traverse in order of storage).
- **Pattern matching**: String algorithms (naïve, KMP, Rabin-Karp) for substring search. Know how to compute failure function in KMP, rolling hash in Rabin-Karp to avoid spurious hits.
- **Array rotation**: Reversal algorithm (reverse parts then whole) to rotate in O(n) time with O(1) space. Also consider juggling algorithm and block swaps. For left rotation by k, effective shift = k mod n.
- **Palindrome check**: Two-pointer technique from ends; skip non-alphanumeric characters if needed (e.g., valid palindrome). For substring palindromes, expand around center or use DP.
#####  Linked Lists
- **Singly linked list**: Node with value and next pointer. Operations: insert (head, tail, middle), delete (by value, by position). Need to handle head updates. Dummy node simplifies edge cases.
- **Doubly linked list**: Each node has prev and next pointers. Enables backward traversal and easier deletion of a given node. Used in LRU cache implementation.
- **Cycle detection**: Floyd’s cycle detection (tortoise and hare) – O(n) time, O(1) space. Also find start of cycle by resetting one pointer to head after detection.
- **List reversal**: Iterative (three pointers: prev, curr, next) or recursive. For singly linked, reverse entire list or reverse sublists (e.g., reverse between positions). For doubly, also swap prev/next.
- **Fast/slow pointers**: Technique for finding middle, detecting cycle, finding k-th from end. Slow moves one step, fast moves two. For middle, when fast reaches end, slow is at middle.
- **Merge lists**: Merge two sorted linked lists – iterative with dummy head. Also merge k sorted lists using priority queue (min-heap) or divide-and-conquer.
#####  Stacks & Queues
- **Stack implementation**: Using arrays (with top pointer) or linked list (push/pop at head). LIFO. Applications: function call stack, undo/redo, expression evaluation.
- **Queue implementation**: Using arrays (circular buffer) or linked list (head for dequeue, tail for enqueue). FIFO. Know circular queue to reuse space.
- **Parentheses matching**: Use stack to push opening brackets, pop on closing and check match. Also valid for multiple types. Edge cases: unmatched closing, empty stack.
- **Expression evaluation**: Infix to postfix (Shunting-yard algorithm), postfix evaluation using stack. Handle operator precedence and associativity.
- **Next greater element**: Monotonic stack (decreasing order) to find next greater for each element in array. O(n) time.
- **Circular queue**: Fixed-size array with front and rear pointers modulo size. Operations: enqueue (move rear), dequeue (move front). Check full/empty conditions carefully.
#####  Hashing & Heaps
- **HashMap / HashSet**: Underlying array of buckets, hash function, collision resolution (chaining vs open addressing). Load factor and rehashing. Java HashMap uses treeify after threshold. Know time complexities: average O(1), worst O(n).
- **Coding hash-based problems**: Two Sum using HashMap to store complements. Group anagrams by sorting string as key. Subarray sum equals k using prefix sum and map.
- **Min heap / Max heap**: Complete binary tree stored in array. For min-heap, parent <= children. Heapify: building heap in O(n). Insert and extract-min in O(log n). PriorityQueue in Java.
- **Priority queue**: Implemented via heap. Used in Dijkstra, Huffman coding, merging k sorted lists. Know comparator customizations.
- **Heapify operations**: Up-heap (percolate up) after insert, down-heap (heapify) after removal. Building heap from array uses bottom-up heapify (O(n)).
- **Heap sort**: Build max-heap, repeatedly extract max and place at end – O(n log n) in-place, not stable.
####  2. Trees
#####  Binary Trees
- **Tree traversals**:
  - **Preorder**: root-left-right; used for copying tree, prefix expression.
  - **Inorder**: left-root-right; gives sorted order in BST.
  - **Postorder**: left-right-root; used for deleting tree, postfix expression.
  - **Level order (BFS)**: using queue; prints tree level by level.
- **Tree height**: Recursive max(left, right) + 1. Edge case: empty tree height 0. Iterative BFS can also compute levels.
- **Tree diameter**: Longest path between any two nodes (may not pass through root). Compute height of left and right for each node, track max (left+right). O(n) with post-order.
- **Balanced tree check**: Height-balanced (difference <=1 for all nodes). Check recursively, early exit if unbalanced.
- **Mirror tree**: Swap left and right children recursively. Also check if two trees are mirrors.
- **Tree boundary**: Print boundary in anti-clockwise: root, left boundary (excluding leaves), leaves (inorder), right boundary (reverse order). Handle edge cases like single node.
- **Revert tree**: Invert binary tree (swap children). Same as mirror.
#####  Binary Search Tree
- **BST operations**: All operations average O(log n), worst O(n) if skewed.
- **Insert / Delete**: Insert as leaf based on comparisons. Delete: case 1 leaf, case 2 one child, case 3 two children (find inorder successor/predecessor, copy value, delete successor).
- **Search**: Compare key with root, go left or right. Recursive or iterative.
- **Inorder successor**: Minimum node in right subtree if exists, else nearest ancestor for which node is in left subtree.
- **BST validation**: Check if tree is valid BST. Use range (min, max) recursively. Or do inorder traversal and check if sorted.
- **Lowest common ancestor**: For BST, compare both nodes with root; if both smaller go left, both larger go right, else current is LCA.
- **Path to node**: Find path from root to node (backtracking or storing ancestors). Useful for LCA in binary tree.
#####  Advanced Trees
- **AVL trees**: Self-balancing BST with balance factor (-1,0,1). Rotations: LL, RR, LR, RL to maintain balance. Insert/delete O(log n) with rebalancing.
- **Segment tree**: For range queries and updates (e.g., sum, min). Build in O(n), query/update O(log n). Nodes store aggregate info for segments. Lazy propagation for range updates.
- **Fenwick tree (BIT)**: For prefix sums and point updates. Simpler than segment tree, but limited to invertible operations (sum, xor). Build O(n log n), query/update O(log n). Index based on least significant bit.
- **Trie**: Tree for strings, each node represents a character. Used for prefix search, auto-complete, spell checker. Insert/search O(L) where L is word length. Memory heavy, can compress.
- **Prefix search**: Given prefix, traverse trie to node, then collect all words (DFS). Alternatively store end-of-word flag.
- **Auto-complete**: Trie with suggestions based on prefix. Often combined with frequency or sorting.
####  3. Graph Algorithms

#####  Graph Basics
- **Adjacency list**: Array of lists for each vertex, space O(V+E). Preferred for sparse graphs. Easy to iterate neighbors.
- **Adjacency matrix**: 2D array of size VxV, space O(V^2). Fast edge check O(1). Suitable for dense graphs.
- **Graph representation**: Choose based on density and operations. For weighted graphs, store weight in list or matrix cell.
- **Directed graphs**: Edges have direction. In-degree and out-degree. Can have cycles.
- **Undirected graphs**: Edges bidirectional. Usually stored as two directed edges or single with both ends.
- **Weighted graphs**: Edges have weights. Represent as list of tuples (neighbor, weight) or matrix with weights.

#####  Traversal
- **Depth First Search**: Recursive or stack. Used for connectivity, cycle detection, topological sort. Time O(V+E). Mark visited to avoid revisits.
- **Breadth First Search**: Queue. Finds shortest path in unweighted graph. Also for level order, bipartite check.
- **Connected components**: Run DFS/BFS on unvisited nodes, each run gives a component. For directed, strongly connected components (Kosaraju/Tarjan).
- **Cycle detection**: Directed: use recursion stack or color array. Undirected: DFS with parent check.
- **Topological sort**: Only DAG. DFS with post-order or Kahn’s algorithm (BFS with indegree). Used for dependency resolution.
- **Strongly connected components**: Kosaraju (two DFS) or Tarjan (single DFS with low-link). Important for analyzing directed graphs.

#####  Shortest Path
- **Dijkstra**: Non-negative weights. Priority queue, O((V+E) log V). Greedy: always relax smallest distance. Not for negative edges.
- **Bellman-Ford**: Handles negative weights, detects negative cycles. Relax all edges V-1 times, O(VE). For each edge, if distance improves, negative cycle.
- **Floyd-Warshall**: All pairs shortest paths. DP over intermediate vertices, O(V^3). Works for negative edges but no negative cycles.
- **0–1 BFS**: For graphs with edge weights 0 or 1. Use deque: push front for 0, back for 1. O(V+E).

#####  Advanced Graph
- **Minimum spanning tree**: Prim (similar to Dijkstra) and Kruskal (sort edges, union-find). Both O(E log V). MST for undirected weighted graphs.
- **Union find**: Disjoint set with union by rank/size and path compression. Near constant time. Used in Kruskal, cycle detection in undirected graphs.
- **Bipartite graph check**: Graph 2-colorable. Use BFS/DFS and assign alternate colors. No odd cycle.
- **Graph coloring**: Assign colors to vertices such that adjacent have different colors. NP-hard for arbitrary colors; for bipartite, 2 colors suffice. Greedy coloring with ordering.

####  4. Recursion & Backtracking

#####  Recursion Basics
- **Base case / recursive case**: Essential to define termination condition to avoid infinite recursion. Base case handles smallest input.
- **Factorial**: Classic: n*factorial(n-1). Tail recursion optimization possible (but not in all languages).
- **Fibonacci**: Naive recursion has exponential time due to overlapping subproblems. Use memoization or iterative.
- **Tower of Hanoi**: Move n disks from source to destination using auxiliary. Recurrence: T(n)=2T(n-1)+1, steps 2^n-1.
- **Power calculation**: Recursive power (a^n) using divide and conquer: a^(n/2)*a^(n/2) for even, etc. O(log n).
- **Array recursion**: Problems like sum, max, reverse array using recursion with indices.
- **String recursion**: Palindrome check, permutations, subsequences.

#####  Combinatorics
- **Generate subsets**: For each element, include/exclude. Backtracking or bitmask. O(2^n). Subsets vs subsequences (order preserved).
- **Generate permutations**: Swap positions (Heap's algorithm) or use visited array. O(n!). Duplicates handling by sorting and skipping.
- **Phone letter mapping**: Map digits to letters, generate all combinations. Backtracking with index.
- **Generate parentheses**: Add open if count < n, close if close < open. Valid only if close <= open at any point.
- **Combination sum**: Find all combinations that sum to target, can reuse same element (with index to avoid order duplicates). Backtracking.

#####  Backtracking
- **N-Queens**: Place queens row by row, check column and diagonals. Backtrack when conflict. Use boolean arrays for columns and diagonals (row-col constant, row+col constant).
- **Sudoku solver**: Find empty cell, try digits 1-9, check row, column, box constraints. Recursively fill.
- **Word search**: DFS from each cell matching first char, mark visited, backtrack. Check boundaries.
- **Rat in maze**: Find path from top-left to bottom-right (can move right/down). Recursive with visited matrix.
- **Knight's tour**: Place knight on board, move to unvisited cells according to knight moves. Warnsdorff's heuristic for optimization.
- **Subset sum**: Check if subset with given sum exists. Backtracking with pruning.

#####  Optimization
- **Memoization**: Store results of subproblems to avoid recomputation (top-down DP). Use map or array. E.g., Fibonacci.
- **Pruning techniques**: In backtracking, cut branches early (e.g., in N-Queens, skip if conflict; in subset sum, if sum exceeds target). Order of choices can improve pruning (e.g., start with largest).

####  5. Searching & Sorting

#####  Searching
- **Linear search**: O(n). Simple but inefficient for large data. Used on unsorted data.
- **Binary search**: O(log n) on sorted array. Must handle integer overflow (mid = low + (high-low)/2). Variants: find first/last occurrence, floor/ceil.
- **Rotated array search**: Modified binary search: check which half is sorted and decide which side to go. Handles duplicates (may degrade to linear).
- **First / last occurrence**: Binary search with condition to move left or right. For first occurrence, if mid == target, move left; for last, move right.
- **Peak element**: Find any peak (element greater than neighbors). Binary search: if mid < mid+1, peak on right, else left. O(log n).
- **Square root (binary)**: Compute integer sqrt using binary search between 0 and x. For precision, use double.
- **2D matrix search**: If matrix rows and columns sorted, search from top-right or bottom-left (O(m+n)). If fully sorted (row-wise), treat as 1D array (binary search on index).
- **Search insert position**: Binary search to find position where target would be inserted (lower bound).

#####  Sorting
- **Bubble sort**: Repeatedly swap adjacent if out of order. O(n^2). Stable. Optimize by stopping if no swaps.
- **Selection sort**: Find minimum and swap to front. O(n^2). Not stable.
- **Insertion sort**: Build sorted portion by inserting each element. O(n^2) but efficient for small or nearly sorted data. Stable.
- **Merge sort**: Divide and conquer, O(n log n) time, O(n) space. Stable. Good for linked lists and external sorting.
- **Quick sort**: Pick pivot, partition, recurse. Average O(n log n), worst O(n^2) if poor pivot. In-place, not stable. Optimizations: random pivot, median-of-three.
- **Heap sort**: Build heap, extract max. O(n log n) in-place, not stable.
- **Counting sort**: O(n+k) where k is range. Stable if using cumulative counts. Only for integers with limited range.
- **Radix sort**: Sort by digits, using counting sort per digit. O(d*(n+k)) where d digits, k base. Good for fixed-length keys.
- **Bucket sort**: Distribute into buckets, sort each (e.g., insertion sort). O(n) average if uniform distribution.

#####  Two Pointer Techniques
- **Two sum / Three sum**: For sorted array, two pointers from ends. For three sum, fix one and use two pointers on remaining. Avoid duplicates by skipping.
- **Container with most water**: Two pointers at ends, move the pointer with smaller height, track max area. O(n).
- **Dutch flag algorithm**: Three-way partitioning (0,1,2). Use low, mid, high pointers. Move mid based on value.
- **Remove duplicates**: From sorted array, two pointers: one for read, one for write. O(n) in-place.

####  6. Greedy Algorithms
- **Activity selection**: Choose non-overlapping activities with max count. Sort by end time, pick if start >= last end. O(n log n).
- **Fractional knapsack**: Items with weight and value, maximize value with weight limit. Sort by value/weight, take fractions. O(n log n).
- **Job scheduling**: Minimize lateness or maximize profit. For scheduling with deadlines and profit (each job takes unit time), sort by profit and assign to latest free slot.
- **Huffman coding**: Build optimal prefix codes. Use min-heap, combine two smallest frequencies repeatedly. Greedy yields optimal compression.
- **Meeting rooms**: Minimum rooms needed. Sort by start and end times, use two pointers or min-heap to track earliest ending.
- **Merge intervals**: Sort by start, then merge overlapping. Output list of merged intervals.
- **Minimum platforms**: For train arrivals/departures, sort arrival and departure separately, two-pointer to find max platforms at any time.
- **Coin change (greedy)**: Works only for canonical coin systems (e.g., USD). Not always optimal; use DP for general.

####  7. Sliding Window
- **Fixed size window**: Sum of subarray of size k: compute first window, then slide by subtracting left, adding right.
- **Variable size window**: Expand right until condition met, then shrink left while condition holds. Used for subarrays with constraints.
- **Maximum sum subarray**: Kadane's algorithm is DP, not sliding window (unless fixed size). For fixed size, use sliding window sum.
- **Longest substring without repeating**: Use two pointers and hashset to track characters in current window. When duplicate, move left to after previous occurrence.
- **Minimum window substring**: Find smallest substring containing all characters of target. Expand right, when condition met, shrink left. Use hashmap to count characters.
- **K distinct characters**: Longest substring with at most K distinct. Use hashmap to count, shrink when >K.
- **Anagram count**: Count occurrences of anagrams of pattern in text. Use sliding window with frequency arrays.
- **Fruits in baskets**: Similar to at most two distinct characters (fruits). Variable window.

####  8. Monotonic Stack
- **Next greater element**: Maintain stack of indices with decreasing values. For each element, pop while smaller, record next greater for popped, push current.
- **Stock span problem**: Consecutive days price <= current. Monotonic stack storing pairs (price, span). Pop while top price <= current, accumulate span.
- **Largest rectangle in histogram**: For each bar, find left and right smaller indices. Use stack to compute next smaller left and right. Area = height * (right-left-1).
- **Sliding window maximum**: Maintain deque of indices with decreasing values. For each window, remove out-of-range front, remove from back smaller than new, add new. Front is max.

####  9. Dynamic Programming

#####  Fundamentals
- **Memoization**: Top-down DP, recursion with caching. Overlapping subproblems identified.
- **Tabulation**: Bottom-up DP, iterative filling table. Often more efficient (no recursion overhead).
- **Overlapping subproblems**: Subproblems recur many times, enabling DP (e.g., Fibonacci).
- **Optimal substructure**: Optimal solution of problem contains optimal solutions to subproblems (e.g., shortest path).
- **Space optimization**: Reduce 2D DP to 1D or variables if only previous states needed (e.g., knapsack).
- **State transitions**: Define recurrence relation carefully. Identify states (indices, remaining capacity, etc.).

#####  1D DP
- **Climbing stairs**: ways[i] = ways[i-1] + ways[i-2]. Base cases.
- **House robber**: Max loot without adjacent. dp[i] = max(dp[i-1], dp[i-2]+nums[i]).
- **Coin change**: Minimum coins to make amount. dp[amount] = min(dp[amount-coin])+1.
- **Longest increasing subsequence**: O(n^2) dp, or O(n log n) with patience sorting (binary search on tails).
- **Perfect squares**: Minimum number of perfect squares summing to n. dp[n] = min(dp[n - i*i])+1.

#####  2D DP
- **Grid paths**: Unique paths from top-left to bottom-right (only right/down). dp[i][j] = dp[i-1][j] + dp[i][j-1]. Base cases.
- **Minimum path sum**: Similar, but take min of top/left plus current cell.
- **Longest common subsequence**: dp[i][j] = dp[i-1][j-1]+1 if chars equal, else max(dp[i-1][j], dp[i][j-1]).
- **Edit distance**: Transform string1 to string2 with insert/delete/replace. dp[i][j] = min of three operations.
- **0/1 knapsack**: Maximize value with weight limit. dp[i][w] = max(dp[i-1][w], dp[i-1][w-weight[i]]+value[i]).

#####  Advanced DP
- **Matrix chain multiplication**: Minimum scalar multiplications. dp[i][j] = min(dp[i][k] + dp[k+1][j] + dims[i-1]*dims[k]*dims[j]) over k.
- **Palindrome partitioning**: Minimum cuts to partition string into palindromes. Precompute palindrome table, then dp[i] = min(dp[j-1]+1) for j..i palindrome.
- **Word break**: Check if string can be segmented into dictionary words. dp[i] = true if dp[j] and s[j:i] in dict.
- **Bitmask DP**: State represented by bitmask (e.g., traveling salesman). dp[mask][last] = min cost.

####  10. String Algorithms

#####  Pattern Matching
- **Naive search**: O(n*m) worst-case. Simple but inefficient.
- **KMP algorithm**: Preprocess pattern to build LPS (longest prefix suffix) array, then search in O(n+m). Avoids backtracking in text.
- **Rabin-Karp**: Rolling hash (e.g., base 256 mod prime). Hash of pattern compared to text window. Hash collisions handled by verification. O(n+m) average.
- **Boyer-Moore**: Preprocess bad character and good suffix heuristics. Skips sections, sublinear on average. Complex to implement.
- **Z algorithm**: Computes Z-array (longest substring starting at i matching prefix). Used for pattern matching by concatenating pattern + "$" + text. O(n+m).
- **Aho-Corasick**: Build trie with failure links for multiple pattern matching. O(n + total matches). Used in antivirus, etc.

#####  String Operations
- **String rotation**: Check if s2 is rotation of s1 using s1+s1 contains s2 (if lengths equal). Also can find rotation point.
- **Anagram detection**: Two strings are anagrams if sorted equal or character counts equal.
- **Group anagrams**: Use sorted string as key in map, or character count tuple.
- **Longest common prefix**: Sort strings and compare first and last, or vertical scanning.
- **Valid anagram**: Same as detection.
- **Isomorphic strings**: Map characters to each other one-to-one. Two passes to ensure bijection.

#####  Palindromes
- **Palindrome check**: Two pointers from ends.
- **Longest palindrome**: Expand around center for each position (odd/even). O(n^2). Manacher's algorithm O(n).
- **Manacher’s algorithm**: Transform string with separators, compute palindrome radii array. Linear time.
- **Palindrome pairs**: Find all pairs (i,j) such that concatenation of words[i]+words[j] is palindrome. Use hashmap and check suffixes/prefixes.
- **Valid palindrome**: Ignore non-alphanumeric, case-insensitive. Two pointers.
- **Shortest palindrome**: Find longest palindrome prefix, then reverse remaining suffix and prepend. Use KMP to find longest prefix palindrome.

#####  Advanced
- **Suffix array**: Array of starting indices of suffixes in lexicographic order. Build in O(n log n) via doubling or SA-IS. Used for pattern matching, LCP.
- **Suffix tree**: Compressed trie of all suffixes. Can be built in O(n) (Ukkonen). Solves many string problems (LCS, repeats).
- **String compression**: Run-length encoding, or shortest encoding using suffix structures.
- **Wildcard matching**: '*' matches any sequence, '?' matches single char. DP or recursion with backtracking.

####  11. Bit Manipulation
- **Bitwise operations**: &, |, ^, ~, <<, >> (arithmetic vs logical shift in languages). Know precedence.
- **Bit masking**: Use masks to set, clear, toggle, check bits. E.g., set kth bit: num | (1<<k); clear: num & ~(1<<k).
- **Count set bits**: Brian Kernighan algorithm: while(n) { count++; n &= n-1; } O(number of set bits). Also built-in: Integer.bitCount().
- **Power of two**: Check if n>0 and (n & (n-1)) == 0.
- **Brian Kernighan algorithm**: As above, clears lowest set bit each iteration.
- **Single number**: Find element appearing once when others appear twice: XOR all, result is the unique element. For two singles, XOR all, then find rightmost set bit, partition.
- **Fast exponentiation**: Compute a^b mod m using binary exponentiation: while(b) { if(b&1) res = res*a mod m; a = a*a mod m; b>>=1; } O(log b).

####  12. Mathematical Algorithms
- **Sieve of Eratosthenes**: Find all primes up to n. O(n log log n). Mark multiples starting from p^2. Optimizations: only odd numbers.
- **GCD / LCM**: Euclidean algorithm for GCD: gcd(a,b) = gcd(b, a%b). LCM = a*b / gcd. Handle overflow.
- **Modular arithmetic**: (a+b)%m = (a%m + b%m)%m; (a*b)%m = (a%m * b%m)%m. Modular inverse using Fermat’s little theorem if m prime.
- **Matrix exponentiation**: Compute linear recurrences (e.g., Fibonacci) in O(log n) by exponentiation of transformation matrix.
- **Prime factorization**: Trial division up to sqrt(n). Optimize by checking 2 then odd numbers. Use precomputed primes for efficiency.
- **Euler’s totient**: φ(n) counts numbers coprime to n. Compute via factorization: φ(n)=n∏(1-1/p). Sieve can compute all φ up to n.

####  13. Advanced Data Structures
- **Fenwick tree**: See 2. Advanced Trees. Supports prefix sum and point update. For range update, use two BITs or difference array.
- **Segment tree**: See 2. Advanced Trees. Can support range min/max/sum, lazy propagation for range updates. Implement iterative (faster) or recursive.
- **Union find**: Disjoint set with union by rank/size and path compression. Near O(α(n)). Used in connectivity, MST.
- **Disjoint set**: Same as union find.
- **Binary lifting**: Preprocess ancestors for each node for LCA queries. up[u][i] = 2^i-th ancestor. O(n log n) preprocess, O(log n) query.
- **LCA queries**: Using binary lifting, or Euler tour + RMQ. Also Tarjan's offline algorithm.

####  14. Specialized Algorithms
- **Mo’s algorithm**: Offline query processing for range queries (e.g., distinct count). Sort queries by block of L, then R. O((N+Q)√N) time.
- **Square root decomposition**: Partition array into blocks of size √N. Precompute per-block aggregates. Queries combine blocks and partial edges. O(√N) per query.
- **Heavy-light decomposition**: Decompose tree into heavy paths to support path queries (e.g., sum, max). Combine with segment tree. O(log^2 n) per query.
- **Persistent data structures**: Allow access to previous versions. E.g., persistent segment tree (functional). Used in problems like K-th number in range.















## Creational Patterns (Object Creation)

### Singleton
**Explanation:** Ensures a class has only one instance and provides a global access point.  
**Java Sample:**
```java
public class Singleton {
    private static Singleton instance;
    private Singleton() {}
    public static Singleton getInstance() {
        if (instance == null) instance = new Singleton();
        return instance;
    }
}
```

### Factory Method
**Explanation:** Defines an interface for creating an object, but subclasses decide which class to instantiate.  
**Java Sample:**
```java
interface Product { void doStuff(); }
class ConcreteProduct implements Product { public void doStuff() { System.out.println("Product A"); } }
abstract class Creator { abstract Product factoryMethod(); }
class ConcreteCreator extends Creator { Product factoryMethod() { return new ConcreteProduct(); } }
```

### Abstract Factory
**Explanation:** Provides an interface for creating families of related or dependent objects without specifying concrete classes.  
**Java Sample:**
```java
interface Button { void render(); }
interface Checkbox { void render(); }
interface GUIFactory { Button createButton(); Checkbox createCheckbox(); }
class WinButton implements Button { public void render() { System.out.println("Windows Button"); } }
class WinFactory implements GUIFactory { public Button createButton() { return new WinButton(); } }
```

### Builder
**Explanation:** Separates the construction of a complex object from its representation, allowing the same construction process to create different representations.  
**Java Sample:**
```java
class Pizza {
    private String dough; private String sauce;
    private Pizza(Builder b) { dough = b.dough; sauce = b.sauce; }
    static class Builder {
        String dough, sauce;
        Builder setDough(String d) { dough = d; return this; }
        Builder setSauce(String s) { sauce = s; return this; }
        Pizza build() { return new Pizza(this); }
    }
}
// Usage: new Pizza.Builder().setDough("thick").setSauce("tomato").build();
```

### Prototype
**Explanation:** Creates new objects by cloning an existing object (prototype) rather than calling constructors.  
**Java Sample:**
```java
class Sheep implements Cloneable {
    String name;
    Sheep(String n) { name = n; }
    public Sheep clone() { try { return (Sheep) super.clone(); } catch(CloneNotSupportedException e) { return null; } }
}
// Sheep dolly = new Sheep("Dolly").clone();
```

### Object Pool
**Explanation:** Reuses objects that are expensive to create by keeping a pool of available instances.  
**Java Sample:**
```java
import java.util.*;
class Pool {
    private List<Object> available = new ArrayList<>();
    public Object acquire() { return available.isEmpty() ? new Object() : available.remove(0); }
    public void release(Object o) { available.add(o); }
}
```

### Lazy Initialization
**Explanation:** Delays the creation of an object or computation until it is first needed.  
**Java Sample:**
```java
class Heavy {
    Heavy() { System.out.println("Creating heavy"); }
}
class Holder {
    private Heavy heavy = null;
    public Heavy getHeavy() {
        if (heavy == null) heavy = new Heavy();
        return heavy;
    }
}
```

### Dependency Injection
**Explanation:** Passes dependencies (services/objects) to a client from the outside rather than having the client create them.  
**Java Sample:**
```java
class Service { void serve() { System.out.println("Service"); } }
class Client {
    private Service service;
    Client(Service s) { service = s; }  // constructor injection
    void doWork() { service.serve(); }
}
// Client c = new Client(new Service());
```

### Service Locator
**Explanation:** Provides a central registry that returns necessary services when asked, abstracting the lookup process.  
**Java Sample:**
```java
class ServiceLocator {
    private static Map<String, Object> services = new HashMap<>();
    public static void register(String name, Object svc) { services.put(name, svc); }
    public static Object lookup(String name) { return services.get(name); }
}
// ServiceLocator.register("logger", new Logger());
```

---

## Structural Patterns (Object Structure)

### Adapter
**Explanation:** Allows incompatible interfaces to work together by wrapping an existing class with a new interface.  
**Java Sample:**
```java
interface Target { void request(); }
class Adaptee { void specificRequest() { System.out.println("Adaptee"); } }
class Adapter implements Target {
    private Adaptee adaptee = new Adaptee();
    public void request() { adaptee.specificRequest(); }
}
```

### Bridge
**Explanation:** Decouples an abstraction from its implementation so that both can vary independently.  
**Java Sample:**
```java
interface Device { void turnOn(); }
class TV implements Device { public void turnOn() { System.out.println("TV on"); } }
class Remote {
    protected Device device;
    Remote(Device d) { device = d; }
    void pressPower() { device.turnOn(); }
}
```

### Composite
**Explanation:** Composes objects into tree structures to represent part-whole hierarchies, allowing clients to treat individual objects and compositions uniformly.  
**Java Sample:**
```java
interface Component { void operation(); }
class Leaf implements Component { public void operation() { System.out.println("Leaf"); } }
class Composite implements Component {
    List<Component> children = new ArrayList<>();
    public void operation() { for(Component c : children) c.operation(); }
    void add(Component c) { children.add(c); }
}
```

### Decorator
**Explanation:** Dynamically adds responsibilities to an object by wrapping it with one or more decorator classes.  
**Java Sample:**
```java
interface Coffee { double cost(); }
class SimpleCoffee implements Coffee { public double cost() { return 1.0; } }
class MilkDecorator implements Coffee {
    private Coffee coffee;
    MilkDecorator(Coffee c) { coffee = c; }
    public double cost() { return coffee.cost() + 0.5; }
}
// Coffee c = new MilkDecorator(new SimpleCoffee());
```

### Facade
**Explanation:** Provides a simplified interface to a complex subsystem, hiding its internal complexity.  
**Java Sample:**
```java
class CPU { void freeze() {} void jump(long pos) {} void execute() {} }
class HardDrive { byte[] read(long lba, int size) { return new byte[size]; } }
class ComputerFacade {
    private CPU cpu = new CPU();
    private HardDrive hd = new HardDrive();
    void start() { cpu.freeze(); cpu.jump(0); cpu.execute(); }
}
```

### Flyweight
**Explanation:** Minimizes memory usage by sharing as much data as possible with similar objects (intrinsic state shared, extrinsic passed).  
**Java Sample:**
```java
import java.util.*;
class TreeType { String name, color; }  // intrinsic
class TreeFactory {
    static Map<String, TreeType> types = new HashMap<>();
    static TreeType getType(String name, String color) {
        String key = name + color;
        if(!types.containsKey(key)) types.put(key, new TreeType(name, color));
        return types.get(key);
    }
}
```

### Proxy
**Explanation:** Provides a surrogate or placeholder for another object to control access, add logging, lazy loading, etc.  
**Java Sample:**
```java
interface Image { void display(); }
class RealImage implements Image { private String file; RealImage(String f) { file = f; load(); } void load() {} public void display() {} }
class ProxyImage implements Image {
    private RealImage real;
    private String file;
    ProxyImage(String f) { file = f; }
    public void display() { if(real == null) real = new RealImage(file); real.display(); }
}
```

### Wrapper
**Explanation:** Wraps a primitive or object to add behavior or convert types; often used as a simple container.  
**Java Sample:**
```java
class IntegerWrapper {
    private int value;
    IntegerWrapper(int v) { value = v; }
    int getValue() { return value; }
    void setValue(int v) { value = v; }
}
```

### Marker
**Explanation:** Uses an empty interface (marker interface) to signal a capability or type information to the compiler or runtime.  
**Java Sample:**
```java
interface SerializableMarker {}  // empty marker
class MyClass implements SerializableMarker { }
// if(obj instanceof SerializableMarker) { ... }
```

---

## Behavioral Patterns (Object Interaction)

### Observer
**Explanation:** Defines a one-to-many dependency so that when one object changes state, all its dependents are notified automatically.  
**Java Sample:**
```java
import java.util.*;
interface Observer { void update(String msg); }
class ConcreteObserver implements Observer { public void update(String msg) { System.out.println(msg); } }
class Subject {
    List<Observer> observers = new ArrayList<>();
    void attach(Observer o) { observers.add(o); }
    void notify(String s) { for(Observer o : observers) o.update(s); }
}
```

### Strategy
**Explanation:** Defines a family of algorithms, encapsulates each, and makes them interchangeable at runtime.  
**Java Sample:**
```java
interface Strategy { int doOperation(int a, int b); }
class Add implements Strategy { public int doOperation(int a, int b) { return a+b; } }
class Context {
    private Strategy strategy;
    Context(Strategy s) { strategy = s; }
    int execute(int a, int b) { return strategy.doOperation(a,b); }
}
```

### Command
**Explanation:** Encapsulates a request as an object, thereby allowing parameterization, queuing, logging, and undoable operations.  
**Java Sample:**
```java
interface Command { void execute(); }
class LightOnCommand implements Command {
    private Light light;
    LightOnCommand(Light l) { light = l; }
    public void execute() { light.on(); }
}
class Light { void on() { System.out.println("Light on"); } }
```

### Chain of Responsibility
**Explanation:** Passes a request along a chain of handlers; each handler decides to process or pass to the next.  
**Java Sample:**
```java
abstract class Handler {
    protected Handler next;
    void setNext(Handler n) { next = n; }
    abstract void handle(int request);
}
class ConcreteHandler extends Handler {
    void handle(int request) { if(request < 10) System.out.println("Handled"); else if(next != null) next.handle(request); }
}
```

### State
**Explanation:** Allows an object to alter its behavior when its internal state changes, appearing to change its class.  
**Java Sample:**
```java
interface State { void doAction(Context ctx); }
class StartState implements State { public void doAction(Context ctx) { System.out.println("Start"); ctx.setState(this); } }
class Context { private State state; void setState(State s) { state = s; } void doAction() { state.doAction(this); } }
```

### Template Method
**Explanation:** Defines the skeleton of an algorithm in a method, deferring some steps to subclasses.  
**Java Sample:**
```java
abstract class Game {
    abstract void initialize();
    abstract void startPlay();
    final void play() { initialize(); startPlay(); } // template method
}
class Cricket extends Game { void initialize() {} void startPlay() {} }
```

### Mediator
**Explanation:** Defines an object that encapsulates how a set of objects interact, promoting loose coupling.  
**Java Sample:**
```java
interface Mediator { void send(String msg, Colleague colleague); }
class ConcreteMediator implements Mediator { public void send(String msg, Colleague c) { System.out.println(msg); } }
abstract class Colleague { protected Mediator mediator; Colleague(Mediator m) { mediator = m; } }
```

### Memento
**Explanation:** Captures and externalizes an object’s internal state so that the object can be restored later without violating encapsulation.  
**Java Sample:**
```java
class Memento { private String state; Memento(String s) { state = s; } String getState() { return state; } }
class Originator { private String state; void set(String s) { state = s; } Memento save() { return new Memento(state); } void restore(Memento m) { state = m.getState(); } }
```

### Visitor
**Explanation:** Represents an operation to be performed on elements of an object structure, allowing new operations without changing the element classes.  
**Java Sample:**
```java
interface Element { void accept(Visitor v); }
class ConcreteElement implements Element { public void accept(Visitor v) { v.visit(this); } }
interface Visitor { void visit(ConcreteElement e); }
class ConcreteVisitor implements Visitor { public void visit(ConcreteElement e) { System.out.println("Visited"); } }
```

### Interpreter
**Explanation:** Defines a grammar for a language and an interpreter to parse sentences in that language.  
**Java Sample:**
```java
interface Expression { boolean interpret(String context); }
class TerminalExpression implements Expression { private String data; TerminalExpression(String d) { data = d; } public boolean interpret(String ctx) { return ctx.contains(data); } }
// Usage: Expression exp = new TerminalExpression("hello"); exp.interpret("hello world");
```

### Iterator
**Explanation:** Provides a way to access elements of an aggregate object sequentially without exposing its underlying representation.  
**Java Sample:**
```java
import java.util.*;
class NameRepository {
    String[] names = {"A","B"};
    Iterator<String> getIterator() { return Arrays.asList(names).iterator(); }
}
// Iterator<String> it = new NameRepository().getIterator(); while(it.hasNext()) System.out.println(it.next());
```
## EVENT
- **Core Architectural Paradigms** ✿ Event-Driven Architecture (EDA) ✿ Message-Driven Architecture (MDA) ✿ Reactive Architecture ✿ Streaming Architecture ✿ Asynchronous Architecture ✿ Distributed Systems ✿ Microservices Architecture ✿ Serverless Architecture ✿ Data-Driven Architecture ✿ Domain-Driven Design (DDD) ✿ CQRS (Command Query Responsibility Segregation) ✿ Event-Based Systems ✿ Flow-Based Programming 
- **Event Streaming Keywords** ✿ Event Streaming ✿ Stream Processing ✿ Real-Time Data Pipelines ✿ Continuous Processing ✿ Data Streams ✿ Unbounded Data ✿ Stateful Stream Processing ✿ Stateless Processing ✿ Windowing (Tumbling, Sliding, Session) ✿ Event Time vs Processing Time ✿ Watermarks ✿ Backpressure ✿ Exactly-once Processing ✿ At-least-once Processing ✿ At-most-once Processing ✿ Stream Joins ✿ Stream Aggregation ✿ Log-based Streaming ✿ Distributed Log ✿ Immutable Log 
- **Event Sourcing Keywords** ✿ Event Sourcing ✿ Event Store ✿ Append-only Log ✿ Immutable Events ✿ Event Replay ✿ Event Rehydration ✿ Snapshotting ✿ Aggregate ✿ Aggregate Root ✿ Domain Events ✿ Command Handling ✿ Event Versioning ✿ Event Schema Evolution ✿ Temporal Modeling ✿ Audit Log ✿ Change Data Capture (CDC) ✿ Write Model / Read Model ✿ Eventual Consistency 
- **Event-Driven Architecture (EDA)** ✿ Event Producer ✿ Event Consumer ✿ Event Broker ✿ Event Bus ✿ Event Channel ✿ Event Notification ✿ Event Carried State Transfer ✿ Event Collaboration ✿ Loose Coupling ✿ Pub/Sub (Publish-Subscribe) ✿ Topic-based Routing ✿ Content-based Routing ✿ Event Filtering ✿ Event Transformation ✿ Event Enrichment ✿ Event Correlation ✿ Event Choreography ✿ Event Orchestration 
- **Message-Driven Architecture (MDA)** ✿ Message Queue ✿ Message Broker ✿ Message Channel ✿ Message Handler ✿ Message Routing ✿ Message Transformation ✿ Message Translator ✿ Message Envelope ✿ Dead Letter Queue (DLQ) ✿ Message Acknowledgment ✿ Message Retry ✿ Idempotency ✿ Guaranteed Delivery ✿ Message Ordering ✿ FIFO / Priority Queue 
- **Push-Based** ✿ Push Model ✿ Event Push ✿ Webhooks ✿ Server Push ✿ Publish-Subscribe ✿ Fan-out ✿ Reactive Push ✿ Observer Pattern 
- **Pull-Based** ✿ Pull Model ✿ Polling ✿ Long Polling ✿ Consumer Pull ✿ Batch Processing ✿ Request-Response ✿ Data Fetching ✿ Lazy Loading 
- **Hybrid Model** ✿ Push-Pull Hybrid ✿ Backpressure Control ✿ Consumer-driven Pull ✿ Reactive Streams 
- **Patterns & Design Concepts**** ✿ Event Notification Pattern ✿ Event-Carried State Transfer Pattern ✿ Competing Consumers Pattern ✿ Saga Pattern (Orchestration / Choreography) ✿ Outbox Pattern ✿ Inbox Pattern ✿ Circuit Breaker ✿ Retry Pattern ✿ Bulkhead Pattern ✿ Idempotent Consumer ✿ Exactly-once Semantics ✿ Event Replay Pattern ✿ Dead Letter Handling ✿ Message Deduplication 
- **Data & Consistency Concepts** ✿ Eventual Consistency ✿ Strong Consistency ✿ Distributed Transactions ✿ Two-Phase Commit (2PC) ✿ Saga Transactions ✿ Data Replication ✿ Data Partitioning ✿ Sharding ✿ Data Synchronization ✿ Consistency Models (CAP Theorem) 
- **Integration & API Concepts** ✿ API Gateway ✿ Webhooks ✿ REST vs Events ✿ gRPC Streaming ✿ GraphQL Subscriptions ✿ Integration Patterns ✿ Enterprise Service Bus (ESB) ✿ Service Mesh ✿ Sidecar Pattern 
- **Observability & Operations** ✿ Distributed Tracing ✿ Correlation ID ✿ Logging ✿ Metrics ✿ Monitoring ✿ Alerting ✿ Lag Monitoring (Consumer Lag) ✿ Throughput / Latency ✿ Backpressure Monitoring 
- **Security & Governance** ✿ Event Schema Registry ✿ Schema Validation ✿ Data Contracts ✿ Encryption in Transit ✿ Encryption at Rest ✿ Authentication / Authorization ✿ Multi-Tenancy ✿ Data Governance 
- **Advanced / Emerging Concepts** ✿ Data Mesh ✿ Streaming ETL ✿ Real-Time Analytics ✿ Event Mesh ✿ Digital Twin ✿ Edge Streaming ✿ AI/ML Streaming Pipelines ✿ Stateful Functions ✿ Serverless Streaming 
- **Related Programming & Framework** ✿ Reactive Streams ✿ Project Reactor ✿ RxJava ✿ Akka Streams ✿ Spring WebFlux ✿ Kafka Streams ✿ Apache Flink ✿ Apache Spark Streaming ✿ Beam (Apache Beam) If you want, I can next: ✿ 🔥 Map these to interview Q&A (FAANG-level) ✿ 📊 Create a mindmap / architecture diagram ✿ 📄 Generate a downloadable PDF cheat sheet ✿ 🧠 Build system design scenarios (Netflix/Uber-style)













