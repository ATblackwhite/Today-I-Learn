#### cd
更改终端所在的文件目录

#### del
删除文件

#### rmdir
删除文件夹
/s 删除其子目录和文件
/q 不询问是否删除

#### dir
显示当前所在目录的所有文件、文件夹

#### 跳转到其他硬盘
只需输入相应的硬盘名称即可，不用添加`cd`命令，如跳转到D盘：
```shell
C:\Windows\System32>D:
D:\>
```

#### takeown
使用`takeown`命令获取所有权：
```bash
takeown /f "Your\File\Path" /r /d y
```

#### icacls
使用`icacls`命令赋予完全控制权限：
```bash
icacls "Your\File\Path" /grant UserName:F /t
```
