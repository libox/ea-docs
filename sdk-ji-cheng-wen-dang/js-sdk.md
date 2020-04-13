---
description: JS SDK 用于由 HTML 、 Css 及 Javascript 制作成的网站
---

# JS SDK

### 一、SDK简介

EA系统是易观基于方舟平台一款触达用户的产品，加强了产品的用户体验和提升了产品的转化率，EA的 JS SDK 是此系统中重要的支撑点，它提供了：

* 触达用户的弹窗功能，支持弹窗样式：

  * 文本样式，支持标题、正文、按钮。
  * 图文混合样式，最上面是标题，下面是正文、图片、按钮。
  * 图文混合样式，最上面是图片，下面是标题、正文、按钮。

####  JS SDK 浏览器版本支持

支持IE 7 以上所有浏览器

### 二、快速开始

   1、 将以下 JS 代码复制到您项目页面中的`<head>`和`</head>`标签之间

{% hint style="info" %}
以下初始化JS代码必须放置在方舟SDK初始化代码之前
{% endhint %}

```javascript
<script>
    (function(config){
        window.AnalysysAgentModalConfig = config || []
    })({
        appKey: '/*设置为实际APPKEY*/', //在EA系统中选择要集成的项目，并在项目属性中查看AppKey
        configURL: '/*设置为实际数据获取地址*/' // 配置您的数据获取地址
    })
</script>

//引用JSSDK文件的script标签必须在初始化代码之下
<script type="text/javascript" src="https://ea.analysys.cn/ark/sdk/AnalysysAgentEA_JS_SDK.min.js"></script>
```

    2、替换方舟SDK

{% hint style="info" %}
方舟SDK替换成EA服务器上的方舟SDK，以下代码放在EA初始化代码之后
{% endhint %}

{% tabs %}
{% tab title="异步集成" %}
```javascript
<script>
    (function(config) {
        window.AnalysysAgent = window.AnalysysAgent || [];
        window.AnalysysAgent.methods = 'identify alias reset track profileSet profileSetOnce profileIncrement profileAppend profileUnset profileDelete registerSuperProperty registerSuperProperties unRegisterSuperProperty clearSuperProperties getSuperProperty getSuperProperties pageView getDistinctId getPresetProperties'.split(' ');

        function factory(b) {
            return function () {
                var a = Array.prototype.slice.call(arguments);
                a.unshift(b);
                window.AnalysysAgent.push(a);
                return window.AnalysysAgent;
            }
        };
        for (var i = 0; i < AnalysysAgent.methods.length; i++) {
            var key = window.AnalysysAgent.methods[i];
            AnalysysAgent[key] = factory(key);
        }
        for (var key in config) {
            if (!AnalysysAgent[key]) AnalysysAgent[key] = factory(key);
            AnalysysAgent[key](config[key]);
        }
        var date = new Date();
        var time = new String(date.getFullYear()) + new String(date.getMonth() + 1) + new String(date.getDate());

        var d = document,
            c = d.createElement('script'),
            n = d.getElementsByTagName('script')[0];
        c.type = 'text/javascript';
        c.async = true;
        c.id = 'ARK_SDK';
        c.src = 'https://ea.analysys.cn/ark/sdk/AnalysysAgent_JS_SDK.min.js' +'?v=' +time; //JS SDK存放地址
        n.parentNode.insertBefore(c, n);
    })({
        appkey: '/*设置为实际APPKEY*/', //APPKEY
        uploadURL: '/*设置为实际地址*/'//上传数据的地址
    })
</script>
```
{% endtab %}

{% tab title="同步集成" %}
```javascript
<script>
    (function(config) {
        window.AnalysysAgent = window.AnalysysAgent || [];
        window.AnalysysAgent.methods = 'identify alias reset track profileSet profileSetOnce profileIncrement profileAppend profileUnset profileDelete registerSuperProperty registerSuperProperties unRegisterSuperProperty clearSuperProperties getSuperProperty getSuperProperties pageView getDistinctId getPresetProperties'.split(' ');

        function factory(b) {
            return function () {
                var a = Array.prototype.slice.call(arguments);
                a.unshift(b);
                window.AnalysysAgent.push(a);
                return window.AnalysysAgent;
            }
        };
        for (var i = 0; i < AnalysysAgent.methods.length; i++) {
            var key = window.AnalysysAgent.methods[i];
            AnalysysAgent[key] = factory(key);
        }
        for (var key in config) {
            if (!AnalysysAgent[key]) AnalysysAgent[key] = factory(key);
            AnalysysAgent[key](config[key]);
        }
    })({
        appkey: '/*设置为实际APPKEY*/', //APPKEY
        uploadURL: '/*设置为实际地址*/'//上传数据的地址
    })
</script>

//引用JS SDK文件的script标签必须在初始化代码之下

//建议在script标签设置id为ARK_SDK,该ID用来引导可视化模块与热图模块的加载
<script type="text/javascript" id="ARK_SDK" src="https://ea.analysys.cn/ark/sdk/AnalysysAgent_JS_SDK.min.js"></script>


```
{% endtab %}
{% endtabs %}

appKey

appkey 为EA系统中集成的项目 AppKey。

* 类型:String。取值长度 1 - 255 字符。

configURL

configURL 为自定义数据获取地址，参数设置后，将从该地址获取数据信息。

* value 类型：String。数据上传地址，格式为 scheme://host + :port\(不包含/后的内容\)。scheme 必须以 http:// 或 https:// 开头，host 只支持域名和 IP，取值长度 1 - 255字符，port 端口号必须携带，eg：[https://ea.analysys.cn:8088](https://ea.analysys.cn:8088) 。

### 三、备注

1、监听事件 window.AnalysysModal\(data\) 说明

```javascript
/**
 * 上报的数据data
 * 类型： Aarry；上报事件集合。
 * eg: [{xwho: 'zA8zsrc71000013', xwhen: 1580895315502, xwhat: '$pageview', xcontext: {$url: 'https://ea.analysys.cn:8088'} }]
 * @param data
 */
window.AnalysysModal = function (data) {
}
```

### 















