[Design Add and Search Words Data Structure](https://leetcode.com/problems/design-add-and-search-words-data-structure/)

``` Java
class WordDictionary {
    static class TrieNode{
        boolean isWord;
        TrieNode[] child = new TrieNode[26];
    }
    
    TrieNode root;
    public WordDictionary() {
        root = new TrieNode();
    }
    
    public void addWord(String word) {
        TrieNode current = root;
        for(char ch: word.toCharArray()){
            if(current.child[ch-'a']==null){
                current.child[ch-'a'] = new TrieNode();
            }
            current = current.child[ch-'a'];
        }
        current.isWord = true;
    }
    
    public boolean search(String word) {
        TrieNode current = root;
        return match(word.toCharArray(), 0, current);
    }
    
    public boolean match(char[] arr, int idx, TrieNode current){
        if(idx==arr.length) return current.isWord;
        
        char ch = arr[idx];
        if(ch!='.'){
            return current.child[ch-'a']!=null && match(arr, idx+1, current.child[ch-'a']);
        }else{
            for(int i=0; i<current.child.length; i++){
                if(current.child[i]!=null){
                    if(match(arr, idx+1, current.child[i])){
                        return true;
                    }
                }
            }
        }
        return false;
    }
    
}

```
