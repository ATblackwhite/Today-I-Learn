<span class="notation">以下内容出自chatGPT</span>

要使用conda添加镜像源，你可以通过修改conda的配置文件`.condarc`或者使用命令行来指定镜像源。这里介绍如何使用命令行来添加镜像源。常见的镜像源有Anaconda官方源、清华大学开源软件镜像站、中科大开源软件镜像站等。以下是添加清华大学镜像源和中科大镜像源为例的操作步骤：

### 添加清华大学镜像源
```bash
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --set show_channel_urls yes
```
### 添加中科大镜像源
```bash
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/main/
conda config --set show_channel_urls yes
```

### 查看当前配置
```bash
conda config --show
```
### 设置优先使用添加的镜像源

你可以通过修改`.condarc`文件或使用命令行来设置优先级，使conda优先使用你添加的镜像源。在命令行中，你可以使用`--add channels`命令添加镜像源，并通过`--append`（追加）或`--prepend`（前置）来控制镜像源的优先级。例如，使用以下命令将清华大学镜像源设置为最高优先级：
```bash
conda config --prepend channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
```

### 注意事项

- 添加镜像源后，conda会优先从你添加的镜像源下载软件包，这可以加快下载速度并减少连接问题。
- 某些镜像源可能不包含所有包或版本，如果遇到问题，尝试切换到其他镜像源或使用官方源。
- 你可以随时通过编辑`.condarc`文件或使用`conda config --remove channels <url>`命令来移除不再需要的镜像源。