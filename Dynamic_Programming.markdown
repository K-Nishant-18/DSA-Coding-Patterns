# Dynamic Programming Pattern in Java

## Overview
The **Dynamic Programming (DP)** pattern is a powerful technique used to solve optimization problems by breaking them down into overlapping subproblems and storing intermediate results to avoid redundant computations. DP is particularly effective for problems with recursive structures where the same subproblems are solved multiple times. It can be implemented using **memoization** (top-down, recursive) or **tabulation** (bottom-up, iterative) approaches.

## Use Cases
- Finding the longest common subsequence or substring between two strings.
- Solving knapsack problems (e.g., 0/1 knapsack, unbounded knapsack).
- Computing the minimum path sum in a grid or matrix.
- Solving problems like Fibonacci numbers, coin change, or longest palindromic subsequence.

## Approach
1. **Identify Overlapping Subproblems**: Determine if the problem can be broken into smaller subproblems that are reused.
2. **Define the State**: Represent the subproblem with a state (e.g., indices, remaining capacity, or current sum).
3. **Formulate the Recurrence Relation**: Write a formula that relates the solution of a subproblem to smaller subproblems.
4. **Implement Memoization or Tabulation**:
   - **Memoization**: Store results in a cache (e.g., HashMap or array) during recursive calls.
   - **Tabulation**: Build a table iteratively, filling it bottom-up based on the recurrence relation.
5. **Optimize Space**: If possible, reduce space complexity by storing only necessary states (e.g., using a rolling array).

## Example Problem: Longest Common Subsequence
Given two strings, find the length of their longest common subsequence (LCS). A subsequence is a sequence of characters that can be derived from a string by deleting some elements without changing the order of the remaining elements.

### Java Implementation
```java
public class LongestCommonSubsequence {
    public static int lcs(String text1, String text2) {
        int m = text1.length(), n = text2.length();
        // Initialize DP table
        int[][] dp = new int[m + 1][n + 1];

        // Fill table iteratively
        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (text1.charAt(i - 1) == text2.charAt(j - 1)) {
                    // If characters match, include them in LCS
                    dp[i][j] = dp[i - 1][j - 1] + 1;
                } else {
                    // Take the maximum of excluding either character
                    dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]);
                }
            }
        }

        return dp[m][n];
    }

    // Optional: Memoization-based solution
    public static int lcsMemoization(String text1, String text2) {
        Integer[][] memo = new Integer[text1.length() + 1][text2.length() + 1];
        return lcsHelper(text1, text2, text1.length(), text2.length(), memo);
    }

    private static int lcsHelper(String text1, String text2, int m, int n, Integer[][] memo) {
        if (m == 0 || n == 0) return 0;
        if (memo[m][n] != null) return memo[m][n];
        if (text1.charAt(m - 1) == text2.charAt(n - 1)) {
            memo[m][n] = 1 + lcsHelper(text1, text2, m - 1, n - 1, memo);
        } else {
            memo[m][n] = Math.max(lcsHelper(text1, text2, m - 1, n, memo),
                                  lcsHelper(text1, text2, m, n - 1, memo));
        }
        return memo[m][n];
    }

    public static void main(String[] args) {
        String text1 = "ABCDGH";
        String text2 = "AEDFHR";
        System.out.println("Length of LCS (Tabulation): " + lcs(text1, text2));
        System.out.println("Length of LCS (Memoization): " + lcsMemoization(text1, text2));
        // Output: Length of LCS (Tabulation): 3
        //         Length of LCS (Memoization): 3
        // Explanation: The LCS is "ADH" or "AFH", both of length 3.
    }
}
```

### Explanation
- **Problem**: Find the length of the longest common subsequence for strings `text1 = "ABCDGH"` and `text2 = "AEDFHR"`.
- **Tabulation Approach**:
  1. Create a DP table `dp[m+1][n+1]`, where `dp[i][j]` represents the length of the LCS for prefixes `text1[0:i]` and `text2[0:j]`.
  2. If characters match (`text1[i-1] == text2[j-1]`), include them: `dp[i][j] = dp[i-1][j-1] + 1`.
  3. If they don’t match, take the maximum of excluding either character: `dp[i][j] = max(dp[i-1][j], dp[i][j-1])`.
  4. The answer is `dp[m][n]`, which is 3 for subsequences like "ADH" or "AFH".
- **Memoization Approach**:
  1. Use a recursive function with a memoization table to cache results.
  2. Same logic as tabulation but implemented top-down.
- **Time Complexity**: O(m * n), where m and n are the lengths of the input strings.
- **Space Complexity**:
  - Tabulation: O(m * n) for the DP table.
  - Memoization: O(m * n) for the memo table, plus O(m + n) for the recursion stack.
- **Optimization Note**: Space can be optimized to O(min(m, n)) by using a rolling array, but this example prioritizes clarity.

## Practice Problems
- LeetCode: [Longest Common Subsequence](https://leetcode.com/problems/longest-common-subsequence/)
- LeetCode: [0/1 Knapsack](https://leetcode.com/problems/partition-equal-subset-sum/) (related to knapsack problems)
- LeetCode: [Longest Palindromic Subsequence](https://leetcode.com/problems/longest-palindromic-subsequence/)

## Additional Notes
- **Choosing Between Memoization and Tabulation**: Tabulation is often more space-efficient for iterative solutions, while memoization is easier to implement for complex recursive problems.
- **Common DP Patterns**: Look for problems involving "longest," "shortest," "maximum," or "minimum" (e.g., longest increasing subsequence, minimum edit distance).
- **Debugging Tip**: Print the DP table to visualize how subproblems are solved.

## Navigation
[Back to README](README.md)