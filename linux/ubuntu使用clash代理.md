
## 配置clash代理
```bash
#提前下载好linux版本的Clash.zip文件，下载链接见文末github链接 
unzip clash.zip 
cd clash 
#在这一步需要新建一个proxy.yaml文件在当前文件夹下，并将代理的终端配置文件复制到proxy.yaml中。如果你曾使用过windows的clash，可以点击Profiles，右键edit配置文件，然后就可以复制内容了。 
chmod +x ./clash-linux-amd64-v1.10.0 ./clash-linux-amd64-v1.10.0 -f proxy.yaml -d . #使用proxy.yaml启动代理
```
clash打印如下日志说明启动成功：
```
INFO[0000] HTTP proxy listening at: [::]:7890 
INFO[0000] SOCKS proxy listening at: [::]:7891 
INFO[0000] RESTful API listening at: 127.0.0.1:9090
```

## 在Python中使用代理
```python3
import os
os.environ["HTTP_PROXY"] = "http://127.0.0.1:7890"
os.environ["HTTPS_PROXY"] = "http://127.0.0.1:7890"
```
## 使用代理进行git clone
```console
git clone https://github.com/twbs/bootstrap.git --config "http.proxy=127.0.0.1:7890"
```
## 文件下载
https://link.zhihu.com/?target=https%3A//github.com/sen-ye/linux-clash

引用地址：如何在Linux（Ubuntu）中实现终端代理? - YeThon的回答 - 知乎
https://www.zhihu.com/question/472418041/answer/3289027461
<iframe src="https://www.zhihu.com/question/472418041/answer/3289027461" width="800" height="1600"></iframe>

