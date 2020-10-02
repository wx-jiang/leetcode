这道题挺经典的，在discuss里发现了一个很有意思的解法，用一个方向向量，以及交换行、列变量。

```c++
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        vector<int> result;
        if (matrix.empty() == true) {
            return result;
        }
        result = matrix[0];
        int direction[4][2] = {{1, 0}, {0, -1}, {-1, 0}, {0, 1}};
        int d = 0;
        int m = matrix.size();
        int n = matrix[0].size();
        int position[2] = {0, n - 1};
        int total_num = (m - 1) * n;
        while (total_num > 0) {
            for (int i = 1; i < m; i++) {
                position[0] = position[0] + direction[d][0];
                position[1] = position[1] + direction[d][1];
                result.push_back(matrix[position[0]][position[1]]);
                total_num = total_num - 1;
            }
            m = m - 1;
            swap(m, n);
            d = (d + 1) % 4;
        }
        return result;
    }
};
```

