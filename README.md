# AlgoNotes
DataStructures and Algorithm Notes

https://leetcode.com/discuss/general-discussion/460599/blind-75-leetcode-questions

https://leetcode.com/discuss/general-discussion/419062/list-of-leetcode-question-to-cover-all-the-concepts-and-type-of-questions

TECHNIQUES USED TO SOLVE ARRAY PROBLEMS
1. Iterating over the array
2. Sorting the array
3. Two Pointer Technique over the sorted array
4. Hashing 


🌟️PROBLEMS ON ARRAY🌟️
1. [TWO NUMBER SUM]Given an array of integers and a targetsum, return an array of 2 numbers from this given array whose sum results in targetsum
Eg: 
i/p: Array - [3, 5, -4, 8, 11, 1, -1, 6], TargetSum - 10
o/p: [-1, 11]
  
Solution:
M1: Using nested for Loop - O(N^2)|O(1)
M2: Sorting the Array + Using Two Pointers Approach - O(NlogN)|O(1)
M3: Using Hash Table - O(N)|O(N)

2.[THREE NUMBER SUM] Given an array, find all possible triplets whose sum results in targetsum
Eg:
i/p: Array - [12, 3, 1, 2, -6, 5, -8, 6], TargetSum - 0
o/p: [[-8,2,6],[-8,3,5],[-6,1,5]]

Solution:
M1: Using 3 nested for loops - O(N^3)|O(1)
M2: Sorting the Array + Using Two Pointers Approach(i.e by fixing an element in array) - O(N^2+NlogN)|O(1)
M3: Using HashTable - O(N^2)|O(N)

3.[SEARCH IN SORTED MATRIX] Given a 2D matrix, where every row and column is sorted.Given a target number return the position of it.N rows and M columns
Eg:
i/p: [
	[1,  4,   7,   12,  15,  1000],
	[2,  5,   19,  31,  32,  1001],
	[3,  8,   24,  33,  35,  1002],
	[40, 41,  42,  44,  45,  1003],
	[99, 100, 103, 106, 128, 1004]
     ], 44
o/p: [3, 3]

Solution:
M1: Iterating over the complete Matrix - O(N*M)|O(1)
M2: Taking the advantage of sorted Matrix - O(N+M)|O(1)
Logic::
	row = 0;
	col = len(matrix[0])-1;
	while(row<len(matrix) and col >=0){
		if(matrix[row][col]>target){
			col-=1;
		}else if(matrix[row][col]<target){
			row+=1;
		}else{
			int[] res = new int[2];
			res[0] = row;
			res[1] = col;
			return res;
		}
	} 
	int[] res = new int[2];
	res[0] = -1;
	res[1] = -1;
	return res;

4.[SHIFTED BINARY SEARCH] Given a shifted sorted array, need tof find if target is present in the array.
[1, 2, 3, 4]- sorted array and its shifted form is - shifted array is - [3, 4, 2, 1]
Eg: 
i/p: [45, 61, 71, 72, 73, 0, 1, 21, 33, 45], target = 33
o/p: 8

Solution:
M1: Linear Search O(N)|O(1)
M2: Using the sorted array for our advantage - O(log(N))|O(1)
Logic::	
	L = 0;
	R = N-1;
	while(L<=R){
		M = (L+R)/2;
		if(arr[M] == target){
			return M;
		}else if(arr[L]<=arr[M]){ //(i.e numbers between L & M are in sorted order)
			if(target>=arr[L] && target<arr[M]){
				R = M-1; //explore left
			}else{
				L = M+1; //explore right
			}
		}else{ //if(arr[M]<=arr[R]) (i.e numbers between M & R are in sorted order)
			if(target<=arr[R] && target > arr[M]){
				L = M+1; //explore right;
			}else{
				R = M-1; //explore left;
			}
		}		  
	}


TECHNIQUES USED TO SOLVE STRING PROBLEMS
1. Find all the substrings of the string
2. Odd length substring and even length substring technique
3. Non-Repeating Character Substring(NRCS)
4. Find all the permutations of the string

ROMAN NUMBERS
I - 1
V - 5
X - 10
L - 50
C - 100
D - 500
M - 1000
X-BAR - 5000
M-BAR - 10000

🌟️PROBLEMS ON STRING🌟️
1.[SUBSTRINGS] Find all the substrings of the string
Eg:
i/p: abc
o/p: {'a', 'b', 'c', 'ab', 'bc', 'abc'}

Solution: 
M1: Finding the different length substrings possible in the string - O(N^2)|O(1)
(N - length of string)
Logic:: 
	for(len = 1 to N){// different length substrings possible
		for(start=0 to (N-len)){// start index of every substring
			end = start+len-1; //end index of every substring
			print(str.substring(start,end));
		}
	}

2.[LONGEST PALINDROMIC SUBSTRING] Find the longest substring which is a palindrome.
Eg:
i/p: abaxyzzyxf
o/p: xyzzyx

Solution:
M1: Find all the substrings of the string and check whether it is a palindrome or not - O(N^3)|O(1)
	O(N^2) * O(N) - O(N^2) - No of substrings are possible, O(N) - to verify if its a palindrome or not
M2: Find the odd length and even length palindromes and keep track of the longest palindrome seen so far - O(N^2)|O(1)
Logic::
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


3.[LONGEST SUBSTRING WITHOUT REPEATING CHARACTERS] Length of the longest substring without repeating characters 
Eg:
i/p: geeksforgeeks
o/p: 7 - (eksforg) or (ksforge)

Solution:
M1: Find all the substrings, check if substring contains unique characters or not - O(N^3)|O(1)
M2: To scan the string from left to right and keep track of the max. length Non-Repeating Character Substring(NRCS) - O(N)|O(1)
Logic:
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

4.[ROMAN NUMBER TO INTEGER] Given a roman number in string format find its numerical value.
Eg:
i/p: VIII , o/p: 8
i/p: L, o/p: 50
i/p: IL, o/p: 49

Solution:
M1 : Scan the string from right to left, and add the val to sum if val>=prev, other substract from sum - O(N)|O(1)
Logic::
int sum=0; int prev = -1
for(i=(N-1) to 0){
	var = findNumericValue(str.charAt(i));
	if(prev>var){
		sum-=var;
	}else{
		sum+=var;
	}
}


ROMAN NUMBERS
I - 1
V - 5
X - 10
L - 50
C - 100
D - 500
M - 1000
X-BAR - 5000
M-BAR - 10000

5.[IMPLEMENT ATOI] Converting Text to Integer
Eg: 
i/p: 123, o/p:123
i/p: 21a, o/p:-1

M1:Typecasting string to Integer, if exception occurs return -1  - O(1)|O(1)
M2:Verify the sign based on 1st character, and then typecaste every charcter from 1 to N and add it to the sum - O(N)O(1)

6.[PERMUTATIONS] Find all the permutations of the string
Eg: 
i/p: [ABA] 
o/p: [AAB, ABA, BAA]  

Solution:
M1: Mainting the alpha array and their freq array - O(N!)
If there are repeating characters, O(N!/repeatNo!) permutations possible.
If there are non repeating characters, O(N!)

In above example A is repeated 2 times - so permutations possible = (3!/2!) = 6

Solution:
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

7.[LONGEST COMMON SUBSTRING] Given two strings, find the common substring present in both the strings.
Eg:
i/p: ABCDGH, ACDGHR
o/p: CDGH
 
Solution:
M1: Find all the substrings of String1 and add them to a list1, and find substrings of String2 now check if they are present in list1. - O(N^2+M^2)|O(N^3)
M2: Using Dynamic Programming - O(N*M)|O(N*M)
Logic::



8.[RECURSIVELY REMOVE ALL ADJACENT DUPLICATES] Recursively remove all the adjacent duplicates from the given string.
Eg:
i/p1: geeksforgeeg 
o/p1: gksfor
i/p2: mississipie
o/p1: mipie


Solution:
M1: Using Iterative Approach - O(N^N)|O(1)
M2: Using the 2 Pointers such that maintaining the prev to hold the last char deleted - O(N)|O(1)
M3: Using Recursive approach - O(N)|O(1)
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

M4: Using stack - O(N)|O(N)
	
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
	
	
9.[PATTERN MATCHER] Given a pattern of (X,Y), and a string str, need to find the X, Y values from the given string.
Eg:
i/p: "XXYXXY", "gogopowerrangergogopowerranger"
o/p: ["go", "powerranger"];

Solution:
M1: Brute Force - Find all the substrings and do the append everything 
M2: Just iterating over the string to find the X and Y based on the given pattern - O(N^2+M)|O(N+M)
	N - String length, M - Pattern Length

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
