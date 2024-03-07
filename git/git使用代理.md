## 设置代理
```condole
git config --global http.proxy http://proxyUser:proxyPassword@proxyServer:proxyPort
```

## 使用临时代理进行git clone
```console
git clone https://github.com/twbs/bootstrap.git --config "http.proxy=127.0.0.1:7890"
```