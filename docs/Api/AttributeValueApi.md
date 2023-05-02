# Swagger\Client\AttributeValueApi

All URIs are relative to *http://orion.lab.fiware.org*

Method | HTTP request | Description
------------- | ------------- | -------------
[**getAttributeValue**](AttributeValueApi.md#getAttributeValue) | **GET** /v2/entities/{entityId}/attrs/{attrName}/value | Get Attribute Value
[**updateAttributeValue**](AttributeValueApi.md#updateAttributeValue) | **PUT** /v2/entities/{entityId}/attrs/{attrName}/value | Update Attribute Value


# **getAttributeValue**
> \Swagger\Client\Model\GetAttributeValueResponse getAttributeValue($entity_id, $attr_name, $type)

Get Attribute Value

This operation returns the `value` property with the value of the attribute. * If attribute value is JSON Array or Object:   * If `Accept` header can be expanded to `application/json` or `text/plain` return the value as a JSON with a     response type of application/json or text/plain (whichever is the first in `Accept` header or     `application/json` in case of `Accept: *_/_*`).   * Else return a HTTP error \"406 Not Acceptable: accepted MIME types: application/json, text/plain\" * If attribute value is a string, number, null or boolean:   * If `Accept` header can be expanded to text/plain return the value as text. In case of a string, citation     marks are used at the begining and end.   * Else return a HTTP error \"406 Not Acceptable: accepted MIME types: text/plain\" Response: * Successful operation uses 200 OK. * Errors use a non-2xx and (optionally) an error payload. See subsection on \"Error Responses\" for   more details.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Swagger\Client\Api\AttributeValueApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$entity_id = "entity_id_example"; // string | Id of the entity in question
$attr_name = "attr_name_example"; // string | Name of the attribute to be retrieved.
$type = "type_example"; // string | Entity type, to avoid ambiguity in case there are several entities with the same entity id.

try {
    $result = $apiInstance->getAttributeValue($entity_id, $attr_name, $type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AttributeValueApi->getAttributeValue: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **entity_id** | **string**| Id of the entity in question |
 **attr_name** | **string**| Name of the attribute to be retrieved. |
 **type** | **string**| Entity type, to avoid ambiguity in case there are several entities with the same entity id. | [optional]

### Return type

[**\Swagger\Client\Model\GetAttributeValueResponse**](../Model/GetAttributeValueResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **updateAttributeValue**
> updateAttributeValue($entity_id, $attr_name, $content_type, $body, $type)

Update Attribute Value

The request payload is the new attribute value. * If the request payload MIME type is `application/json`, then the value of the attribute is set to   the JSON object or array coded in the payload (if the payload is not a valid JSON document,   then an error is returned). * If the request payload MIME type is `text/plain`, then the following algorithm is applied to the   payload:   * If the payload starts and ends with citation-marks (`\"`), the value is taken as a string     (the citation marks themselves are not considered part of the string)   * If `true` or `false`, the value is taken as a boolean.   * If `null`, the value is taken as null.   * If these first three tests 'fail', the text is interpreted as a number.   * If not a valid number, then an error is returned and the attribute's value is unchanged. The payload MIME type in the request is specified in the `Content-Type` HTTP header. Response: * Successful operation uses 204 No Content * Errors use a non-2xx and (optionally) an error payload. See subsection on \"Error Responses\" for   more details.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Swagger\Client\Api\AttributeValueApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$entity_id = "entity_id_example"; // string | Id of the entity to be updated.
$attr_name = "attr_name_example"; // string | Attribute name.
$content_type = "content_type_example"; // string | 
$body = new \Swagger\Client\Model\UpdateAttributeValueRequest(); // \Swagger\Client\Model\UpdateAttributeValueRequest | 
$type = "type_example"; // string | Entity type, to avoid ambiguity in case there are several entities with the same entity id.

try {
    $apiInstance->updateAttributeValue($entity_id, $attr_name, $content_type, $body, $type);
} catch (Exception $e) {
    echo 'Exception when calling AttributeValueApi->updateAttributeValue: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **entity_id** | **string**| Id of the entity to be updated. |
 **attr_name** | **string**| Attribute name. |
 **content_type** | **string**|  |
 **body** | [**\Swagger\Client\Model\UpdateAttributeValueRequest**](../Model/UpdateAttributeValueRequest.md)|  |
 **type** | **string**| Entity type, to avoid ambiguity in case there are several entities with the same entity id. | [optional]

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

