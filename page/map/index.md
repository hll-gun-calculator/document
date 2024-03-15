---
title: 地图合集
layout: default
has_children: true
nav_order: 4
---

# 地图合集
{: .d-inline-block }

地图
{: .label .label-green }

{: .note }
作为’地图测量‘所加载地图数据，这包含地图本身、额外图层、坐标

# 配置地图合集

| 名称              | 描述             | 类型                  | 是否必须 | 最低支持版本 |
|-----------------|----------------|---------------------|:----:|--------|
| name            | 函数名称           | String or [MapI18n] |  ✅   |        |
| description     | 描述             | String or [MapI18n] |      |        |
| size            | 地图大小, [宽,高]    | List                |  ✅   |        |
| initialPosition | 初始位置           | List                |      |        |
| factions        | 阵营             | Map，配置              |      |        |
| assets          | 基本地图         | Map                 |      |        |
| childs          | 图层             | Map                 |      |        |
| marker          | [marker参数](标记) | List                |      |        |

## assets参数

| 名称             | 描述 | 类型     |   是否必须    | 最低支持版本 |
|----------------|----|--------|:---------:|--------|
| assets.network | 网络 | String | 任意一个，不可同时 |        |
| assets.local   | 本地 | String | 任意一个，不可同时 |        |

## marker参数

| 名称                         | 描述       | 类型                    | 是否必须 | 最低支持版本 |
|----------------------------|----------|-----------------------|:----:|--------|
| marker.$Index[^1].name     | 标记名称     | num                   |  ✅   |        |
| marker.$Index[^1].iconType | 图标类型     | [MapIconType]                    |  ✅   |        |
| marker.$Index[^1].iconPath | 图标地址(可选) | String                |      |        |
| marker.$Index[^1].points   | 点坐标      | List<MarkerPointItem> |  ✅   |        |

[^1]: 列表下标，并非常数

[MapI18n]: {% link page/dataType/index.md %}
[MapIconType]: {% link page/dataType/index.md %}
