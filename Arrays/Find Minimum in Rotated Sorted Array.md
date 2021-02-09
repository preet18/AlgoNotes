### [Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)
Suppose an array of length n sorted in ascending order is rotated between 1 and n times. For example, the array nums = [0,1,2,4,5,6,7] might become:

[4,5,6,7,0,1,2] if it was rotated 4 times.
[0,1,2,4,5,6,7] if it was rotated 7 times.
Notice that rotating an array [a[0], a[1], a[2], ..., a[n-1]] 1 time results in the array [a[n-1], a[0], a[1], a[2], ..., a[n-2]].

Given the sorted rotated array nums, return the minimum element of this array.

##### Example 1:
**Input:** nums = [3,4,5,1,2]
**Output:** 1

##### Example 2:
**Input:** nums = [4,5,6,7,0,1,2]
**Output:** 0

##### Example 3:
**Input:** [11,13,15,17]
**Output:** 11

### Solution
#### Method 1:
Using linear search

**Complexity:** O(N)|O(1)

#### Method 2:
Using Binary Search

**Complexity:** O(log(N))|O(1)

##### Logic:
```
class Solution {
    public int findMin(int[] nums) {
        int min = Integer.MAX_VALUE;
        int lo = 0;
        int hi = nums.length - 1;
        while(lo<=hi){
            int mid = (lo+hi)/2;
            if(nums[lo]<=nums[mid]){
                min = Math.min(min, nums[lo]);
                lo = mid+1;
            }else{//if(nums[mid]<=nums[hi])
                min = Math.min(nums[mid], min);
                hi = mid-1;
            }
        }
        return min;
    }
}
```
