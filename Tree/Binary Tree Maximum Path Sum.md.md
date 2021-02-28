### [Binary Tree Maximum Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/)
A path in a binary tree is a sequence of nodes where each pair of adjacent nodes in the sequence has an edge connecting them. A node can only appear in the sequence at most once. Note that the path does not need to pass through the root.

The path sum of a path is the sum of the node's values in the path.

Given the root of a binary tree, return the maximum path sum of any path.

##### Example 1:
![](https://github.com/preet18/AlgoNotes/blob/master/Tree/Pictures/Image1.png)

**Input:** root = [1,2,3]\
**Output:** 6\
**Explanation:** The optimal path is 2 -> 1 -> 3 with a path sum of 2 + 1 + 3 = 6.

##### Example 2:
![](https://github.com/preet18/AlgoNotes/blob/master/Tree/Pictures/Image2.png)

**Input:** root = [-10,9,20,null,null,15,7]\
**Output:** 42\
**Explanation:** The optimal path is 15 -> 20 -> 7 with a path sum of 15 + 20 + 7 = 42.

##### Constraints:
The number of nodes in the tree is in the range [1, 3 * 104].\
-1000 <= Node.val <= 1000

### Solution
#### Method 1:
Finding the Sequence of elements with maximum sum in the given binary tree. 

**Complexity:** O(N)|O(H)

#### Logic:
```
class Solution {
    int maxValue;
    public int maxPathSum(TreeNode root) {
        if(root==null)
            return 0;
        maxValue = Integer.MIN_VALUE;
        maxPathSumUtil(root);
        return maxValue;
    }
    
    public int maxPathSumUtil(TreeNode root){
        if(root==null){
            return 0;
        }
        int left = Math.max(0, maxPathSumUtil(root.left));
        int right = Math.max(0, maxPathSumUtil(root.right));
        maxValue = Math.max(maxValue, left+right+root.val);
        return Math.max(left,right)+root.val;
    }
}
```

