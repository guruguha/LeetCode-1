Given an integer array sorted in non-decreasing order, there is exactly one integer in the array that occurs more than 25% of the time.

Return that integer.

 

```
Example 1:

Input: arr = [1,2,2,6,6,6,6,7,10]
Output: 6
 

Constraints:

1 <= arr.length <= 10^4
0 <= arr[i] <= 10^5
```

**Solution**
```
class Solution {
    public int findSpecialInteger(int[] arr) {
        int window = arr.length/4;
        System.out.println(window);
        int  i = 0; 
        
        while(i + window <= arr.length-1) {
            if(arr[i] == arr[i+window]) break; 
            i++;
        }
        return arr[i];
    }
}
```