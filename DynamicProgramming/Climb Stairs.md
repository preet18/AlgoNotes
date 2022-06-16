[Climb Stairs](https://leetcode.com/problems/climbing-stairs/)


### Using Recursive Approach
``` Java
class Solution {
    //Using Recursive Appraoch O(2^N)
    int noOfPaths=0;
    public int climbStairs(int n) {
        if(n==0) return noOfPaths=0;
        noOfPaths=0;
        climbStairsUtil(n, 0);
        return noOfPaths;
    }
    
    public void climbStairsUtil(int n, int currentStep){
        if(n==currentStep){
            noOfPaths++;
            return;
        }
        if(n<currentStep){
            return;
        }
        climbStairsUtil(n, currentStep+1);
        climbStairsUtil(n, currentStep+2);
    }
}
```

### Using Dynamic Programming
``` Java
//Using Dynamic Programming - O(N)
  public int climbStairs(int n) {
        int[] dp = new int[n+1];
        dp[0]=1;
        dp[1]=1;
        for(int i=2; i<=n; i++){
            dp[i] = dp[i-1]+dp[i-2];
        }
        return dp[n];
    }
```
