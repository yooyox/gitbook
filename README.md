# 小白入门

* ## 1. RabbitMQ是什么意思？
  * RabbitMQ是一款主流的消息中间件。消息中间件，又叫消息队列（Message Queue）。其实它就是一个消息的容器，在程序之间传送消息时的一个中介方容器，可以接收、存储和转发消息。
* ## 2. 我们可以在什么时候用到它？
  * 流量削峰
    * 使用消息队列以后了，用户请求先会到消息队列中，可以限制发送给系统的消息的数量。这样可以避免大量的用户请求在同一时间到达系统。防止系统宕机。
  * 应用解耦
    * 可以将系统拆成不同功能的子系统，每个子系统订阅不同类型的消息。
  * 异步处理
    * 消息发送者在发送完消息以后，不用等待响应。
* ## 3. RabbitMQ是怎么工作的？
  * 抽象的原理
  *

      ![](https://lh6.googleusercontent.com/-71c1MdaIy4aOcSZkvXCKM9jP-AWPXRHx\_5RoEtWs7OjuIhvffOWNQ--\_uQvpsqpIrssUMd9-h2MrFD4a-yOMpmkt9YZHhTwMfY7Xh2B3zw8gRW9ZYC\_FFaWZATXi0rpeLbg-WUtm2sSkLAmi\_6aB4Q)

      * 几个主要角色
        * Producer：生产者。发送消息的程序。
        * Connection：网络连接。如TCP连接。
        * Channel：信道。进行消息读写的一个通道。可以被复用，我们就不用不断地建立和销毁TCP连接。
        * Broker：服务节点。接收客户端的连接，相当于是一个消息代理服务的实体。
        * Virtual Host：虚拟主机。一个Broker可以有多个Virtual Host，用来进行资源的隔离。
        * Exchange：交换机。接收Producer发送来的消息，并根据路由将消息发送给指定的队列。
        * Queue：队列。存放交换机发来的消息。
        * Consumer：消费者。等待接收消息的程序。
  * 如果你觉得上面的概念太晦涩了。那我们来看张图吧：
    *

        ![](https://lh6.googleusercontent.com/F78QLGUba08B8PKD6ADPCGEVUs\_wi87MlJjftbnu3Mu7dtKD6zyVyzrKn3y1gSct9Ru5l7IMOldFQuYSJFCSWe9qx0a4CnfhJzas\_J22MIEil382HQHgnoimT6G3\_MeGCwI09oHAEgQ7ll0jFnpTap0)
    * Producer想把礼物送给Consumer。他来到邮局，有一个Exchange接待了他，他把礼物交给了这个Exchange后就走了。这个Exchange找到了自己的车，把礼物装到车里。礼物开始派送啦，从车里被拿给了Consumer，Consumer拆开礼物，没问题就签收了，订单成功完成啦。
