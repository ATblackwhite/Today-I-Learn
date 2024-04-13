#### DataParallel()
DataParallel类用于并行训练，用法
```python
if torch.cuda.device_count() > 1:
	model = torch.nn.DataParallel(model)
```

#### Identity()
`nn.Identity()` 是PyTorch中的一个层，其作用是实现一个恒等映射，即这个层对输入数据不做任何改变，直接将输入输出。在神经网络中使用 `nn.Identity()` 可以在不改变数据流的情况下占位或替换网络中的某些层。

##### 主要用途

1. **替换网络中的层**：
    - 在修改预训练网络结构时，`nn.Identity()` 可用于替换掉不需要的层。例如，在迁移学习中，常常需要替换掉原始网络的最后一层（如分类层），以适应新的任务，这时可以将其替换为 `nn.Identity()`。
2. **占位符**：
    - 在设计复杂网络时，`nn.Identity()` 可以作为占位符使用，这样可以在不改变网络结构的前提下留出空间，以后可以根据需要添加实际的层。
3. **维护数据流**：
    - 在某些网络设计中，可能需要在不同的分支中保持数据流的完整性，即使某些分支不进行任何操作，也需要通过 `nn.Identity()` 来维持结构的一致性。
#### BCELoss and BCEWithLogitsLoss
`BCELoss` 和 `BCEWithLogitsLoss` 都是用于二元分类问题的损失函数，但它们之间有一些关键的区别：
##### BCELoss

- `BCELoss` 计算二元交叉熵损失，要求输入是概率值，即每个元素的值必须在0和1之间。
- 这通常意味着你需要在模型的最后一层使用sigmoid激活函数来确保输出是有效的概率。
- 公式为：
- $$L=−\frac{1}{N}​\sum​_{i=1}^{N}[y_i​⋅log(\hat{y}_i​)+(1−yi​)⋅log(1−\hat{y}^​i​)]$$
-  其中，$\hat{y}_i​$是模型预测的概率（经过sigmoid函数处理），$y_i$​ 是实际标签。

##### BCEWithLogitsLoss

- `BCEWithLogitsLoss` 结合了sigmoid激活函数和BCELoss的计算，在数值上更稳定。
- 它期望的输入是未经sigmoid变换的原始得分（也称为logits），并且在内部应用sigmoid激活函数。
- 这种损失函数通常更稳定，并且在实现中更有效，因为它组合了sigmoid和BCELoss的计算步骤，避免了因为单独计算而可能产生的数值问题。
- 公式与BCELoss相同，但是应用于sigmoid变换前的logits。

##### 使用建议

- 如果模型的输出已经通过sigmoid激活函数，使得所有预测值都在0和1之间，那么应使用 `BCELoss`。
- 如果模型输出是原始得分（logits），没有经过sigmoid激活，那么应使用 `BCEWithLogitsLoss`。这种方式在数值上更稳定，是推荐的做法。

#### CEloss
注意：torch的Cross-Entropy函数在内部已实现softmax，因此在模型最后一层可以不实现softmax
#### 损失函数参数reduction
一般损失函数会返回一波批次的损失平均值，如果要保留每个样本的损失则使用`reduction='none'`