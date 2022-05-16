[Valid Anagram](https://leetcode.com/problems/valid-anagram/)

``` Java
class Solution {
    //O(S+T)|O(26)
    public boolean isAnagram(String s, String t) {
        if(s.length()==0 && t.length()==0){
            return true;
        }
        int[] alpha = new int[26];
        for(char ch: s.toCharArray()){
            alpha[ch-'a']++;
        }
        
        for(char ch: t.toCharArray()){
            alpha[ch-'a']--;
        }
        
       for(int x :alpha){
            if(x!=0){
                return false;
            }
        }
        return true;
    }
}
```
