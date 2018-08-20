Move Zeroes

Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

Example:
```
Input: [0,1,0,3,12]
Output: [1,3,12,0,0]
```
Note:
* You must do this in-place without making a copy of the array.
* Minimize the total number of operations.

```java
class Solution {
    public void moveZeroes(int[] nums) {
        if(nums.length >= 0) {
            int zero = 0;
            int count = 0;
            for(int i = 0; i < nums.length; i++) {
                if(nums[i] == 0) {
                    zero++;
                } else {
                    nums[count] = nums[i];
                    count++;
                }    
            }
            for(int j = 0; j < zero; j++) {
                nums[nums.length - 1 - j] = 0;
            }
        }
    }
}

public void moveZeroes(int[] nums) {
    int low = 0;
    for (int num : nums) if (num != 0) nums[low++] = num;  
    while (low < nums.length) nums[low++] = 0;
    return;
}
```
