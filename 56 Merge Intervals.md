想法比较简单，先是给intervals排序，然后遍历一遍intervals。

但是可能时间复杂度和空间复杂度都比较高/(ㄒoㄒ)/~~

```c++
class Solution {
public:
    vector<vector<int>> merge(vector<vector<int>>& intervals) {
        if (intervals.size() == 0 || intervals.size() == 1) {
            return intervals;
        }
        sort(intervals.begin(), intervals.end(), cmp);
        vector<vector<int> > res;
        res.push_back(intervals[0]);
        int mark = 0;
        for (int i = 1; i < intervals.size(); i++) {
            if (intervals[i][0] <= res[mark][1]) {
                res[mark][1] = max(res[mark][1], intervals[i][1]);
            }
            else {
                res.push_back(intervals[i]);
                mark = mark + 1;
            }
        }
        return res;
    }
    static bool cmp(vector<int> a, vector<int> b) {
        return a[0] < b[0];
    }
};
```

