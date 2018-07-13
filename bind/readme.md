bind
=====

* version    `bing9.10`
* name server  `118.24.169.84`
* my domain   `orangleliu.info`, 解析服务dnspod提供
* test domain  `cn.orangleliu.info`, 权威dns测试域名

**小主机，请不要攻击，感谢**

### 说明 

* `name.conf` 总配置入口, logging配置
* `name.conf.local` 域名zone的分布和acl配置
* `name.conf.options` forwords配置还有服务监听等配置，转发的重要配置都在这里
* `db.*` 具体的zone配置

### 实现功能

* forwards功能，简单的公共dns
* 权威dns，解析我自己的一个子域名 `cn.orangleliu.info`
* dns query log的记录

### 简单测试 

国内
```
dig cn.orangleliu.info +short
118.24.169.84
```

国外
```
dig cn.orangleliu.info +short
45.78.37.246
```

dns forword功能
```
dig google.com @118.24.169.84

; <<>> DiG 9.9.7-P3 <<>> google.com @118.24.169.84
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 9641
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		129	IN	A	216.58.203.14

;; Query time: 81 msec
;; SERVER: 118.24.169.84#53(118.24.169.84)
;; WHEN: Fri Jul 13 11:28:17 CST 2018
;; MSG SIZE  rcvd: 55
```