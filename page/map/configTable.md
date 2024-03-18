---
title: 地图配置表
layout: default
parent: 地图合集
---

# 配置地图合集

| 名称              | 描述                                         | 类型                  | 例子                 | 是否必须 | 最低支持版本 |
|-----------------|--------------------------------------------|---------------------|--------------------|:----:|--------|
| name            | 函数名称                                       | String or [MapI18n] | "none"             |  ✅   |        |
| description     | 描述                                         | String or [MapI18n] | null               |      |        |
| size            | 地图大小, [宽,高]                                | List                | [1000, 1000]       |  ✅   |        |
| initialPosition | 初始位置                                       | List                | [0,0]              |      |        |
| factions        | 阵营, 详情查看[配置](/page/dataType/factions)的阵营名称 | Map<Factions>       | {"America": {...}} |      |        |
| assets          | 基本地图,[assets参数](#assets参数)                 | Map                 | {}                 |      |        |
| childs          | 图层                                         | Map                 | {}                 |      |        |
| marker          | [marker参数](#marker参数)                      | List                | []                 |      |        |

## factions参数

| 名称                                 | 描述   | 类型                              | 例子          | 是否必须 | 最低支持版本 |
|------------------------------------|------|---------------------------------|-------------|------|--------|
| factions.$FactionsName.gunPosition | 火炮位置 | List<[Gun](/page/dataType/Gun)> | [Gun]          |      |        |
| factions.$FactionsName.points      | HQ点  | List                            | [[0,0],[1,1]] |      |        |
| factions.$FactionsName.direction   | 方向   | MapInfoFactionInfoDirection     | 查看          |  ✅    |        |

例子:

```json
{
  "America": {
    "gunPosition": [
      {
        "name": "America Gun 1",
        "description": {
          "zh_CN": "位置"
        },
        "offset": [114.876, 1890]
      }
    ],
    "points": [
      [40, 300]
    ],
    "direction": "Left"
  }
}
```

## assets参数

| 名称             | 描述 | 类型     |   是否必须    | 最低支持版本 |
|----------------|----|--------|:---------:|--------|
| assets.network | 网络 | String | 任意一个，不可同时 |        |
| assets.local   | 本地 | String | 任意一个，不可同时 |        |

例子:

```json
{
  "network": "http://"
}
```

或

```json
{
  "local": "//sd//"
}
```

## marker参数

| 名称                         | 描述       | 类型                    | 是否必须 | 最低支持版本 |
|----------------------------|----------|-----------------------|:----:|--------|
| marker.$Index[^1].name     | 标记名称     | num                   |  ✅   |        |
| marker.$Index[^1].iconType | 图标类型     | [MapIconType]         |  ✅   |        |
| marker.$Index[^1].iconPath | 图标地址(可选) | String                |      |        |
| marker.$Index[^1].points   | 点坐标      | List<MarkerPointItem> |  ✅   |        |

# 例子

- by https://github.com/hell-gun-calculator/document/blob/main/config/map

[^1]: 列表下标，并非常数

[MapI18n]: {% link page/dataType/index.md %}
[MapIconType]: {% link page/dataType/index.md %}