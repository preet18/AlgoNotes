### [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)
You are given an integer array nums sorted in ascending order (with distinct values), and an integer target.
Suppose that nums is rotated at some pivot unknown to you beforehand (i.e., [0,1,2,4,5,6,7] might become [4,5,6,7,0,1,2]).
If target is found in the array return its index, otherwise, return -1.

##### Example 1:
**Input:** nums = [4,5,6,7,0,1,2], target = 0
**Output:** 4

##### Example 2:
**Input:** nums = [4,5,6,7,0,1,2], target = 3
**Output:** -1

##### Example 3:
**Input:** nums = [1], target = 0
**Output:** -1

### Solution
#### Method 1:
Using linear search

**Complexity:** O(N)|O(1)

#### Method 2:
Using Binary Search

**Complexity:** O(log(N))|O(1)

##### Logic:
```
public int search(int[] arr, int target) {
        int lo = 0;
        int hi = arr.length-1;
        
        while(lo<=hi){
            int mid = (lo+hi)/2;
            
            if(target==arr[mid]){
                return mid;
            }
            if(arr[lo]<=arr[mid]){
                if(arr[lo]<=target && arr[mid]>target){
                    hi = mid-1;
                }else{
                    lo = mid+1;
                }
            }else if(arr[mid]<arr[hi]){
                if(arr[mid]<target && arr[hi]>=target){
                    lo = mid+1;
                }else{
                    hi = mid-1;
                }
            }
        }
        return -1;
    }
```

