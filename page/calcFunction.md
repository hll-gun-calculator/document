---
title: calcFunction
layout: default
nav_order: 3
---

# 什么是函数

在应用中函数是动态的，它允许从网络或本地添加,函数内置的计算公式是火炮计算器核心，它将变量放置在公式内计算出结果，因此改变'函数'
会有不同结果。

# 如何导入?

设置 > 计算函数 > + > 选择从网络 或 本地

# 配置函数

配置文件是一个json文件，它由多个字段组成


| 名称                           | 描述   | 类似     | 是否必须 | 最低支持版本 |
|------------------------------|------|--------|:----:|--------|
| name                         | 函数名称 | String |  ✅   |        |
| version                      | 函数版本 | String |  ✅   |        |
| author                       | 作者   | String |      |        |
| website                      | 网站   | String |      |        |
| child                        | 阵营   | Map    |      |        |
| child.$Factions.maximumRange | 最大角度 | num    |  ✅   |        |
| child.$Factions.minimumRange | 最小角度 | num    |  ✅   |        |
| child.$Factions.envs         | 变量集  | Map    |  ✅   |        |
| child.$Factions.fun          | 函数   | String |  ✅   |        |

例子:

```json
{
    "name": "easyarty-calc",
    "version": "0.0.1",
    "author": "easyarty",
    "website": "easyarty.com",
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
