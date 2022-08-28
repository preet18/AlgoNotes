[Auto Complete Feature Using Trie](https://www.geeksforgeeks.org/auto-complete-feature-using-trie/)

### Problem Statement
We are given a Trie with a set of strings stored in it. Now the user types in a prefix of his search query, we need to give him all recommendations to auto-complete his query based on the strings stored in the Trie. We assume that the Trie stores past searches by the users.
For example if the Trie store {“abc”, “abcd”, “aa”, “abbbaba”} and the User types in “ab” then he must be shown {“abc”, “abcd”, “abbbaba”}.


Trie with a strings in it.
user -> types prefix of search query, 
-> give him all recommendations to auto-complete his query based on the strings stored in the Trie.
    a 
   a b
    b c
   b   d
    a
     b
    a




### Solution

```
/*package whatever //do not write package name here */
import java.util.List;
import java.util.ArrayList;

import java.io.*;

class GFG {
    
	public static void main (String[] args) {
		System.out.println("GfG!");
		List<String> words = List.of("hello", "dog", "hell", "cat", "a", "hel","help","helps","helping", "hela");
		//Trie trie = new Trie(words);
		TrieNode root = new TrieNode();
		for(String word: words){
		    insert(root, word);
		}
		//System.out.println(trie.suggest("hel"));
		List<String> res = autoComplete(root, "hel");
		System.out.println("Count :: " + res.size());
		for(String word: res){
		    System.out.println(word);
		}
	}
	
	static void insert(TrieNode currNode, String key) {
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


	static List<String> autoComplete(TrieNode root, String key){
	    //TrieNode root = main;
	    List<String> res = new ArrayList<>();
    	for(int i=0; i<key.length(); i++){
    		int id = key.charAt(i)-'a';
    		if(root.children[id]==null){
    			return res;
    		}
    		root = root.children[id];
    	}
    	StringBuilder prefix = new StringBuilder(key);
    	findPossibleSearch(root, prefix, res);
    	return res;
    }

    static void findPossibleSearch(TrieNode currNode, StringBuilder prefix, List<String> res){
        if(currNode.isEndOfWord){
    		res.add(prefix.toString());
    	}
    	for(int i=0; i<currNode.children.length; i++){
    		if(currNode.children[i]!=null){
    			StringBuilder currString = new StringBuilder(prefix);
    			//System.out.println("Current Char :: " + (char)('a'+i));
    			currString.append((char)('a'+i));
    			findPossibleSearch(currNode.children[i], currString, res);
    		}
    	}
    	
    
    }
}

class TrieNode{
        TrieNode[] children = new TrieNode[26];
        boolean isEndOfWord = false;
    }

```
