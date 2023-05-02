# Swagger\Client\EntitiesApi

All URIs are relative to *http://orion.lab.fiware.org*

Method | HTTP request | Description
------------- | ------------- | -------------
[**createEntity**](EntitiesApi.md#createEntity) | **POST** /v2/entities | Create Entity
[**listEntities**](EntitiesApi.md#listEntities) | **GET** /v2/entities | List Entities
[**removeEntity**](EntitiesApi.md#removeEntity) | **DELETE** /v2/entities/{entityId} | Remove Entity
[**replaceAllEntityAttributes**](EntitiesApi.md#replaceAllEntityAttributes) | **PUT** /v2/entities/{entityId}/attrs | Replace all entity attributes
[**retrieveEntity**](EntitiesApi.md#retrieveEntity) | **GET** /v2/entities/{entityId} | Retrieve Entity
[**retrieveEntityAttributes**](EntitiesApi.md#retrieveEntityAttributes) | **GET** /v2/entities/{entityId}/attrs | Retrieve Entity Attributes
[**updateExistingEntityAttributes**](EntitiesApi.md#updateExistingEntityAttributes) | **PATCH** /v2/entities/{entityId}/attrs | Update Existing Entity Attributes
[**updateOrAppendEntityAttributes**](EntitiesApi.md#updateOrAppendEntityAttributes) | **POST** /v2/entities/{entityId}/attrs | Update or Append Entity Attributes


# **createEntity**
> createEntity($content_type, $body, $options)

Create Entity

The payload is an object representing the entity to be created. The object follows the JSON entity representation format (described in a \"JSON Entity Representation\" section). Response: * Successful operation uses 201 Created (if upsert option is not used) or 204 No Content (if   upsert option is used). Response includes a `Location` header with the URL of the   created entity. * Errors use a non-2xx and (optionally) an error payload. See subsection on \"Error Responses\" for   more details.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Swagger\Client\Api\EntitiesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$content_type = "content_type_example"; // string | 
$body = new \Swagger\Client\Model\CreateEntityRequest(); // \Swagger\Client\Model\CreateEntityRequest | 
$options = "options_example"; // string | Options dictionary

try {
    $apiInstance->createEntity($content_type, $body, $options);
} catch (Exception $e) {
    echo 'Exception when calling EntitiesApi->createEntity: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **content_type** | **string**|  |
 **body** | [**\Swagger\Client\Model\CreateEntityRequest**](../Model/CreateEntityRequest.md)|  |
 **options** | **string**| Options dictionary | [optional]

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **listEntities**
> \Swagger\Client\Model\ListEntitiesResponse[] listEntities($id, $type, $id_pattern, $type_pattern, $q, $mq, $georel, $geometry, $coords, $limit, $offset, $attrs, $metadata, $order_by, $options)

List Entities

Retrieves a list of entities that match different criteria by id, type, pattern matching (either id or type) and/or those which match a query or geographical query (see [Simple Query Language](#simple_query_language) and  [Geographical Queries](#geographical_queries)). A given entity has to match all the criteria to be retrieved (i.e., the criteria is combined in a logical AND way). Note that pattern matching query parameters are incompatible (i.e. mutually exclusive) with their corresponding exact matching parameters, i.e. `idPattern` with `id` and `typePattern` with `type`. The response payload is an array containing one object per matching entity. Each entity follows the JSON entity representation format (described in \"JSON Entity Representation\" section). Response code: * Successful operation uses 200 OK * Errors use a non-2xx and (optionally) an error payload. See subsection on \"Error Responses\" for   more details.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Swagger\Client\Api\EntitiesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$id = "id_example"; // string | A comma-separated list of elements. Retrieve entities whose ID matches one of the elements in the list. Incompatible with `idPattern`.
$type = "type_example"; // string | comma-separated list of elements. Retrieve entities whose type matches one of the elements in the list. Incompatible with `typePattern`.
$id_pattern = "id_pattern_example"; // string | A correctly formated regular expression. Retrieve entities whose ID matches the regular expression. Incompatible with `id`.
$type_pattern = "type_pattern_example"; // string | A correctly formated regular expression. Retrieve entities whose type matches the regular expression. Incompatible with `type`.
$q = "q_example"; // string | A query expression, composed of a list of statements separated by `;`, i.e., q=statement1;statement2;statement3. See [Simple Query Language specification](#simple_query_language).
$mq = "mq_example"; // string | A query expression for attribute metadata, composed of a list of statements separated by `;`, i.e., mq=statement1;statement2;statement3. See [Simple Query Language specification](#simple_query_language).
$georel = "georel_example"; // string | Spatial relationship between matching entities and a reference shape. See [Geographical Queries](#geographical_queries).
$geometry = "geometry_example"; // string | Geografical area to which the query is restricted. See [Geographical Queries](#geographical_queries).
$coords = "coords_example"; // string | List of latitude-longitude pairs of coordinates separated by ';'. See [Geographical Queries](#geographical_queries).
$limit = 1.2; // double | Limits the number of entities to be retrieved
$offset = 1.2; // double | Establishes the offset from where entities are retrieved
$attrs = "attrs_example"; // string | Comma-separated list of attribute names whose data are to be included in the response. The attributes are retrieved in the order specified by this parameter. If this parameter is not included, the attributes are retrieved in arbitrary order. See \"Filtering out attributes and metadata\" section for more detail.
$metadata = "metadata_example"; // string | A list of metadata names to include in the response. See \"Filtering out attributes and metadata\" section for more detail.
$order_by = "order_by_example"; // string | Criteria for ordering results. See \"Ordering Results\" section for details.
$options = "options_example"; // string | Options dictionary

try {
    $result = $apiInstance->listEntities($id, $type, $id_pattern, $type_pattern, $q, $mq, $georel, $geometry, $coords, $limit, $offset, $attrs, $metadata, $order_by, $options);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EntitiesApi->listEntities: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **string**| A comma-separated list of elements. Retrieve entities whose ID matches one of the elements in the list. Incompatible with &#x60;idPattern&#x60;. | [optional]
 **type** | **string**| comma-separated list of elements. Retrieve entities whose type matches one of the elements in the list. Incompatible with &#x60;typePattern&#x60;. | [optional]
 **id_pattern** | **string**| A correctly formated regular expression. Retrieve entities whose ID matches the regular expression. Incompatible with &#x60;id&#x60;. | [optional]
 **type_pattern** | **string**| A correctly formated regular expression. Retrieve entities whose type matches the regular expression. Incompatible with &#x60;type&#x60;. | [optional]
 **q** | **string**| A query expression, composed of a list of statements separated by &#x60;;&#x60;, i.e., q&#x3D;statement1;statement2;statement3. See [Simple Query Language specification](#simple_query_language). | [optional]
 **mq** | **string**| A query expression for attribute metadata, composed of a list of statements separated by &#x60;;&#x60;, i.e., mq&#x3D;statement1;statement2;statement3. See [Simple Query Language specification](#simple_query_language). | [optional]
 **georel** | **string**| Spatial relationship between matching entities and a reference shape. See [Geographical Queries](#geographical_queries). | [optional]
 **geometry** | **string**| Geografical area to which the query is restricted. See [Geographical Queries](#geographical_queries). | [optional]
 **coords** | **string**| List of latitude-longitude pairs of coordinates separated by &#39;;&#39;. See [Geographical Queries](#geographical_queries). | [optional]
 **limit** | **double**| Limits the number of entities to be retrieved | [optional]
 **offset** | **double**| Establishes the offset from where entities are retrieved | [optional]
 **attrs** | **string**| Comma-separated list of attribute names whose data are to be included in the response. The attributes are retrieved in the order specified by this parameter. If this parameter is not included, the attributes are retrieved in arbitrary order. See \&quot;Filtering out attributes and metadata\&quot; section for more detail. | [optional]
 **metadata** | **string**| A list of metadata names to include in the response. See \&quot;Filtering out attributes and metadata\&quot; section for more detail. | [optional]
 **order_by** | **string**| Criteria for ordering results. See \&quot;Ordering Results\&quot; section for details. | [optional]
 **options** | **string**| Options dictionary | [optional]

### Return type

[**\Swagger\Client\Model\ListEntitiesResponse[]**](../Model/ListEntitiesResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **removeEntity**
> removeEntity($entity_id, $type)

Remove Entity

Delete the entity. Response: * Successful operation uses 204 No Content * Errors use a non-2xx and (optionally) an error payload. See subsection on \"Error Responses\" for   more details.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Swagger\Client\Api\EntitiesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$entity_id = "entity_id_example"; // string | Id of the entity to be deleted
$type = "type_example"; // string | Entity type, to avoid ambiguity in case there are several entities with the same entity id.

try {
    $apiInstance->removeEntity($entity_id, $type);
} catch (Exception $e) {
    echo 'Exception when calling EntitiesApi->removeEntity: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **entity_id** | **string**| Id of the entity to be deleted |
 **type** | **string**| Entity type, to avoid ambiguity in case there are several entities with the same entity id. | [optional]

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **replaceAllEntityAttributes**
> replaceAllEntityAttributes($entity_id, $content_type, $body, $type, $options)

Replace all entity attributes

The request payload is an object representing the new entity attributes. The object follows the JSON entity representation format (described in a \"JSON Entity Representation\" above), except that `id` and `type` are not allowed. The attributes previously existing in the entity are removed and replaced by the ones in the request. Response: * Successful operation uses 204 No Content * Errors use a non-2xx and (optionally) an error payload. See subsection on \"Error Responses\" for   more details.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Swagger\Client\Api\EntitiesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$entity_id = "entity_id_example"; // string | Id of the entity in question.
$content_type = "content_type_example"; // string | 
$body = new \Swagger\Client\Model\ReplaceAllEntityAttributesRequest(); // \Swagger\Client\Model\ReplaceAllEntityAttributesRequest | 
$type = "type_example"; // string | Entity type, to avoid ambiguity in case there are several entities with the same entity id.
$options = "options_example"; // string | Operations options

try {
    $apiInstance->replaceAllEntityAttributes($entity_id, $content_type, $body, $type, $options);
} catch (Exception $e) {
    echo 'Exception when calling EntitiesApi->replaceAllEntityAttributes: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **entity_id** | **string**| Id of the entity in question. |
 **content_type** | **string**|  |
 **body** | [**\Swagger\Client\Model\ReplaceAllEntityAttributesRequest**](../Model/ReplaceAllEntityAttributesRequest.md)|  |
 **type** | **string**| Entity type, to avoid ambiguity in case there are several entities with the same entity id. | [optional]
 **options** | **string**| Operations options | [optional]

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **retrieveEntity**
> \Swagger\Client\Model\RetrieveEntityResponse retrieveEntity($entity_id, $type, $attrs, $metadata, $options)

Retrieve Entity

The response is an object representing the entity identified by the ID. The object follows the JSON entity representation format (described in \"JSON Entity Representation\" section). This operation must return one entity element only, but there may be more than one entity with the same ID (e.g. entities with same ID but different types). In such case, an error message is returned, with the HTTP status code set to 409 Conflict. Response: * Successful operation uses 200 OK * Errors use a non-2xx and (optionally) an error payload. See subsection on \"Error Responses\" for more details.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Swagger\Client\Api\EntitiesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$entity_id = "entity_id_example"; // string | Id of the entity to be retrieved
$type = "type_example"; // string | Entity type, to avoid ambiguity in case there are several entities with the same entity id.
$attrs = "attrs_example"; // string | Comma-separated list of attribute names whose data must be included in the response. The attributes are retrieved in the order specified by this parameter. See \"Filtering out attributes and metadata\" section for more detail. If this parameter is not included, the attributes are retrieved in arbitrary order, and all the attributes of the entity are included in the response.
$metadata = "metadata_example"; // string | A list of metadata names to include in the response. See \"Filtering out attributes and metadata\" section for more detail.
$options = "options_example"; // string | Options dictionary

try {
    $result = $apiInstance->retrieveEntity($entity_id, $type, $attrs, $metadata, $options);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EntitiesApi->retrieveEntity: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **entity_id** | **string**| Id of the entity to be retrieved |
 **type** | **string**| Entity type, to avoid ambiguity in case there are several entities with the same entity id. | [optional]
 **attrs** | **string**| Comma-separated list of attribute names whose data must be included in the response. The attributes are retrieved in the order specified by this parameter. See \&quot;Filtering out attributes and metadata\&quot; section for more detail. If this parameter is not included, the attributes are retrieved in arbitrary order, and all the attributes of the entity are included in the response. | [optional]
 **metadata** | **string**| A list of metadata names to include in the response. See \&quot;Filtering out attributes and metadata\&quot; section for more detail. | [optional]
 **options** | **string**| Options dictionary | [optional]

### Return type

[**\Swagger\Client\Model\RetrieveEntityResponse**](../Model/RetrieveEntityResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **retrieveEntityAttributes**
> \Swagger\Client\Model\RetrieveEntityAttributesResponse retrieveEntityAttributes($entity_id, $type, $attrs, $metadata, $options)

Retrieve Entity Attributes

This request is similar to retreiving the whole entity, however this one omits the `id` and `type` fields. Just like the general request of getting an entire entity, this operation must return only one entity element. If more than one entity with the same ID is found (e.g. entities with same ID but different type), an error message is returned, with the HTTP status code set to 409 Conflict. Response: * Successful operation uses 200 OK * Errors use a non-2xx and (optionally) an error payload. See subsection on \"Error Responses\" for   more details.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Swagger\Client\Api\EntitiesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$entity_id = "entity_id_example"; // string | Id of the entity to be retrieved
$type = "type_example"; // string | Entity type, to avoid ambiguity in case there are several entities with the same entity id.
$attrs = "attrs_example"; // string | Comma-separated list of attribute names whose data are to be included in the response. The attributes are retrieved in the order specified by this parameter. If this parameter is not included, the attributes are retrieved in arbitrary order, and all the attributes of the entity are included in the response. See \"Filtering out attributes and metadata\" section for more detail.
$metadata = "metadata_example"; // string | A list of metadata names to include in the response. See \"Filtering out attributes and metadata\" section for more detail.
$options = "options_example"; // string | Options dictionary

try {
    $result = $apiInstance->retrieveEntityAttributes($entity_id, $type, $attrs, $metadata, $options);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EntitiesApi->retrieveEntityAttributes: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **entity_id** | **string**| Id of the entity to be retrieved |
 **type** | **string**| Entity type, to avoid ambiguity in case there are several entities with the same entity id. | [optional]
 **attrs** | **string**| Comma-separated list of attribute names whose data are to be included in the response. The attributes are retrieved in the order specified by this parameter. If this parameter is not included, the attributes are retrieved in arbitrary order, and all the attributes of the entity are included in the response. See \&quot;Filtering out attributes and metadata\&quot; section for more detail. | [optional]
 **metadata** | **string**| A list of metadata names to include in the response. See \&quot;Filtering out attributes and metadata\&quot; section for more detail. | [optional]
 **options** | **string**| Options dictionary | [optional]

### Return type

[**\Swagger\Client\Model\RetrieveEntityAttributesResponse**](../Model/RetrieveEntityAttributesResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **updateExistingEntityAttributes**
> updateExistingEntityAttributes($entity_id, $content_type, $body, $type, $options)

Update Existing Entity Attributes

The request payload is an object representing the attributes to update. The object follows the JSON entity representation format (described in \"JSON Entity Representation\" section), except that `id` and `type` are not allowed. The entity attributes are updated with the ones in the payload. In addition to that, if one or more attributes in the payload doesn't exist in the entity, an error is returned. Response: * Successful operation uses 204 No Content * Errors use a non-2xx and (optionally) an error payload. See subsection on \"Error Responses\" for   more details.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Swagger\Client\Api\EntitiesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$entity_id = "entity_id_example"; // string | Id of the entity to be updated
$content_type = "content_type_example"; // string | 
$body = new \Swagger\Client\Model\UpdateExistingEntityAttributesRequest(); // \Swagger\Client\Model\UpdateExistingEntityAttributesRequest | 
$type = "type_example"; // string | Entity type, to avoid ambiguity in case there are several entities with the same entity id.
$options = "options_example"; // string | Operations options

try {
    $apiInstance->updateExistingEntityAttributes($entity_id, $content_type, $body, $type, $options);
} catch (Exception $e) {
    echo 'Exception when calling EntitiesApi->updateExistingEntityAttributes: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **entity_id** | **string**| Id of the entity to be updated |
 **content_type** | **string**|  |
 **body** | [**\Swagger\Client\Model\UpdateExistingEntityAttributesRequest**](../Model/UpdateExistingEntityAttributesRequest.md)|  |
 **type** | **string**| Entity type, to avoid ambiguity in case there are several entities with the same entity id. | [optional]
 **options** | **string**| Operations options | [optional]

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **updateOrAppendEntityAttributes**
> updateOrAppendEntityAttributes($entity_id, $content_type, $body, $type, $options)

Update or Append Entity Attributes

The request payload is an object representing the attributes to append or update. The object follows the JSON entity representation format (described in \"JSON Entity Representation\" section), except that `id` and `type` are not allowed. The entity attributes are updated with the ones in the payload, depending on whether the `append` operation option is used or not. * If `append` is not used: the entity attributes are updated (if they previously exist) or appended   (if they don't previously exist) with the ones in the payload. * If `append` is used (i.e. strict append semantics): all the attributes in the payload not   previously existing in the entity are appended. In addition to that, in case some of the   attributes in the payload already exist in the entity, an error is returned. Response: * Successful operation uses 204 No Content * Errors use a non-2xx and (optionally) an error payload. See subsection on \"Error Responses\" for   more details.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Swagger\Client\Api\EntitiesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$entity_id = "entity_id_example"; // string | Entity id to be updated
$content_type = "content_type_example"; // string | 
$body = new \Swagger\Client\Model\UpdateOrAppendEntityAttributesRequest(); // \Swagger\Client\Model\UpdateOrAppendEntityAttributesRequest | 
$type = "type_example"; // string | Entity type, to avoid ambiguity in case there are several entities with the same entity id.
$options = "options_example"; // string | Operations options

try {
    $apiInstance->updateOrAppendEntityAttributes($entity_id, $content_type, $body, $type, $options);
} catch (Exception $e) {
    echo 'Exception when calling EntitiesApi->updateOrAppendEntityAttributes: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **entity_id** | **string**| Entity id to be updated |
 **content_type** | **string**|  |
 **body** | [**\Swagger\Client\Model\UpdateOrAppendEntityAttributesRequest**](../Model/UpdateOrAppendEntityAttributesRequest.md)|  |
 **type** | **string**| Entity type, to avoid ambiguity in case there are several entities with the same entity id. | [optional]
 **options** | **string**| Operations options | [optional]

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

