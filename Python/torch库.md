pytorch基础：(https://transformers.run/c2/2021-12-14-transformers-note-3/)
#### torch.no_grad()
**`with torch.no_grad():`**：这是一个上下文管理器，用于临时禁用梯度计算。在 PyTorch 中，`.grad` 属性默认会跟踪所有的操作，以便在反向传播时计算梯度。但在进行模型推理（即模型评估或预测时），我们不需要计算梯度。使用 `torch.no_grad()` 可以减少内存消耗并加速计算，因为它告诉 PyTorch 不用保存操作的中间结果和计算梯度。
#### torch.clamp
在 PyTorch 中，`torch.clamp` 函数用于将张量中的值剪切到指定范围。具体来说，输入张量中任何小于指定最小值的值都将被设置为该最小值，而任何大于指定最大值的值都将被设置为该最大值。介于最小值和最大值之间的值将保持不变。
```python
t = torch.tensor([-1, 0.5, 2, 0.8])
clamped_t = torch.clamp(t, min=0, max=1)
# clamped_t的值会是[0, 0.5, 1, 0.8]
```


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

#### torch.gather()
`torch.gather` 函数在 PyTorch 中是用于从输入张量中按照指定索引收集值的函数。简单来说，它按照一个索引张量的结构，从一个源张量中提取出值来形成一个新的张量。

函数的原型是：
`torch.gather(input, dim, index, *, sparse_grad=False, out=None) → Tensor`
- `input` 是要收集数据的原始张量。
- `dim` 是你想要在哪个维度上进行索引操作的指示。
- `index` 是包含了要收集的元素索引的张量，它的形状与 `input` 在非 `dim` 维度上的形状相同。
- `out` 是一个可选参数，用于指定输出的张量。

当你调用 `torch.gather` 时，它会沿着指定的维度 `dim` 查找，并从 `input` 中取出 `index` 指示位置上的值。

例如，假设你有一个形状为 `(3, 4)` 的二维张量 `input` 和一个同样形状的 `index` 张量，你可以这样使用 `torch.gather`：
```python
input = torch.tensor([[1, 2, 3, 4],
                      [5, 6, 7, 8],
                      [9, 10, 11, 12]])
# 假设我们想从每一行中取出一个元素
index = torch.tensor([[0], [1], [2]])
# 用 torch.gather 在第1维上收集
output = torch.gather(input, 1, index)
```

输出 `output` 将是：
```python
tensor([[ 1],
        [ 6],
        [11]])
```

因为 `index` 张量在第1维（列）上的值分别为 0, 1, 和 2，所以从 `input` 的每一行中收集了第0, 1, 和 2个元素。

`torch.gather` 是一个非常灵活的函数，可以用于多种场景，比如重新排列张量的元素、从概率分布中收集特定事件的概率、或者在构造高级损失函数时选择特定的元素。
