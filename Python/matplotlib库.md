## matplotlib和matplotlib_inline的关系
### matplotlib

- `matplotlib` 是一个广泛使用的 Python 绘图库，用于创建高质量的图表和图形。
- 它提供了一个类似于 MATLAB 的绘图框架，并支持各种静态、动态和交互式的图表。
- `matplotlib` 可以用于 Python 脚本、Python 和 IPython shell、Jupyter notebook、web 应用服务器以及各种图形用户界面工具包等。

### matplotlib_inline

- `matplotlib_inline` 是一个用于 Jupyter Notebook 和 IPython 的后端模块，它使得 `matplotlib` 的图表可以内嵌在 Notebook 中显示。
- 当你在 Jupyter Notebook 中使用 `%matplotlib inline` 魔法命令时，你实际上是在启用 `matplotlib_inline` 后端。
- 这个后端会自动将 `matplotlib` 生成的图表以 PNG 或 SVG 的形式嵌入到 Notebook 中，使得图表随着笔记本内容一起显示，而不是在新窗口中打开。

### 主要区别

- `matplotlib` 是一个完整的绘图库，提供了绘制图表所需的各种工具和功能。
- `matplotlib_inline` 是一个专门为 Jupyter Notebook 和 IPython 环境设计的后端，用于在这些环境中内嵌显示图表。
- 在 Jupyter Notebook 中使用 `matplotlib` 绘图时，通常会配合 `matplotlib_inline` 使用，以便于图表能够直接在笔记本中显示。

简而言之，`matplotlib` 是用来创建图表的，而 `matplotlib_inline` 是用来在 Jupyter 环境中更好地展示这些图表的工具。
## matplotlib显示图像
对于彩色图像，`matplotlib` 通常期望数据的形状为 `(高度, 宽度, 通道数)`，其中通道数通常是3（对于RGB图像）或4（对于RGBA图像）。
```python
import matplotlib.pyplot as plt

plt.imshow(image)
plt.show()
```