# List Bucket

You can use JingdongStorageService.listBuckets to list all Buckets under designated users, the following codes show how to list designated users’ Bucket lists by simple methods:
```
// endpoint以华北-北京为例，其它region请按实际情况填写  
String endpoint = "oss.cn-north-1.jcloudcs.com";  
//您的AccessKey和SecretKey可以登录到对象存储的控制台，在【Access Key 管理】中查看。  
String accessKey = "<yourAccessKey>";  
String SecretKey = "<yourSecretKey>";  
  
// 创建JingdongStorageService实例  
Credential credential = new Credential(accessKey, secreteKey);  
//默认配置文件。如用户需要个别配置，则自行配置。例:config.setMaxConnections(20);  
ClientConfig config = new ClientConfig();  
JingdongStorageService jss= new JingdongStorageService (credential, config);  
//设置Endpoint  
jss.setEndpoint(endpoint);  
      
// 列举bucket  
List<Bucket> buckets = jss.listBucket();  
for (Bucket bucket : buckets) {  
    System.out.println(" - " + bucket.getName());  
}  
// 关闭jss  
jss.destroy();
```
