### [Longest Common Subsequence](https://leetcode.com/problems/longest-common-subsequence/)
Given two strings text1 and text2, return the length of their longest common subsequence.

A subsequence of a string is a new string generated from the original string with some characters(can be none) deleted without changing the relative order of the remaining characters. (eg, "ace" is a subsequence of "abcde" while "aec" is not). A common subsequence of two strings is a subsequence that is common to both strings.

If there is no common subsequence, return 0.
##### Example 1:
**Input:** text1 = "abcde", text2 = "ace" 
**Output:** 3 
**Explanation:** The longest common subsequence is "ace" and its length is 3.

##### Example 2:
**Input:** text1 = "abc", text2 = "abc"
**Output:** 3
**Explanation:** The longest common subsequence is "abc" and its length is 3.

##### Example 3:
**Input:** text1 = "abc", text2 = "def"
**Output:** 0
**Explanation:** There is no such common subsequence, so the result is 0.

### Solution
#### Method 1:
Find all the substrings of String1 and add them to a list1, and find substrings of String2 now check if they are present in list1. 

**Complexity:** O(N^2+M^2)|O(N^3) 

#### Method 2:
Using Dynamic Programming

**Complexity:** O(M*N)|O(M*N)

##### Logic:
```
class Solution {
    public int longestCommonSubsequence(String text1, String text2) {
        int m = text1.length();
        int n = text2.length();
        int[][] arr = new int[m+1][n+1];
        for(int i=0; i<m+1; i++){
            for(int j=0; j<n+1; j++){
                if(i==0||j==0){
                    arr[i][j] = 0;
                }else if(text1.charAt(i-1)==text2.charAt(j-1)){
                    arr[i][j] = arr[i-1][j-1]+1;
                }else{
                    arr[i][j] = Math.max(arr[i-1][j], arr[i][j-1]);   
                }
            }
        }
        return arr[m][n];
    }
}
```
