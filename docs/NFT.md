# NFT


## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**cid** | **str** | Self-describing content-addressed identifiers for distributed systems. Check [spec](https://github.com/multiformats/cid) for more info. | [optional] 
**size** | **float** | Size in bytes of the NFT data. | [optional]  if omitted the server will use the default value of 132614
**created** | **datetime** | This is a timestamp in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format: YYYY-MM-DDTHH:MM:SSZ. | [optional] 
**type** | **str** | MIME type of the upload file or &#39;directory&#39; when uploading multiple files. | [optional] 
**scope** | **str** | Name of the JWT token used to create this NFT. | [optional]  if omitted the server will use the default value of "default"
**pin** | [**Pin**](Pin.md) |  | [optional] 
**files** | [**Files**](Files.md) |  | [optional] 
**deals** | [**[Deal]**](Deal.md) |  | [optional] 
**any string name** | **bool, date, datetime, dict, float, int, list, str, none_type** | any string name can be used but the value must be the correct type | [optional]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


