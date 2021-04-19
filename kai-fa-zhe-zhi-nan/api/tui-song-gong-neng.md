# 推送API

## 1、基于用户ID发送推送消息

**请求地址：**【POST】[https://ea.analysys.cn/push/api/send](https://ea.analysys.cn/push/api/send)

**Header参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :---: | :---: | :---: | :---: |
| appKey | 是 | 字符串 | 项目设置中appKey |
| token | 是 | 字符串 | 项目设置中ApI AccessKey |
| Content-Type | 是 | 字符串 | 默认值：application/json |

**Body参数：**

```text
    {
        "userId":"13262953685",
        "channelType":0,
        "iosPackageName":"com.analysys.eaApp",
        "androidPackageName":"com.analysys.eaApp",
        "iosUrl":"testControler",
        "androidUrl":"com.analysys.eaApp.testActivity",
        "title":"你好",
        "content":"你好",
        "openType":0,
        "certificateType":0,
        "extraMsg":{
            "1111":"2222"
        },
        "timestamp":"2020-7-13 22:23:59",
        "trigerStartTime":"2020-7-13 22:23:59",
        "triggerEndTime":"2020-7-13 22:23:59",
        "sendType":0,
        "sendCycle":"10",
        "apiUuid":"sssssss"
    }
```

| 参数 | 必选      | 类型          | 说明 |
| :--- | :--- | :--- | :---: |
| userId | 是 | 字符串 | 用户ID,方舟系统中的userID |
| channelType | 是 | 整型 | 业务类型，0：推送 |
| iosPackageName | 否 | 字符串 | ios包名 |
| androidPackageName | 否 | 字符串 | android包名 |
| iosUrl | 否 | 字符串 | ios页面跳转的ur地址 |
| androidUrl | 否 | 字符串 | android页面跳转的ur地址 |
| title | 是 | 字符串 | 推送标题 |
| content | 是 | 字符串 | 推送内容 |
| openType | 是 | 整型 | 点击通知消息打开APP的方式，0：打开APP；2：打开APP内页面 |
| certificateType | 是 | 整型 | IOS是否为测试证书，0：生产证书；1：测试证书 |
| extraMsg | 否 | 键值对 | 自定义扩展字段 |
| timestamp | 是 | 字符串 | 创建时间 |
| triggerStartTime | 是 | 字符串 | 开始时间 |
| triggerEndTime | 是 | 字符串 | 结束时间 |
| sendType | 是 | 字符串 | 发送的类型，取值如下：发送频率说明 |
| sendCycle | 是 | 字符串 | 发送的时间频率，取值如下：发送频率说明 |
| apiUuid | 是 | 字符串 | 活动的唯一标识，一个活动只能存在一个，如果上传同一个标识的活动，后台会把已经存在的活动取消，在创建新活动 |

**发送频率说明**

| sendType | sendCycle | 说明 |
| :--- | :--- | :--- |
| 0:一次性发送 | n大于等于0 | 0：立即发送；n&gt;0：延迟n秒发送 |
| 3:天为周期 | 10:30:00 | 每天的10:30发送 |
| 4:星期为周期 | nT10:30:00,n为1~7 | 例如:2T10:30:00 ，每周二的10:30发送 |
| 5:月为周期 | nT10:30:00,n为1~31 | 例如:15T10:30:00 ，每月的15号的10:30发送 |
| 6:年为周期 | 07-18 10:30:30 | 每年的7月18号的10:30:30发送 |

**返回结果：**

```text
{
  "code": 0,
  "message": "成功",
}
```

| **参数** | 类型 | 说明 |
| :--- | :--- | :--- |
| code | 整型 | 错误码，0：成功；非0失败 |
| message | 字符串 | 描述信息 |

## 2、基于用户ID取消推送

**请求地址：**【POST】[https://ea.analysys.cn/push/api/](https://ea.analysys.cn/push/api/send)cancel

**Header参数：**

| 参数 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | :--- |
| appKey | 是 | 字符串 | 项目设置中appKey |
| token | 是 | 字符串 | 项目设置中ApI AccessKey |
| Content-Type | 是 | 字符串 | 默认值：application/json |

**Body参数：**

```text
{
    "userId":"13262953685",
    "channelType":0,
    "apiUuid":"sssssss"
}
```

| 参数 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | :--- |
| userId | 是 | 字符串 | 用户ID,方舟系统中的userID |
| channelType | 是 | 字符串 | 业务类型，0：推送 |
| apiUuid | 是 | 字符串 | 活动的唯一标识 |

**返回结果：**

```text
{
    "code": 0,
    "message": "成功",
 }
```

| 参数 | 类型 | 说明 |
| :--- | :--- | :--- |
| code | 整型 | 错误码，0：成功；非0失败 |
| message | 字符串 | 描述信息 |

