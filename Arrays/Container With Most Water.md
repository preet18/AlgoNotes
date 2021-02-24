### [Container with Most Water](https://www.geeksforgeeks.org/container-with-most-water/)
[Leetcode URL](https://leetcode.com/problems/container-with-most-water/)
Given n non-negative integers a1, a2, ..., an , where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of the line i is at (i, ai) and (i, 0). Find two lines, which, together with the x-axis forms a container, such that the container contains the most water.

Notice that you may not slant the container.

##### Example 1:
**Input:** height = [1,8,6,2,5,4,8,3,7]
**Output:** 49
**Explanation:** The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.

##### Example 2:
**Input:** height = [1,1]
**Output:** 1

##### Example 3:
**Input:** height = [4,3,2,1,4]
**Output:** 16

##### Example 4:
**Input:** height = [1,2,1]
**Output:** 2

### Solution
#### Method 1:
Using Nested For Loop

**Complexity:** O(N^2)|O(1)

#### Logic:
```
public int maxArea(int[] height) {
    int max = 0;
    int n = height.length;
    for(int i=0; i<n; i++){
        for(int j=i+1; j<n; j++){
            max = Math.max(max, Math.min(height[i],height[j])*(j-i));
        }
    }
    return max;
}
```

#### Method 2:
Using Two Pointer Technique(Without Sorting)

**Complexity:** O(N)|O(1)

##### Logic:
```
class Solution {
    public int maxArea(int[] height){
        int max = 0;
        int n = height.length;
        int i = 0;
        int j = n-1;
        while(i<j){
            max = Math.max(max, Math.min(height[i],height[j])*(j-i));
            if(height[i]>height[j]){
                j--;
            }else{
                i++;
            }
        }
        return max;
    }
}
```
