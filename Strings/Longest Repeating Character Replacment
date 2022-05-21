[Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/)

``` Java

class Solution {
    //O(N)|O(26)
    public int characterReplacement(String s, int k) {
        int window_start = 0;
        int max_count = 0;
        int max_length = 0;
        int[] char_count = new int[26];
        
        for(int window_end=0; window_end<s.length(); window_end++){
            char_count[s.charAt(window_end)-'A']++;
            //max_count = Math.max(max_count, char_count[s.charAt(window_end)-'A']);
            max_count = findMax(char_count);
            while(window_end-window_start+1-max_count>k){
                char_count[s.charAt(window_start)-'A']--;
                window_start++;
            }
            
            max_length = Math.max(max_length, window_end-window_start+1);
        }
        return max_length;
    }
    
    public int findMax(int[] char_count){
        int max = 0;
        for(int e:char_count){
            max = Math.max(max,e);
        }
        return max;
    }
}
```
