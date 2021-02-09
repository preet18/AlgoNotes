### [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
Given a string s, find the length of the longest substring without repeating characters.

##### Example 1:
**Input:** s = "abcabcbb"
**Output:** 3

##### Example 2:
**Input:** s = "bbbbb"
**Output:** 1

##### Example 3:
**Input:** s = "pwwkew"
**Output:** 3

### Solution
#### Method 1:
Find all the substrings, check if substring contains unique characters or not.

**Complexity:** O(N^3)|O(1)

#### Method 2:
To scan the string from left to right and keep track of the max. length Non-Repeating Character Substring(NRCS) 

**Complexity:** O(N)|O(1)

##### Logic:
###### USING HASHMAP
```
class Solution {
    public int lengthOfLongestSubstring(String s) {
        Map<Character, Integer> map = new HashMap<Character, Integer>();
        int max=0;
        for(int i=0,j=0; i<s.length(); i++){
            if(map.containsKey(s.charAt(i))){
                j = Math.max(j,map.get(s.charAt(i))+1);
                // We are putting Math.max(j,map.get(s.charAt(i))+1) because in case of abba, if we just give map.get(s.charAt(i))+1, then it will fail.
            }
            map.put(s.charAt(i),i);
            max = Math.max(max, i-j+1);
        }
        return max;
    }
}
```

###### USING HASHTABLE
```
//Hash table to store the char last visited position in the string
int[] arr = new int[26];
for(i=0 to 26)
	arr[i] = -1;

start = 0; //Start index of longest unique substring
st = 0; //start index of current substring
max = 0; //maxLength of substring

for(i=0 to n){
	pos = (int) str.charAt(i)-97;
	if(arr[pos]==-1){
		arr[pos]=i;
	}else{
		if(arr[pos]>=st){ // if char is appearing after the starting index
			if((i-st)>max){ // current substring length is greater then maxlength
				start = st;
				max = (i-st);
			}
			st = arr[pos]+1;
		}
		arr[pos] = i;
	}
}
if((n-st)>max){
	start = st;
	max = (n-st);
}
print(str(start, start+max));
```

