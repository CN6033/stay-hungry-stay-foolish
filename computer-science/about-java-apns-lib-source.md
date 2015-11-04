# 阅读java-apns库源码总结

有如下几点感悟

## 一、有关源码组织
java-apns库的主体功能代码在 **com.notnoop.apns** package下，另外 **com.notnoop.exceptions** 这个package保存了异常定义。

其中，**com.notnoop.apns** 代码主要分为两部分。一部分是接口的定义，另一部分在 **internal** package下，是功能的具体实现。

## 二、何如快速学习一个库所提供的所有功能
在了解java-apns库的源码组织之后，想要快速了解它的功能就只要把java-apns库的接口定义看一遍，就基本能了解一个大概了。下面是java-apns库的所有接口：

- APNS

> The main class to interact with the APNS Service. Provides an interface to create the ApnsServiceBuilder and ApnsNotification payload.（其实也就是一个辅助类）

- ApnsService

> 这是推送服务所提供的所有功能的定义。提供了start、stop、push、getInactiveDevices和testConnection这些操作接口。

- ApnsServiceBuilder

> ApnsServiceBuilder用来辅助构建ApnsService实例。

- PayloadBuilder

> PayloadBuilder用来辅助用户构建合法的payload，并提供一些检校功能。例如，isTooLong方法协助用户检查payload是否超过苹果对payload的长度限制。

- ApnsDelegate

> 定义了消息推送状态变更时的回调（callback）接口。支持的事件有messageSent、messageSendFailed、connectionClosed、cacheLengthExceeded和notificationsResent。

- StartSendingApnsDelegate

> 这是对ApnsDelegate接口的一个扩充，补充了startSending事件，用来告诉调用方某一条消息已经开始推送了。

- ApnsDelegateAdapter

> 空的ApnsDelegate接口实现，同Java其它Adapter类语意一直。

- ApnsNotification

> Represents an APNS notification to be sent to Apple service.

- SimpleApnsNotification

> Represents an APNS notification to be sent to Apple service. Deprecated.

- EnhancedApnsNotification

> Represents an APNS notification to be sent to Apple service.

- ReconnectPolicy

> 连接重连策略接口。用户可以自己定义，也能选择三个默认实现：NEVER、EVERY_HALF_HOUR和EVERY_NOTIFICATION。

- DeliveryError

> 推送失败状态定义

在了解这些接口之后，就可以放心使用这个库了。

## 三、设计模式
TODO
