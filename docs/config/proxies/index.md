```{.yaml linenums="1"}
proxies:
- name: "ss"
  type: ss
  server: server
  port: 443
  ip-version: ipv4
  udp: true
  interface-name: eth0
  routing-mark: 1234
  tfo: false
  mptcp: false
  skip-cert-verify: false

  dialer-proxy: ss1

  smux:
    enable: false
    brutal-opts:
      enabled: false
```

## proxies

代理节点书写以 `proxies`为开头,其内容为数组

### name

必须项,代理名称,书写时请确保不会与其他代理节点重名

### type

必须项,代理节点类型

### server

必须项,代理节点服务器(域名/ip)

### port

必须项,代理节点端口

### ip-version

设置节点使用 IP 版本,可选: `dual`/`ipv4`/`ipv6`/`ipv4-prefer`/`ipv6-prefer`,默认使用`dual`

* ipv4: 仅使用 IPv4
* ipv6: 仅使用 IPv6
* ipv4-prefer : 优先使用 IPv4,对于 TCP 会进行双栈解析,并发链接但是优先使用 IPv4 链接,UDP 则为双栈解析,获取结果中的第一个 IPv4
* ipv6-prefer:优先使用 IPv6,对于 TCP 会进行双栈解析,并发链接但是优先使用 IPv6 链接,UDP 则为双栈解析,获取结果中的第一个 IPv6

### udp

是否允许UDP通过代理,默认为`false`

!!! note
    此选项在`TUIC`等基于`UDP`或者`VMess`等默认`UoT`的协议中默认开启

### interface-name

指定节点绑定的接口,从此接口发起连接

### routing-mark

节点发起连接时附加的路由标记

### tfo

启用`TCP Fast Open`,仅生效于`TCP`协议

### mptcp

启用`TCP Multi Path`,仅生效于`TCP`协议

### skip-cert-verify

跳过证书验证,仅适用于使用`tls`的协议

### dialer-proxy

参阅 [dialer-proxy](./dialer-proxy.md)

### smux

仅支持[`Shadowsocks`](./ss.md)/[`VMess`](./vmess.md)/[`VLESS`](./vless.md)/[`Trojan`](./trojan.md)协议,参阅 [sing-mux](./sing-mux.md)

#### brutal-opts

TCP Brutal

参阅 [brutal-opts](./sing-mux.md#brutal-opts)
