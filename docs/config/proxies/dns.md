```{.yaml linenums="1"}
proxies:
- name: "dns-out"
  type: dns
```

`dns`出站会将请求劫持到内部[dns](../dns/index.md)模块,所有请求均在内部处理

!!! warning ""
    暂不支持劫持tcp请求,请配合[网络类型规则使用](../rules/network.md)
