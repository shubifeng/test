# analysis-web swagger（数据平台api）


<a name="overview"></a>
## 概览
全局统一约定：1.时间传输用时间戳类型，2.所有金额一律以分为单位进行处理并返回


### 版本信息
*版本* : 1.1.0.RELEASE


### 联系方式
*名字* : 舒笔锋，罗灿江


### URI scheme
*域名* : localhost:9063  
*基础路径* : /


### 标签

* 云分销app-商品数据 : Report Ware Controller
* 云分销app-预付款报表 : Report Channel Purchase Controller




<a name="paths"></a>
## 路径

<a name="orderchartusingget"></a>
### 预付款提货汇总柱状图
```
GET /reports/channelPurchase/orderChart
```


#### 参数

|类型|名称|说明|类型|默认值|
|---|---|---|---|---|
|**Query**|**beginTime**  <br>*必填*|beginTime|integer (int64)||
|**Query**|**endTime**  <br>*必填*|endTime|integer (int64)||
|**Query**|**orderType**  <br>*可选*|预付款订单类型：YUN_MI (1云米产品提货), XIAO_MI (2小米生态链产品提货), MATERIAL (3物料提货)|integer (int32)|`1`|
|**Query**|**timeType**  <br>*必填*|timeType可选值: day(d按天,默认),month(m按月),quart(q按季),year(y按年)|enum (day, month, quart, year)||
|**Query**|**token**  <br>*必填*|用户会话token|string||


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[响应体«渠道预付款统计汇总»](#ffdb961c8fc98065b580208fcebe1527)|
|**400**|业务异常{"timestamp": 0, "status": 0, "path": "url", "error": "msg" }|无内容|


#### 消耗

* `application/json`


#### 生成

* `*/*`


#### 标签

* 云分销app-预付款报表


#### HTTP请求示例

##### 请求 path
```
/reports/channelPurchase/orderChart
```


##### 请求 query
```
json :
{
  "beginTime" : 0,
  "endTime" : 0,
  "orderType" : 0,
  "timeType" : "string",
  "token" : "string"
}
```


#### HTTP响应示例

##### 响应 200
```
json :
{
  "code" : 0,
  "desc" : "string",
  "result" : {
    "listData" : [ {
      "dataTime" : "string",
      "orderFee" : 0,
      "orderNum" : 0,
      "refundOrderFee" : 0,
      "refundOrderNum" : 0
    } ],
    "totalData" : {
      "orderFee" : 0,
      "orderNum" : 0,
      "refundOrderFee" : 0,
      "refundOrderNum" : 0
    }
  },
  "timestamp" : 0
}
```


<a name="orderchartdetailusingget"></a>
### 预付款提货报表明细
```
GET /reports/channelPurchase/orderChartDetail
```


#### 参数

|类型|名称|说明|类型|默认值|
|---|---|---|---|---|
|**Query**|**beginTime**  <br>*必填*|beginTime|integer (int64)||
|**Query**|**endTime**  <br>*必填*|endTime|integer (int64)||
|**Query**|**orderType**  <br>*可选*|预付款订单类型：YUN_MI (1云米产品提货), XIAO_MI (2小米生态链产品提货), MATERIAL (3物料提货)|integer (int32)|`1`|
|**Query**|**token**  <br>*必填*|用户会话token|string||


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[响应体«List«渠道预付款订单统计详情»»](#74b4471f037d036851ef2e84df92b819)|
|**400**|业务异常{"timestamp": 0, "status": 0, "path": "url", "error": "msg" }|无内容|


#### 消耗

* `application/json`


#### 生成

* `*/*`


#### 标签

* 云分销app-预付款报表


#### HTTP请求示例

##### 请求 path
```
/reports/channelPurchase/orderChartDetail
```


##### 请求 query
```
json :
{
  "beginTime" : 0,
  "endTime" : 0,
  "orderType" : 0,
  "token" : "string"
}
```


#### HTTP响应示例

##### 响应 200
```
json :
{
  "code" : 0,
  "desc" : "string",
  "result" : [ {
    "channelId" : 0,
    "orderFee" : 0,
    "orderNum" : 0,
    "productNum" : 0,
    "channelName" : "string",
    "secondChannel" : "string",
    "rootChannel" : "string"
  } ],
  "timestamp" : 0
}
```


<a name="waressaleslistusingget"></a>
### 商品数据：订单商品的销售量，销售额
```
GET /reports/wares/sales
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Query**|**beginTime**  <br>*必填*|beginTime|integer (int64)|
|**Query**|**endTime**  <br>*必填*|endTime|integer (int64)|
|**Query**|**platformType**  <br>*必填*|平台类型：YUN_MI (1云米商城), MI_JIA (2米家商城), TIAN_MAO (3天猫商城), YU_FU_KUAN (4预付款提货)|enum (YUN_MI, MI_JIA, TIAN_MAO, YU_FU_KUAN)|
|**Query**|**timeType**  <br>*必填*|timeType可选值: day(d按天,默认),month(m按月),quart(q按季),year(y按年)|enum (day, month, quart, year)|
|**Query**|**token**  <br>*必填*|用户会话token|string|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[响应体«List«某个时间内商品的销售量与销售额»»](#aebb836524779bf4ac3a54ccb8344e2e)|
|**400**|业务异常{"timestamp": 0, "status": 0, "path": "url", "error": "msg" }|无内容|


#### 消耗

* `application/json`


#### 生成

* `*/*`


#### 标签

* 云分销app-商品数据


#### HTTP请求示例

##### 请求 path
```
/reports/wares/sales
```


##### 请求 query
```
json :
{
  "beginTime" : 0,
  "endTime" : 0,
  "platformType" : "string",
  "timeType" : "string",
  "token" : "string"
}
```


#### HTTP响应示例

##### 响应 200
```
json :
{
  "code" : 0,
  "desc" : "string",
  "result" : [ {
    "data_time" : "string",
    "quantity" : "string",
    "sales" : "string"
  } ],
  "timestamp" : 0
}
```


<a name="waressalesdetaillistusingget"></a>
### 商品数据：订单商品的销售量，销售额
```
GET /reports/wares/salesDetail
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Query**|**beginTime**  <br>*必填*|beginTime|integer (int64)|
|**Query**|**endTime**  <br>*必填*|endTime|integer (int64)|
|**Query**|**platformType**  <br>*必填*|平台类型：YUN_MI (1云米商城), MI_JIA (2米家商城), TIAN_MAO (3天猫商城), YU_FU_KUAN (4预付款提货)|enum (YUN_MI, MI_JIA, TIAN_MAO, YU_FU_KUAN)|
|**Query**|**timeType**  <br>*必填*|timeType可选值: day(d按天,默认),month(m按月),quart(q按季),year(y按年)|enum (day, month, quart, year)|
|**Query**|**token**  <br>*必填*|用户会话token|string|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[响应体«List«某个时间内某一种商品的销售量与销售额»»](#cfb221ddf0dca9fffaa481bcdf5c9aef)|
|**400**|业务异常{"timestamp": 0, "status": 0, "path": "url", "error": "msg" }|无内容|


#### 消耗

* `application/json`


#### 生成

* `*/*`


#### 标签

* 云分销app-商品数据


#### HTTP请求示例

##### 请求 path
```
/reports/wares/salesDetail
```


##### 请求 query
```
json :
{
  "beginTime" : 0,
  "endTime" : 0,
  "platformType" : "string",
  "timeType" : "string",
  "token" : "string"
}
```


#### HTTP响应示例

##### 响应 200
```
json :
{
  "code" : 0,
  "desc" : "string",
  "result" : [ {
    "name" : "string",
    "quantity" : 0,
    "sales" : 0
  } ],
  "timestamp" : 0
}
```


<a name="wareprodlistusingget"></a>
### 商品数据：商品的库存量，待发货数
```
GET /reports/wares/stock
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Query**|**catalogIds**  <br>*可选*|商品所属类目id：多个以,分割。https://note.youdao.com/share/?token=6E940ACE238B4D39AADA5F67B20C6B04&gid=42130582|string|
|**Query**|**pendingCountRange**  <br>*可选*|待出库范围：10,200 表示（开始值,结束值），或者为空值|string|
|**Query**|**prodName**  <br>*可选*|prodName|string|
|**Query**|**saleStatus**  <br>*可选*|商品在售状态：0预售,1在售|integer (int32)|
|**Query**|**stockCountRange**  <br>*可选*|库存范围：10,200 表示（开始值,结束值），或者为空值|string|
|**Query**|**token**  <br>*必填*|用户会话token|string|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[响应体«List«商品的存库与待发货数»»](#4da52ddafa2dcabe4d6c85f62445e2f9)|
|**400**|业务异常{"timestamp": 0, "status": 0, "path": "url", "error": "msg" }|无内容|


#### 消耗

* `application/json`


#### 生成

* `*/*`


#### 标签

* 云分销app-商品数据


#### HTTP请求示例

##### 请求 path
```
/reports/wares/stock
```


##### 请求 query
```
json :
{
  "catalogIds" : "string",
  "pendingCountRange" : "string",
  "prodName" : "string",
  "saleStatus" : 0,
  "stockCountRange" : "string",
  "token" : "string"
}
```


#### HTTP响应示例

##### 响应 200
```
json :
{
  "code" : 0,
  "desc" : "string",
  "result" : [ {
    "name" : "string",
    "pending_count" : 0,
    "stock" : 0,
    "type_name" : "string"
  } ],
  "timestamp" : 0
}
```




<a name="definitions"></a>
## 定义

<a name="channelpurchaseordertotaldto"></a>
### ChannelPurchaseOrderTotalDTO
ChannelPurchaseOrderResp的数据汇总


|名称|说明|类型|
|---|---|---|
|**orderFee**  <br>*可选*|提货金额  <br>**样例** : `0`|integer (int64)|
|**orderNum**  <br>*可选*|提货订单数  <br>**样例** : `0`|integer (int64)|
|**refundOrderFee**  <br>*可选*|退货退款额  <br>**样例** : `0`|integer (int64)|
|**refundOrderNum**  <br>*可选*|退货退款订单  <br>**样例** : `0`|integer (int64)|


<a name="4da52ddafa2dcabe4d6c85f62445e2f9"></a>
### 响应体«List«商品的存库与待发货数»»

|名称|说明|类型|
|---|---|---|
|**code**  <br>*必填*|状态码  <br>**样例** : `0`|integer (int32)|
|**desc**  <br>*可选*|状态描述  <br>**样例** : `"string"`|string|
|**result**  <br>*可选*|返回数据  <br>**样例** : `[ "[61f16ed3a104d14e18777d63d3d38c53](#61f16ed3a104d14e18777d63d3d38c53)" ]`|< [商品的存库与待发货数](#61f16ed3a104d14e18777d63d3d38c53) > array|
|**timestamp**  <br>*可选*|响应时间戳  <br>**样例** : `0`|integer (int64)|


<a name="aebb836524779bf4ac3a54ccb8344e2e"></a>
### 响应体«List«某个时间内商品的销售量与销售额»»

|名称|说明|类型|
|---|---|---|
|**code**  <br>*必填*|状态码  <br>**样例** : `0`|integer (int32)|
|**desc**  <br>*可选*|状态描述  <br>**样例** : `"string"`|string|
|**result**  <br>*可选*|返回数据  <br>**样例** : `[ "[e52e877e04cbe4739038e4a2f3406cc1](#e52e877e04cbe4739038e4a2f3406cc1)" ]`|< [某个时间内商品的销售量与销售额](#e52e877e04cbe4739038e4a2f3406cc1) > array|
|**timestamp**  <br>*可选*|响应时间戳  <br>**样例** : `0`|integer (int64)|


<a name="cfb221ddf0dca9fffaa481bcdf5c9aef"></a>
### 响应体«List«某个时间内某一种商品的销售量与销售额»»

|名称|说明|类型|
|---|---|---|
|**code**  <br>*必填*|状态码  <br>**样例** : `0`|integer (int32)|
|**desc**  <br>*可选*|状态描述  <br>**样例** : `"string"`|string|
|**result**  <br>*可选*|返回数据  <br>**样例** : `[ "[900f21f598e484fe615236de8a8e15f3](#900f21f598e484fe615236de8a8e15f3)" ]`|< [某个时间内某一种商品的销售量与销售额](#900f21f598e484fe615236de8a8e15f3) > array|
|**timestamp**  <br>*可选*|响应时间戳  <br>**样例** : `0`|integer (int64)|


<a name="74b4471f037d036851ef2e84df92b819"></a>
### 响应体«List«渠道预付款订单统计详情»»

|名称|说明|类型|
|---|---|---|
|**code**  <br>*必填*|状态码  <br>**样例** : `0`|integer (int32)|
|**desc**  <br>*可选*|状态描述  <br>**样例** : `"string"`|string|
|**result**  <br>*可选*|返回数据  <br>**样例** : `[ "[760591bfb351570dd3bc1ce434b44ee8](#760591bfb351570dd3bc1ce434b44ee8)" ]`|< [渠道预付款订单统计详情](#760591bfb351570dd3bc1ce434b44ee8) > array|
|**timestamp**  <br>*可选*|响应时间戳  <br>**样例** : `0`|integer (int64)|


<a name="ffdb961c8fc98065b580208fcebe1527"></a>
### 响应体«渠道预付款统计汇总»

|名称|说明|类型|
|---|---|---|
|**code**  <br>*必填*|状态码  <br>**样例** : `0`|integer (int32)|
|**desc**  <br>*可选*|状态描述  <br>**样例** : `"string"`|string|
|**result**  <br>*可选*|返回数据  <br>**样例** : `"[24667b16b4386ce548d58ba280809d4c](#24667b16b4386ce548d58ba280809d4c)"`|[渠道预付款统计汇总](#24667b16b4386ce548d58ba280809d4c)|
|**timestamp**  <br>*可选*|响应时间戳  <br>**样例** : `0`|integer (int64)|


<a name="61f16ed3a104d14e18777d63d3d38c53"></a>
### 商品的存库与待发货数

|名称|说明|类型|
|---|---|---|
|**name**  <br>*可选*|商品名称  <br>**样例** : `"string"`|string|
|**pending_count**  <br>*可选*|代发货数  <br>**样例** : `0`|integer (int32)|
|**stock**  <br>*可选*|库存数  <br>**样例** : `0`|integer (int32)|
|**type_name**  <br>*可选*|商品类型名称  <br>**样例** : `"string"`|string|


<a name="e52e877e04cbe4739038e4a2f3406cc1"></a>
### 某个时间内商品的销售量与销售额

|名称|说明|类型|
|---|---|---|
|**data_time**  <br>*可选*|x轴时间  <br>**样例** : `"string"`|string|
|**quantity**  <br>*可选*|y轴商品销售量  <br>**样例** : `"string"`|string|
|**sales**  <br>*可选*|y轴商品销售额  <br>**样例** : `"string"`|string|


<a name="900f21f598e484fe615236de8a8e15f3"></a>
### 某个时间内某一种商品的销售量与销售额

|名称|说明|类型|
|---|---|---|
|**name**  <br>*可选*|商品名称  <br>**样例** : `"string"`|string|
|**quantity**  <br>*可选*|商品销量  <br>**样例** : `0`|integer (int32)|
|**sales**  <br>*可选*|商品销额  <br>**样例** : `0`|integer (int64)|


<a name="24667b16b4386ce548d58ba280809d4c"></a>
### 渠道预付款统计汇总

|名称|说明|类型|
|---|---|---|
|**listData**  <br>*可选*|列表数据  <br>**样例** : `[ "[41878b656a79712e08a5e35f45061c92](#41878b656a79712e08a5e35f45061c92)" ]`|< [渠道预付款订单统计列表](#41878b656a79712e08a5e35f45061c92) > array|
|**totalData**  <br>*可选*|汇总数据  <br>**样例** : `"[channelpurchaseordertotaldto](#channelpurchaseordertotaldto)"`|[ChannelPurchaseOrderTotalDTO](#channelpurchaseordertotaldto)|


<a name="41878b656a79712e08a5e35f45061c92"></a>
### 渠道预付款订单统计列表

|名称|说明|类型|
|---|---|---|
|**dataTime**  <br>*可选*|数据时间  <br>**样例** : `"string"`|string|
|**orderFee**  <br>*可选*|提货金额  <br>**样例** : `0`|integer (int64)|
|**orderNum**  <br>*可选*|提货订单数  <br>**样例** : `0`|integer (int64)|
|**refundOrderFee**  <br>*可选*|退货退款额  <br>**样例** : `0`|integer (int64)|
|**refundOrderNum**  <br>*可选*|退货退款订单  <br>**样例** : `0`|integer (int64)|


<a name="760591bfb351570dd3bc1ce434b44ee8"></a>
### 渠道预付款订单统计详情

|名称|说明|类型|
|---|---|---|
|**channelId**  <br>*可选*|渠道ID  <br>**样例** : `0`|integer (int64)|
|**channelName**  <br>*可选*|门店名称  <br>**样例** : `"string"`|string|
|**orderFee**  <br>*可选*|提货金额  <br>**样例** : `0`|integer (int64)|
|**orderNum**  <br>*可选*|提货订单数  <br>**样例** : `0`|integer (int64)|
|**productNum**  <br>*可选*|商品数  <br>**样例** : `0`|integer (int64)|
|**rootChannel**  <br>*可选*|城市运营名称  <br>**样例** : `"string"`|string|
|**secondChannel**  <br>*可选*|经销商名称  <br>**样例** : `"string"`|string|





