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