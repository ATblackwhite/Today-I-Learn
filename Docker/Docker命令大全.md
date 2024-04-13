[Docker 命令大全 | 菜鸟教程 (runoob.com)](https://www.runoob.com/docker/docker-command-manual.html#:~:text=Docker%20%E5%91%BD%E4%BB%A4%E5%A4%A7%E5%85%A8%20%E5%AE%B9%E5%99%A8%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F%E7%AE%A1%E7%90%86%20run%20start%2Fstop%2Frestart%20kill%20rm%20pause%2Funpause,commit%20cp%20diff%20%E9%95%9C%E5%83%8F%E4%BB%93%E5%BA%93%20login%20pull%20push%20sea..)

#### 列出容器：ps
`docker ps [OPTIONS]`
##### OPTIONS说明：
- **-a :**显示所有的容器，包括未运行的。
- **-f :**根据条件过滤显示的内容。
- **--format :**指定返回值的模板文件。
- **-l :**显示最近创建的容器。
- **-n :**列出最近创建的n个容器。
	列出最近创建的5个容器信息。`docker ps -n 5`
- **--no-trunc :**不截断输出。
- **-q :**静默模式，只显示容器编号。
- **-s :**显示总的文件大小。
##### 输出详情介绍：
**CONTAINER ID:** 容器 ID。
**IMAGE:** 使用的镜像。
**COMMAND:** 启动容器时运行的命令。
**CREATED:** 容器的创建时间。
**STATUS:** 容器状态。
状态有7种：
- created（已创建）
- restarting（重启中）
- running（运行中）
- removing（迁移中）
- paused（暂停）
- exited（停止）
- dead（死亡）
**PORTS:** 容器的端口信息和使用的连接类型（tcp\udp）。
**NAMES:** 自动分配的容器名称。

#### 创建并运行容器：run
`docker run [OPTIONS] IMAGE [COMMAND] [ARG...]`
##### OPTIONS说明：
- **-a stdin:** 指定标准输入输出内容类型，可选 STDIN/STDOUT/STDERR 三项；
- **-d:** 后台运行容器，并返回容器ID；
- **-i:** 以交互模式运行容器，通常与 -t 同时使用；
- **-P:** 随机端口映射，容器内部端口**随机**映射到主机的端口
- **-p:** 指定端口映射，格式为：主机(宿主)端口:容器端口
- **-t:** 为容器重新分配一个伪输入终端，通常与 -i 同时使用；
- **--name:** 为容器指定一个名称；如果容器名字中间有空格需加引号表示
- **--dns 8.8.8.8:** 指定容器使用的DNS服务器，默认和宿主一致；
- **--dns-search example.com:** 指定容器DNS搜索域名，默认和宿主一致；
- **-h "mars":** 指定容器的hostname；
- **-e username="ritchie":** 设置环境变量；
- **--env-file=[]:** 从指定文件读入环境变量；
- **--cpuset="0-2" or --cpuset="0,1,2":** 绑定容器到指定CPU运行；
- **-m :**设置容器使用内存最大值；
- **--net="bridge":** 指定容器的网络连接类型，支持 bridge/host/none/container: 四种类型；
- **--link=[]:** 添加链接到另一个容器；
- **--expose=[]:** 开放一个端口或一组端口；
- **--volume , -v:** 绑定一个卷
- **--gpus:** 容器能访问GPU

#### 启动容器：start
```bash
docker start <container_name>
```

#### 进入容器终端：attach
```shell
docker attach <container_name>
```

#### 将容器保存为镜像：commit
```shell
docker commit 容器ID 容器镜像名:标签
```
#### 导出镜像：save
```shell
docker save -o 镜像文件名.tar 容器镜像名:标签
```
#### 导入镜像：load
```shell
docker load -i 镜像文件名.tar
```

#### 删除容器：rm
`docker rm [OPTIONS] CONTAINER [CONTAINER...]`
OPTIONS说明：
- **-f** :通过 SIGKILL 信号强制删除一个运行中的容器。
- **-l** :移除容器间的网络连接，而非容器本身。
- **-v** :删除与容器关联的卷。