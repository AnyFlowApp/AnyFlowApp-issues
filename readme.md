#Read Me

这里是 AnyFlow App 的技术支持仓库，在这里你可以：

### 查看说明文档

[使用说明](https://github.com/AnyFlowApp/AnyFlowApp-issues/blob/master/help_Zh.md)

### 反馈问题或提出建议

[Issue](https://github.com/AnyFlowApp/AnyFlowApp-issues/issues)

## 版本更新记录

### V1.3

2016-12-22

##### New
* 大幅度提升了核心服务的性能，以及稳定性
* 可以从 URL 批量导入规则，支持 Surge 和 ShadowRocket 格式
* 加入 LRU 缓存来提升规则引擎的匹配速度
* 改进图标

##### Fix

* 解锁 GeoIP 匹配功能
* SS 连接的内存泄漏
* 一些代码中错位的 Log 级别
* iPad 上的显示方向错误

### V1.2

2016-12-15

##### New
* SS 支持  代理
* 加入 ShadowSocks 代理
* 修改配置后自动生效，不再需要重启 VPN 服务
* 导入日志文件

##### Fix

* DNS 在有些情况下会丢失
* VPN 某些情况下无法通过 app 来关闭
* iPad上的显示错误
* Rule Test 界面在输入为空时会崩溃 

### V1.1

2016-12-07 

第一个完整可工作的版本

##### New
* 加入代理模块
* 加入规则模块

##### Fix

无

### V1.0

这是为了上线 appstore 提交的基础版本
