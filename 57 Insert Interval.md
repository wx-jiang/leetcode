思路和discuss里的高赞是类似的，时间复杂度都是O(n)。

本来的想法是用一个for循环，然后里面各种if语句处理情况，但是代码好长，而且不简洁。

还是高赞的代码简洁明了呀。

ps：这个边界条件的处理，还有点小绕/(ㄒoㄒ)/~~，if语句的判断条件总是写错。

```c++
class Solution {
public:
    vector<vector<int>> insert(vector<vector<int>>& intervals, vector<int>& newInterval) {
        vector<vector<int> > res;
        int i = 0;
        int len = intervals.size();
        while (i < len && intervals[i][1] < newInterval[0]) {
            res.push_back(intervals[i]);
            i++;
        }
        while (i < len && intervals[i][0] <= newInterval[1]) {
            newInterval[0] = min(intervals[i][0], newInterval[0]);
            newInterval[1] = max(intervals[i][1], newInterval[1]);
            i++;
        }
        res.push_back(newInterval);
        while (i < len) {
            res.push_back(intervals[i]);
            i++;
        }
        return res;
    }
};
```

