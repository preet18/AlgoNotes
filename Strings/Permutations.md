Given an array nums of distinct integers, return all the possible permutations. You can return the answer in any order.

**Example 1:**

```
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

**Example 2:**

```
Input: nums = [0,1]
Output: [[0,1],[1,0]]
```

**Example 3:**
```
Input: nums = [1]
Output: [[1]]
```

## Solution
```
class Solution {
    public List<List<Integer>> permute(int[] nums) {
        Map<Integer, Integer> map = new HashMap<>();
        for(int i=0; i<nums.length; i++){
            if(map.containsKey(nums[i])){
                map.put(nums[i], map.get(nums[i])+1);
            }else{
                map.put(nums[i],1);
            }
        }
        
        int[] str = new int[map.size()];
        int[] count = new int[map.size()];
        
        int id = 0;
        for(Integer key: map.keySet()){
            str[id] = key;
            count[id] = map.get(key);
            id++;
        }
        
        List<Integer> r = new ArrayList<Integer>(Arrays.asList(new Integer[nums.length]));
        
        List<List<Integer>> result = new ArrayList<>();
        
        return permuteUtil(str, count, result, r, 0);
        //return result;
    }
    
    public List<List<Integer>> permuteUtil(int[] str, int[] count, List<List<Integer>> result, List<Integer> r, int level){
        if(level==r.size()){
            result.add(new ArrayList<>(r));
            return result;
        }
        
        for(int i=0; i<str.length; i++){
            if(count[i]==0){
                continue;
            }
            
            r.set(level,str[i]);
            count[i]--;
            result = permuteUtil(str, count, result, r, level+1);
            count[i]++;
        }
        return result;
    }
}
```
