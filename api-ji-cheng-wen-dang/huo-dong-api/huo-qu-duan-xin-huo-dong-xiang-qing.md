# 获取短信活动详情

## 1: 接口地址

```
/ea/api/sms/activityDetailInfo
```

## 2:请求参数示例

接口请求参数，更多参数说明参照 查询API 中的 [通用参数]() 说明

> Header参数

| 参数名 | 必填 | 类型 | 说明 |
| :--- | :--- | :--- | :--- |
| appKey | 是 | string | 项目中设置的appKey |
| token | 是 | string | 项目中设置的apiAccessKey |
| Content-Type | 是 | string | 默认值：application/json |

> Body 参数

```bash
{
    //活动唯一标识
    "activityId":"281761410923458560",
    "page":{
        "pageIndex":0,  //分页索引，第N页 
        "pageSize":10   //每页返回条数
    }
}
```

## 3: 返回参数示例

```bash
{
    "code": 0, //错误码，0：成功；非0失败
    "message": "成功", //描述信息
    "timestamp": 1608576777628,
    "data":{
        "page": 0, //分页索引，第N页 
        "pageSize": 10, //每页返回条数
        "total": 30, // 总条数
        "sendList":[{
            "phone":"18802232111",   // 手机号
            "sign":"签名内容",        // 签名内容
            "content":"诚挚的邀请您参与XXX峰会"  //发送内容
        }]
    }
}
```

## 4: 接口调用示例

```bash
 curl -H "Content-Type:application/json" -H "token:4113c9cad1c301113783f433e254888c" -H "appKey:31abd9593e9983ec" -X POST --data '{
    "page":{
        "activityId":"281761410923458560",
        "pageIndex":0,  //分页索引，第N页 
        "pageSize":10   //每页返回条数
    }
}' http://127.0.0.1:4005/ea/api/sms/activityDetailInfo
```

