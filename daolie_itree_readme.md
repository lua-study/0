# itree v1.0.5

#### 概述

js 实现无限层级的树形结构 -- 比如多级嵌套菜单、多级目录等...

1. 支持自定义子节点id，父节点id
2. 支持排序
3. 支持父节点id错误监控

#### API

| 属性  | 说明             | 类型   | 必填 | 默认值 |
| ----- | ---------------- | ------ | ---- | ------ |
| list  | 数据源           | Array  | 是   | -      |
| id    | 子节点id     | String | 否   | id     |
| pid   | 父节点id     | String | 否   | pid    |
| nopid | 无父节点id时的标识 | \*     | 否   | null   |
| sort  | 排序的标识   | String | 否   | -      |

#### 示例

```javascript
const list = [
    { id: 1, pId: 2, rank: 1 },
    { id: 2, pId: 0, rank: 2 },
    { id: 3, pId: 0, rank: 1 },
    { id: 0, pId: 'NULL' },
];

const itree = new Itree({
    list: list,
    pid: 'pId',
    nopid: 'NULL',
    sort: 'rank',
});

/**
 * @return tree         树形结构, 保护子节点数据, 层级
 * @return levelsMap    层级Map
 * @return idsMap       子节点Map, 包含子节点全部数据
 * @return pidsMap      父节点Map, 包含子节点全部数据
 * @return ids          子节点标志列表, 按tree顺序排列
 */
const { tree, levelsMap, idsMap, pidsMap, ids } = itree;
```

#### 返回数据

```json
{
    "tree": [
        {
            "id": 0,
            "pId": "NULL",
            "children": [
                {
                    "id": 3,
                    "pId": 0,
                    "rank": 1,
                    "children": [],
                    "level": 2
                },
                {
                    "id": 2,
                    "pId": 0,
                    "rank": 2,
                    "children": [
                        {
                            "id": 1,
                            "pId": 2,
                            "rank": 1,
                            "children": [],
                            "level": 3
                        }
                    ],
                    "level": 2
                }
            ],
            "level": 1
        }
    ],
    "levelsMap": {
        "0": 1,
        "1": 3,
        "2": 2,
        "3": 2
    },
    "idsMap": {
        "0": {
            "id": 0,
            "pId": "NULL",
            "children": [
                {
                    "id": 3,
                    "pId": 0,
                    "rank": 1,
                    "children": [],
                    "level": 2
                },
                {
                    "id": 2,
                    "pId": 0,
                    "rank": 2,
                    "children": [
                        {
                            "id": 1,
                            "pId": 2,
                            "rank": 1,
                            "children": [],
                            "level": 3
                        }
                    ],
                    "level": 2
                }
            ],
            "level": 1
        },
        "1": {
            "id": 1,
            "pId": 2,
            "rank": 1,
            "children": [],
            "level": 3
        },
        "2": {
            "id": 2,
            "pId": 0,
            "rank": 2,
            "children": [
                {
                    "id": 1,
                    "pId": 2,
                    "rank": 1,
                    "children": [],
                    "level": 3
                }
            ],
            "level": 2
        },
        "3": {
            "id": 3,
            "pId": 0,
            "rank": 1,
            "children": [],
            "level": 2
        }
    },
    "pidsMap": {
        "0": [
            {
                "id": 3,
                "pId": 0,
                "rank": 1,
                "children": [],
                "level": 2
            },
            {
                "id": 2,
                "pId": 0,
                "rank": 2,
                "children": [
                    {
                        "id": 1,
                        "pId": 2,
                        "rank": 1,
                        "children": [],
                        "level": 3
                    }
                ],
                "level": 2
            }
        ],
        "2": [
            {
                "id": 1,
                "pId": 2,
                "rank": 1,
                "children": [],
                "level": 3
            }
        ]
    },
    "ids": [0, 3, 2, 1]
}
```

#### 作者

SuperIron


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)