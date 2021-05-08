# 使用logstash处理通达信tc50日志

以下内容是笔记，而非最佳实践。

ELK版本是5.x。更高版本filebeat配置略有变化，请参考官方文档。

日志由filebeat采集，发给logstash处理，入库elasticsearch和kafka

为避免filebeat直连造成logstash连接过多，部分内网站点采用redis中转。

公网站点日志采集，采用直连logstash并ssl加密。

filebeat负责：简单过滤无用日志，多行合并，添加站点标识sitename，再发redis或者logstash

最早是用服务器命名规则用区分站点。在filebeat添加的fields字段sitename更方便。



