# 用Docker安装RabbitMQ

* ## 1. 下载镜像
  * `docker pull rabbitmq:3.11-management`
* ## 2. 根据下载的镜像，创建和启动容器
  * `docker run -d --name rabbitmq -p 5672:5672 -p 15672:15672 -e RABBITMQ_DEFAULT_USER=admin -e RABBITMQ_DEFAULT_PASS=123456 rabbitmq:3.11-management`
  * 容器名：rabbitmq。
  * 应用访问端口：5672。
  * 控制台web端口：15672。
  * 用户名：admin。
  * 密码：123456。
* ## 3. 查看正在运行的容器
  * `docker ps`
  *

      ![](https://lh5.googleusercontent.com/OiWyd1B0NsEkm0KWD3M5xWfFyh9ZURm8gvaBoH7UuvLcANHlp2g\_e8n7A9M286G-M74gchsSSx-stkDTadPIhI5Z7lHXn3bhPAtthhh21mCllBrq3YBYjRE-uTAHarZ6bvC98JLtVdFy-n9efedTekQ)
* ## 4. 用浏览器打开web管理端
  * `http://localhost:15672/`
  *

      ![](https://lh6.googleusercontent.com/N34yYj\_Y22QwN-KF1c3qqIjHdEbnA1pzZDzP9A\_1rIp9Jr79gmNhCnOHBUBw08vUvsIXCowGktaS4UdVW7EZU5OBgeY4QFmhBP4XyEPIuGohx344bsTEoM6pfjnW1-qk9YXVphZea\_-IgHee6PCp23o)
  * 可以在web页可视化地管理我们的RabbitMQ。
