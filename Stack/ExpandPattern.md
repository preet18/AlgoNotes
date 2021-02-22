Alphabets are inside () and the number -9<=0>=9 which is under{} solve the string according to the sample input output  

**Input** (z){-2}oho

**Output** ZZoho

**Input** ((X){2}(y){3}(z)){2}

**Output** xxyyyzxxyyyz

```
import java.util.*;
import java.io.*;

public class HelloWorld{

     public static void main(String []args){
        //System.out.println("Hello World");
        Scanner sc = new Scanner(System.in);
        String input = sc.nextLine();
        String output = expandInput(input);
        System.out.println(output);
     }
     
     
     public static String expandInput(String input){
         Stack<String> stack = new Stack<>();
         for(int i=0; i<input.length(); i++){
             System.out.println(" i : " + input.charAt(i));
             if(input.charAt(i)==')'){
                 String x = retrieveString(stack);
                 System.out.println(x);
                 stack.push(x);
                 if(input.charAt(i)=='{'){
                     i = findNumber(input, i+1, x, stack);
                 }
             }else{
                 //System.out.println(input.substring(i,i+1));
                 stack.push(input.substring(i,i+1));
             }
         }
         return stack.pop();
     }
     
     
     public static String retrieveString(Stack<String> stack){
         StringBuilder sb = new StringBuilder("");
         while(!stack.peek().equals("(")){
             //System.out.println("----------00-------"+stack.peek());
             sb.append(stack.pop());
         }
         //System.out.println(sb.toString());
         stack.pop();
         sb.reverse();
         return sb.toString();
     }
     
     public static int findNumber(String input, int i, String x, Stack<String> stack){
         StringBuilder num = new StringBuilder("");
         while(input.charAt(i)!='}'){
             num.append(input.charAt(i));
             i++;
         }
         int val = Math.abs(Integer.parseInt(num.toString()));
         System.out.println(val);
         StringBuilder sb = new StringBuilder("");
         String ip = stack.pop();
         while(val-->0){
             sb.append(ip);
             val--;
         }
         System.out.println("------"+sb.toString());
         stack.push(sb.toString());
         return i;
     }
}
```
