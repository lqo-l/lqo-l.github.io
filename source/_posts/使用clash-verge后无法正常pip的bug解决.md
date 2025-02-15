---
title: 使用clash-verge后无法正常pip的bug解决
tags:
  - 
date: 2024-03-16 09:20:25
categories:
cover: img/top/24-3-16-2.jpg
top_img:
description: 
copyright: false

---
最近在cmd命令提示符中尝试pip安装包，出现了奇怪的报错，报错信息如下:
```shell
C:\Users\username>pip install numpy
WARNING: Retrying (Retry(total=4, connect=None, read=None, redirect=None, status=None)) after connection broken by 'SSLError(SSLEOFError(8, 'EOF occurred in violation of protocol (_ssl.c:997)'))': /simple/numpy/
WARNING: Retrying (Retry(total=3, connect=None, read=None, redirect=None, status=None)) after connection broken by 'SSLError(SSLEOFError(8, 'EOF occurred in violation of protocol (_ssl.c:997)'))': /simple/numpy/
WARNING: Retrying (Retry(total=2, connect=None, read=None, redirect=None, status=None)) after connection broken by 'SSLError(SSLEOFError(8, 'EOF occurred in violation of protocol (_ssl.c:997)'))': /simple/numpy/
WARNING: Retrying (Retry(total=1, connect=None, read=None, redirect=None, status=None)) after connection broken by 'SSLError(SSLEOFError(8, 'EOF occurred in violation of protocol (_ssl.c:997)'))': /simple/numpy/
WARNING: Retrying (Retry(total=0, connect=None, read=None, redirect=None, status=None)) after connection broken by 'SSLError(SSLEOFError(8, 'EOF occurred in violation of protocol (_ssl.c:997)'))': /simple/numpy/
Could not fetch URL https://pypi.org/simple/numpy/: There was a problem confirming the ssl certificate: HTTPSConnectionPool(host='pypi.org', port=443): Max retries exceeded with url: /simple/numpy/ (Caused by SSLError(SSLEOFError(8, 'EOF occurred in violation of protocol (_ssl.c:997)'))) - skipping
ERROR: Could not find a version that satisfies the requirement numpy (from versions: none)
ERROR: No matching distribution found for numpy
```
**原因和我使用的代理软件clash-verge有关，其解决方法如下：**
## 方法一：关闭系统代理
简单粗暴，但是注意是关闭系统代理，只是修改为直连模式的话并不能解决问题
<!-- ![clash-verge界面](img/article/24.3.16/clash.png ) -->

<center>
<img src="https://lqo-l.github.io/img/article/24.3.16/clash.png" alt="clash-verge界面"  width="600" />
clash-verge界面
</center>


## 方法二：设置http_proxy和https_proxy环境变量
pip前,在终端（cmd）中运行下述两行命令来指定HTTP 和 HTTPS 协议的代理服务器：
```shell
set http_proxy=http://127.0.0.1:7890
set https_proxy=http://127.0.0.1:7890
```
其中，7890是clash-verge默认的监听端口，修改过的话根据你代理的设置来即可。
<!-- ![端口7890](img/article/24.3.16/clash_port.png) -->
<center>
<img src="https://lqo-l.github.io/img/article/24.3.16/clash_port.png" alt="端口7890"  width="600" />
端口7890
</center>


之后就可以正常pip了~
**注：** 这样配置环境变量只在当前终端有效，新开终端需要重新运行这两行命令。