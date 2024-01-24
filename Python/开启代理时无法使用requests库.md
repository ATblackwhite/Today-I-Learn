### 如果你的请求不想走v2ray的设置：

设置 -> 参数设置 -> 系统代理设置 -> 下拉选中：socks={ip}:{socks_port}
![[requests不走代理.png]]

### 如果你的请求想走v2ray则设置为：
`http=http://{ip}:{http_port};https=http://{ip}:{http_port}`
![[requests走代理.png]]