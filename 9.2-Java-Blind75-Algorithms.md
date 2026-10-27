# Blind 75 LeetCode Solutions in Java: A Beginner-Friendly Architectural Reference

Welcome to the comprehensive, beginner-friendly guide to mastering the **Blind 75** algorithms and data structures problems in **Java**.

Whether you are preparing for technical software engineering interviews or strengthening your core computer science fundamentals, this guide is written to make complex algorithmic patterns easy to understand, step by step. We avoid confusing jargon wherever possible, explain the core "Aha!" insights in plain English, and provide fully commented, clean Java code that you can easily follow and run.

Every problem is organized into six structured parts:
- **Problem Introduction & Example**: A clear explanation of what the problem is asking in simple terms, accompanied by concrete sample inputs, outputs, and edge cases.
- **High-Level Solution Intuition**: The conceptual breakthrough behind the optimal solution, explaining why the initial brute-force approach is too slow and how the optimal pattern simplifies the problem.
- **Complexity Analysis**: A beginner-friendly breakdown of Big-O Time Complexity (how execution time scales as input size grows) and Space Complexity (how much additional memory is allocated).
- **Pseudocode & High-Level Skeleton (ASCII Diagram)**: A visual blueprint and ASCII flowchart that maps out the program logic before writing actual Java code.
- **Java Program**: Idiomatic, clean, and thoroughly commented Java code designed for readability, with descriptive variable names and helpful in-line explanations.
- **Example Trace & Data Structure Rationale**: A step-by-step walkthrough of the program state on a concrete example, followed by a dedicated breakdown of why specific data structures were chosen over other alternatives.

---

## Table of Contents

- [Category 1: Arrays & Hashing](#category-1-arrays--hashing)
  - [1. Two Sum](#1-two-sum-leetcode-1)
  - [2. Contains Duplicate](#2-contains-duplicate-leetcode-217)
  - [3. Valid Anagram](#3-valid-anagram-leetcode-242)
  - [4. Group Anagrams](#4-group-anagrams-leetcode-49)
  - [5. Top K Frequent Elements](#5-top-k-frequent-elements-leetcode-347)
  - [6. Product of Array Except Self](#6-product-of-array-except-self-leetcode-238)
  - [7. Longest Consecutive Sequence](#7-longest-consecutive-sequence-leetcode-128)
  - [8. Encode and Decode Strings](#8-encode-and-decode-strings-leetcode-271)
- [Category 2: Two Pointers, Sliding Window & Stack](#category-2-two-pointers-sliding-window--stack)
  - [9. Valid Palindrome](#9-valid-palindrome-leetcode-125)
  - [10. 3Sum](#10-3sum-leetcode-15)
  - [11. Container With Most Water](#11-container-with-most-water-leetcode-11)
  - [12. Best Time to Buy and Sell Stock](#12-best-time-to-buy-and-sell-stock-leetcode-121)
  - [13. Longest Substring Without Repeating Characters](#13-longest-substring-without-repeating-characters-leetcode-3)
  - [14. Longest Repeating Character Replacement](#14-longest-repeating-character-replacement-leetcode-424)
  - [15. Minimum Window Substring](#15-minimum-window-substring-leetcode-76)
  - [16. Valid Parentheses](#16-valid-parentheses-leetcode-20)
- [Category 3: Binary Search & Linked List](#category-3-binary-search--linked-list)
  - [17. Search in Rotated Sorted Array](#17-search-in-rotated-sorted-array-leetcode-33)
  - [18. Find Minimum in Rotated Sorted Array](#18-find-minimum-in-rotated-sorted-array-leetcode-153)
  - [19. Reverse Linked List](#19-reverse-linked-list-leetcode-206)
  - [20. Merge Two Sorted Lists](#20-merge-two-sorted-lists-leetcode-21)
  - [21. Reorder List](#21-reorder-list-leetcode-143)
  - [22. Remove Nth Node From End of List](#22-remove-nth-node-from-end-of-list-leetcode-19)
  - [23. Linked List Cycle](#23-linked-list-cycle-leetcode-141)
  - [24. Merge k Sorted Lists](#24-merge-k-sorted-lists-leetcode-23)
- [Category 4: Trees & Tries](#category-4-trees--tries)
  - [25. Invert Binary Tree](#25-invert-binary-tree-leetcode-226)
  - [26. Maximum Depth of Binary Tree](#26-maximum-depth-of-binary-tree-leetcode-104)
  - [27. Same Tree](#27-same-tree-leetcode-100)
  - [28. Subtree of Another Tree](#28-subtree-of-another-tree-leetcode-572)
  - [29. Lowest Common Ancestor of a Binary Search Tree](#29-lowest-common-ancestor-of-a-binary-search-tree-leetcode-235)
  - [30. Binary Tree Level Order Traversal](#30-binary-tree-level-order-traversal-leetcode-102)
  - [31. Validate Binary Search Tree](#31-validate-binary-search-tree-leetcode-98)
  - [32. Kth Smallest Element in a BST](#32-kth-smallest-element-in-a-bst-leetcode-230)
  - [33. Construct Binary Tree from Preorder and Inorder Traversal](#33-construct-binary-tree-from-preorder-and-inorder-traversal-leetcode-105)
  - [34. Binary Tree Maximum Path Sum](#34-binary-tree-maximum-path-sum-leetcode-124)
  - [35. Serialize and Deserialize Binary Tree](#35-serialize-and-deserialize-binary-tree-leetcode-297)
  - [36. Implement Trie (Prefix Tree)](#36-implement-trie-prefix-tree-leetcode-208)
  - [37. Design Add and Search Words Data Structure](#37-design-add-and-search-words-data-structure-leetcode-211)
  - [38. Word Search II](#38-word-search-ii-leetcode-212)
- [Category 5: Heap, Backtracking & Graphs](#category-5-heap-backtracking--graphs)
  - [39. Find Median from Data Stream](#39-find-median-from-data-stream-leetcode-295)
  - [40. Combination Sum](#40-combination-sum-leetcode-39)
  - [41. Word Search](#41-word-search-leetcode-79)
  - [42. Number of Islands](#42-number-of-islands-leetcode-200)
  - [43. Clone Graph](#43-clone-graph-leetcode-133)
  - [44. Pacific Atlantic Water Flow](#44-pacific-atlantic-water-flow-leetcode-417)
  - [45. Course Schedule](#45-course-schedule-leetcode-207)
  - [46. Number of Connected Components in an Undirected Graph](#46-number-of-connected-components-in-an-undirected-graph-leetcode-323)
  - [47. Graph Valid Tree](#47-graph-valid-tree-leetcode-261)
  - [48. Alien Dictionary](#48-alien-dictionary-leetcode-269)
- [Category 6: Intervals & Matrix](#category-6-intervals--matrix)
  - [49. Insert Interval](#49-insert-interval-leetcode-57)
  - [50. Merge Intervals](#50-merge-intervals-leetcode-56)
  - [51. Non-overlapping Intervals](#51-non-overlapping-intervals-leetcode-435)
  - [52. Meeting Rooms](#52-meeting-rooms-leetcode-252)
  - [53. Meeting Rooms II](#53-meeting-rooms-ii-leetcode-253)
  - [54. Set Matrix Zeroes](#54-set-matrix-zeroes-leetcode-73)
  - [55. Spiral Matrix](#55-spiral-matrix-leetcode-54)
  - [56. Rotate Image](#56-rotate-image-leetcode-48)
- [Category 7: Dynamic Programming](#category-7-dynamic-programming)
  - [57. Climbing Stairs](#57-climbing-stairs-leetcode-70)
  - [58. Coin Change](#58-coin-change-leetcode-322)
  - [59. Longest Increasing Subsequence](#59-longest-increasing-subsequence-leetcode-300)
  - [60. Word Break](#60-word-break-leetcode-139)
  - [61. House Robber](#61-house-robber-leetcode-198)
  - [62. House Robber II](#62-house-robber-ii-leetcode-213)
  - [63. Decode Ways](#63-decode-ways-leetcode-91)
  - [64. Unique Paths](#64-unique-paths-leetcode-62)
  - [65. Jump Game](#65-jump-game-leetcode-55)
  - [66. Maximum Subarray](#66-maximum-subarray-leetcode-53)
  - [67. Maximum Product Subarray](#67-maximum-product-subarray-leetcode-152)
  - [68. Palindromic Substrings](#68-palindromic-substrings-leetcode-647)
  - [69. Longest Palindromic Substring](#69-longest-palindromic-substring-leetcode-5)
  - [70. Longest Common Subsequence](#70-longest-common-subsequence-leetcode-1143)
- [Category 8: Bit Manipulation & Math](#category-8-bit-manipulation--math)
  - [71. Number of 1 Bits](#71-number-of-1-bits-leetcode-191)
  - [72. Counting Bits](#72-counting-bits-leetcode-338)
  - [73. Reverse Bits](#73-reverse-bits-leetcode-190)
  - [74. Missing Number](#74-missing-number-leetcode-268)
  - [75. Sum of Two Integers](#75-sum-of-two-integers-leetcode-371)

---


# Category 1: Arrays & Hashing

---

## 1. Two Sum (LeetCode #1)

### Problem Introduction & Example
Imagine you are given an array of integers named `nums` and a single integer called `target`. Your goal is to find the indices (the 0-based positions) of the two numbers in `nums` that add up exactly to `target`. 

You can assume that every input will have exactly one valid solution, and you are not allowed to use the same element twice (meaning you cannot pick the number at index 2 and add it to itself). The indices can be returned in any order.

- **Example**:
  - Input: `nums = [2, 7, 11, 15]`, `target = 9`
  - Output: `[0, 1]`
  - Explanation: We check pairs of numbers. Here, `nums[0] + nums[1] == 2 + 7 == 9`. Therefore, the matching indices are `0` and `1`.

### High-Level Solution Intuition
**Why the naive approach is slow**:
A beginner's first instinct is often to write two nested loops: pick the first number with an outer loop, and then scan through every remaining number with an inner loop to see if their sum equals the target. While this works, comparing every possible pair takes quadratic time—$\mathcal{O}(n^2)$—which becomes very sluggish when dealing with arrays containing tens of thousands of numbers.

**The "Aha!" Breakthrough (The Complement Technique)**:
Instead of asking *"Does any other number in the array add up with my current number to reach target?"*, we can rephrase the question algebraically:
$$\text{complement} = \text{target} - \text{currentNumber}$$
When we are standing at number `7` and our target is `9`, what we are really looking for is the missing puzzle piece: $9 - 7 = 2$.
So, as we walk through the array, we ask a quick question: *"Have we already seen the complement $2$ earlier in our walk?"*

To answer this question instantaneously, we use a **Hash Map** (in Java, a `HashMap<Integer, Integer>`). A Hash Map allows us to store each number we've encountered along with its index, and check if our needed complement exists in near-instant $\mathcal{O}(1)$ average time.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — We only need to iterate through the array of length $n$ a single time. Inside the loop, looking up whether the complement exists in our `HashMap` and inserting a new entry both take $\mathcal{O}(1)$ constant time on average. Thus, the overall running time scales linearly with the input size.
- **Space Complexity**: $\mathcal{O}(n)$ — In the worst-case scenario (for example, if the two numbers that add up to the target happen to be the very last two elements in the array), we will store up to $n$ key-value pairs in our hash map.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                     Two Sum Architecture                    |
+-------------------------------------------------------------+
| Initialize empty HashMap: [Number Value -> Index in Array]  |
|                                                             |
| Iterate through nums with index i:                          |
|    complement = target - nums[i]                            |
|                                                             |
|    +------------------------------------+                   |
|    | Has complement been seen before?   |                   |
|    +-----------------+------------------+                   |
|                      |                                      |
|            YES       |        NO                            |
|             v        v                                      |
|    Pair found!       Store current number in map:           |
|    Return indices:   map.put(nums[i], i)                    |
|    [map.get(comp), i]                                       |
|                      Continue scanning to next index...     |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    public int[] twoSum(int[] nums, int target) {
        // Step 1: Create a hash map to remember numbers we have already seen.
        // Key: the number value, Value: the index where that number was found.
        Map<Integer, Integer> numToIndex = new HashMap<>();

        // Step 2: Traverse through the array element by element.
        for (int i = 0; i < nums.length; i++) {
            int currentNum = nums[i];
            int complement = target - currentNum;

            // Step 3: Check if the required complement is already in our map.
            if (numToIndex.containsKey(complement)) {
                // If yes, we found our two numbers! Return their indices.
                int complementIndex = numToIndex.get(complement);
                return new int[] { complementIndex, i };
            }

            // Step 4: If not found, save the current number and its index for future lookups.
            numToIndex.put(currentNum, i);
        }

        // The problem guarantees exactly one solution exists, so this line is rarely reached.
        return new int[] {};
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `nums = [2, 7, 11, 15]`, `target = 9`
  - Start with an empty map: `{}`.
  - **Index 0 (`num = 2`)**:
    - We need complement $= 9 - 2 = 7$.
    - Is `7` in our map? No, map is empty.
    - Put `2` at index `0` into map: `{2: 0}`.
  - **Index 1 (`num = 7`)**:
    - We need complement $= 9 - 7 = 2$.
    - Is `2` in our map? Yes! It was stored at index `0`.
    - We immediately return `[0, 1]`. The search terminates!
- **Data Structures Used & Why**:
  - `HashMap<Integer, Integer>`: An array requires scanning from start to end ($\mathcal{O}(n)$ time) just to locate an element. A `HashMap`, by using hash codes to index directly into internal memory buckets, provides $\mathcal{O}(1)$ average lookup time. Trading a small amount of extra memory ($\mathcal{O}(n)$ auxiliary space) buys us an enormous speedup from $\mathcal{O}(n^2)$ down to $\mathcal{O}(n)$.

---

## 2. Contains Duplicate (LeetCode #217)

### Problem Introduction & Example
You are given an array of integers called `nums`. Your task is simple: return `true` if any number appears at least twice in the array, and return `false` if every single element in the array is distinct (unique).

- **Example 1**:
  - Input: `nums = [1, 2, 3, 1]`
  - Output: `true` (The value `1` shows up at index 0 and again at index 3).
- **Example 2**:
  - Input: `nums = [1, 2, 3, 4]`
  - Output: `false` (Every number is unique).

### High-Level Solution Intuition
**Why naive approaches fall short**:
- Comparing every element with every other element using two nested loops takes $\mathcal{O}(n^2)$ time, which will time out on large inputs.
- Sorting the array first takes $\mathcal{O}(n \log n)$ time. Once sorted, duplicates sit right next to each other, but sorting reorganizes the entire array, which incurs extra computational work.

**The "Aha!" Breakthrough (The Guest List Analogy)**:
Think of this problem like checking guests into an event using a guest list where nobody is allowed to enter twice:
As each number arrives, we check if it is already in our "seen set". If it is already there, we immediately catch the duplicate and return `true`. If it isn't, we add it to our set and move on to the next number.

In Java, a `HashSet` is designed precisely for this: it only stores unique values and allows us to test for containment in $\mathcal{O}(1)$ average time.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — We make at most a single pass over the array of size $n$. In each iteration, inserting a number into a `HashSet` takes $\mathcal{O}(1)$ amortized time.
- **Space Complexity**: $\mathcal{O}(n)$ — If all numbers in the array turn out to be distinct, the `HashSet` will eventually store all $n$ numbers.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                  Contains Duplicate Pipeline                |
+-------------------------------------------------------------+
| Initialize empty HashSet: seen                              |
|                                                             |
| For each number in nums:                                    |
|    +------------------------------------+                   |
|    | Has this number been seen before?  |                   |
|    +-----------------+------------------+                   |
|                      |                                      |
|            YES       |        NO                            |
|             v        v                                      |
|    Duplicate found!  Add number to seen:                    |
|    Return true       seen.add(number)                       |
|                      Check next number...                   |
|                                                             |
| If loop finishes without duplicates -> Return false         |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.HashSet;
import java.util.Set;

class Solution {
    public boolean containsDuplicate(int[] nums) {
        // Create a set to keep track of every distinct number we've encountered so far.
        Set<Integer> seen = new HashSet<>();

        for (int num : nums) {
            // The set.add() method in Java is very neat:
            // It returns 'true' if the element was successfully added (was not present),
            // and returns 'false' if the element was ALREADY in the set.
            if (!seen.add(num)) {
                return true; // Duplicate detected!
            }
        }

        // If we examined all numbers and never saw a duplicate, all are distinct.
        return false;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `nums = [1, 2, 3, 1]`
  - Start with empty set: `seen = {}`.
  - Process `1`: `seen.add(1)` $\rightarrow$ returns `true` (success). `seen = {1}`.
  - Process `2`: `seen.add(2)` $\rightarrow$ returns `true` (success). `seen = {1, 2}`.
  - Process `3`: `seen.add(3)` $\rightarrow$ returns `true` (success). `seen = {1, 2, 3}`.
  - Process `1`: `seen.add(1)` $\rightarrow$ returns `false` because `1` is already present!
  - We immediately return `true`.
- **Data Structures Used & Why**:
  - `HashSet<Integer>`: A HashSet is backed by a hash table that calculates a hash code for each integer. This gives us average $\mathcal{O}(1)$ time complexity for additions and checks, making it dramatically faster than searching through a standard `ArrayList` which would take $\mathcal{O}(n)$ for each lookup.

---

## 3. Valid Anagram (LeetCode #242)

### Problem Introduction & Example
Given two strings `s` and `t`, write a function that returns `true` if `t` is an **anagram** of `s`, and `false` otherwise.

An **anagram** is a word or phrase formed by rearranging the letters of another word or phrase. This means both words must use the exact same letters with the exact same frequencies—just in a different order.

- **Example 1**:
  - Input: `s = "anagram"`, `t = "nagaram"`
  - Output: `true` (Both contain 3 'a's, 1 'n', 1 'g', 1 'r', 1 'm').
- **Example 2**:
  - Input: `s = "rat"`, `t = "car"`
  - Output: `false` ('rat' has 't', while 'car' has 'c').

### High-Level Solution Intuition
**Why naive approaches fall short**:
Sorting both strings alphabetically (e.g., turning `"anagram"` into `"aaagmnr"`) and then checking if they are identical is easy to think of, but sorting takes $\mathcal{O}(n \log n)$ time and creates new character arrays.

**The "Aha!" Breakthrough (The Tally Sheet Technique)**:
Two strings can only be anagrams if they have:
1. The exact same length.
2. The exact same frequency for each character.

Imagine keeping a tally sheet for all 26 letters of the English alphabet:
- As we read string `s`, we add 1 to the tally of each letter we see.
- As we read string `t`, we subtract 1 from the tally of each letter we see.
If the two strings are genuine anagrams, every addition from `s` will be perfectly canceled out by a subtraction from `t`. At the end, every letter's balance should be exactly `0`!

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — Where $n$ is the length of string `s`. We scan both strings in a single pass of $n$ steps, and then check 26 entries in our tally array.
- **Space Complexity**: $\mathcal{O}(1)$ — Our frequency array is strictly fixed at 26 elements (one slot for each lowercase English letter), meaning memory usage never grows, regardless of how long the strings are.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                      Valid Anagram Logic                    |
+-------------------------------------------------------------+
| 1. Check lengths: if s.length() != t.length() -> return false|
|                                                             |
| 2. Create frequency array: int[26] charCounts               |
|                                                             |
| 3. Single Pass Loop:                                        |
|    For each index i:                                        |
|       charCounts[s.charAt(i) - 'a']++   (Deposit from s)    |
|       charCounts[t.charAt(i) - 'a']--   (Withdraw from t)   |
|                                                             |
| 4. Verification:                                            |
|    Do all 26 buckets equal 0?                               |
|       YES -> return true                                    |
|       NO  -> return false                                   |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public boolean isAnagram(String s, String t) {
        // Quick sanity check: anagrams must have identical lengths.
        if (s.length() != t.length()) {
            return false;
        }

        // Create a fixed frequency array of size 26 for letters 'a' through 'z'.
        int[] charCounts = new int[26];

        // Loop through both strings simultaneously.
        for (int i = 0; i < s.length(); i++) {
            // Subtracting 'a' converts characters to 0-based indices:
            // 'a' - 'a' = 0, 'b' - 'a' = 1, ..., 'z' - 'a' = 25.
            charCounts[s.charAt(i) - 'a']++;
            charCounts[t.charAt(i) - 'a']--;
        }

        // If s and t were true anagrams, every counter will have balanced out to 0.
        for (int count : charCounts) {
            if (count != 0) {
                return false;
            }
        }

        return true;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `s = "rat"`, `t = "car"`
  - Lengths match ($3 == 3$).
  - $i=0$: `s[0] = 'r'`, `t[0] = 'c'`. Increment count of `'r'` ($+1$), decrement count of `'c'` ($-1$).
  - $i=1$: `s[1] = 'a'`, `t[1] = 'a'`. Increment count of `'a'` ($+1$), decrement count of `'a'` ($-1 \rightarrow$ balance is $0$).
  - $i=2$: `s[2] = 't'`, `t[2] = 'r'`. Increment count of `'t'` ($+1$), decrement count of `'r'` (balance of `'r'` becomes $0$).
  - Final check of the tally array: Count for `'c'` is $-1 \ne 0$. Return `false`.
- **Data Structures Used & Why**:
  - `int[26]` array: While a `HashMap<Character, Integer>` works, using a primitive `int[26]` array is vastly more efficient. Array indexing via `char - 'a'` runs at raw CPU memory speeds with zero object creation overhead and $\mathcal{O}(1)$ space.

---

## 4. Group Anagrams (LeetCode #49)

### Problem Introduction & Example
Given an array of strings called `strs`, group all the anagrams together. You can return the grouped answer in any order.

- **Example**:
  - Input: `strs = ["eat", "tea", "tan", "ate", "nat", "bat"]`
  - Output: `[["bat"], ["nat", "tan"], ["ate", "eat", "tea"]]`
  - Explanation: `"eat"`, `"tea"`, and `"ate"` all consist of the same letters `{'a', 'e', 't'}`. Therefore, they belong in the same group.

### High-Level Solution Intuition
**How to group words together?**
To place anagrams into the same bucket, we need a reliable "signature" or "fingerprint" that is identical for all words in the same anagram family.

Notice what happens when you sort the letters of any anagram alphabetically:
- `"eat"` $\rightarrow$ `"aet"`
- `"tea"` $\rightarrow$ `"aet"`
- `"ate"` $\rightarrow$ `"aet"`

They all produce the exact same canonical string `"aet"`!
We can use this sorted string as the **key** in a Hash Map:
- Key: The sorted version of the word (e.g., `"aet"`).
- Value: A list of original words that share that sorted key (`["eat", "tea", "ate"]`).

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n \cdot k \log k)$ — Where $n$ is the total number of words in `strs`, and $k$ is the maximum length of a word. For each of the $n$ words, sorting its characters takes $\mathcal{O}(k \log k)$ time.
- **Space Complexity**: $\mathcal{O}(n \cdot k)$ — To store all the words and their groups inside the hash map.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                     Group Anagrams Flow                     |
+-------------------------------------------------------------+
| Initialize Map: String (Sorted Key) -> List<String>         |
|                                                             |
| For each word in strs:                                      |
|    chars = word.toCharArray()                               |
|    sort(chars)                                              |
|    key = String(chars)                                      |
|                                                             |
|    +------------------------------------+                   |
|    | Does map contain this key?         |                   |
|    +-----------------+------------------+                   |
|                      |                                      |
|         NO           |          YES                         |
|          v           v                                      |
|   Create new list    Append original word to existing list  |
|                                                             |
| Return all values of map as a List of Lists                 |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.*;

class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        // Map where:
        // Key   = the alphabetically sorted string (the anagram's "signature")
        // Value = list of original strings matching this signature
        Map<String, List<String>> anagramGroups = new HashMap<>();

        for (String word : strs) {
            // Step 1: Sort the characters of the word to create its canonical key.
            char[] charArray = word.toCharArray();
            Arrays.sort(charArray);
            String sortedKey = new String(charArray);

            // Step 2: If this key doesn't exist yet, initialize an empty list for it.
            // computeIfAbsent is a clean, modern Java method that does this in one step!
            anagramGroups.computeIfAbsent(sortedKey, k -> new ArrayList<>()).add(word);
        }

        // Return all the grouped lists
        return new ArrayList<>(anagramGroups.values());
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `strs = ["eat", "tea", "tan"]`
  - `word = "eat"`: sorted key is `"aet"`. Map: `{"aet": ["eat"]}`.
  - `word = "tea"`: sorted key is `"aet"`. Map: `{"aet": ["eat", "tea"]}`.
  - `word = "tan"`: sorted key is `"ant"`. Map: `{"aet": ["eat", "tea"], "ant": ["tan"]}`.
  - Result: `[["eat", "tea"], ["tan"]]`.
- **Data Structures Used & Why**:
  - `HashMap<String, List<String>>`: Maps a single identifier to an expanding bucket of matching strings. It gives us $\mathcal{O}(1)$ average time to look up the appropriate bucket for each word.

---

## 5. Top K Frequent Elements (LeetCode #347)

### Problem Introduction & Example
Given an integer array `nums` and an integer `k`, return the `k` most frequent elements in the array. You can return the answer in any order.

- **Example**:
  - Input: `nums = [1, 1, 1, 2, 2, 3]`, `k = 2`
  - Output: `[1, 2]`
  - Explanation: `1` appears 3 times, `2` appears 2 times, and `3` appears 1 time. The 2 most frequent numbers are `1` and `2`.

### High-Level Solution Intuition
**Step 1: Count Frequencies**:
First, count how many times every number appears using a `HashMap`. For `[1, 1, 1, 2, 2, 3]`, we get `{1: 3, 2: 2, 3: 1}`.

**Step 2: How to get the top k without sorting? (Bucket Sort)**:
Sorting the frequency map takes $\mathcal{O}(n \log n)$, and a Min-Heap takes $\mathcal{O}(n \log k)$. Can we do it in pure linear $\mathcal{O}(n)$ time?
Yes, using **Bucket Sort**!
Notice that the maximum possible frequency of any number cannot exceed the length of the array $n$.
We can create an array of lists called `buckets` where:
- The **index** represents the frequency (how many times a number appeared).
- The **content** at that index is the list of numbers that appeared that many times.

Then, we simply scan our bucket array backwards (from highest frequency $n$ down to $1$) and gather numbers until we have collected $k$ elements.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — Counting frequencies is $\mathcal{O}(n)$, placing numbers into buckets is $\mathcal{O}(n)$, and collecting the top $k$ elements from the buckets takes at most $n$ iterations.
- **Space Complexity**: $\mathcal{O}(n)$ — To store the frequency map and the bucket array of lists.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                 Bucket Sort Frequency Flow                  |
+-------------------------------------------------------------+
| 1. Frequency Map: {1 -> 3 times, 2 -> 2 times, 3 -> 1 time} |
|                                                             |
| 2. Buckets Array (Index = Frequency Count):                 |
|    Index:   0       1        2        3       4 ...         |
|    Lists:  [ ]     [3]      [2]      [1]     [ ]            |
|                                                             |
| 3. Scan backwards from right (highest frequency):           |
|    - Bucket 3: add 1 (collected 1)                          |
|    - Bucket 2: add 2 (collected 2 == k) -> Done!            |
|    Return: [1, 2]                                           |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.*;

class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        // Step 1: Count the frequency of each number using a HashMap.
        Map<Integer, Integer> freqMap = new HashMap<>();
        for (int num : nums) {
            freqMap.put(num, freqMap.getOrDefault(num, 0) + 1);
        }

        // Step 2: Create buckets where index = frequency.
        // The maximum possible frequency is nums.length.
        List<Integer>[] buckets = new List[nums.length + 1];
        for (int num : freqMap.keySet()) {
            int frequency = freqMap.get(num);
            if (buckets[frequency] == null) {
                buckets[frequency] = new ArrayList<>();
            }
            buckets[frequency].add(num);
        }

        // Step 3: Traverse buckets from highest frequency to lowest.
        int[] result = new int[k];
        int count = 0;

        for (int freq = buckets.length - 1; freq >= 0 && count < k; freq--) {
            if (buckets[freq] != null) {
                for (int num : buckets[freq]) {
                    result[count++] = num;
                    if (count == k) {
                        return result; // We collected our top k elements!
                    }
                }
            }
        }

        return result;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `nums = [1, 1, 1, 2, 2, 3]`, `k = 2`
  - Frequency map: `{1: 3, 2: 2, 3: 1}`.
  - Bucket allocation:
    - `buckets[1] = [3]`
    - `buckets[2] = [2]`
    - `buckets[3] = [1]`
  - Start scanning from index 6 down to 0:
    - Index 3: found `[1]`. Add `1` to result. (Count = 1).
    - Index 2: found `[2]`. Add `2` to result. (Count = 2 == $k$). Stop!
  - Result: `[1, 2]`.
- **Data Structures Used & Why**:
  - `List<Integer>[] buckets`: Using an array where the index directly represents the frequency bypasses the need to sort elements with a comparator or maintain a priority queue, achieving an optimal $\mathcal{O}(n)$ runtime.

---

## 6. Product of Array Except Self (LeetCode #238)

### Problem Introduction & Example
Given an integer array `nums`, return an array `answer` such that `answer[i]` is equal to the product of all elements of `nums` except `nums[i]`.
You must write an algorithm that runs in $\mathcal{O}(n)$ time and **without using the division operator**.

- **Example**:
  - Input: `nums = [1, 2, 3, 4]`
  - Output: `[24, 12, 8, 6]`
  - Explanation:
    - For index 0: $2 \times 3 \times 4 = 24$
    - For index 1: $1 \times 3 \times 4 = 12$
    - For index 2: $1 \times 2 \times 4 = 8$
    - For index 3: $1 \times 2 \times 3 = 6$

### High-Level Solution Intuition
**Why can't we just multiply everything and divide?**
If division were allowed, we could multiply all numbers together to get the total product $P$, and then for each element compute $P / nums[i]$. However:
1. The problem explicitly forbids division.
2. If the array contains a `0`, division by zero crashes our code!

**The "Aha!" Breakthrough (Prefix & Suffix Products)**:
For any element at index $i$, notice that the product of everything except $nums[i]$ is simply:
$$(\text{product of all numbers to the left of } i) \times (\text{product of all numbers to the right of } i)$$

We can solve this in two clean passes using our output array directly:
1. **Pass 1 (Left to Right)**: Fill `result[i]` with the product of all numbers to the left of $i$.
2. **Pass 2 (Right to Left)**: Walk backwards, maintaining a running product of numbers to the right, and multiply it directly into `result[i]`.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — We traverse the array twice (once left-to-right, once right-to-left).
- **Space Complexity**: $\mathcal{O}(1)$ — No extra arrays are created; we compute both prefixes and suffixes directly within the output array itself (the output array does not count toward auxiliary space complexity).

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                 Prefix & Suffix Product Flow                |
+-------------------------------------------------------------+
| nums:       [   1,       2,       3,       4   ]            |
|                                                             |
| Pass 1 (Left->Right): accumulate prefix products            |
| result:     [   1,       1,       2,       6   ]            |
|              (none)     (1)     (1*2)   (1*2*3)             |
|                                                             |
| Pass 2 (Right->Left): multiply by running suffix product    |
| runningSuffix starts at 1                                   |
| i=3: result[3] = 6 * 1  = 6;  suffix becomes 1 * 4  = 4     |
| i=2: result[2] = 2 * 4  = 8;  suffix becomes 4 * 3  = 12    |
| i=1: result[1] = 1 * 12 = 12; suffix becomes 12 * 2 = 24    |
| i=0: result[0] = 1 * 24 = 24;                               |
| Final:      [  24,      12,       8,       6   ]            |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int n = nums.length;
        int[] result = new int[n];

        // Pass 1: Compute left (prefix) products.
        // result[i] will store the product of all elements to the left of index i.
        result[0] = 1; // Base case: there are no elements to the left of index 0
        for (int i = 1; i < n; i++) {
            result[i] = result[i - 1] * nums[i - 1];
        }

        // Pass 2: Multiply with right (suffix) products on the fly.
        // rightProduct keeps a running multiplication of all numbers to the right of index i.
        int rightProduct = 1;
        for (int i = n - 1; i >= 0; i--) {
            result[i] = result[i] * rightProduct;
            rightProduct *= nums[i]; // Incorporate current number into the right product
        }

        return result;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `nums = [1, 2, 3, 4]`
  - After Pass 1: `result = [1, 1, 2, 6]`.
  - Pass 2 starts with `rightProduct = 1`:
    - $i=3$: `result[3] = 6 * 1 = 6`, `rightProduct = 1 * 4 = 4`
    - $i=2$: `result[2] = 2 * 4 = 8`, `rightProduct = 4 * 3 = 12`
    - $i=1$: `result[1] = 1 * 12 = 12`, `rightProduct = 12 * 2 = 24`
    - $i=0$: `result[0] = 1 * 24 = 24`
  - Output: `[24, 12, 8, 6]`.
- **Data Structures Used & Why**:
  - Output array `int[]`: By computing the prefix products in `result[]` and maintaining suffix products in a single scalar `int rightProduct`, we avoid allocating two separate helper arrays `prefix[]` and `suffix[]`, saving memory and keeping auxiliary space strictly $\mathcal{O}(1)$.

---

## 7. Longest Consecutive Sequence (LeetCode #128)

### Problem Introduction & Example
Given an unsorted array of integers `nums`, return the length of the longest sequence of consecutive numbers (numbers that differ by 1, such as 1, 2, 3, 4).
You must write an algorithm that runs in $\mathcal{O}(n)$ time.

- **Example**:
  - Input: `nums = [100, 4, 200, 1, 3, 2]`
  - Output: `4`
  - Explanation: The longest consecutive sequence is `[1, 2, 3, 4]`. Its length is 4.

### High-Level Solution Intuition
**Why not just sort the array?**
If we sorted the array, consecutive numbers would sit right next to each other, making counting easy. However, sorting takes $\mathcal{O}(n \log n)$ time, and the problem strictly demands a linear $\mathcal{O}(n)$ solution!

**The "Aha!" Breakthrough (Only Start from the Beginning)**:
1. Place all numbers into a `HashSet` so we can look up any number in $\mathcal{O}(1)$ time.
2. How do we avoid re-checking numbers repeatedly?
   Ask this crucial question for each number `x`:
   *"Is $(x - 1)$ already in the set?"*
   - If $(x - 1)$ IS in the set, then `x` is NOT the beginning of a sequence—it's just a follower! We can safely skip `x`.
   - If $(x - 1)$ is NOT in the set, then `x` is the **true starting leader** of a consecutive streak! We count upward: $x+1, x+2, x+3, \dots$ until the streak breaks.

Because we only count upwards starting from the actual beginning of each sequence, every number is visited at most twice across the entire algorithm, ensuring linear $\mathcal{O}(n)$ performance.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — Even though there is a `while` loop inside a `for` loop, the inner loop only executes for the first number of each sequence. Across the whole array, every number is processed a constant number of times.
- **Space Complexity**: $\mathcal{O}(n)$ — To store the unique numbers in our `HashSet`.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|             Longest Consecutive Sequence Logic              |
+-------------------------------------------------------------+
| Insert all numbers into HashSet: {100, 4, 200, 1, 3, 2}     |
|                                                             |
| For each num in set:                                        |
|    Is (num - 1) in set?                                     |
|    +----------------------+                                 |
|    | YES: Skip!           | (It is part of a longer streak) |
|    | NO:  Found start!    |                                 |
|    +----------+-----------+                                 |
|               |                                             |
|               v                                             |
|    current = num, streak = 1                                |
|    While set.contains(current + 1):                         |
|       current++, streak++                                   |
|    maxStreak = max(maxStreak, streak)                       |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.HashSet;
import java.util.Set;

class Solution {
    public int longestConsecutive(int[] nums) {
        if (nums == null || nums.length == 0) {
            return 0;
        }

        // Step 1: Put all numbers in a HashSet for O(1) instant lookups
        Set<Integer> numSet = new HashSet<>();
        for (int num : nums) {
            numSet.add(num);
        }

        int longestStreak = 0;

        // Step 2: Iterate through the unique numbers in the set
        for (int num : numSet) {
            // Check if 'num' is the very start of a sequence
            // (i.e., num - 1 does NOT exist in the set)
            if (!numSet.contains(num - 1)) {
                int currentNum = num;
                int currentStreak = 1;

                // Count upwards as long as the next consecutive number exists
                while (numSet.contains(currentNum + 1)) {
                    currentNum++;
                    currentStreak++;
                }

                // Update the overall longest streak found
                longestStreak = Math.max(longestStreak, currentStreak);
            }
        }

        return longestStreak;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `nums = [100, 4, 200, 1, 3, 2]`
  - `numSet = {1, 2, 3, 4, 100, 200}`
  - Check `100`: Is 99 in set? No $\rightarrow$ start streak at 100: is 101 in set? No $\rightarrow$ streak = 1.
  - Check `4`: Is 3 in set? Yes $\rightarrow$ skip (not a start).
  - Check `200`: Is 199 in set? No $\rightarrow$ start streak at 200: is 201 in set? No $\rightarrow$ streak = 1.
  - Check `1`: Is 0 in set? No $\rightarrow$ start streak at 1:
    - 2 exists $\rightarrow$ streak = 2
    - 3 exists $\rightarrow$ streak = 3
    - 4 exists $\rightarrow$ streak = 4
    - 5 does not exist $\rightarrow$ stop. Longest streak = 4.
  - Output: 4.
- **Data Structures Used & Why**:
  - `HashSet<Integer>`: Provides $\mathcal{O}(1)$ membership checks (`contains`). It also naturally eliminates duplicates, preventing unnecessary work on duplicate numbers.

---

## 8. Encode and Decode Strings (LeetCode #271)

### Problem Introduction & Example
Design an algorithm to encode a list of strings into a single string, which can be transmitted over a network and then decoded back into the original list of strings.

- **Example**:
  - Input: `["lint", "code", "love", "you"]`
  - Encoded string: `"4#lint4#code4#love3#you"`
  - Decoded list: `["lint", "code", "love", "you"]`

**Key Challenge**: The strings can contain any possible ASCII characters, including delimiters like commas, slashes, or hashes!

### High-Level Solution Intuition
**Why simple delimiters fail**:
If you just join strings with a delimiter like `","` or `"#"`, what happens if one of the strings itself contains that character (e.g. `["hello#world", "test"]`)? The decoder will get confused and split the word in half!

**The "Aha!" Breakthrough (Length-Prefixed Framing)**:
This is the same principle used by real-world network protocols (like HTTP chunked transfer and TCP):
Before writing each word, prepend its **length** followed by a designated separator character (like `#`):
$$\text{Format}: \text{<length>}\#\text{<content>}$$

When decoding:
1. Scan until you find the `#` symbol.
2. Read the digits before `#`—this tells you the exact integer length $L$ of the upcoming string.
3. Read exactly $L$ characters immediately following the `#`.
Because we know the exact length in advance, even if the word contains `#` or numbers, we will never misinterpret them as delimiters!

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(N)$ — Where $N$ is the total number of characters across all strings. Both encoding and decoding process each character a constant number of times.
- **Space Complexity**: $\mathcal{O}(N)$ — To store the single encoded string and the decoded output list.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                Length-Prefixed Framing Protocol             |
+-------------------------------------------------------------+
| Encoding:                                                   |
| For each word:                                              |
|    append word.length() + "#" + word                        |
|                                                             |
| Example: ["hi", "a#b"] -> "2#hi3#a#b"                       |
|                                                             |
| Decoding:                                                   |
| Pointer i = 0                                               |
| While i < length:                                           |
|    Find next '#' index                                      |
|    len = parse integer from i to hashIndex                  |
|    word = substring from hashIndex + 1 to hashIndex + 1 + len|
|    add word to result                                       |
|    advance i past the word                                  |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.ArrayList;
import java.util.List;

public class Codec {

    // Encodes a list of strings to a single string.
    public String encode(List<String> strs) {
        StringBuilder encoded = new StringBuilder();

        for (String s : strs) {
            // Write length, delimiter, and actual string
            encoded.append(s.length()).append('#').append(s);
        }

        return encoded.toString();
    }

    // Decodes a single string to a list of strings.
    public List<String> decode(String s) {
        List<String> result = new ArrayList<>();
        int i = 0;

        while (i < s.length()) {
            // Locate the delimiter '#'
            int hashIndex = s.indexOf('#', i);

            // Extract the length of the upcoming word
            int length = Integer.parseInt(s.substring(i, hashIndex));

            // Extract the exact word based on the parsed length
            int wordStart = hashIndex + 1;
            int wordEnd = wordStart + length;
            result.add(s.substring(wordStart, wordEnd));

            // Move pointer to the start of the next length prefix
            i = wordEnd;
        }

        return result;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `["hi", "a#b"]`
  - **Encode**:
    - `"hi"`: length is 2 $\rightarrow$ `"2#hi"`
    - `"a#b"`: length is 3 $\rightarrow$ `"3#a#b"`
    - Output string: `"2#hi3#a#b"`
  - **Decode**:
    - Start at $i = 0$. Find `#` at index 1.
    - Parse length between 0 and 1: length $= 2$.
    - Read 2 characters from index 2 to 4: extracts `"hi"`.
    - Next $i = 4$. Find `#` at index 5.
    - Parse length between 4 and 5: length $= 3$.
    - Read 3 characters from index 6 to 9: extracts `"a#b"` (the `#` inside the word is safely read as part of the string!).
    - Result: `["hi", "a#b"]`.
- **Data Structures Used & Why**:
  - `StringBuilder`: Used during encoding because normal Java string concatenation (`+`) creates a new string object on every iteration ($\mathcal{O}(n^2)$ copying overhead). `StringBuilder` appends in amortized $\mathcal{O}(1)$ time.


# Category 2: Two Pointers, Sliding Window & Stack

---

## 9. Valid Palindrome (LeetCode #125)

### Problem Introduction & Example
A phrase is a **palindrome** if, after turning all uppercase letters into lowercase letters and getting rid of all non-alphanumeric characters (spaces, commas, colons, punctuation), it reads the exact same forward and backward. 

Given a string `s`, return `true` if it is a palindrome, or `false` otherwise.

- **Example**:
  - Input: `s = "A man, a plan, a canal: Panama"`
  - Output: `true`
  - Explanation: When we remove punctuation and convert to lowercase, the phrase becomes `"amanaplanacanalpanama"`, which reads identically forwards and backwards!

### High-Level Solution Intuition
**Why naive approaches waste memory**:
A beginner might first clean the string using regular expressions or string concatenation, and then reverse the entire cleaned string to compare it with the original. However, creating brand new cleaned and reversed strings consumes extra memory ($\mathcal{O}(n)$ space) and requires multiple passes.

**The "Aha!" Breakthrough (Two Inward-Walking Pointers)**:
Instead of building a new string, imagine placing two index fingers on the original string:
- `left` finger starts at the very beginning (index 0).
- `right` finger starts at the very end (index `s.length() - 1`).

As they walk toward each other:
1. If the `left` finger is pointing at a space or punctuation, advance it forward.
2. If the `right` finger is pointing at a space or punctuation, advance it backward.
3. When both fingers land on valid letters or digits, compare them (ignoring uppercase/lowercase). If they don't match, it's not a palindrome!
4. If they meet in the middle without finding any mismatches, the string is definitely a palindrome.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — We examine each character at most once as the two pointers move towards each other from opposite ends.
- **Space Complexity**: $\mathcal{O}(1)$ — No extra string or character array is allocated; we operate directly on the input string using two primitive integer indices.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                  Two-Pointer Palindrome Walk                |
+-------------------------------------------------------------+
| left pointer -> 0                            right -> len - 1|
|                                                             |
| While left < right:                                         |
|    If s[left] is not alphanumeric:  left++                  |
|    Else if s[right] is not alphanumeric: right--            |
|    Else:                                                    |
|       If toLowerCase(s[left]) != toLowerCase(s[right]):     |
|          return false                                       |
|       left++, right--                                       |
|                                                             |
| All characters matched successfully -> Return true          |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public boolean isPalindrome(String s) {
        int left = 0;
        int right = s.length() - 1;

        while (left < right) {
            // Step 1: Move left pointer forward until it hits a letter or digit
            while (left < right && !Character.isLetterOrDigit(s.charAt(left))) {
                left++;
            }

            // Step 2: Move right pointer backward until it hits a letter or digit
            while (left < right && !Character.isLetterOrDigit(s.charAt(right))) {
                right--;
            }

            // Step 3: Compare both characters in lower case
            char leftChar = Character.toLowerCase(s.charAt(left));
            char rightChar = Character.toLowerCase(s.charAt(right));

            if (leftChar != rightChar) {
                return false; // Mismatch found!
            }

            // Move both pointers inward
            left++;
            right--;
        }

        return true;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `s = "A man, a... Panama"`
  - `left` points to `'A'`, `right` points to `'a'`: Match (`'a' == 'a'`).
  - Next, `left` advances past spaces and punctuation to `'m'`, `right` advances past `'a'` to `'m'`: Match.
  - Continues moving inward until pointers meet in the middle without any conflicts $\rightarrow$ Returns `true`.
- **Data Structures Used & Why**:
  - Two primitive integer pointers (`left`, `right`): Inspecting characters directly using `charAt()` completely avoids allocating helper strings or array copies, keeping memory usage constant at $\mathcal{O}(1)$.

---

## 10. 3Sum (LeetCode #15)

### Problem Introduction & Example
Given an integer array `nums`, find all unique triplets `[nums[i], nums[j], nums[k]]` such that:
1. `i != j`, `i != k`, and `j != k` (three distinct positions), and
2. `nums[i] + nums[j] + nums[k] == 0`.

The solution set must not contain duplicate triplets (for instance, if `[-1, 0, 1]` is added, you cannot add another `[0, 1, -1]`).

- **Example**:
  - Input: `nums = [-1, 0, 1, 2, -1, -4]`
  - Output: `[[-1, -1, 2], [-1, 0, 1]]`
  - Explanation: `(-1) + 0 + 1 = 0` and `(-1) + (-1) + 2 = 0`. Notice that duplicate triplets are filtered out.

### High-Level Solution Intuition
**Why naive approaches fall short**:
Testing all possible triplets with three nested loops takes cubic time—$\mathcal{O}(n^3)$. Filtering out duplicates with sets makes it even slower.

**The "Aha!" Breakthrough (Sort First, then Two Pointers)**:
1. **Sort the array first**: Sorting takes $\mathcal{O}(n \log n)$ time, which is much faster than $\mathcal{O}(n^3)$ and gives us two massive advantages:
   - Duplicates become adjacent, making them easy to skip.
   - We can use the two-pointer technique!
2. **Fix one element and search for the other two**:
   - Loop through the array with index `i`, fixing `nums[i]`.
   - Now, we just need two other numbers that sum to `-nums[i]`.
   - Place two pointers: `left = i + 1` and `right = nums.length - 1`.
   - If `nums[left] + nums[right]` is too small ($< -nums[i]$), increase `left`.
   - If the sum is too large, decrease `right`.
   - If it equals 0, record the triplet, advance both pointers, and skip any duplicate numbers.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n^2)$ — Sorting takes $\mathcal{O}(n \log n)$. The outer loop runs $n$ times, and for each iteration the two-pointer search takes $\mathcal{O}(n)$ time, leading to overall $\mathcal{O}(n^2)$ time.
- **Space Complexity**: $\mathcal{O}(1)$ or $\mathcal{O}(\log n)$ — Depending on the sorting implementation, beyond the returned list of triplets.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                      3Sum Architecture                      |
+-------------------------------------------------------------+
| Sort array: [-4, -1, -1, 0, 1, 2]                           |
|                                                             |
| Fix i = 1 (value: -1):                                      |
| Target sum for (left + right) = -(-1) = +1                  |
|                                                             |
|   [-4,  -1,  -1,   0,   1,   2]                             |
|          ^    ^              ^                              |
|          i   left          right                            |
|                                                             |
|   nums[left] + nums[right] = -1 + 2 = 1 (Matches target!)   |
|   -> Add triplet [-1, -1, 2] to results                     |
|   -> Skip duplicate lefts & rights, then move both inward   |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.*;

class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        if (nums == null || nums.length < 3) return result;

        // Step 1: Sort the array to enable two pointers and duplicate skipping
        Arrays.sort(nums);

        for (int i = 0; i < nums.length - 2; i++) {
            // Optimization: If the smallest number is > 0, remaining numbers are also > 0,
            // so three positive numbers can never sum to 0.
            if (nums[i] > 0) break;

            // Skip duplicate values for the first element
            if (i > 0 && nums[i] == nums[i - 1]) continue;

            int left = i + 1;
            int right = nums.length - 1;

            while (left < right) {
                int sum = nums[i] + nums[left] + nums[right];

                if (sum == 0) {
                    result.add(Arrays.asList(nums[i], nums[left], nums[right]));

                    // Skip duplicate values for the second element
                    while (left < right && nums[left] == nums[left + 1]) left++;
                    // Skip duplicate values for the third element
                    while (left < right && nums[right] == nums[right - 1]) right--;

                    left++;
                    right--;
                } else if (sum < 0) {
                    left++; // Sum is too small, move left pointer to increase it
                } else {
                    right--; // Sum is too large, move right pointer to decrease it
                }
            }
        }

        return result;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `nums = [-1, 0, 1, 2, -1, -4]` $\rightarrow$ Sorted: `[-4, -1, -1, 0, 1, 2]`
  - $i=0$ (`nums[0] = -4`): Target for `left + right` is 4. Largest possible sum is $-1 + 2 = 1 < 4$. No match.
  - $i=1$ (`nums[1] = -1`): Target is 1.
    - `left = 2` (val `-1`), `right = 5` (val `2`): sum $= -1 + 2 = 1 \rightarrow$ Add `[-1, -1, 2]`.
    - Pointers move inward: `left = 3` (val `0`), `right = 4` (val `1`): sum $= 0 + 1 = 1 \rightarrow$ Add `[-1, 0, 1]`.
  - $i=2$ (`nums[2] = -1`): Duplicate of index 1! Skipped by `if (nums[i] == nums[i-1])`.
  - Result: `[[-1, -1, 2], [-1, 0, 1]]`.
- **Data Structures Used & Why**:
  - `ArrayList<List<Integer>>`: Dynamically holds the resulting triplets.
  - Sorting + Two Pointers avoids having to insert elements into a `HashSet<List<Integer>>` to filter duplicates, significantly saving memory and hashing overhead.

---

## 11. Container With Most Water (LeetCode #11)

### Problem Introduction & Example
You are given an integer array `height` of length $n$. Each index represents a vertical wall at position $i$ with height `height[i]`. Find two lines that together with the x-axis form a container, such that the container holds the greatest amount of water. Return the maximum volume of water it can hold.

- **Example**:
  - Input: `height = [1, 8, 6, 2, 5, 4, 8, 3, 7]`
  - Output: `49`
  - Explanation: Choosing the line at index 1 (`height = 8`) and index 8 (`height = 7`) gives a width of $8 - 1 = 7$. The height is limited by the shorter wall ($\min(8, 7) = 7$). The volume is $7 \times 7 = 49$.

### High-Level Solution Intuition
The volume of water between two walls `left` and `right` is determined by geometry:
$$\text{Area} = (\text{right} - \text{left}) \times \min(\text{height[left]}, \text{height[right]})$$

**The "Aha!" Breakthrough (Squeeze from the Widest Bounds)**:
Start with the widest container possible: `left = 0` and `right = height.length - 1`.
Now, as we bring the two walls closer together, the **width is guaranteed to decrease**.
To have any chance of finding a bigger area with a smaller width, we **must find taller walls**.

Which wall is currently holding us back? The **shorter one**! The shorter wall is the bottleneck.
Moving the taller wall inward could never increase the area, because the height is still capped by the shorter wall and the width just shrank.
Therefore, the optimal greedy move is: **always move the pointer pointing to the shorter wall inward**!

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — Every step moves either the `left` or `right` pointer inward by 1, visiting each wall at most once.
- **Space Complexity**: $\mathcal{O}(1)$ — Only a few primitive integer variables are maintained.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|             Container With Most Water Logic                 |
+-------------------------------------------------------------+
| left = 0, right = n - 1, maxWater = 0                       |
|                                                             |
| While left < right:                                         |
|    width = right - left                                     |
|    h = min(height[left], height[right])                     |
|    maxWater = max(maxWater, width * h)                      |
|                                                             |
|    If height[left] < height[right]:                         |
|        left++   (Abandon the shorter left wall)             |
|    Else:                                                    |
|        right--  (Abandon the shorter right wall)            |
|                                                             |
| Return maxWater                                             |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public int maxArea(int[] height) {
        int maxWater = 0;
        int left = 0;
        int right = height.length - 1;

        while (left < right) {
            int width = right - left;
            int containerHeight = Math.min(height[left], height[right]);
            int area = width * containerHeight;

            maxWater = Math.max(maxWater, area);

            // The shorter wall limits the container capacity.
            // Move inward past the shorter wall in search of a taller one.
            if (height[left] < height[right]) {
                left++;
            } else {
                right--;
            }
        }

        return maxWater;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `height = [1, 8, 6, 2, 5, 4, 8, 3, 7]`
  - `left = 0 (h=1), right = 8 (h=7)`: area $= 8 \times 1 = 8$. Left wall is shorter $\rightarrow$ `left++`.
  - `left = 1 (h=8), right = 8 (h=7)`: area $= 7 \times 7 = 49$. Right wall is shorter $\rightarrow$ `right--`.
  - Continues checking inward. No subsequent pair exceeds 49.
  - Max water recorded: 49.
- **Data Structures Used & Why**:
  - Primitive indices: The two-pointer greedy invariant guarantees that the optimal pair cannot be missed, eliminating the need to store candidate rectangles or check all $\mathcal{O}(n^2)$ pairs.

---

## 12. Best Time to Buy and Sell Stock (LeetCode #121)

### Problem Introduction & Example
You are given an array `prices` where `prices[i]` is the price of a given stock on the $i^{th}$ day.
You want to maximize your profit by choosing a **single day** to buy one stock and choosing a **different day in the future** to sell that stock. Return the maximum profit you can achieve. If you cannot achieve any profit, return `0`.

- **Example**:
  - Input: `prices = [7, 1, 5, 3, 6, 4]`
  - Output: `5`
  - Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit $= 6 - 1 = 5$. (Note: you cannot sell on day 1 for 7 because you must buy before you sell).

### High-Level Solution Intuition
To maximize profit, you want to:
1. Buy at the lowest historical price seen so far.
2. Sell on the current day if the resulting profit beats our previous best.

As you walk through the days chronologically:
- Keep track of `minPriceSoFar`.
- At every day, compute what profit you would make if you sold today: `currentPrice - minPriceSoFar`.
- If that profit is higher than `maxProfit`, update `maxProfit`.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — We inspect each day's price exactly once in a single forward pass.
- **Space Complexity**: $\mathcal{O}(1)$ — Only two integer variables (`minPrice` and `maxProfit`) are needed.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                 One-Pass Stock Profit Logic                 |
+-------------------------------------------------------------+
| minPrice = Infinity, maxProfit = 0                          |
|                                                             |
| For each price in prices:                                   |
|    If price < minPrice:                                     |
|        minPrice = price        (Found a cheaper buy day)    |
|    Else:                                                    |
|        profit = price - minPrice                            |
|        maxProfit = max(maxProfit, profit)                   |
|                                                             |
| Return maxProfit                                            |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public int maxProfit(int[] prices) {
        int minPrice = Integer.MAX_VALUE;
        int maxProfit = 0;

        for (int price : prices) {
            if (price < minPrice) {
                // Record the lowest price seen so far
                minPrice = price;
            } else {
                // Calculate profit if sold today, and record if it's a new record
                int currentProfit = price - minPrice;
                if (currentProfit > maxProfit) {
                    maxProfit = currentProfit;
                }
            }
        }

        return maxProfit;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `prices = [7, 1, 5, 3, 6, 4]`
  - Day 0 (price 7): `minPrice = 7`, `maxProfit = 0`.
  - Day 1 (price 1): `minPrice = 1` (new low), `maxProfit = 0`.
  - Day 2 (price 5): profit $= 5 - 1 = 4 \rightarrow maxProfit = 4$.
  - Day 3 (price 3): profit $= 3 - 1 = 2 \rightarrow maxProfit = 4$.
  - Day 4 (price 6): profit $= 6 - 1 = 5 \rightarrow maxProfit = 5$.
  - Day 5 (price 4): profit $= 4 - 1 = 3 \rightarrow maxProfit = 5$.
  - Result: 5.
- **Data Structures Used & Why**:
  - Two scalar variables: Because the timeline only moves forward, we only ever care about the minimum price encountered *prior* to the current day. No arrays or lists are required.

---

## 13. Longest Substring Without Repeating Characters (LeetCode #3)

### Problem Introduction & Example
Given a string `s`, find the length of the longest substring that contains no repeating characters.

- **Example 1**:
  - Input: `s = "abcabcbb"`
  - Output: `3`
  - Explanation: The answer is `"abc"`, with a length of 3.
- **Example 2**:
  - Input: `s = "bbbbb"`
  - Output: `1` (The longest substring without duplicates is `"b"`).

### High-Level Solution Intuition
**The "Aha!" Breakthrough (The Sliding Window Technique)**:
Imagine a window `[left, right]` sliding across the string:
- The `right` pointer expands the window one character at a time.
- We maintain a `HashMap` (or integer array) that remembers the **most recent index where each character appeared**.
- If the character at `right` has already been seen *inside the current window* (meaning its last seen position $\ge left$), a duplicate has occurred!
- Instead of nudging `left` forward one character at a time, we can **jump `left` directly past the previous instance of that duplicate**:
  $$\text{left} = \max(\text{left}, \text{lastSeenIndex} + 1)$$
- At every step, the window length is `right - left + 1`. We track the maximum length seen.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — Both `left` and `right` pointers only move forward. Each character is visited at most once by `right`.
- **Space Complexity**: $\mathcal{O}(\min(m, n))$ — Where $m$ is the size of the character alphabet (e.g. 128 for ASCII).

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|               Sliding Window Duplicate Jumping              |
+-------------------------------------------------------------+
| String: a   b   c   a   b   c   b   b                       |
|         ^           ^                                       |
|        left       right                                     |
|                                                             |
| At right = 3 (char 'a'):                                    |
| Character 'a' was seen at index 0.                          |
| Jump left pointer to index 0 + 1 = 1!                       |
| New window: [b, c, a] -> Valid and distinct!                |
|                                                             |
| maxLength = max(maxLength, right - left + 1)                |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    public int lengthOfLongestSubstring(String s) {
        // Map stores: Key = character, Value = most recent index seen
        Map<Character, Integer> lastSeen = new HashMap<>();
        int maxLength = 0;
        int left = 0;

        for (int right = 0; right < s.length(); right++) {
            char ch = s.charAt(right);

            // If we've seen this character before and it falls inside our current window,
            // slide the left boundary past the duplicate's previous position.
            if (lastSeen.containsKey(ch)) {
                left = Math.max(left, lastSeen.get(ch) + 1);
            }

            // Update the latest position of this character
            lastSeen.put(ch, right);

            // Calculate current window size and update max
            maxLength = Math.max(maxLength, right - left + 1);
        }

        return maxLength;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `s = "pwwkew"`
  - $r=0$ (`'p'`): `lastSeen={'p':0}`, `left=0`, window length $= 1$.
  - $r=1$ (`'w'`): `lastSeen={'p':0, 'w':1}`, `left=0`, window length $= 2$.
  - $r=2$ (`'w'`): `'w'` was seen at 1. Jump `left = max(0, 1 + 1) = 2`. `lastSeen={'w':2}`, window length $= 1$.
  - $r=3$ (`'k'`): `left=2`, window length $= 2$ (`"wk"`).
  - $r=4$ (`'e'`): `left=2`, window length $= 3$ (`"wke"`).
  - $r=5$ (`'w'`): `'w'` was seen at 2. Jump `left = max(2, 2 + 1) = 3`. Window length $= 3$ (`"kew"`).
  - Max length recorded: 3.
- **Data Structures Used & Why**:
  - `Map<Character, Integer>`: Storing the exact last seen index lets `left` skip directly past duplicates in $\mathcal{O}(1)$ time, rather than slowly shrinking the window character by character.

---

## 14. Longest Repeating Character Replacement (LeetCode #424)

### Problem Introduction & Example
You are given a string `s` consisting of uppercase English letters and an integer `k`. You can choose any character of the string and change it to any other uppercase letter. You are allowed to do this at most `k` times. Return the length of the longest substring containing the same letter that you can achieve.

- **Example**:
  - Input: `s = "AABABBA"`, `k = 1`
  - Output: `4`
  - Explanation: If we change the `'B'` at index 2 into an `'A'`, the substring `"AABA"` becomes `"AAAA"`, which has length 4.

### High-Level Solution Intuition
**When is a window valid?**
Consider any sliding window of characters `[left, right]`:
- The length of the window is `right - left + 1`.
- The most frequent character appears `maxFreq` times.
- The number of characters that we would need to replace to make the entire window uniform is:
  $$\text{Replacements Needed} = \text{Window Length} - \text{maxFreq}$$

If $\text{Window Length} - \text{maxFreq} \le k$, we have enough operations to turn all other characters into the dominant character! The window is **valid**.
If $\text{Window Length} - \text{maxFreq} > k$, we have exceeded our replacement budget, so we must shrink the window by moving `left` forward.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — The `right` pointer traverses from 0 to $n - 1$, and the `left` pointer only ever moves forward.
- **Space Complexity**: $\mathcal{O}(1)$ — The frequency table is an `int[26]` array, which occupies fixed constant space.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|               Sliding Window Replacement Flow               |
+-------------------------------------------------------------+
| counts = int[26], maxFreq = 0, left = 0                     |
|                                                             |
| For right from 0 to n - 1:                                  |
|    counts[s[right] - 'A']++                                 |
|    maxFreq = max(maxFreq, counts[s[right] - 'A'])           |
|                                                             |
|    While (windowLen - maxFreq) > k:                         |
|        counts[s[left] - 'A']--                              |
|        left++                                               |
|                                                             |
|    maxLength = max(maxLength, right - left + 1)             |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public int characterReplacement(String s, int k) {
        int[] freq = new int[26];
        int maxFreq = 0;
        int left = 0;
        int maxLength = 0;

        for (int right = 0; right < s.length(); right++) {
            // Increment the count of the incoming character
            int index = s.charAt(right) - 'A';
            freq[index]++;

            // Update the maximum frequency of any single character in the window
            maxFreq = Math.max(maxFreq, freq[index]);

            // If characters needing replacement exceed k, shrink window from left
            while ((right - left + 1) - maxFreq > k) {
                freq[s.charAt(left) - 'A']--;
                left++;
            }

            // Update maximum valid window size seen
            maxLength = Math.max(maxLength, right - left + 1);
        }

        return maxLength;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `s = "ABAB"`, `k = 2`
  - $r=0$ (`'A'`): `freq['A']=1`, `maxFreq=1`. Window length 1. Replacements needed $= 1 - 1 = 0 \le 2$.
  - $r=1$ (`'B'`): `freq['B']=1`, `maxFreq=1`. Window length 2. Replacements needed $= 2 - 1 = 1 \le 2$.
  - $r=2$ (`'A'`): `freq['A']=2`, `maxFreq=2`. Window length 3. Replacements needed $= 3 - 2 = 1 \le 2$.
  - $r=3$ (`'B'`): `freq['B']=2`, `maxFreq=2`. Window length 4. Replacements needed $= 4 - 2 = 2 \le 2$.
  - Result: 4 (the entire string can be made uniform).
- **Data Structures Used & Why**:
  - `int[26]` frequency array: Provides $\mathcal{O}(1)$ character count increments and decrements, eliminating the overhead of a `HashMap`.

---

## 15. Minimum Window Substring (LeetCode #76)

### Problem Introduction & Example
Given two strings `s` and `t` of lengths $m$ and $n$ respectively, return the **minimum window substring** of `s` such that every character in `t` (including duplicate characters) is included in the window. If there is no such substring, return the empty string `""`.

- **Example**:
  - Input: `s = "ADOBECODEBANC"`, `t = "ABC"`
  - Output: `"BANC"`
  - Explanation: The minimum substring containing `'A'`, `'B'`, and `'C'` is `"BANC"` (length 4).

### High-Level Solution Intuition
This is the ultimate test of the **Sliding Window** technique:
1. **Count requirements**: Count how many of each character we need from `t` using a frequency map `targetCount`.
2. **Expand Right**: Move `right` across `s`. When a character's count in our window reaches the requirement in `targetCount`, we increment `matchedChars`.
3. **Shrink Left**: When `matchedChars == uniqueCharsToMatch`, the window is **valid**!
   Now, greedily shrink `left` as much as possible while maintaining validity, updating our shortest window record.
   Once `left` removes an essential character and the window becomes invalid, resume expanding `right`.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(m + n)$ — Each character in `s` is added to the window by `right` once and removed by `left` at most once.
- **Space Complexity**: $\mathcal{O}(1)$ — Character frequency tables for standard ASCII have a fixed size of 128 elements.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                Minimum Window Substring Loop                |
+-------------------------------------------------------------+
| 1. Build targetCount from t                                 |
|                                                             |
| 2. While right < s.length():                                |
|       Add s[right] to windowCount                           |
|       If count matches target: matchedChars++               |
|                                                             |
|       While matchedChars == uniqueChars:                    |
|           Record min window [minStart, minLen]              |
|           Remove s[left] from windowCount                   |
|           If count falls below target: matchedChars--       |
|           left++                                            |
|                                                             |
| 3. Return s.substring(minStart, minStart + minLen)          |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public String minWindow(String s, String t) {
        if (s == null || t == null || s.length() < t.length()) {
            return "";
        }

        // Frequency requirements for characters in t
        int[] targetCount = new int[128];
        int uniqueCharsToMatch = 0;
        for (char c : t.toCharArray()) {
            if (targetCount[c] == 0) uniqueCharsToMatch++;
            targetCount[c]++;
        }

        int[] windowCount = new int[128];
        int matchedChars = 0;
        int minLen = Integer.MAX_VALUE;
        int minStart = 0;
        int left = 0;

        for (int right = 0; right < s.length(); right++) {
            char rightChar = s.charAt(right);
            windowCount[rightChar]++;

            // Check if current character satisfies its quota in t
            if (targetCount[rightChar] > 0 && windowCount[rightChar] == targetCount[rightChar]) {
                matchedChars++;
            }

            // Window is valid! Try to shrink it from the left to find the minimum
            while (matchedChars == uniqueCharsToMatch) {
                int currentLen = right - left + 1;
                if (currentLen < minLen) {
                    minLen = currentLen;
                    minStart = left;
                }

                char leftChar = s.charAt(left);
                windowCount[leftChar]--;
                // If removing leftChar breaks our quota, the window is no longer valid
                if (targetCount[leftChar] > 0 && windowCount[leftChar] < targetCount[leftChar]) {
                    matchedChars--;
                }
                left++;
            }
        }

        return minLen == Integer.MAX_VALUE ? "" : s.substring(minStart, minStart + minLen);
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `s = "ADOBECODEBANC"`, `t = "ABC"`
  - Target needs: `A:1, B:1, C:1`. Unique characters to match $= 3$.
  - Window expands until index 5 (`"ADOBEC"`): contains A, B, C. Valid! Length $= 6$.
  - Left shrinks: removes `'A'` $\rightarrow$ window `"DOBEC"` is invalid (`matchedChars = 2`).
  - Window expands again until index 10 (`"CODEBA"`): valid again.
  - Final contraction reaches `"BANC"` (indices 9 to 12, length 4).
  - Return `"BANC"`.
- **Data Structures Used & Why**:
  - `int[128]`: Direct ASCII index mapping allows $\mathcal{O}(1)$ increments, decrements, and comparisons with zero garbage collection overhead.

---

## 16. Valid Parentheses (LeetCode #20)

### Problem Introduction & Example
Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.
An input string is valid if:
1. Open brackets are closed by the same type of brackets.
2. Open brackets are closed in the correct order.
3. Every closing bracket has a corresponding open bracket of the same type.

- **Example 1**: `s = "()[]{}"` $\rightarrow$ `true`
- **Example 2**: `s = "(]"` $\rightarrow$ `false`
- **Example 3**: `s = "([)]"` $\rightarrow$ `false` (Incorrect closing order!)

### High-Level Solution Intuition
**Why a Stack? (LIFO - Last In, First Out)**:
Notice that the most *recently* opened bracket must be the very *first* one closed.
Think of a stack of cafeteria trays: the last tray placed on top must be the first one picked up.

A **Stack** is the perfect data structure for this behavior:
- Whenever you encounter an opening bracket (`'('`, `'{'`, `'['`), push its matching closing bracket onto the stack.
- Whenever you encounter a closing bracket, pop the top element from the stack. It must match the current character!
- If the stack is empty when a closing bracket arrives, or if the popped bracket doesn't match, the string is invalid.
- At the end, if the stack is completely empty, every opened bracket was closed properly!

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — We iterate through the string of length $n$ once. Pushing and popping from a stack are $\mathcal{O}(1)$ operations.
- **Space Complexity**: $\mathcal{O}(n)$ — In the worst case (e.g. `"(((((("`), the stack holds all $n$ characters.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                     Stack Validation Flow                   |
+-------------------------------------------------------------+
| char is '(': push ')' onto stack                            |
| char is '{': push '}' onto stack                            |
| char is '[': push ']' onto stack                            |
|                                                             |
| char is closing bracket:                                    |
|    Is stack empty OR stack.pop() != char?                   |
|       YES -> Mismatch! Return false                         |
|                                                             |
| End of string:                                              |
|    Return stack.isEmpty()                                   |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.ArrayDeque;
import java.util.Deque;

class Solution {
    public boolean isValid(String s) {
        // Quick sanity check: an odd number of brackets can never be valid
        if (s.length() % 2 != 0) return false;

        // In Java, ArrayDeque is preferred over java.util.Stack for LIFO queues
        Deque<Character> stack = new ArrayDeque<>();

        for (char c : s.toCharArray()) {
            if (c == '(') {
                stack.push(')');
            } else if (c == '{') {
                stack.push('}');
            } else if (c == '[') {
                stack.push(']');
            } else {
                // If stack is empty or the popped bracket doesn't match current character
                if (stack.isEmpty() || stack.pop() != c) {
                    return false;
                }
            }
        }

        // If the stack is completely empty, all open brackets were properly closed
        return stack.isEmpty();
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `s = "{[]}"`
  - Step 1: `'{'` $\rightarrow$ push `'}'`. Stack: `['}']`.
  - Step 2: `'['` $\rightarrow$ push `']'`. Stack: `['}', ']']`.
  - Step 3: `']'` $\rightarrow$ pop from stack: matches `']'`. Stack: `['}']`.
  - Step 4: `'}'` $\rightarrow$ pop from stack: matches `'}'`. Stack: `[]`.
  - Finished string: `stack.isEmpty() == true`. Returns `true`.
- **Data Structures Used & Why**:
  - `ArrayDeque<Character>`: In Java, `ArrayDeque` is backed by a resizable circular array, making it much faster and lighter than the legacy `java.util.Stack` class (which inherits thread-synchronization locks from `Vector`).


# Category 3: Binary Search & Linked List

---

## 17. Search in Rotated Sorted Array (LeetCode #33)

### Problem Introduction & Example
You are given an integer array `nums` that was originally sorted in ascending order with unique values. However, before being passed to your function, it was rotated at some unknown pivot index. 
For example, `[0, 1, 2, 4, 5, 6, 7]` might be rotated to become `[4, 5, 6, 7, 0, 1, 2]`.

Given this rotated array and an integer `target`, return the index of `target` if it exists in `nums`, or `-1` if it does not.
You must design an algorithm that runs in logarithmic $\mathcal{O}(\log n)$ time.

- **Example**:
  - Input: `nums = [4, 5, 6, 7, 0, 1, 2]`, `target = 0`
  - Output: `4`
  - Explanation: `0` is located at index 4.

### High-Level Solution Intuition
**Why simple binary search gets confused**:
In a regular sorted array, if `target > nums[mid]`, you know with 100% certainty that the target must be on the right. But in a rotated array, the rotation pivot breaks that direct assumption.

**The "Aha!" Breakthrough (One Half is Always Normal)**:
Notice this magical property of any rotated sorted array:
Whenever you cut the array in half at `mid`, **at least one of the two halves is guaranteed to be strictly sorted in ascending order**!

How do we check which half is normal?
- Compare `nums[left]` with `nums[mid]`:
  - If `nums[left] <= nums[mid]`, the **left half is completely normal and sorted**!
  - If not, the **right half is completely normal and sorted**!

Once you know which half is normally sorted, checking if `target` lies inside that half is easy:
- If target falls within that sorted range, search there!
- If not, search the other half.
This halves our search space in every step, preserving $\mathcal{O}(\log n)$ binary search time!

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(\log n)$ — Each iteration divides the remaining search space in half.
- **Space Complexity**: $\mathcal{O}(1)$ — Only three integer pointers (`left`, `right`, `mid`) are tracked in memory.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|             Rotated Binary Search Architecture              |
+-------------------------------------------------------------+
| [4,  5,  6,  7,  0,  1,  2]       target = 0                |
|  L           M           R                                  |
|                                                             |
| Step 1: nums[L] (4) <= nums[M] (7) -> Left half is sorted!  |
| Step 2: Is target 0 inside [4 .. 7]? No!                    |
|         Therefore, target MUST be in the right half!        |
|         Set L = M + 1 (search range becomes [0, 1, 2])      |
|                                                             |
| Step 3: Recalculate mid -> nums[M] == 0 == target! Found!   |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public int search(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            // Found target!
            if (nums[mid] == target) {
                return mid;
            }

            // Check if the left half is normally sorted
            if (nums[left] <= nums[mid]) {
                // If target lies cleanly within the sorted left half
                if (target >= nums[left] && target < nums[mid]) {
                    right = mid - 1; // Search left
                } else {
                    left = mid + 1;  // Search right
                }
            } 
            // Otherwise, the right half must be normally sorted
            else {
                // If target lies cleanly within the sorted right half
                if (target > nums[mid] && target <= nums[right]) {
                    left = mid + 1;  // Search right
                } else {
                    right = mid - 1; // Search left
                }
            }
        }

        return -1; // Target not found
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `nums = [4, 5, 6, 7, 0, 1, 2]`, `target = 0`
  - $L=0, R=6 \rightarrow M=3$ (`nums[3] = 7`).
  - `nums[0] (4) <= nums[3] (7)`: Left half is sorted. Is $0$ between 4 and 7? No $\rightarrow L = M + 1 = 4$.
  - $L=4, R=6 \rightarrow M=5$ (`nums[5] = 1`).
  - `nums[4] (0) <= nums[5] (1)`: Left half `[0, 1]` is sorted. Is $0$ between 0 and 1? Yes $\rightarrow R = M - 1 = 4$.
  - $L=4, R=4 \rightarrow M=4$ (`nums[4] = 0`). Target matches! Returns index 4.
- **Data Structures Used & Why**:
  - Direct pointer indexing: Standard binary search pointers operate in-place without memory allocation.

---

## 18. Find Minimum in Rotated Sorted Array (LeetCode #153)

### Problem Introduction & Example
Suppose an array of length $n$ sorted in ascending order is rotated between 1 and $n$ times.
Given the sorted rotated array `nums` of unique elements, return the **minimum element** of this array.
You must write an algorithm that runs in $\mathcal{O}(\log n)$ time.

- **Example 1**:
  - Input: `nums = [3, 4, 5, 1, 2]`
  - Output: `1`
  - Explanation: The original sorted array was `[1, 2, 3, 4, 5]` rotated 3 times.

### High-Level Solution Intuition
In a non-rotated sorted array, elements always increase as you go right.
In a rotated array, there is exactly one "inflection cliff" where the largest number drops down to the smallest number (e.g. `5 -> 1`).
Our mission is to find that cliff using binary search:

Compare `nums[mid]` with the rightmost boundary `nums[right]`:
- **If `nums[mid] > nums[right]`**:
  This means the cliff must exist somewhere to the **right** of `mid` (because if the array were normally sorted, `mid` would be smaller than `right`). So the minimum is on the right $\rightarrow$ `left = mid + 1`.
- **If `nums[mid] <= nums[right]`**:
  This means the entire right portion from `mid` to `right` is properly sorted. The minimum is either at `mid` itself or somewhere to the left $\rightarrow$ `right = mid`.

When `left == right`, the search space has converged to the exact minimum element!

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(\log n)$ — Cuts the search space in half with each iteration.
- **Space Complexity**: $\mathcal{O}(1)$ — Operates strictly in-place with zero extra memory.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|              Find Minimum in Rotated Array                  |
+-------------------------------------------------------------+
| [3,  4,  5,  1,  2]                                         |
|  L       M       R                                          |
|                                                             |
| Compare nums[mid] (5) with nums[right] (2):                 |
| 5 > 2 -> Cliff drop is in RIGHT half!                       |
| Shift left = mid + 1                                        |
|                                                             |
| Search space becomes: [1, 2]                                |
|                        L  R                                 |
| nums[mid] (1) <= nums[right] (2) -> right = mid             |
| Left converges with Right at index 3 -> Value is 1!         |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public int findMin(int[] nums) {
        int left = 0;
        int right = nums.length - 1;

        while (left < right) {
            int mid = left + (right - left) / 2;

            // If mid is greater than right, the pivot cliff is on the right side
            if (nums[mid] > nums[right]) {
                left = mid + 1;
            } else {
                // Otherwise, the minimum is at mid or to the left of mid
                right = mid;
            }
        }

        return nums[left];
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `nums = [4, 5, 6, 7, 0, 1, 2]`
  - $L=0, R=6 \rightarrow M=3$ (`nums[3] = 7`). $7 > 2 \rightarrow L = 4$.
  - $L=4, R=6 \rightarrow M=5$ (`nums[5] = 1`). $1 \le 2 \rightarrow R = 5$.
  - $L=4, R=5 \rightarrow M=4$ (`nums[4] = 0`). $0 \le 1 \rightarrow R = 4$.
  - $L == R == 4$. Loop terminates. Return `nums[4] = 0`.
- **Data Structures Used & Why**:
  - Two pointers: Directly bisecting the array indices avoids recursion call overhead and runs in constant $\mathcal{O}(1)$ space.

---

## 19. Reverse Linked List (LeetCode #206)

### Problem Introduction & Example
Given the `head` of a singly linked list, reverse the list, and return the reversed list's new head.

- **Example**:
  - Input: `head = [1, 2, 3, 4, 5]`
  - Output: `[5, 4, 3, 2, 1]`
  - Explanation: Every node that pointed forward now points backward.

### High-Level Solution Intuition
**Visualizing Linked Lists**:
Think of a linked list like a train where each carriage is coupled to the next carriage:
`1 -> 2 -> 3 -> null`
To reverse the train, you cannot simply swap numbers in place; you must unhook each coupling link and reattach it to point in the opposite direction!

We use three pointers during the journey:
1. `prev` (initially `null`): The node that came before `curr`. This will become the new target of `curr.next`.
2. `curr` (initially `head`): The node currently having its link flipped.
3. `nextTemp`: A temporary holder to remember where the rest of the train is before we break the coupling link.

At each step:
- Remember the next node: `nextTemp = curr.next`.
- Flip the pointer: `curr.next = prev`.
- Advance `prev` to `curr`.
- Advance `curr` to `nextTemp`.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — We visit each node in the list once.
- **Space Complexity**: $\mathcal{O}(1)$ — Pointers are updated in-place without allocating new nodes.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                  In-Place List Reversal                     |
+-------------------------------------------------------------+
| null       1  ----->   2  ----->   3  -----> null           |
| prev      curr       next                                   |
|                                                             |
| Step 1: nextTemp = curr.next (Save 2)                       |
| Step 2: curr.next = prev     (1 points back to null)        |
| Step 3: prev = curr          (prev advances to 1)           |
| Step 4: curr = nextTemp      (curr advances to 2)           |
|                                                             |
| Repeat until curr == null -> prev is the new head!          |
+-------------------------------------------------------------+
```

### Java Program
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int val) { this.val = val; }
 * }
 */
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode curr = head;

        while (curr != null) {
            // Save the next node before we overwrite curr.next
            ListNode nextTemp = curr.next;

            // Reverse the link
            curr.next = prev;

            // Move pointers one step forward
            prev = curr;
            curr = nextTemp;
        }

        // When curr reaches null, prev is sitting at the new head of the reversed list
        return prev;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `1 -> 2 -> null`
  - Start: `prev = null, curr = 1`.
  - Iteration 1: `nextTemp = 2`, `1.next = null`, `prev = 1`, `curr = 2`.
  - Iteration 2: `nextTemp = null`, `2.next = 1`, `prev = 2`, `curr = null`.
  - Loop terminates. Return `prev` (Node 2). The list is now `2 -> 1 -> null`.
- **Data Structures Used & Why**:
  - Pointer references (`prev`, `curr`): In-place pointer redirection achieves $\mathcal{O}(1)$ space, compared to a recursive call stack which would consume $\mathcal{O}(n)$ memory.

---

## 20. Merge Two Sorted Lists (LeetCode #21)

### Problem Introduction & Example
You are given the heads of two sorted linked lists `list1` and `list2`. Merge the two lists into one sorted linked list by splicing together the existing nodes. Return the head of the merged list.

- **Example**:
  - Input: `list1 = [1, 2, 4]`, `list2 = [1, 3, 4]`
  - Output: `[1, 1, 2, 3, 4, 4]`

### High-Level Solution Intuition
Think of this like merging two already-sorted decks of playing cards:
Look at the top card of both decks. Whichever is smaller gets placed face down onto our merged pile, and we draw the next card from that deck. Repeat until one deck runs out.

**Beginner Pro-Tip (The Dummy Sentinel Node)**:
When building a new linked list, deciding what the first `head` node should be often requires awkward `if/else` checks.
To make code clean and bug-free, create a fake starting node called `dummy` (e.g. `new ListNode(-1)`).
Maintain a `tail` pointer starting at `dummy`. At each step, attach the smaller node to `tail.next` and advance `tail`.
At the end, simply return `dummy.next`!

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n + m)$ — Where $n$ and $m$ are the lengths of the two lists. We compare and advance through each node once.
- **Space Complexity**: $\mathcal{O}(1)$ — We reuse the existing nodes directly by updating their pointers.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                  Merge Two Sorted Lists                     |
+-------------------------------------------------------------+
| dummy -> [tail]                                             |
|                                                             |
| list1: 1 -> 2 -> 4                                          |
| list2: 1 -> 3 -> 4                                          |
|                                                             |
| 1 <= 1: tail.next = list1 (1), advance list1                |
| 2 > 1 : tail.next = list2 (1), advance list2                |
| 2 <= 3: tail.next = list1 (2), advance list1                |
| ...                                                         |
| Once one list runs dry: attach remaining tail in O(1)!      |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        // Create a dummy node to act as a permanent anchor for the start of the list
        ListNode dummy = new ListNode(-1);
        ListNode tail = dummy;

        // While both lists still have nodes to compare
        while (list1 != null && list2 != null) {
            if (list1.val <= list2.val) {
                tail.next = list1;
                list1 = list1.next;
            } else {
                tail.next = list2;
                list2 = list2.next;
            }
            tail = tail.next;
        }

        // Attach whatever remains of the non-empty list
        tail.next = (list1 != null) ? list1 : list2;

        return dummy.next;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `l1 = [1, 3]`, `l2 = [2]`
  - `dummy` anchor created.
  - Compare 1 and 2: attach 1. `l1` moves to 3.
  - Compare 3 and 2: attach 2. `l2` moves to null.
  - `l2` is empty: attach remaining of `l1` (node 3) directly to `tail.next`.
  - Result: `1 -> 2 -> 3`.
- **Data Structures Used & Why**:
  - Sentinel `dummy` node: Eliminates special cases when initializing the merged list head.

---

## 21. Reorder List (LeetCode #143)

### Problem Introduction & Example
You are given the head of a singly linked-list:
$L_0 \rightarrow L_1 \rightarrow \dots \rightarrow L_{n-1} \rightarrow L_n$
Reorder the list into the following interleaved order:
$L_0 \rightarrow L_n \rightarrow L_1 \rightarrow L_{n-1} \rightarrow L_2 \rightarrow L_{n-2} \rightarrow \dots$
You may not modify the values inside the nodes; you must physically re-link the nodes themselves.

- **Example**:
  - Input: `head = [1, 2, 3, 4]`
  - Output: `[1, 4, 2, 3]`

### High-Level Solution Intuition
Notice what the pattern is actually doing:
It takes the **first half** of the list in normal order (`1 -> 2`) and weaves it together with the **second half** of the list in **reversed order** (`4 -> 3`).

This gives us a crystal-clear 3-step game plan:
1. **Find the middle** of the list using Fast and Slow pointers.
2. **Reverse the second half** of the list.
3. **Merge the two halves alternately** (interleaving nodes 1 by 1).

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — Finding the middle takes $n/2$ steps, reversing the second half takes $n/2$ steps, and weaving the two halves takes $n$ steps.
- **Space Complexity**: $\mathcal{O}(1)$ — Pure in-place pointer updates.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                    Reorder List Workflow                    |
+-------------------------------------------------------------+
| 1. Find Middle: [1 -> 2 -> 3 -> 4]                          |
|    First Half:  1 -> 2 -> null                              |
|    Second Half: 3 -> 4 -> null                              |
|                                                             |
| 2. Reverse Second Half:                                     |
|    [3 -> 4] becomes [4 -> 3 -> null]                        |
|                                                             |
| 3. Interleave/Weave Together:                               |
|    1 ------> 2                                              |
|     \       /                                               |
|      v     v                                                |
|       4 --> 3                                               |
|    Result: 1 -> 4 -> 2 -> 3                                 |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public void reorderList(ListNode head) {
        if (head == null || head.next == null) return;

        // Step 1: Find the middle node using Slow & Fast pointers
        ListNode slow = head;
        ListNode fast = head;
        while (fast.next != null && fast.next.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }

        // Step 2: Split and reverse the second half
        ListNode secondHalf = slow.next;
        slow.next = null; // Disconnect the two halves

        ListNode prev = null;
        ListNode curr = secondHalf;
        while (curr != null) {
            ListNode nextTemp = curr.next;
            curr.next = prev;
            prev = curr;
            curr = nextTemp;
        }
        secondHalf = prev; // Head of reversed second half

        // Step 3: Interleave the two lists
        ListNode firstHalf = head;
        while (secondHalf != null) {
            ListNode temp1 = firstHalf.next;
            ListNode temp2 = secondHalf.next;

            firstHalf.next = secondHalf;
            secondHalf.next = temp1;

            firstHalf = temp1;
            secondHalf = temp2;
        }
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `[1, 2, 3, 4]`
  - Middle detected at node 2.
  - Second half `3 -> 4` reversed to `4 -> 3`.
  - Weave: `1` points to `4`, `4` points to `2`, `2` points to `3`. Result: `1 -> 4 -> 2 -> 3`.
- **Data Structures Used & Why**:
  - Slow and Fast pointers: Finds the list midpoint in a single pass without needing to count total length or allocate extra lists.

---

## 22. Remove Nth Node From End of List (LeetCode #19)

### Problem Introduction & Example
Given the `head` of a linked list, remove the $n^{th}$ node from the end of the list and return its head.

- **Example**:
  - Input: `head = [1, 2, 3, 4, 5]`, `n = 2`
  - Output: `[1, 2, 3, 5]`
  - Explanation: Counting from the back: 5 is 1st, 4 is 2nd. Removing node 4 gives `[1, 2, 3, 5]`.

### High-Level Solution Intuition
**How to find the Nth node from the end in one pass?**
Maintain two pointers, `fast` and `slow`, separated by a gap of exactly $n$ nodes:
1. Send `fast` ahead by $n + 1$ steps.
2. Now move both `fast` and `slow` forward at the exact same pace.
3. When `fast` falls off the end of the list (`null`), where is `slow`?
   Because `fast` was $n + 1$ nodes ahead, `slow` is sitting **directly in front of the node that needs to be deleted**!
4. Remove the node in one line: `slow.next = slow.next.next`.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(L)$ — Where $L$ is the length of the linked list (single pass).
- **Space Complexity**: $\mathcal{O}(1)$ — Constant pointer space.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                Two-Pointer Fixed-Gap Traversal              |
+-------------------------------------------------------------+
| dummy -> 1 -> 2 -> 3 -> 4 -> 5 -> null      (n = 2)         |
|                                                             |
| Step 1: Move fast ahead by n + 1 (3 steps):                 |
| dummy -> 1 -> 2 -> 3 -> 4 -> 5 -> null                      |
| slow               fast                                     |
|                                                             |
| Step 2: Move both until fast == null:                       |
| dummy -> 1 -> 2 -> 3 -> 4 -> 5 -> null                      |
|                    slow           fast                      |
|                                                             |
| Step 3: Delete node 4: slow.next = slow.next.next           |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        // Dummy node protects against deleting the head node
        ListNode dummy = new ListNode(0);
        dummy.next = head;

        ListNode fast = dummy;
        ListNode slow = dummy;

        // Move fast ahead by n + 1 steps to create the gap
        for (int i = 0; i <= n; i++) {
            fast = fast.next;
        }

        // Move both forward until fast reaches the end
        while (fast != null) {
            fast = fast.next;
            slow = slow.next;
        }

        // Delete the target node
        slow.next = slow.next.next;

        return dummy.next;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `head = [1, 2]`, `n = 1`
  - `dummy -> 1 -> 2 -> null`
  - `fast` moves 2 steps: lands on node 2.
  - `while(fast != null)`: `fast` moves to null, `slow` moves from dummy to node 1.
  - `slow.next = slow.next.next` (bypasses node 2 to null).
  - Return `dummy.next` $\rightarrow$ `[1]`.
- **Data Structures Used & Why**:
  - `dummy` sentinel node: Handles edge cases where the head itself is the node being removed.

---

## 23. Linked List Cycle (LeetCode #141)

### Problem Introduction & Example
Given `head`, the head of a linked list, determine if the linked list contains a **cycle** (loop).
A cycle occurs if some node in the list can be reached again by repeatedly following the `next` pointer.
Return `true` if there is a cycle, or `false` otherwise.

- **Example**:
  - Input: `head = [3, 2, 0, -4]`, where `-4` points back to `2`.
  - Output: `true`

### High-Level Solution Intuition
**The "Aha!" Breakthrough (Floyd's Tortoise and Hare Algorithm)**:
Imagine two runners on a circular race track:
- A slow runner (Tortoise) who moves 1 step at a time.
- A fast runner (Hare) who moves 2 steps at a time.

If the track is straight (no cycle), the fast runner will quickly reach the finish line (`null`) and stop.
However, if the track has a loop, both runners will enter the loop. Because the fast runner closes the gap between them by 1 step in every tick, the fast runner is **guaranteed to eventually lap and collide with the slow runner**!

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — If there is no cycle, `fast` reaches null in $n/2$ steps. If there is a cycle, `fast` catches `slow` within at most $n$ iterations inside the loop.
- **Space Complexity**: $\mathcal{O}(1)$ — No hash set is needed; we only store two pointer references.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                 Floyd's Tortoise and Hare                   |
+-------------------------------------------------------------+
|      3  ----> 2  ----> 0  ----> -4                          |
|               ^                  |                          |
|               +------------------+                          |
|                                                             |
| Step 0: slow at 3,  fast at 3                               |
| Step 1: slow at 2,  fast at 0                               |
| Step 2: slow at 0,  fast at 2                               |
| Step 3: slow at -4, fast at -4  --> COLLISION! Cycle found! |
+-------------------------------------------------------------+
```

### Java Program
```java
public class Solution {
    public boolean hasCycle(ListNode head) {
        if (head == null || head.next == null) {
            return false;
        }

        ListNode slow = head;
        ListNode fast = head;

        while (fast != null && fast.next != null) {
            slow = slow.next;         // Moves 1 step
            fast = fast.next.next;    // Moves 2 steps

            // If fast and slow meet, there is a cycle
            if (slow == fast) {
                return true;
            }
        }

        // Fast reached null, so list has an end (no cycle)
        return false;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `1 -> 2 -> loop back to 1`
  - Start: `slow = 1, fast = 1`.
  - Step 1: `slow = 2`, `fast = 1` (moved 2 steps: $1 \rightarrow 2 \rightarrow 1$).
  - Step 2: `slow = 1`, `fast = 1` (moved 2 steps: $1 \rightarrow 2 \rightarrow 1$).
  - `slow == fast` collision! Returns `true`.
- **Data Structures Used & Why**:
  - Two pointers: Eliminates the $\mathcal{O}(n)$ space required by a `HashSet<ListNode>`, achieving $\mathcal{O}(1)$ space complexity.

---

## 24. Merge k Sorted Lists (LeetCode #23)

### Problem Introduction & Example
You are given an array of `k` linked-lists, where each individual linked-list is already sorted in ascending order.
Merge all `k` linked-lists into one single sorted linked-list and return it.

- **Example**:
  - Input: `lists = [[1, 4, 5], [1, 3, 4], [2, 6]]`
  - Output: `[1, 1, 2, 3, 4, 4, 5, 6]`

### High-Level Solution Intuition
At any given moment, the absolute smallest remaining node across all $k$ lists must be sitting at the head of one of those $k$ lists.

**The "Aha!" Breakthrough (Min-Heap / PriorityQueue)**:
Instead of scanning all $k$ heads manually in $\mathcal{O}(k)$ time to pick the smallest:
1. Put the head of each non-empty list into a **Min-Heap (PriorityQueue)**.
2. The Min-Heap instantly serves up the smallest node in $\mathcal{O}(\log k)$ time!
3. Pop that smallest node, attach it to our merged list.
4. If that popped node had a `next` node behind it in its original list, insert `next` into the heap.
5. Repeat until the heap is empty!

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(N \log k)$ — Where $N$ is the total number of nodes across all lists, and $k$ is the number of linked lists. Inserting and extracting from a heap of size $k$ takes $\mathcal{O}(\log k)$ time per node.
- **Space Complexity**: $\mathcal{O}(k)$ — The priority queue stores at most $k$ node references at any point in time.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                 Min-Heap Merge k Lists                      |
+-------------------------------------------------------------+
| Min-Heap (size <= k):                                       |
| [ Node(1, list1), Node(1, list2), Node(2, list3) ]          |
|                                                             |
| Step 1: Poll smallest node (1 from list1)                   |
| Step 2: Attach to merged tail                               |
| Step 3: Push list1.next (Node(4)) into Min-Heap             |
| Step 4: Repeat until heap is empty!                         |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.PriorityQueue;

class Solution {
    public ListNode mergeKLists(ListNode[] lists) {
        if (lists == null || lists.length == 0) return null;

        // Min-Heap comparing node values
        PriorityQueue<ListNode> minHeap = new PriorityQueue<>((a, b) -> a.val - b.val);

        // Add the head of each non-empty list into the heap
        for (ListNode node : lists) {
            if (node != null) {
                minHeap.offer(node);
            }
        }

        ListNode dummy = new ListNode(0);
        ListNode tail = dummy;

        // Repeatedly extract smallest node and replenish from the same list
        while (!minHeap.isEmpty()) {
            ListNode smallest = minHeap.poll();
            tail.next = smallest;
            tail = tail.next;

            if (smallest.next != null) {
                minHeap.offer(smallest.next);
            }
        }

        return dummy.next;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `lists = [[1, 4], [2, 5]]`
  - Heap holds: `[1, 2]`.
  - Poll 1 $\rightarrow$ attach 1. Offer 4 into heap. Heap: `[2, 4]`.
  - Poll 2 $\rightarrow$ attach 2. Offer 5 into heap. Heap: `[4, 5]`.
  - Poll 4 $\rightarrow$ attach 4. Heap: `[5]`.
  - Poll 5 $\rightarrow$ attach 5. Heap: `[]`.
  - Output: `1 -> 2 -> 4 -> 5`.
- **Data Structures Used & Why**:
  - `PriorityQueue<ListNode>`: Keeps track of the smallest node among $k$ candidates in $\mathcal{O}(\log k)$ instead of an $\mathcal{O}(k)$ linear search across all heads, yielding significant performance gains when $k$ is large.


# Category 4: Trees & Tries

---

## 25. Invert Binary Tree (LeetCode #226)

### Problem Introduction & Example
Given the `root` of a binary tree, invert the tree (turn it into its mirror image) and return its root.

- **Example**:
  - Input: `root = [4, 2, 7, 1, 3, 6, 9]`
  - Output: `[4, 7, 2, 9, 6, 3, 1]`
  - Explanation: Every node's left child becomes its right child, and its right child becomes its left child.

### High-Level Solution Intuition
**Visualizing Tree Inversion**:
Think of holding the tree up in front of a mirror:
For every single node in the tree:
1. Swap its left child pointer and right child pointer.
2. Recursively do the exact same swap for its left subtree.
3. Recursively do the exact same swap for its right subtree.

The base case is when you reach an empty leaf (`null`), in which case there is nothing to swap, so you simply return `null`.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — We visit every node in the binary tree exactly once to swap its children.
- **Space Complexity**: $\mathcal{O}(h)$ — Where $h$ is the height of the tree. This corresponds to the memory allocated on the call stack by recursion ($\mathcal{O}(\log n)$ for balanced trees, $\mathcal{O}(n)$ for skewed trees).

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                  Invert Binary Tree DFS                     |
+-------------------------------------------------------------+
|          4                               4                  |
|        /   \                           /   \                |
|       2     7          ===>            7     2              |
|      / \   / \                       / \   / \              |
|     1   3 6   9                     9   6 3   1             |
|                                                             |
| Invert Function:                                            |
|   If node == null: return null                              |
|   Swap(node.left, node.right)                               |
|   Invert(node.left)                                         |
|   Invert(node.right)                                        |
|   Return node                                               |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public TreeNode invertTree(TreeNode root) {
        // Base case: an empty tree or leaf child requires no action
        if (root == null) {
            return null;
        }

        // Step 1: Swap the left and right children of current node
        TreeNode temp = root.left;
        root.left = root.right;
        root.right = temp;

        // Step 2: Recursively invert the subtrees
        invertTree(root.left);
        invertTree(root.right);

        return root;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: Tree `[2, 1, 3]`
  - At root 2: swap child 1 and child 3 $\rightarrow$ left is now 3, right is now 1.
  - Recurse on 3: leaf node, returns 3.
  - Recurse on 1: leaf node, returns 1.
  - Output: `[2, 3, 1]`.
- **Data Structures Used & Why**:
  - Implicit recursion call stack: Exploits the natural recursive definition of a binary tree without needing to manage an explicit queue or stack.

---

## 26. Maximum Depth of Binary Tree (LeetCode #104)

### Problem Introduction & Example
Given the `root` of a binary tree, return its maximum depth.
The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

- **Example**:
  - Input: `root = [3, 9, 20, null, null, 15, 7]`
  - Output: `3` (Path: `3 -> 20 -> 15` or `3 -> 20 -> 7`).

### High-Level Solution Intuition
**Divide and Conquer**:
If you know the maximum depth of your left subtree and the maximum depth of your right subtree, what is the maximum depth at your current node?
It is simply:
$$\text{depth} = 1 + \max(\text{leftDepth}, \text{rightDepth})$$
The `1` counts your current node, and `Math.max()` picks whichever branch goes deeper.
Base case: If a node is `null`, its depth is `0`.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — Every node is visited once.
- **Space Complexity**: $\mathcal{O}(h)$ — Equal to the maximum recursion depth, which is the height of the tree $h \le n$.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                     Max Depth Postorder                     |
+-------------------------------------------------------------+
|        3               maxDepth(3) = 1 + max(left, right)   |
|       / \                                                   |
|      9   20            maxDepth(9) = 1                      |
|         /  \           maxDepth(20) = 1 + max(1, 1) = 2    |
|        15   7          -> Result at root = 1 + 2 = 3        |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public int maxDepth(TreeNode root) {
        // Base case: empty tree has depth 0
        if (root == null) {
            return 0;
        }

        // Recursively compute the depth of both children
        int leftDepth = maxDepth(root.left);
        int rightDepth = maxDepth(root.right);

        // Current node's depth is 1 + the greater of the two child depths
        return 1 + Math.max(leftDepth, rightDepth);
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: Root 3 with child 9 (leaf) and child 20 (with leaves 15 and 7).
  - Node 9: leaves are null $\rightarrow$ returns $1 + \max(0, 0) = 1$.
  - Node 15 and Node 7: return 1.
  - Node 20: returns $1 + \max(1, 1) = 2$.
  - Node 3: returns $1 + \max(1, 2) = 3$.
- **Data Structures Used & Why**:
  - Recursion call frame: Resolves subtrees bottom-up with minimal memory overhead.

---

## 27. Same Tree (LeetCode #100)

### Problem Introduction & Example
Given the roots of two binary trees `p` and `q`, write a function to check if they are identical or not.
Two binary trees are considered identical if they are structurally the same and their corresponding nodes have the same value.

- **Example 1**: `p = [1, 2, 3]`, `q = [1, 2, 3]` $\rightarrow$ `true`
- **Example 2**: `p = [1, 2]`, `q = [1, null, 2]` $\rightarrow$ `false`

### High-Level Solution Intuition
To compare two trees, traverse them simultaneously:
1. If both nodes are `null`, they match! Return `true`.
2. If only one node is `null`, or if their values differ (`p.val != q.val`), they don't match! Return `false`.
3. Check both branches: both the left subtrees MUST match AND the right subtrees MUST match.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(\min(N, M))$ — Where $N$ and $M$ are the number of nodes in each tree.
- **Space Complexity**: $\mathcal{O}(\min(H_p, H_q))$ — Call stack depth bounded by tree height.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                      Same Tree Compare                      |
+-------------------------------------------------------------+
| If p == null && q == null: return true                      |
| If p == null || q == null: return false                     |
| If p.val != q.val:         return false                     |
|                                                             |
| Return isSameTree(p.left, q.left) &&                        |
|        isSameTree(p.right, q.right)                         |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public boolean isSameTree(TreeNode p, TreeNode q) {
        // Both are null -> Identical
        if (p == null && q == null) {
            return true;
        }

        // One is null while the other is not, or values differ
        if (p == null || q == null || p.val != q.val) {
            return false;
        }

        // Both left and right subtrees must match
        return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `p = [1, 2]`, `q = [1, null, 2]`
  - Compare root: `1 == 1` $\rightarrow$ proceed.
  - Compare left: `p.left = 2`, `q.left = null` $\rightarrow$ mismatch! Returns `false`.
- **Data Structures Used & Why**:
  - Recursion: Synchronized step-by-step traversal compares structures directly without requiring serialization into strings.

---

## 28. Subtree of Another Tree (LeetCode #572)

### Problem Introduction & Example
Given the roots of two binary trees `root` and `subRoot`, return `true` if there is a subtree of `root` that has the exact same structure and node values as `subRoot`, and `false` otherwise.

- **Example**:
  - Input: `root = [3, 4, 5, 1, 2]`, `subRoot = [4, 1, 2]`
  - Output: `true` (The subtree starting at node 4 in `root` is identical to `subRoot`).

### High-Level Solution Intuition
A tree `subRoot` is a subtree of `root` if:
1. `root` itself is identical to `subRoot` (we can reuse the `isSameTree` helper from Problem 27!), OR
2. `subRoot` matches somewhere in the **left subtree** of `root`, OR
3. `subRoot` matches somewhere in the **right subtree** of `root`.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(N \times M)$ — Where $N$ is the number of nodes in `root` and $M$ is the number of nodes in `subRoot`.
- **Space Complexity**: $\mathcal{O}(H)$ — Recursion call stack depth bounded by the height of `root`.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                  Subtree Check Pipeline                     |
+-------------------------------------------------------------+
| isSubtree(root, subRoot):                                   |
|    If root == null: return false                            |
|    If isSame(root, subRoot): return true                    |
|    Return isSubtree(root.left, subRoot) ||                  |
|           isSubtree(root.right, subRoot)                    |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public boolean isSubtree(TreeNode root, TreeNode subRoot) {
        if (root == null) return false;

        // Check if trees are identical starting from current node
        if (isSame(root, subRoot)) return true;

        // Otherwise check in left or right subtrees
        return isSubtree(root.left, subRoot) || isSubtree(root.right, subRoot);
    }

    private boolean isSame(TreeNode a, TreeNode b) {
        if (a == null && b == null) return true;
        if (a == null || b == null || a.val != b.val) return false;

        return isSame(a.left, b.left) && isSame(a.right, b.right);
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `root = [3, 4, 5, 1, 2]`, `subRoot = [4, 1, 2]`
  - Check at root 3: values differ ($3 \ne 4$).
  - Recurse left to node 4: `isSame(node 4, subRoot 4)` evaluates to `true`!
  - Return `true`.
- **Data Structures Used & Why**:
  - Mutual recursion: Reuses the `isSame` primitive across all nodes cleanly.

---

## 29. Lowest Common Ancestor of a Binary Search Tree (LeetCode #235)

### Problem Introduction & Example
Given a **Binary Search Tree (BST)**, find the **Lowest Common Ancestor (LCA)** node of two given nodes `p` and `q`.
The LCA is defined as the lowest node in the tree that has both `p` and `q` as descendants (where a node can be a descendant of itself).

- **Example**:
  - Input: `root = [6, 2, 8, 0, 4, 7, 9]`, `p = 2`, `q = 8`
  - Output: `6` (Node 6 is the ancestor where paths to 2 and 8 diverge).

### High-Level Solution Intuition
**Take advantage of the BST Invariant**:
In a BST, for any node `curr`:
- All values in its left subtree are **smaller** than `curr.val`.
- All values in its right subtree are **larger** than `curr.val`.

Starting at `root`:
- If both `p.val` and `q.val` are **smaller** than `curr.val`, then both targets must be in the **left subtree** $\rightarrow$ `curr = curr.left`.
- If both `p.val` and `q.val` are **larger** than `curr.val`, then both targets must be in the **right subtree** $\rightarrow$ `curr = curr.right`.
- If one value is smaller and one is larger (or one equals `curr.val`), **they split here**! This split point is guaranteed to be their Lowest Common Ancestor!

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(h)$ — Where $h$ is tree height ($\mathcal{O}(\log n)$ for balanced trees, $\mathcal{O}(n)$ worst case).
- **Space Complexity**: $\mathcal{O}(1)$ — Can be written iteratively with zero extra memory.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                      BST LCA Invariant                      |
+-------------------------------------------------------------+
|         6  <-- Both p(2) and q(8) split here! LCA is 6.     |
|       /   \                                                 |
|      2     8                                                |
|     / \   / \                                               |
|    0   4 7   9                                              |
|                                                             |
| While curr != null:                                         |
|    If p, q < curr.val  -> curr = curr.left                  |
|    If p, q > curr.val  -> curr = curr.right                 |
|    Else                -> return curr (Split point found!)  |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        TreeNode curr = root;

        while (curr != null) {
            // Both nodes lie in the left subtree
            if (p.val < curr.val && q.val < curr.val) {
                curr = curr.left;
            }
            // Both nodes lie in the right subtree
            else if (p.val > curr.val && q.val > curr.val) {
                curr = curr.right;
            }
            // Split point reached: this node is the LCA
            else {
                return curr;
            }
        }

        return null;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `root = 6`, `p = 2`, `q = 4`
  - At 6: both 2 and 4 are $< 6 \rightarrow$ move to `curr.left` (node 2).
  - At 2: $p=2 == curr.val$. Split condition triggers! Return node 2.
- **Data Structures Used & Why**:
  - Pointer iteration: Navigating the tree via a `while` loop avoids recursive call frames, achieving $\mathcal{O}(1)$ space.

---

## 30. Binary Tree Level Order Traversal (LeetCode #102)

### Problem Introduction & Example
Given the `root` of a binary tree, return the level order traversal of its nodes' values (i.e. from left to right, level by level).

- **Example**:
  - Input: `root = [3, 9, 20, null, null, 15, 7]`
  - Output: `[[3], [9, 20], [15, 7]]`

### High-Level Solution Intuition
**Breadth-First Search (BFS) with a Queue**:
Think of this like water rippling outward in waves:
1. Place the root in a FIFO `Queue`.
2. In each iteration of the while loop, check `queue.size()`. This size tells you **exactly how many nodes belong to the current horizontal level**.
3. Loop through that exact size: poll each node, record its value, and enqueue its left and right children.
4. Add that level's list to the final result, and proceed to the next wave!

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — Every node is inserted into and removed from the queue once.
- **Space Complexity**: $\mathcal{O}(n)$ — The widest level in a full binary tree holds up to $n/2$ nodes in the queue.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                      BFS Level Order                        |
+-------------------------------------------------------------+
| Queue starts: [3]                                           |
| Wave 0 (size 1): Poll 3 -> add [3]. Enqueue 9, 20           |
| Wave 1 (size 2): Poll 9, Poll 20 -> add [9, 20]. Enqueue 15,7|
| Wave 2 (size 2): Poll 15, Poll 7 -> add [15, 7]             |
| Queue empty -> Return [[3], [9, 20], [15, 7]]               |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.*;

class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> result = new ArrayList<>();
        if (root == null) return result;

        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);

        while (!queue.isEmpty()) {
            int levelSize = queue.size();
            List<Integer> currentLevel = new ArrayList<>(levelSize);

            // Process all nodes that belong to the current horizontal level
            for (int i = 0; i < levelSize; i++) {
                TreeNode curr = queue.poll();
                currentLevel.add(curr.val);

                if (curr.left != null) queue.offer(curr.left);
                if (curr.right != null) queue.offer(curr.right);
            }

            result.add(currentLevel);
        }

        return result;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `[3, 9, 20]`
  - Queue: `[3]`. Size = 1. Poll 3. Add children 9, 20. Level: `[3]`.
  - Queue: `[9, 20]`. Size = 2. Poll 9, Poll 20. Level: `[9, 20]`.
  - Result: `[[3], [9, 20]]`.
- **Data Structures Used & Why**:
  - `Queue<TreeNode>` (LinkedList): FIFO order ensures nodes are processed in horizontal order. Snapshotting `queue.size()` cleanly partitions nodes into separate levels.

---

## 31. Validate Binary Search Tree (LeetCode #98)

### Problem Introduction & Example
Given the `root` of a binary tree, determine if it is a valid **Binary Search Tree (BST)**.
A valid BST must satisfy:
- The left subtree of a node contains only nodes with keys **less than** the node's key.
- The right subtree of a node contains only nodes with keys **greater than** the node's key.
- Both the left and right subtrees must also be binary search trees.

- **Example 1**: `root = [2, 1, 3]` $\rightarrow$ `true`
- **Example 2**: `root = [5, 1, 4, null, null, 3, 6]` $\rightarrow$ `false` (Root is 5, but its right child is 4).

### High-Level Solution Intuition
**A Common Beginner Trap**:
It is not enough to just check if `node.left.val < node.val < node.right.val`!
Consider this tree:
```
    10
   /  \
  5    15
      /  \
     6    20
```
Here, 6 is smaller than 15, but 6 is in the right subtree of 10! Because $6 < 10$, this tree is **invalid**.
Every node must satisfy boundaries passed down by **all of its ancestors**.

**The "Aha!" Breakthrough (The Bounding Box)**:
As you traverse down the tree, pass down a valid range `(minLimit, maxLimit)`:
- Root starts with `(-infinity, +infinity)`.
- When you go left, the upper limit shrinks: `maxLimit = node.val`.
- When you go right, the lower limit expands: `minLimit = node.val`.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — Every node is checked once.
- **Space Complexity**: $\mathcal{O}(h)$ — Recursion call stack depth bounded by tree height.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                 BST Validity Bounding Box                   |
+-------------------------------------------------------------+
|                  ( -inf < 5 < +inf )                        |
|                           5                                 |
|                         /   \                               |
|        ( -inf < 1 < 5 )      ( 5 < 4 < +inf )               |
|               1                       4  <-- VIOLATION!     |
|                                                             |
| validate(node, min, max):                                   |
|   If node == null: return true                              |
|   If node.val <= min || node.val >= max: return false       |
|   Return validate(node.left, min, node.val) &&              |
|          validate(node.right, node.val, max)                |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public boolean isValidBST(TreeNode root) {
        return validate(root, null, null);
    }

    private boolean validate(TreeNode node, Integer min, Integer max) {
        if (node == null) {
            return true;
        }

        // Check if current node violates lower or upper boundary
        if ((min != null && node.val <= min) || (max != null && node.val >= max)) {
            return false;
        }

        // Left child must be < node.val; right child must be > node.val
        return validate(node.left, min, node.val) && 
               validate(node.right, node.val, max);
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `[2, 1, 3]`
  - Root 2: bounds `(null, null)` $\rightarrow$ Valid.
  - Left 1: bounds `(null, 2)`: $1 < 2 \rightarrow$ Valid.
  - Right 3: bounds `(2, null)`: $3 > 2 \rightarrow$ Valid.
  - Returns `true`.
- **Data Structures Used & Why**:
  - `Integer` wrapper objects: Passing `null` bounds avoids overflow problems with `Integer.MIN_VALUE` and `Integer.MAX_VALUE`.

---

## 32. Kth Smallest Element in a BST (LeetCode #230)

### Problem Introduction & Example
Given the `root` of a binary search tree and an integer `k`, return the $k^{th}$ smallest value (1-indexed) among all the node values in the tree.

- **Example**:
  - Input: `root = [3, 1, 4, null, 2]`, `k = 1`
  - Output: `1`

### High-Level Solution Intuition
**In-Order Traversal Magic**:
An **In-Order Traversal** (Left $\rightarrow$ Root $\rightarrow$ Right) on a Binary Search Tree always visits nodes in **strictly ascending order**!
If you simulate an in-order traversal with a stack:
- Every time you pop a node, it is the next smallest number in the tree!
- Decrement $k$.
- When $k$ reaches $0$, that popped node is your answer. You can stop immediately without traversing the rest of the tree!

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(h + k)$ — We dive to the leftmost leaf in $\mathcal{O}(h)$ time and pop $k$ nodes.
- **Space Complexity**: $\mathcal{O}(h)$ — The stack holds at most the height of the tree.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                     In-Order BST Stack                      |
+-------------------------------------------------------------+
|        3               Stack dives left: [3, 1]             |
|       / \              Pop 1 -> k = 1 - 1 = 0!              |
|      1   4             k == 0 -> Found! Return 1            |
|       \                                                     |
|        2                                                    |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.ArrayDeque;
import java.util.Deque;

class Solution {
    public int kthSmallest(TreeNode root, int k) {
        Deque<TreeNode> stack = new ArrayDeque<>();
        TreeNode curr = root;

        while (curr != null || !stack.isEmpty()) {
            // Push all left children to reach the smallest element
            while (curr != null) {
                stack.push(curr);
                curr = curr.left;
            }

            // Pop smallest element
            curr = stack.pop();
            k--;

            // When k reaches 0, we found the kth smallest element
            if (k == 0) {
                return curr.val;
            }

            // Move to right subtree
            curr = curr.right;
        }

        return -1;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `root = [3, 1, 4, null, 2]`, `k = 2`
  - Push 3, push 1.
  - Pop 1: $k = 2 - 1 = 1$. Move right of 1 to node 2. Push 2.
  - Pop 2: $k = 1 - 1 = 0 \rightarrow$ Return 2!
- **Data Structures Used & Why**:
  - `ArrayDeque<TreeNode>`: Iterative in-order traversal allows early exit the instant $k$ reaches 0, saving time.

---

## 33. Construct Binary Tree from Preorder and Inorder Traversal (LeetCode #105)

### Problem Introduction & Example
Given two integer arrays `preorder` and `inorder` representing the preorder and inorder traversals of the same binary tree, reconstruct and return the binary tree.

- **Example**:
  - Input: `preorder = [3, 9, 20, 15, 7]`, `inorder = [9, 3, 15, 20, 7]`
  - Output: `[3, 9, 20, null, null, 15, 7]`

### High-Level Solution Intuition
1. **Preorder Traversal** is: `[ Root | Left Subtree | Right Subtree ]`.
   The very first element in `preorder` is **always the root** of the current subtree!
2. **Inorder Traversal** is: `[ Left Subtree | Root | Right Subtree ]`.
   Finding that root value inside `inorder` splits the tree in half:
   - Everything to the left of the root in `inorder` belongs to the left subtree!
   - Everything to the right belongs to the right subtree!
3. Pre-populate a `HashMap` with `(value -> inorderIndex)` to find root positions in $\mathcal{O}(1)$ time.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — Building the hash map takes $\mathcal{O}(n)$. Constructing each of the $n$ nodes takes $\mathcal{O}(1)$ time.
- **Space Complexity**: $\mathcal{O}(n)$ — To store the hash map and the recursion stack.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|             Preorder / Inorder Reconstruction               |
+-------------------------------------------------------------+
| Preorder: [ 3 |  9  |  20, 15, 7 ]                          |
|            Root  Left    Right                              |
|                                                             |
| Inorder:  [  9  | 3 |  15, 20, 7 ]                          |
|             Left Root    Right                              |
|                                                             |
| 1. Root = 3                                                 |
| 2. Inorder index of 3 is 1 -> Left size = 1                 |
| 3. Recurse left with [9], recurse right with [20, 15, 7]    |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    private Map<Integer, Integer> inorderIndexMap;
    private int preorderIndex = 0;

    public TreeNode buildTree(int[] preorder, int[] inorder) {
        // Map inorder values to their indices for O(1) lookups
        inorderIndexMap = new HashMap<>();
        for (int i = 0; i < inorder.length; i++) {
            inorderIndexMap.put(inorder[i], i);
        }

        return buildSubtree(preorder, 0, inorder.length - 1);
    }

    private TreeNode buildSubtree(int[] preorder, int inStart, int inEnd) {
        if (inStart > inEnd) {
            return null;
        }

        int rootVal = preorder[preorderIndex++];
        TreeNode root = new TreeNode(rootVal);

        int inIndex = inorderIndexMap.get(rootVal);

        // Build left subtree first because preorder is (Root, Left, Right)
        root.left = buildSubtree(preorder, inStart, inIndex - 1);
        root.right = buildSubtree(preorder, inIndex + 1, inEnd);

        return root;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `preorder = [3, 9, 20]`, `inorder = [9, 3, 20]`
  - `rootVal = 3`. `inorderIndexMap.get(3) = 1`.
  - Left subtree: range `[0, 0]` $\rightarrow$ node 9.
  - Right subtree: range `[2, 2]` $\rightarrow$ node 20.
  - Result: `[3, 9, 20]`.
- **Data Structures Used & Why**:
  - `HashMap<Integer, Integer>`: Prevents repeated linear scans of `inorder` to locate the root, keeping overall runtime strictly linear $\mathcal{O}(n)$.

---

## 34. Binary Tree Maximum Path Sum (LeetCode #124)

### Problem Introduction & Example
A path in a binary tree is a sequence of nodes where each adjacent pair is connected by an edge. A node can only appear at most once in a path. The path does not need to pass through the root.
Return the **maximum path sum** of any non-empty path.

- **Example**:
  - Input: `root = [-10, 9, 20, null, null, 15, 7]`
  - Output: `42`
  - Explanation: The optimal path is `15 -> 20 -> 7`, which sums to $15 + 20 + 7 = 42$.

### High-Level Solution Intuition
For any node `X`, there are two distinct concepts:
1. **The Turning Point Path**: `X` acts as the highest "peak" or arch connecting its left branch and right branch:
   $$\text{archSum} = X.val + \text{gain}(X.left) + \text{gain}(X.right)$$
   This path cannot be extended further upward to `X`'s parent.
2. **The Branch Gain to Parent**: `X` can only offer **one** single branch upward to its parent:
   $$\text{branchGain} = X.val + \max(\text{gain}(X.left), \text{gain}(X.right))$$

If a child branch produces a negative sum, we clamp it to `0` (we choose not to include it).

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — Every node is visited once in post-order traversal.
- **Space Complexity**: $\mathcal{O}(h)$ — Recursion call stack depth.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                  Max Path Sum Post-Order                    |
+-------------------------------------------------------------+
|              -10                                            |
|             /    \                                          |
|            9      20                                        |
|                  /  \                                       |
|                 15   7                                      |
|                                                             |
| At node 20:                                                 |
|    gain(15) = 15, gain(7) = 7                               |
|    Arch path = 20 + 15 + 7 = 42! Update global max.         |
|    Return to parent = 20 + max(15, 7) = 35                  |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    private int maxSum = Integer.MIN_VALUE;

    public int maxPathSum(TreeNode root) {
        calculateMaxGain(root);
        return maxSum;
    }

    private int calculateMaxGain(TreeNode node) {
        if (node == null) return 0;

        // Discard negative branch contributions by clamping to 0
        int leftGain = Math.max(0, calculateMaxGain(node.left));
        int rightGain = Math.max(0, calculateMaxGain(node.right));

        // Path where current node is the highest turning peak
        int currentPathSum = node.val + leftGain + rightGain;
        maxSum = Math.max(maxSum, currentPathSum);

        // Return single branch path extendable to parent
        return node.val + Math.max(leftGain, rightGain);
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `[-10, 9, 20, null, null, 15, 7]`
  - Leaf 15 returns 15; leaf 7 returns 7.
  - Node 20: arch sum $= 20 + 15 + 7 = 42 \rightarrow maxSum = 42$. Returns $20 + 15 = 35$ to parent.
  - Leaf 9 returns 9.
  - Node -10: arch sum $= -10 + 9 + 35 = 34 < 42$.
  - Result: 42.
- **Data Structures Used & Why**:
  - Global variable `maxSum`: Separates the returned branch value from the local peak calculation.

---

## 35. Serialize and Deserialize Binary Tree (LeetCode #297)

### Problem Introduction & Example
Design an algorithm to serialize a binary tree into a string and deserialize that string back into the original binary tree structure.

- **Example**:
  - Input: `root = [1, 2, 3, null, null, 4, 5]`
  - Encoded: `"1,2,X,X,3,4,X,X,5,X,X"`
  - Decoded: Original tree reconstructed.

### High-Level Solution Intuition
Use **Preorder DFS** traversal:
- **Serialize**:
  - If a node is `null`, append `"X,"`.
  - Else, append `node.val + ","`, then recurse left and right.
- **Deserialize**:
  - Split the string by comma and place the tokens into a FIFO `Queue`.
  - Recursively rebuild: poll token; if `"X"`, return `null`. Otherwise create the node and recursively wire its `left` and `right`.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — Every node is encoded and decoded once.
- **Space Complexity**: $\mathcal{O}(n)$ — For the serialized string and the recursion queue.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|               Preorder Serialization Pipeline               |
+-------------------------------------------------------------+
|         1                                                   |
|        / \       Encode:                                    |
|       2   3      1,2,X,X,3,4,X,X,5,X,X                      |
|          / \                                                |
|         4   5    Decode:                                    |
|                  Poll "1" -> new Node(1)                    |
|                  left: poll "2" -> left="X", right="X"      |
|                  right: poll "3" -> left="4", right="5"     |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.*;

public class Codec {
    private static final String NULL_NODE = "X";
    private static final String DELIMITER = ",";

    // Encodes a tree to a single string.
    public String serialize(TreeNode root) {
        StringBuilder sb = new StringBuilder();
        serializeHelper(root, sb);
        return sb.toString();
    }

    private void serializeHelper(TreeNode node, StringBuilder sb) {
        if (node == null) {
            sb.append(NULL_NODE).append(DELIMITER);
            return;
        }
        sb.append(node.val).append(DELIMITER);
        serializeHelper(node.left, sb);
        serializeHelper(node.right, sb);
    }

    // Decodes your encoded data to tree.
    public TreeNode deserialize(String data) {
        Queue<String> nodes = new LinkedList<>(Arrays.asList(data.split(DELIMITER)));
        return deserializeHelper(nodes);
    }

    private TreeNode deserializeHelper(Queue<String> nodes) {
        String val = nodes.poll();
        if (val == null || val.equals(NULL_NODE)) {
            return null;
        }

        TreeNode node = new TreeNode(Integer.parseInt(val));
        node.left = deserializeHelper(nodes);
        node.right = deserializeHelper(nodes);
        return node;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: Tree `[1, 2]`
  - Encoded: `"1,2,X,X,X"`
  - Queue: `["1", "2", "X", "X", "X"]`
  - Poll 1 $\rightarrow$ create Node(1). Left polls 2 $\rightarrow$ Node(2). Left and right of 2 poll "X" (null).
  - Right of 1 polls "X" (null).
  - Tree fully restored!
- **Data Structures Used & Why**:
  - `Queue<String>`: FIFO polling mirrors the preorder recursive call sequence.

---

## 36. Implement Trie (Prefix Tree) (LeetCode #208)

### Problem Introduction & Example
A **Trie** (pronounced "try") or prefix tree is a specialized tree structure used for storing strings to enable fast prefix matching, such as autocomplete and spell checkers.
Implement the `Trie` class with `insert`, `search`, and `startsWith`.

- **Example**:
  - `insert("apple")`
  - `search("apple")` $\rightarrow$ `true`
  - `search("app")` $\rightarrow$ `false`
  - `startsWith("app")` $\rightarrow$ `true`

### High-Level Solution Intuition
Each Trie node represents a character transition and contains:
1. An array of child pointers `children = new TrieNode[26]`.
2. A boolean `isEndOfWord` indicating if a complete word terminates here.
- **Insert**: Walk character by character, creating child nodes as needed. Mark the last node `isEndOfWord = true`.
- **Search**: Follow characters. If any child is null, return `false`. At the end, check `isEndOfWord`.
- **StartsWith**: Same as search, but only requires reaching the end of the prefix.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(L)$ for all operations, where $L$ is word length.
- **Space Complexity**: $\mathcal{O}(N \times 26)$ — Where $N$ is total characters across all inserted words.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                      Trie Architecture                      |
+-------------------------------------------------------------+
|                         (root)                              |
|                           | 'a'                             |
|                          [a]                                |
|                           | 'p'                             |
|                          [p]                                |
|                           | 'p'                             |
|                          [p] (isEnd = false: prefix "app")  |
|                           | 'l'                             |
|                          [l]                                |
|                           | 'e'                             |
|                          [e] (isEnd = true: word "apple")   |
+-------------------------------------------------------------+
```

### Java Program
```java
class Trie {

    private static class TrieNode {
        TrieNode[] children = new TrieNode[26];
        boolean isEndOfWord = false;
    }

    private final TrieNode root;

    public Trie() {
        root = new TrieNode();
    }

    public void insert(String word) {
        TrieNode curr = root;
        for (char c : word.toCharArray()) {
            int idx = c - 'a';
            if (curr.children[idx] == null) {
                curr.children[idx] = new TrieNode();
            }
            curr = curr.children[idx];
        }
        curr.isEndOfWord = true;
    }

    public boolean search(String word) {
        TrieNode node = findPrefixNode(word);
        return node != null && node.isEndOfWord;
    }

    public boolean startsWith(String prefix) {
        return findPrefixNode(prefix) != null;
    }

    private TrieNode findPrefixNode(String prefix) {
        TrieNode curr = root;
        for (char c : prefix.toCharArray()) {
            int idx = c - 'a';
            if (curr.children[idx] == null) {
                return null;
            }
            curr = curr.children[idx];
        }
        return curr;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: Insert `"apple"`
  - `root -> 'a' -> 'p' -> 'p' -> 'l' -> 'e'` (marked `isEndOfWord = true`).
  - `startsWith("app")`: follows `'a' -> 'p' -> 'p'`. Exists $\rightarrow$ returns `true`.
  - `search("app")`: node exists but `isEndOfWord == false` $\rightarrow$ returns `false`.
- **Data Structures Used & Why**:
  - `TrieNode[26]`: Array indexing via `c - 'a'` provides $\mathcal{O}(1)$ branch operations.

---

## 37. Design Add and Search Words Data Structure (LeetCode #211)

### Problem Introduction & Example
Design a data structure that supports adding words and searching with a `.` wildcard that matches any letter.

- **Example**:
  - `addWord("bad")`
  - `search("pad")` $\rightarrow$ `false`
  - `search(".ad")` $\rightarrow$ `true` (The `.` matches `'b'`).

### High-Level Solution Intuition
Store words in a **Trie**.
When searching:
- If character is a normal letter: follow that child.
- If character is `'.'`: **backtrack across all 26 non-null children**! If any child branch succeeds, return `true`.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(L)$ for `addWord`; $\mathcal{O}(L)$ for exact searches, up to $\mathcal{O}(26^L)$ in worst case for wildcards.
- **Space Complexity**: $\mathcal{O}(N \times 26)$ for the Trie.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                   Wildcard Trie Backtracking                |
+-------------------------------------------------------------+
| Word: ".ad"                                                 |
| At root: char == '.'                                        |
|    Try child 'b': does "ad" match under 'b'? -> YES!        |
|    Early return true!                                       |
+-------------------------------------------------------------+
```

### Java Program
```java
class WordDictionary {

    private static class Node {
        Node[] children = new Node[26];
        boolean isEndOfWord = false;
    }

    private final Node root;

    public WordDictionary() {
        root = new Node();
    }

    public void addWord(String word) {
        Node curr = root;
        for (char c : word.toCharArray()) {
            int idx = c - 'a';
            if (curr.children[idx] == null) {
                curr.children[idx] = new Node();
            }
            curr = curr.children[idx];
        }
        curr.isEndOfWord = true;
    }

    public boolean search(String word) {
        return searchInNode(word, 0, root);
    }

    private boolean searchInNode(String word, int index, Node node) {
        if (node == null) return false;
        if (index == word.length()) return node.isEndOfWord;

        char c = word.charAt(index);

        if (c == '.') {
            // Wildcard: try all 26 branches
            for (Node child : node.children) {
                if (child != null && searchInNode(word, index + 1, child)) {
                    return true;
                }
            }
            return false;
        } else {
            return searchInNode(word, index + 1, node.children[c - 'a']);
        }
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: Dict has `"bad"`. Search `".ad"`.
  - `.` branches across children. Child `'b'` is non-null.
  - Follows `'a'` then `'d'`. Ends at terminal node $\rightarrow$ returns `true`.
- **Data Structures Used & Why**:
  - Trie + DFS: Prunes invalid word prefixes immediately.

---

## 38. Word Search II (LeetCode #212)

### Problem Introduction & Example
Given an `m x n` `board` of characters and a list of strings `words`, return all words on the board. Each word must be constructed from sequentially adjacent cells.

- **Example**:
  - Input: `board = [["o","a","a","n"],["e","t","a","e"],["i","h","k","r"],["i","f","l","v"]]`, `words = ["oath","pea","eat","rain"]`
  - Output: `["eat","oath"]`

### High-Level Solution Intuition
Searching for each word individually on the board is too slow.
Instead:
1. Build a **Trie** from all words.
2. Run DFS on the board and Trie **simultaneously**.
3. If the current board letter is not in the Trie node's children, **prune immediately**!
4. Store the complete word string at terminal Trie nodes to avoid building strings dynamically.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(M \times N \times 4 \times 3^{L-1})$ — Board dimensions $M \times N$, max word length $L$.
- **Space Complexity**: $\mathcal{O}(\sum \text{len}(words))$ — For the Trie.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                Trie + Grid Backtracking Flow                |
+-------------------------------------------------------------+
| 1. Build Trie from words ["oath", "eat"]                    |
| 2. Start DFS at cell (0, 0) = 'o'                           |
|    'o' exists in Trie root -> advance in Trie               |
|    Check 4 neighbors:                                       |
|      (0, 1) = 'a' -> exists in Trie                         |
|        (1, 1) = 't' -> exists in Trie                       |
|          (1, 2) = 'h' -> word="oath" found!                 |
| 3. De-duplicate and prune word from Trie                    |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.*;

class Solution {

    private static class TrieNode {
        TrieNode[] children = new TrieNode[26];
        String word = null; // Stores word at terminal node
    }

    public List<String> findWords(char[][] board, String[] words) {
        // Step 1: Build the Trie
        TrieNode root = new TrieNode();
        for (String w : words) {
            TrieNode curr = root;
            for (char c : w.toCharArray()) {
                int idx = c - 'a';
                if (curr.children[idx] == null) {
                    curr.children[idx] = new TrieNode();
                }
                curr = curr.children[idx];
            }
            curr.word = w;
        }

        List<String> result = new ArrayList<>();
        int rows = board.length;
        int cols = board[0].length;

        // Step 2: DFS from each cell
        for (int r = 0; r < rows; r++) {
            for (int c = 0; c < cols; c++) {
                dfs(board, r, c, root, result);
            }
        }

        return result;
    }

    private void dfs(char[][] board, int r, int c, TrieNode node, List<String> result) {
        if (r < 0 || r >= board.length || c < 0 || c >= board[0].length) return;

        char ch = board[r][c];
        if (ch == '#' || node.children[ch - 'a'] == null) {
            return;
        }

        node = node.children[ch - 'a'];

        if (node.word != null) {
            result.add(node.word);
            node.word = null; // Prevent duplicate additions
        }

        board[r][c] = '#'; // Mark visited

        dfs(board, r + 1, c, node, result);
        dfs(board, r - 1, c, node, result);
        dfs(board, r, c + 1, node, result);
        dfs(board, r, c - 1, node, result);

        board[r][c] = ch; // Backtrack
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: Board contains `'o' -> 'a' -> 't' -> 'h'`.
  - Cell matches Trie: walks node to node until terminal node holds `"oath"`.
  - Added to result. `node.word` set to null to avoid re-adding.
- **Data Structures Used & Why**:
  - Trie: Tests prefix validity for thousands of dictionary words at the same time in $\mathcal{O}(1)$ step transitions.


# Category 5: Heap, Backtracking & Graphs

---

## 39. Find Median from Data Stream (LeetCode #295)

### Problem Introduction & Example
The **median** is the middle value in an ordered integer list. If the size of the list is even, there is no single middle value, so the median is the average (mean) of the two middle values.
Design a data structure that supports dynamically adding numbers from a data stream and calculating the median at any moment.

- **Example**:
  - `addNum(1)`
  - `addNum(2)`
  - `findMedian()` $\rightarrow$ `1.5`
  - `addNum(3)`
  - `findMedian()` $\rightarrow$ `2.0`

### High-Level Solution Intuition
**Why sorting on every query fails**:
If we insert numbers into a list and sort it every time `findMedian()` is called, each call takes $\mathcal{O}(n \log n)$ time—far too slow for millions of streaming numbers.

**The "Aha!" Breakthrough (The Two-Heap Balance)**:
Imagine dividing all numbers into two equal teams:
1. **Left Team (Smaller half of numbers)**: Stored in a **Max-Heap** so the largest number of the small half sits right at the top (`leftMaxHeap.peek()`).
2. **Right Team (Larger half of numbers)**: Stored in a **Min-Heap** so the smallest number of the large half sits right at the top (`rightMinHeap.peek()`).

**The Balance Rules**:
- Every number in `leftMaxHeap` must be $\le$ every number in `rightMinHeap`.
- Either both heaps have the exact same size, or `leftMaxHeap` has exactly 1 more element than `rightMinHeap`.

Then finding the median takes $\mathcal{O}(1)$ instant time:
- If `leftMaxHeap` has more elements: the median is simply `leftMaxHeap.peek()`.
- If both heaps have equal sizes: the median is `(leftMaxHeap.peek() + rightMinHeap.peek()) / 2.0`.

### Complexity Analysis
- **Time Complexity**:
  - `addNum`: $\mathcal{O}(\log n)$ — Inserting into a heap and rebalancing.
  - `findMedian`: $\mathcal{O}(1)$ — Directly reading the roots of the heaps.
- **Space Complexity**: $\mathcal{O}(n)$ — To store the streaming numbers in the heaps.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                     Two-Heap Median Architecture            |
+-------------------------------------------------------------+
|    Smaller Half [Max-Heap]       Larger Half [Min-Heap]     |
|          [ 1, 2 ]                      [ 4, 5 ]             |
|              ^                             ^                |
|           max = 2                       min = 4             |
|                                                             |
|   Median = (2 + 4) / 2.0 = 3.0                              |
|                                                             |
|   If 3 arrives:                                             |
|   Adds to max-heap: [1, 2, 3]                               |
|   Median = max-heap.peek() = 3.0                            |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.Collections;
import java.util.PriorityQueue;

class MedianFinder {
    private PriorityQueue<Integer> leftMaxHeap;  // Stores the smaller half
    private PriorityQueue<Integer> rightMinHeap; // Stores the larger half

    public MedianFinder() {
        // Collections.reverseOrder() turns a Java PriorityQueue into a Max-Heap
        leftMaxHeap = new PriorityQueue<>(Collections.reverseOrder());
        rightMinHeap = new PriorityQueue<>();
    }

    public void addNum(int num) {
        // Step 1: Add new number to max-heap
        leftMaxHeap.offer(num);

        // Step 2: Ensure all elements in left are <= elements in right
        rightMinHeap.offer(leftMaxHeap.poll());

        // Step 3: Maintain size balance (left can hold at most 1 more than right)
        if (leftMaxHeap.size() < rightMinHeap.size()) {
            leftMaxHeap.offer(rightMinHeap.poll());
        }
    }

    public double findMedian() {
        if (leftMaxHeap.size() > rightMinHeap.size()) {
            return leftMaxHeap.peek();
        } else {
            return (leftMaxHeap.peek() + rightMinHeap.peek()) / 2.0;
        }
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: Stream: `1, 2, 3`
  - Add 1: `left=[1], right=[]`. Median: 1.0.
  - Add 2: `left=[1], right=[2]`. Median: $(1+2)/2.0 = 1.5$.
  - Add 3: `left=[2, 1], right=[3]`. Median: `left.peek() = 2.0`.
- **Data Structures Used & Why**:
  - `PriorityQueue` (Max & Min): Provides $\mathcal{O}(1)$ access to the boundary elements dividing the dataset, allowing instantaneous median calculations without sorting.

---

## 40. Combination Sum (LeetCode #39)

### Problem Introduction & Example
Given an array of distinct integers `candidates` and a target integer `target`, return a list of all unique combinations of `candidates` where the chosen numbers sum to `target`. You may return the combinations in any order.
The same number may be chosen from `candidates` an unlimited number of times.

- **Example**:
  - Input: `candidates = [2, 3, 6, 7]`, `target = 7`
  - Output: `[[2, 2, 3], [7]]`

### High-Level Solution Intuition
**Backtracking (Decision Tree)**:
At each candidate number:
- **Option 1**: Include the current number in our combination, reduce the remaining target, and stay on the current number (because we are allowed to reuse it).
- **Option 2**: Exclude the current number, and move to the next candidate.

If `remainingTarget == 0`, we found a valid combination!
If `remainingTarget < 0`, we exceeded the target, so we backtrack.
Sorting `candidates` beforehand lets us prune the search early when `candidate > remainingTarget`.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(2^T)$ — Where $T = \text{target} / \min(\text{candidates})$.
- **Space Complexity**: $\mathcal{O}(\text{target} / \min(\text{candidates}))$ — Maximum recursion depth.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                  Combination Sum Backtracking               |
+-------------------------------------------------------------+
|                        target = 7                           |
|                       /          \                          |
|             pick 2 (rem=5)       skip 2 (try 3)             |
|             /            \                                  |
|      pick 2 (rem=3)    skip 2                               |
|       /         \                                           |
| pick 2 (rem=1)  pick 3 (rem=0) -> [2, 2, 3] Valid!          |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.*;

class Solution {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> result = new ArrayList<>();
        Arrays.sort(candidates); // Sorting enables early pruning
        backtrack(candidates, target, 0, new ArrayList<>(), result);
        return result;
    }

    private void backtrack(int[] candidates, int remaining, int start, 
                          List<Integer> current, List<List<Integer>> result) {
        if (remaining == 0) {
            result.add(new ArrayList<>(current)); // Deep copy
            return;
        }

        for (int i = start; i < candidates.length; i++) {
            // Prune search: further candidates will also exceed remaining
            if (candidates[i] > remaining) {
                break;
            }

            current.add(candidates[i]);
            // Stay at index i to allow re-using the same candidate
            backtrack(candidates, remaining - candidates[i], i, current, result);
            current.remove(current.size() - 1); // Backtrack
        }
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `candidates = [2, 3, 6, 7]`, `target = 7`
  - Try 2 (rem 5) $\rightarrow$ try 2 (rem 3) $\rightarrow$ try 3 (rem 0) $\rightarrow$ adds `[2, 2, 3]`.
  - Skip to 7 (rem 0) $\rightarrow$ adds `[7]`.
  - Result: `[[2, 2, 3], [7]]`.
- **Data Structures Used & Why**:
  - `ArrayList<Integer>` with backtracking: Operates on a single working list, deep-copying only when a valid sum is found.

---

## 41. Word Search (LeetCode #79)

### Problem Introduction & Example
Given an `m x n` grid of characters `board` and a string `word`, return `true` if `word` exists in the grid.
The word can be constructed from letters of sequentially adjacent cells (horizontally or vertically neighboring). The same letter cell may not be used more than once in a word.

- **Example**:
  - Input: `board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]]`, `word = "ABCCED"`
  - Output: `true`

### High-Level Solution Intuition
1. Scan the board to find any cell matching the first character `word.charAt(0)`.
2. From each match, launch a **Depth-First Search (DFS)**:
   - Base cases: Out-of-bounds, cell already visited, or character doesn't match $\rightarrow$ return `false`.
   - If we matched all characters up to `word.length() - 1` $\rightarrow$ return `true`!
   - Mark the current cell visited by replacing its character with `'#'`.
   - Explore all 4 orthogonal neighbors (Up, Down, Left, Right).
   - **Backtrack**: Restore the original character so other exploration paths can use this cell!

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(M \times N \times 3^L)$ — Where $L$ is the length of `word`.
- **Space Complexity**: $\mathcal{O}(L)$ — Maximum recursion stack depth.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                  Word Search Backtracking                   |
+-------------------------------------------------------------+
| At cell (r, c):                                             |
| Does board[r][c] == word[index]?                            |
|    NO  -> return false                                      |
|    YES -> Save char, mark board[r][c] = '#'                 |
|           Explore UP, DOWN, LEFT, RIGHT                     |
|           Restore original char (Backtrack)                 |
|           Return true if any direction succeeded            |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public boolean exist(char[][] board, String word) {
        int rows = board.length;
        int cols = board[0].length;

        for (int r = 0; r < rows; r++) {
            for (int c = 0; c < cols; c++) {
                if (board[r][c] == word.charAt(0) && dfs(board, word, r, c, 0)) {
                    return true;
                }
            }
        }

        return false;
    }

    private boolean dfs(char[][] board, String word, int r, int c, int index) {
        if (index == word.length()) {
            return true;
        }

        // Boundary and match checks
        if (r < 0 || r >= board.length || c < 0 || c >= board[0].length 
            || board[r][c] != word.charAt(index)) {
            return false;
        }

        // Mark cell visited
        char temp = board[r][c];
        board[r][c] = '#';

        // Explore 4 directions
        boolean found = dfs(board, word, r + 1, c, index + 1) ||
                        dfs(board, word, r - 1, c, index + 1) ||
                        dfs(board, word, r, c + 1, index + 1) ||
                        dfs(board, word, r, c - 1, index + 1);

        // Backtrack: restore character
        board[r][c] = temp;

        return found;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `word = "AB"`, grid `[['A', 'B']]`
  - Cell `(0, 0) = 'A'` matches. Marked `'#'`.
  - Recurse right to `(0, 1) = 'B'`: matches. Word complete! Return `true`.
- **Data Structures Used & Why**:
  - In-place marker (`board[r][c] = '#'`): Avoids allocating a `boolean[][] visited` matrix.

---

## 42. Number of Islands (LeetCode #200)

### Problem Introduction & Example
Given an `m x n` 2D binary grid `grid` representing a map of `'1'`s (land) and `'0'`s (water), return the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically.

- **Example**:
  - Input:
    ```
    [
      ["1","1","0","0","0"],
      ["1","1","0","0","0"],
      ["0","0","1","0","0"],
      ["0","0","0","1","1"]
    ]
    ```
  - Output: `3`

### High-Level Solution Intuition
**The "Flood Fill / Sink the Island" Technique**:
Iterate through every cell of the grid:
- Whenever you stumble onto an unvisited land cell (`'1'`), you have discovered a **brand new island**!
- Increment `islandCount++`.
- Launch a DFS from that cell that "sinks" the entire connected island by flipping every reachable `'1'` into a `'0'`.
By submerging the island, we ensure that none of its cells will ever be counted again!

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(M \times N)$ — Every cell is visited a constant number of times.
- **Space Complexity**: $\mathcal{O}(M \times N)$ — Maximum recursion stack in the worst case (grid full of land).

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                     Island Sinking DFS                      |
+-------------------------------------------------------------+
| Encounter '1' -> islandCount++                              |
| Sinking DFS:                                                |
|    grid[r][c] = '0'                                         |
|    dfs(r+1, c)   dfs(r-1, c)   dfs(r, c+1)   dfs(r, c-1)    |
| All connected land is sunk so it won't be recounted!        |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public int numIslands(char[][] grid) {
        if (grid == null || grid.length == 0) return 0;

        int islands = 0;
        int rows = grid.length;
        int cols = grid[0].length;

        for (int r = 0; r < rows; r++) {
            for (int c = 0; c < cols; c++) {
                if (grid[r][c] == '1') {
                    islands++;
                    sinkIsland(grid, r, c);
                }
            }
        }

        return islands;
    }

    private void sinkIsland(char[][] grid, int r, int c) {
        // Boundary check and water check
        if (r < 0 || r >= grid.length || c < 0 || c >= grid[0].length || grid[r][c] == '0') {
            return;
        }

        // Sink current cell
        grid[r][c] = '0';

        // Sink all connected neighbors
        sinkIsland(grid, r + 1, c);
        sinkIsland(grid, r - 1, c);
        sinkIsland(grid, r, c + 1);
        sinkIsland(grid, r, c - 1);
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `[["1","1"],["1","0"]]`
  - Find `(0, 0) = '1'`: `islands = 1`.
  - `sinkIsland(0, 0)` turns `(0, 0)`, `(0, 1)`, and `(1, 0)` into `'0'`.
  - Grid becomes all `'0'`s. Total islands: 1.
- **Data Structures Used & Why**:
  - In-place mutation: Overwriting `'1'` with `'0'` saves memory by eliminating a visited matrix.

---

## 43. Clone Graph (LeetCode #133)

### Problem Introduction & Example
Given a reference of a node in a connected undirected graph, return a **deep copy (clone)** of the graph. Each node contains a value (`val`) and a list of its neighbors.

- **Example**:
  - Input: `adjList = [[2,4],[1,3],[2,4],[1,3]]`
  - Output: Deep copy with completely new node objects preserving identical connections.

### High-Level Solution Intuition
Graphs can contain cycles (e.g. node 1 connects to node 2, which connects back to node 1). If you traverse without remembering where you've been, you'll enter an infinite loop!

We use a **Hash Map (`Map<Node, Node>`)** where:
- Key: The original node in the old graph.
- Value: The newly cloned copy of that node.

When visiting a node `curr`:
- If `curr` is already in our map, return its cloned copy immediately.
- Otherwise, create `new Node(curr.val)` and put it in the map.
- Recursively clone all of `curr`'s neighbors and add them to the clone's neighbor list.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(V + E)$ — Where $V$ is number of vertices and $E$ is number of edges.
- **Space Complexity**: $\mathcal{O}(V)$ — To store the hash map and recursion stack.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                     Graph Clone with Map                    |
+-------------------------------------------------------------+
| Map: Original Node -> Cloned Node                           |
|                                                             |
| clone(Node 1):                                              |
|    clone1 = new Node(1); map.put(1, clone1)                 |
|    for neighbor 2 of 1:                                     |
|       clone1.neighbors.add(clone(2))                         |
|          clone(Node 2):                                     |
|             clone2 = new Node(2); map.put(2, clone2)         |
|             for neighbor 1 of 2:                            |
|                1 is already in map! -> return clone1        |
|                clone2.neighbors.add(clone1)                 |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    private Map<Node, Node> visited = new HashMap<>();

    public Node cloneGraph(Node node) {
        if (node == null) return null;

        // If already cloned, return the cloned instance
        if (visited.containsKey(node)) {
            return visited.get(node);
        }

        // Clone current node
        Node clone = new Node(node.val);
        visited.put(node, clone);

        // Recursively clone all neighbors
        for (Node neighbor : node.neighbors) {
            clone.neighbors.add(cloneGraph(neighbor));
        }

        return clone;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: Cycle `1 <-> 2`
  - Clone 1 created and placed in map.
  - Recurse on neighbor 2: clone 2 created and placed in map.
  - Recurse on neighbor 1 of node 2: node 1 is already in map $\rightarrow$ returns clone 1!
  - Recursion unwinds cleanly.
- **Data Structures Used & Why**:
  - `HashMap<Node, Node>`: Acts as both a cycle prevention mechanism and an object lookup table.

---

## 44. Pacific Atlantic Water Flow (LeetCode #417)

### Problem Introduction & Example
There is an `m x n` island bordering the **Pacific Ocean** (top and left edges) and the **Atlantic Ocean** (bottom and right edges). Water can flow to neighboring cells with equal or lower heights.
Return a list of grid coordinates where water can flow to **both** the Pacific and Atlantic oceans.

- **Example**:
  - Input: Matrix of cell heights.
  - Output: List of `[row, col]` pairs where water can reach both oceans.

### High-Level Solution Intuition
**The "Aha!" Breakthrough (Reverse the Flow - Go Uphill!)**:
Instead of testing whether water can flow downhill from every single cell to both oceans:
Start at the oceans and see how far water can flow **UPHILL**!
1. Start DFS from all cells touching the **Pacific Ocean**, marking all uphill reachable cells in `canReachPacific[][]`.
2. Start DFS from all cells touching the **Atlantic Ocean**, marking all uphill reachable cells in `canReachAtlantic[][]`.
3. Any cell where both `canReachPacific[r][c]` and `canReachAtlantic[r][c]` are `true` can reach both oceans!

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(M \times N)$ — Each cell is visited at most twice per ocean.
- **Space Complexity**: $\mathcal{O}(M \times N)$ — For the two reachability matrices.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                 Reverse Uphill Water Flow                   |
+-------------------------------------------------------------+
| Pacific (Top/Left) ------>  [DFS Uphill]                    |
|                             canReachPacific[][]             |
|                                     ^                       |
|                                     | Intersection (BOTH)   |
|                                     v                       |
| Atlantic (Bottom/Right) --> [DFS Uphill]                    |
|                             canReachAtlantic[][]            |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.*;

class Solution {
    public List<List<Integer>> pacificAtlantic(int[][] heights) {
        List<List<Integer>> result = new ArrayList<>();
        if (heights == null || heights.length == 0) return result;

        int rows = heights.length;
        int cols = heights[0].length;

        boolean[][] pacific = new boolean[rows][cols];
        boolean[][] atlantic = new boolean[rows][cols];

        // Start from vertical ocean borders (columns)
        for (int r = 0; r < rows; r++) {
            dfs(heights, r, 0, pacific, heights[r][0]);              // Left: Pacific
            dfs(heights, r, cols - 1, atlantic, heights[r][cols - 1]); // Right: Atlantic
        }

        // Start from horizontal ocean borders (rows)
        for (int c = 0; c < cols; c++) {
            dfs(heights, 0, c, pacific, heights[0][c]);              // Top: Pacific
            dfs(heights, rows - 1, c, atlantic, heights[rows - 1][c]); // Bottom: Atlantic
        }

        // Collect cells that can reach both oceans
        for (int r = 0; r < rows; r++) {
            for (int c = 0; c < cols; c++) {
                if (pacific[r][c] && atlantic[r][c]) {
                    result.add(Arrays.asList(r, c));
                }
            }
        }

        return result;
    }

    private void dfs(int[][] heights, int r, int c, boolean[][] reachable, int prevHeight) {
        if (r < 0 || r >= heights.length || c < 0 || c >= heights[0].length 
            || reachable[r][c] || heights[r][c] < prevHeight) {
            return;
        }

        reachable[r][c] = true;

        dfs(heights, r + 1, c, reachable, heights[r][c]);
        dfs(heights, r - 1, c, reachable, heights[r][c]);
        dfs(heights, r, c + 1, reachable, heights[r][c]);
        dfs(heights, r, c - 1, reachable, heights[r][c]);
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: Cell `(0, 4)` is on Pacific top edge and Atlantic right edge.
  - Reached by Pacific from top row; reached by Atlantic from right column.
  - Both boolean flags true $\rightarrow$ added to result.
- **Data Structures Used & Why**:
  - Two `boolean[][]` matrices: Decouples the independent ocean reachabilities cleanly.

---

## 45. Course Schedule (LeetCode #207)

### Problem Introduction & Example
There are `numCourses` courses to take, labeled `0` to `numCourses - 1`. You are given an array `prerequisites` where `prerequisites[i] = [a, b]` means you must take course `b` before course `a`.
Return `true` if you can finish all courses, or `false` if there is an impossible circular prerequisite.

- **Example 1**: `numCourses = 2, prereqs = [[1, 0]]` $\rightarrow$ `true` (Take 0, then 1).
- **Example 2**: `numCourses = 2, prereqs = [[1, 0], [0, 1]]` $\rightarrow$ `false` (Circular dependency!).

### High-Level Solution Intuition
**Cycle Detection via Kahn's Algorithm (Topological Sort)**:
Think of courses like college requirements:
1. Count the **in-degree** of each course (how many prerequisite courses it requires).
2. Any course with `in-degree == 0` has **no prerequisites**! You can take it immediately. Add all such courses to a `Queue`.
3. While the queue is not empty:
   - "Take" a course by polling it from the queue and incrementing `takenCount`.
   - For every course that depended on this course, reduce its remaining prerequisite count by 1.
   - If any dependent course's prerequisites drop to 0, add it to the queue!
4. If `takenCount == numCourses`, you successfully finished all courses! If not, a circular dependency locked some courses.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(V + E)$ — Where $V$ is number of courses and $E$ is number of prerequisite edges.
- **Space Complexity**: $\mathcal{O}(V + E)$ — For the adjacency list and in-degree array.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                  Kahn's Topological Sort                    |
+-------------------------------------------------------------+
| 0 -> 1 (Course 0 unlocks Course 1)                          |
| In-degrees: [0: 0, 1: 1]                                    |
|                                                             |
| Queue: [0]                                                  |
| Poll 0: count = 1. Decrement in-degree of 1 -> becomes 0!   |
| Queue: [1]                                                  |
| Poll 1: count = 2.                                          |
|                                                             |
| count == numCourses (2 == 2) -> Return true!                |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.*;

class Solution {
    public boolean canFinish(int numCourses, int[][] prerequisites) {
        List<List<Integer>> adj = new ArrayList<>();
        for (int i = 0; i < numCourses; i++) {
            adj.add(new ArrayList<>());
        }

        int[] inDegree = new int[numCourses];

        // Build directed graph: prereq -> course
        for (int[] edge : prerequisites) {
            int course = edge[0];
            int prereq = edge[1];
            adj.get(prereq).add(course);
            inDegree[course]++;
        }

        // Add all courses with 0 prerequisites to the queue
        Queue<Integer> queue = new LinkedList<>();
        for (int i = 0; i < numCourses; i++) {
            if (inDegree[i] == 0) {
                queue.offer(i);
            }
        }

        int completedCourses = 0;

        while (!queue.isEmpty()) {
            int curr = queue.poll();
            completedCourses++;

            // Unlock dependent courses
            for (int nextCourse : adj.get(curr)) {
                inDegree[nextCourse]--;
                if (inDegree[nextCourse] == 0) {
                    queue.offer(nextCourse);
                }
            }
        }

        return completedCourses == numCourses;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `[[1, 0], [0, 1]]`
  - In-degree: course 0 requires 1, course 1 requires 1. Both have in-degree 1.
  - Queue is empty from the start!
  - `completedCourses = 0 != 2` $\rightarrow$ returns `false`.
- **Data Structures Used & Why**:
  - `int[] inDegree` & `Queue<Integer>`: Tracks readiness dynamically, processing ready nodes in topological order.

---

## 46. Number of Connected Components in an Undirected Graph (LeetCode #323)

### Problem Introduction & Example
You have a graph of `n` nodes. You are given an integer `n` and an array `edges` where `edges[i] = [ai, bi]` connects nodes `ai` and `bi`. Return the number of **connected components** in the graph.

- **Example**:
  - Input: `n = 5, edges = [[0, 1], [1, 2], [3, 4]]`
  - Output: `2` (Group 1: `{0, 1, 2}`, Group 2: `{3, 4}`).

### High-Level Solution Intuition
**Disjoint Set Union (Union-Find)**:
1. Initially, every node is in its own separate component: `count = n`.
2. For each edge `(u, v)`:
   - Find the root representative of `u` and `v`.
   - If they have different roots, merge (union) them! Every successful union merges two components into one, so decrement `count--`.
3. The remaining `count` is the answer.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(V + E \cdot \alpha(V))$ — Where $\alpha$ is the Inverse Ackermann function (effectively $\mathcal{O}(1)$).
- **Space Complexity**: $\mathcal{O}(V)$ — For the parent array.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                      Union-Find Flow                        |
+-------------------------------------------------------------+
| Initial: {0}, {1}, {2}, {3}, {4}  -> count = 5              |
| Edge (0, 1): union(0, 1)          -> count = 4              |
| Edge (1, 2): union(0, 2)          -> count = 3              |
| Edge (3, 4): union(3, 4)          -> count = 2              |
| Final Component Count = 2                                   |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    private static class UnionFind {
        int[] parent;
        int count;

        UnionFind(int n) {
            count = n;
            parent = new int[n];
            for (int i = 0; i < n; i++) parent[i] = i;
        }

        int find(int x) {
            if (parent[x] != x) {
                parent[x] = find(parent[x]); // Path compression
            }
            return parent[x];
        }

        void union(int a, int b) {
            int rootA = find(a);
            int rootB = find(b);
            if (rootA != rootB) {
                parent[rootA] = rootB;
                count--;
            }
        }
    }

    public int countComponents(int n, int[][] edges) {
        UnionFind uf = new UnionFind(n);
        for (int[] edge : edges) {
            uf.union(edge[0], edge[1]);
        }
        return uf.count;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `n=3, edges=[[0,1]]`
  - Start with 3 components.
  - Edge `(0, 1)` unions roots 0 and 1 $\rightarrow$ `count` becomes 2.
  - Return 2.
- **Data Structures Used & Why**:
  - `UnionFind` with path compression: Far faster and simpler than building an adjacency list and running multiple DFS traversals.

---

## 47. Graph Valid Tree (LeetCode #261)

### Problem Introduction & Example
Given `n` nodes labeled `0` to `n - 1` and a list of undirected edges, determine whether these edges form a **valid tree**.

- **Example 1**: `n = 5, edges = [[0,1],[0,2],[0,3],[1,4]]` $\rightarrow$ `true`
- **Example 2**: `n = 5, edges = [[0,1],[1,2],[2,3],[1,3],[1,4]]` $\rightarrow$ `false` (Contains a cycle!).

### High-Level Solution Intuition
In graph theory, a graph of $n$ nodes is a valid tree if and only if it satisfies two rules:
1. **Rule 1**: It must have exactly **$n - 1$ edges**. (If it has fewer edges, it cannot be fully connected; if it has more, it must contain a cycle).
2. **Rule 2**: It must contain **no cycles** (which also implies it is fully connected when Rule 1 holds).

Using Union-Find:
- If `edges.length != n - 1`, return `false` immediately.
- For each edge, check if `find(u) == find(v)`. If they already share the same root, adding this edge creates a cycle $\rightarrow$ return `false`.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n \cdot \alpha(n))$ — Nearly linear.
- **Space Complexity**: $\mathcal{O}(n)$ — For the parent array.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                     Tree Validity Check                     |
+-------------------------------------------------------------+
| Check 1: Does edges.length == n - 1?                        |
|    NO -> Cannot be a tree! Return false                     |
|                                                             |
| Check 2: For each edge (u, v):                              |
|    If find(u) == find(v): Cycle detected! Return false      |
|    Else: union(u, v)                                        |
|                                                             |
| Return true                                                 |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public boolean validTree(int n, int[][] edges) {
        // Condition 1: A tree with n nodes MUST have exactly n - 1 edges
        if (edges.length != n - 1) {
            return false;
        }

        int[] parent = new int[n];
        for (int i = 0; i < n; i++) parent[i] = i;

        // Condition 2: No cycles
        for (int[] edge : edges) {
            int root1 = find(parent, edge[0]);
            int root2 = find(parent, edge[1]);

            if (root1 == root2) {
                return false; // Cycle detected
            }

            parent[root1] = root2;
        }

        return true;
    }

    private int find(int[] parent, int i) {
        if (parent[i] != i) {
            parent[i] = find(parent, parent[i]); // Path compression
        }
        return parent[i];
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `n=4, edges=[[0,1],[1,2],[2,0]]`
  - $3 == 4 - 1$ (passes edge count).
  - Union (0,1): merged. Union (1,2): merged.
  - Union (2,0): roots match $\rightarrow$ Cycle detected! Return `false`.
- **Data Structures Used & Why**:
  - Union-Find: Validating edge count and checking cycle connectivity simultaneously detects disconnected trees and cyclic graphs in constant memory.

---

## 48. Alien Dictionary (LeetCode #269)

### Problem Introduction & Example
There is a new alien language that uses the English alphabet. However, the alphabetical order among letters is unknown.
You are given a list of strings `words` sorted lexicographically by the rules of this alien language. Return a string of the unique letters in the new alien language sorted in increasing order. If the order is invalid, return `""`.

- **Example**:
  - Input: `words = ["wrt","wrf","er","ett","rftt"]`
  - Output: `"wertf"`

### High-Level Solution Intuition
**Topological Sort on Lexicographical Pairs**:
Comparing adjacent words reveals the alphabetical ranking of letters:
- Compare `words[i]` and `words[i+1]`: find the first character where they differ, say `c1` and `c2`. This tells us that `c1` comes before `c2` in the alien alphabet! This creates a directed edge: `c1 -> c2`.
- Edge case: If `w1` is longer than `w2` and starts with `w2` (e.g. `["apple", "app"]`), the list is invalid $\rightarrow$ return `""`.
- Once all edges are constructed, run Kahn's Topological Sort.
- If the output contains all unique letters, return it. If a cycle is present, return `""`.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(C)$ — Where $C$ is total characters across all words.
- **Space Complexity**: $\mathcal{O}(1)$ — At most 26 lowercase English letters.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                  Alien Dictionary Pipeline                  |
+-------------------------------------------------------------+
| "wrt" vs "wrf"  -> 't' comes before 'f'  (t -> f)           |
| "wrf" vs "er"   -> 'w' comes before 'e'  (w -> e)           |
| "er"  vs "ett"  -> 'r' comes before 't'  (r -> t)           |
| "ett" vs "rftt" -> 'e' comes before 'r'  (e -> r)           |
|                                                             |
| Topo Sort: w -> e -> r -> t -> f                            |
| Result: "wertf"                                             |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.*;

class Solution {
    public String alienOrder(String[] words) {
        Map<Character, Set<Character>> adj = new HashMap<>();
        Map<Character, Integer> inDegree = new HashMap<>();

        // Initialize all unique characters
        for (String word : words) {
            for (char c : word.toCharArray()) {
                inDegree.putIfAbsent(c, 0);
                adj.putIfAbsent(c, new HashSet<>());
            }
        }

        // Build directed graph by comparing adjacent words
        for (int i = 0; i < words.length - 1; i++) {
            String w1 = words[i];
            String w2 = words[i + 1];

            // Invalid prefix rule: e.g. "apple" cannot come before "app"
            if (w1.length() > w2.length() && w1.startsWith(w2)) {
                return "";
            }

            for (int j = 0; j < Math.min(w1.length(), w2.length()); j++) {
                char parent = w1.charAt(j);
                char child = w2.charAt(j);

                if (parent != child) {
                    if (!adj.get(parent).contains(child)) {
                        adj.get(parent).add(child);
                        inDegree.put(child, inDegree.get(child) + 1);
                    }
                    break; // Only the first differing character matters
                }
            }
        }

        // Topological Sort (Kahn's BFS)
        Queue<Character> queue = new LinkedList<>();
        for (char c : inDegree.keySet()) {
            if (inDegree.get(c) == 0) {
                queue.offer(c);
            }
        }

        StringBuilder order = new StringBuilder();
        while (!queue.isEmpty()) {
            char curr = queue.poll();
            order.append(curr);

            for (char neighbor : adj.get(curr)) {
                inDegree.put(neighbor, inDegree.get(neighbor) - 1);
                if (inDegree.get(neighbor) == 0) {
                    queue.offer(neighbor);
                }
            }
        }

        // If cycle exists, topological sort cannot visit all characters
        if (order.length() < inDegree.size()) {
            return "";
        }

        return order.toString();
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `words = ["z", "x", "z"]`
  - Edge `z -> x`, then edge `x -> z`. Cycle detected! Both have in-degree 1. Queue is empty. Returns `""`.
- **Data Structures Used & Why**:
  - `Map<Character, Set<Character>>`: Tracks alien letter relationships cleanly without assuming continuous ASCII indexing.


# Category 6: Intervals & Matrix

---

## 49. Insert Interval (LeetCode #57)

### Problem Introduction & Example
You are given an array of non-overlapping intervals `intervals` where `intervals[i] = [starti, endi]` is sorted in ascending order by `starti`.
You are also given a `newInterval = [start, end]`.
Insert `newInterval` into `intervals` such that the list is still sorted and contains no overlapping intervals (merge any intervals that overlap with the new one).

- **Example**:
  - Input: `intervals = [[1, 3], [6, 9]]`, `newInterval = [2, 5]`
  - Output: `[[1, 5], [6, 9]]`
  - Explanation: Because `[2, 5]` overlaps with `[1, 3]`, they merge together into `[1, 5]`.

### High-Level Solution Intuition
Think of inserting `newInterval` across three natural phases along a timeline:
1. **Phase 1 (Before)**: Add all existing intervals that end *before* `newInterval` even starts (`interval.end < newInterval.start`). They don't touch `newInterval` at all.
2. **Phase 2 (Overlap & Merge)**: For any interval that overlaps with `newInterval` (`interval.start <= newInterval.end`), absorb it into `newInterval`:
   - `newInterval.start = min(newInterval.start, interval.start)`
   - `newInterval.end = max(newInterval.end, interval.end)`
   Once all overlapping intervals are merged, add this big combined `newInterval`.
3. **Phase 3 (After)**: Add all remaining intervals that start *after* `newInterval` ends.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — We iterate through the list of intervals exactly once.
- **Space Complexity**: $\mathcal{O}(n)$ — For the output list of intervals.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                   3-Phase Interval Insertion                |
+-------------------------------------------------------------+
| Existing: [1, 3]           [6, 9]                           |
| New:              [2, 5]                                    |
|                                                             |
| Phase 1: None strictly left of [2, 5]                       |
| Phase 2: [1, 3] overlaps [2, 5] -> merged: [1, 5]           |
| Phase 3: [6, 9] strictly right of [1, 5] -> append [6, 9]   |
| Result:  [[1, 5], [6, 9]]                                   |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public int[][] insert(int[][] intervals, int[] newInterval) {
        List<int[]> result = new ArrayList<>();
        int i = 0;
        int n = intervals.length;

        // Phase 1: Add all intervals ending before newInterval starts
        while (i < n && intervals[i][1] < newInterval[0]) {
            result.add(intervals[i]);
            i++;
        }

        // Phase 2: Merge overlapping intervals with newInterval
        while (i < n && intervals[i][0] <= newInterval[1]) {
            newInterval[0] = Math.min(newInterval[0], intervals[i][0]);
            newInterval[1] = Math.max(newInterval[1], intervals[i][1]);
            i++;
        }
        result.add(newInterval);

        // Phase 3: Add all remaining intervals that start after newInterval ends
        while (i < n) {
            result.add(intervals[i]);
            i++;
        }

        return result.toArray(new int[result.size()][]);
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `intervals = [[1, 2], [3, 5], [6, 7], [8, 10], [12, 16]]`, `newInterval = [4, 8]`
  - Phase 1: `[1, 2]` ends at 2 $< 4 \rightarrow$ added.
  - Phase 2: `[3, 5]`, `[6, 7]`, `[8, 10]` overlap with `[4, 8]` $\rightarrow$ merged to `[min(3, 4), max(10, 8)] = [3, 10]`. Add `[3, 10]`.
  - Phase 3: `[12, 16]` added.
  - Result: `[[1, 2], [3, 10], [12, 16]]`.
- **Data Structures Used & Why**:
  - `ArrayList<int[]>`: Dynamically accumulates intervals because the final count after merges is not known in advance.

---

## 50. Merge Intervals (LeetCode #56)

### Problem Introduction & Example
Given an array of `intervals` where `intervals[i] = [starti, endi]`, merge all overlapping intervals and return an array of non-overlapping intervals that cover the entire time span.

- **Example**:
  - Input: `intervals = [[1, 3], [2, 6], [8, 10], [15, 18]]`
  - Output: `[[1, 6], [8, 10], [15, 18]]`
  - Explanation: Since `[1, 3]` and `[2, 6]` overlap, they merge into `[1, 6]`.

### High-Level Solution Intuition
1. **Sort by start time**: Sorting takes $\mathcal{O}(n \log n)$ and guarantees that intervals appear in chronological order.
2. Maintain `currentInterval`:
   - If the next interval starts *before or at* the end of `currentInterval` (`next.start <= current.end`), they **overlap**! Merge them by stretching `current.end = max(current.end, next.end)`.
   - If it starts *after* `current.end`, there is a gap! Add `current` to the output and make `next` the new `currentInterval`.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n \log n)$ — Dominated by sorting the intervals.
- **Space Complexity**: $\mathcal{O}(n)$ — For storing sorted and merged output.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                    Merge Intervals Flow                     |
+-------------------------------------------------------------+
| Sorted: [1, 3]  [2, 6]  [8, 10]  [15, 18]                   |
|                                                             |
| 1. Curr = [1, 3]                                            |
| 2. Next = [2, 6] -> 2 <= 3 (Overlap!)                       |
|    Merged end = max(3, 6) = 6 -> [1, 6]                     |
| 3. Next = [8, 10] -> 8 > 6 (Disjoint!)                      |
|    Add [1, 6], Curr becomes [8, 10]                         |
| 4. Next = [15, 18] -> Add [8, 10], Curr becomes [15, 18]    |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.*;

class Solution {
    public int[][] merge(int[][] intervals) {
        if (intervals.length <= 1) return intervals;

        // Step 1: Sort intervals by start time ascending
        Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));

        List<int[]> merged = new ArrayList<>();
        int[] currentInterval = intervals[0];
        merged.add(currentInterval);

        for (int[] interval : intervals) {
            int currentEnd = currentInterval[1];
            int nextStart = interval[0];
            int nextEnd = interval[1];

            // Overlap detected: extend end boundary
            if (nextStart <= currentEnd) {
                currentInterval[1] = Math.max(currentEnd, nextEnd);
            } else {
                // No overlap: add new interval to merged list
                currentInterval = interval;
                merged.add(currentInterval);
            }
        }

        return merged.toArray(new int[merged.size()][]);
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `[[1, 4], [4, 5]]`
  - $i=0$: `current = [1, 4]`.
  - $i=1$: `nextStart = 4 <= currentEnd = 4`.
  - Overlap! Update `currentEnd = max(4, 5) = 5`. Result: `[[1, 5]]`.
- **Data Structures Used & Why**:
  - In-place mutation of `currentInterval` inside `List<int[]>`: Updates the latest interval without redundant deletions.

---

## 51. Non-overlapping Intervals (LeetCode #435)

### Problem Introduction & Example
Given an array of intervals `intervals`, return the **minimum number of intervals** you need to remove to make the remaining intervals non-overlapping.

- **Example**:
  - Input: `intervals = [[1, 2], [2, 3], [3, 4], [1, 3]]`
  - Output: `1` (Remove `[1, 3]` and the remaining three are non-overlapping).

### High-Level Solution Intuition
**The "Aha!" Breakthrough (Greedy Interval Scheduling)**:
Minimizing removals is mathematically identical to **maximizing the number of compatible intervals you can keep**.
How do you fit as many events into your calendar as possible?
Always pick the event that **finishes earliest**! An event that ends early leaves the maximum possible room open for future events.

1. Sort intervals by their **end times**: `interval[1]`.
2. Keep track of `lastEnd`.
3. For each interval:
   - If it starts before `lastEnd` (`interval[0] < lastEnd`), it overlaps with our schedule $\rightarrow$ remove it (`removals++`).
   - If it starts at or after `lastEnd`, it fits cleanly! Accept it and update `lastEnd = interval[1]`.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n \log n)$ — Sorting $n$ intervals by end time.
- **Space Complexity**: $\mathcal{O}(1)$ or $\mathcal{O}(\log n)$ — In-place sort memory.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|              Greedy Earliest End-Time Schedule              |
+-------------------------------------------------------------+
| Sort by END time: [1, 2], [2, 3], [1, 3], [3, 4]            |
|                                                             |
| Keep [1, 2] -> lastEnd = 2                                  |
| Keep [2, 3] -> 2 >= 2 -> valid! lastEnd = 3                 |
| Check [1, 3]-> 1 < 3  -> OVERLAP! Remove (count = 1)        |
| Keep [3, 4] -> 3 >= 3 -> valid! lastEnd = 4                 |
| Total removed = 1                                           |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.Arrays;

class Solution {
    public int eraseOverlapIntervals(int[][] intervals) {
        if (intervals.length == 0) return 0;

        // Sort intervals by end time ascending
        Arrays.sort(intervals, (a, b) -> Integer.compare(a[1], b[1]));

        int removals = 0;
        int lastEnd = intervals[0][1];

        for (int i = 1; i < intervals.length; i++) {
            // Overlap detected: current interval starts before previous ends
            if (intervals[i][0] < lastEnd) {
                removals++;
            } else {
                // Valid: advance lastEnd
                lastEnd = intervals[i][1];
            }
        }

        return removals;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `[[1, 2], [1, 2], [1, 2]]`
  - All end at 2. Keep the first `[1, 2]`.
  - Next two both start at $1 < 2 \rightarrow$ both removed.
  - Result: 2.
- **Data Structures Used & Why**:
  - Greedy scalar `lastEnd`: Eliminates complex interval trees or $\mathcal{O}(n^2)$ DP tables.

---

## 52. Meeting Rooms (LeetCode #252)

### Problem Introduction & Example
Given an array of meeting time intervals where `intervals[i] = [starti, endi]`, determine if a person could attend all meetings without any time conflicts.

- **Example 1**: `intervals = [[0, 30], [5, 10], [15, 20]]` $\rightarrow$ `false` (Conflict between 0-30 and 5-10).
- **Example 2**: `intervals = [[7, 10], [2, 4]]` $\rightarrow$ `true` (No overlap).

### High-Level Solution Intuition
A person can attend all meetings if no two meetings overlap:
1. Sort meetings chronologically by start time.
2. Check adjacent pairs: if meeting $i$ ends after meeting $i+1$ starts (`intervals[i][1] > intervals[i+1][0]`), a scheduling conflict exists $\rightarrow$ return `false`.
3. If no consecutive meetings overlap, return `true`.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n \log n)$ — Sorting $n$ meetings.
- **Space Complexity**: $\mathcal{O}(1)$ — In-place array comparison.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                     Meeting Rooms Check                     |
+-------------------------------------------------------------+
| Sorted: [2, 4], [7, 10]                                     |
| Check pair: 4 <= 7 -> Valid! Person can attend both.        |
|                                                             |
| Sorted: [0, 30], [5, 10]                                    |
| Check pair: 30 > 5 -> Conflict! Return false.               |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.Arrays;

class Solution {
    public boolean canAttendMeetings(int[][] intervals) {
        if (intervals == null || intervals.length <= 1) return true;

        // Sort by start time
        Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));

        for (int i = 0; i < intervals.length - 1; i++) {
            // Conflict if current meeting ends after next meeting starts
            if (intervals[i][1] > intervals[i + 1][0]) {
                return false;
            }
        }

        return true;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `[[0, 30], [5, 10]]`
  - $30 > 5 \rightarrow$ conflict detected $\rightarrow$ returns `false`.
- **Data Structures Used & Why**:
  - In-place sorting: Checks adjacent intervals without requiring pairwise comparisons.

---

## 53. Meeting Rooms II (LeetCode #253)

### Problem Introduction & Example
Given an array of meeting time intervals `intervals` where `intervals[i] = [starti, endi]`, return the **minimum number of conference rooms** required.

- **Example**:
  - Input: `intervals = [[0, 30], [5, 10], [15, 20]]`
  - Output: `2`
  - Explanation: Room 1 hosts `[0, 30]`. Room 2 hosts `[5, 10]` and then reuses the same room for `[15, 20]`.

### High-Level Solution Intuition
**Min-Heap for Room Allocation**:
Sort meetings by start time.
Use a **Min-Heap** to store the end times of meetings that are currently in progress:
- The root of the Min-Heap represents the meeting that finishes **earliest**.
- When a new meeting arrives at time $T$:
  - If $T \ge$ earliest finish time, that room is now **empty**! We reuse it (poll the old end time).
  - Otherwise, all active rooms are currently occupied, so a **new room** must be opened!
- Add the current meeting's end time into the heap.
The size of the heap at the end is the maximum number of concurrent rooms needed.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n \log n)$ — Sorting takes $\mathcal{O}(n \log n)$. Each of the $n$ heap operations takes $\mathcal{O}(\log n)$.
- **Space Complexity**: $\mathcal{O}(n)$ — To store end times in the Min-Heap.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                    Min-Heap Room Allocation                 |
+-------------------------------------------------------------+
| Meetings: [0, 30], [5, 10], [15, 20]                        |
|                                                             |
| Meeting [0, 30] -> Heap: [30] (1 room)                      |
| Meeting [5, 10] -> 5 < 30 (Conflict!) -> Heap: [10, 30] (2) |
| Meeting [15, 20]-> 15 >= 10 (Reuse room!)                   |
|                    poll 10, push 20 -> Heap: [20, 30] (2)   |
|                                                             |
| Max concurrent rooms = heap.size() = 2                      |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.Arrays;
import java.util.PriorityQueue;

class Solution {
    public int minMeetingRooms(int[][] intervals) {
        if (intervals == null || intervals.length == 0) return 0;

        // Sort meetings by start time
        Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));

        // Min-heap to track active meetings' end times
        PriorityQueue<Integer> minHeap = new PriorityQueue<>();

        // Add first meeting's end time
        minHeap.offer(intervals[0][1]);

        for (int i = 1; i < intervals.length; i++) {
            // If earliest meeting ended before current starts, reuse that room
            if (intervals[i][0] >= minHeap.peek()) {
                minHeap.poll();
            }

            // Allocate room
            minHeap.offer(intervals[i][1]);
        }

        return minHeap.size();
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `[[0, 30], [5, 10], [15, 20]]`
  - Meeting 1: `heap = [30]`.
  - Meeting 2: start $5 < 30 \rightarrow$ new room! `heap = [10, 30]`.
  - Meeting 3: start $15 \ge 10 \rightarrow$ reuse room! Poll 10, add 20. `heap = [20, 30]`.
  - Return heap size: 2.
- **Data Structures Used & Why**:
  - `PriorityQueue<Integer>` (Min-Heap): Gives $\mathcal{O}(1)$ immediate access to the earliest finishing meeting room.

---

## 54. Set Matrix Zeroes (LeetCode #73)

### Problem Introduction & Example
Given an `m x n` integer matrix `matrix`, if an element is 0, set its entire row and column to 0's **in place** with $\mathcal{O}(1)$ extra memory.

- **Example**:
  - Input: `matrix = [[1, 1, 1], [1, 0, 1], [1, 1, 1]]`
  - Output: `[[1, 0, 1], [0, 0, 0], [1, 0, 1]]`

### High-Level Solution Intuition
**How to get $\mathcal{O}(1)$ space without creating extra marker arrays?**
Use the **first row and first column of the matrix itself as your marker arrays**!
- `matrix[r][0] = 0` indicates that row `r` should be zeroed.
- `matrix[0][c] = 0` indicates that column `c` should be zeroed.

Because cell `matrix[0][0]` overlaps both row 0 and column 0, we use a separate boolean variable `firstColZero` to track the state of column 0.
1. Scan the matrix: if `matrix[r][c] == 0`, set flags in row 0 and column 0.
2. Use the flags to zero out the inner cells `(1..m-1, 1..n-1)`.
3. Finally, zero out row 0 and column 0 based on their individual flags.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(M \times N)$ — Two passes through the matrix.
- **Space Complexity**: $\mathcal{O}(1)$ — Markers are stored in-place.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                 In-Place Matrix Zero Markers                |
+-------------------------------------------------------------+
|    Col 0    Col 1    Col 2                                  |
|   +-----------------------+                                 |
| R0|  [0,0]    0        1  |  <- Row 0 acts as col markers   |
| R1|    0      0        0  |                                 |
| R2|    1      0        1  |                                 |
|   +-----------------------+                                 |
|     ^                                                       |
|   Col 0 acts as row markers                                 |
|   'firstColZero' tracks original col 0 state                |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public void setZeroes(int[][] matrix) {
        int rows = matrix.length;
        int cols = matrix[0].length;
        boolean firstColZero = false;

        // Step 1: Record zero markers in first row and first column
        for (int r = 0; r < rows; r++) {
            if (matrix[r][0] == 0) {
                firstColZero = true;
            }
            for (int c = 1; c < cols; c++) {
                if (matrix[r][c] == 0) {
                    matrix[r][0] = 0;
                    matrix[0][c] = 0;
                }
            }
        }

        // Step 2: Use markers to zero out inner cells
        for (int r = 1; r < rows; r++) {
            for (int c = 1; c < cols; c++) {
                if (matrix[r][0] == 0 || matrix[0][c] == 0) {
                    matrix[r][c] = 0;
                }
            }
        }

        // Step 3: Zero out first row if needed
        if (matrix[0][0] == 0) {
            for (int c = 0; c < cols; c++) {
                matrix[0][c] = 0;
            }
        }

        // Step 4: Zero out first column if needed
        if (firstColZero) {
            for (int r = 0; r < rows; r++) {
                matrix[r][0] = 0;
            }
        }
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `[[1, 1], [0, 1]]`
  - Cell `(1, 0) == 0` $\rightarrow$ `firstColZero = true`, `matrix[1][0] = 0`.
  - Column 0 and row 1 zeroed $\rightarrow$ `[[0, 1], [0, 0]]`.
- **Data Structures Used & Why**:
  - Repurposing row 0 and column 0: Eliminates external $\mathcal{O}(M + N)$ boolean arrays.

---

## 55. Spiral Matrix (LeetCode #54)

### Problem Introduction & Example
Given an `m x n` matrix, return all elements of the matrix in spiral order.

- **Example**:
  - Input: `matrix = [[1,2,3],[4,5,6],[7,8,9]]`
  - Output: `[1,2,3,6,9,8,7,4,5]`

### High-Level Solution Intuition
**Peeling the Onion Layer by Layer**:
Maintain 4 boundary walls: `top`, `bottom`, `left`, `right`.
While `top <= bottom` and `left <= right`:
1. Move **Right** along `top` row, then increment `top++`.
2. Move **Down** along `right` column, then decrement `right--`.
3. Move **Left** along `bottom` row (if `top <= bottom`), then decrement `bottom--`.
4. Move **Up** along `left` column (if `left <= right`), then increment `left++`.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(M \times N)$ — Every cell is visited once.
- **Space Complexity**: $\mathcal{O}(1)$ — Constant boundary memory.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                    Spiral Matrix Boundaries                 |
+-------------------------------------------------------------+
|           top ->  1  ------> 2  ------> 3                   |
|                   ^                     |                   |
|                   |                     v                   |
|                   4          5          6                   |
|                   ^                     |                   |
|                   |                     v                   |
|        bottom ->  7  <------ 8 <------- 9                   |
|                   ^                     ^                   |
|                  left                 right                 |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> result = new ArrayList<>();
        if (matrix == null || matrix.length == 0) return result;

        int top = 0;
        int bottom = matrix.length - 1;
        int left = 0;
        int right = matrix[0].length - 1;

        while (top <= bottom && left <= right) {
            // Traverse Right
            for (int c = left; c <= right; c++) {
                result.add(matrix[top][c]);
            }
            top++;

            // Traverse Down
            for (int r = top; r <= bottom; r++) {
                result.add(matrix[r][right]);
            }
            right--;

            // Traverse Left (ensure row hasn't crossed)
            if (top <= bottom) {
                for (int c = right; c >= left; c--) {
                    result.add(matrix[bottom][c]);
                }
                bottom--;
            }

            // Traverse Up (ensure col hasn't crossed)
            if (left <= right) {
                for (int r = bottom; r >= top; r--) {
                    result.add(matrix[r][left]);
                }
                left++;
            }
        }

        return result;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `[[1, 2], [3, 4]]`
  - Right: 1, 2 (`top = 1`). Down: 4 (`right = 0`). Left: 3 (`bottom = 0`).
  - Result: `[1, 2, 4, 3]`.
- **Data Structures Used & Why**:
  - 4 bounding variables (`top, bottom, left, right`): Shrinks boundaries cleanly with zero auxiliary 2D arrays.

---

## 56. Rotate Image (LeetCode #48)

### Problem Introduction & Example
You are given an `n x n` 2D matrix representing an image. Rotate the image by 90 degrees clockwise **in place** (do not allocate another matrix).

- **Example**:
  - Input: `matrix = [[1,2,3],[4,5,6],[7,8,9]]`
  - Output: `[[7,4,1],[8,5,2],[9,6,3]]`

### High-Level Solution Intuition
**A Clever Mathematical Trick**:
Rotating an image by 90 degrees clockwise can be decomposed into two simpler operations:
1. **Transpose the matrix** (reflect across the main diagonal: swap `matrix[i][j]` with `matrix[j][i]`).
2. **Reverse each row horizontally** (swap elements from left to right).

$$\begin{pmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \\ 7 & 8 & 9 \end{pmatrix} \xrightarrow{\text{Transpose}} \begin{pmatrix} 1 & 4 & 7 \\ 2 & 5 & 8 \\ 3 & 6 & 9 \end{pmatrix} \xrightarrow{\text{Reverse Rows}} \begin{pmatrix} 7 & 4 & 1 \\ 8 & 5 & 2 \\ 9 & 6 & 3 \end{pmatrix}$$

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n^2)$ — Transpose visits each pair once, row reversal visits each row once.
- **Space Complexity**: $\mathcal{O}(1)$ — Modifies matrix in-place.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                  Transpose + Reverse Rows                   |
+-------------------------------------------------------------+
| 1 2 3          1 4 7           7 4 1                        |
| 4 5 6  ----->  2 5 8  ----->   8 5 2                        |
| 7 8 9          3 6 9           9 6 3                        |
|                                                             |
| Step 1: Transpose matrix (swap along diagonal)              |
| Step 2: Reverse each row horizontally                       |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public void rotate(int[][] matrix) {
        int n = matrix.length;

        // Step 1: Transpose matrix (reflect along main diagonal)
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                int temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }

        // Step 2: Reverse each row horizontally
        for (int i = 0; i < n; i++) {
            int left = 0;
            int right = n - 1;
            while (left < right) {
                int temp = matrix[i][left];
                matrix[i][left] = matrix[i][right];
                matrix[i][right] = temp;
                left++;
                right--;
            }
        }
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `[[1, 2], [3, 4]]`
  - Transpose: swap `(0, 1)` and `(1, 0)` $\rightarrow$ `[[1, 3], [2, 4]]`.
  - Reverse row 0: `[1, 3] -> [3, 1]`. Reverse row 1: `[2, 4] -> [4, 2]`.
  - Result: `[[3, 1], [4, 2]]`.
- **Data Structures Used & Why**:
  - In-place swaps: Clean mathematical decomposition (Transpose + Reverse) eliminates complex 4-way coordinate rotation indexing and avoids $\mathcal{O}(n^2)$ extra space.


# Category 7: Dynamic Programming

---

## 57. Climbing Stairs (LeetCode #70)

### Problem Introduction & Example
You are climbing a staircase that has `n` total steps. Each time, you can choose to climb either 1 step or 2 steps. In how many distinct ways can you climb to the very top?

- **Example**:
  - Input: `n = 3`
  - Output: `3`
  - Explanation: The 3 distinct ways are:
    1. 1 step + 1 step + 1 step
    2. 1 step + 2 steps
    3. 2 steps + 1 step

### High-Level Solution Intuition
**The "Aha!" Breakthrough (Working Backwards from the Top)**:
To reach step $i$, where could you have possibly come from on your last move?
- You could have taken a 1-step leap from step $i - 1$.
- You could have taken a 2-step leap from step $i - 2$.
Therefore, the total number of ways to reach step $i$ is simply:
$$\text{ways}(i) = \text{ways}(i - 1) + \text{ways}(i - 2)$$
This is identical to the famous **Fibonacci Sequence**!
Instead of storing all previous answers in a large array, we only need to remember the last two step counts (`prev1` and `prev2`), keeping space complexity at $\mathcal{O}(1)$.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — A single loop from 3 up to $n$.
- **Space Complexity**: $\mathcal{O}(1)$ — Only two scalar variables are kept in memory.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                     Climbing Stairs DP                      |
+-------------------------------------------------------------+
| Step 1: 1 way                                               |
| Step 2: 2 ways                                              |
| Step 3: ways(2) + ways(1) = 2 + 1 = 3                       |
| Step 4: ways(3) + ways(2) = 3 + 2 = 5                       |
|                                                             |
| prev2 -> prev1 -> curr                                      |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public int climbStairs(int n) {
        if (n <= 2) return n;

        int prev2 = 1; // ways to reach step 1
        int prev1 = 2; // ways to reach step 2

        for (int i = 3; i <= n; i++) {
            int current = prev1 + prev2;
            prev2 = prev1;
            prev1 = current;
        }

        return prev1;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `n = 4`
  - $i=3$: `current = 2 + 1 = 3`, `prev2 = 2`, `prev1 = 3`.
  - $i=4$: `current = 3 + 2 = 5`, `prev2 = 3`, `prev1 = 5`.
  - Result: 5.
- **Data Structures Used & Why**:
  - Two integer variables: Fibonacci recurrence requires only the immediate two preceding states, saving $\mathcal{O}(n)$ heap memory.

---

## 58. Coin Change (LeetCode #322)

### Problem Introduction & Example
You are given an integer array `coins` representing coin denominations and an integer `amount`. Return the **fewest number of coins** you need to make up that exact amount. If it cannot be made up, return `-1`.

- **Example**:
  - Input: `coins = [1, 2, 5]`, `amount = 11`
  - Output: `3` (11 = 5 + 5 + 1)

### High-Level Solution Intuition
**Bottom-Up Dynamic Programming**:
Let `dp[a]` be the minimum number of coins needed to make amount `a`:
- Base case: `dp[0] = 0` (0 coins needed for amount 0).
- Initialize all other `dp[a]` to a large value (`amount + 1`).
- For each amount from 1 to `amount`, try every coin:
  - If `coin <= a`: `dp[a] = min(dp[a], 1 + dp[a - coin])`.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(\text{amount} \times C)$ — Where $C$ is the number of coin denominations.
- **Space Complexity**: $\mathcal{O}(\text{amount})$ — For the 1D DP array.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                      Coin Change 1D DP                      |
+-------------------------------------------------------------+
| dp[0] = 0, dp[1..amount] = inf                              |
|                                                             |
| For a from 1 to amount:                                     |
|    For each coin in coins:                                  |
|       if coin <= a:                                         |
|          dp[a] = min(dp[a], 1 + dp[a - coin])               |
|                                                             |
| Return dp[amount] > amount ? -1 : dp[amount]                |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.Arrays;

class Solution {
    public int coinChange(int[] coins, int amount) {
        if (amount < 0) return -1;
        if (amount == 0) return 0;

        int[] dp = new int[amount + 1];
        Arrays.fill(dp, amount + 1); // Sentinel value
        dp[0] = 0;

        for (int a = 1; a <= amount; a++) {
            for (int coin : coins) {
                if (a - coin >= 0) {
                    dp[a] = Math.min(dp[a], 1 + dp[a - coin]);
                }
            }
        }

        return dp[amount] > amount ? -1 : dp[amount];
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `coins = [1, 2]`, `amount = 3`
  - `dp[0] = 0`.
  - $a=1$: coin 1 $\rightarrow 1 + dp[0] = 1$.
  - $a=2$: coin 1 $\rightarrow 1 + dp[1] = 2$; coin 2 $\rightarrow 1 + dp[0] = 1$. Min is 1.
  - $a=3$: coin 1 $\rightarrow 1 + dp[2] = 2$; coin 2 $\rightarrow 1 + dp[1] = 2$. Min is 2.
  - Result: 2.
- **Data Structures Used & Why**:
  - `int[amount + 1]`: Caches subproblems bottom-up, preventing exponential recursion.

---

## 59. Longest Increasing Subsequence (LeetCode #300)

### Problem Introduction & Example
Given an integer array `nums`, return the length of the longest strictly increasing subsequence.

- **Example**:
  - Input: `nums = [10, 9, 2, 5, 3, 7, 101, 18]`
  - Output: `4` (Subsequence: `[2, 3, 7, 101]`).

### High-Level Solution Intuition
**Patience Sorting with Binary Search ($\mathcal{O}(n \log n)$)**:
Maintain an array `tails` where `tails[i]` stores the smallest tail element among all increasing subsequences of length $i + 1$.
For each number `x` in `nums`:
- Use Binary Search to find the position of `x` in `tails`.
- If `x` is greater than all tails, append it (expanding the LIS length!).
- Otherwise, replace the first element in `tails` that is $\ge x$ with `x` (giving future numbers a better chance to build a longer sequence).
The final length of `tails` is the maximum LIS length!

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n \log n)$ — Binary search on `tails` for each of the $n$ elements.
- **Space Complexity**: $\mathcal{O}(n)$ — For the `tails` array.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                Patience Sorting (LIS in O(n log n))         |
+-------------------------------------------------------------+
| x = 10 -> tails: [10]                                       |
| x = 9  -> replaces 10: [9]                                  |
| x = 2  -> replaces 9: [2]                                   |
| x = 5  -> appends: [2, 5]                                   |
| x = 3  -> replaces 5: [2, 3]                                |
| x = 7  -> appends: [2, 3, 7]                                |
| x = 101-> appends: [2, 3, 7, 101]                           |
| x = 18 -> replaces 101: [2, 3, 7, 18]                       |
| Final Length = 4                                            |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public int lengthOfLIS(int[] nums) {
        if (nums == null || nums.length == 0) return 0;

        int[] tails = new int[nums.length];
        int size = 0;

        for (int x : nums) {
            int left = 0, right = size;

            // Binary search for insertion position
            while (left < right) {
                int mid = left + (right - left) / 2;
                if (tails[mid] < x) {
                    left = mid + 1;
                } else {
                    right = mid;
                }
            }

            tails[left] = x;
            if (left == size) {
                size++;
            }
        }

        return size;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `nums = [0, 1, 0, 3, 2, 3]`
  - Tail progression: `[0]` $\rightarrow [0, 1] \rightarrow [0, 1, 3] \rightarrow [0, 1, 2] \rightarrow [0, 1, 2, 3]$. Length: 4.
- **Data Structures Used & Why**:
  - `tails[]` array with binary search: Replaces standard $\mathcal{O}(n^2)$ DP with optimal $\mathcal{O}(n \log n)$ time.

---

## 60. Word Break (LeetCode #139)

### Problem Introduction & Example
Given a string `s` and a dictionary of strings `wordDict`, return `true` if `s` can be segmented into a sequence of dictionary words.

- **Example**:
  - Input: `s = "leetcode"`, `wordDict = ["leet", "code"]`
  - Output: `true` (Can be split into `"leet code"`).

### High-Level Solution Intuition
Let `dp[i]` be `true` if the prefix of length `i` (`s[0..i-1]`) can be successfully segmented:
- `dp[0] = true` (an empty string is trivially segmented).
- For each length `i` from 1 to `s.length()`:
  - For each split point `j` from 0 to `i - 1`:
    - If `dp[j] == true` AND `wordDict.contains(s.substring(j, i))`, then `dp[i] = true`!

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n^2 \cdot L)$ — Where $n$ is string length and $L$ is substring extraction length.
- **Space Complexity**: $\mathcal{O}(n + M)$ — For the `dp` array and dictionary `HashSet`.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                      Word Break 1D DP                       |
+-------------------------------------------------------------+
| s: "leetcode"                                               |
| dp[0] = T  (empty)                                          |
| dp[4] = T  ("leet" in dict && dp[0] == T)                   |
| dp[8] = T  ("code" in dict && dp[4] == T)                   |
| Result = dp[8] = true                                       |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.*;

class Solution {
    public boolean wordBreak(String s, List<String> wordDict) {
        Set<String> wordSet = new HashSet<>(wordDict);
        boolean[] dp = new boolean[s.length() + 1];
        dp[0] = true; // Base case

        for (int i = 1; i <= s.length(); i++) {
            for (int j = 0; j < i; j++) {
                if (dp[j] && wordSet.contains(s.substring(j, i))) {
                    dp[i] = true;
                    break;
                }
            }
        }

        return dp[s.length()];
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `s = "applepenapple"`, `dict = ["apple", "pen"]`
  - $i=5$: `"apple"` valid $\rightarrow dp[5] = true$.
  - $i=8$: $dp[5]$ is true and `"pen"` valid $\rightarrow dp[8] = true$.
  - $i=13$: $dp[8]$ is true and `"apple"` valid $\rightarrow dp[13] = true$. Returns `true`.
- **Data Structures Used & Why**:
  - `HashSet<String>`: Provides $\mathcal{O}(1)$ average dictionary lookup compared to $\mathcal{O}(K)$ on a `List`.

---

## 61. House Robber (LeetCode #198)

### Problem Introduction & Example
You are a robber planning to rob houses along a street. Adjacent houses have security alarms that trigger if two adjacent houses are robbed on the same night. Return the maximum money you can rob without alerting the police.

- **Example**:
  - Input: `nums = [1, 2, 3, 1]`
  - Output: `4` (Rob house 0 ($1$) + house 2 ($3$) = $4$).

### High-Level Solution Intuition
At each house `i`:
- **Option 1**: Rob house `i` $\rightarrow$ add `nums[i]` to money from house `i - 2`.
- **Option 2**: Skip house `i` $\rightarrow$ keep money from house `i - 1`.
$$\text{rob}(i) = \max(\text{rob}(i - 1), \text{rob}(i - 2) + nums[i])$$
Only the previous two values are needed, enabling $\mathcal{O}(1)$ space!

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — Single pass over houses.
- **Space Complexity**: $\mathcal{O}(1)$ — Two scalar variables.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                     House Robber State                      |
+-------------------------------------------------------------+
| rob1 (house i - 2)    rob2 (house i - 1)                    |
|                                                             |
| For each num in nums:                                       |
|    newRob = max(rob2, rob1 + num)                           |
|    rob1 = rob2                                              |
|    rob2 = newRob                                            |
| Return rob2                                                 |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public int rob(int[] nums) {
        if (nums == null || nums.length == 0) return 0;

        int rob1 = 0; // max profit up to house i - 2
        int rob2 = 0; // max profit up to house i - 1

        for (int num : nums) {
            int current = Math.max(rob2, rob1 + num);
            rob1 = rob2;
            rob2 = current;
        }

        return rob2;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `nums = [2, 7, 9, 3, 1]`
  - Progressive values: 2, 7, 11, 11, 12.
  - Final profit: 12.
- **Data Structures Used & Why**:
  - Two integer variables: Eliminates DP array allocations.

---

## 62. House Robber II (LeetCode #213)

### Problem Introduction & Example
Same as House Robber, but houses are arranged in a **circle** (the first house is adjacent to the last house).

- **Example**:
  - Input: `nums = [2, 3, 2]`
  - Output: `3` (Robbing house 0 ($2$) and house 2 ($2$) triggers alarms because they are adjacent in a circle).

### High-Level Solution Intuition
Because house 0 and house $n-1$ are neighbors, you can **never rob both**.
This splits into two linear subproblems:
1. Rob from index $0$ to $n - 2$ (exclude last house).
2. Rob from index $1$ to $n - 1$ (exclude first house).
The answer is $\max(\text{Subproblem 1}, \text{Subproblem 2})$.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — Two passes over the array.
- **Space Complexity**: $\mathcal{O}(1)$ — Constant memory.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                    Circular House Robber                    |
+-------------------------------------------------------------+
| Scenario 1: Rob houses [0 .. n-2]                           |
| Scenario 2: Rob houses [1 .. n-1]                           |
| Result = max(Scenario 1, Scenario 2)                        |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public int rob(int[] nums) {
        if (nums == null || nums.length == 0) return 0;
        if (nums.length == 1) return nums[0];

        return Math.max(robRange(nums, 0, nums.length - 2), 
                        robRange(nums, 1, nums.length - 1));
    }

    private int robRange(int[] nums, int start, int end) {
        int rob1 = 0;
        int rob2 = 0;

        for (int i = start; i <= end; i++) {
            int current = Math.max(rob2, rob1 + nums[i]);
            rob1 = rob2;
            rob2 = current;
        }

        return rob2;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `nums = [1, 2, 3, 1]`
  - Range `[0, 2]` yields 4. Range `[1, 3]` yields 3.
  - Max is 4.
- **Data Structures Used & Why**:
  - Reusing linear helper: Decomposes circular constraints into standard linear passes.

---

## 63. Decode Ways (LeetCode #91)

### Problem Introduction & Example
A message containing letters from A-Z can be encoded into numbers: `'A' -> "1"`, ..., `'Z' -> "26"`.
Given a string of digits `s`, return the number of ways to decode it.

- **Example**:
  - Input: `s = "226"`
  - Output: `3` ("BZ" (2 26), "VF" (22 6), or "BBF" (2 2 6)).

### High-Level Solution Intuition
Let `dp[i]` be the decode ways for prefix of length `i`:
- **Single digit**: If `s[i - 1]` is between 1 and 9, add `dp[i - 1]`.
- **Two digits**: If `s[i - 2..i - 1]` forms a number between 10 and 26, add `dp[i - 2]`.
State rolling reduces space to $\mathcal{O}(1)$.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — Single pass through string.
- **Space Complexity**: $\mathcal{O}(1)$ — Two scalar variables.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                      Decode Ways States                     |
+-------------------------------------------------------------+
| Digits:   "2"      "2"      "6"                             |
| dp:      dp[0]=1  dp[1]=1  dp[2]=2  dp[3]=3                 |
|                                                             |
| At '6': single digit "6" (valid) -> +dp[2] (2)              |
|         two digits "26" (valid)  -> +dp[1] (1)              |
| Total = 2 + 1 = 3                                           |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public int numDecodings(String s) {
        if (s == null || s.length() == 0 || s.charAt(0) == '0') {
            return 0;
        }

        int prev2 = 1; // dp[0]
        int prev1 = 1; // dp[1]

        for (int i = 2; i <= s.length(); i++) {
            int current = 0;
            int singleDigit = s.charAt(i - 1) - '0';
            int twoDigits = Integer.parseInt(s.substring(i - 2, i));

            if (singleDigit >= 1 && singleDigit <= 9) {
                current += prev1;
            }
            if (twoDigits >= 10 && twoDigits <= 26) {
                current += prev2;
            }

            prev2 = prev1;
            prev1 = current;
        }

        return prev1;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `s = "12"`
  - `prev2 = 1, prev1 = 1`.
  - $i=2$: single '2' valid (+1), two '12' valid (+1). `current = 2`.
  - Result: 2.
- **Data Structures Used & Why**:
  - Two state variables: Rolling states eliminate the DP array.

---

## 64. Unique Paths (LeetCode #62)

### Problem Introduction & Example
A robot on an `m x n` grid begins at `(0, 0)` and wants to reach `(m - 1, n - 1)`. It can only move either down or right. Return the number of unique paths.

- **Example**:
  - Input: `m = 3, n = 7`
  - Output: `28`

### High-Level Solution Intuition
To reach `(r, c)`, the robot must come from either `(r - 1, c)` or `(r, c - 1)`:
$$\text{paths}(r, c) = \text{paths}(r - 1, c) + \text{paths}(r, c - 1)$$
Can be space-optimized to a single 1D array `row[c] += row[c - 1]`.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(m \times n)$ — Visits every grid cell.
- **Space Complexity**: $\mathcal{O}(n)$ — 1D row array.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                      Unique Paths Grid                      |
+-------------------------------------------------------------+
|   1     1     1     1                                       |
|   1     2     3     4   (cell = above + left)               |
|   1     3     6    10                                       |
|                                                             |
| In 1D: row[c] = row[c] + row[c - 1]                         |
+-------------------------------------------------------------+
```

### Java Program
```java
import java.util.Arrays;

class Solution {
    public int uniquePaths(int m, int n) {
        int[] row = new int[n];
        Arrays.fill(row, 1); // Base case: first row

        for (int r = 1; r < m; r++) {
            for (int c = 1; c < n; c++) {
                row[c] += row[c - 1];
            }
        }

        return row[n - 1];
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `m = 3, n = 3`
  - Row 0: `[1, 1, 1]`
  - Row 1: `[1, 2, 3]`
  - Row 2: `[1, 3, 6]`. Result: 6.
- **Data Structures Used & Why**:
  - `int[n]`: Compresses 2D table to 1D row memory.

---

## 65. Jump Game (LeetCode #55)

### Problem Introduction & Example
Given an integer array `nums` where each element represents your maximum jump length, return `true` if you can reach the last index, or `false` otherwise.

- **Example 1**: `[2, 3, 1, 1, 4]` $\rightarrow$ `true`
- **Example 2**: `[3, 2, 1, 0, 4]` $\rightarrow$ `false`

### High-Level Solution Intuition
**Greedy Reachability**:
Track `maxReach`, the farthest index reachable so far.
Iterate through `nums`:
- If `i > maxReach`, you are trapped $\rightarrow$ return `false`.
- Update `maxReach = max(maxReach, i + nums[i])`.
- If `maxReach >= n - 1`, return `true`.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — Single forward pass.
- **Space Complexity**: $\mathcal{O}(1)$ — Single scalar variable.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                      Greedy Jump Reach                      |
+-------------------------------------------------------------+
| i=0: maxReach = max(0, 0 + 2) = 2                           |
| i=1: maxReach = max(2, 1 + 3) = 4 >= lastIndex -> SUCCESS!  |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public boolean canJump(int[] nums) {
        int maxReach = 0;

        for (int i = 0; i < nums.length; i++) {
            if (i > maxReach) {
                return false;
            }
            maxReach = Math.max(maxReach, i + nums[i]);
            if (maxReach >= nums.length - 1) {
                return true;
            }
        }

        return true;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `[3, 2, 1, 0, 4]`
  - Reaches index 3 with `maxReach = 3`.
  - At index 4: $4 > 3 \rightarrow$ returns `false`.
- **Data Structures Used & Why**:
  - Scalar `maxReach`: Solves reachability without extra data structures.

---

## 66. Maximum Subarray (LeetCode #53)

### Problem Introduction & Example
Given an integer array `nums`, find the subarray with the largest sum, and return its sum.

- **Example**:
  - Input: `nums = [-2, 1, -3, 4, -1, 2, 1, -5, 4]`
  - Output: `6` (Subarray `[4, -1, 2, 1]`).

### High-Level Solution Intuition
**Kadane's Algorithm (Drop the Baggage!)**:
As you scan elements, maintain `currentSum`:
- If `currentSum < 0`, carrying it forward will only drag down future sums. Reset `currentSum = 0`!
- Add `nums[i]` to `currentSum`.
- Update `maxSum = max(maxSum, currentSum)`.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — Single pass through array.
- **Space Complexity**: $\mathcal{O}(1)$ — Constant memory.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                     Kadane's Algorithm                      |
+-------------------------------------------------------------+
| For each num in nums:                                       |
|    if currentSum < 0: currentSum = 0                        |
|    currentSum += num                                        |
|    maxSum = max(maxSum, currentSum)                         |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public int maxSubArray(int[] nums) {
        int maxSum = nums[0];
        int currentSum = 0;

        for (int num : nums) {
            if (currentSum < 0) {
                currentSum = 0;
            }
            currentSum += num;
            maxSum = Math.max(maxSum, currentSum);
        }

        return maxSum;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `[-2, 1, -3, 4, -1, 2, 1]`
  - Reset at -2 $\rightarrow$ pick 1 $\rightarrow$ reset at -2 $\rightarrow$ pick 4, -1, 2, 1 $\rightarrow$ sum 6.
- **Data Structures Used & Why**:
  - Scalar variables: Kadane's algorithm reduces quadratic subproblem searches to an optimal linear scan.

---

## 67. Maximum Product Subarray (LeetCode #152)

### Problem Introduction & Example
Given an integer array `nums`, find a subarray that has the largest product, and return that product.

- **Example**:
  - Input: `nums = [2, 3, -2, 4]`
  - Output: `6` (Subarray `[2, 3]`).

### High-Level Solution Intuition
Multiplying by a negative number flips signs:
- A negative minimum product multiplied by another negative number becomes a **huge positive maximum**!
Therefore, maintain both `maxProd` and `minProd`:
- When `nums[i] < 0`, swap `maxProd` and `minProd` before multiplying!

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — Single pass.
- **Space Complexity**: $\mathcal{O}(1)$ — Constant scalar state.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                Maximum Product State Machine                |
+-------------------------------------------------------------+
| If num < 0: swap(maxProd, minProd)                          |
| maxProd = max(num, maxProd * num)                           |
| minProd = min(num, minProd * num)                           |
| result  = max(result, maxProd)                              |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public int maxProduct(int[] nums) {
        int result = nums[0];
        int maxProd = nums[0];
        int minProd = nums[0];

        for (int i = 1; i < nums.length; i++) {
            int num = nums[i];

            if (num < 0) {
                int temp = maxProd;
                maxProd = minProd;
                minProd = temp;
            }

            maxProd = Math.max(num, maxProd * num);
            minProd = Math.min(num, minProd * num);

            result = Math.max(result, maxProd);
        }

        return result;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `[-2, 3, -4]`
  - At -4, swapping max and min turns negative product into positive $24$. Result: 24.
- **Data Structures Used & Why**:
  - Dual scalars: Tracks both maximum and minimum products without arrays.

---

## 68. Palindromic Substrings (LeetCode #647)

### Problem Introduction & Example
Given a string `s`, return the number of palindromic substrings in it.

- **Example**:
  - Input: `s = "aaa"`
  - Output: `6` (`"a"`, `"a"`, `"a"`, `"aa"`, `"aa"`, `"aaa"`).

### High-Level Solution Intuition
**Expand Around Centers**:
Every palindrome has a center:
- Odd-length: centered at single character `(i, i)`.
- Even-length: centered between two characters `(i, i + 1)`.
For each of the $2n - 1$ centers, expand outward while characters match, incrementing the count.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n^2)$ — $2n - 1$ centers, each expanding at most $n/2$ steps.
- **Space Complexity**: $\mathcal{O}(1)$ — In-place expansion pointers.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                   Expand Around Center                      |
+-------------------------------------------------------------+
| For each center i:                                          |
|    count += expand(i, i)                                    |
|    count += expand(i, i + 1)                                |
| Return count                                                |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public int countSubstrings(String s) {
        int count = 0;

        for (int i = 0; i < s.length(); i++) {
            count += countPalindromes(s, i, i);     // Odd length
            count += countPalindromes(s, i, i + 1); // Even length
        }

        return count;
    }

    private int countPalindromes(String s, int left, int right) {
        int count = 0;
        while (left >= 0 && right < s.length() && s.charAt(left) == s.charAt(right)) {
            count++;
            left--;
            right++;
        }
        return count;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `s = "abc"`
  - Centers (0,0), (1,1), (2,2) each contribute 1. Total: 3.
- **Data Structures Used & Why**:
  - Two pointers: Eliminates 2D DP matrix allocations.

---

## 69. Longest Palindromic Substring (LeetCode #5)

### Problem Introduction & Example
Given a string `s`, return the longest palindromic substring in `s`.

- **Example**:
  - Input: `s = "babad"`
  - Output: `"bab"` (or `"aba"`).

### High-Level Solution Intuition
Expand around all $2n - 1$ centers `(i, i)` and `(i, i + 1)`.
Keep track of the start index and maximum length found during expansion.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n^2)$ — Up to $2n$ centers expanding at most $n$ times.
- **Space Complexity**: $\mathcal{O}(1)$ — In-place expansion pointers.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|             Longest Palindromic Center Expansion            |
+-------------------------------------------------------------+
| For each center i:                                          |
|    expand(i, i)                                             |
|    expand(i, i + 1)                                         |
| Return substring(start, start + maxLen)                     |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    private int start = 0;
    private int maxLen = 0;

    public String longestPalindrome(String s) {
        if (s == null || s.length() < 2) return s;

        for (int i = 0; i < s.length(); i++) {
            expand(s, i, i);     // Odd length
            expand(s, i, i + 1); // Even length
        }

        return s.substring(start, start + maxLen);
    }

    private void expand(String s, int left, int right) {
        while (left >= 0 && right < s.length() && s.charAt(left) == s.charAt(right)) {
            left--;
            right++;
        }

        int currentLen = right - left - 1;
        if (currentLen > maxLen) {
            maxLen = currentLen;
            start = left + 1;
        }
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `s = "cbbd"`
  - Center `(1, 2)` ('b', 'b') yields length 2 (`"bb"`). Output: `"bb"`.
- **Data Structures Used & Why**:
  - Two pointers: Provides $\mathcal{O}(1)$ space compared to $\mathcal{O}(n^2)$ DP tables.

---

## 70. Longest Common Subsequence (LeetCode #1143)

### Problem Introduction & Example
Given two strings `text1` and `text2`, return the length of their longest common subsequence.

- **Example**:
  - Input: `text1 = "abcde"`, `text2 = "ace"`
  - Output: `3` (Subsequence `"ace"`).

### High-Level Solution Intuition
Let `dp[i][j]` be the length of LCS of prefixes `text1[0..i-1]` and `text2[0..j-1]`:
- If characters match (`text1[i - 1] == text2[j - 1]`):
  $$dp[i][j] = 1 + dp[i - 1][j - 1]$$
- If characters do not match:
  $$dp[i][j] = \max(dp[i - 1][j], dp[i][j - 1])$$

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(M \times N)$ — Where $M$ and $N$ are string lengths.
- **Space Complexity**: $\mathcal{O}(M \times N)$ — 2D DP matrix.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                      LCS 2D Table                           |
+-------------------------------------------------------------+
|       ""    a    c    e                                     |
|  ""    0    0    0    0                                     |
|   a    0    1    1    1    (match 'a' -> 1 + diagonal)      |
|   b    0    1    1    1                                     |
|   c    0    1    2    2    (match 'c' -> 1 + diagonal)      |
|   d    0    1    2    2                                     |
|   e    0    1    2    3    (match 'e' -> 1 + diagonal)      |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public int longestCommonSubsequence(String text1, String text2) {
        int m = text1.length();
        int n = text2.length();
        int[][] dp = new int[m + 1][n + 1];

        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (text1.charAt(i - 1) == text2.charAt(j - 1)) {
                    dp[i][j] = 1 + dp[i - 1][j - 1];
                } else {
                    dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]);
                }
            }
        }

        return dp[m][n];
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `text1 = "abc"`, `text2 = "ac"`
  - Match 'a' $\rightarrow$ 1. Match 'c' $\rightarrow$ 2. Result: 2.
- **Data Structures Used & Why**:
  - `int[m + 1][n + 1]`: Caches subproblem solutions, converting an exponential $\mathcal{O}(2^{M+N})$ tree into polynomial time.


# Category 8: Bit Manipulation & Math

---

## 71. Number of 1 Bits (LeetCode #191)

### Problem Introduction & Example
Write a function that takes the binary representation of a positive integer `n` and returns the number of set bits (`1`s) it contains (also known as the Hamming weight).

- **Example**:
  - Input: `n = 11` (in binary: `1011`)
  - Output: `3` (There are three `1` bits).

### High-Level Solution Intuition
**The "Aha!" Breakthrough (Brian Kernighan's Algorithm)**:
Instead of looping 32 times and checking every bit one by one:
Notice what happens when you compute `n & (n - 1)`:
- In binary arithmetic, subtracting 1 flips the **lowest set bit (`1`)** to `0`, and turns all trailing `0`s to `1`s.
- When you perform `n & (n - 1)`, that lowest `1` bit is **wiped out to 0** while all higher bits remain completely unchanged!
Every time we execute `n = n & (n - 1)`, exactly one `1` bit vanishes.
So, we simply count how many times we can perform this operation until `n` becomes 0!

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(k)$ — Where $k$ is the number of `1` bits ($k \le 32$). The loop runs only as many times as there are set bits.
- **Space Complexity**: $\mathcal{O}(1)$ — Operates strictly in CPU registers.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                 Brian Kernighan's Bit Clear                 |
+-------------------------------------------------------------+
| n       = 12  ( 1 1 0 0 )                                   |
| n - 1   = 11  ( 1 0 1 1 )                                   |
| n & n-1 = 8   ( 1 0 0 0 )  <- Cleared lowest 1 bit!         |
|                                                             |
| Repeat until n == 0. Loop count = set bit count.            |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public int hammingWeight(int n) {
        int count = 0;

        while (n != 0) {
            n = n & (n - 1); // Clears the lowest set bit
            count++;
        }

        return count;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `n = 11` (binary `1011`)
  - Iteration 1: `11 & 10 = 10` (`1010`), `count = 1`.
  - Iteration 2: `10 & 9 = 8` (`1000`), `count = 2`.
  - Iteration 3: `8 & 7 = 0` (`0000`), `count = 3`.
  - Loop terminates. Returns 3.
- **Data Structures Used & Why**:
  - Primitive integer bitwise operations: Executes directly in CPU registers with zero object allocations.

---

## 72. Counting Bits (LeetCode #338)

### Problem Introduction & Example
Given an integer `n`, return an array `ans` of length `n + 1` such that for each `i` (`0 <= i <= n`), `ans[i]` is the number of `1`'s in the binary representation of `i`. Solve it in $\mathcal{O}(n)$ linear time.

- **Example**:
  - Input: `n = 5`
  - Output: `[0, 1, 1, 2, 1, 2]`
  - Explanation:
    - 0: `0` $\rightarrow$ 0
    - 1: `1` $\rightarrow$ 1
    - 2: `10` $\rightarrow$ 1
    - 3: `11` $\rightarrow$ 2
    - 4: `100` $\rightarrow$ 1
    - 5: `101` $\rightarrow$ 2

### High-Level Solution Intuition
**Dynamic Programming on Bits**:
Notice what happens when you shift a binary number right by 1 (`i >> 1` or `i / 2`):
- All bits shift right, dropping the last bit.
- Therefore, the number `i` has the exact same bit count as `i / 2`, plus `1` if `i` is odd!
$$\text{ans}[i] = \text{ans}[i >> 1] + (i \ \& \ 1)$$
Because `i / 2` has already been computed, we can build the entire answer array in a single pass!

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — One constant-time operation for each number from 0 to $n$.
- **Space Complexity**: $\mathcal{O}(1)$ — Excluding the returned output array.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                   Counting Bits Recurrence                  |
+-------------------------------------------------------------+
| ans[i] = ans[i >> 1] + (i & 1)                              |
|                                                             |
| i = 0: ans[0] = 0                                           |
| i = 1: ans[0] + 1 = 1                                       |
| i = 2: ans[1] + 0 = 1                                       |
| i = 3: ans[1] + 1 = 2                                       |
| i = 4: ans[2] + 0 = 1                                       |
| i = 5: ans[2] + 1 = 2                                       |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public int[] countBits(int n) {
        int[] ans = new int[n + 1];

        for (int i = 1; i <= n; i++) {
            // Count of (i >> 1) plus 1 if the lowest bit of i is 1
            ans[i] = ans[i >> 1] + (i & 1);
        }

        return ans;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `n = 4`
  - `ans[0] = 0`.
  - $i=1$: `ans[0] + 1 = 1`.
  - $i=2$: `ans[1] + 0 = 1`.
  - $i=3$: `ans[1] + 1 = 2`.
  - $i=4$: `ans[2] + 0 = 1`.
  - Output: `[0, 1, 1, 2, 1]`.
- **Data Structures Used & Why**:
  - `int[n + 1]`: Caches smaller subproblems, avoiding recalculation of bit counts for shared prefixes.

---

## 73. Reverse Bits (LeetCode #190)

### Problem Introduction & Example
Reverse the bits of a given 32-bit unsigned integer.

- **Example**:
  - Input: `00000010100101000001111010011100` (43261596)
  - Output: `00111001011110000010100101000000` (964176192)

### High-Level Solution Intuition
Loop exactly 32 times:
1. Make room in `result` by shifting it left: `result <<= 1`.
2. Extract the lowest bit of `n`: `(n & 1)`.
3. Add that bit to `result`: `result |= (n & 1)`.
4. Shift `n` right using the **logical unsigned shift operator `>>>`**: `n >>>= 1`.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(1)$ — Exactly 32 iterations.
- **Space Complexity**: $\mathcal{O}(1)$ — Single scalar variable.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                     Reverse 32 Bits Flow                    |
+-------------------------------------------------------------+
| result = 0                                                  |
| Loop 32 times:                                              |
|    result = (result << 1) | (n & 1)                         |
|    n = n >>> 1                                              |
| Return result                                               |
+-------------------------------------------------------------+
```

### Java Program
```java
public class Solution {
    // treat n as an unsigned value
    public int reverseBits(int n) {
        int result = 0;

        for (int i = 0; i < 32; i++) {
            // Shift result left to make room for next bit
            result <<= 1;
            // Add the lowest bit of n to result
            result |= (n & 1);
            // Logical unsigned shift n right
            n >>>= 1;
        }

        return result;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: For 4 bits (e.g. `n = 0b0011`):
  - Iteration 1: bit = 1, `result = 1`, `n = 001`.
  - Iteration 2: bit = 1, `result = 11`, `n = 00`.
  - Iteration 3: bit = 0, `result = 110`, `n = 0`.
  - Iteration 4: bit = 0, `result = 1100`, `n = 0`.
  - Result is `1100` (reversed!).
- **Data Structures Used & Why**:
  - Primitive 32-bit `int` with unsigned shift `>>>`: Directly uses native hardware registers without heap overhead.

---

## 74. Missing Number (LeetCode #268)

### Problem Introduction & Example
Given an array `nums` containing `n` distinct numbers in the range `[0, n]`, return the only number in the range that is missing from the array.

- **Example**:
  - Input: `nums = [3, 0, 1]`
  - Output: `2` (Range is `[0, 3]`, missing number is 2).

### High-Level Solution Intuition
**The "Aha!" Breakthrough (XOR Cancellation)**:
In bitwise logic, XOR ($\oplus$) has two amazing properties:
1. Any number XORed with itself cancels out to zero: $x \oplus x = 0$.
2. Any number XORed with zero stays itself: $x \oplus 0 = x$.

If we XOR all the expected numbers from $0$ to $n$, and also XOR all the actual numbers present in `nums`:
Every number that is present will appear **twice** (once in the range and once in `nums`) and cancel out to 0!
The single number that is missing will only appear **once**, surviving as the final result!
This avoids any risk of 32-bit integer overflow that Gauss's summation formula could cause on huge arrays.

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(n)$ — Single pass through the array.
- **Space Complexity**: $\mathcal{O}(1)$ — Constant memory.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                      XOR Cancellation                       |
+-------------------------------------------------------------+
| Expected [0..3]:   0 ^ 1 ^ 2 ^ 3                            |
| Actual nums:       3 ^ 0 ^ 1                                |
|                                                             |
| Combined XOR:                                               |
| (0 ^ 0) ^ (1 ^ 1) ^ (3 ^ 3) ^ 2 = 0 ^ 0 ^ 0 ^ 2 = 2!        |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public int missingNumber(int[] nums) {
        int missing = nums.length;

        for (int i = 0; i < nums.length; i++) {
            missing ^= i ^ nums[i];
        }

        return missing;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `nums = [3, 0, 1]` ($n = 3$)
  - Initial `missing = 3`.
  - $i=0$: `missing ^= 0 ^ 3 = 0`.
  - $i=1$: `missing ^= 1 ^ 0 = 1`.
  - $i=2$: `missing ^= 2 ^ 1 = 2`.
  - Result: 2.
- **Data Structures Used & Why**:
  - Bitwise XOR on primitive integer: Completely immune to arithmetic integer overflow and runs in $\mathcal{O}(1)$ space without sorting or hash sets.

---

## 75. Sum of Two Integers (LeetCode #371)

### Problem Introduction & Example
Given two integers `a` and `b`, return the sum of the two integers without using the operators `+` and `-`.

- **Example**:
  - Input: `a = 1, b = 2`
  - Output: `3`

### High-Level Solution Intuition
**Simulating a Digital Logic Half-Adder**:
Computers add numbers using logic gates:
1. **Addition without carry**: The XOR operator `a ^ b` adds bits where only one of them is 1 (like adding bits without carrying over).
2. **Carry**: The AND operator followed by left shift `(a & b) << 1` identifies bits where both were 1 and shifts the carry to the next higher power of 2.
We set `a = sum` and `b = carry`, and repeat until there are no carries left (`b == 0`)!

### Complexity Analysis
- **Time Complexity**: $\mathcal{O}(1)$ — At most 32 loop iterations for 32-bit integers.
- **Space Complexity**: $\mathcal{O}(1)$ — Constant scalar memory.

### Pseudocode & High-Level Skeleton (ASCII Diagram)
```
+-------------------------------------------------------------+
|                   Hardware Adder Simulation                 |
+-------------------------------------------------------------+
| While b != 0:                                               |
|    carry = (a & b) << 1                                     |
|    a     = a ^ b       (partial sum without carry)          |
|    b     = carry       (propagate carry)                    |
| Return a                                                    |
+-------------------------------------------------------------+
```

### Java Program
```java
class Solution {
    public int getSum(int a, int b) {
        while (b != 0) {
            // Carry is generated where both bits are 1, shifted left by 1
            int carry = (a & b) << 1;

            // Sum without carry
            a = a ^ b;

            // Propagate carry to be added in the next cycle
            b = carry;
        }

        return a;
    }
}
```

### Example Trace & Data Structure Rationale
- **Step-by-Step Example Walkthrough**: `a = 2 (0010)`, `b = 3 (0011)`
  - Step 1: `carry = (2 & 3) << 1 = 4`, `a = 2 ^ 3 = 1`, `b = 4`.
  - Step 2: `carry = (1 & 4) << 1 = 0`, `a = 1 ^ 4 = 5`, `b = 0`.
  - Returns 5.
- **Data Structures Used & Why**:
  - Bitwise operations on primitive `int`: Simulates hardware addition at register speed.
