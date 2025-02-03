Contents:  
[1.Problems](cheatsheet_leetcode.md#1problems)  
[2.Skills](cheatsheet_leetcode.md#2skills)  
[3.Complexity](cheatsheet_leetcode.md#3complexity)  

# 1.Problems
* [1.1.Top 100 Liked Easy](cheatsheet_leetcode.md#11top-100-liked---easy--is-also-top-interview-)
* [1.2.Top 100 Liked Medium](cheatsheet_leetcode.md#12top-100-liked---medium--is-also-top-interview)
* [1.3.Top 100 Liked Hard](cheatsheet_leetcode.md#13top-100-liked---hard--is-also-top-interview)
* [1.4.Top Interview Easy](cheatsheet_leetcode.md#14top-interview---easy-wo-top-100-liked)
* [1.5.Top Interview Medium](cheatsheet_leetcode.md#15top-interview---medium-wo-top-100-liked)
* [1.6.Top Interview Hard](cheatsheet_leetcode.md#16top-interview---hard-wo-top-100-liked)
* [1.7.Others](cheatsheet_leetcode.md#17others)

## 1.1.Top 100 Liked - Easy (★ is also top interview)
|count|problem|remark|
|--|--|--|
|1★|1. Two Sum | BF two for loop for all combination, two pointers left and right on sorted array, hash map cache |
|2★|13. Roman to Integer | for loop with multiple cases if |
|3★|14. Longest Common Prefix | for loop, time O(MN) |
|4★|20. Valid Parentheses | std::stack |
|5★|21. Merge Two Sorted Lists | two pointers on each up and down, list, time O(M+N) |
|6|35. Search Insert Position | binary search, mid mid, time O(logN) |
|7★|70. Climbing Stairs | 1D-DP 5ways, BF for-loop+math, one to two possible paths: minus1 or minus2, BF recursive subproblem T:O(2^N) S:O(N), recursion with hash map memoization T:O(N) S:O(N), bottom up iterative vector tabulation T:O(N) S:O(N), space optimization temp prev and curr swap T:O(N) S:O(1) |
|8★|94. Binary Tree Inorder Traversal | DFS recursive childnode, DFS iterative with stack, add after all left children (left then right) in if == nullptr |
|9★|101. Symmetric Tree | DFS recursive childnode, BFS iterative with queue |
|10★|104. Maximum Depth of Binary Tree| DFS recursive childnode, BFS iterative with queue, time O(N), space O(height) |
|11★|118. Pascal's Triangle| for loop, 2D vector |
|12★|121. Best Time to Buy and Sell Stock| 2D-DP, Kadane's algo, 53. Maximum Subarray |
|13★|136. Single Number| hash map cache, space O(N), sorting, share variable, bit operation, XOR^=, space O(1), sum & set |
|14★|141. Linked List Cycle| Floyd Cycle detection, two pointers faster and slow (hit with while) |
|15★|160. Intersection of Two Linked Lists| hash map cache, two pointers with subtraction (hit with fixed range), two pointers with switching (hit with while) |
|16★|169. Majority Element| vector/hash map cache, space O(N), share variable, space O(1) |
|17★|206. Reverse Linked List| temp prev and curr swap, list recursive nextnode |
|18|226. Invert Binary Tree|  DFS recursive childnode, BFS iterative with queue |
|19★|234. Palindrome Linked List|  Floyd's algo, two pointers faster and slow (find the mid), 206. Reverse Linked List, three steps |
|20★|283. Move Zeroes| for loop, swap, time O(N), space O(1) |
|21|543. Diameter of Binary Tree| 104. Maximum Depth of Binary Tree, DFS recursive childnode |
|22|704. Binary Search| binary search, time O(logN), left mid floor need +1, right mid ceil need -1,  mid mid seperate if-else |

## 1.2.Top 100 Liked - Medium (★ is also top interview)
|count|problem|remark|
|--|--|--|
|1★|2. Add Two Numbers| for loop, list, dummy start node for return, decimal, carry |
|2★|3. Longest Substring Without Repeating Characters| sliding window, vector/hash map cache, two pointers cur and accumulated |
|3★|5. Longest Palindromic Substring| two pointers left and right, BF three for loop time O(N^3), inner to outer odd and even expand O(N^2) saving no. combination, DP outer to inner subproblem bottom up SC O(N^2) TC O(N^2) saving comparison |
|4★|11. Container With Most Water | BF two for loop time O(N^2), two pointers left and right comparison |
|5★|15. 3Sum | sorted vector to avoid duplicate, iterative start point, then two for loop with hash map cache or two pointers left and right represent positive and negative |
|6★|17. Letter Combinations of a Phone Number| for loop with multiple cases if, hash map cache, vector instead hash map, queue FIFO BFS accumulate str|
|7★|19. Remove Nth Node From End of List| two pointers fast and slow with subtraction (fast hit, slow reach) |
|8★|22. Generate Parentheses | recursive, two counters left and right accumulated |
|9|24. Swap Nodes in Pairs | dummy start node for prev, prev and curr swap |
|10|31. Next Permutation | permutation/combination/anagrams/palindromic, swap, reverse, special solution |
|11★|33. Search in Rotated Sorted Array | binary search find sep, using sep and % for rotated array, binary search find target, left mid, mid mid, (189. Rotate Array + 153. Find Minimum in Rotated Sorted Array) |
|12★|34. Find First and Last Position of Element in Sorted Array | binary search, left mid, right mid |
|13|39. Combination Sum| recursive subproblem, minus vec elements subproblem, backtracking, push_back before pop_back after, with DFS |
|14|45. Jump Game II | 1D-DP 4ways, iterative start point, plus cur leave right subproblem, BF recursive subproblem T:O(N!) S:O(N), recursion with hash map memoization T:O(N^2) S:O(N), bottom up iterative vector tabulation T:O(N^2) S:O(N), Greedy BFS curMax nextMax T:O(N) S:O(1)|
|15★|46. Permutations | permutation/combination/anagrams/palindromic, swap for caching used, backtracking, push_back before pop_back after, global and local container, recursive, dfs by vec |
|16★|48. Rotate Image | 2d vector indexing, reverse up to down left to right, then swap the symmetry |
|17★|49. Group Anagrams| permutation/combination/anagrams/palindromic, hash map cache, vector instead hash map, array to str as key, sorted str as key |
|18★|53. Maximum Subarray| 2D-DP 6ways, BF two for loop all possible selection iterative start point T:O(N^2) S:O(1), take or not take, BF recursive subproblem T:O(N^2) S:O(N), recursion with hash map memoization T:O(N) S:O(N), bottom up iterative vector tabulation T:O(N) S:O(N), Kadane's algo T:O(N) S:O(1), divide and conquer|
|19★|54. Spiral Matrix | 2d vector indexing, two counters %2, four directions %4 |
|20★|55. Jump Game | BFS curMax nextMax, share max variable |
|21★|56. Merge Intervals | sorting, lambda compare function, two value left and right |
|22★|62. Unique Paths | 2D-DP 5ways, BF iterative BFS or recursive DFS next one T:O(2^m+n) S:O(m+n), DP recursive with hash map memoization T:O(m*n) S:O(m*n), DP iterative with tabulation T:O(n*m) S:O(m*n), space optimization instead of 2d array using one or two 1d vector T:O(n*m) S:O(m), left is left top is cur then new cur is cur, permutation and combination math |
|23|64. Minimum Path Sum | 2D-DP 4ways, BF iterative BFS or recursive DFS next one T:O(2^m+n) S:O(m+n), DP recursive with hash map memoization T:O(m*n) S:O(m*n), DP iterative with tabulation T:O(m*n) S:O(m*n), space optimization instead of 2d array using one or two 1d vector T:O(m*n) S:O(m), left is left top is cur then new cur is cur | 
|24|72. Edit Distance | 2D-DP 4ways, two pointers on each up and down recursive next one, BF recursive subproblem T:O(3^m+n) S:O(m+n), DP recursive with hash map memoization T:O(m*n) S:O(m*n), DP iterative with tabulation T:O(m*n) S:O(m*n), space optimization instead of 2d array using one or two 1d vector T:O(m*n) S:O(m), left is left top is cur then new cur is cur |
|25★|73. Set Matrix Zeroes| 2d vector indexing, in place store |
|26|74. Search a 2D Matrix | binary search, % for colId, / for rowId, mid mid seperate if-else |
|27★|75. Sort Colors | two pointers left and right, dutch partitioning problem, three pointers, swap |
|28★|78. Subsets| permutation/combination/anagrams/palindromic, recursive subproblem, backtracking, push_back before pop_back after, with DFS, iterative push_back to cache 2^n combinations, bit operation, shift>><< for 2^n |
|29★|79. Word Search | iterative start point, in place store, DFS with marker memoization M:O(m\*n*4^k) S:O(k) | 
|30★|98. Validate Binary Search Tree | 94. Binary Tree Inorder Traversal, with prev cache |
|31★|102. Binary Tree Level Order Traversal| BFS iterative with queue, DFS recursive childnode with height propagation |
|32★|105. Construct Binary Tree from Preorder and Inorder Traversal | recursive subproblem, preorder shows next root, inorder shows left and right |
|33|114. Flatten Binary Tree to Linked List | BFS iterative with queue, DFS recursive childnode, preorder in left-right tree, postorder in right-left tree, swap, subtree moving | 
|34★|128. Longest Consecutive Sequence | sorted vector, check left and right see if I'm a bridge, hash map for caching subproblem sum, not neccessary to update all |
|35★|131. Palindrome Partitioning | backtracking, push_back before pop_back after, global and local container, left and right pointers, DP, recursive subproblem, take or not take for 2^n |  
|36★|138. Copy List with Random Pointer| hash map for one-to-one old new node mapping, deep copy, in place store the the next node, swap with next preserved |
|37★|139. Word Break| 1D-DP 4ways, iterative start point, check left elements leave right subproblem, BF recursive subproblem T:O(N!) S:O(N), recursion with hash map memoization T:O(N^2) S:O(N), bottom up iterative vector tabulation T:O(N^2) S:O(N), temp prev and curr swap, space T:O(N^2) S:O(1) | 
|38|142. Linked List Cycle II | Floyd Cycle detection, two pointers faster and slow (hit with while), head and slow same pace find start, 2(x+y)-(x+y) = nC |
|39★|146. LRU Cache| data sturcture design, double link list std::list, std::splice, iterator, hash map|
|40★|148. Sort List | merge sort, two pointer, nlogn |
|41★|152. Maximum Product Subarray | 2D-DP, Kadane's algo, 53. Maximum Subarray, 關鍵不同是要避開短期相乘是負的 但之後可能會正回來的可能 greedy求max不可行 相乘時用max(1,)來跟前一次比也很屌 |
|42|153. Find Minimum in Rotated Sorted Array| binary search find sep |
|43★|155. Min Stack| data sturcture design, stack, paired min val, pop and push together |
|44★|189. Rotate Array| % loop for overflow, reverse triple, |
|45★|198. House Robber| 1D-DP 4ways, take or not take, BF recursive subproblem, T:O(2^N) S:O(N), top down recursion with hash map memoization T:O(N) S:O(N), bottom up iterative with tabulation T:O(N) S:O(N), space optimization T:O(N) S:O(1) cur prev preprev |
|46|199. Binary Tree Right Side View| 102. Binary Tree Level Order Traversal, left to right accumulated, right to left validated |
|47★|200. Number of Islands| undirectional graph, find connected component, DFS/BFS iterative, marked or erase visisted |
|48★|207. Course Schedule| directional graph, graph cycle detection, DFS recursive, marked visisted/processed |
|49★|208. Implement Trie (Prefix Tree) | data sturcture design, BF two unordered_set, linked list or tree like stringstream/nodestream | 
|50★|215. Kth Largest Element in an Array | sorting, lambda function, Heap (priority_queue), quicksort selection | 
|51★|230. Kth Smallest Element in a BST | 102. Binary Tree Level Order Traversal |
|52★|236. Lowest Common Ancestor of a Binary Tree | DFS, overwritten return | 
|53★|238. Product of Array Except Self | BF two for loop N^2, prefix and suffix accumlated | 
|54★|240. Search a 2D Matrix II | binary search smaller one, from top right go left and down |
|55★|287. Find the Duplicate Number| BF two for loop N^2, hash map, sorting, Floyd Cycle detection, two pointers faster and slow (hit with while), head and slow same pace find start, 2(x+y)-(x+y) = nC |
|56★|300. Longest Increasing Subsequence| 2D-DP 5ways, take or not take, BF recursive subproblem T:O(2^N) S:O(N), recursion with hash map memoization T:O(N^2) S:O(N^2), bottom up iterative vector tabulation T:O(N^2) S:O(N^2), space optimization 1D vector accumulated two for loop iterative start point and |57|prev point T:O(N^2) S:O(N), binary search |
|58★|322. Coin Change| 1D-DP 3ways, take or not take, iterative try each element, row is curIdx, col is sum, BF recursive subproblem T:O(N^N) S:O(K), recursion with hash map memoization T:O(K) S:O(K), bottom up iterative vector tabulation T:O(K) S:O(K) |
|59★|347. Top K Frequent Elements | hash map (unordered_map), BST (multimap), Heap (priority_queue), O(n log(n-k)), quicksort selection |
|60|394. Decode String | stack, current accumulation |
|61|416. Partition Equal Subset Sum | 2D-DP 5ways, take or not take, iterative try each element, row is curIdx, col is sum, BF recursive subproblem T:O(2^N) S:O(N), recursion with hash map memoization T:O(N*sum) S:O(N*sum), iterative vector tabulation T:O(N*sum) S:O(N*sum), space optimization T:O(N*sum) S:O(sum), bitmask |
|62|438. Find All Anagrams in a String| sliding window, vector instead hash map, left minus right plus, compare the window at once |
|63|560. Subarray Sum Equals K | fake sliding window, BF two for loop N^2, prefix sum (aacumulated sum array), hash map | 
|64|567. Permutation in String| sliding window, vector instead hash map, left minus right plus, compare the window at once |
|65|739. Daily Temperatures | stack, pause someone |
|66|994. Rotting Oranges | BFS iterative with queue, undirectional graph, matrix, 2d vector indexing, in place store |
|67|1143. Longest Common Subsequence | DP |

## 1.3.Top 100 Liked - Hard (★ is also top interview)
|count|problem|remark|
|--|--|--|
|1★|4. Median of Two Sorted Arrays
|2★|23. Merge k Sorted Lists
|3|25. Reverse Nodes in k-Group
|4|32. Longest Valid Parentheses
|5★|41. First Missing Positive
|6★|42. Trapping Rain Water
|7|51. N-Queens
|8★|76. Minimum Window Substring
|9★|84. Largest Rectangle in Histogram
|10★|124. Binary Tree Maximum Path Sum
|11★|239. Sliding Window Maximum
|12★|295. Find Median from Data Stream

## 1.4.Top Interview - Easy (w/o top 100 liked)
|count|problem|remark|
|--|--|--|
|1|26. Remove Duplicates from Sorted Array| BF hasp map space O(N), two pointers cur and accumulated space O(1) |
|2|28. Find the Index of the First Occurrence in a String| BF two for loop searching time O(N^2) |
|3|66. Plus One| for loop, time O(N), decimal, carry |
|4|69. Sqrt(x)| math: Newton's method, math, binary search smaller one |
|5|88. Merge Sorted Array| two pointers on each up and down, array/vector, time O(M+N) |
|6|108. Convert Sorted Array to Binary Search Tree| pick mid recursive childnode, binary search like |
|7|125. Valid Palindrome|BF stack space O(N), two pointers left and right space O(1), time O(N), isalnum, ascii |
|8|163. Missing Ranges| N/A |
|9|171. Excel Sheet Column Number| for loop, time O(N), ascii |
|10|190. Reverse Bits| bit operation, OR\|= addition, shift>><<, AND&1 mask last digit |
|11|191. Number of 1 Bits| bit operation, shift>><<, AND&1 mask last digit|
|12|202. Happy Number| Floyd Cycle detection, two numbers faster and slow (hit with while), decimal, %10 last digit, shift /10 |
|13|217. Contains Duplicate| BF two for loop time O(N^2), BF hash map space O(N), vector instead hash map, sorted time O(nlogn) |
|14|242. Valid Anagram| BF hash map space O(N), vector instead hash map, sorted time O(nlogn) |
|15|268. Missing Number| BF hash map space O(N), vector instead hash map, sorted time O(nlogn), bit operation, XOR^=, space O(1), binary search shorter, sum=(head+tail)/2 |
|16|326. Power of Three| iterative or recursive %3 last digit, shift /3, cache all into vector/hash map to lookup, 3^n % target == 0 |
|17|344. Reverse String| temp prev and curr swap, two pointers left and right, recursive childnode|
|18|350. Intersection of Two Arrays II| BF two for loop time O(N^2), BF hash map space O(N), sorted time O(nlogn), two pointers on each up and down|
|19|387. First Unique Character in a String| BF two for loop time O(N^2), BF hash map space O(N) |
|20|412. Fizz Buzz| for loop with multiple cases if, % or count or indexing |

## 1.5.Top Interview - Medium (w/o top 100 liked)
|count|problem|remark|
|--|--|--|
|1|7. Reverse Integer
|2|8. String to Integer (atoi)
|3|29. Divide Two Integers|
|4|36. Valid Sudoku
|5|38. Count and Say
|6|50. Pow(x, n)
|7|91. Decode Ways
|8|103. Binary Tree Zigzag Level Order Traversal
|9|116. Populating Next Right Pointers in Each Node
|10|122. Best Time to Buy and Sell Stock II
|11|130. Surrounded Regions
|12|134. Gas Station
|13|150. Evaluate Reverse Polish Notation
|14|162. Find Peak Element
|15|166. Fraction to Recurring Decimal
|16|172. Factorial Trailing Zeroes
|17|179. Largest Number
|18|204. Count Primes
|19|210. Course Schedule II
|20|227. Basic Calculator II
|21|237. Delete Node in a Linked List
|22|251. Flatten 2D Vector
|23|253. Meeting Rooms II
|24|277. Find the Celebrity
|25|279. Perfect Squares
|26|285. Inorder Successor in BST
|27|289. Game of Life
|28|308. Range Sum Query 2D - Mutable
|29|324. Wiggle Sort II
|30|328. Odd Even Linked List
|31|334. Increasing Triplet Subsequence
|32|340. Longest Substring with At Most K Distinct Characters
|33|341. Flatten Nested List Iterator
|34|348. Design Tic-Tac-Toe
|35|371. Sum of Two Integers
|36|378. Kth Smallest Element in a Sorted Matrix
|37|380. Insert Delete GetRandom O(1)
|38|384. Shuffle an Array
|39|395. Longest Substring with At Least K Repeating Characters
|40|454. 4Sum II

## 1.6.Top Interview - Hard (w/o top 100 liked)
|count|problem|remark|
|--|--|--|
|1|10. Regular Expression Matching
|2|44. Wildcard Matching
|3|127. Word Ladder
|4|140. Word Break II
|5|149. Max Points on a Line
|6|212. Word Search II
|7|218. The Skyline Problem
|8|269. Alien Dictionary
|9|297. Serialize and Deserialize Binary Tree
|10|315. Count of Smaller Numbers After Self
|11|329. Longest Increasing Path in a Matrix

## 1.7.Others
|count|problem|remark|
|--|--|--|
|1| 144. Binary Tree Preorder Traversal | DFS recursive childnode, DFS iterative with stack, push_back before going to children (left then right) in if != nullptr |
|2| 145. Binary Tree Postorder Traversal | DFS recursive childnode, DFS iterative with stack, insert_front before going to children (right then left) in if != nullptr, or optionally go right if last node is not right |
|3| 76. Minimum Window Substring| sliding window |
|4| 622. Design Circular Queue | data sturcture design, ring buffer |
|5| 460. LFU Cache | data sturcture design, |

# 2.Skills
* [2.1.Hashtags](cheatsheet_leetcode.md#21hashtags)
* [2.2.Examples](cheatsheet_leetcode.md#22examples)
* [2.3.Templates](cheatsheet_leetcode.md#23templates)

## 2.1.Hashtags

| Tags | Details |
-------|---------|
| Array, Matrix, String, Two Pointers, Sorting, Swap, Reverse | processing sequential data |
| Mod and Divided                                    | moving digits on integer by / % |
| Bit Manipulation, Bitmask                          | moving digits on binaries by << >>, check redundancy by ^= |
| Stack, Queue, HashMap, Heap, BST                   | caching data: std::stack, std::queue, std::priority_queue, std::unordered_map, std::map, std::unordered_multimap, std::multimap | 
| Linked List, Slow and Fast Pointers                | cycle detecting, cycle start point locating, mid of linked list |
| Brute-force: Recursive Func, Iterative For loop         | collecting all combination |
| Binary Tree, Tree Traversal                                 | pre-order, in-order, post-order, level-order |
| Depth-First Search (DFS), Breadth-First Search(BFS)          | recursive or iterative |
| Directional Graph, Undirectional Graph, Connected Component  | visited, processed |
| Dynamic Programming (DP) | 5ways: BF, REC, REC_MEM, ITER_TAB, SPACE_OPT |
| Backtracking             | push_back and pop_back |
| Binary Search             | left mid left+1, right mid right-1, left mid left+1 right-1 equal return | 
| Sliding Window            | left minus right plus |
| Divide and Conquer        | left-mid and mid-right subproblem |
| Greedy | put the rocks first then the sands |
| Math   | permutation and combination, prime, sqrt | 

## 2.2.Examples
### Array, Matrix, String, Sorting, Two Pointers, Swap
- [344. Reverse String](https://leetcode.com/problems/reverse-string/)
```cpp
void reverseString(vector<char>& s) {
    int i = 0;
    int j = s.size() - 1;
    while (i < j) {
        char temp = s[i];
        s[i] = s[j];
        s[j] = temp;
        i++;
        j--;
    }
}
```
- [136. Single Number](https://leetcode.com/problems/single-number/description/)
```cpp
int singleNumber(vector<int>& nums) { 
   sort(nums.begin(),nums.end());
    for(int i=1;i<nums.size();i+=2)
    {
        if(nums[i]!=nums[i-1])
            return nums[i-1];
    }
    return nums[nums.size()-1];
}
```

### Mod and Divided
- [7. Reverse Integer](https://leetcode.com/problems/reverse-integer/description/)
```cpp
int reverseInteger(int num) {
    int reversed = 0;
    while (num != 0) {
        int digit = num % 10;        // Get the last digit
        reversed = reversed * 10 + digit; // Shift reversed and add the new digit
        num /= 10;                   // Remove the last digit from the number
    }   
    return reversed;
}
```
- [cplusplus rand](https://cplusplus.com/reference/cstdlib/rand/)
```cpp
#include <time.h>
srand (time(NULL));
// int rand (void); Returns a pseudo-random integral number in the range between 0 and RAND_MAX.
int v1 = rand() % 100;         // v1 in the range 0 to 99
int v2 = rand() % 100 + 1;     // v2 in the range 1 to 100
int v3 = rand() % 30 + 1985;   // v3 in the range 1985-2014 
float v4 = static_cast<float>(rand()) / RAND_MAX * 2.f; // v4 in the range 0.0 to 2.0
```

### Bit Manipulation, Bitmask
- [190. Reverse Bits](https://leetcode.com/problems/reverse-bits/)
```cpp
uint32_t reverseBits(uint32_t n) {
    uint32_t sum = 0;
    for (int i=0; i<32; i++)
    {
        uint32_t lastDigit = n&1;
        n >>= 1;
        sum <<= 1;
        sum |= lastDigit;
    }
    return sum;
}
```
- [7. Reverse Integer](https://leetcode.com/problems/reverse-integer/description/)
```cpp
int singleNumber(vector<int>& nums) { 
   int ans=0;
   for(auto x:nums) ans^=x;
   return ans;
}
```
- [Alternative operator representations](https://en.cppreference.com/w/cpp/language/operator_alternative)
```cpp
# bitand, and, and_eq: &, &&, &=
# bitor, or, or_eq: |, ||, |=
# not, not_eq: ~, ~=
# xor, xor_eq: |, |=
void bitManipulation() {
    int x = 5, y = 3; // x = 0101, y = 0011
    std::cout << "AND: " << (x & y) << ", OR: " << (x | y) << "\n";
    std::cout << "XOR: " << (x ^ y) << ", NOT x: " << (~x) << "\n";
}
```

### Stack, Queue, Hash Table
- Hash table: [1. Two Sum](https://leetcode.com/problems/two-sum/), [15. 3Sum](https://leetcode.com/problems/3sum/)
```cpp
vector<int> twoSum(vector<int>& nums, int target) {
    unordered_map<int, int> numMap;
    int n = nums.size();

    for (int i = 0; i < n; i++) {
        int complement = target - nums[i];
        if (numMap.count(complement)) {
            return {numMap[complement], i};
        }
        numMap[nums[i]] = i;
    }

    return {}; // No solution found
}
```
- Stack: [20. Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)
```cpp
bool isValidParentheses(string s) {
    stack<char> st;
    for (char c : s) {
        if (c == '(') {
            st.push(')');
        } else if (c == '{') {
            st.push('}');
        } else if (c == '[') {
            st.push(']');
        } else if (st.empty() || st.top() != c) {
            return false;
        } else {
            st.pop();
        }
    }
    return st.empty();
}
```
### Linked List, Slow and Fast Pointers
- [141. Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/) 
```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
// while two pointers fast and slow hit, then return true
bool hasCycle(ListNode *head) {
    ListNode *fast = head;
    ListNode *slow = head;    
    while(fast != NULL && fast ->next != NULL)
    {
        fast = fast->next->next;
        slow = slow->next;
        if(fast == slow)
            return true;
    }
    return false;
}
```
- [142. Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/description/)
```cpp
// while two pointers fast and slow hit, then head and slow go at same pace find start because 2(x+y)-(x+y) = nC 
ListNode *detectCycle(ListNode *head) {
    ListNode *fast = head;
    ListNode *slow = head;
    while (fast != nullptr && fast->next != nullptr)
    {
        fast = fast -> next -> next;
        slow = slow -> next;
        if (slow == fast) break;
    }
    if (fast == nullptr || fast->next == nullptr) return nullptr;
    while (head!=slow)
    {
        head = head -> next;
        slow = slow -> next;
        if (head == slow) break;
    }
    return head;
}
```
- [876. Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/description/)
```cpp
// while two pointers fast hits the end, then slow is at the mid.
ListNode *findMid(ListNode *head) {
    ListNode *slow = head, *fast = head, *mid;
    while (fast && fast->next)
        slow = slow->next, fast = fast->next->next;
    mid = slow;
    return mid;
}
```
### Brute-force: Recursive Func, Iterative For loop
- Iterative For loop: [53. Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)
```cpp
int maxSubArray(vector<int>& nums) {
    int sum = INT_MIN;
    int size = nums.size();
    for(int len = 1; len <= size ; len++){
        for(int start = 0; start <= (size - len) ; start++){
            int value = 0;
            for(int i = start ; i <= (start + len - 1) ; i++){
                value += nums[i];
            }
    	    sum = max(value, sum);
        }
    }
}
int maxSubArray(vector<int>& nums) {
    int sum = INT_MIN;
    int size = nums.size();
    for(int start = 0; start < size ; start++){            
        for(int len = 1; len <= (size - start)  ; len++){
            int value = 0;
            for(int i = start ; i < (start + len) ; i++){
                value += nums[i];
            }
            sum = max(value, sum);
        }
    }
}
int maxSubArray(vector<int>& nums) {
    int sum = INT_MIN;
    int size = nums.size();
    for(int len = 1; len <= size ; len++){            
        for(int left = 0; left <= (size - len); left++){
            for(int right = left ; right < left + len ; right++){
                    value += nums[right];
            }
            sum = max(value, sum);
        }
    }
}
int maxSubArray(vector<int>& nums) {
    int sum = INT_MIN;
    int size = nums.size();
    for(int left = 0; left < size ; left++){
        for(int right = left; right < size  ; right++){
            for(int i = left ; i <= right ; i++){
                    value += nums[i];
            }
            sum = max(value, sum);
        }
    }
}
int maxSubArray(vector<int>& nums) {    
    return solve(nums, 0, false);
}
int solve(vector<int>& A, int i, bool mustPick) {
    // our subarray must contain atleast 1 element. If mustPick is false at end means no element is picked and this is not valid case
    if(i >= size(A)) return mustPick ? 0 : -1e5;       
    if(mustPick)
        return max(0, A[i] + solve(A, i+1, true));                  // either stop here or choose current element and recurse
    return max(solve(A, i+1, false), A[i] + solve(A, i+1, true));   // try both choosing current element or not choosing
}
```
- Recursive Func: [509. Fibonacci Number](https://leetcode.com/problems/fibonacci-number), or [Factorial](https://www.geeksforgeeks.org/program-for-factorial-of-a-number/)
```cpp
int fib(int n) {
    if(n==0) return 0;
    if(n==1) return 1;
    return fib(n-1)+fib(n-2);
}
```

### Binary Tree, Tree Traversal
- [145. Binary Tree Postorder Traversal](https://leetcode.com/problems/binary-tree-postorder-traversal/), [144. Binary Tree Preorder Traversal](https://leetcode.com/problems/binary-tree-preorder-traversal/), [94. Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/)
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */

// Pre-order traversal (root -> left -> right)
void preOrder(TreeNode* root) {
    if (!root) return;
    cout << root->val << " ";
    preOrder(root->left);
    preOrder(root->right);
}

// In-order traversal (left -> root -> right)
void inOrder(TreeNode* root) {
    if (!root) return;
    inOrder(root->left);
    cout << root->val << " ";
    inOrder(root->right);
}

// Post-order traversal (left -> right -> root)
void postOrder(TreeNode* root) {
    if (!root) return;
    postOrder(root->left);
    postOrder(root->right);
    cout << root->val << " ";
}
```
- [102. Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)
```cpp
// Level-order traversal (Breadth-First Search)
void levelOrder(TreeNode* root) {
    if (!root) return; // no null node inside queue
    queue<TreeNode*> q;
    q.push(root);
    while (!q.empty()) {
        TreeNode* current = q.front();
        q.pop();
        cout << current->val << " ";
        if (current->left) q.push(current->left);
        if (current->right) q.push(current->right);
    }
}
vector<vector<int>> result;
printLevel(result, root, 1);
void printLevel(TreeNode* curNode, int curlevel) {
    if (!curNode) return;
    if (curlevel>result.size()) result.push_back({});
    result[curlevel-1].push_back(curNode->val);
    printLevel(curNode->left, curlevel + 1);
    printLevel(curNode->right, curlevel + 1);
}
```
- [104. Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)
```cpp
int maxDepth(TreeNode* root) {
    if(!root) return 0;
    int maxLeft = maxDepth(root->left);
    int maxRight = maxDepth(root->right);
    return max(maxLeft, maxRight)+1;
}
```
### Dynamic Programming (DP)
- [70. Climbing Stairs](https://leetcode.com/problems/climbing-stairs/description/), or [user Abhishek](https://leetcode.com/u/archit91/)
```cpp
int fibBF(int n) {
    if (n <= 1) return n;
    return fibBF(n - 1) + fibBF(n - 2);
}

int fibREC_MEM(int n, std::vector<int> &memo) {
    if (n <= 1) return n;
    if (memo[n] != -1) return memo[n];
    return memo[n] = fibREC_MEM(n - 1, memo) + fibREC_MEM(n - 2, memo);
}

int fibITER_TAB(int n) {
    if (n <= 1) return n;
    std::vector<int> dp(n + 1);
    dp[0] = 0; dp[1] = 1;
    for (int i = 2; i <= n; i++) dp[i] = dp[i - 1] + dp[i - 2];
    return dp[n];
}

int fibSPACE_OPT(int n) {
    if (n <= 1) return n;
    int a = 0, b = 1, c;
    for (int i = 2; i <= n; i++) {
        c = a + b;
        a = b;
        b = c;
    }
    return b;
}
```
### Backtracking
- [39. Combination Sum](https://leetcode.com/problems/combination-sum/description/)
```cpp
vector<vector<int>> output; 
vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
    vector<int> curVec;
    combinationSum(candidates, target, 0, curVec);
    return output;
}
void combinationSum(vector<int>& candidates, int target, int start, vector<int> curVec) 
{
    if (target == 0)
        output.push_back(curVec);
    for (int i = start; i<candidates.size(); i++)
    {
        if (target-candidates[i] >= 0)
        {
            curVec.push_back(candidates[i]);
            combinationSum(candidates, target-candidates[i], i, curVec);
            curVec.pop_back();
        }
    }
}
```

### Binary Search
- [704. Binary Search](https://leetcode.com/problems/binary-search/description/) left mid or right mid
```cpp
// left mid
int search(vector<int>& nums, int target) {
    int left = 0, right = nums.size()-1;
    while (left < right) // equal is end
    {
        const int mid = (left+right)/2;
        if (nums[mid] < target)
            left = mid+1;
        else
            right = mid;
    }
    return nums[right] == target ? right : -1;
}

// right mid
int search(vector<int>& nums, int target) {
    int left = 0, right = nums.size()-1;
    while (left < right) // equal is end
    {
        const int mid = (left+right+1)/2;
        if (nums[mid] > target)
            right = mid-1;
        else
            left = mid;
    }
    return nums[left] == target ? left : -1;
}
```
- [69. Sqrt(x)](https://leetcode.com/problems/sqrtx/description/) on mid
```cpp
// on mid
int search(vector<int>& nums, int target) {
    int left = 0, right = nums.size()-1;
    while (left <= right) // after equal then end
    {
        const int mid = left + (right-left)/2;
        if (nums[mid] < target)
            left = mid+1;
        else if (nums[mid] > target)
            right = mid-1;
        else
            return mid;
    }
    return -1; // or return right; (lower) // or return left; (higher)
}
```

### Sliding windows
- [567. Permutation in String](https://leetcode.com/problems/permutation-in-string/description/)
```cpp
// Input: s1 = "ab", s2 = "eidbaooo"
// Output: true
// Explanation: s2 contains one permutation of s1 ("ba").
bool checkInclusion(string s1, string s2) {
    int s1Size = s1.size(), s2Size = s2.size();
    if(s1Size > s2Size) return false;
    
    vector<int> s1FixedWindow(26,0);
    vector<int> s2Seq(26,0);
    
    for(int i=0;i<s1Size;i++){
        s1FixedWindow[s1[i]-'a']++;
        s2Seq[s2[i]-'a']++;
    }
    
    if(s1FixedWindow == s2Seq) return true;
    
    for(int i=s1Size;i<s2Size;i++){
        s2Seq[s2[i-s1Size] - 'a']--;
        s2Seq[s2[i] - 'a']++;
        if(s2Seq == s1FixedWindow) return true;
    }
    return false;
}
```
### Divide and Conquer
- [53. Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)
```cpp
int maxDivideConquer(std::vector<int> &nums, int left, int right) {
    if (left == right) return nums[left];
    int mid = left + (right - left) / 2;
    return std::max(maxDivideConquer(nums, left, mid),
                    maxDivideConquer(nums, mid + 1, right));
}
```
### Greedy
- [322. Coin Change](https://leetcode.com/problems/coin-change/description/) warning!! greedy does not work in this problem if there is no ensurement that the number can be changed 100% anyway
```cpp
int coinChange(std::vector<int> &coins, int amount) {
    std::sort(coins.rbegin(), coins.rend());
    int count = 0;
    for (int coin : coins) {
        if (amount == 0) break;
        count += amount / coin;
        amount %= coin;
    }
    return (amount == 0) ? count : -1;
}
```
### Math
- [204. Count Primes](https://leetcode.com/problems/count-primes/description/)
```cpp
bool isPrime(int n) {
    if (n <= 1) return false;
    for (int i = 2; i * i <= n; i++) {
        if (n % i == 0) return false;
    }
    return true;
}
```

## 2.3.Templates
- Abhishek's solutions from BF to Optimal: https://leetcode.com/u/archit91/
- Backtracing Template: https://leetcode.com/problems/palindrome-partitioning/discuss/182307/Java%3A-Backtracking-Template-General-Approach
- Binary Search 101 O(logN): https://leetcode.com/problems/binary-search/discuss/423162/Binary-Search-101
- Sliding Window Template: https://leetcode.com/problems/find-all-anagrams-in-a-string/discuss/92007/Sliding-Window-algorithm-template-to-solve-all-the-Leetcode-substring-search-problem.
- Iterative binary tree traversal (pre, post, in-order): https://leetcode.com/problems/binary-tree-postorder-traversal/discuss/45551/Preorder-Inorder-and-Postorder-Iteratively-Summarization
- Recursive binary tree traversal (pre, post, in-order): https://leetcode.com/problems/binary-tree-inorder-traversal/discuss/283746/All-DFS-traversals-(preorder-inorder-postorder)-in-Python-in-1-line
- 1D DP N! to N^2: https://leetcode.com/problems/jump-game-ii/discuss/1192401/Easy-Solutions-w-Explanation-or-Optimizations-from-Brute-Force-to-DP-to-Greedy-BFS
- 2D DP N^2 to N: https://leetcode.com/problems/maximum-subarray/discuss/1595195/C%2B%2BPython-7-Simple-Solutions-w-Explanation-or-Brute-Force-%2B-DP-%2B-Kadane-%2B-Divide-and-Conquer
- 2D DP 2^m+n to m*n: https://leetcode.com/problems/unique-paths/discuss/1581998/C%2B%2BPython-5-Simple-Solutions-w-Explanation-or-Optimization-from-Brute-Force-to-DP-to-Math
- Kadane's Algorithm O(N)O(1) (maxCur, maxSoFar, max(0, maxCur), reset if maxCur is neg): https://leetcode.com/problems/best-time-to-buy-and-sell-stock/discuss/39038/Kadane's-Algorithm-Since-no-one-has-mentioned-about-this-so-far-%3A)-(In-case-if-interviewer-twists-the-input) 
- Floyd Cycle Detection Algorithm: https://leetcode.com/problems/linked-list-cycle-ii/solutions/1701128/c-java-python-slow-and-fast-image-explanation-beginner-friendly/

# 3.Complexity
## 3.1.Order
- n! > 2^n > n^2 > log n > n > log n > 1
- ![圖片](https://github.com/user-attachments/assets/decb318f-2588-4043-83bc-a509ab38e657)
## 3.2.How to compute O(log N)?
- Binary Search Example
  - In **binary search**, we repeatedly split the search space in half until we either find the target element or have no elements left to search.
  - If we start with N elements, after one step, we're down to N/2, after two steps N/4, and so on, until we are left with 1 element.
  - The question is: how many times can we halve the number N until we're left with 1? This number is log2(N), because:
    - N / 2^k = 1, where k is the number of steps
    - log2(N) = k
    - Thus, binary search runs in O(log N) time.

- Binary Tree Example
  - In a **balanced binary tree**, every node has at most two children. The number of nodes doubles as we move down each level of the tree.
  - At depth 0, there is 1 node (the root). At depth 1, there are 2 nodes. At depth 2, there are 4 nodes, and so on. For depth h, there are 2^h nodes.
  - If the tree has N nodes, the height h of the tree is approximately log2(N), because:
    - 2^h = N
    - h = log2(N)
    - Since searching, inserting, or deleting a node involves traversing from the root to a leaf, and the number of steps to do so is proportional to the height of the tree, the time complexity is O(log N).
