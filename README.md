# 使用logstash处理通达信tc50日志，严禁商用

用ELK给通达信交易主站tc50装个X光机，实时监控系统运行细节，快速回答以下问题：
- 哪些客户委托最多？
- 登录、委托耗时多少？
- 哪些客户端版本使用最多？
- 哪些报错信息最多？
- 哪些站点哪些机器承载的业务量最多？


以下内容是笔记，非最佳实践。比如假如重做可能会把普通和两融日志放在一起而非分开索引。。。

> ELK版本是5.x。更高版本filebeat配置略有变化，请参考官方文档。

> 日志由filebeat采集，发给logstash处理，入库elasticsearch和kafka

> 为避免filebeat直连造成logstash连接过多，部分内网站点采用redis中转。

> 公网站点日志采集，filebeat直连logstash，压缩并ssl加密。

> filebeat：过滤无用日志，多行合并，添加站点标识sitename，发redis或者logstash

> 最早是用服务器命名规则用区分站点。在filebeat添加的fields字段sitename更方便。

- 生成证书：找台linux，修改 my_openssl.cnf 中的 alt_names 生成自用证书。
```
openssl req -x509 -batch -nodes -days 36500 -newkey rsa:2048 -keyout logstash.key -out logstash.crt -config my_openssl.cnf
```

- 安装filebeat服务的脚本install-service-filebeat.ps1，略作修改，清空fbdata下的文件将重新传输日志：
```
# set-executionpolicy remotesigned
# 如果安装服务的脚本执行报错，可能要先运行上面这行命令

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


![image](https://user-images.githubusercontent.com/23710675/117530060-ad179780-b00d-11eb-9258-7457eacbd062.png)


Elastic Stack、logstash、elasticsearch、kibana、filebeat 等是 Elasticsearch BV.公司商标

https://www.elastic.co/legal/trademarks


