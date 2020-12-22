# 拉取短信活动列表

## 1:接口地址

```bash
【POST】 /ea/api/sms/activityList
```

## 2:请求参数示例

接口请求参数，更多参数说明参照 查询API 中的 [通用参数]() 说明。

> Header参数

| 参数名 | 必填 | 类型 | 说明 |
| :--- | :--- | :--- | :--- |
| appKey | 是 | string | 项目设置中的appkey |
| token | 是 | string | 项目设置中Api AccessKey |
| Content-Type | 是 | string | 默认值: application/json |

> Body参数

```
{
    "page":{
        "pageIndex":0,  //分页索引，第N页 
        "pageSize":10   //每页返回条数
    }
}
```

{% hint style="info" %}
 特殊参数说明
{% endhint %}

## 3: 返回参数示例

```bash
{
    "code": 0,  //错误码，0：成功；非0失败
    "message": "成功",  //描述信息
    "timestamp": 1608576777628,
    "data":{
        "page": 0,  //分页索引，第N页
        "pageSize": 10, //每页返回条数
        "total": 30, //总条数
        //活动列表
        "activityList":[{
            "activityId":"281761410923458560", //活动唯一标识
            "activityName":"测试活动",          //活动名称
            "createTime":"2020-12-17 12:19:15" //活动创建时间
        }]
    }
}
```

## 4. 接口调用示例

```bash
curl -H "Content-Type:application/json" -H "token:4113c9cad1c301113783f433e254888c" -H "appKey:31abd9593e9983ec" -X POST --data '{
    "page":{
        "pageIndex":0,  //分页索引，第N页 
        "pageSize":10   //每页返回条数
    }
}' http://127.0.0.1:4005/ea/api/sms/activityList
```

