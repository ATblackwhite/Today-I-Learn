>以下内容出自chatGPT

在 C++ 中，可以使用标准模板库（STL）中的 `std::map` 或 `std::unordered_map` 来创建一个字典（也称为映射）。这两种容器都允许你存储键值对，但它们在内部实现和性能特性上有所不同。

### std::map

`std::map` 是基于红黑树实现的，它会根据键对元素进行排序。它的优点是能够保持元素的顺序，但在插入和搜索操作上通常比 `std::unordered_map` 慢。
```cpp
#include <iostream>
#include <map>
#include <string>

int main() {
    std::map<std::string, int> myMap;
    myMap["apple"] = 5;
    myMap["banana"] = 3;
    myMap["orange"] = 4;

    // 访问元素
    std::cout << "apple has " << myMap["apple"] << " units." << std::endl;

    // 遍历字典
    for (const auto& pair : myMap) {
        std::cout << pair.first << " has " << pair.second << " units." << std::endl;
    }

    return 0;
}

```
### std::unordered_map

`std::unordered_map` 基于哈希表实现。它提供了平均情况下更快的查找、插入和删除操作，但不保持元素的顺序。
```cpp
#include <iostream>
#include <unordered_map>
#include <string>

int main() {
    std::unordered_map<std::string, int> myMap;
    myMap["apple"] = 5;
    myMap["banana"] = 3;
    myMap["orange"] = 4;

    // 访问元素
    std::cout << "apple has " << myMap["apple"] << " units." << std::endl;

    // 遍历字典
    for (const auto& pair : myMap) {
        std::cout << pair.first << " has " << pair.second << " units." << std::endl;
    }

    return 0;
}

```
### 选择哪一个？

- 如果你需要保持键值对的顺序，使用 `std::map`。
- 如果你需要更高效的查找、插入和删除操作，并且不在乎元素的顺序，使用 `std::unordered_map`。

在使用这些容器时，要注意键类型必须支持比较操作（对于 `std::map`）或哈希操作（对于 `std::unordered_map`）。对于自定义类型作为键，你可能需要提供自定义的比较或哈希函数。