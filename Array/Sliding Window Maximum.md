# Sliding Window Maximum

Given an array nums, there is a sliding window of size k which is moving from the very left of the array to the very right. You can only see the k numbers in the window. Each time the sliding window moves right by one position. Return the max sliding window.

Example :
```
Input: nums = [1,3,-1,-3,5,3,6,7], and k = 3
Output: [3,3,5,5,6,7]
Explanation:

Window position                Max
---------------               -----
[1  3  -1] -3  5  3  6  7       3
 1 [3  -1  -3] 5  3  6  7       3
 1  3 [-1  -3  5] 3  6  7       5
 1  3  -1 [-3  5  3] 6  7       5
 1  3  -1  -3 [5  3  6] 7       6
 1  3  -1  -3  5 [3  6  7]      7
```

Note:
* You may assume k is always valid, 1 ≤ k ≤ input array's size for non-empty array.

Follow up:
* Could you solve it in linear time?

## Solution

```java
#
class Solution {
    public int[] maxSlidingWindow(int[] nums, int k) {
        if (nums == null || k <= 0) {
			return new int[0];
		}
        ArrayDeque<Integer> window = new ArrayDeque<>();
        int[] result = new int[nums.length - (k - 1)];
        int ri = 0;
        for(int i = 0; i < nums.length; i++) {
            while(!window.isEmpty() && window.peek() < i - k + 1) {
                window.poll();
            }
            while(!window.isEmpty() && nums[window.peekLast()] < nums[i]) {
                window.pollLast();
            }
            window.offer(i);
            if (i >= k - 1) {
				        result[ri++] = nums[window.peek()];
			      }
        }
        return result;
    }
}
```
