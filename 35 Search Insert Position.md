二分查找，需要注意的是最后要有一个判断

```c++
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        int len = nums.size();
        if (len == 0) {
            return 0;
        }
        int l = 0;
        int r = len - 1;
        int mid;
        while (l < r) {
            mid = (l + r) / 2;
            if (nums[mid] == target) {
                return mid;
            }
            else if (nums[mid] > target) {
                r = mid - 1;
            }
            else {
                l = mid + 1;
            }
        }
        if (nums[l] >= target) {
            return l;
        }
        else {
            return l + 1;
        }
    }
};
```

