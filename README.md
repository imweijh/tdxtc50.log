# 使用logstash处理通达信tc50日志

以下内容是笔记，非最佳实践。比如假如重做可能会把普通和两融日志放在一起而非分开索引。。。

ELK版本是5.x。更高版本filebeat配置略有变化，请参考官方文档。

日志由filebeat采集，发给logstash处理，入库elasticsearch和kafka

为避免filebeat直连造成logstash连接过多，部分内网站点采用redis中转。

公网站点日志采集，采用直连logstash并ssl加密。

filebeat负责：简单过滤无用日志，多行合并，添加站点标识sitename，再发redis或者logstash

最早是用服务器命名规则用区分站点。在filebeat添加的fields字段sitename更方便。

- 生成证书：找台linux，修改 my_openssl.cnf 中的 alt_names 生成自用证书。
```
openssl req -x509 -batch -nodes -days 36500 -newkey rsa:2048 -keyout logstash.key -out logstash.crt -config my_openssl.cnf
```

- 安装filebeat服务的脚本install-service-filebeat.ps1，略作修改：
```
# set-executionpolicy remotesigned

# delete service if it already exists
if (Get-Service filebeat -ErrorAction SilentlyContinue) {
  $service = Get-WmiObject -Class Win32_Service -Filter "name='filebeat'"
  $service.StopService()
  Start-Sleep -s 1
  $service.delete()
}

$workdir = Split-Path $MyInvocation.MyCommand.Path

# create new service
New-Service -name filebeat `
  -displayName filebeat `
  -binaryPathName "`"$workdir\\filebeat.exe`" -c `"$workdir\\filebeat.yml`" -path.home `"$workdir`" -path.data `"$workdir\\fbdata`""

```





