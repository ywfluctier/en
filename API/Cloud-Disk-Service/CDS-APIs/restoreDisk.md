# restoreDisk


## 描述
-   Data recovery operations can only be executed on the source hard disk, from which the snapshot was taken.
-   Snapshots can be used for data recovery operations only if the source hard disk is available.
-   After the cloud disk service is restored, the current data will be cleared. Please be cautious.


## 请求方式
POST

## 请求地址
https://disk.jdcloud-api.com/v1/regions/{regionId}/disks/{diskId}:restore

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**diskId**|String|True||Cloud Disk Service ID|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**snapshotId**|String|True||Snapshot ID used to recover the cloud disk|


## 返回参数
|名称|类型|描述|
|---|---|---|



## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|