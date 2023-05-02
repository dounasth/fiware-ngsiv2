# Swagger\Client\TypesApi

All URIs are relative to *http://orion.lab.fiware.org*

Method | HTTP request | Description
------------- | ------------- | -------------
[**listEntityTypes**](TypesApi.md#listEntityTypes) | **GET** /v2/types/ | List Entity Types
[**retrieveEntityType**](TypesApi.md#retrieveEntityType) | **GET** /v2/types/{entityType} | Retrieve entity type


# **listEntityTypes**
> \Swagger\Client\Model\ListEntityTypesResponse[] listEntityTypes($limit, $offset, $options)

List Entity Types

If the `values` option is not in use, this operation returns a JSON array with the entity types. Each element is a JSON object with information about the type: * `type` : the entity type name. * `attrs` : the set of attribute names along with all the entities of such type, represented in   a JSON object whose keys are the attribute names and whose values contain information of such   attributes (in particular a list of the types used by attributes with that name along with all the   entities). * `count` : the number of entities belonging to that type. If the `values` option is used, the operation returns a JSON array with a list of entity type names as strings. Results are ordered by entity `type` in alphabetical order. Response code: * Successful operation uses 200 OK * Errors use a non-2xx and (optionally) an error payload. See subsection on \"Error Responses\" for   more details.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Swagger\Client\Api\TypesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$limit = 1.2; // double | Limit the number of types to be retrieved.
$offset = 1.2; // double | Skip a number of records.
$options = "options_example"; // string | Options dictionary.

try {
    $result = $apiInstance->listEntityTypes($limit, $offset, $options);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling TypesApi->listEntityTypes: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **limit** | **double**| Limit the number of types to be retrieved. | [optional]
 **offset** | **double**| Skip a number of records. | [optional]
 **options** | **string**| Options dictionary. | [optional]

### Return type

[**\Swagger\Client\Model\ListEntityTypesResponse[]**](../Model/ListEntityTypesResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **retrieveEntityType**
> \Swagger\Client\Model\RetrieveEntityTypeResponse retrieveEntityType($entity_type)

Retrieve entity type

This operation returns a JSON object with information about the type: * `attrs` : the set of attribute names along with all the entities of such type, represented in   a JSON object whose keys are the attribute names and whose values contain information of such   attributes (in particular a list of the types used by attributes with that name along with all the   entities). * `count` : the number of entities belonging to that type. Response code: * Successful operation uses 200 OK * Errors use a non-2xx and (optionally) an error payload. See subsection on \"Error Responses\" for   more details.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Swagger\Client\Api\TypesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$entity_type = "entity_type_example"; // string | Entity Type

try {
    $result = $apiInstance->retrieveEntityType($entity_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling TypesApi->retrieveEntityType: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **entity_type** | **string**| Entity Type |

### Return type

[**\Swagger\Client\Model\RetrieveEntityTypeResponse**](../Model/RetrieveEntityTypeResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

