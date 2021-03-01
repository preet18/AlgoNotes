### [Longest Palindrome By Shuffling and Deleting](https://www.geeksforgeeks.org/find-longest-palindrome-formed-by-removing-or-shuffling-chars-from-string/)
Given a string, find the longest palindrome that can be constructed by removing or shuffling characters from the string. Return only one palindrome if there are multiple palindrome strings of longest length.

##### Example 1:
**Input:** abc
**Output:** a OR b OR c

##### Example 2:
**Input:** aabbcc
**Output:** abccba OR baccab OR cbaabc OR
any other palindromic string of length 6.

##### Example 3:
**Input:** abbaccd
**Output:** abcdcba OR ...

##### Example 4:
**Input:** aba
**Output:** aba

### Solution
#### Method 1:
We can divide any palindromic string into three parts – beg, mid and end. For palindromic string of odd length say 2n + 1, ‘beg’ consists of first n characters of the string, ‘mid’ will consist of only 1 character i.e. (n + 1)th character and ‘end’ will consists of last n characters of the palindromic string. For palindromic string of even length 2n, ‘mid’ will always be empty. It should be noted that ‘end’ will be reverse of ‘beg’ in order for string to be palindrome.

The idea is to use above observation in our solution. As shuffling of characters is allowed, order of characters doesn’t matter in the input string. We first get frequency of each character in the input string. Then all characters having even occurrence (say 2n) in the input string will be part of the output string as we can easily place n characters in ‘beg’ string and the other n characters in the ‘end’ string (by preserving the palindromic order). For characters having odd occurrence (say 2n + 1), we fill ‘mid’ with one of all such characters. and remaining 2n characters are divided in halves and added at beginning and end.

**Complexity:** O(N)|O(N)

##### Logic:
###### USING HASHMAP
```
public class Solution {

	//O(N)|O(N)
	public static void main(String args[]) {
		Scanner sc = new Scanner(System.in);
		String str = sc.next();
		Map<Character, Integer> freqMap = new HashMap<>();
		for(char ch:str.toCharArray()) {
			freqMap.put(ch, freqMap.getOrDefault(ch,0)+1);
		}
		System.out.println(findLongestPalindrome(freqMap));
	}

	private static String findLongestPalindrome(Map<Character, Integer> freqMap) {
		StringBuilder beg = new StringBuilder();
		String mid = "";
		for(Character key:freqMap.keySet()) {
			if(freqMap.get(key)%2!=0) {
				mid = key.toString();
			}
			for(int i=0; i<freqMap.get(key)/2; i++) {
				beg.append(key);
			}
		}
		return beg.toString()+mid+beg.reverse().toString();
	}
}

```

