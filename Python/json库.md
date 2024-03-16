json库可以使python解析或者保存json文件

在python中字典常常用json文件形式保存
```python
import json

# 示例字典
my_dict = {'name': 'John', 'age': 30, 'city': 'New York'}

# 保存字典到JSON文件
with open('my_dict.json', 'w') as f:
    json.dump(my_dict, f)
```
tips： 在dump()方法中，可以添加`indent=`来设置缩进，使文件更加可读。否则文件将以紧凑的形式显示
tips2：json只能序列化python自带形式变量，如果想序列化可以使用自定义函数，添加`default=`参数将变量转换为python变量形式。或者提前将变量进行转换。