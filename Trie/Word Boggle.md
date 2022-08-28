### PROBLEM 
[Word Boggle](https://www.geeksforgeeks.org/boggle-find-possible-words-board-characters/)

### Solution
``` Java
/*package whatever //do not write package name here */

import java.util.*;
import java.lang.*;
import java.io.*;

class GFG {
    
    static class Trie{
        Trie[] alpha;
        boolean end;
        Trie(){
            alpha = new Trie[256];
            end = false;
        }
    }
    
    public static void wordBoggle(Trie root, char[][] mat, int n, int m){
        boolean[][] visited;
        ArrayList<String> list = new ArrayList<String>();
        for(int i=0; i<n; i++){
            for(int j=0; j<m; j++){
                
                Trie node = root;
                visited = new boolean[n][m];
                
                char ch = mat[i][j];
                int pos = ch-'A';
                String str = String.valueOf(ch);
                if(node.alpha[pos]!=null){
                    wordBoggleUtil(node.alpha[pos], mat, i, j, n, m, visited, list, str);
                }
            }
        }
        if(list.size()>0){
            printSolution(list);
        }else{
            System.out.println("-1");
        }
    }
    
    public static void printSolution(ArrayList<String> list){
        Collections.sort(list);
        for(int i=0; i<list.size(); i++){
            System.out.print(list.get(i) + " ");
        }    
        System.out.println();
    }
    
    public static boolean isSafe(Trie node, char[][] mat, int row, int col, int n, int m, boolean[][] visited){
        /*char ch = mat[row][col];
        int pos = ch - 'A';
        */
        if(row==-1 || row==n || col==-1 || col==m || visited[row][col] || node.alpha[mat[row][col]-'A']==null){
            return false;
        }
        return true;
    }
    
    public static void wordBoggleUtil(Trie node, char[][] mat, int row, int col, int n, int m, boolean[][] visited, ArrayList<String> list, String str){
        if(node.end==true && !list.contains(str)){
            list.add(str);
        }
        
        visited[row][col] = true;
        if(isSafe(node, mat, row+1, col, n, m, visited)){
            char ch = mat[row+1][col];
            int pos = ch - 'A';
            wordBoggleUtil(node.alpha[pos], mat, row+1, col, n, m, visited, list, str+String.valueOf(ch));
        }
        
        if(isSafe(node, mat, row-1, col, n, m, visited)){
            char ch = mat[row-1][col];
            int pos = ch - 'A';
            wordBoggleUtil(node.alpha[pos], mat, row-1, col, n, m, visited, list, str+String.valueOf(ch));
        }
        
        if(isSafe(node, mat, row, col+1, n, m, visited)){
            char ch = mat[row][col+1];
            int pos = ch - 'A';
            wordBoggleUtil(node.alpha[pos], mat, row, col+1, n, m, visited, list, str+String.valueOf(ch));
        }
        
        if(isSafe(node, mat, row, col-1, n, m, visited)){
            char ch = mat[row][col-1];
            int pos = ch - 'A';
            wordBoggleUtil(node.alpha[pos], mat, row, col-1, n, m, visited, list, str+String.valueOf(ch));
        }
        
        if(isSafe(node, mat, row+1, col+1, n, m, visited)){
            char ch = mat[row+1][col+1];
            int pos = ch - 'A';
            wordBoggleUtil(node.alpha[pos], mat, row+1, col+1, n, m, visited, list, str+String.valueOf(ch));
        }
        
        if(isSafe(node, mat, row+1, col-1, n, m, visited)){
            char ch = mat[row+1][col-1];
            int pos = ch - 'A';
            wordBoggleUtil(node.alpha[pos], mat, row+1, col-1, n, m, visited, list, str+String.valueOf(ch));
        }
        
        if(isSafe(node, mat, row-1, col+1, n, m, visited)){
            char ch = mat[row-1][col+1];
            int pos = ch - 'A';
            wordBoggleUtil(node.alpha[pos], mat, row-1, col+1, n, m, visited, list, str+String.valueOf(ch));
        }
        
        if(isSafe(node, mat, row-1, col-1, n, m, visited)){
            char ch = mat[row-1][col-1];
            int pos = ch - 'A';
            wordBoggleUtil(node.alpha[pos], mat, row-1, col-1, n, m, visited, list, str+String.valueOf(ch));
        }
        
        visited[row][col] = false;
        return;
    }
    
    public static void insertWords(Trie root, String[] strs, int x){
        
        for(int i=0; i<x; i++){
            insertWordUtil(root, strs[i]);
        }
            
    }
    
    public static void insertWordUtil(Trie root, String str){
        Trie node = root;
        
        for(int i=0; i<str.length(); i++){
            char ch = str.charAt(i);
            int pos = (int)ch-'A';
            //System.out.println("Pos " + pos);
            if(node.alpha[pos]==null){
                node.alpha[pos] = new Trie();
            }
            node = node.alpha[pos];
        }
        
        node.end = true;
    }
    
	public static void main (String[] args) {
		Scanner sc = new Scanner(System.in);
		int t = sc.nextInt();
		while(t-->0){
		    int x = sc.nextInt();
		    String[] strs = new String[x];
		    for(int i=0; i<x; i++){
		        strs[i] = sc.next();
		    }
		    
		    int n = sc.nextInt();
		    int m = sc.nextInt();
		    char[][] mat = new char[n][m];
		    for(int i=0; i<n; i++){
		        for(int j=0; j<m; j++){
		            mat[i][j] = sc.next().charAt(0);
		        }
		    }
		    
		    
		    Trie root = new Trie();
		    insertWords(root, strs, x);
		    
		    wordBoggle(root, mat, n, m);
		}
	}
}
```
