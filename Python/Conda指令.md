
#### 环境安装位置
C:\\Users\\{username}\\.conda\\envs
#### 第三方库位置

C:\\Users\\{username}\\.conda\\envs\\{env}\\Lib\\site-packages

#### 初始化conda
```bash
conda init
```
初次安装conda时需先初始化conda
#### 列出环境列表
```shell
conda env list
```

#### 删除环境
```shell
conda env remove --name 环境名
```
或者，如果你是在环境被激活的状态下，也可以使用：
```shell
conda remove --name 环境名 --all
```

#### 备份环境
如果你担心将来可能需要这个环境，使用以下命令导出环境到一个YAML文件：
```bash
conda env export --name 环境名 > environment.yaml
```
#### conda 创建环境
```shell
conda create -n {环境名} python={python版本如：3.9}
```
--prefix=安装路径/环境名：用于将环境安装在指定位置
#### 使用环境
```shell
conda activate {环境名}
```

#### 列出环境下的包
```Shell
conda list #<包名>(可选，不添加包名则列出当前环境所有包，可使用正则表达式)
```
-n(--name) <environment_name> ：`<environment_name>`应该被替换为目标环境的名称。这将显示该环境中安装的所有软件包及其版本信息。
--export > <packages.txt>：这个命令会将当前环境的包列表导出到`packages.txt`文件中。这个文件可以用于在另一台机器或环境中重新创建相同的环境。

#### 删除环境
1. 使用`conda env remove --name <环境名>`命令来删除指定环境。这个命令会删除指定环境的所有文件和目录。
2. 如果只是想删除环境下的包，可以使用`conda remove --name <环境名> <包名>`命令来删除指定环境中的指定包。

#### 下载包
```bash
conda install <package>
```
-c <\channel>表示到指定频道去下载

#### 删除包
**从当前激活的环境中删除指定的包：**
```bash
conda remove --name 环境名 包名
```
或者，如果你已经激活了目标环境，可以直接使用：
```bash
conda remove 包名
```
