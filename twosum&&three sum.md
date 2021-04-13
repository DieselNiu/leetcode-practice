Two sums



solution 1:

两次遍历的基本功

```
    class Solution{
          public int[] twoSum(int[] nums, int target){
              for(int i = 0;i < nums.length-1;i++){
                  for(int j = i+1; j< nums.length;j++){
                      if(nums[j] == target - nums[i]){
                          return new int[] {i,j};
                      }
                  }
              }
              return null;
          }
      }
```

solution 2
先把他们全部放进hashmap中,在做一次循环 两次哈希
```
   class Solution {
        public int[] twoSum(int[] nums, int target) {
            Map<Integer, Integer> map = new HashMap<>();
            for (int i = 0; i < nums.length; i++) {
                map.put(nums[i], i);
            }

            for (int j = 0; j < nums.length; j++) {
                int other = target - nums[j];
                //如果他存在且不是nums[i]本身
                if (map.containsKey(other) && map.get(other) != j) {
                    return new int[]{j, map.get(other)};
                }
            }
            return new int[]{-1, -1};

        }
    }
```

Solution 3

一次哈希
```
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer,Integer > map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            if(map.containsKey(target-nums[i])){
                return new int[] {i, map.get(target-nums[i])};
            } else {
                map.put(nums[i],i);
            }
        }
        return null;
    }
}
```


Three sum


Solution 1

暴力求解,三重循环这时会包含重复的三元组

```
 class Solution {
        public List<List<Integer>> threeSum(int[] nums) {
            List<List<Integer>> results = new ArrayList<>();
            for (int i = 0; i < nums.length - 2; i++) {
                for (int j = i + 1; j < nums.length - 1; j++) {
                    for (int k = j + 1; k < nums.length; k++) {
                        if (nums[i] + nums[j] + nums[k] == 0) {
                            results.add(Arrays.asList(nums[i],nums[j],nums[k]));
                        }
                    }

                }

            }
            return results;

        }
    }
```
   

Solution 2 
hashmap来记录,a,b,a+b=-c


Solution 3
排序+双指针