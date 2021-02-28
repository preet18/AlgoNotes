### [Serialize and Deserialize Binary Tree](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/)
Serialization is the process of converting a data structure or object into a sequence of bits so that it can be stored in a file or memory buffer, or transmitted across a network connection link to be reconstructed later in the same or another computer environment.

Design an algorithm to serialize and deserialize a binary tree. There is no restriction on how your serialization/deserialization algorithm should work. You just need to ensure that a binary tree can be serialized to a string and this string can be deserialized to the original tree structure.

Clarification: The input/output format is the same as how LeetCode serializes a binary tree. You do not necessarily need to follow this format, so please be creative and come up with different approaches yourself.

##### Example 1:

![](https://github.com/preet18/AlgoNotes/blob/master/Tree/Pictures/Image7.png)

**Input:** root = [1,2,3,null,null,4,5]\
**Output:** [1,2,3,null,null,4,5]\

##### Example 2:

**Input:** root = []\
**Output:** []\

##### Example 3:

**Input:** root = [1]\
**Output:** [1]\

##### Example 4:

**Input:** root = [1,2]\
**Output:** [1,2]\

##### Constraints:

The number of nodes in the tree is in the range [0, 104].
-1000 <= Node.val <= 1000

### Solution
#### Method 1:

**Complexity:** O(N)|O(H)

#### Logic:
```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
public class Codec {
    int i=0;
    // Encodes a tree to a single string.
    public String serialize(TreeNode root) {
       
        if(root==null){
           return "";
       }
       StringBuilder sb = new StringBuilder();
        serializeUtil(root, sb);
        System.out.println(sb.toString().substring(0,sb.length()-1));
        return sb.toString().substring(0,sb.length()-1);
    }
    
    public void serializeUtil(TreeNode root, StringBuilder sb){
        if(root==null){
            sb.append("X,");
            return;
        }
        sb.append(root.val+",");
        serializeUtil(root.left, sb);
        serializeUtil(root.right, sb);
        return;
    }
    
    // Decodes your encoded data to tree.
   public TreeNode deserialize(String data) {
       if(data.length()==0){
            return null;
        }
       i=0;
       String[] arr = data.split(",");
       System.out.println(arr[0]);
       return deserializeUtil(arr);
    }
    
    public TreeNode deserializeUtil(String[] arr){
        if(arr[i].equals("X")){
            return null;
        }
        System.out.println(arr[i] + "- " + i);
        TreeNode node = new TreeNode(Integer.parseInt(arr[i]));
        i++;
        node.left = deserializeUtil(arr);
        i++;
        node.right = deserializeUtil(arr);
        return node; 
    }
    
    
}

// Your Codec object will be instantiated and called as such:
// Codec ser = new Codec();
// Codec deser = new Codec();
// TreeNode ans = deser.deserialize(ser.serialize(root));
```

