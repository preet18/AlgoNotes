
[Kth Smallest Element in a BST](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)

**APPROACH 1**
``` Java
class Solution {
    //O(N)|O(H)
    public int kthSmallest(TreeNode root, int k) {
        if(root==null) return -1;
        Stack<TreeNode> stack = new Stack<TreeNode>();
        while(root!=null || !stack.isEmpty()){
            while(root!=null){
                stack.push(root);
                root = root.left;
            }
            TreeNode temp = stack.pop();
            if(--k==0) return temp.val;
            root = temp.right;
        }
        return -1;
    }
}
```

**APPROACH 2**
``` Java
class Solution {
    //Using Recursive Approach - O(N)|O(log(N))
    static class Result{
        int k;
        int val;
        Result(int k, int val){
            this.k = k;
            this.val = val;
        }
    }
    public int kthSmallest(TreeNode root, int k) {
        Result result = new Result(k, 0);
        inorderTraversal(root, result);
        return result.val;
    }
    public static void inorderTraversal(TreeNode root, Result result){
        if(root==null) return;
        inorderTraversal(root.left, result);
        if(--result.k==0){
            result.val = root.val;
        }
        inorderTraversal(root.right, result);
    }
    
}
```
