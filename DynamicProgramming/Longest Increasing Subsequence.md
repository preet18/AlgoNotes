
[Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/)

## Appraoch 1 - Using DFS
``` Java
//O(2^N)|O(N) 
    // Every element has 2 options i.e to include or not. 
    //O(N) specifies the recursive stack size
    
    public int lengthOfLIS(int[] nums) {
        if(nums.length==0) return 0;
        return lengthOfLISUtil(nums, 0, Integer.MIN_VALUE);
    }
    
    public int lengthOfLISUtil(int[] nums, int i, int prev){
        if(i>=nums.length) return 0;
        int take = 0;
        int donttake = lengthOfLISUtil(nums, i+1, prev);
        if(nums[i]>prev){
            take = 1+lengthOfLISUtil(nums, i+1, nums[i]);
        }
        return Math.max(take, donttake);
    }

```

## Appraoch 2 - Using Dynamic Programming and Memotization

``` Java
//O(N^2)|O(N)
    public int lengthOfLIS(int[] nums) {
        if(nums.length==0) return 0;
        int[] dp = new int[nums.length];
        Arrays.fill(dp,1);
        int res = 1;
        for(int i=0; i<nums.length; i++){
            for(int j=0; j<i; j++){
                if(nums[i]>nums[j]){
                    dp[i] = Math.max(dp[i], dp[j]+1); 
                    res = Math.max(res, dp[i]);
                }
                    
            }
        }
        return res;
    }
    
```
