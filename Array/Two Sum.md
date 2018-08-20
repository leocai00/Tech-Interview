# Two Sum

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

Example:

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```
## Solution

```java
#Brute Force
class Solution {
  public int[] twoSum(int[] nums, int target) {
      for (int i = 0; i < nums.length; i++) {
          for (int j = i + 1; j < nums.length; j++) {
              if (nums[j] == target - nums[i]) {
                  return new int[] { i, j };
              }
          }
      }
      throw new IllegalArgumentException("No two sum solution");
  }
}

# HashMap
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();
        for(int i = 0; i < nums.length; i++) {
            map.put(nums[i], i);
        }
        for(int i = 0; i < nums.length; i++) {
            int temp = target - nums[i];
            if(map.containsKey(temp) && map.get(temp) != i) {
                return new int[] {i, map.get(temp)};
            }
        }
        throw new IllegalArgumentException("no two sum solution");
    }
}
```
