# Dounasth\Ngsiv2\BatchOperationsApi

All URIs are relative to *http://orion.lab.fiware.org*

Method | HTTP request | Description
------------- | ------------- | -------------
[**notify**](BatchOperationsApi.md#notify) | **POST** /v2/op/notify | Notify
[**query**](BatchOperationsApi.md#query) | **POST** /v2/op/query | Query
[**update**](BatchOperationsApi.md#update) | **POST** /v2/op/update | Update


# **notify**
> notify($content_type, $body, $options)

Notify

This operation is intended to consume a notification payload so that all the entity data included by such notification is persisted, overwriting if necessary. This operation is useful when one NGSIv2 endpoint is subscribed to another NGSIv2 endpoint (federation scenarios).  The request payload must be an NGSIv2 notification payload.  The behaviour must be exactly the same as `POST /v2/op/update` with `actionType` equal to `append`. Response code: * Successful operation uses 200 OK * Errors use a non-2xx and (optionally) an error payload. See subsection on \"Error Responses\" for   more details.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Dounasth\Ngsiv2\Api\BatchOperationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$content_type = "content_type_example"; // string | 
$body = new \Dounasth\Ngsiv2\Model\NotifyRequest(); // \Dounasth\Ngsiv2\Model\NotifyRequest | 
$options = "options_example"; // string | Options dictionary

try {
    $apiInstance->notify($content_type, $body, $options);
} catch (Exception $e) {
    echo 'Exception when calling BatchOperationsApi->notify: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **content_type** | **string**|  |
 **body** | [**\Dounasth\Ngsiv2\Model\NotifyRequest**](../Model/NotifyRequest.md)|  |
 **options** | **string**| Options dictionary | [optional]

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **query**
> \Dounasth\Ngsiv2\Model\QueryResponse[] query($content_type, $body, $limit, $offset, $order_by, $options)

Query

The response payload is an Array containing one object per matching entity, or an empty array `[]` if  no entities are found. The entities follow the JSON entity representation format (described in the section \"JSON Entity Representation\"). The payload may contain the following elements (all of them optional): + `entities`: a list of entites to search for. Each element is represented by a JSON object with the   following elements:     + `id` or `idPattern`: Id or pattern of the affected entities. Both cannot be used at the same       time, but one of them must be present.     + `type` or `typePattern`: Type or type pattern of the entities to search for. Both cannot be used at       the same time. If omitted, it means \"any entity type\". + `attrs`: List of attributes to be provided (if not specified, all attributes). + `expression`: an expression composed of `q`, `mq`, `georel`, `geometry` and `coords` (see \"List    entities\" operation above about this field). + `metadata`: a list of metadata names to include in the response.    See \"Filtering out attributes and metadata\" section for more detail. Response code: * Successful operation uses 200 OK * Errors use a non-2xx and (optionally) an error payload. See subsection on \"Error Responses\" for   more details.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Dounasth\Ngsiv2\Api\BatchOperationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$content_type = "content_type_example"; // string | 
$body = new \Dounasth\Ngsiv2\Model\QueryRequest(); // \Dounasth\Ngsiv2\Model\QueryRequest | 
$limit = 1.2; // double | Limit the number of entities to be retrieved.
$offset = 1.2; // double | Skip a number of records.
$order_by = "order_by_example"; // string | Criteria for ordering results. See \"Ordering Results\" section for details.
$options = "options_example"; // string | Options dictionary

try {
    $result = $apiInstance->query($content_type, $body, $limit, $offset, $order_by, $options);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BatchOperationsApi->query: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **content_type** | **string**|  |
 **body** | [**\Dounasth\Ngsiv2\Model\QueryRequest**](../Model/QueryRequest.md)|  |
 **limit** | **double**| Limit the number of entities to be retrieved. | [optional]
 **offset** | **double**| Skip a number of records. | [optional]
 **order_by** | **string**| Criteria for ordering results. See \&quot;Ordering Results\&quot; section for details. | [optional]
 **options** | **string**| Options dictionary | [optional]

### Return type

[**\Dounasth\Ngsiv2\Model\QueryResponse[]**](../Model/QueryResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **update**
> update($content_type, $body, $options)

Update

This operation allows to create, update and/or delete several entities in a single batch operation. The payload is an object with two properties: + `actionType`, to specify the kind of update action to do: either `append`, `appendStrict`, `update`,   `delete`, or `replace`. + `entities`, an array of entities, each entity specified using the JSON entity representation format   (described in the section \"JSON Entity Representation\"). This operation is split in as many individual operations as entities in the `entities` vector, so the `actionType` is executed for each one of them. Depending on the `actionType`, a mapping with regular non-batch operations can be done: * `append`: maps to `POST /v2/entities` (if the entity does not already exist) or `POST /v2/entities/<id>/attrs`   (if the entity already exists). * `appendStrict`: maps to `POST /v2/entities` (if the entity does not already exist) or   `POST /v2/entities/<id>/attrs?options=append` (if the entity already exists). * `update`: maps to `PATCH /v2/entities/<id>/attrs`. * `delete`: maps to `DELETE /v2/entities/<id>/attrs/<attrName>` on every attribute included in the entity or   to `DELETE /v2/entities/<id>` if no attribute were included in the entity. * `replace`: maps to `PUT /v2/entities/<id>/attrs`. Response: * Successful operation uses 204 No Content. * Errors use a non-2xx and (optionally) an error payload. See subsection on \"Error Responses\" for   more details.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Dounasth\Ngsiv2\Api\BatchOperationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$content_type = "content_type_example"; // string | 
$body = new \Dounasth\Ngsiv2\Model\UpdateRequest(); // \Dounasth\Ngsiv2\Model\UpdateRequest | 
$options = "options_example"; // string | Options dictionary

try {
    $apiInstance->update($content_type, $body, $options);
} catch (Exception $e) {
    echo 'Exception when calling BatchOperationsApi->update: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **content_type** | **string**|  |
 **body** | [**\Dounasth\Ngsiv2\Model\UpdateRequest**](../Model/UpdateRequest.md)|  |
 **options** | **string**| Options dictionary | [optional]

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

