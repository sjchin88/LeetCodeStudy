# Two Pointers

## Fast/Slow pointer (same direction)

## Sliding Window (Concept)

This concept is efficient when we want to find a contiguous subarray(or substring) with specified conditions.&#x20;

Problems:&#x20;



209\. Minimum Size Subarray Sum [https://leetcode.com/problems/minimum-size-subarray-sum/](https://leetcode.com/problems/minimum-size-subarray-sum/)

1004\. Max Consecutive Ones III [https://leetcode.com/problems/max-consecutive-ones-iii/](https://leetcode.com/problems/max-consecutive-ones-iii/)

```java
class Solution {
    public int minSubArrayLen(int target, int[] nums) {
        int left = 0; 
        int right = 0; 
        int minLength = nums.length+1;
        int sum = 0; 
        for(right = 0; right < nums.length; right++){
            //add the nums[right] to sum
            sum+=nums[right];
            //continue increase the left index if sum >= target
            while(sum >= target){
                //first check if there is a smaller minimum length
                minLength = Math.min(minLength, right-left+1);
                //minus off the nums[left] value from sum
                sum-= nums[left];
                //increment the left index
                left++;
            }
        }
        if(minLength <= nums.length){
            return minLength;
        }else{
            return 0;
        }
    }
}
```
