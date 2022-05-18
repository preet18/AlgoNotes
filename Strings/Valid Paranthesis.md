[Valid Paranthesis](https://leetcode.com/problems/valid-parentheses/)

``` Java
class Solution {
    //O(N)|O(N)
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<Character>();
        
        for(char ch: s.toCharArray()){
            if(ch=='('||ch=='['||ch=='{'){
                stack.push(ch);
            }else{
                if(stack.isEmpty()) return false;
                char x = stack.pop();
                if(ch==')'){
                    if(x!='(') return false;
                }else if(ch==']'){
                    if(x!='[') return false;
                }else if(ch=='}'){
                    if(x!='{') return false;
                }else{
                return false;
                }
            }
        }
        
        if(!stack.isEmpty()) return false;
        return true;
    }
}
```
