# describeIndexPerformance


## 描述
Obtain statistics on index performance based on user-defined query conditions, and provide missing indexes and suggestions for index creation. Users can use these information to find index-related performance bottlenecks and optimize them. <br>- Support SQL Server Only

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/performance:describeIndexPerformance

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True||RDS instance ID, which uniquely identifies an RDS instance|
|**regionId**|String|True||Region code, with range detailed in [Regions and Availability Zone Comparison Table](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**db**|String|False||Multiple names of the database to be queried are separated by commas and all databases are by default.|
|**pageNumber**|Integer|False||The default of the page number of the data displayed is 1 and the value range is [-1,1000). When pageNumber is -1, return all data page numbers; when the total number of pages is exceeded, display the last page.|
|**pageSize**|Integer|False||The default of the number of data displayed per page is 50 and the value range is [1,100]. It can only be a multiple of 10 used for the interface to query the list.|
|**queryType**|String|True||查询类型，不同的查询类型按照相应的字段从高到低返回结果。<br>支持如下类型：<br>Missing：缺失索引<br>Size：索引大小，单位KB<br>Updates：索引更新次数<br>Scans：表扫描次数<br>Used：最少使用<br>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**indexPerformanceResult**|[IndexPerformanceResult[]](##IndexPerformanceResult)|When the queryType is Missing, the field is empty <br>when the queryType is other values, return IndexPerformanceResult|
|**missingIndexResult**|[MissingIndexResult[]](##MissingIndexResult)|When queryType is Missing, the result set is MissingIndexResult<br>when queryType is other values, the field is null.|
|**pageNumber**|Integer|The Page Number of the Current Data|
|**pageSize**|Integer|The Number of Data Displayed Per Page|
|**totalCount**|Integer|Total Number of Records|
### <a name="IndexPerformanceResult">IndexPerformanceResult</a>
|名称|类型|描述|
|---|---|---|
|**db**|String|Database Name|
|**index**|String|Index Name|
|**lastUserScan**|String|The most recent table scan time, format: YYYY-MM-DD hh:mm:ss|
|**lastUserSeek**|String|Last index search time, format YYYY-MM-DD hh:mm:ss|
|**lastUserUpdate**|String|The most recent index update time, format: YYYY-MM-DD hh:mm:ss|
|**sizeKB**|Integer|Index Size in KB|
|**table**|String|Table Name|
|**userScans**|Integer|Cumulative number of table scans since the server was started|
|**userSeeks**|Integer|Cumulative index search times since the server was started|
|**userUpdates**|Integer|Cumulative number of index updates since the server was started|
### <a name="MissingIndexResult">MissingIndexResult</a>
|名称|类型|描述|
|---|---|---|
|**avgUserImpact**|Number|The average percentage gain that the user may get during query after implementing this missing index. This value indicates that if this missing index is implemented, the query cost will decrease by this percentage on average.|
|**db**|String|Database Name|
|**equalityColumns**|String|A comma-separated list of columns that make up the equality predicate. The form of the predicate is as follows: <br>table.column =constant_value|
|**includedColumns**|String|A comma-separated list of columns that make up the unequal predicate. The predicate may take the following form:<br>table.column > constant_value<br> Any comparison operator other than "=" indicates they are unequal.|
|**inequalityColumns**|String|A comma-separated list of the covered columns for the query, i.e., the fields following Include in the SQL statement that created the index|
|**table**|String|Table Name|
|**userScans**|Integer|Number of scans caused by the query of a user that might have used the suggested index in the group.|
|**userSeeks**|Integer||

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
