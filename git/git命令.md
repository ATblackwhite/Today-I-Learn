
#### git查看commit
```bash
git log
```
按下q即可退出

#### 初始化仓库
```shell
git init
```

#### 添加文件到仓库中
```shell
git add .
```

#### 将当前工作目录中的更改保存到本地代码仓库中
```shell
git commit -m "Initial commit"
```

#### 将本地仓库与远程仓库进行关联
```shell
git remote add origin <远程仓库链接>
```

#### 将本地仓库中的代码推送到远程仓库中
```shell
git push origin 分支名
```

#### 切换到目标分支
```shell
git checkout <分支名>
```

#### 合并分支
```shell
git merge <另一分支名>
```
如果报错“fatal: refusing to merge unrelated histories”，在后面加上`--allow-unrelated-histories`

#### 删除本地分支
```shell
git branch -d <分支名>
```

删除远程仓库分支
```shell
git push origin -d <分支名>
```