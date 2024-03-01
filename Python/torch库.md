
#### torch.no_grad()
**`with torch.no_grad():`**：这是一个上下文管理器，用于临时禁用梯度计算。在 PyTorch 中，`.grad` 属性默认会跟踪所有的操作，以便在反向传播时计算梯度。但在进行模型推理（即模型评估或预测时），我们不需要计算梯度。使用 `torch.no_grad()` 可以减少内存消耗并加速计算，因为它告诉 PyTorch 不用保存操作的中间结果和计算梯度。

#### torch.cat
在 PyTorch 中，可以使用`torch.cat()`函数拼接张量
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