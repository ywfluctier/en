# describeInstanceAttributes


## 描述
Query the details of the RDS instance (MySQL, SQL Server, etc.) and the MySQL read-only instance details

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True||RDS instance ID, which uniquely identifies an RDS instance|
|**regionId**|String|True||Region code, with range detailed in [Regions and Availability Zone Comparison Table](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**dbInstanceAttributes**|[DBInstanceAttribute](##DBInstanceAttribute)||
### <a name="DBInstanceAttribute">DBInstanceAttribute</a>
|名称|类型|描述|
|---|---|---|
|**auditStatus**|String|Audit status, detailed in [Enumeration Parameter Definition](../Enum-Definitions/Enum-Definitions.md)|
|**azId**|String[]|AZ ID, the first is AZ for the primary instance, which is detailed in [Regions and Availability Zone Comparison Table](../Enum-Definitions/Regions-AZ.md)|
|**charge**|[Charge](##Charge)|Billing Configuration|
|**connectionMode**|String|Access mode, detailed in [Enumeration Parameter Definition](../Enum-Definitions/Enum-Definitions.md)|
|**createTime**|String|Instance Creation Time|
|**engine**|String|Instance engine type, such as MySQL or SQL Server, etc., detailed in [Enumeration Parameter Definition](../Enum-Definitions/Enum-Definitions.md)|
|**engineVersion**|String|Instance engine version, detailed in [Enumeration Parameter Definition](../Enum-Definitions/Enum-Definitions.md)|
|**instanceCPU**|Integer|Number of CPU Cores|
|**instanceClass**|String|Instance Type Code|
|**instanceId**|String|Instance ID|
|**instanceMemoryMB**|Integer|Memory Size in MB|
|**instanceName**|String|Instance name with specific rules detailed in the Help Center Documentation: [Name and Password Restrictions](../../../documentation/Cloud-Database-and-Cache/RDS/Introduction/Restrictions/SQLServer-Restrictions.md)|
|**instancePort**|String|Application Access Port|
|**instanceStatus**|String|Instance status, detailed in [Enumeration Parameter Definition](../Enum-Definitions/Enum-Definitions.md)|
|**instanceStorageGB**|Integer|Disk, in GB|
|**instanceType**|String|Instance type, such as primary instances, read-only instances, etc., detailed in [Enumeration Parameter Definition](../Enum-Definitions/Enum-Definitions.md)|
|**internalDomainName**|String|Instance Public Network Domain Name|
|**publicDomainName**|String|Instance Intranet Domain Name|
|**regionId**|String|Region ID, detailed in [Regions and Availability Zone Comparison Table](../Enum-Definitions/Regions-AZ.md)|
|**subnetId**|String|Subnet ID|
|**vpcId**|String|VPC ID|
### <a name="Charge">Charge</a>
|名称|类型|描述|
|---|---|---|
|**chargeExpiredTime**|String|Expiration time, i.e. the expiration time of Pay-In-Advance resource, which shall be subject to ISO8601, with the UTC time used in the format of YYYY-MM-DDTHH:mm:ssZ. Pay-As-You-Go resource field is blank.|
|**chargeMode**|String|Payment model, the value shall be prepaid_by_duration, postpaid_by_usage or postpaid_by_duration; prepaid_by_duration refers to Pay-In-Advance; postpaid_by_usage refers to Pay By Consumption and Pay-As-You-Go; postpaid_by_duration refers to Pay By Configuration and Pay-As-You-Go, and is postpaid_by_duration by default|
|**chargeRetireTime**|String|The expected release time refers to the expected release time of resources. This value is both available for the Pay-In-Advance/Pay-As-You-Go resources, conforming to the ISO8601 standard, with the UTC time used in the format of YYYY-MM-DDTHH:mm:ssZ|
|**chargeStartTime**|String|The start time of the billing shall be subject to ISO8601, with the UTC time used in the format of YYYY-MM-DDTHH:mm:ssZ|
|**chargeStatus**|String|Cost payment status, the value is respectively normal, overdue and arrear.|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
