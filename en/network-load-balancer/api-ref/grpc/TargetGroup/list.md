---
editable: false
sourcePath: en/_api-ref-grpc/loadbalancer/v1/api-ref/grpc/TargetGroup/list.md
---

# Network Load Balancer API, gRPC: TargetGroupService.List {#List}

Retrieves the list of TargetGroup resources in the specified folder.

## gRPC request

**rpc List ([ListTargetGroupsRequest](#yandex.cloud.loadbalancer.v1.ListTargetGroupsRequest)) returns ([ListTargetGroupsResponse](#yandex.cloud.loadbalancer.v1.ListTargetGroupsResponse))**

## ListTargetGroupsRequest {#yandex.cloud.loadbalancer.v1.ListTargetGroupsRequest}

```json
{
  "folderId": "string",
  "pageSize": "int64",
  "pageToken": "string",
  "filter": "string"
}
```

#|
||Field | Description ||
|| folderId | **string**

Required field. ID of the folder to list target groups in.
To get the folder ID, use a [TargetGroupService.List](#List) request. ||
|| pageSize | **int64**

The maximum number of results per page to return. If the number of available
results is larger than `pageSize`,
the service returns a [ListTargetGroupsResponse.nextPageToken](#yandex.cloud.loadbalancer.v1.ListTargetGroupsResponse)
that can be used to get the next page of results in subsequent list requests.
Default value: 100. ||
|| pageToken | **string**

Page token. To get the next page of results, set `pageToken` to the
[ListTargetGroupsResponse.nextPageToken](#yandex.cloud.loadbalancer.v1.ListTargetGroupsResponse) returned by a previous list request. ||
|| filter | **string**

A filter expression that filters resources listed in the response.
The expression must specify:
1. The field name. Currently you can only filter by the [TargetGroup.name](#yandex.cloud.loadbalancer.v1.TargetGroup) field.
2. An `=` operator.
3. The value in double quotes (`"`). Must be 3-63 characters long and match the regular expression `[a-z][-a-z0-9]{1,61}[a-z0-9]`. ||
|#

## ListTargetGroupsResponse {#yandex.cloud.loadbalancer.v1.ListTargetGroupsResponse}

```json
{
  "targetGroups": [
    {
      "id": "string",
      "folderId": "string",
      "createdAt": "google.protobuf.Timestamp",
      "name": "string",
      "description": "string",
      "labels": "string",
      "regionId": "string",
      "targets": [
        {
          "subnetId": "string",
          "address": "string"
        }
      ]
    }
  ],
  "nextPageToken": "string"
}
```

#|
||Field | Description ||
|| targetGroups[] | **[TargetGroup](#yandex.cloud.loadbalancer.v1.TargetGroup)**

List of TargetGroup resources. ||
|| nextPageToken | **string**

This token allows you to get the next page of results for list requests. If the number of results
is larger than [ListTargetGroupsRequest.pageSize](#yandex.cloud.loadbalancer.v1.ListTargetGroupsRequest), use
the `nextPageToken` as the value
for the [ListTargetGroupsRequest.pageToken](#yandex.cloud.loadbalancer.v1.ListTargetGroupsRequest) query parameter
in the next list request. Each subsequent list request will have its own
`nextPageToken` to continue paging through the results. ||
|#

## TargetGroup {#yandex.cloud.loadbalancer.v1.TargetGroup}

A TargetGroup resource. For more information, see [Target groups and resources](/docs/network-load-balancer/concepts/target-resources).

#|
||Field | Description ||
|| id | **string**

Output only. ID of the target group. ||
|| folderId | **string**

ID of the folder that the target group belongs to. ||
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Output only. Creation timestamp in [RFC3339](https://www.ietf.org/rfc/rfc3339.txt) text format. ||
|| name | **string**

Name of the target group.
The name is unique within the folder. 3-63 characters long. ||
|| description | **string**

Description of the target group. 0-256 characters long. ||
|| labels | **string**

Resource labels as `` key:value `` pairs. Maximum of 64 per resource. ||
|| regionId | **string**

ID of the region where the target group resides. ||
|| targets[] | **[Target](#yandex.cloud.loadbalancer.v1.Target)**

A list of targets in the target group. ||
|#

## Target {#yandex.cloud.loadbalancer.v1.Target}

A Target resource. For more information, see [Target groups and resources](/docs/network-load-balancer/concepts/target-resources).

#|
||Field | Description ||
|| subnetId | **string**

ID of the subnet that targets are connected to.
All targets in the target group must be connected to the same subnet within a single availability zone. ||
|| address | **string**

IP address of the target. ||
|#