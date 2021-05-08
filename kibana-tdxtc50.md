timelion 各地站点委托耗时-融资融券
```
.es(index="tdxtc2r-*",q='beat.hostname.keyword:tdx2r52* AND reqstr:"(0-202)普通股票委托"',metric='avg:etime').label(两融上海委托).yaxis(2), .es(index="tdxtc2r-*",q='beat.hostname.keyword:tdxJY61* AND reqstr:"(0-202)普通股票委托"',metric='avg:etime').label(两融深圳委托).yaxis(2), .es(index="tdxtc2r-*",q='beat.hostname.keyword:tdxxy-fg* AND reqstr:"(0-202)普通股票委托"',metric='avg:etime').label(两融凤岗委托).yaxis(2),
```

timelion 各地站点委托耗时-集中交易
```
.es(index="tdxtc50-*",q='beat.hostname.keyword:tdxshenyang* AND reqstr:"(0-202)普通股票委托"',metric='avg:etime').label(沈阳委托).yaxis(2),  .es(index="tdxtc50-*",q='beat.hostname.keyword:chengdudx* AND reqstr:"(0-202)普通股票委托"',metric='avg:etime').label(成电委托).yaxis(2), .es(index="tdxtc50-*",q='beat.hostname.keyword:chengdu35* AND reqstr:"(0-202)普通股票委托"',metric='avg:etime').label(成移委托).yaxis(2), .es(index="tdxtc50-*",q='beat.hostname.keyword:beijingtc* AND reqstr:"(0-202)普通股票委托"',metric='avg:etime').label(北京委托).yaxis(2), .es(index="tdxtc50-*",q='beat.hostname.keyword:changsha* AND reqstr:"(0-202)普通股票委托"',metric='avg:etime').label(长沙委托).yaxis(2),  .es(index="tdxtc50-*",q='beat.hostname.keyword:shtdxjy* AND reqstr:"(0-202)普通股票委托"',metric='avg:etime').label(上海委托).yaxis(2),  .es(index="tdxtc50-*",q='beat.hostname.keyword:tdxjy-fg* AND reqstr:"(0-202)普通股票委托"',metric='avg:etime').label(凤岗委托).yaxis(2), .es(index="tdxtc50-*",q='(beat.hostname:tdxjy60* OR beat.hostname:tdxjy19*) AND reqstr:"(0-202)普通股票委托"',metric='avg:etime').label(深圳委托).yaxis(2),
```

timelion 各地站点登录耗时-融资融券
```
.es(index="tdxtc2r-*",q='beat.hostname.keyword:tdx2r52* AND reqstr:"客户校验"',metric='avg:etime').label(两融上海登录).yaxis(2),  .es(index="tdxtc2r-*",q='beat.hostname.keyword:tdxJY61* AND reqstr:"客户校验"',metric='avg:etime').label(两融深圳登录).yaxis(2),  .es(index="tdxtc2r-*",q='beat.hostname.keyword:tdxxy-fg* AND reqstr:"客户校验"',metric='avg:etime').label(两融凤岗登录).yaxis(2),
```

timelion 各地站点登录耗时-集中交易
```
.es(index="tdxtc50-*",q='beat.hostname.keyword:tdxshenyang* AND reqstr:"(0-98)集成客户校验(*)"',metric='avg:etime').label(沈阳登录).yaxis(2),  .es(index="tdxtc50-*",q='beat.hostname.keyword:chengdudx* AND reqstr:"(0-98)集成客户校验(*)"',metric='avg:etime').label(成电登录).yaxis(2), .es(index="tdxtc50-*",q='beat.hostname.keyword:chengdu35* AND reqstr:"(0-98)集成客户校验(*)"',metric='avg:etime').label(成移登录).yaxis(2), .es(index="tdxtc50-*",q='beat.hostname.keyword:beijingtc* AND reqstr:"(0-98)集成客户校验(*)"',metric='avg:etime').label(北京登录).yaxis(2), .es(index="tdxtc50-*",q='beat.hostname.keyword:changsha* AND reqstr:"(0-98)集成客户校验(*)"',metric='avg:etime').label(长沙登录).yaxis(2),  .es(index="tdxtc50-*",q='beat.hostname.keyword:shtdxjy* AND reqstr:"(0-98)集成客户校验(*)"',metric='avg:etime').label(上海登录).yaxis(2),  .es(index="tdxtc50-*",q='beat.hostname.keyword:tdxjy-fg* AND reqstr:"(0-98)集成客户校验(*)"',metric='avg:etime').label(凤岗登录).yaxis(2), .es(index="tdxtc50-*",q='beat.hostname.keyword:tdxjy60* AND reqstr:"(0-98)集成客户校验(*)"',metric='avg:etime').label(深圳登录).yaxis(2),
```

![image](https://user-images.githubusercontent.com/23710675/117529720-af78f200-b00b-11eb-805c-1d08c9e7b0e1.png)


客户端版本占比
![image](https://user-images.githubusercontent.com/23710675/117529263-498b6b00-b009-11eb-8bfc-7e52437dcee6.png)

客户操作系统占比
![image](https://user-images.githubusercontent.com/23710675/117529334-a5ee8a80-b009-11eb-86a5-79bca95a73c9.png)

站点-主机-承载的业务量
![image](https://user-images.githubusercontent.com/23710675/117529476-4c3a9000-b00a-11eb-9e3c-515613ff428e.png)

委托最多的营业部客户
![image](https://user-images.githubusercontent.com/23710675/117529633-25c92480-b00b-11eb-8ef1-065cb4f65096.png)

主机日志量
![image](https://user-images.githubusercontent.com/23710675/117529814-6f663f00-b00c-11eb-9102-b966973f6bb3.png)

错误信息
![image](https://user-images.githubusercontent.com/23710675/117529862-afc5bd00-b00c-11eb-9b1e-5342e605cfc2.png)



