[Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/)

``` Java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int n = nums.length;
        
        if(n<=1){
            return nums;
        }
        
        int[] output = new int[n];
        
        //creating the left product and storing the output array
        output[0] = 1;
        for(int i=1; i<n; i++){
            output[i] = output[i-1]*nums[i-1];
        }
        
        int prod = 1;
        for(int i=n-1; i>=0; i--){
            output[i] = output[i]*prod;
            prod *= nums[i];
        }
        return output;
    }
}
```
