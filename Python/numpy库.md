#### mean()
numpy.mean(a, axis, dtype, out，keepdims )

mean()函数功能：求取均值  
经常操作的参数为axis，以m * n矩阵举例：
- axis 不设置值，对 m * n 个数求均值，返回一个实数
- axis = 0：压缩行，对各列求均值，返回 1 * n 矩阵
- axis =1 ：压缩列，对各行求均值，返回 m * 1 矩阵
详解地址：[http://t.csdnimg.cn/RNLsJ]

#### cov()
函数原型：`def cov(m, y=None, rowvar=True, bias=False, ddof=None, fweights=None,aweights=None)`
- m:一维或则二维的数组，默认情况下每一行代表一个变量（属性），每一列代表一个观测
- y:与m具有一样的形式的一组数据，**如果y=None则说明计算的是本矩阵的方差**
- rowvar:默认为True,此时每一行代表一个变量（属性），每一列代表一个观测；为False时，则反之
- bias:默认为False,此时标准化时除以n-1；反之为n。其中n为观测数
- ddof:类型是int，当其值非None时，bias参数作用将失效。当ddof=1时，将会返回无偏估计（除以n-1），即使指定了fweights和aweights参数；当ddof=0时，则返回简单平均值。
- frequency weights:一维数组，代表每个观测要重复的次数（相当于给观测赋予权重）
- analytic weights:一维数组，代表观测矢量权重。对于被认为“重要”的观察,这些相对权重通常很大,而对于被认为不太重要的观察,这些相对权重较小。如果ddof = 0,则可以使用权重数组将概率分配给观测向量。
详解地址：[http://t.csdnimg.cn/ASYeq]

#### random
numpy生成随机数矩阵
##### randint()
```python
import numpy as np 
# 定义矩阵的尺寸，例如3x3 
rows, cols = 3, 3 
# 生成随机0或1的矩阵 
matrix = np.random.randint(0, 2, size=(rows, cols))
```
#### squeeze(x)
在Python的NumPy库中，`squeeze`方法可以移除数组中所有长度为1的轴：
```python
import numpy as np
x = np.array([[[1], [2], [3]]])
print(x.shape)  # 输出: (1, 3, 1)
x_squeezed = np.squeeze(x)
print(x_squeezed.shape)  # 输出: (3,)
```

#### expand_dims(x, axis)
类似于torch中的unsqueeze
```python
import numpy as np

x = np.array([1, 2, 3])
print(x.shape)  # 输出: (3,)
# 在第一个轴（0轴）前添加一个维度
x_unsqueezed = np.expand_dims(x, axis=0)
print(x_unsqueezed.shape)  # 输出: (1, 3)
# 在第二个轴（1轴）后添加一个维度
x_unsqueezed = np.expand_dims(x, axis=1)
print(x_unsqueezed.shape)  # 输出: (3, 1)
```
#### array()
可以将PIL(pillow)对象以及list转换为numpy数组
#### eye(N, M=None, k=0, dtype=float, order='C')
`np.eye`是NumPy库中的一个函数，用于创建一个二维数组（矩阵），其中对角线上的元素为1，其余位置的元素为0。这种矩阵通常称为单位矩阵或者身份矩阵。`np.eye`的使用非常适合生成独热编码，因为独热编码正是对角线元素为1，其余为0的特殊形式。
##### 使用方法
`np.eye(N, M=None, k=0, dtype=float, order='C')`
- `N`：返回数组的行数。
- `M`：（可选）返回数组的列数。如果未指定，默认为`N`。
- `k`：（可选）对角线的索引。默认为0，表示主对角线；正值表示在主对角线之上，负值表示在主对角线之下。
- `dtype`：（可选）返回数组的数据类型，默认为`float`。
- `order`：（可选）是否在内存中按行优先(`C`)还是列优先(`F`)顺序创建数组。

#### concatenate((a1, a2, ...), axis=0, out=None)
`numpy.concatenate` 是 NumPy 库中用于拼接数组的函数。这个方法可以将多个数组沿指定轴连接在一起形成一个新的数组。
- `a1, a2, ...`：需要被连接的数组。它们必须具有相同的形状，除了沿着连接轴的维度。
- `axis`：指定连接的轴。默认是 0，意味着沿着第一个轴连接。如果指定为 `None`，则先将输入数组展平再进行连接。
- `out`：用于存放结果的数组。如果提供了该参数，则其形状必须足够大以容纳输出结果。
#### transpose()
交换数组的维度