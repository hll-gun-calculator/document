---
title: 计算函数更新
layout: default
parent: 计算函数
---

# 更新
{: .d-inline-block }

函数
{: .label .label-green }

计算函数提供更新，在清单中`updataFunction`字段为此实现，在应用中允许用户主动更新或由程序决定，`updataFunction`是一个列表，如果提供第一条更新链接无效，程序会持续往下按照提供地址获取新配置。

## 更新条件

- 用户主动更新
- 初始化检查计算函数版本是否更新
- 长时间再次使用强制更新

# 配置

| 名称   | 描述              | 必须 | 版本 |
|------|-----------------|----|----|
| name | 来源名称            | ✅  |    |
| path | 网络地址，http/https | ✅  |    |

```json
{
  "updataFunction": [
    {
      "name": "example website",
      "path": "https://example.com/example.json"
    },
    {
      "name": "example2 website",
      "path": "https://example2.com/example.json"
    }
  ]
}
```