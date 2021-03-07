### [Lowest Common Ancestor of Binary Tree](https://www.geeksforgeeks.org/lowest-common-ancestor-binary-tree-set-1/)
[Leetcode](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)

Let T be a rooted tree. The lowest common ancestor between two nodes n1 and n2 is defined as the lowest node in T that has both n1 and n2 as descendants (where we allow a node to be a descendant of itself).

![](https://github.com/preet18/AlgoNotes/blob/master/Tree/Pictures/LCA%20of%20Binary%20Tree.png)

##### Example 1:
![](https://github.com/preet18/AlgoNotes/blob/master/Tree/Pictures/LCA%20of%20Binary%20Tree%20-%20Example%201.png)

**Input:** root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1\
**Output:** 3\
**Explanation:** The LCA of nodes 5 and 1 is 3.

##### Example 2:
![](https://github.com/preet18/AlgoNotes/blob/master/Tree/Pictures/LCA%20of%20Binary%20Tree%20-%20Example%201.png)

**Input:** root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 4\
**Output:** 5\
**Explanation:** The LCA of nodes 5 and 4 is 5, since a node can be a descendant of itself according to the LCA definition.

##### Example 3:
**Input:** root = [1,2], p = 1, q = 2\
**Output:** 1

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
    //O(N)|O(H)
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if(root==null) return null;
        
        List<TreeNode> m = new ArrayList<>();
        List<TreeNode> n = new ArrayList<>();
        
        lowerCommonAncestorUtil(root, p, m);
        lowerCommonAncestorUtil(root, q, n);
        
        TreeNode res = null;
        for(int i=0, j=0; i<m.size() && j<n.size(); i++,j++){
            if(m.get(i).val!=n.get(j).val){
                break;
            }
            res = m.get(i);
        }
        return res;
    }
    
    public boolean lowerCommonAncestorUtil(TreeNode root, TreeNode node, List<TreeNode> lst){
        if(root==null){
            return false;
        }
        lst.add(root);
        if(root.val==node.val) return true;
        if(lowerCommonAncestorUtil(root.left, node, lst)) return true;
        if(lowerCommonAncestorUtil(root.right, node, lst)) return true;
        lst.remove(lst.size()-1);
        return false;
    }
}
```

#### Method 2:
The idea is to traverse the tree starting from the root. If any of the given keys (n1 and n2) matches with the root, then the root is LCA (assuming that both keys are present). If the root doesn’t match with any of the keys, we recur for the left and right subtree. The node which has one key present in its left subtree and the other key present in the right subtree is the LCA. If both keys lie in the left subtree, then the left subtree has LCA also, otherwise, LCA lies in the right subtree.  

```
class Solution {
    
    //O(N)|O(H)
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if(root==null) return null;
        
        if(p.val==root.val || root.val==q.val){
            return root;
        }
        
        TreeNode left_lca = lowestCommonAncestor(root.left, p, q);
        TreeNode right_lca = lowestCommonAncestor(root.right, p, q);
        
        if(left_lca!=null && right_lca!=null){
            return root;
        }
        
        return left_lca!=null?left_lca:right_lca;
    }
}
```

