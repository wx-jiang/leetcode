这道题的想法挺巧妙的。我看到投票最优的做法，时间复杂度是O(n)，空间复杂度是常数，挺厉害的。

分别从左右两端逼近，同时维持max_left和max_right。具体看代码。

```c++
class Solution {
public:
    int trap(vector<int>& height) {
        int left = 0;
        int right = height.size() - 1;
        int max_left = 0;
        int max_right = 0;
        int result = 0;
        while (left <= right) {
            if (height[left] >= height[right]) {
                if (height[right] > max_right) {
                    max_right = height[right];
                }
                else {
                    result = result + (max_right - height[right]);
                }
                right = right - 1;
            }
            else {
                if (height[left] < max_left) {
                    result = result + (max_left - height[left]);
                }
                else {
                    max_left = height[left];
                }
                left = left + 1;
            }
        }
        return result;
    }
};
```