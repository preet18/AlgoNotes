[Palindromic Substrings]()

``` Java
class Solution {
    //O(N^2)|O(1)
    public int countSubstrings(String s) {
        if(s.length()==0||s.length()==1) return s.length();
        int count_of_palindromic_substrings = 1;
        for(int i=1; i<s.length(); i++){
            count_of_palindromic_substrings++;
            count_of_palindromic_substrings += findPalindromicSubstringsCount(s,i-1,i);
            count_of_palindromic_substrings += findPalindromicSubstringsCount(s,i-1,i+1);
        }
        return count_of_palindromic_substrings;
    }
    
    public int findPalindromicSubstringsCount(String s, int l, int r){
        int count = 0;
        while(l>=0 && r<s.length()){
            if(s.charAt(l)!=s.charAt(r)){
                break;
            }
            count++;
            l--;
            r++;
        }
        return count;
    }
}
```
