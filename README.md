# config-center

## 说明
- 配置文件格式统一用yaml或properties
- 命名与服务的spring.application.name 对应。
- 该配置文件仓库已经配置了webhooks, 在这里提交修改后会自动发送POST请求到配置中心服务。
- 然后通过消息总线通知所有的实例（你所修改的配置文件所属的）拉取最新配置。

## 现象观察
- 访问 http://api.notobject.com/tag 记住当前的值
- 修改 ccsu-proxy-server.yml 中"tag"的值 并提交
- 刷新 http://api.notobject.com/tag 可看到已经获取到最新的配置
- 多次刷新，值仍是最新的，说明所有实例已获取最新配置。（api.notobject.com 已做负载均衡，会交替请求两个ccsu-proxy-server实例）
