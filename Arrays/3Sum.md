### [3Sum](https://leetcode.com/problems/3sum/)
Given an array nums of n integers, are there elements a, b, c in nums such that a + b + c = 0? Find all unique triplets in the array which gives the sum of zero.

Notice that the solution set must not contain duplicate triplets.

##### Example 1:
**Input:** nums = [-1,0,1,2,-1,-4]
**Output:** [[-1,-1,2],[-1,0,1]]

##### Example 2:
**Input:** nums = []
**Output:** []

##### Example 3:
**Input:** [0]
**Output:** []

### Solution
#### Method 1:
Using Nested for loop

**Complexity:** O(N^3)|O(1)

##### Logic:
```
public List<List<Integer>> threeSum(int[] nums) {
        int n = nums.length;
        Set<List<Integer>> res = new HashSet<>();
        for(int i=0; i<n; i++){
            for(int j=i+1; j<n; j++){
                for(int k=j+1; k<n; k++){
                    int sum = nums[i]+nums[j]+nums[k];
                    if(sum==0){
                        List<Integer> lst = Arrays.asList(nums[i], nums[j], nums[k]);
                        Collections.sort(lst);
                        res.add(lst);
                    }
                }
            }
        }
        return new ArrayList<>(res);
    }
```

#### Method 2:
Using Two Pointer Technique

**Complexity:** O(Nlog(N)+N^2)|O(1)

##### Logic:
```
public List<List<Integer>> threeSum(int[] nums){
        Set<List<Integer>> res = new HashSet<>();
        Arrays.sort(nums);
        int n = nums.length;
        for(int i=0; i<n; i++){
            twoPointer(i, nums, res);
        }
        return new ArrayList<>(res);
    }
    
    public void twoPointer(int i, int[] nums, Set<List<Integer>> res){
        int n = nums.length;
        int lo = i+1;
        int hi = n-1;
        
        while(lo<hi){
            int sum = nums[i]+nums[lo]+nums[hi];
            
            if(sum==0){
                res.add(Arrays.asList(nums[i],nums[lo],nums[hi]));
                lo++;
                hi--;
            }else if(sum<0 || (lo>i+1 && nums[lo]==nums[lo-1])){
                lo++;
            }else{ //if(sum>0 || (hi<n-1 && nums[hi]==nums[hi+1]))
                hi--;
            }
        }
    }
```

#### Method 2:
Using HashMap

**Complexity:** O(N^2)|O(N)

##### Logic:
```
public List<List<Integer>> threeSum(int[] nums){
        Set<List<Integer>> res = new HashSet<>();
        Map<Integer, Integer> map = new HashMap<>();
        int n = nums.length;
        for(int i=0; i<n; i++){
            map.put(nums[i], i);
        }
        
        for(int i=0; i<n; i++){
            for(int j=i+1; j<n; j++){
                int diff = -(nums[i]+nums[j]);
                Integer val = map.get(diff);
                if(val!=null && val!=i && val!=j){
                    List<Integer> lst = Arrays.asList(nums[i], nums[j], diff);
                    Collections.sort(lst);
                    res.add(lst);
                }
            }
        }
        
        return new ArrayList<>(res);
    }
```
