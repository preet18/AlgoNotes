[Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/)


**BRUTE FORCE**
``` Java
//O(N2)|O(1)
  public int maxProduct(int[] nums) {
        int max_so_far = nums[0];
        for(int i=0; i<nums.length; i++){
            int max_ending_here = nums[i];
            max_so_far = Math.max(max_so_far, max_ending_here);
            for(int j=i+1; j<nums.length; j++){
                max_ending_here = max_ending_here*nums[j];
                max_so_far = Math.max(max_so_far, max_ending_here);
            }
        }
        return max_so_far;
    }
```

**OPTIMISED APPROACH**
``` Java
//O(N)|O(1)
    public int maxProduct(int[] nums) {
        int res = nums[0];
        int max = nums[0];
        int min = nums[0];
        
        for(int i=1; i<nums.length; i++){
            if(nums[i]<0){
                int temp = max;
                max = min;
                min = temp;
            }
            
            max = Math.max(nums[i], nums[i]*max);
            min = Math.min(nums[i], nums[i]*min);
            
            res = Math.max(res, max);
        }
        
        return res;
    }
```
