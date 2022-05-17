  [Group Anagrams](https://leetcode.com/problems/group-anagrams/)
  
  
  ``` Java
  class Solution {
    
    //O(strs.length * (length of str)) = O(K*N) | O(26)
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> map = new HashMap<>();
        
        for(String str:strs){
            char[] ch = str.toCharArray();
            char[] alpha = new char[26];
            for(char c: ch) alpha[c-'a']++;
            String keyStr = String.valueOf(alpha);
            List<String> temp = map.getOrDefault(keyStr, new ArrayList<String>());
            temp.add(str);
            map.put(keyStr, temp);
        }
        
        return new ArrayList<>(map.values());
    }
}
```
