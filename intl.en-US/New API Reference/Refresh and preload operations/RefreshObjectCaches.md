# RefreshObjectCaches

Refreshes files on Alibaba Cloud Content Delivery Network \(CDN\) nodes. After files are refreshed, the original file content immediately becomes invalid. If clients request the original file content, Alibaba Cloud CDN redirects the requests to the origin server of the content. Then, Alibaba Cloud CDN caches the latest content to CND nodes and returns it to the clients. Alibaba Cloud CDN allows you to refresh content from multiple URLs at a time.

**Note:**

-   Alibaba Cloud CDN supports POST requests in which parameters are sent as a form.
-   You can call the **RefreshObjectCaches** operation to refresh content and call the **PushObjectCache** operation to prefetch content.
-   You can refresh content from a maximum of 2,000 URLs and 100 directories per day with each Alibaba Cloud account. Subdirectories are also refreshed.
-   You can specify a maximum of 1,000 URLs in each refresh request.
-   You can specify a maximum of 1,000 URLs per minute for a single accelerated domain name.
-   The maximum number of times that each user can call this operation per second is 50.
-   For more information about how to automate refresh or prefetch tasks, see [Prefetch and refresh task scripts](~~151829~~).

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Cdn&api=RefreshObjectCaches&type=RPC&version=2018-05-10)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|RefreshObjectCaches|The operation that you want to perform. Set the value to **RefreshObjectCaches**. |
|ObjectPath|String|Yes|abc.com/image/1.png\\nabc.com/image/2.png|The URLs from which content is refreshed. Format: **accelerated domain name/paths or directories of files to be refreshed**.

 Separate multiple URLs with line feed characters \(\\n\) or a pair of carriage return and line feed characters \(\\r\\n\). |
|ObjectType|String|No|File|The type of content to be refreshed. Valid values:

 -   **File**: a file.
-   **Directory**: the files under the specified directory.

 Default value: **File**. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RefreshTaskId|String|704222904|The ID of the refresh task. If multiple tasks are returned, the IDs are separated with commas \(,\). |
|RequestId|String|D61E4801-EAFF-4A63-AAE1-FBF6CE1CFD1C|The ID of the request. |

## Examples

Sample requests

```
http(s)://cdn.aliyuncs.com/? Action=RefreshObjectCaches
&ObjectPath=abc.com/image/1.png\nabc.com/image/2.png
&ObjectType=File
&<Common request parameters>
```

Sample success responses

`XML` format

```
<RefreshObjectCachesResponse>
  <RefreshTaskId>704222904</RefreshTaskId>
  <RequestId>D61E4801-EAFF-4A63-AAE1-FBF6CE1CFD1C</RequestId>
</RefreshObjectCachesResponse>
```

`JSON` format

```
{
"RefreshTaskId":"704222904",
"RequestId":"D61E4801-EAFF-4A63-AAE1-FBF6CE1CFD1C"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Cdn).

