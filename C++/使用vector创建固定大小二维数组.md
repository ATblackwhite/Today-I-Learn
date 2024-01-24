[[climit库]]
C++中的vector容器可以创建动态大小的数组，如果要创建二维且初始化固定大小的数组，可以这么写
```Cpp
vector<vector<int>> grid(m, vector<int>(n));
```
不过，仅限于做题的情况下，创建固定大小的二维数组还是用正常的`int a[m][n];`比较合适一点
但在某些情况下，如：给二维数组统一赋上某一个值，此时使用vector容器可以使用std::fill函数给每个数组统一赋上初始值
```cpp
#include <vector>
#include <algorithm>
#include <climits>

const int ROWS = 10;
const int COLS = 10;
std::vector<std::vector<int>> vec(ROWS, std::vector<int>(COLS));

for(auto& row : vec) {
    std::fill(row.begin(), row.end(), INT_MAX);
}

```
或初始化时赋值
```cpp
#include <vector>
#include <climits>

const int ROWS = 10;
const int COLS = 10;
std::vector<std::vector<int>> vec(ROWS, std::vector<int>(COLS, INT_MAX));

```