# Dounasth\Ngsiv2\RegistrationsApi

All URIs are relative to *http://orion.lab.fiware.org*

Method | HTTP request | Description
------------- | ------------- | -------------
[**createRegistration**](RegistrationsApi.md#createRegistration) | **POST** /v2/registrations | Create Registration
[**deleteRegistration**](RegistrationsApi.md#deleteRegistration) | **DELETE** /v2/registrations/{registrationId} | Delete Registration
[**listRegistrations**](RegistrationsApi.md#listRegistrations) | **GET** /v2/registrations | List Registrations
[**retrieveRegistration**](RegistrationsApi.md#retrieveRegistration) | **GET** /v2/registrations/{registrationId} | Retrieve Registration
[**updateRegistration**](RegistrationsApi.md#updateRegistration) | **PATCH** /v2/registrations/{registrationId} | Update Registration


# **createRegistration**
> createRegistration($content_type, $body)

Create Registration

Creates a new context provider registration. This is typically used for binding context sources as providers of certain data. The registration is represented by a JSON object as described at the beginning of this section. Response: * Successful operation uses 201 Created * Errors use a non-2xx and (optionally) an error payload. See subsection on \"Error Responses\" for   more details.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Dounasth\Ngsiv2\Api\RegistrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$content_type = "content_type_example"; // string | 
$body = new \Dounasth\Ngsiv2\Model\CreateRegistrationRequest(); // \Dounasth\Ngsiv2\Model\CreateRegistrationRequest | 

try {
    $apiInstance->createRegistration($content_type, $body);
} catch (Exception $e) {
    echo 'Exception when calling RegistrationsApi->createRegistration: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **content_type** | **string**|  |
 **body** | [**\Dounasth\Ngsiv2\Model\CreateRegistrationRequest**](../Model/CreateRegistrationRequest.md)|  |

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **deleteRegistration**
> deleteRegistration($registration_id)

Delete Registration

Cancels a context provider registration. Response: * Successful operation uses 204 No Content * Errors use a non-2xx and (optionally) an error payload. See subsection on \"Error Responses\" for   more details.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Dounasth\Ngsiv2\Api\RegistrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$registration_id = "registration_id_example"; // string | registration Id.

try {
    $apiInstance->deleteRegistration($registration_id);
} catch (Exception $e) {
    echo 'Exception when calling RegistrationsApi->deleteRegistration: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **registration_id** | **string**| registration Id. |

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **listRegistrations**
> \Dounasth\Ngsiv2\Model\ListRegistrationsResponse[] listRegistrations($limit, $offset, $options)

List Registrations

Lists all the context provider registrations present in the system.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Dounasth\Ngsiv2\Api\RegistrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$limit = 1.2; // double | Limit the number of registrations to be retrieved
$offset = 1.2; // double | Skip a number of registrations
$options = "options_example"; // string | Options dictionary

try {
    $result = $apiInstance->listRegistrations($limit, $offset, $options);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling RegistrationsApi->listRegistrations: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **limit** | **double**| Limit the number of registrations to be retrieved | [optional]
 **offset** | **double**| Skip a number of registrations | [optional]
 **options** | **string**| Options dictionary | [optional]

### Return type

[**\Dounasth\Ngsiv2\Model\ListRegistrationsResponse[]**](../Model/ListRegistrationsResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **retrieveRegistration**
> \Dounasth\Ngsiv2\Model\RetrieveRegistrationResponse retrieveRegistration($registration_id)

Retrieve Registration

The response is the registration represented by a JSON object as described at the beginning of this section. Response: * Successful operation uses 200 OK * Errors use a non-2xx and (optionally) an error payload. See subsection on \"Error Responses\" for   more details.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Dounasth\Ngsiv2\Api\RegistrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$registration_id = "registration_id_example"; // string | registration Id.

try {
    $result = $apiInstance->retrieveRegistration($registration_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling RegistrationsApi->retrieveRegistration: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **registration_id** | **string**| registration Id. |

### Return type

[**\Dounasth\Ngsiv2\Model\RetrieveRegistrationResponse**](../Model/RetrieveRegistrationResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **updateRegistration**
> updateRegistration($registration_id, $content_type, $body)

Update Registration

Only the fields included in the request are updated in the registration. Response: * Successful operation uses 204 No Content * Errors use a non-2xx and (optionally) an error payload. See subsection on \"Error Responses\" for   more details.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Dounasth\Ngsiv2\Api\RegistrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$registration_id = "registration_id_example"; // string | registration Id.
$content_type = "content_type_example"; // string | 
$body = new \Dounasth\Ngsiv2\Model\UpdateRegistrationRequest(); // \Dounasth\Ngsiv2\Model\UpdateRegistrationRequest | 

try {
    $apiInstance->updateRegistration($registration_id, $content_type, $body);
} catch (Exception $e) {
    echo 'Exception when calling RegistrationsApi->updateRegistration: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **registration_id** | **string**| registration Id. |
 **content_type** | **string**|  |
 **body** | [**\Dounasth\Ngsiv2\Model\UpdateRegistrationRequest**](../Model/UpdateRegistrationRequest.md)|  |

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

