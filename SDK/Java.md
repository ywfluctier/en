
# Introduction #

Welcome to the JD Cloud Developer Java Tools Kit (Java SDK). With JD Cloud Java SDK, you can access the services provided by JD Cloud without complex programming. 

To conveniently understand the meaning of some of the concepts and parameters in the SDK, we recommend that you review the OpenAPI to use the Getting Started document before using the SDK. To understand the specific parameters and meanings of each API, refer to the program comments or documentation for specific product lines under OpenAPI&SDK.


# Environment Preparation #

1.     The JD Cloud Java SDK is applicable to jdk7 and above versions.

2.     To apply the accesskey and the secretKey r (AK/ SK) in advance in the AccessKey Management page under the Account Management of JD Cloud User Center before starting to call the JD Cloud open API. AK/ SK information shall be kept properly and if lost, it is likely to cause illegal users to use this information to operate your resources on the cloud, resulting data or property losses.



# SDK usage method #

If you use Apache Maven to manage a Java project, you only need to add a corresponding dependency in the pom.xml file of the project, as follows:

<dependency>
    <groupId>com.jdcloud.sdk</groupId>
    <artifactId>core</artifactId>
    <version>1.0.0</version>
</dependency>
<!-- SDK of corresponding product line -->
<dependency>
    <groupId>com.jdcloud.sdk</groupId>
    <artifactId>vm</artifactId>
    <version>0.6.1</version>
</dependency>
You can also download the SDK source code yourself. The source code address is: [Java SDK](https://github.com/jdcloud-api/jdcloud-sdk-java).

With any of the problems in the SDK use, you are welcomed to communicate with the Github project [SDK Use Problem Feedback page](https://github.com/jdcloud-api/jdcloud-sdk-java/issues).

Note: JD Cloud does not provide other downloading ways, please be sure to use the above-mentioned official download method!

 

# Call SDK #

The calling of the Java SDK is mainly divided into four steps:

 1. Set accessKey and secretKey

 2. Create Client

 3. Set Request Parameters

 4. Response to implementation requests

The following is an example of a call to query details for individual VM Instance

	import com.jdcloud.sdk.JdcloudSdkException;
	import com.jdcloud.sdk.auth.CredentialsProvider;
	import com.jdcloud.sdk.auth.StaticCredentialsProvider;
	import com.jdcloud.sdk.http.HttpRequestConfig;
	import com.jdcloud.sdk.http.Protocol;
	import com.jdcloud.sdk.service.vm.client.VmClient;
	import com.jdcloud.sdk.service.vm.model.*;
	
	public class VmClientExample {

	    public static void main(String[] args) {
	        // 1. Set accessKey and securKey
	        String accessKeyId = "{accessKey}";
	        String secretAccessKey = "{secretKey}";
	        CredentialsProvider credentialsProvider = new StaticCredentialsProvider(accessKeyId, secretAccessKey);

	        // 2. Creating XXXClient
	        VmClient vmClient = VmClient.builder()
	                .credentialsProvider(credentialsProvider)
	                . httpRequestConfig(new HttpRequestConfig.Builder().protocol(Protocol.HTTPS).build()) // is default as HTTPS
	                .build();

	        // 3. Set Request Parameters
	        DescribeInstanceRequest request = new DescribeInstanceRequest();
	        request.regionId("cn-north-1");
	        request.instanceId("i-c0se9uju");

	        // 4. Execution Requests
	        try {
	            DescribeInstanceResponse response = vmClient.describeInstance(request);

	            // Return business error
	            if(response.getError() != null) {
	                // call the API to return business errors, error handling
	                System.out.println(response.getRequestId() + " failed: " + response.getError().getMessage());
	                return;
	            }

	            DescribeInstanceResult result = response.getResult();
	            // 5. Normal return to result and follow-up processing using the return data
            
 	       }catch (JdcloudSdkException jse) {
	            // call API failed, error handling
 	       }
	    }
	}


If you need to set up an additional header, for example to call an interface that opens the MFA operation protection, you need to pass x-jdcloud-security-token, as follows:

	vmClient.setCustomHeader("x-jdcloud-security-token", "xxxx");