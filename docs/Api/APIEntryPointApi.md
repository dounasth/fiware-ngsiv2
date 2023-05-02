# Dounasth\Ngsiv2\APIEntryPointApi

All URIs are relative to *http://orion.lab.fiware.org*

Method | HTTP request | Description
------------- | ------------- | -------------
[**retrieveAPIResources**](APIEntryPointApi.md#retrieveAPIResources) | **GET** /v2 | Retrieve API Resources


# **retrieveAPIResources**
> \Dounasth\Ngsiv2\Model\RetrieveApiResourcesResponse retrieveAPIResources()

Retrieve API Resources

This resource does not have any attributes. Instead it offers the initial API affordances in the form of the links in the JSON body. It is recommended to follow the “url” link values, [Link](https://tools.ietf.org/html/rfc5988) or Location headers where applicable to retrieve resources. Instead of constructing your own URLs, to keep your client decoupled from implementation details.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Dounasth\Ngsiv2\Api\APIEntryPointApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);

try {
    $result = $apiInstance->retrieveAPIResources();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling APIEntryPointApi->retrieveAPIResources: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters
This endpoint does not need any parameter.

### Return type

[**\Dounasth\Ngsiv2\Model\RetrieveApiResourcesResponse**](../Model/RetrieveApiResourcesResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

