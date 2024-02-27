
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

#### conda 创建环境
```shell
conda create -n {环境名} python={python版本如：3.9}
```

#### 使用环境
```shell
conda activate {环境名}
```

#### 列出环境下的包
```Shell
conda list -n <environment_name>
```
其中`<environment_name>`应该被替换为目标环境的名称。这将显示该环境中安装的所有软件包及其版本信息。

#### 删除环境
1. 使用`conda env remove --name <环境名>`命令来删除指定环境。这个命令会删除指定环境的所有文件和目录。
2. 如果只是想删除环境下的包，可以使用`conda remove --name <环境名> <包名>`命令来删除指定环境中的指定包。