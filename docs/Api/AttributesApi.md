# Swagger\Client\AttributesApi

All URIs are relative to *http://orion.lab.fiware.org*

Method | HTTP request | Description
------------- | ------------- | -------------
[**getAttributeData**](AttributesApi.md#getAttributeData) | **GET** /v2/entities/{entityId}/attrs/{attrName} | Get attribute data
[**removeASingleAttribute**](AttributesApi.md#removeASingleAttribute) | **DELETE** /v2/entities/{entityId}/attrs/{attrName} | Remove a Single Attribute
[**updateAttributeData**](AttributesApi.md#updateAttributeData) | **PUT** /v2/entities/{entityId}/attrs/{attrName} | Update Attribute Data


# **getAttributeData**
> \Swagger\Client\Model\GetAttributeDataResponse getAttributeData($entity_id, $attr_name, $type, $metadata)

Get attribute data

Returns a JSON object with the attribute data of the attribute. The object follows the JSON representation for attributes (described in \"JSON Attribute Representation\" section). Response: * Successful operation uses 200 OK. * Errors use a non-2xx and (optionally) an error payload. See subsection on \"Error Responses\" for   more details.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Swagger\Client\Api\AttributesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$entity_id = "entity_id_example"; // string | Id of the entity
$attr_name = "attr_name_example"; // string | Name of the attribute to be retrieved.
$type = "type_example"; // string | Entity type, to avoid ambiguity in case there are several entities with the same entity id.
$metadata = "metadata_example"; // string | A list of metadata names to include in the response. See \"Filtering out attributes and metadata\" section for more detail.

try {
    $result = $apiInstance->getAttributeData($entity_id, $attr_name, $type, $metadata);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AttributesApi->getAttributeData: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **entity_id** | **string**| Id of the entity |
 **attr_name** | **string**| Name of the attribute to be retrieved. |
 **type** | **string**| Entity type, to avoid ambiguity in case there are several entities with the same entity id. | [optional]
 **metadata** | **string**| A list of metadata names to include in the response. See \&quot;Filtering out attributes and metadata\&quot; section for more detail. | [optional]

### Return type

[**\Swagger\Client\Model\GetAttributeDataResponse**](../Model/GetAttributeDataResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **removeASingleAttribute**
> removeASingleAttribute($entity_id, $attr_name, $type)

Remove a Single Attribute

Removes an entity attribute. Response: * Successful operation uses 204 No Content * Errors use a non-2xx and (optionally) an error payload. See subsection on \"Error Responses\" for   more details.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Swagger\Client\Api\AttributesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$entity_id = "entity_id_example"; // string | Id of the entity.
$attr_name = "attr_name_example"; // string | Attribute name.
$type = "type_example"; // string | Entity type, to avoid ambiguity in case there are several entities with the same entity id.

try {
    $apiInstance->removeASingleAttribute($entity_id, $attr_name, $type);
} catch (Exception $e) {
    echo 'Exception when calling AttributesApi->removeASingleAttribute: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **entity_id** | **string**| Id of the entity. |
 **attr_name** | **string**| Attribute name. |
 **type** | **string**| Entity type, to avoid ambiguity in case there are several entities with the same entity id. | [optional]

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **updateAttributeData**
> updateAttributeData($entity_id, $attr_name, $content_type, $body, $type)

Update Attribute Data

The request payload is an object representing the new attribute data. Previous attribute data is replaced by the one in the request. The object follows the JSON representation for attributes (described in \"JSON Attribute Representation\" section). Response: * Successful operation uses 204 No Content * Errors use a non-2xx and (optionally) an error payload. See subsection on \"Error Responses\" for   more details.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Swagger\Client\Api\AttributesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$entity_id = "entity_id_example"; // string | Id of the entity to update
$attr_name = "attr_name_example"; // string | Attribute name
$content_type = "content_type_example"; // string | 
$body = new \Swagger\Client\Model\UpdateAttributeDataRequest(); // \Swagger\Client\Model\UpdateAttributeDataRequest | 
$type = "type_example"; // string | Entity type, to avoid ambiguity in case there are several entities with the same entity id.

try {
    $apiInstance->updateAttributeData($entity_id, $attr_name, $content_type, $body, $type);
} catch (Exception $e) {
    echo 'Exception when calling AttributesApi->updateAttributeData: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **entity_id** | **string**| Id of the entity to update |
 **attr_name** | **string**| Attribute name |
 **content_type** | **string**|  |
 **body** | [**\Swagger\Client\Model\UpdateAttributeDataRequest**](../Model/UpdateAttributeDataRequest.md)|  |
 **type** | **string**| Entity type, to avoid ambiguity in case there are several entities with the same entity id. | [optional]

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

