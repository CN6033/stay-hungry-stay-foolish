# 阅读java-apns库源码总结

有如下几点感悟

## 一、有关源码组织
apns库的主体功能代码在**com.notnoop.apns** package下，另外还有**com.notnoop.exceptions**这个package专门放置了所有异常的定义。

其中，**com.notnoop.apns** 代码主要分为两部分。一部分是各种接口的定义，另一部分在**internal** package下，功能的具体实现都在这。

## 二、何如快速学习一个库所提供的所有功能
在了解apns库的源码组织之后，想要快速了解它的功能就只要把apns库的所有接口定义看一遍，就基本能了解一个大概了。下面是apns库的所有接口：
- APNS
> The main class to interact with the APNS Service. Provides an interface to create the ApnsServiceBuilder and ApnsNotification payload.
- ApnsService
> 这是整个推送服务所提供的基本功能入口的接口定义。提供了start/stop/push/getInactiveDevices/testConnection这些操作入口。
- ApnsServiceBuilder
> ApnsServiceBuilder用来支持灵活构建ApnsService instance。
- PayloadBuilder
> PayloadBuilder用来辅助用户快速构建合法的payload，并提供一些检校功能。例如，isTooLong方法协助用户检查payload是否超过苹果对payload的长度限制。
- ApnsDelegate
> 定义了当消息推送状态变更时的回掉接口。主要事件有messageSent、messageSendFailed、connectionClosed、cacheLengthExceeded和notificationsResent。
- StartSendingApnsDelegate
> 这是对ApnsDelegate接口的一个扩充，补充了startSending事件，用来告诉调用方某一条消息已经开始推送了。
- ApnsDelegateAdapter
> 空的ApnsDelegate接口实现，同Java其他Adapter类语意一直。
- ApnsNotification
> Represents an APNS notification to be sent to Apple service.
- SimpleApnsNotification
> Represents an APNS notification to be sent to Apple service. Deprecated.
- EnhancedApnsNotification
> Represents an APNS notification to be sent to Apple service.
- ReconnectPolicy
> APNs连接重连策略。用户可以自己定义，也能选择三个默认实现：NEVER、EVERY_HALF_HOUR和EVERY_NOTIFICATION。
- DeliveryError
> 推送失败状态定义

在了解这些接口之后，就可以放心使用这个库了。
