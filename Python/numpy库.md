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
