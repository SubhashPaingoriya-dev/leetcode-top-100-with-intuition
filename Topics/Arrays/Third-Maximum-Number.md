# Leetcode 414 - Third Maximum Number

## Optimized C++ Solution

```cpp
class Solution {
public:
    int thirdMax(vector<int>& nums) {

        long first = LONG_MIN;
        long second = LONG_MIN;
        long third = LONG_MIN;

        for(int num : nums) {

            // Skip duplicates
            if(num == first || num == second || num == third)
                continue;

            if(num > first) {
                third = second;
                second = first;
                first = num;
            }
            else if(num > second) {
                third = second;
                second = num;
            }
            else if(num > third) {
                third = num;
            }
        }

        return (third == LONG_MIN) ? first : third;
    }
};
```

## Complexity
- Time Complexity: `O(n)`
- Space Complexity: `O(1)`

## Approach
- Maintain three maximum distinct numbers:
  - `first`
  - `second`
  - `third`
- Traverse the array once.
- Ignore duplicates.
- If third maximum does not exist, return the maximum number.
