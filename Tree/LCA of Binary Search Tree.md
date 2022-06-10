[Lowest Common Ancestor of Binary Search Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)


**APPROACH 1** 
``` Java
class Solution {
    //Using recursive approach - O(N)|O(H)
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if(root==null) return root;
        if(p.val<root.val && q.val<root.val)
            return lowestCommonAncestor(root.left, p, q);
        else if(p.val>root.val && q.val>root.val)
            return lowestCommonAncestor(root.right, p, q);
        return root;
    }
}
```

**APPROACH 2**
``` Java
class Solution {
        //Using Iterative Approach - O(N)|O(H)
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        while(root!=null){
            if(p.val<root.val && q.val<root.val){
                root = root.left;
            }else if(p.val>root.val && q.val>root.val){
                root = root.right;
            }else{
                return root;
            }
        }
        return root;
    }
}
``` 
