# 故障排查



## 使用mtr排查网络异常

mtr工具的主要作用是在于两点丢包时候的异常点排查及路径搜集，是ping和tracert的结合。
相比于ping它会有路由节点的展示，而相对于tracert它会展示中间路由节点的丢包情况，可以根据丢包梯度情况简单分析出可能的异常节点并向对应运营商进行反馈。

由于骨干外网路径可能存在的异步路由（即数据包来回路径不一致，可能在某一方向看无明显异常点，另一方向才会显示异常）与ECMP（运营商在多根路径上做负载均衡，某一根异常导致部分IP丢包），建议提供双向mtr。

### Windows下使用mtr

**用法（以winmtr为例）**

1、输入目标域名或IP地址（注意前面不能加空格），点击start开始探测

![image](/images/mtr_win01.png)

2、运行一段时间后，点击stop 停止探测。同时可以选择Copy Text to clipboard：将测试结果以文本格式复制到粘贴板。

![image](/images/mtr_win02.png)

### Linux下使用mtr

**下载安装**

centos系统可用 yum install -y mtr 安装，其他操作系统建议采用相关下载工具

**用法**

1、mtr + 目标域名或IP地址，并回车执行命令

![image](/images/mtr_linux01.png)

2、等待路由跟踪结束即可

![image](/images/mtr_linux02.png)

### Mac下使用mtr

**用法**

1、mtr + 目标域名或IP地址，回车执行，等待路由追踪结束即可

![image](/images/mtr_mac01.png)
