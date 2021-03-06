### [Lowest Common Ancestor of Binary Tree](https://www.geeksforgeeks.org/lowest-common-ancestor-binary-tree-set-1/)
[Leetcode](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)

Let T be a rooted tree. The lowest common ancestor between two nodes n1 and n2 is defined as the lowest node in T that has both n1 and n2 as descendants (where we allow a node to be a descendant of itself).

##### Example 1:
![](https://github.com/preet18/AlgoNotes/blob/master/Tree/Pictures/Image2.png)

**Input:** root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1\
**Output:** 3\
**Explanation:** The LCA of nodes 5 and 1 is 3.

##### Example 2:
![](https://github.com/preet18/AlgoNotes/blob/master/Tree/Pictures/Image1.png)

**Input:** root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 4\
**Output:** 5\
**Explanation:** The LCA of nodes 5 and 4 is 5, since a node can be a descendant of itself according to the LCA definition.

##### Example 3:
**Input:** root = [1,2], p = 1, q = 2\
**Output:** 1\

##### Constraints:
* The number of nodes in the tree is in the range [2, 10^5].
* -10^9 <= Node.val <= 10^9
* All Node.val are unique.
* p != q
* p and q will exist in the tree.

### Solution
#### Method 1:
Storing the path from root to n1 and path from root to n2. And comparing the paths to check the lowest/nearest common node to n1 and n2.

**Complexity:** O(N)|O(H)

#### Logic:
```
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        
    }
}
```

#### Method 2:
The idea is to traverse the tree starting from the root. If any of the given keys (n1 and n2) matches with the root, then the root is LCA (assuming that both keys are present). If the root doesn’t match with any of the keys, we recur for the left and right subtree. The node which has one key present in its left subtree and the other key present in the right subtree is the LCA. If both keys lie in the left subtree, then the left subtree has LCA also, otherwise, LCA lies in the right subtree.  

```
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        
    }
}
```

