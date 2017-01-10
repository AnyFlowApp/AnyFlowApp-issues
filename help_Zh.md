# AnyFlow 使用说明

AnyFlow 主要功能分为两大部分，分别是 **流量分析** 和 **流量分发**

## 流量分析

### 作用

帮助开发者分析手机上的网络请求，目前支持以下查看以下类型的请求:

#### HTTP 

* 服务器的 Host
* 服务器的 IP 地址
* 请求头
* 请求 Body
* 响应头
* 响应 Body
* 请求开始时间
* 获取到 DNS 结果的时间
* 连接成功的时间
* 收到响应头的时间
* 完成时间

#### DNS 

* 请求的域名
* 使用的 DNS 服务器
* 返回结果的 DNS 服务器
* 查询开始时间
* 查询结束时间

### 使用方法

首先在 Analytics Tab 中，打开 Enable 选项。然后切换至 Status Tab 连接 VPN，就已经进入了记录状态。这时可以点击 Home 键盘将 AnyFlow 切换至后台，进行其他会产生网络访问的操作。完成后在切换回 AnyFlow 进行查看即可。

### 其他说明

Analytics 功能会记录所有流量到文件系统中，这个动作虽然是异步进行的，但还是会消耗一定的资源，所以请只在需要的时候，打开这个选项，

## 流量分发

### 作用

按照规则对流量进行分发，主要对应四个 Policy:

#### Direct
直接连接 

#### Proxy
通过代理服务器连接，使用这个选项需要事先添加 Proxy 

#### Reject 
拒绝请求，即直接断开 TCP 连接

#### Drop 
静默拒绝请求，功能类似 Reject，但会保持请求的 TCP 连接，实际上不向外转发。
主要的意义在于有些 APP 的请求如果通过 Reject 的方法进行处理，会引发很高频率的重试，照成大量的资源消耗，所以加入了 Drop 策略

### 规则匹配模型

#### Work Mode：

可能有以下三个值:

* Direct 
* Rule Proxy
* Global Proxy

这是个全局选项，当一个请求过来的时候，首先参考这个选项的值。值为 Direct 和 Global Proxy 时，都会直接使用相应的 Policy 处理，只有值为 Rule Proxy 时，才会使用具体的规则来匹配。

#### Rule Group

Rule Group 为一组规则的集合，每个 Rule Group 仅有在 Enable 状态下，即前面打勾时，才会生效。

#### Rule 

这个没啥好讲的

#### Default Policy

所有 Rule Group 里面的所有 Rule 都没有匹配上时，就会使用这个 Policy。

### 匹配的顺序

Rule Group 按照从上往下的顺序进行匹配。
Rule Group 中的 Rule 也按照从上往下的顺序进行匹配。

### 使用方法

添加对应的规则以及 Proxy，然后连接 VPN 即可。

### 其他说明

添加规则后，可以使用 More Tab 里 Rule Test 工具来对规则进行测试，也可以通过 Analytics 功能来查看已经发生的每一个请求使用的 Policy。


