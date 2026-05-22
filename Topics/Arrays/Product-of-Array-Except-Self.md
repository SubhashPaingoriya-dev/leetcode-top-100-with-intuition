# Leetcode 238 - Product of Array Except Self

## Optimized C++ Solution

```cpp
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {

        int n = nums.size();

        vector<int> prefArr(n, 1), suffArr(n, 1);

        // Build prefix and suffix product arrays
        for(int i = 1; i < n; i++) {

            prefArr[i] = prefArr[i - 1] * nums[i - 1];

            suffArr[n - i - 1] = suffArr[n - i] * nums[n - i];
        }

        // Multiply prefix and suffix products
        for(int i = 0; i < n; i++) {

            prefArr[i] *= suffArr[i];
        }

        return prefArr;
    }
};
```

## Complexity
- Time Complexity: `O(n)`
- Space Complexity: `O(n)`

## Approach
- Create:
  - Prefix product array
  - Suffix product array
- `prefArr[i]` stores product of all elements before index `i`
- `suffArr[i]` stores product of all elements after index `i`
- Final answer for each index:
  
```text
prefArr[i] * suffArr[i]
```

## Example

Input:
```text
[1,2,3,4]
```

Prefix Array:
```text
[1,1,2,6]
```

Suffix Array:
```text
[24,12,4,1]
```

Output:
```text
[24,12,8,6]
```
