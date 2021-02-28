### [Subtree of Another Tree](https://leetcode.com/problems/subtree-of-another-tree/)
Given two non-empty binary trees s and t, check whether tree t has exactly the same structure and node values with a subtree of s. A subtree of s is a tree consists of a node in s and all of this node's descendants. The tree s could also be considered as a subtree of itself.

##### Example 1:
Given tree s:

![](https://github.com/preet18/AlgoNotes/blob/master/Tree/Pictures/Image3.png)

Given tree t:

![](https://github.com/preet18/AlgoNotes/blob/master/Tree/Pictures/Image4.png)

Return true, because t has the same structure and node values with a subtree of s.

##### Example 2:
Given tree s:

![](https://github.com/preet18/AlgoNotes/blob/master/Tree/Pictures/Image5.png)

Given tree t:

![](https://github.com/preet18/AlgoNotes/blob/master/Tree/Pictures/Image6.png)

Return false.

### Solution
#### Method 1:

**Complexity:** O(N)|O(H)

#### Logic:
```
class Solution {
    public boolean isSubtree(TreeNode s, TreeNode t) {
        if (s == null) return false;
        if (isSame(s, t)) return true;
        return isSubtree(s.left, t) || isSubtree(s.right, t);
    }
    
    private boolean isSame(TreeNode s, TreeNode t) {
        if (s == null && t == null) return true;
        if (s == null || t == null) return false;
        
        if (s.val != t.val) return false;
        
        return isSame(s.left, t.left) && isSame(s.right, t.right);
    }

}
```

