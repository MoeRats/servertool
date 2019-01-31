# BBR
自动安装TCP BBR的最新内核

#### 安装
使用root用户登录，运行以下命令：
```
wget --no-check-certificate https://github.com/MoeRats/servertool/raw/master/bbr.sh && chmod +x bbr.sh && ./bbr.sh
```
安装完成后，脚本会提示需要重启 VPS，输入 y 并回车后重启。

#### 查看内核版本

```
uname -r
```
显示为最新版就表示 OK 了

#### 校验
```
sysctl net.ipv4.tcp_available_congestion_control
```
返回值一般为：

`net.ipv4.tcp_available_congestion_control = bbr cubic reno`或者为：`net.ipv4.tcp_available_congestion_control = reno cubic bbr`


```
sysctl net.ipv4.tcp_congestion_control
```
返回值一般为：`net.ipv4.tcp_congestion_control = bbr`

```
sysctl net.core.default_qdisc
```
返回值一般为：`net.core.default_qdisc = fq`


#### 查看是否启动
```
lsmod | grep bbr
```
返回值是`tcp_bbr`模块，即说明 bbr 已启动。

注意：并不是所有的 VPS 都会有此返回值，若没有也属正常。


# 服务器测试
服务器下载和I/O测速脚本
自动测试下载和I / O速度脚本

#### 功能
显示当前测试的各种系统信息；
取自世界多处的知名数据中心的测试点，下载测试比较全面；
支持 IPv6 下载测速；
IO 测试三次，并显示平均值。
#### 使用方法
方法一
```
wget -qO- bench.sh | bash
```
或者
```
curl -Lso- bench.sh | bash
```
方法二
```
wget -qO- 86.re/bench.sh | bash
```
或者
```
curl -so- 86.re/bench.sh | bash
```
