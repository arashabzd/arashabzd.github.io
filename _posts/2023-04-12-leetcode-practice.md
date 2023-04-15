---
title: LeetCode Practice 
date: 2023-04-12 13:49:00 +0330
categories: [Coding, Python]
tags: [leetcode, python]     # TAG names should always be lowercase
math: true
---
# LeetCode
My LeetCode practice notes

\# | Problem | Difficulty | Tags | Notes
---|---|---|---|---
1 | [TwoSum](https://leetcode.com/problems/two-sum/description/) | Easy | `Array` `Hash Table` `Two Pointers` | **Brute Force** $\mathcal O(n^2)$ <br/><br/> **Two Pointers** $\mathcal O(n\log n)$: *Sort and set two pointer at left and right of the list, increase left if `sum < target` and decrease right if `sum > target`.* <br/><br/> **Two-pass Hash Table** $\mathcal O(n)$: *Build a {number: index} table, for each element look for `target - element` in the table.* <br/><br/> **One-pass Hash Table** $\mathcal O(n)$: *Create the table on the fly.*
2 | [ThreeSum](https://leetcode.com/problems/3sum/) | Medium | `Array` `Hash Table` `Two Pointers` | **Two Pointers** $\mathcal O (n^2)$: *Sort and iterate the list for target, use two poiters approach to search in the rest of the list.* <br/><br/> **Hash Table** $\mathcal O (n^2)$: *Sort and build a {number: index} table, iterate the list for two numbers and search the third number in the table.*
3 | [ThreeSum Closest](https://leetcode.com/problems/3sum-closest/) | Medium | `Array` `Two Pointers` | **Two Pointers** $\mathcal O (n^2)$: Same as Two Pointers solution for ThreeSum problem but keep track of best distance and best sum.
4 | [Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/description/) | Easy | `String` | **Horizontal** $\mathcal O (c)$: $lcp(s_1, s_2, s_3) = lcp(lcp(s_1, s_2), s_3)$ <br/><br/> **Vertical** $\mathcal O (c)$: Find the shortest string and match its characters, one by one, with the rest of the strings.
5 | [Longest Substring without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/) | Medium | `String` `Window` `Hash Table` | **Window** $\mathcal O (n)$: Add unseen characters to a {char: index} table until you find a character that you have seen. If the seen character is outside of current window keep going else move the left pointer to the right of the previously seen character.
6 | [Longest Palindromic Substring]() | Medium | `String` `DP` | **DP** $\mathcal O (n^2)$: Substring `s[i:j+1]` is palindrome if `s[i]==s[j]` and `s[i+1:j]` is palindrome.
7 | [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/description/) | Easy | `Stack` | **Stack** $\mathcal O (n)$
8 | [Generate Parentheses](https://leetcode.com/problems/generate-parentheses/) | Medium | `Backtracking` `DP` | **Backtracking**: Assume a binary tree where edges are `(` and `)` and nodes are sequence of parentheses from root to that node (root is empty). Traverse the tree (depth first) to depth of n and check the validity of the parentheses. If not valid backtrack else if  you have n pairs of parentheses add the result and backtrack else continue traversing. <br/><br/> **Dynamic Programming**: Each element in the set of n-pair valid parentheses, `dp[n]` (n > 1), can be broken into  `( + *dp[i] + ) + *dp[n-i-1]` for `i=0,...,n-1` where `*dp[i]` is all the emelents of `dp[i]`.
9 | [Container with Most Water](https://leetcode.com/problems/container-with-most-water/description/) | Medium | `Array` `Two Pointers` `Greedy` | **Two Pointers** $\mathcal O (n)$:
10 | [Reverse Integer](https://leetcode.com/problems/reverse-integer/description/) | Medium | `Math` | $\mathcal O(\log_{10} n)$
<!-- 11 | [Jump Game]() -->