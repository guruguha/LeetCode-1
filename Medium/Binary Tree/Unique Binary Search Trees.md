Given n, how many structurally unique BST's (binary search trees) that store values 1 ... n?

```
Example:

Input: 3
Output: 5
Explanation:
Given n = 3, there are a total of 5 unique BST's:

    1         3     3      2      1
     \       /     /      / \      \
      3     2     1      1   3      2
     /     /       \                 \
    2     1         2                 3
 ```

**Solution - DP**

```
class Solution {
    public int numTrees(int X) {
        int r[] = new int[X+1];
        r[0] = 1;
        r[1] = 1;
        
        // n is the length of the sequence
        for(int n = 2; n <= X; n++) {
            
            // for a given n, i is made as the root of the BST
            for(int i = 1; i <= n; i++) {
                
                // number of ways to form BST with n elements = 
                // number of ways to form BST with [i-1] number of elements * 
                // number of ways to form BST with [n-i] number of elements
                // Ex: i = 3 n = 6
                //in the sequence 1, 2, 3, 4, 5, 6 left of i has [i-1] elements and right of i has [n-i] elements
                r[n] += r[i-1] * r[n-i];
            }
        }
        return r[X];
    }
}
```


** Solution - DP with Recursion**

```
class Solution {
    public int numTrees(int n) {
        Map<Integer, Integer> map = new HashMap<>();
        map.put(0, 1);
        map.put(1, 1);
        return helper(n, map);
    }
    
    private int helper(int n, Map<Integer, Integer> map) {
        if(map.containsKey(n))
            return map.get(n);
        
        int sum = 0;
        
        for(int i = 1; i <= n; i++) {
            sum += helper(i-1, map) * helper(n-i, map);
        }
        
        map.put(n, sum);
        
        return sum;
    }
}
```
