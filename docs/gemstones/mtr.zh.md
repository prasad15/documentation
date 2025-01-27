---
title: mtr - 网络诊断
author: tianci li
contributors: Steven Spencer
date: 2021-10-20
---

# `mtr`简介

`mtr`是一个网络诊断工具，可以诊断网络问题，用来替代 `ping`与`traceroute`命令，在性能上，`mtr`命令的速度更加快。

## 使用`mtr`
```bash
# 安装 mtr
shell >  dnf -y install mtr
```

`mtr`命令的常见选项如下，通常情况下，都不需要额外选项，后面直接跟主机名或IP地址

|选项|说明|
|---|---|
|-4 |# 仅使用IPv4|
|-6  |# 仅使用IPv6|
|-c  COUNT  |# 发送的ping数|
|-n  |# 不解析主机名|
|-z   |# 显示AS号|
|-b  |# 显示ip和主机名|  
|-w |# 输出范围广泛的报告|

终端交互的信息如下：
```bash
shell > mtr -c 10 bing.com

                    My traceroutr  [v0.92]
li(192.168.100.4)                           2021-10-20T08:02:05+0800
Keys:Help   Display mode  Restart Statistics  Order of fields  quit
HOST: li                 Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. _gateway             0.0%    10    2.0   5.6   2.0  12.9   3.6
  2. 10.9.128.1           0.0%    10   13.9  14.8   8.5  20.7   3.9
  3. 120.80.175.109       0.0%    10   15.8  15.0  10.0  20.1   3.1
  4. 112.89.0.57         20.0%    10   18.9  15.2  11.5  18.9   2.9
  5. 219.158.8.114        0.0%    10   10.8  14.4  10.6  20.5   3.5
  6. 219.158.24.134       0.0%    10   13.1  14.5  11.9  18.9   2.2
  7. 219.158.10.30        0.0%    10   14.9  21.2  12.0  29.8   6.9
  8. 219.158.33.114       0.0%    10   17.7  17.1  13.0  20.0   2.0
  9. ???                 100.0    10    0.0   0.0   0.0   0.0   0.0
 10. ???                 100.0    10    0.0   0.0   0.0   0.0   0.0
 11. ???                 100.0    10    0.0   0.0   0.0   0.0   0.0
 12. ???                 100.0    10    0.0   0.0   0.0   0.0   0.0
 13. a-0001.a-msedge.net  0.0%    10   18.4  15.7   9.5  19.3   3.1
...
```

* Loss% - 丢包率
* Snt - 已发送的包数
* Last - 最后一个包的延迟
* Avg - 平均延迟
* Best - 最低延迟
* Wrst - 最差延时
* StDev - 方差（稳定性）

## 交互时的快捷键
<kbd>p</kbd> - 暂停；
<kbd>d</kbd> - 切换显示模式；
<kbd>n</kbd> - 开/关DNS；
<kbd>r</kbd> - 重置所有计数器；
<kbd>j</kbd> - 切换延迟显示信息；
<kbd>y</kbd> - 切换IP信息；
<kbd>q</kbd> - 退出交互。
