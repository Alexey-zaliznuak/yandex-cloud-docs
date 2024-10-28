---
editable: false
sourcePath: en/_api-ref-grpc/mdb/kafka/v1/api-ref/grpc/User/get.md
---

# Managed Service for Apache Kafka® API, gRPC: UserService.Get {#Get}

Returns the specified Kafka user.

To get the list of available Kafka users, make a [List](/docs/managed-kafka/api-ref/grpc/User/list#List) request.

## gRPC request

**rpc Get ([GetUserRequest](#yandex.cloud.mdb.kafka.v1.GetUserRequest)) returns ([User](#yandex.cloud.mdb.kafka.v1.User))**

## GetUserRequest {#yandex.cloud.mdb.kafka.v1.GetUserRequest}

```json
{
  "clusterId": "string",
  "userName": "string"
}
```

#|
||Field | Description ||
|| clusterId | **string**

Required field. ID of the Apache Kafka® cluster the user belongs to.

To get the cluster ID, make a [ClusterService.List](/docs/managed-kafka/api-ref/grpc/Cluster/list#List) request. ||
|| userName | **string**

Required field. Name of the Kafka user to return.

To get the name of the user, make a [UserService.List](/docs/managed-kafka/api-ref/grpc/User/list#List) request. ||
|#

## User {#yandex.cloud.mdb.kafka.v1.User}

```json
{
  "name": "string",
  "clusterId": "string",
  "permissions": [
    {
      "topicName": "string",
      "role": "AccessRole",
      "allowHosts": [
        "string"
      ]
    }
  ]
}
```

A Kafka user.
For more information, see the [Operations -> Accounts](/docs/managed-kafka/operations/cluster-accounts) section of the documentation.

#|
||Field | Description ||
|| name | **string**

Name of the Kafka user. ||
|| clusterId | **string**

ID of the Apache Kafka® cluster the user belongs to.

To get the Apache Kafka® cluster ID, make a [ClusterService.List](/docs/managed-kafka/api-ref/grpc/Cluster/list#List) request. ||
|| permissions[] | **[Permission](#yandex.cloud.mdb.kafka.v1.Permission)**

Set of permissions granted to this user. ||
|#

## Permission {#yandex.cloud.mdb.kafka.v1.Permission}

#|
||Field | Description ||
|| topicName | **string**

Name or prefix-pattern with wildcard for the topic that the permission grants access to.

To get the topic name, make a [TopicService.List](/docs/managed-kafka/api-ref/grpc/Topic/list#List) request. ||
|| role | enum **AccessRole**

Access role type to grant to the user.

- `ACCESS_ROLE_UNSPECIFIED`
- `ACCESS_ROLE_PRODUCER`: Producer role for the user.
- `ACCESS_ROLE_CONSUMER`: Consumer role for the user.
- `ACCESS_ROLE_ADMIN`: Admin role for the user. ||
|| allowHosts[] | **string**

Lists hosts allowed for this permission.
Only ip-addresses allowed as value of single host.
When not defined, access from any host is allowed.

Bare in mind that the same host might appear in multiple permissions at the same time,
hence removing individual permission doesn't automatically restricts access from the `allowHosts` of the permission.
If the same host(s) is listed for another permission of the same principal/topic, the host(s) remains allowed. ||
|#