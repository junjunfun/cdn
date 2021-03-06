# 预热URL {#task_878830 .task}

您可以在业务高峰前预热热门资源，也可以预热流量较低的加速域名，再次访问该资源时，直接从CDN节点获取，从而提升CDN的缓存命中率。

执行本文操作之前，请确保您已完成阿里云[账号注册](https://account.alibabacloud.com/register/intl_register.htm)和[实名认证](https://account-intl.console.aliyun.com/#/intlAuth)。

CDN节点作为所有使用CDN的用户公用的节点资源，因此CDN配置的缓存规则表示了该资源在CDN上的缓存最长时间，如果您的CDN加速域名流量较低，则可能提前从CDN节点的缓存中清除。即缓存按照热度属性采取末尾淘汰制。热度是指文件在节点上被访问的频率，文件热度不够，被提前剔除。

-   预热功能是指将URL提前上传到CDN的L2节点上，再次访问时无需从源站获取资源，虽然预热没有直接提升L1的命中率，但是提升了CDN的真实命中率。
-   刷新功能是指将特定URL或者目录下的所有历史缓存的内容清除掉，该操作常用于源站进行同名更新后导致CDN缓存内容为历史垃圾数据，刷新后将使URL下次访问时直接回源，会导致命中率下降，请您谨慎使用CDN刷新功能。

1.  登录[CDN控制台](https://cdn.console.aliyun.com)。
2.  在左侧导航栏，单击**刷新**。 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/5168/156860488456840_zh-CN.png)

3.  选择**操作类型**和**预热**，填写**URL**。
4.  单击**提交**。

