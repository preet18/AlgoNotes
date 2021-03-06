# TECHNIQUES USED TO SOLVE STRING PROBLEMS

Find all the substrings of the string
Odd length substring and even length substring technique
Non-Repeating Character Substring(NRCS)
Find all the permutations of the string
Suffix Trie
ROMAN NUMBERS I - 1 V - 5 X - 10 L - 50 C - 100 D - 500 M - 1000 X-BAR - 5000 M-BAR - 10000


# 🌟️PROBLEMS ON STRING🌟️ 
### 1.[SUBSTRINGS] Find all the substrings of the string 
Eg: 
i/p: abc 
o/p: {'a', 'b', 'c', 'ab', 'bc', 'abc'}

### Solution: 
**M1:** Finding the different length substrings possible in the string - O(N^2)|O(1) (N - length of string) 
#### Logic:: 
	for(len = 1 to N){// different length substrings possible
		for(start=0 to (N-len)){// start index of every substring
			end = start+len-1; //end index of every substring
			print(str.substring(start,end));
		}
	}

### 2.[LONGEST PALINDROMIC SUBSTRING] Find the longest substring which is a palindrome.
Eg:
i/p: abaxyzzyxf
o/p: xyzzyx

### Solution: 
**M1:** Find all the substrings of the string and check whether it is a palindrome or not - O(N^3)|O(1)
	O(N^2) * O(N) - O(N^2) - No of substrings are possible, O(N) - to verify if its a palindrome or not
	
**M2:** Find the odd length and even length palindromes and keep track of the longest palindrome seen so far - O(N^2)|O(1)
#### Logic::
	String result;
	for(id 1 to N){
		odd = getLongestPalindrome(string, id-1, id+1); // {a}b{axyzzyzxf}
		even = getLongestPalindrome(string, id-1, id); // {a}{baxyzzyzxf}
	}

	getLongestPalindrome(string, leftIdx, rightIdx){
		while(leftIdx>=0 && rightIdx < len(string)){
			if(string[leftIdx] ! = string[rightIdx]){
				break;
			}
			leftIdx -=1;
			rightIdx +=1;
		}
		result = string.substring(leftIdx+1, rightIdx);	
	}

### 3.[LONGEST SUBSTRING WITHOUT REPEATING CHARACTERS] Length of the longest substring without repeating characters 
Eg:
i/p: geeksforgeeks
o/p: 7 - (eksforg) or (ksforge)

### Solution: 
**M1:** Find all the substrings, check if substring contains unique characters or not - O(N^3)|O(1)
**M2:** To scan the string from left to right and keep track of the max. length Non-Repeating Character Substring(NRCS) - O(N)|O(1)
#### Logic:
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
	
### 4.[ROMAN NUMBER TO INTEGER] Given a roman number in string format find its numerical value.
Eg:
i/p: VIII , o/p: 8
i/p: L, o/p: 50
i/p: IL, o/p: 49

### Solution:
**M1:** Scan the string from right to left, and add the val to sum if val>=prev, other substract from sum - O(N)|O(1)
#### Logic::
int sum=0; int prev = -1
for(i=(N-1) to 0){
	var = findNumericValue(str.charAt(i));
	if(prev>var){
		sum-=var;
	}else{
		sum+=var;
	}
}


### ROMAN NUMBERS
I - 1
V - 5
X - 10
L - 50
C - 100
D - 500
M - 1000
X-BAR - 5000
M-BAR - 10000

### 5.[IMPLEMENT ATOI] Converting Text to Integer
Eg: 
i/p: 123, o/p:123
i/p: 21a, o/p:-1

**M1:** Typecasting string to Integer, if exception occurs return -1  - O(1)|O(1)
**M2:** Verify the sign based on 1st character, and then typecaste every charcter from 1 to N and add it to the sum - O(N)O(1)

### 6.[PERMUTATIONS] Find all the permutations of the string
Eg: 
i/p: [ABA] 
o/p: [AAB, ABA, BAA]  

### Solution:
**M1:** Mainting the alpha array and their freq array - O(N!)
If there are repeating characters, O(N!/repeatNo!) permutations possible.
If there are non repeating characters, O(N!)

In above example A is repeated 2 times - so permutations possible = (3!/2!) = 6

### Solution:
```
//Forming the count map(TreeMap) 
for(char ch:input){
	if(countMap.containsKey(ch)){
		countMap.put(ch, countMap.get(ch)+1);
	}else{
		countMap.put(ch, 1);
	}
}
//To Store the char of countMap
char[] str = new char[countMap.size()]
//To Store the freq of countMap
int[] count = new int[countMap.size()]

int id = 0;
for(char key: countMap.keySet()){
	str[index] = key;
	count[index] = countMap.get(key);
	id++;
}

char[] result = new char[input.length];
permuteUtil(str, count, result, 0);

permuteUtil(char[] str, int[] count, char[] result, int level){
	//level to indicate the length of the current string.
	if(level==result.length){
		print(result);
		return;
	}

	for(int i=0 to str.length){
		if(count[i]==0){
			continue;
		}
		result[level] = str[i];
		count[i]--;
		permuteUtil(str,count,result,level+1);
		count[i]++;
	}
}
```

### 7.[LONGEST COMMON SUBSTRING] Given two strings, find the common substring present in both the strings.
Eg:
i/p: ABCDGH, ACDGHR
o/p: CDGH
 
### Solution:
**M1:** Find all the substrings of String1 and add them to a list1, and find substrings of String2 now check if they are present in list1. - O(N^2+M^2)|O(N^3)
**M2:** Using Dynamic Programming - O(N*M)|O(N*M)
Logic::


### 8.[RECURSIVELY REMOVE ALL ADJACENT DUPLICATES] Recursively remove all the adjacent duplicates from the given string. 
Eg: 
i/p1: geeksforgeeg 
o/p1: gksfor 
i/p2: mississipie 
o/p1: mipie

### Solution: 
**M1:** Using Iterative Approach - O(N^N)|O(1) 
**M2:** Using the 2 Pointers such that maintaining the prev to hold the last char deleted - O(N)|O(1) 
**M3:** Using Recursive approach - O(N)|O(1) 
#### Logic::
removeUtil(String str, char last_removed){ 
//If string is of length 0 or 1, just return the string 
	if(str.length()==0||str.length()==1){ 
		return str; 
	}

	if(str.charAt(0)==str.charAt(1)){
		last_removed = str.charAt(0);
		while(str.length()>1 && str.charAt(0)==str.charAt(1)){
			str = str.substring(1, str.length());
		}
		str = str.substring(1, str.length());
		return removeUtil(str, last_removed);
	}
	
	String rem_str = removeUtil(str.substring(1, str.length()), last_removed);
	
	//This is for the example like "paap"
	if(rem_str.length()!=0 && rem_str.charAt(0) ==str.charAt(0)){
		last_removed = str.charAt(0);
		return rem_str.substring(1, rem_str.length());
	}
	
	//This condition is for the example like "caacc"
	if(rem_str.length()==0 && last_removed==str.charAt(0)){
		return rem_str;
	}
	return (str.charAt(0)+rem_str);
}

**M4:** Using stack - O(N)|O(N)
#### Logic::
func(String a){
		Stack<Character> st = new Stack<>();
		char prev = a.charAt(0);
		st.push(a.charAt(0));
		
		for(int i=1; i<a.length(); i++){
			if(!st.isEmpty() && a.charAt(i)==st.peek()){
				prev = st.pop();
			}else if(a.charAt(i)==prev){
			}else{
				st.push(a.charAt(i));
				prev = a.charAt(i);
			}
		}
		
		String ans = "";
		while(!st.isEmpty()){
			char temp = st.pop();
			ans += temp;
		}
		System.out.println(new StringBuilder(ans).reverse() + " "); 
	}
}
### 9.[PATTERN MATCHER] Given a pattern of (X,Y), and a string str, need to find the X, Y values from the given string. 
Eg: 
i/p: "XXYXXY", "gogopowerrangergogopowerranger" 
o/p: ["go", "powerranger"];

### Solution: 
M1: Brute Force - Find all the substrings and do the append everything 
M2: Just iterating over the string to find the X and Y based on the given pattern - O(N^2+M)|O(N+M) N - String length, M - Pattern Length
Logic::
String[] patternMatcher(String pattern, String str){
	if(pattern.length()>str.length()){
		return new string[]();
	}
	char[] patternArr = new char[Pattern.length()];
	patternArr = pattern.toCharArray();
	
	//to make sure first letter in the Pattern is X, (And checking if switching is done to make it beginning)
	boolean didSwitch = buildPatternArray(patternArr, pattern);
	
	Map<Character, Integer> count = null;
	int firstPosOfY = findCOuntAndFirstPosOfY(patternArr, count);
	
	//If String is a two words combination
	if(count.get('Y')!=0){
		double lenY;
		double n = Double.valueOf(str.length());
		
		//Checking the different length string words, which satisfies the pattern 
		for(int lenX = 1; lenX <=n; lenX++){
			//Finding the length of Y for the corresponding length of X
			lenY = (n-count.get('X')*lenX)/count.get('Y');
			
			//If the string 2 - is Empty or if is not a integer, then we are not considering the length of String X
			if(lenY==0 || lenY%1!=0){
				continue;
			}
			
			//Finding the starting position of the String2
			int fIdY = lenX * firstPosOfY;
			String X = str.substring(0, lenX);
			String Y = str.substring(fIdY, fIdY + (int)lenY);
			
			//Framing the string based on the pattern from X and Y
			String potentialMatch = buildPotentialMatch(patternArr, X, Y);
			
			//Checking if the framed String matches the  Original String
			if(str.equals(potentialMatch)){
				return didSwitch ? new String[]{Y,X}: new String[]{X, Y};
			}
		}
	}else{
		double lenX = str.length()/count.get('X')'
		if(lenX>=1){
			String X = str.substring(0, (int)lenX);
			
			//Framing the string based on the pattern from X
			String potentialMatch = buildPotentialMatch(X, "");
			
			//Checking if the framed String matches the  Original String
			if(str.equals(potentialMatch()){
				return didSwitch?new String[]{"",X}:new String[]{X,""};
			}
		}
	}	
}

boolean buildPatternArray(char[] patternArr, String pattern){
	//To indicate if pattern is reveresed or not
	boolean rev = false;
	
	if(patternArr[0]=='X'){
		return rev;
	}else{
		for(int i=0; i<patternArr.length(); i++){
			if(patterArr[i]=='X'){
				patternArr[i] = 'Y';
			}else{
				patternArr[i] = 'X';
			}
		}
		rev = true;
		return rev;
	}
	
}

int findCountAndFirstPosOfY(char[] patternArr, Map<Character, Integer>count){
	count.put('X', 0);
	count.put('Y', 0);
	
	int firstPosOfY = -1;
	for(int i=0; i<patternArr.length; i++){
		if(patternArr[i]=='X'){
			count.put('X', count.get('X')+1);
		}else{
			count.put('Y', count.get('Y')+1);
			if(firstPosOfY==-1){
				firstPosOfY = i;
			}
		}
	}
	return firstPosOfY;
}

String buildPotentailMatch(char[] patternArr, String X, String Y){
	StringBuffer res = new StringBuffer("");
	for(char ch : patternArr){
		if(ch=='X')
			res.append(X);
		else
			res.append(Y);
	}
	return res.toString();
}



10.[KNUTH-MORRIS-PRATT ALGORITHM] To check whether the first string contains the second string or not.
Eg:
i/p: aefoaefcdaefcdaed, aefcdaed
o/p: YES

Solution:
M1: Find all the substrings and comparing all those substrings with the second string - O(N^2+N^2*M)|O(N^2*N)
M2: Naive Approach - Comparing every character of the first string with the second string - O(N^2)|O(1)
M3: Using Knuth-Morris-Pratt Algorithm - O(N+M)|O(M) - N - length of str1, M - length of str2
Logic::
	boolean KnuthMorrisPrattAlgorithm(String string, String substring){
		int[] pattern = buildPattern(substring);
		return doesMatch(string, substring, pattern);
	}

	int[] buildPattern(String substring){
		int[] pattern = new pattern[substring.length()];
		Arrays.fill(pattern, -1);
		int j = 0;
		int i = 1;
		while(i<substring.length()){
			if(substring.charAt(i)==substring.charAt(j)){
				pattern[i] = j;
				i++;
				j++;
			}else if(j>0){
				j = pattern[j-1]+1;
			}else{
				i++;
			}
		}
		return pattern;
	}	

	boolean doesMatch(String string, String substring, int[] pattern){
		int i=0;
		int j=0;
		while(i+substring.length()-j <= string.length()){
			if(string.charAt(i)==substring.charAt(j)){
				if(j==substring.length()-1){
					return true;
				}
				i++;
				j++;
			}else if(j>0){
				j = pattern[j-1]+1;
			}else{
				i++;
			}
		}
		return false;
	}


11.[CONSTRUCTION OF A SUFFIX TRIE]
[SUFFIX TRIE] Trie Data Structure, which stores all the suffixes of the given string
Eg: 
i/p: "babc"
o/p: {"babc", "abc", "bc", "c"}

Solution:
M1: Find all the suffixes and frame the suffix trie - O(N^2)|O(N^2)
static class TrieNode{
	HashMap<Character, TrieNode> children = new HashMap<Character, TrieNode>();
}

static class suffixTrie{
	TrieNode root = TrieNode();
	char endSymbol = '*';
	
	public suffixTrie(String str){
		populateSuffixTrie(str);
	}
	
	public void populateSuffixTrieFrom(String str){
		for(int i=0; i<str.length(); i++){
			insertSubstringStartingAt(i, str);
		}
	}
}

public void insertSubstringStartingAt(int start, String str){
	TrieNode node = root;
	for(int i=start; i<str.length(); i++){
		char ch = str.charAt(i);
		if(!node.children.containsKey(ch)){
			node.children.put(ch, new TrieNode());
		}
		node = node.children.get(ch);
	}
	node.children.put(endSymbol, null);
}

12.[FINDING A STRING IN A SUFFIX TRIE]
Eg:
i/p: "pumpkin", "pump"
o/p: yes


Solution:
M1: O(M)|O(1) - M length of the string that need to searched 
public boolean contains(String str){
	TrieNode node = root;
	for(int i=0; i<str.length(); i++){
		char ch = str.charAt(i);
		if(!node.children.containsKey(ch)){
			return false;
		}
		node  = node.children.get(ch);
	}
	return node.children.containsKey(endSymbol)?true:false;
}

13.[MULTI STRING MATCH]Given a big string and list of strings, find the smaller strings of list which are present in the bigger string.
Eg:
i/p: str = "this is a big string", list = [this, yo, is, a, bigger, string, kappa]
o/p: [T, F, T, T, F, T, F]

Solution:
M1: Take each string of the list and iterate over the bigger string - O(b*n*s)|O(n)
	b - length of big string, n - no of elements in the list, s - length of the largest string in list.
M2: Forming the suffix Trie of the big string and searching list of strings in the suffix trie - O(b^2+n*s)|O(b^2+n)
M3: Framing the trie of strings in the list and then iterating over the trie for every suffix of the bigger string - O(n*s+b*s)|O(n*s+n)



14.[GENERATE PARENTHESIS] Given n parenthesis, write a function to generate all combinations of well-formed parenthesis.
Eg: 
i/p: N=3
o/p: [((())), (()()), (())(), ()(()), ()()()]

Solution:
M1: Just comparing the available no of parenthesis with the possible no of parenthesis while inserting - O(N*cat(N))
List<String> generateParenthesis(int n){
	if(n>0){
		List<String> list = new ArrayList<String>();
		char[] str = new char[2*n];
		int pos = 0, open = 0, close = 0;
		createParenthesis(list, str, n, pos, open, close);
	}
	return null;
}

createParenthesis(List<String> list, char[] str, int n, int pos, int open, int close){
	if(close==n){
		list.add(new String(str));
		return;
	}
	if(open<n){
		str[pos]='(';
		createParenthesis(list, str, n, pos+1, open+1, close);
	}
	if(open>close){
		str[pos]=')';
		createParenthesis(list, str, n, pos+1, open, close+1);
	}
}

15.[GROUP ANAGRAMS] 
Eg:
i/p: [eat, team tan, ate, nat, bat]
o/p: [ [ate, eat, tea], [nat, tan], [bat]]

Solution:
M1: Using HashMap group all the anagrams, i.e by storing hash as a key in map and string as value corresponding to the hashvalue. - O(N*S^2)|O(N*S)
N - Length of the list, S - Length of biggest String

List<List<String>> groupAnagrams(String[] strs){
	List<List<String>> res = new ArrayList<>();
	Map<String, List<String>> map = new HashMap<>();
	
	for(String str: strs){
		//Generating the hash for the string
		String orderKey = getSortedKey(str);
		if(map.containsKey(orderKey)){
			map.get(orderKey).add(str);
		}else{
			List<String> list = new ArrayList<>();
			list.add(str);
			map.put(orderKey, list);
		}
	}
	res.addALL(map.values());
	return res;
}

getSortedKey(String str){
	char[] arr = new char[26];
	for(i=0; i<str.length(); i++){
		arr[str.charAt(i)-'a']++;
	}
	return new String(arr);
}

16.[LETTER COMBINATIONS OF THE PHONE NUMBER]
Eg:
i/p: 23
o/p: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"]

Solution:
M1: Just form the map with a possible characters for different numbers and use recursive approach to find the combinations possible 
List<String> letterCombinations(String digits){
	if(digits.length()<0){
		int n = digits.length();
		char[] str = new char[n];
		List<String> list = new ArrayList<String>();
		int pos = 0;
		Map<Character, List<Character>> map = formMap();
		formString(list, str, n, pos, map, digits);
		return list;
	}
	return Arrays.asList();
}

public Map<Character, List<Character>> formMap(){
	Map<Character, List<Character>> map = new HashMap<>();
	map.put('2', Arrays.asList('a','b','c'));
	map.put('3', Arrays.asList('d','e','f'));
	"
	"
	"
	"
	"
	
	return map;
}

formString(List<String> list, char[] str, int n, int pos, Map<Character, List<Character>> map, String digits){
	if(pos==n){
		list.add(new String(str));
		return;
	}
	
	List<Character> alphaList = map.get(digits.charAt(pos));
	for(Character ch : alphaList){
		str[pos] = ch;
		formString(list, str, n, pos, map, digits);
	}
}
