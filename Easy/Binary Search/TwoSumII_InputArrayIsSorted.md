Given an array of integers that is already sorted in ascending order, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2.

Note:

Your returned answers (both index1 and index2) are not zero-based.
You may assume that each input would have exactly one solution and you may not use the same element twice.
```
Example:

Input: numbers = [2,7,11,15], target = 9
Output: [1,2]
Explanation: The sum of 2 and 7 is 9. Therefore index1 = 1, index2 = 2.
```

**Solution**

Takes O(nlogn)

```
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int low = 0;
        int high = numbers.length-1;
        
        for(int i = 0; i < numbers.length-1; i++) {
            int tmp = target - numbers[i];
            int index = binarySearch(numbers, i+1, numbers.length-1, tmp);
            
            if (index != -1) {
                return new int[] {i+1, index+1};
            }
        }
        return new int[] {-1, -1};
    }
    
    private int binarySearch(int[] numbers, int low, int high, int element) {
        while(low <= high) {
            int mid = low + (high-low)/2;
            if(numbers[mid] == element) return mid;
            if(numbers[mid] > element) {
                high = mid-1;
            } else {
                low = mid+1;
            }
        }
        return -1;
    }
}
```

