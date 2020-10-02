本来觉得很难，因为不允许分配新的内存，所以最开始的想法是用固定的分配，通过一个while循环和一个for循环不断旋转，但是很难。

之后又想到把每个数组旋转，但是还是很难，而且要处理很多情况。

大佬的想法很简单，先是reverse整个matrix，之后进行转置矩阵就可以了，时间复杂度应该是O($n^2$)，很简单。这是顺时针旋转，逆时针旋转的方法类似。

```c++
class Solution {

public:

  void rotate(vector<vector<int>>& matrix) {

​    reverse(matrix.begin(), matrix.end());

​    for (int i = 0; i < matrix.size(); i++) {

​      for (int j = i + 1; j < matrix.size(); j++) {

​        swap(matrix[i][j], matrix[j][i]);

​      }

​    }

  }

};
```

