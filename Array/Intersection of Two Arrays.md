# Intersection of Two Arrays

Given two arrays, write a function to compute their intersection.

Example 1:
```
Input: nums1 = [1,2,2,1], nums2 = [2,2]
Output: [2]
```
Example 2:
```
Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
Output: [9,4]
```

Note:
* Each element in the result must be unique.
* The result can be in any order.

## Solution

```java
# HashSet
class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        HashSet<Integer> set1 = new HashSet<Integer>();
        for(int i: nums1){
            set1.add(i);
        }

        HashSet<Integer> set2 = new HashSet<Integer>();
        for(int i: nums2){
            if(set1.contains(i)){
                set2.add(i);
            }
        }

        int[] result = new int[set2.size()];
        int i=0;
        for(int n: set2){
            result[i++] = n;
        }

        return result;
    }
}

# Binary Search
class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        Arrays.sort(nums1);
        Arrays.sort(nums2);

        ArrayList<Integer> list = new ArrayList<Integer>();
        for(int i=0; i<nums1.length; i++){
            if(i==0 || (i>0 && nums1[i]!=nums1[i-1])){
                if(Arrays.binarySearch(nums2, nums1[i])>-1){
                    list.add(nums1[i]);
                }
            }
        }

        int[] result = new int[list.size()];
        int k=0;
        for(int i: list){
            result[k++] = i;
        }

        return result;
    }
}
```
