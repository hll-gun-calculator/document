---
title: 计算函数
layout: default
has_children: true
nav_order: 3
---

# 计算函数
{: .d-inline-block }

支持版本(v0.0.1)
{: .label .label-blue }

函数
{: .label .label-green }

它是计算器的核心，负责对输入值比对各项参数最后求结果，同时你可以随时改用其他‘计算函数’，在内部提供阵营公式、变量、角度;如果允许你可以在应用内更新‘计算函数’.

# 如何导入?

设置 > 计算函数 > + > 选择从网络 或 本地

# 配置函数

配置文件是一个json文件，它由多个字段组成

| 名称                           | 描述                        | 类型                  | 是否必须 | 最低支持版本 |
|------------------------------|---------------------------|---------------------|:----:|--------|
| name                         | 函数名称                      | String or [MapI18n] |  ✅   |        |
| description                  | 描述                        | String or [MapI18n] |      |        |
| version                      | 函数版本                      | String              |  ✅   |        |
| author                       | 作者                        | String              |      |        |
| updataFunction               | 更新,[配置](./updataFunction) | List                |      |        |
| website                      | 网站                        | String              |      |        |
| child                        | 阵营                        | Map                 | 至少一个 |        |
| child.$Factions.maximumRange | 最大角度                      | num                 |  ✅   |        |
| child.$Factions.minimumRange | 最小角度                      | num                 |  ✅   |        |
| child.$Factions.envs         | 变量集                       | Map                 |  ✅   |        |
| child.$Factions.fun          | 函数                        | String              |  ✅   |        |

例子: [查看完整](/config/calcFunction/example.json)

```json
{
  "name": "easyarty-calc",
  "version": "0.0.1",
  "author": "easyarty",
  "website": "easyarty.com",
  "updataFunction": [
    {
      "name": "github path",
      "path": "https://raw.githubusercontent.com/hell-gun-calculator/document/main/config/calcFunction/example.json"
    }
  ],
  "child": {
    "America": {
      "maximumRange": 1600,
      "minimumRange": 100,
      "envs": {
        "maxAngle": 978,
        "maxRange": 1600,
        "minAngle": 622
      },
      "fun": "{maxAngle}-({inputValue}-100)/({maxRange}-100)*({maxAngle}-{minAngle})"
    }
  }
}
```

## 支持运算

fun内置对公式简单解析，基本满足火炮运算所需公式，`{}`包裹的内容为变量，注意它不支持高级语法。

```text
+, -, *, /, ~/, %, -(Negative), >, <, ==, >=, <=, !=, &&, ||, !, &, |,
~, ^, >>, <<, =, +=, -=, &=, |=, ^=, >>=, <<=, expr1 ? expr2 : expr3
```

[MapI18n]: {% link page/dataType/index.md %}
