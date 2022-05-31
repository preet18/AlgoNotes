[Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)

### Approach1: Using Queue
``` Java
class Solution {
    //O(N)|O(N)
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> list = new ArrayList<>();
        if(root==null) return list;
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);
        while(!queue.isEmpty()){
            int n = queue.size();
            list.add(new ArrayList<>());
            int len = list.size();
            for(int i=0; i<n; i++){
                TreeNode currNode = queue.poll();
                list.get(len-1).add(currNode.val);
                if(currNode.left!=null)
                    queue.add(currNode.left);
                if(currNode.right!=null)
                    queue.add(currNode.right);
            }
        }
        return list;
    }
}
```


### Approach2: Using Recursion
``` Java
class Solution {
    //O(N)|O(H)
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> lst = new ArrayList<>();
        if(root==null){
            return lst;
        }
        int level = 0;
        levelOrderUtil(lst, root, level);
        return lst;
    }
    
    public void levelOrderUtil(List<List<Integer>> lst, TreeNode root, int level){
        if(root==null){
            return;
        }
        if(lst.size()-1<level){
            lst.add(new ArrayList<>());
        }
        lst.get(level).add(root.val);
        levelOrderUtil(lst, root.left, level+1);
        levelOrderUtil(lst, root.right, level+1);
        return;
    }
}
```
