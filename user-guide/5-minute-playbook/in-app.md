# 创建 App 弹窗活动

### 一、设置活动信息

![&#x7B2C;&#x4E00;&#x6B65;&#xFF1A;&#x8BBE;&#x7F6E;&#x6D3B;&#x52A8;&#x4FE1;&#x606F;](../../.gitbook/assets/image%20%289%29.png)

填写活动名称、活动有效期以及是否开启转化跟踪功能。

### 二、选择目标人群

![&#x7B2C;&#x4E8C;&#x6B65;&#xFF1A;&#x9009;&#x62E9;&#x76EE;&#x6807;&#x4EBA;&#x7FA4;](../../.gitbook/assets/image%20%2815%29.png)

通过下拉菜单选择本次 App 弹窗活动将要触达的人群，这些人群可以来自“用户行为分析系统”、“用户标签系统”、“CDP 系统”、“CRM 系统”等。

### 三、设置活动的触发条件

![&#x7B2C;&#x4E09;&#x6B65;&#xFF1A;&#x8BBE;&#x7F6E;&#x6D3B;&#x52A8;&#x89E6;&#x53D1;&#x6761;&#x4EF6;](../../.gitbook/assets/image%20%2813%29.png)

通过设置好的触发条件，当用户满足条件时，系统自动触发活动并将 App 弹窗推送给用户。

* 基于 App 启动事件触发：在 App 启动后，弹窗显示在指定的 App 内页面
* 基于用户行为触发：每次触发设定的事件时，弹窗立即显示在当前页面或者后续指定的 App 内页面

同时，App 弹窗支持用户体验相关的设置：

* 最大弹窗次数：在活动期间内，达到设置的数值时，不再向用户显示弹窗

### 四、设置 App 弹窗的内容及样式

![&#x7B2C;&#x56DB;&#x6B65;&#xFF1A;&#x8BBE;&#x7F6E; App &#x5F39;&#x7A97;&#x7684;&#x6837;&#x5F0F;](../../.gitbook/assets/image%20%2823%29.png)

选择 App 样式模板并填写相关内容信息：

* 图片模板：填写图片的 URL 地址，触发弹窗后，会在 App 内弹出一个图片，用户点击图片可以跳转到指定的落地页
* 图文模板：相比图片模板，额外可以增加一些文字信息，例如活动标题和描述
* 文本模板：单纯的文本弹窗，支持点击不同的按钮跳转到不同的位置

{% hint style="info" %}
如何正确填写弹窗的跳转地址？

目前易达支持 2 类页面地址表达方式：

1. 页面原始地址：

   Android：com.analysys.easytouch.FeedbackActivity

   iOS：EAMineController

2. DeepLink：analysys://android/open\_webview?url=https://ark.analysys.cn

使用 DeepLink 时，需要 App 本身已经能够支持 DeepLink 跳转链接。
{% endhint %}

### 五、预览并执行

预览并执行活动，活动正式运行，状态由“草稿”变为“进行中”或“即将开始”。

