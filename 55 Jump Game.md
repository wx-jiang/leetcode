一开始觉得应该要用动态规划，但是没想到递推公式应该是什么样的。

然后看了一下discuss。

动态规划：从后向前推。但是时间复杂度比较高，可能会达到O(n^2)。

后来看到了贪心算法，确实很妙，我没有想到/(ㄒoㄒ)/~~

```c++
class Solution {
public:
    bool canJump(vector<int>& nums) {
        int farest = 0;
        for (int i = 0; i < nums.size(); i++) {
            if (farest < i) {
                return false;
            }
            else {
                farest = max(farest, i + nums[i]);
            }
        }
        return true;
    }
};
```

