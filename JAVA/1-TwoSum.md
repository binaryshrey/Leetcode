TwoSum - 

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
iterate over each element from the given array and add numbers one by one

# Approach
<!-- Describe your approach to solving the problem. -->
iterative approach - check each element sum with the other elements until the target sum is achieved.


# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
O(n^2), where n is the number of elements in the `nums` array. This is because for each element (outer loop), the algorithm potentially checks every other element (inner loop) to find a pair that sums to the target. As a result, the number of comparisons grows quadratically with the size of the input array.

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
O(1), which means it uses a constant amount of extra space. The only additional space used is for the return array that holds the two indices, which does not depend on the size of the input array. Thus, the space used remains constant regardless of the input size.

# Code
```java []
class Solution {
    public int[] twoSum(int[] nums, int target) {
        for(int i=0;i<nums.length;i++){
            for(int j=i+1;j<nums.length;j++){
                if(nums[i] + nums[j] == target){
                  return new int[] {i,j};
                }
            }
        }
        return new int[]{};
    }
}
```