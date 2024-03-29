pytorch基础：(https://transformers.run/c2/2021-12-14-transformers-note-3/)
#### torch.tensor()
在PyTorch中，可以使用`torch.tensor()`函数将列表转换为张量。这个函数接受一个数据列表作为输入，并返回一个包含这些数据的PyTorch张量。这里是一个简单的例子：
```python
import torch

# 定义一个列表
list_data = [1, 2, 3, 4, 5]

# 将列表转换为张量
tensor_data = torch.tensor(list_data)

print(tensor_data)
```
在这个例子中，`list_data`是一个包含整数的列表，使用`torch.tensor()`函数将其转换为一个PyTorch张量`tensor_data`。打印出来的`tensor_data`将显示其内容和张量类型。
#### torch.no_grad()
**`with torch.no_grad():`**：这是一个上下文管理器，用于临时禁用梯度计算。在 PyTorch 中，`.grad` 属性默认会跟踪所有的操作，以便在反向传播时计算梯度。但在进行模型推理（即模型评估或预测时），我们不需要计算梯度。使用 `torch.no_grad()` 可以减少内存消耗并加速计算，因为它告诉 PyTorch 不用保存操作的中间结果和计算梯度。
#### 变量复制转移
1. 使用`.to()`方法
```python
# 转移到计算卡上
tensor_variable = tensor_variable.to("cuda")
# 转移到cpu
tenso_variable = tensor_variable.to("cpu)
```
2. 使用`.cpu()`转移到cpu上

#### torch.clamp
在 PyTorch 中，`torch.clamp` 函数用于将张量中的值剪切到指定范围。具体来说，输入张量中任何小于指定最小值的值都将被设置为该最小值，而任何大于指定最大值的值都将被设置为该最大值。介于最小值和最大值之间的值将保持不变。
```python
t = torch.tensor([-1, 0.5, 2, 0.8])
clamped_t = torch.clamp(t, min=0, max=1)
# clamped_t的值会是[0, 0.5, 1, 0.8]
```


#### torch.cuda.is_available()
查看torch能否使用cuda

#### torch.Tensor.scatter_(dim, index, src)
- **dim** (int)：是要散布的维度。
- **index** (LongTensor)：包含要散布到的索引。
- **src**：要散布的值。它可以是一个与输出同形状的张量，或者当我们只需要散布一个值时，它可以是一个标量。

#### torch.Tensor.view(\*shape)
- **shape**：一个由新形状的维度组成的整数序列。你可以指定所有的维度大小，或者使用 `-1` 在一个维度上让 PyTorch 自动计算其大小。

#### torch.Tensor.detach()
`detach()` 方法在 PyTorch 中用于创建一个新的张量，该张量从当前计算图中分离出来。这意味着通过 `detach()` 方法创建的新张量不会有梯度，也就是说，它不会在反向传播过程中更新梯度。这个方法通常用于防止对某些张量的操作被纳入梯度计算中，例如，当你想固定某些模型参数或者数据时。
##### 注意事项

- 使用 `detach()` 方法可以避免在不需要梯度的场合进行不必要的梯度计算，这在特定场景下可以提高效率，如在评估模型时。
- 分离出来的张量与原张量共享数据，因此改变其中一个张量的值会影响另一个。
- `detach()` 方法常用于固定预训练网络的某些层，或者在进行一些特定的操作时不希望影响梯度传播。

#### torch.randperm(n)
`torch.randperm(n)` 是 PyTorch 中的一个函数，用于生成一个从 `0` 到 `n-1` 的随机排列。这个函数返回一个包含 `0` 到 `n-1` 所有整数的一维张量，这些整数被随机排列。该方法常用于生成乱序索引，可以用于乱序遍历数组或将数据集分割为训练集和测试集等场景。


##### 工作原理
1. **前向传播**：计算模型的输出，并根据预测结果和真实结果计算损失（loss）。
2. **反向传播**：调用损失张量的 `.backward()` 方法来计算模型参数（weights 和 biases）的梯度。
3. **参数更新**：执行 `optimizer.step()` 来更新模型参数。这个步骤会根据之前计算的梯度来调整模型参数，以减少损失。
##### 注意事项
- 在调用 `optimizer.step()` 之前，通常需要先调用 `optimizer.zero_grad()` 来清除累积的梯度，以防止在每次更新时梯度被累加。
- 参数更新步骤（`optimizer.step()`）不会自动清除梯度，因此在下一次反向传播前，需要手动清除旧的梯度。
- 选择合适的优化器和学习率对于训练过程非常重要，因为它们直接影响到模型训练的速度和质量。
#### torch.nonzero()
PyTorch中的`nonzero()`方法是一个非常有用的函数，它用于获取张量中所有非零元素的索引。这个方法通常在你想知道哪些元素满足特定条件（例如，不等于零）时非常有用。`nonzero`返回的是一个索引的张量，每行都包含原始张量中非零元素的索引。
```python
# 创建一个张量 
tensor = torch.tensor([[0, 1, 0], [2, 0, 2], [0, 0, 0]]) 
# 使用nonzero方法找到非零元素的索引 
nonzero_indices = torch.nonzero(tensor)
# 或者
nonzero_indices = tensor.nonzero()

#结果为[[0, 1], [1, 0], [1, 2]]
```
#### torch.randint()
```python
import torch
# 定义矩阵的尺寸，例如3x3
rows, cols = 3, 3
# 生成随机0或1的矩阵
matrix = torch.randint(0, 2, (rows, cols))
```
#### torch.squeeze(x)
在PyTorch中，`squeeze`方法同样用于移除张量中所有长度为1的维度。如果指定了维度参数，则仅尝试移除该维度；如果该维度的长度不是1，则张量不会发生变化
```python
import torch
x = torch.zeros(1, 3, 1)
print(x.size())  # 输出: torch.Size([1, 3, 1])
x_squeezed = torch.squeeze(x)
print(x_squeezed.size())  # 输出: torch.Size([3])
```

#### torch.Tensor.unsqueeze(dim)
`unsqueeze`方法用于在指定位置添加一个长度为1的维度：
```python
import torch
x = torch.tensor([1, 2, 3])
print(x.size())  # 输出: torch.Size([3])
# 在第0轴前添加一个维度
x_unsqueezed = x.unsqueeze(0)
print(x_unsqueezed.size())  # 输出: torch.Size([1, 3])
# 在第1轴后添加一个维度
x_unsqueezed = x.unsqueeze(1)
print(x_unsqueezed.size())  # 输出: torch.Size([3, 1])
```
#### 张量拼接
##### torch.cat()
如果你想要在现有的维度上合并张量，而不是添加一个新的维度，你可以使用`torch.cat`。
```python
import torch

# 示例张量
tensor1 = torch.rand(2, 3)  # 形状为 [2, 3]
tensor2 = torch.rand(2, 2)  # 形状为 [2, 2]

# 沿着水平方向（第二维）拼接它们
result = torch.cat((tensor1, tensor2), dim=1)

print(result)
print("Result shape:", result.shape)
```
##### torch.stack()
`torch.stack`函数会沿着一个新的维度合并张量列表，这意味着所有张量必须有完全相同的形状。
##### 选择`stack`还是`cat`
- 如果你想在所有张量上添加一个新的维度，使用`torch.stack`。
- 如果你想在某个现有的维度上合并张量，使得该维度的大小增加，使用`torch.cat`。

#### torch.Tensor.argmax()
`tensor.argmax()` 是一个在深度学习和数值计算库中常见的方法，如PyTorch、TensorFlow等。这个方法用于找到张量（tensor）中最大元素的索引。

具体来说，`argmax()` 方法会沿着指定的维度（如果有的话）遍历张量，并返回最大元素的索引。如果没有指定维度，它通常会在整个张量上操作，并返回单个最大元素的索引。

### 参数

- **axis**（或某些库中的`dim`）: 你想在哪个维度上寻找最大值。如果未指定，`argmax()` 会在张量的全部元素中寻找最大值。
- **keepdims**（可选）: 是否保持输出的维度与输入相同。如果设置为`True`，输出将保持与原始张量相同的维度，但所有非操作轴上的维度大小都会是1。

### 返回值

- 返回最大元素的索引。如果`axis`指定了维度，则返回在该维度上每个切片的最大元素的索引的张量。

### 示例

假设我们有一个PyTorch的张量示例：
```python
import torch

# 创建一个2x3的张量
tensor = torch.tensor([[1, 2, 3], [4, 5, 6]])

# 沿着维度0找到最大值的索引
index = tensor.argmax(dim=0)

# 沿着维度1找到最大值的索引
index_along_dim1 = tensor.argmax(dim=1)

print(index)  # 输出: tensor([1, 1, 1])
print(index_along_dim1)  # 输出: tensor([2, 2])
```
在这个例子中，`argmax(dim=0)` 沿第一个维度找到最大值，结果表明每列的最大值都在第二行。`argmax(dim=1)` 沿第二个维度找到最大值，结果表明每行的最大值都在第三列。