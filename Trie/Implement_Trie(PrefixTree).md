
[Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree/)

``` Java
class Trie {
    
    TrieNode root;
    public Trie() {
        root = new TrieNode();
    }
    
    static class TrieNode{
        boolean isWord;
        TrieNode[] child = new TrieNode[26];

        void addTrieNode(char key){
            child[key-'a'] = new TrieNode();
        }
    }
    
    public void insert(String word) {
        TrieNode current = root;
        for(char ch: word.toCharArray()){
            if(current.child[ch-'a']==null){
                current.addTrieNode(ch);
            }
            current = current.child[ch-'a'];
        }
        current.isWord = true;
    }
    
    public boolean search(String word) {
        TrieNode current = root;
        for(char ch: word.toCharArray()){
            current = current.child[ch-'a'];
            if(current==null){
                return false;
            }
        }
        return current.isWord;
    }
    
    public boolean startsWith(String prefix) {
        TrieNode current = root;
        for(char ch: prefix.toCharArray()){
            current = current.child[ch-'a'];
            if(current==null){
                return false;
            }
        }
        return true;
        
    }
    
    
}



```
