# createInstance


## 描述
Create an RDS instance and the user can use the corresponding database client or application to link to the RDS instance through the domain name and port to operate.

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||Region code, with range detailed in [Regions and Availability Zone Comparison Table](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceSpec**|[DBInstanceSpec](##DBInstanceSpec)|True||New Instance Type Created|

### <a name="DBInstanceSpec">DBInstanceSpec</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**azId**|String[]|True||AZ ID, the first ID must be AZ where the primary instance is located. If the two AZs are the same, you also need to enter two azIds.|
|**chargeSpec**|[ChargeSpec](##ChargeSpec)|True||Billing specification, including billing type, billing period, etc.|
|**engine**|String|True||Instance engine type, detailed in [Enumeration Parameter Definition](../Enum-Definitions/Enum-Definitions.md)|
|**engineVersion**|String|True||Instance engine version, detailed in [Enumeration Parameter Definition](../Enum-Definitions/Enum-Definitions.md)|
|**instanceClass**|String|True||Instance type code, which can be obtained through [describeInstanceClasses](../instance/describeInstanceClasses.md) interface|
|**instanceName**|String|False||Instance name with specific rules detailed in the Help Center Documentation: [Name and Password Restrictions](../../../documentation/Cloud-Database-and-Cache/RDS/Introduction/Restrictions/SQLServer-Restrictions.md)|
|**instanceStorageGB**|Integer|True||Disk Size, in GB|
|**subnetId**|String|True||Subnet ID|
|**vpcId**|String|True||VPC ID|
### <a name="ChargeSpec">ChargeSpec</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**chargeDuration**|Integer|False||Pay-In-Advance billing duration, the Pay-In-Advance is compulsory and valid only when the value of chargeMode is prepaid_by_duration. When chargeUnit is month, the value shall be 1~9; when chargeUnit is year, the value shall be 1, 2 or 3|
|**chargeMode**|String|False|postpaid_by_duration|Billing model value is prepaid_by_duration, postpaid_by_usage or postpaid_by_duration; prepaid_by_duration means Pay-In-Advance, postpaid_by_usage means Pay-As-You-Go By Consumption and postpaid_by_duration means pay by configuration; is postpaid_by_duration by default. Please refer to the Help Documentation of specific product line to confirm the billing type supported by the production line|
|**chargeUnit**|String|False||Billing unit of Pay-In-Advance, the Pay-In-Advance is compulsory, and valid only when chargeMode is prepaid_by_duration, and the value is month or year and month by default|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**instanceId**|String||

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
