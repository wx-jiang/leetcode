一开始以为是背包问题，所以想要用动态规划解决，但是想了一下，有两个困难。

第一：无法去掉重复的情况，比如7 = 2 + 5 = 3 + 4，如果都用vector储存的话，感觉占用的空间很大

第二：递推的公式比较难写

 

所以看了一下discussion：

```
class Solution {
public:
    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        sort(candidates.begin(), candidates.end());
        vector<vector<int> > res;
        vector<int> combination;
        help(candidates, target, res, combination, 0);
        return res;
    }

private:
    void help(vector<int>& candidates, int target, vector<vector<int> >& result, vector<int>& combination, int begin_index) {
        if (target == 0) {
            result.push_back(combination);
            return;
        }
        for (int i = begin_index; i < candidates.size() && target >= candidates[i]; i++) {
            combination.push_back(candidates[i]);
            help(candidates, target - candidates[i], result, combination, i);
            combination.pop_back();
        }
    }
};
```

