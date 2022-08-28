[Trie Delete](https://www.geeksforgeeks.org/trie-delete/)

```
/*package whatever //do not write package name here */
import java.util.List;
import java.util.ArrayList;

import java.io.*;

class GFG {
    
	public static void main (String[] args) {
		String keys[] = { "the", "a", "there",
                        "answer", "any", "by",
                        "bye", "their", "hero", "heroplane" };
        int n = keys.length;
 
        TrieNode root = new TrieNode();
 
        // Construct trie
        for (int i = 0; i < n; i++)
            insert(root, keys[i]);
 
        // Search for different keys
        if(search(root, "the"))
            System.out.println("Yes");
        else
            System.out.println("No");
 
        if(search(root, "these"))
            System.out.println("Yes");
        else
            System.out.println("No");
 
        remove(root, "heroplane", 0);
         
        if(search(root, "hero"))
            System.out.println("Yes");
        else
            System.out.println("No");
	}
	
	public static void insert(TrieNode currNode, String key) {
	    //TrieNode currNode = root;
        for(int i=0; i<key.length(); i++){
            char ch = key.charAt(i);
            int id = ch - 'a';
            if(currNode.children[id]==null){
                currNode.children[id] = new TrieNode();
            } 
            currNode = currNode.children[id];
        }
        currNode.isEndOfWord = true;
    }

    public static boolean search(TrieNode currNode, String key){
        // Your code here
        //TrieNode currNode = root;
        for(int i=0; i<key.length(); i++){
            char ch = key.charAt(i);
            int id = ch - 'a';
            if(currNode.children[id]==null){
                return false;
            }
            currNode = currNode.children[id];
        }
        return currNode.isEndOfWord;
    }
     
    public static TrieNode remove(TrieNode root, String key, int k){
    	if(k==key.length()){
    		if(root.isEndOfWord && isEmpty(root)){
    			root.isEndOfWord = false;
    			return null;
    		}
    		root.isEndOfWord = false;
    	}
    	int id = key.charAt(k)-'a';
    	root.children[id] = remove(root.children[id], key, ++k);
    
    	if(isEmpty(root) && !root.isEndOfWord){
    		return null;
    	}
    	return root;
    }

    public static boolean isEmpty(TrieNode root){
    	for(int i=0; i<root.children.length; i++){
    		if(root.children[i]!=null){
    			return false;
    		}
    	}
    	return true;
    }
}

class TrieNode{
    TrieNode[] children = new TrieNode[26];
    boolean isEndOfWord = false;
}
```
