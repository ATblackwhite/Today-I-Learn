#### 保存模型
pytorch提供方法来让你保存模型中的参数，确保你的模型继承自`torch.nn.Module`
```python
import torch

model = create_model()
...
training
...
torch.save(model.state_dict(), 'path/to/save')
```

#### 加载模型
请确保加载的模型和保存的模型文件有相同的结构
```python
import torch
import torch.nn as nn

# 假设我们有一个简单的神经网络模型
class SimpleModel(nn.Module):
    def __init__(self):
        super(SimpleModel, self).__init__()
        self.fc = nn.Linear(10, 5)  # 示例：10个输入特征和5个输出特征

    def forward(self, x):
        return self.fc(x)

# 实例化模型
model = SimpleModel()

# 加载.pth文件
model_path = 'path_to_your_model.pth'
model.load_state_dict(torch.load(model_path))

# 确保在评估模式下使用模型，这对于包含如Dropout和BatchNorm等层的模型很重要
model.eval()
```
