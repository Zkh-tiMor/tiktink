# TikTink

前后端分离开发的短视频应用app的后端

V.0.1.0
更新：
1. Logic, DAO层引入自定义上下文
2. 基于自定义 context 实现请求处理链路追踪
3. logger 日志打印模块化封装处理

在controller层中不应该有自定义行为，需要定制化的
操作应该封装好后在controller层调用

如果需要调用下游提供的服务，应传入空白context，调用结束后会
将所有链路信息记录在context中。

V.0.2.0

1. 优化数据库操作逻辑
2. 修改数据库表设计

应尽量避免在循环中操作数据库；表的主键仅用做组织数据，不承担查询功能

V0.2.1

1. 修改数据库及模型字段属性 将id使用varchar类型替换。

在controller层中不应当有自定义行为，指在使用某些频次较高的方法时，应考虑再
封装一层以应对日后可能的拓展。否则修改会很麻烦

参数达到2个或2个以上，该考虑是否可以封装成一个结构体来传参


V0.2.2

- 列表查询引入分页限制

V0.3.0
- 在点赞功能中以Cache的形式引入Redis，提升对高频操作支持的并发量。定时任务将Redis数据同步至MySQL

V0.3.1
- 改用 github.com/pkg/errors 包来进行内部链路追踪。产生错误将记录堆栈信息和参数并打印日志
- 修复用户登录可能无响应的BUG

