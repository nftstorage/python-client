# nft_storage.NFTStorageAPI

All URIs are relative to *https://api.nft.storage*

Method | HTTP request | Description
------------- | ------------- | -------------
[**check**](NFTStorageAPI.md#check) | **GET** /check/{cid} | Check if a CID of an NFT is being stored by nft.storage.
[**delete**](NFTStorageAPI.md#delete) | **DELETE** /{cid} | Stop storing the content with the passed CID
[**list**](NFTStorageAPI.md#list) | **GET** / | List all stored files
[**status**](NFTStorageAPI.md#status) | **GET** /{cid} | Get information for the stored file CID
[**store**](NFTStorageAPI.md#store) | **POST** /upload | Store a file


# **check**
> CheckResponse check(cid)

Check if a CID of an NFT is being stored by nft.storage.

Includes the IPFS pinning state and the Filecoin deal state.

### Example


```python
import time
import nft_storage
from nft_storage.api import nft_storage_api
from nft_storage.model.error_response import ErrorResponse
from nft_storage.model.check_response import CheckResponse
from pprint import pprint
# Defining the host is optional and defaults to https://api.nft.storage
# See configuration.py for a list of all supported configuration parameters.
configuration = nft_storage.Configuration(
    host = "https://api.nft.storage"
)


# Enter a context with an instance of the API client
with nft_storage.ApiClient() as api_client:
    # Create an instance of the API class
    api_instance = nft_storage_api.NFTStorageAPI(api_client)
    cid = "bafkreidivzimqfqtoqxkrpge6bjyhlvxqs3rhe73owtmdulaxr5do5in7u" # str | CID for the NFT

    # example passing only required values which don't have defaults set
    try:
        # Check if a CID of an NFT is being stored by nft.storage.
        api_response = api_instance.check(cid)
        pprint(api_response)
    except nft_storage.ApiException as e:
        print("Exception when calling NFTStorageAPI->check: %s\n" % e)
```


### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **cid** | **str**| CID for the NFT |

### Return type

[**CheckResponse**](CheckResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | OK |  -  |
**404** | Not Found |  -  |
**5XX** | Internal Server Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **delete**
> DeleteResponse delete(cid)

Stop storing the content with the passed CID

Stop storing the content with the passed CID on nft.storage. - Unpin the item from the underlying IPFS pinning service. - Cease renewals for expired Filecoin deals involving the CID.    ⚠️ This does not remove the content from the network.  - Does not terminate any established Filecoin deal. - Does not remove the content from other IPFS nodes in the network that already cached or pinned the CID.    Note: the content will remain available if another user has stored the CID with nft.storage. 

### Example

* Bearer (JWT) Authentication (bearerAuth):

```python
import time
import nft_storage
from nft_storage.api import nft_storage_api
from nft_storage.model.error_response import ErrorResponse
from nft_storage.model.delete_response import DeleteResponse
from nft_storage.model.unauthorized_error_response import UnauthorizedErrorResponse
from nft_storage.model.forbidden_error_response import ForbiddenErrorResponse
from pprint import pprint
# Defining the host is optional and defaults to https://api.nft.storage
# See configuration.py for a list of all supported configuration parameters.
configuration = nft_storage.Configuration(
    host = "https://api.nft.storage"
)

# The client must configure the authentication and authorization parameters
# in accordance with the API server security policy.
# Examples for each auth method are provided below, use the example that
# satisfies your auth use case.

# Configure Bearer authorization (JWT): bearerAuth
configuration = nft_storage.Configuration(
    access_token = 'YOUR_BEARER_TOKEN'
)

# Enter a context with an instance of the API client
with nft_storage.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = nft_storage_api.NFTStorageAPI(api_client)
    cid = "bafkreidivzimqfqtoqxkrpge6bjyhlvxqs3rhe73owtmdulaxr5do5in7u" # str | CID for the NFT

    # example passing only required values which don't have defaults set
    try:
        # Stop storing the content with the passed CID
        api_response = api_instance.delete(cid)
        pprint(api_response)
    except nft_storage.ApiException as e:
        print("Exception when calling NFTStorageAPI->delete: %s\n" % e)
```


### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **cid** | **str**| CID for the NFT |

### Return type

[**DeleteResponse**](DeleteResponse.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | OK |  -  |
**401** | Unauthorized |  -  |
**403** | Forbidden |  -  |
**5XX** | Internal Server Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **list**
> ListResponse list()

List all stored files

### Example

* Bearer (JWT) Authentication (bearerAuth):

```python
import time
import nft_storage
from nft_storage.api import nft_storage_api
from nft_storage.model.error_response import ErrorResponse
from nft_storage.model.list_response import ListResponse
from nft_storage.model.unauthorized_error_response import UnauthorizedErrorResponse
from nft_storage.model.forbidden_error_response import ForbiddenErrorResponse
from pprint import pprint
# Defining the host is optional and defaults to https://api.nft.storage
# See configuration.py for a list of all supported configuration parameters.
configuration = nft_storage.Configuration(
    host = "https://api.nft.storage"
)

# The client must configure the authentication and authorization parameters
# in accordance with the API server security policy.
# Examples for each auth method are provided below, use the example that
# satisfies your auth use case.

# Configure Bearer authorization (JWT): bearerAuth
configuration = nft_storage.Configuration(
    access_token = 'YOUR_BEARER_TOKEN'
)

# Enter a context with an instance of the API client
with nft_storage.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = nft_storage_api.NFTStorageAPI(api_client)
    before = dateutil_parser('2020-07-27T17:32:28Z') # datetime | Return results created before provided timestamp (optional)
    limit = 10 # int | Max records to return (optional) if omitted the server will use the default value of 10

    # example passing only required values which don't have defaults set
    # and optional values
    try:
        # List all stored files
        api_response = api_instance.list(before=before, limit=limit)
        pprint(api_response)
    except nft_storage.ApiException as e:
        print("Exception when calling NFTStorageAPI->list: %s\n" % e)
```


### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **before** | **datetime**| Return results created before provided timestamp | [optional]
 **limit** | **int**| Max records to return | [optional] if omitted the server will use the default value of 10

### Return type

[**ListResponse**](ListResponse.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | OK |  -  |
**401** | Unauthorized |  -  |
**403** | Forbidden |  -  |
**5XX** | Internal Server Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **status**
> GetResponse status(cid)

Get information for the stored file CID

Includes the IPFS pinning state and the Filecoin deal state.

### Example

* Bearer (JWT) Authentication (bearerAuth):

```python
import time
import nft_storage
from nft_storage.api import nft_storage_api
from nft_storage.model.error_response import ErrorResponse
from nft_storage.model.unauthorized_error_response import UnauthorizedErrorResponse
from nft_storage.model.get_response import GetResponse
from nft_storage.model.forbidden_error_response import ForbiddenErrorResponse
from pprint import pprint
# Defining the host is optional and defaults to https://api.nft.storage
# See configuration.py for a list of all supported configuration parameters.
configuration = nft_storage.Configuration(
    host = "https://api.nft.storage"
)

# The client must configure the authentication and authorization parameters
# in accordance with the API server security policy.
# Examples for each auth method are provided below, use the example that
# satisfies your auth use case.

# Configure Bearer authorization (JWT): bearerAuth
configuration = nft_storage.Configuration(
    access_token = 'YOUR_BEARER_TOKEN'
)

# Enter a context with an instance of the API client
with nft_storage.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = nft_storage_api.NFTStorageAPI(api_client)
    cid = "bafkreidivzimqfqtoqxkrpge6bjyhlvxqs3rhe73owtmdulaxr5do5in7u" # str | CID for the NFT

    # example passing only required values which don't have defaults set
    try:
        # Get information for the stored file CID
        api_response = api_instance.status(cid)
        pprint(api_response)
    except nft_storage.ApiException as e:
        print("Exception when calling NFTStorageAPI->status: %s\n" % e)
```


### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **cid** | **str**| CID for the NFT |

### Return type

[**GetResponse**](GetResponse.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | OK |  -  |
**401** | Unauthorized |  -  |
**403** | Forbidden |  -  |
**5XX** | Internal Server Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **store**
> UploadResponse store(body)

Store a file

Store a file with nft.storage. You can upload either a single file or multiple files in a directory  Send the POST request with one of: - a single file as a single Blob/File Object as the body - multiple files as FormData with `Content-Disposition` headers for each part to specify filenames and the request header `Content-Type: multipart/form-data`.  You can also upload a Content Addressed Archive (CAR) file, by setting the request body as a single CAR Blob/File object and providing the request header `Content-Type: application/car` Providing a CAR file allows you to pre-compute the root CID for 1 or more files, ensures that the nft.storage will store and provide your assets with the same CID. 

### Example

* Bearer (JWT) Authentication (bearerAuth):

```python
import time
import nft_storage
from nft_storage.api import nft_storage_api
from nft_storage.model.error_response import ErrorResponse
from nft_storage.model.upload_response import UploadResponse
from nft_storage.model.unauthorized_error_response import UnauthorizedErrorResponse
from nft_storage.model.forbidden_error_response import ForbiddenErrorResponse
from pprint import pprint
# Defining the host is optional and defaults to https://api.nft.storage
# See configuration.py for a list of all supported configuration parameters.
configuration = nft_storage.Configuration(
    host = "https://api.nft.storage"
)

# The client must configure the authentication and authorization parameters
# in accordance with the API server security policy.
# Examples for each auth method are provided below, use the example that
# satisfies your auth use case.

# Configure Bearer authorization (JWT): bearerAuth
configuration = nft_storage.Configuration(
    access_token = 'YOUR_BEARER_TOKEN'
)

# Enter a context with an instance of the API client
with nft_storage.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = nft_storage_api.NFTStorageAPI(api_client)
    body = open('/path/to/file', 'rb') # file_type | 

    # example passing only required values which don't have defaults set
    try:
        # Store a file
        api_response = api_instance.store(body)
        pprint(api_response)
    except nft_storage.ApiException as e:
        print("Exception when calling NFTStorageAPI->store: %s\n" % e)
```


### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **file_type**|  |

### Return type

[**UploadResponse**](UploadResponse.md)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: image/*, application/car, multipart/form-data
 - **Accept**: application/json


### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | OK |  -  |
**400** | Bad Request |  -  |
**401** | Unauthorized |  -  |
**403** | Forbidden |  -  |
**5XX** | Internal Server Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

