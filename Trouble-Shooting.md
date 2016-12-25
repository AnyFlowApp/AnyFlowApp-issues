# AnyFlow Trouble-Shooting

## 前言

AnyFlow 是一个功能强大并及其复杂的网络工具，可以做很多事情。

因为以上原因，以及早期版本存在一些不完善的地方，有些朋友使用 AnyFlow 的过程中遇到了一些问题，那么我们需要一些耐心和网络知识来帮助解决。

我作为 AnyFlow 的开发者，把这些天用户反馈的问题了进行了统一整理，希望可以对大家有所帮助。

## 使用说明

为了节省大家的时间，对软件不够了解的同学，请先阅读下面的文档

[使用说明](https://github.com/AnyFlowApp/AnyFlowApp-issues/blob/master/help_Zh.md)

## 可能出现问题的地方

### 1，Work Mode 设置

各种规则仅在 **WorkMode** = **Rule Proxy** 模式时才起作用，如果 Work Mode 设置不正确，可能导致无法使用 SS，或者无法拦截广告。

具体请参考使用说明中的规则模型。

### 2，DNS 设置

初始状态中，Addition DNS 中是有几个公共 DNS 服务器的，如果设置了 ``Ignore DNS = True``，而且 ``Addition DNS = 空``，那么会无法获得 DNS 而上不了网。建议保留 ``Addition DNS`` 中的配置。

具体请参考使用说明中的 DNS 部分。

### 3，Reject 规则
Reject 速度非常快，而对某些 APP 来说，请求被 Reject 掉之后，取决于这个 APP 的策略，会有不同的行为。可能就不再请求了，也可能死循环一般在很短的时间里面重试几百次。

如果快速重试，将可能导致发热或者其他的一系列问题，例如 Reject 规则占用了大量的资源导致其他流量不正常等。

这时可以将 Reject 改成安全的 Drop 规则来解决这个问题。

### 4，Analytics
开启 Analytics 时，AnyFlow 需要记录所有的流量到文件系统。是的，你没有看错，这里说的是手机里面全部的网络流量。这会消耗一定的资源，可能导致发热，或者运行变慢的问题。

如果感觉到发热可能是这个原因，请只在需要的时候开启这个选项。

### 5，日志级别
默认日志级别为 Warn。如果设置为更低的日志级别，那么会产生很多日志，这也可能会导致发热。

## 排查问题的步骤
举例来说，如果目标是打造一个包含代理和去广告功能的 AnyFlow，那么如果不能正常工作了，应该按照以下步骤来排查。

### 确认系统版本
* 未在 9.3.5 以下的系统进行过测试，可能会有兼容性问题
* 如果是越狱的系统，可能无法运行

### 确认 WorkMode 和 Default
``WorkMode=RuleProxy``
``Default Policy=Direct``

### 确认 DNS 配置
``Ignore System DNS = False``
``Addition DNS=8.8.8.8, 114.114.114.114, 223.5.5.5``

#### 确认了以上配置之后，取消勾选所有的 Rule Group，连接 VPN。这时应该可以像没有连接 VPN 时一样，可以正常的访问国内网站。如果不行，则表示有问题需要进一步排查。

### 确认 Proxy 配置

* 检查服务器 地址，端口，加密方式，密码 这几项配置是否正确
* ping 服务器测试网络连通状态

####确认了以上配置之后，设置 WorkMode=Global Proxy，连接 AnyFlow，那么所有流量都会从配置好的 Proxy 进行访问。这时应该可以依然访问百度等网站。如果不行，则表示有问题需要进一步排查。

### 确认 Rule Group 配置
如果要使用 Proxy，那么至少要勾选一组可用的 Rule Group。为了排查自己 Rule Group 中可能出现的配置问题，可以先导入 ABCLite 提供的 rule 作为测试。导入 ABCLite 规则之后，把其他的 RuleGroup 都取消掉勾选，然后连接 AnyFlow 进行网络访问测试。如果 ABCLite 规则正常，但是其他的 RuleGroup 不正常，那么说明是规则的原因，请自己仔细排查规则。

[ABCLite Rule](http://www.abclite.cn/Abclite.conf)

####确认了以上配置之后，应该全部工作正常。

## 提交 bug 报告

如果按照以上步骤进行排查了，依然有问题，那么可以向作者提交 Bug 报告，步骤如下：

* 进入 More > Log > Log Level，设置 Level = debug
* 重新进行出现问题的操作
* 进入 More > Log，找到相应的日志，并进行导出。
* 将 Log Level 修改回来

日志分为两个部分，AnyFlow 和 Tunnel。AnyFlow 包含 APP 本身的操作日志，Tunnel 包括处理网络访问的部分，即 VPN 模块。选择相应的部分进行导出即可，如果不确定可以将两个一起导出给我。

Bug 报告请包含日志和尽量详细的复现步骤，以便问题可以得到解决。

邮箱： AlexaZhou@163.com

注：目前 V1.3 版本日志中包含有 SS 的密码等配置，如果又需要的话，导出时可以自己对这些信息进行遮盖处理。下一版本开始不会在日志中包含这些信息。




