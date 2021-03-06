# putMetricData


## 描述
The interface is the interface for customized metric monitoring data reporting, which is convenient for you to report the time series data collected by yourself to the Cloud Monitor. It can report original data and aggregated statistical data. It supports reporting methods in batches. A single request contains up to 50 data points; the data size does not exceed 256k.

## 请求方式
POST

## 请求地址
https://monitor.{regionId}.jdcloud-api.com/v1/customMetrics

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**metricDataList**|[MetricDataCm[]](##MetricDataCm)|False||Data parameter|

### <a name="MetricDataCm">MetricDataCm</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dimensions**|Object|True||Data dimension, data type is map type, support at least one, up to five tags, no more than 255 bytes in total length, only English, numbers, underlines_, dot., [0-9][a-z] [A-Z] [. _ ] are allowed, others will return err|
|**metric**|String|True||Monitoring indicator name, no more than 255 bytes in length, only English, numbers, underlines_, dot., [0-9][a-z] [A-Z] [. _ ] are allowed, others will return err|
|**namespace**|String|True||Naming space, no more than 255 bytes in length, only English, numbers, underlines_, dot., [0-9][a-z] [A-Z] [. _ ] are allowed, others will return err|
|**timestamp**|Integer|True||Time stamp for reporting data points only supports 10-bit, second-level time stamp, the time of the past 30 days cannot be written in|
|**type**|Integer|True||Data reporting type, 1 is the original value, 2 is aggregated data. When the aggregated data is reported, it is suggested that it shall be reported during the period of 60s, otherwise, it cannot be queried normally.|
|**values**|Object|True||Indicator value collection, the data type must be the map type, key is the data type, value is the data value, when type=1, key only can be “value”, the reported is the original value, when type=2, key can be "avg”, "sum”, "last”, "max”, "min”, “count”, which only support the above types, otherwise it will report an error, value contents are integers or floating point numbers, the largest value is 9223372036854775807, count only supports numbers >=0|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**error**|Object|Error information|
|**requestId**|String|Requested identifier id|
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**errMetricDataList**|[MetricDataList[]](##MetricDataList)||
|**success**|Boolean|All successful write-ins are true, or false|
### <a name="MetricDataList">MetricDataList</a>
|名称|类型|描述|
|---|---|---|
|**errDetail**|String|Error data description|
|**errMetricData**|String|Error data|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|invalid parameter|
|**500**|internal server error|
|**429**|quota exceed|
