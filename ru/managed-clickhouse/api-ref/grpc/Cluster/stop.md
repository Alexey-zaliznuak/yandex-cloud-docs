---
editable: false
sourcePath: en/_api-ref-grpc/mdb/clickhouse/v1/api-ref/grpc/Cluster/stop.md
---

# Managed Service for ClickHouse API, gRPC: ClusterService.Stop {#Stop}

Stops the specified ClickHouse cluster.

## gRPC request

**rpc Stop ([StopClusterRequest](#yandex.cloud.mdb.clickhouse.v1.StopClusterRequest)) returns ([operation.Operation](#yandex.cloud.operation.Operation))**

## StopClusterRequest {#yandex.cloud.mdb.clickhouse.v1.StopClusterRequest}

```json
{
  "clusterId": "string"
}
```

#|
||Field | Description ||
|| clusterId | **string**

Required field. ID of the ClickHouse cluster to stop. ||
|#

## operation.Operation {#yandex.cloud.operation.Operation}

```json
{
  "id": "string",
  "description": "string",
  "createdAt": "google.protobuf.Timestamp",
  "createdBy": "string",
  "modifiedAt": "google.protobuf.Timestamp",
  "done": "bool",
  "metadata": {
    "clusterId": "string"
  },
  // Includes only one of the fields `error`, `response`
  "error": "google.rpc.Status",
  "response": {
    "id": "string",
    "folderId": "string",
    "createdAt": "google.protobuf.Timestamp",
    "name": "string",
    "description": "string",
    "labels": "string",
    "environment": "Environment",
    "monitoring": [
      {
        "name": "string",
        "description": "string",
        "link": "string"
      }
    ],
    "config": {
      "version": "string",
      "clickhouse": {
        "config": {
          "effectiveConfig": {
            "logLevel": "LogLevel",
            "mergeTree": {
              "replicatedDeduplicationWindow": "google.protobuf.Int64Value",
              "replicatedDeduplicationWindowSeconds": "google.protobuf.Int64Value",
              "partsToDelayInsert": "google.protobuf.Int64Value",
              "partsToThrowInsert": "google.protobuf.Int64Value",
              "inactivePartsToDelayInsert": "google.protobuf.Int64Value",
              "inactivePartsToThrowInsert": "google.protobuf.Int64Value",
              "maxReplicatedMergesInQueue": "google.protobuf.Int64Value",
              "numberOfFreeEntriesInPoolToLowerMaxSizeOfMerge": "google.protobuf.Int64Value",
              "maxBytesToMergeAtMinSpaceInPool": "google.protobuf.Int64Value",
              "maxBytesToMergeAtMaxSpaceInPool": "google.protobuf.Int64Value",
              "minBytesForWidePart": "google.protobuf.Int64Value",
              "minRowsForWidePart": "google.protobuf.Int64Value",
              "ttlOnlyDropParts": "google.protobuf.BoolValue",
              "allowRemoteFsZeroCopyReplication": "google.protobuf.BoolValue",
              "mergeWithTtlTimeout": "google.protobuf.Int64Value",
              "mergeWithRecompressionTtlTimeout": "google.protobuf.Int64Value",
              "maxPartsInTotal": "google.protobuf.Int64Value",
              "maxNumberOfMergesWithTtlInPool": "google.protobuf.Int64Value",
              "cleanupDelayPeriod": "google.protobuf.Int64Value",
              "numberOfFreeEntriesInPoolToExecuteMutation": "google.protobuf.Int64Value",
              "maxAvgPartSizeForTooManyParts": "google.protobuf.Int64Value",
              "minAgeToForceMergeSeconds": "google.protobuf.Int64Value",
              "minAgeToForceMergeOnPartitionOnly": "google.protobuf.BoolValue",
              "mergeSelectingSleepMs": "google.protobuf.Int64Value",
              "mergeMaxBlockSize": "google.protobuf.Int64Value",
              "checkSampleColumnIsCorrect": "google.protobuf.BoolValue",
              "maxMergeSelectingSleepMs": "google.protobuf.Int64Value",
              "maxCleanupDelayPeriod": "google.protobuf.Int64Value"
            },
            "compression": [
              {
                "method": "Method",
                "minPartSize": "int64",
                "minPartSizeRatio": "double",
                "level": "google.protobuf.Int64Value"
              }
            ],
            "dictionaries": [
              {
                "name": "string",
                "structure": {
                  "id": {
                    "name": "string"
                  },
                  "key": {
                    "attributes": [
                      {
                        "name": "string",
                        "type": "string",
                        "nullValue": "string",
                        "expression": "string",
                        "hierarchical": "bool",
                        "injective": "bool"
                      }
                    ]
                  },
                  "rangeMin": {
                    "name": "string",
                    "type": "string",
                    "nullValue": "string",
                    "expression": "string",
                    "hierarchical": "bool",
                    "injective": "bool"
                  },
                  "rangeMax": {
                    "name": "string",
                    "type": "string",
                    "nullValue": "string",
                    "expression": "string",
                    "hierarchical": "bool",
                    "injective": "bool"
                  },
                  "attributes": [
                    {
                      "name": "string",
                      "type": "string",
                      "nullValue": "string",
                      "expression": "string",
                      "hierarchical": "bool",
                      "injective": "bool"
                    }
                  ]
                },
                "layout": {
                  "type": "Type",
                  "sizeInCells": "int64",
                  "maxArraySize": "int64"
                },
                // Includes only one of the fields `fixedLifetime`, `lifetimeRange`
                "fixedLifetime": "int64",
                "lifetimeRange": {
                  "min": "int64",
                  "max": "int64"
                },
                // end of the list of possible fields
                // Includes only one of the fields `httpSource`, `mysqlSource`, `clickhouseSource`, `mongodbSource`, `postgresqlSource`
                "httpSource": {
                  "url": "string",
                  "format": "string",
                  "headers": [
                    {
                      "name": "string",
                      "value": "string"
                    }
                  ]
                },
                "mysqlSource": {
                  "db": "string",
                  "table": "string",
                  "port": "int64",
                  "user": "string",
                  "password": "string",
                  "replicas": [
                    {
                      "host": "string",
                      "priority": "int64",
                      "port": "int64",
                      "user": "string",
                      "password": "string"
                    }
                  ],
                  "where": "string",
                  "invalidateQuery": "string",
                  "closeConnection": "google.protobuf.BoolValue",
                  "shareConnection": "google.protobuf.BoolValue"
                },
                "clickhouseSource": {
                  "db": "string",
                  "table": "string",
                  "host": "string",
                  "port": "int64",
                  "user": "string",
                  "password": "string",
                  "where": "string",
                  "secure": "google.protobuf.BoolValue"
                },
                "mongodbSource": {
                  "db": "string",
                  "collection": "string",
                  "host": "string",
                  "port": "int64",
                  "user": "string",
                  "password": "string",
                  "options": "string"
                },
                "postgresqlSource": {
                  "db": "string",
                  "table": "string",
                  "hosts": [
                    "string"
                  ],
                  "port": "int64",
                  "user": "string",
                  "password": "string",
                  "invalidateQuery": "string",
                  "sslMode": "SslMode"
                }
                // end of the list of possible fields
              }
            ],
            "graphiteRollup": [
              {
                "name": "string",
                "patterns": [
                  {
                    "regexp": "string",
                    "function": "string",
                    "retention": [
                      {
                        "age": "int64",
                        "precision": "int64"
                      }
                    ]
                  }
                ],
                "pathColumnName": "string",
                "timeColumnName": "string",
                "valueColumnName": "string",
                "versionColumnName": "string"
              }
            ],
            "kafka": {
              "securityProtocol": "SecurityProtocol",
              "saslMechanism": "SaslMechanism",
              "saslUsername": "string",
              "saslPassword": "string",
              "enableSslCertificateVerification": "google.protobuf.BoolValue",
              "maxPollIntervalMs": "google.protobuf.Int64Value",
              "sessionTimeoutMs": "google.protobuf.Int64Value",
              "debug": "Debug",
              "autoOffsetReset": "AutoOffsetReset"
            },
            "kafkaTopics": [
              {
                "name": "string",
                "settings": {
                  "securityProtocol": "SecurityProtocol",
                  "saslMechanism": "SaslMechanism",
                  "saslUsername": "string",
                  "saslPassword": "string",
                  "enableSslCertificateVerification": "google.protobuf.BoolValue",
                  "maxPollIntervalMs": "google.protobuf.Int64Value",
                  "sessionTimeoutMs": "google.protobuf.Int64Value",
                  "debug": "Debug",
                  "autoOffsetReset": "AutoOffsetReset"
                }
              }
            ],
            "rabbitmq": {
              "username": "string",
              "password": "string",
              "vhost": "string"
            },
            "maxConnections": "google.protobuf.Int64Value",
            "maxConcurrentQueries": "google.protobuf.Int64Value",
            "keepAliveTimeout": "google.protobuf.Int64Value",
            "uncompressedCacheSize": "google.protobuf.Int64Value",
            "markCacheSize": "google.protobuf.Int64Value",
            "maxTableSizeToDrop": "google.protobuf.Int64Value",
            "maxPartitionSizeToDrop": "google.protobuf.Int64Value",
            "builtinDictionariesReloadInterval": "google.protobuf.Int64Value",
            "timezone": "string",
            "geobaseEnabled": "google.protobuf.BoolValue",
            "geobaseUri": "string",
            "queryLogRetentionSize": "google.protobuf.Int64Value",
            "queryLogRetentionTime": "google.protobuf.Int64Value",
            "queryThreadLogEnabled": "google.protobuf.BoolValue",
            "queryThreadLogRetentionSize": "google.protobuf.Int64Value",
            "queryThreadLogRetentionTime": "google.protobuf.Int64Value",
            "partLogRetentionSize": "google.protobuf.Int64Value",
            "partLogRetentionTime": "google.protobuf.Int64Value",
            "metricLogEnabled": "google.protobuf.BoolValue",
            "metricLogRetentionSize": "google.protobuf.Int64Value",
            "metricLogRetentionTime": "google.protobuf.Int64Value",
            "traceLogEnabled": "google.protobuf.BoolValue",
            "traceLogRetentionSize": "google.protobuf.Int64Value",
            "traceLogRetentionTime": "google.protobuf.Int64Value",
            "textLogEnabled": "google.protobuf.BoolValue",
            "textLogRetentionSize": "google.protobuf.Int64Value",
            "textLogRetentionTime": "google.protobuf.Int64Value",
            "textLogLevel": "LogLevel",
            "opentelemetrySpanLogEnabled": "google.protobuf.BoolValue",
            "opentelemetrySpanLogRetentionSize": "google.protobuf.Int64Value",
            "opentelemetrySpanLogRetentionTime": "google.protobuf.Int64Value",
            "queryViewsLogEnabled": "google.protobuf.BoolValue",
            "queryViewsLogRetentionSize": "google.protobuf.Int64Value",
            "queryViewsLogRetentionTime": "google.protobuf.Int64Value",
            "asynchronousMetricLogEnabled": "google.protobuf.BoolValue",
            "asynchronousMetricLogRetentionSize": "google.protobuf.Int64Value",
            "asynchronousMetricLogRetentionTime": "google.protobuf.Int64Value",
            "sessionLogEnabled": "google.protobuf.BoolValue",
            "sessionLogRetentionSize": "google.protobuf.Int64Value",
            "sessionLogRetentionTime": "google.protobuf.Int64Value",
            "zookeeperLogEnabled": "google.protobuf.BoolValue",
            "zookeeperLogRetentionSize": "google.protobuf.Int64Value",
            "zookeeperLogRetentionTime": "google.protobuf.Int64Value",
            "asynchronousInsertLogEnabled": "google.protobuf.BoolValue",
            "asynchronousInsertLogRetentionSize": "google.protobuf.Int64Value",
            "asynchronousInsertLogRetentionTime": "google.protobuf.Int64Value",
            "backgroundPoolSize": "google.protobuf.Int64Value",
            "backgroundMergesMutationsConcurrencyRatio": "google.protobuf.Int64Value",
            "backgroundSchedulePoolSize": "google.protobuf.Int64Value",
            "backgroundFetchesPoolSize": "google.protobuf.Int64Value",
            "backgroundMovePoolSize": "google.protobuf.Int64Value",
            "backgroundDistributedSchedulePoolSize": "google.protobuf.Int64Value",
            "backgroundBufferFlushSchedulePoolSize": "google.protobuf.Int64Value",
            "backgroundMessageBrokerSchedulePoolSize": "google.protobuf.Int64Value",
            "backgroundCommonPoolSize": "google.protobuf.Int64Value",
            "defaultDatabase": "google.protobuf.StringValue",
            "totalMemoryProfilerStep": "google.protobuf.Int64Value",
            "totalMemoryTrackerSampleProbability": "google.protobuf.DoubleValue",
            "queryMaskingRules": [
              {
                "name": "string",
                "regexp": "string",
                "replace": "string"
              }
            ],
            "dictionariesLazyLoad": "google.protobuf.BoolValue",
            "queryCache": {
              "maxSizeInBytes": "google.protobuf.Int64Value",
              "maxEntries": "google.protobuf.Int64Value",
              "maxEntrySizeInBytes": "google.protobuf.Int64Value",
              "maxEntrySizeInRows": "google.protobuf.Int64Value"
            }
          },
          "userConfig": {
            "logLevel": "LogLevel",
            "mergeTree": {
              "replicatedDeduplicationWindow": "google.protobuf.Int64Value",
              "replicatedDeduplicationWindowSeconds": "google.protobuf.Int64Value",
              "partsToDelayInsert": "google.protobuf.Int64Value",
              "partsToThrowInsert": "google.protobuf.Int64Value",
              "inactivePartsToDelayInsert": "google.protobuf.Int64Value",
              "inactivePartsToThrowInsert": "google.protobuf.Int64Value",
              "maxReplicatedMergesInQueue": "google.protobuf.Int64Value",
              "numberOfFreeEntriesInPoolToLowerMaxSizeOfMerge": "google.protobuf.Int64Value",
              "maxBytesToMergeAtMinSpaceInPool": "google.protobuf.Int64Value",
              "maxBytesToMergeAtMaxSpaceInPool": "google.protobuf.Int64Value",
              "minBytesForWidePart": "google.protobuf.Int64Value",
              "minRowsForWidePart": "google.protobuf.Int64Value",
              "ttlOnlyDropParts": "google.protobuf.BoolValue",
              "allowRemoteFsZeroCopyReplication": "google.protobuf.BoolValue",
              "mergeWithTtlTimeout": "google.protobuf.Int64Value",
              "mergeWithRecompressionTtlTimeout": "google.protobuf.Int64Value",
              "maxPartsInTotal": "google.protobuf.Int64Value",
              "maxNumberOfMergesWithTtlInPool": "google.protobuf.Int64Value",
              "cleanupDelayPeriod": "google.protobuf.Int64Value",
              "numberOfFreeEntriesInPoolToExecuteMutation": "google.protobuf.Int64Value",
              "maxAvgPartSizeForTooManyParts": "google.protobuf.Int64Value",
              "minAgeToForceMergeSeconds": "google.protobuf.Int64Value",
              "minAgeToForceMergeOnPartitionOnly": "google.protobuf.BoolValue",
              "mergeSelectingSleepMs": "google.protobuf.Int64Value",
              "mergeMaxBlockSize": "google.protobuf.Int64Value",
              "checkSampleColumnIsCorrect": "google.protobuf.BoolValue",
              "maxMergeSelectingSleepMs": "google.protobuf.Int64Value",
              "maxCleanupDelayPeriod": "google.protobuf.Int64Value"
            },
            "compression": [
              {
                "method": "Method",
                "minPartSize": "int64",
                "minPartSizeRatio": "double",
                "level": "google.protobuf.Int64Value"
              }
            ],
            "dictionaries": [
              {
                "name": "string",
                "structure": {
                  "id": {
                    "name": "string"
                  },
                  "key": {
                    "attributes": [
                      {
                        "name": "string",
                        "type": "string",
                        "nullValue": "string",
                        "expression": "string",
                        "hierarchical": "bool",
                        "injective": "bool"
                      }
                    ]
                  },
                  "rangeMin": {
                    "name": "string",
                    "type": "string",
                    "nullValue": "string",
                    "expression": "string",
                    "hierarchical": "bool",
                    "injective": "bool"
                  },
                  "rangeMax": {
                    "name": "string",
                    "type": "string",
                    "nullValue": "string",
                    "expression": "string",
                    "hierarchical": "bool",
                    "injective": "bool"
                  },
                  "attributes": [
                    {
                      "name": "string",
                      "type": "string",
                      "nullValue": "string",
                      "expression": "string",
                      "hierarchical": "bool",
                      "injective": "bool"
                    }
                  ]
                },
                "layout": {
                  "type": "Type",
                  "sizeInCells": "int64",
                  "maxArraySize": "int64"
                },
                // Includes only one of the fields `fixedLifetime`, `lifetimeRange`
                "fixedLifetime": "int64",
                "lifetimeRange": {
                  "min": "int64",
                  "max": "int64"
                },
                // end of the list of possible fields
                // Includes only one of the fields `httpSource`, `mysqlSource`, `clickhouseSource`, `mongodbSource`, `postgresqlSource`
                "httpSource": {
                  "url": "string",
                  "format": "string",
                  "headers": [
                    {
                      "name": "string",
                      "value": "string"
                    }
                  ]
                },
                "mysqlSource": {
                  "db": "string",
                  "table": "string",
                  "port": "int64",
                  "user": "string",
                  "password": "string",
                  "replicas": [
                    {
                      "host": "string",
                      "priority": "int64",
                      "port": "int64",
                      "user": "string",
                      "password": "string"
                    }
                  ],
                  "where": "string",
                  "invalidateQuery": "string",
                  "closeConnection": "google.protobuf.BoolValue",
                  "shareConnection": "google.protobuf.BoolValue"
                },
                "clickhouseSource": {
                  "db": "string",
                  "table": "string",
                  "host": "string",
                  "port": "int64",
                  "user": "string",
                  "password": "string",
                  "where": "string",
                  "secure": "google.protobuf.BoolValue"
                },
                "mongodbSource": {
                  "db": "string",
                  "collection": "string",
                  "host": "string",
                  "port": "int64",
                  "user": "string",
                  "password": "string",
                  "options": "string"
                },
                "postgresqlSource": {
                  "db": "string",
                  "table": "string",
                  "hosts": [
                    "string"
                  ],
                  "port": "int64",
                  "user": "string",
                  "password": "string",
                  "invalidateQuery": "string",
                  "sslMode": "SslMode"
                }
                // end of the list of possible fields
              }
            ],
            "graphiteRollup": [
              {
                "name": "string",
                "patterns": [
                  {
                    "regexp": "string",
                    "function": "string",
                    "retention": [
                      {
                        "age": "int64",
                        "precision": "int64"
                      }
                    ]
                  }
                ],
                "pathColumnName": "string",
                "timeColumnName": "string",
                "valueColumnName": "string",
                "versionColumnName": "string"
              }
            ],
            "kafka": {
              "securityProtocol": "SecurityProtocol",
              "saslMechanism": "SaslMechanism",
              "saslUsername": "string",
              "saslPassword": "string",
              "enableSslCertificateVerification": "google.protobuf.BoolValue",
              "maxPollIntervalMs": "google.protobuf.Int64Value",
              "sessionTimeoutMs": "google.protobuf.Int64Value",
              "debug": "Debug",
              "autoOffsetReset": "AutoOffsetReset"
            },
            "kafkaTopics": [
              {
                "name": "string",
                "settings": {
                  "securityProtocol": "SecurityProtocol",
                  "saslMechanism": "SaslMechanism",
                  "saslUsername": "string",
                  "saslPassword": "string",
                  "enableSslCertificateVerification": "google.protobuf.BoolValue",
                  "maxPollIntervalMs": "google.protobuf.Int64Value",
                  "sessionTimeoutMs": "google.protobuf.Int64Value",
                  "debug": "Debug",
                  "autoOffsetReset": "AutoOffsetReset"
                }
              }
            ],
            "rabbitmq": {
              "username": "string",
              "password": "string",
              "vhost": "string"
            },
            "maxConnections": "google.protobuf.Int64Value",
            "maxConcurrentQueries": "google.protobuf.Int64Value",
            "keepAliveTimeout": "google.protobuf.Int64Value",
            "uncompressedCacheSize": "google.protobuf.Int64Value",
            "markCacheSize": "google.protobuf.Int64Value",
            "maxTableSizeToDrop": "google.protobuf.Int64Value",
            "maxPartitionSizeToDrop": "google.protobuf.Int64Value",
            "builtinDictionariesReloadInterval": "google.protobuf.Int64Value",
            "timezone": "string",
            "geobaseEnabled": "google.protobuf.BoolValue",
            "geobaseUri": "string",
            "queryLogRetentionSize": "google.protobuf.Int64Value",
            "queryLogRetentionTime": "google.protobuf.Int64Value",
            "queryThreadLogEnabled": "google.protobuf.BoolValue",
            "queryThreadLogRetentionSize": "google.protobuf.Int64Value",
            "queryThreadLogRetentionTime": "google.protobuf.Int64Value",
            "partLogRetentionSize": "google.protobuf.Int64Value",
            "partLogRetentionTime": "google.protobuf.Int64Value",
            "metricLogEnabled": "google.protobuf.BoolValue",
            "metricLogRetentionSize": "google.protobuf.Int64Value",
            "metricLogRetentionTime": "google.protobuf.Int64Value",
            "traceLogEnabled": "google.protobuf.BoolValue",
            "traceLogRetentionSize": "google.protobuf.Int64Value",
            "traceLogRetentionTime": "google.protobuf.Int64Value",
            "textLogEnabled": "google.protobuf.BoolValue",
            "textLogRetentionSize": "google.protobuf.Int64Value",
            "textLogRetentionTime": "google.protobuf.Int64Value",
            "textLogLevel": "LogLevel",
            "opentelemetrySpanLogEnabled": "google.protobuf.BoolValue",
            "opentelemetrySpanLogRetentionSize": "google.protobuf.Int64Value",
            "opentelemetrySpanLogRetentionTime": "google.protobuf.Int64Value",
            "queryViewsLogEnabled": "google.protobuf.BoolValue",
            "queryViewsLogRetentionSize": "google.protobuf.Int64Value",
            "queryViewsLogRetentionTime": "google.protobuf.Int64Value",
            "asynchronousMetricLogEnabled": "google.protobuf.BoolValue",
            "asynchronousMetricLogRetentionSize": "google.protobuf.Int64Value",
            "asynchronousMetricLogRetentionTime": "google.protobuf.Int64Value",
            "sessionLogEnabled": "google.protobuf.BoolValue",
            "sessionLogRetentionSize": "google.protobuf.Int64Value",
            "sessionLogRetentionTime": "google.protobuf.Int64Value",
            "zookeeperLogEnabled": "google.protobuf.BoolValue",
            "zookeeperLogRetentionSize": "google.protobuf.Int64Value",
            "zookeeperLogRetentionTime": "google.protobuf.Int64Value",
            "asynchronousInsertLogEnabled": "google.protobuf.BoolValue",
            "asynchronousInsertLogRetentionSize": "google.protobuf.Int64Value",
            "asynchronousInsertLogRetentionTime": "google.protobuf.Int64Value",
            "backgroundPoolSize": "google.protobuf.Int64Value",
            "backgroundMergesMutationsConcurrencyRatio": "google.protobuf.Int64Value",
            "backgroundSchedulePoolSize": "google.protobuf.Int64Value",
            "backgroundFetchesPoolSize": "google.protobuf.Int64Value",
            "backgroundMovePoolSize": "google.protobuf.Int64Value",
            "backgroundDistributedSchedulePoolSize": "google.protobuf.Int64Value",
            "backgroundBufferFlushSchedulePoolSize": "google.protobuf.Int64Value",
            "backgroundMessageBrokerSchedulePoolSize": "google.protobuf.Int64Value",
            "backgroundCommonPoolSize": "google.protobuf.Int64Value",
            "defaultDatabase": "google.protobuf.StringValue",
            "totalMemoryProfilerStep": "google.protobuf.Int64Value",
            "totalMemoryTrackerSampleProbability": "google.protobuf.DoubleValue",
            "queryMaskingRules": [
              {
                "name": "string",
                "regexp": "string",
                "replace": "string"
              }
            ],
            "dictionariesLazyLoad": "google.protobuf.BoolValue",
            "queryCache": {
              "maxSizeInBytes": "google.protobuf.Int64Value",
              "maxEntries": "google.protobuf.Int64Value",
              "maxEntrySizeInBytes": "google.protobuf.Int64Value",
              "maxEntrySizeInRows": "google.protobuf.Int64Value"
            }
          },
          "defaultConfig": {
            "logLevel": "LogLevel",
            "mergeTree": {
              "replicatedDeduplicationWindow": "google.protobuf.Int64Value",
              "replicatedDeduplicationWindowSeconds": "google.protobuf.Int64Value",
              "partsToDelayInsert": "google.protobuf.Int64Value",
              "partsToThrowInsert": "google.protobuf.Int64Value",
              "inactivePartsToDelayInsert": "google.protobuf.Int64Value",
              "inactivePartsToThrowInsert": "google.protobuf.Int64Value",
              "maxReplicatedMergesInQueue": "google.protobuf.Int64Value",
              "numberOfFreeEntriesInPoolToLowerMaxSizeOfMerge": "google.protobuf.Int64Value",
              "maxBytesToMergeAtMinSpaceInPool": "google.protobuf.Int64Value",
              "maxBytesToMergeAtMaxSpaceInPool": "google.protobuf.Int64Value",
              "minBytesForWidePart": "google.protobuf.Int64Value",
              "minRowsForWidePart": "google.protobuf.Int64Value",
              "ttlOnlyDropParts": "google.protobuf.BoolValue",
              "allowRemoteFsZeroCopyReplication": "google.protobuf.BoolValue",
              "mergeWithTtlTimeout": "google.protobuf.Int64Value",
              "mergeWithRecompressionTtlTimeout": "google.protobuf.Int64Value",
              "maxPartsInTotal": "google.protobuf.Int64Value",
              "maxNumberOfMergesWithTtlInPool": "google.protobuf.Int64Value",
              "cleanupDelayPeriod": "google.protobuf.Int64Value",
              "numberOfFreeEntriesInPoolToExecuteMutation": "google.protobuf.Int64Value",
              "maxAvgPartSizeForTooManyParts": "google.protobuf.Int64Value",
              "minAgeToForceMergeSeconds": "google.protobuf.Int64Value",
              "minAgeToForceMergeOnPartitionOnly": "google.protobuf.BoolValue",
              "mergeSelectingSleepMs": "google.protobuf.Int64Value",
              "mergeMaxBlockSize": "google.protobuf.Int64Value",
              "checkSampleColumnIsCorrect": "google.protobuf.BoolValue",
              "maxMergeSelectingSleepMs": "google.protobuf.Int64Value",
              "maxCleanupDelayPeriod": "google.protobuf.Int64Value"
            },
            "compression": [
              {
                "method": "Method",
                "minPartSize": "int64",
                "minPartSizeRatio": "double",
                "level": "google.protobuf.Int64Value"
              }
            ],
            "dictionaries": [
              {
                "name": "string",
                "structure": {
                  "id": {
                    "name": "string"
                  },
                  "key": {
                    "attributes": [
                      {
                        "name": "string",
                        "type": "string",
                        "nullValue": "string",
                        "expression": "string",
                        "hierarchical": "bool",
                        "injective": "bool"
                      }
                    ]
                  },
                  "rangeMin": {
                    "name": "string",
                    "type": "string",
                    "nullValue": "string",
                    "expression": "string",
                    "hierarchical": "bool",
                    "injective": "bool"
                  },
                  "rangeMax": {
                    "name": "string",
                    "type": "string",
                    "nullValue": "string",
                    "expression": "string",
                    "hierarchical": "bool",
                    "injective": "bool"
                  },
                  "attributes": [
                    {
                      "name": "string",
                      "type": "string",
                      "nullValue": "string",
                      "expression": "string",
                      "hierarchical": "bool",
                      "injective": "bool"
                    }
                  ]
                },
                "layout": {
                  "type": "Type",
                  "sizeInCells": "int64",
                  "maxArraySize": "int64"
                },
                // Includes only one of the fields `fixedLifetime`, `lifetimeRange`
                "fixedLifetime": "int64",
                "lifetimeRange": {
                  "min": "int64",
                  "max": "int64"
                },
                // end of the list of possible fields
                // Includes only one of the fields `httpSource`, `mysqlSource`, `clickhouseSource`, `mongodbSource`, `postgresqlSource`
                "httpSource": {
                  "url": "string",
                  "format": "string",
                  "headers": [
                    {
                      "name": "string",
                      "value": "string"
                    }
                  ]
                },
                "mysqlSource": {
                  "db": "string",
                  "table": "string",
                  "port": "int64",
                  "user": "string",
                  "password": "string",
                  "replicas": [
                    {
                      "host": "string",
                      "priority": "int64",
                      "port": "int64",
                      "user": "string",
                      "password": "string"
                    }
                  ],
                  "where": "string",
                  "invalidateQuery": "string",
                  "closeConnection": "google.protobuf.BoolValue",
                  "shareConnection": "google.protobuf.BoolValue"
                },
                "clickhouseSource": {
                  "db": "string",
                  "table": "string",
                  "host": "string",
                  "port": "int64",
                  "user": "string",
                  "password": "string",
                  "where": "string",
                  "secure": "google.protobuf.BoolValue"
                },
                "mongodbSource": {
                  "db": "string",
                  "collection": "string",
                  "host": "string",
                  "port": "int64",
                  "user": "string",
                  "password": "string",
                  "options": "string"
                },
                "postgresqlSource": {
                  "db": "string",
                  "table": "string",
                  "hosts": [
                    "string"
                  ],
                  "port": "int64",
                  "user": "string",
                  "password": "string",
                  "invalidateQuery": "string",
                  "sslMode": "SslMode"
                }
                // end of the list of possible fields
              }
            ],
            "graphiteRollup": [
              {
                "name": "string",
                "patterns": [
                  {
                    "regexp": "string",
                    "function": "string",
                    "retention": [
                      {
                        "age": "int64",
                        "precision": "int64"
                      }
                    ]
                  }
                ],
                "pathColumnName": "string",
                "timeColumnName": "string",
                "valueColumnName": "string",
                "versionColumnName": "string"
              }
            ],
            "kafka": {
              "securityProtocol": "SecurityProtocol",
              "saslMechanism": "SaslMechanism",
              "saslUsername": "string",
              "saslPassword": "string",
              "enableSslCertificateVerification": "google.protobuf.BoolValue",
              "maxPollIntervalMs": "google.protobuf.Int64Value",
              "sessionTimeoutMs": "google.protobuf.Int64Value",
              "debug": "Debug",
              "autoOffsetReset": "AutoOffsetReset"
            },
            "kafkaTopics": [
              {
                "name": "string",
                "settings": {
                  "securityProtocol": "SecurityProtocol",
                  "saslMechanism": "SaslMechanism",
                  "saslUsername": "string",
                  "saslPassword": "string",
                  "enableSslCertificateVerification": "google.protobuf.BoolValue",
                  "maxPollIntervalMs": "google.protobuf.Int64Value",
                  "sessionTimeoutMs": "google.protobuf.Int64Value",
                  "debug": "Debug",
                  "autoOffsetReset": "AutoOffsetReset"
                }
              }
            ],
            "rabbitmq": {
              "username": "string",
              "password": "string",
              "vhost": "string"
            },
            "maxConnections": "google.protobuf.Int64Value",
            "maxConcurrentQueries": "google.protobuf.Int64Value",
            "keepAliveTimeout": "google.protobuf.Int64Value",
            "uncompressedCacheSize": "google.protobuf.Int64Value",
            "markCacheSize": "google.protobuf.Int64Value",
            "maxTableSizeToDrop": "google.protobuf.Int64Value",
            "maxPartitionSizeToDrop": "google.protobuf.Int64Value",
            "builtinDictionariesReloadInterval": "google.protobuf.Int64Value",
            "timezone": "string",
            "geobaseEnabled": "google.protobuf.BoolValue",
            "geobaseUri": "string",
            "queryLogRetentionSize": "google.protobuf.Int64Value",
            "queryLogRetentionTime": "google.protobuf.Int64Value",
            "queryThreadLogEnabled": "google.protobuf.BoolValue",
            "queryThreadLogRetentionSize": "google.protobuf.Int64Value",
            "queryThreadLogRetentionTime": "google.protobuf.Int64Value",
            "partLogRetentionSize": "google.protobuf.Int64Value",
            "partLogRetentionTime": "google.protobuf.Int64Value",
            "metricLogEnabled": "google.protobuf.BoolValue",
            "metricLogRetentionSize": "google.protobuf.Int64Value",
            "metricLogRetentionTime": "google.protobuf.Int64Value",
            "traceLogEnabled": "google.protobuf.BoolValue",
            "traceLogRetentionSize": "google.protobuf.Int64Value",
            "traceLogRetentionTime": "google.protobuf.Int64Value",
            "textLogEnabled": "google.protobuf.BoolValue",
            "textLogRetentionSize": "google.protobuf.Int64Value",
            "textLogRetentionTime": "google.protobuf.Int64Value",
            "textLogLevel": "LogLevel",
            "opentelemetrySpanLogEnabled": "google.protobuf.BoolValue",
            "opentelemetrySpanLogRetentionSize": "google.protobuf.Int64Value",
            "opentelemetrySpanLogRetentionTime": "google.protobuf.Int64Value",
            "queryViewsLogEnabled": "google.protobuf.BoolValue",
            "queryViewsLogRetentionSize": "google.protobuf.Int64Value",
            "queryViewsLogRetentionTime": "google.protobuf.Int64Value",
            "asynchronousMetricLogEnabled": "google.protobuf.BoolValue",
            "asynchronousMetricLogRetentionSize": "google.protobuf.Int64Value",
            "asynchronousMetricLogRetentionTime": "google.protobuf.Int64Value",
            "sessionLogEnabled": "google.protobuf.BoolValue",
            "sessionLogRetentionSize": "google.protobuf.Int64Value",
            "sessionLogRetentionTime": "google.protobuf.Int64Value",
            "zookeeperLogEnabled": "google.protobuf.BoolValue",
            "zookeeperLogRetentionSize": "google.protobuf.Int64Value",
            "zookeeperLogRetentionTime": "google.protobuf.Int64Value",
            "asynchronousInsertLogEnabled": "google.protobuf.BoolValue",
            "asynchronousInsertLogRetentionSize": "google.protobuf.Int64Value",
            "asynchronousInsertLogRetentionTime": "google.protobuf.Int64Value",
            "backgroundPoolSize": "google.protobuf.Int64Value",
            "backgroundMergesMutationsConcurrencyRatio": "google.protobuf.Int64Value",
            "backgroundSchedulePoolSize": "google.protobuf.Int64Value",
            "backgroundFetchesPoolSize": "google.protobuf.Int64Value",
            "backgroundMovePoolSize": "google.protobuf.Int64Value",
            "backgroundDistributedSchedulePoolSize": "google.protobuf.Int64Value",
            "backgroundBufferFlushSchedulePoolSize": "google.protobuf.Int64Value",
            "backgroundMessageBrokerSchedulePoolSize": "google.protobuf.Int64Value",
            "backgroundCommonPoolSize": "google.protobuf.Int64Value",
            "defaultDatabase": "google.protobuf.StringValue",
            "totalMemoryProfilerStep": "google.protobuf.Int64Value",
            "totalMemoryTrackerSampleProbability": "google.protobuf.DoubleValue",
            "queryMaskingRules": [
              {
                "name": "string",
                "regexp": "string",
                "replace": "string"
              }
            ],
            "dictionariesLazyLoad": "google.protobuf.BoolValue",
            "queryCache": {
              "maxSizeInBytes": "google.protobuf.Int64Value",
              "maxEntries": "google.protobuf.Int64Value",
              "maxEntrySizeInBytes": "google.protobuf.Int64Value",
              "maxEntrySizeInRows": "google.protobuf.Int64Value"
            }
          }
        },
        "resources": {
          "resourcePresetId": "string",
          "diskSize": "int64",
          "diskTypeId": "string"
        }
      },
      "zookeeper": {
        "resources": {
          "resourcePresetId": "string",
          "diskSize": "int64",
          "diskTypeId": "string"
        }
      },
      "backupWindowStart": "google.type.TimeOfDay",
      "access": {
        "dataLens": "bool",
        "webSql": "bool",
        "metrika": "bool",
        "serverless": "bool",
        "dataTransfer": "bool",
        "yandexQuery": "bool"
      },
      "cloudStorage": {
        "enabled": "bool",
        "moveFactor": "google.protobuf.DoubleValue",
        "dataCacheEnabled": "google.protobuf.BoolValue",
        "dataCacheMaxSize": "google.protobuf.Int64Value",
        "preferNotToMerge": "google.protobuf.BoolValue"
      },
      "sqlDatabaseManagement": "google.protobuf.BoolValue",
      "sqlUserManagement": "google.protobuf.BoolValue",
      "embeddedKeeper": "google.protobuf.BoolValue",
      "backupRetainPeriodDays": "google.protobuf.Int64Value"
    },
    "networkId": "string",
    "health": "Health",
    "status": "Status",
    "serviceAccountId": "string",
    "maintenanceWindow": {
      // Includes only one of the fields `anytime`, `weeklyMaintenanceWindow`
      "anytime": "AnytimeMaintenanceWindow",
      "weeklyMaintenanceWindow": {
        "day": "WeekDay",
        "hour": "int64"
      }
      // end of the list of possible fields
    },
    "plannedOperation": {
      "info": "string",
      "delayedUntil": "google.protobuf.Timestamp"
    },
    "securityGroupIds": [
      "string"
    ],
    "deletionProtection": "bool"
  }
  // end of the list of possible fields
}
```

An Operation resource. For more information, see [Operation](/docs/api-design-guide/concepts/operation).

#|
||Field | Description ||
|| id | **string**

ID of the operation. ||
|| description | **string**

Description of the operation. 0-256 characters long. ||
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Creation timestamp. ||
|| createdBy | **string**

ID of the user or service account who initiated the operation. ||
|| modifiedAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

The time when the Operation resource was last modified. ||
|| done | **bool**

If the value is `false`, it means the operation is still in progress.
If `true`, the operation is completed, and either `error` or `response` is available. ||
|| metadata | **[StopClusterMetadata](#yandex.cloud.mdb.clickhouse.v1.StopClusterMetadata)**

Service-specific metadata associated with the operation.
It typically contains the ID of the target resource that the operation is performed on.
Any method that returns a long-running operation should document the metadata type, if any. ||
|| error | **[google.rpc.Status](https://cloud.google.com/tasks/docs/reference/rpc/google.rpc#status)**

The error result of the operation in case of failure or cancellation.

Includes only one of the fields `error`, `response`.

The operation result.
If `done == false` and there was no failure detected, neither `error` nor `response` is set.
If `done == false` and there was a failure detected, `error` is set.
If `done == true`, exactly one of `error` or `response` is set. ||
|| response | **[Cluster](#yandex.cloud.mdb.clickhouse.v1.Cluster)**

The normal response of the operation in case of success.
If the original method returns no data on success, such as Delete,
the response is [google.protobuf.Empty](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#google.protobuf.Empty).
If the original method is the standard Create/Update,
the response should be the target resource of the operation.
Any method that returns a long-running operation should document the response type, if any.

Includes only one of the fields `error`, `response`.

The operation result.
If `done == false` and there was no failure detected, neither `error` nor `response` is set.
If `done == false` and there was a failure detected, `error` is set.
If `done == true`, exactly one of `error` or `response` is set. ||
|#

## StopClusterMetadata {#yandex.cloud.mdb.clickhouse.v1.StopClusterMetadata}

#|
||Field | Description ||
|| clusterId | **string**

ID of the ClickHouse cluster being stopped. ||
|#

## Cluster {#yandex.cloud.mdb.clickhouse.v1.Cluster}

A ClickHouse Cluster resource. For more information, see the
[Cluster](/docs/managed-clickhouse/concepts) section in the Developer's Guide.

#|
||Field | Description ||
|| id | **string**

ID of the ClickHouse cluster.
This ID is assigned by MDB at creation time. ||
|| folderId | **string**

ID of the folder that the ClickHouse cluster belongs to. ||
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Creation timestamp in [RFC3339](https://www.ietf.org/rfc/rfc3339.txt) text format. ||
|| name | **string**

Name of the ClickHouse cluster.
The name is unique within the folder. 1-63 characters long. ||
|| description | **string**

Description of the ClickHouse cluster. 0-256 characters long. ||
|| labels | **string**

Custom labels for the ClickHouse cluster as `key:value` pairs. Maximum 64 per resource. ||
|| environment | enum **Environment**

Deployment environment of the ClickHouse cluster.

- `ENVIRONMENT_UNSPECIFIED`
- `PRODUCTION`: Stable environment with a conservative update policy:
only hotfixes are applied during regular maintenance.
- `PRESTABLE`: Environment with more aggressive update policy: new versions
are rolled out irrespective of backward compatibility. ||
|| monitoring[] | **[Monitoring](#yandex.cloud.mdb.clickhouse.v1.Monitoring)**

Description of monitoring systems relevant to the ClickHouse cluster. ||
|| config | **[ClusterConfig](#yandex.cloud.mdb.clickhouse.v1.ClusterConfig)**

Configuration of the ClickHouse cluster. ||
|| networkId | **string**

ID of the network that the cluster belongs to. ||
|| health | enum **Health**

Aggregated cluster health.

- `HEALTH_UNKNOWN`: State of the cluster is unknown ([Host.health](/docs/managed-clickhouse/api-ref/grpc/Cluster/listHosts#yandex.cloud.mdb.clickhouse.v1.Host) for every host in the cluster is UNKNOWN).
- `ALIVE`: Cluster is alive and well ([Host.health](/docs/managed-clickhouse/api-ref/grpc/Cluster/listHosts#yandex.cloud.mdb.clickhouse.v1.Host) for every host in the cluster is ALIVE).
- `DEAD`: Cluster is inoperable ([Host.health](/docs/managed-clickhouse/api-ref/grpc/Cluster/listHosts#yandex.cloud.mdb.clickhouse.v1.Host) for every host in the cluster is DEAD).
- `DEGRADED`: Cluster is working below capacity ([Host.health](/docs/managed-clickhouse/api-ref/grpc/Cluster/listHosts#yandex.cloud.mdb.clickhouse.v1.Host) for at least one host in the cluster is not ALIVE). ||
|| status | enum **Status**

Current state of the cluster.

- `STATUS_UNKNOWN`: Cluster state is unknown.
- `CREATING`: Cluster is being created.
- `RUNNING`: Cluster is running normally.
- `ERROR`: Cluster encountered a problem and cannot operate.
- `UPDATING`: Cluster is being updated.
- `STOPPING`: Cluster is stopping.
- `STOPPED`: Cluster stopped.
- `STARTING`: Cluster is starting. ||
|| serviceAccountId | **string**

ID of the service account used for access to Object Storage. ||
|| maintenanceWindow | **[MaintenanceWindow](#yandex.cloud.mdb.clickhouse.v1.MaintenanceWindow)**

Maintenance window for the cluster. ||
|| plannedOperation | **[MaintenanceOperation](#yandex.cloud.mdb.clickhouse.v1.MaintenanceOperation)**

Planned maintenance operation to be started for the cluster within the nearest `maintenanceWindow`. ||
|| securityGroupIds[] | **string**

User security groups ||
|| deletionProtection | **bool**

Deletion Protection inhibits deletion of the cluster ||
|#

## Monitoring {#yandex.cloud.mdb.clickhouse.v1.Monitoring}

Monitoring system metadata.

#|
||Field | Description ||
|| name | **string**

Name of the monitoring system. ||
|| description | **string**

Description of the monitoring system. ||
|| link | **string**

Link to the monitoring system charts for the ClickHouse cluster. ||
|#

## ClusterConfig {#yandex.cloud.mdb.clickhouse.v1.ClusterConfig}

#|
||Field | Description ||
|| version | **string**

Version of the ClickHouse server software. ||
|| clickhouse | **[Clickhouse](#yandex.cloud.mdb.clickhouse.v1.ClusterConfig.Clickhouse)**

Configuration and resource allocation for ClickHouse hosts. ||
|| zookeeper | **[Zookeeper](#yandex.cloud.mdb.clickhouse.v1.ClusterConfig.Zookeeper)**

Configuration and resource allocation for ZooKeeper hosts. ||
|| backupWindowStart | **[google.type.TimeOfDay](https://github.com/googleapis/googleapis/blob/master/google/type/timeofday.proto)**

Time to start the daily backup, in the UTC timezone. ||
|| access | **[Access](#yandex.cloud.mdb.clickhouse.v1.Access)**

Access policy for external services. ||
|| cloudStorage | **[CloudStorage](#yandex.cloud.mdb.clickhouse.v1.CloudStorage)** ||
|| sqlDatabaseManagement | **[google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value)**

Whether database management through SQL commands is enabled. ||
|| sqlUserManagement | **[google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value)**

Whether user management through SQL commands is enabled. ||
|| embeddedKeeper | **[google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value)**

Whether cluster should use embedded Keeper instead of Zookeeper. ||
|| backupRetainPeriodDays | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

Retain period of automatically created backup in days ||
|#

## Clickhouse {#yandex.cloud.mdb.clickhouse.v1.ClusterConfig.Clickhouse}

#|
||Field | Description ||
|| config | **[ClickhouseConfigSet](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfigSet)**

Configuration settings of a ClickHouse server. ||
|| resources | **[Resources](#yandex.cloud.mdb.clickhouse.v1.Resources)**

Resources allocated to ClickHouse hosts. ||
|#

## ClickhouseConfigSet {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfigSet}

#|
||Field | Description ||
|| effectiveConfig | **[ClickhouseConfig](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig)**

Required field. Effective settings for a ClickHouse cluster (a combination of settings defined
in `userConfig` and `defaultConfig`). ||
|| userConfig | **[ClickhouseConfig](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig)**

User-defined settings for a ClickHouse cluster. ||
|| defaultConfig | **[ClickhouseConfig](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig)**

Default configuration for a ClickHouse cluster. ||
|#

## ClickhouseConfig {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig}

ClickHouse configuration options. Detailed description for each set of options
is available in [ClickHouse documentation](https://clickhouse.com/docs/en/operations/server_settings/settings/).

Any options not listed here are not supported.

#|
||Field | Description ||
|| logLevel | enum **LogLevel**

Logging level for the ClickHouse cluster. Possible values: TRACE, DEBUG, INFORMATION, WARNING, ERROR.

- `LOG_LEVEL_UNSPECIFIED`
- `TRACE`
- `DEBUG`
- `INFORMATION`
- `WARNING`
- `ERROR` ||
|| mergeTree | **[MergeTree](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.MergeTree)**

Settings for the MergeTree engine.
See description in [ClickHouse documentation](https://clickhouse.com/docs/en/operations/server_settings/settings/#merge_tree). ||
|| compression[] | **[Compression](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.Compression)**

Compression settings for the ClickHouse cluster.
See in-depth description in [ClickHouse documentation](https://clickhouse.com/docs/en/operations/server_settings/settings/#compression). ||
|| dictionaries[] | **[ExternalDictionary](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary)**

Configuration of external dictionaries to be used by the ClickHouse cluster.
See in-depth description in [ClickHouse documentation](https://clickhouse.com/docs/en/query_language/dicts/external_dicts/). ||
|| graphiteRollup[] | **[GraphiteRollup](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.GraphiteRollup)**

Settings for thinning Graphite data.
See in-depth description in [ClickHouse documentation](https://clickhouse.com/docs/en/operations/server_settings/settings/#server_settings-graphite_rollup). ||
|| kafka | **[Kafka](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.Kafka)** ||
|| kafkaTopics[] | **[KafkaTopic](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.KafkaTopic)** ||
|| rabbitmq | **[Rabbitmq](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.Rabbitmq)** ||
|| maxConnections | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

Maximum number of inbound connections. ||
|| maxConcurrentQueries | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

Maximum number of simultaneously processed requests. ||
|| keepAliveTimeout | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

Number of milliseconds that ClickHouse waits for incoming requests before closing the connection. ||
|| uncompressedCacheSize | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

Cache size (in bytes) for uncompressed data used by MergeTree tables. ||
|| markCacheSize | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

Approximate size (in bytes) of the cache of "marks" used by MergeTree tables. ||
|| maxTableSizeToDrop | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

Maximum size of the table that can be deleted using a DROP query. ||
|| maxPartitionSizeToDrop | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

Maximum size of the partition that can be deleted using a DROP query. ||
|| builtinDictionariesReloadInterval | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The setting is deprecated and has no effect. ||
|| timezone | **string**

The server's time zone to be used in DateTime fields conversions. Specified as an IANA identifier. ||
|| geobaseEnabled | **[google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value)**

Enable or disable geobase. ||
|| geobaseUri | **string**

Address of the archive with the user geobase in Object Storage. ||
|| queryLogRetentionSize | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum size that query_log can grow to before old data will be removed. If set to 0, automatic removal of
query_log data based on size is disabled. ||
|| queryLogRetentionTime | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum time that query_log records will be retained before removal. If set to 0, automatic removal of
query_log data based on time is disabled. ||
|| queryThreadLogEnabled | **[google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value)**

Whether query_thread_log system table is enabled. ||
|| queryThreadLogRetentionSize | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum size that query_thread_log can grow to before old data will be removed. If set to 0, automatic removal of
query_thread_log data based on size is disabled. ||
|| queryThreadLogRetentionTime | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum time that query_thread_log records will be retained before removal. If set to 0, automatic removal of
query_thread_log data based on time is disabled. ||
|| partLogRetentionSize | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum size that part_log can grow to before old data will be removed. If set to 0, automatic removal of
part_log data based on size is disabled. ||
|| partLogRetentionTime | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum time that part_log records will be retained before removal. If set to 0, automatic removal of
part_log data based on time is disabled. ||
|| metricLogEnabled | **[google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value)**

Whether metric_log system table is enabled. ||
|| metricLogRetentionSize | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum size that metric_log can grow to before old data will be removed. If set to 0, automatic removal of
metric_log data based on size is disabled. ||
|| metricLogRetentionTime | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum time that metric_log records will be retained before removal. If set to 0, automatic removal of
metric_log data based on time is disabled. ||
|| traceLogEnabled | **[google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value)**

Whether trace_log system table is enabled. ||
|| traceLogRetentionSize | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum size that trace_log can grow to before old data will be removed. If set to 0, automatic removal of
trace_log data based on size is disabled. ||
|| traceLogRetentionTime | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum time that trace_log records will be retained before removal. If set to 0, automatic removal of
trace_log data based on time is disabled. ||
|| textLogEnabled | **[google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value)**

Whether text_log system table is enabled. ||
|| textLogRetentionSize | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum size that text_log can grow to before old data will be removed. If set to 0, automatic removal of
text_log data based on size is disabled. ||
|| textLogRetentionTime | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum time that text_log records will be retained before removal. If set to 0, automatic removal of
text_log data based on time is disabled. ||
|| textLogLevel | enum **LogLevel**

Logging level for text_log system table. Possible values: TRACE, DEBUG, INFORMATION, WARNING, ERROR.

- `LOG_LEVEL_UNSPECIFIED`
- `TRACE`
- `DEBUG`
- `INFORMATION`
- `WARNING`
- `ERROR` ||
|| opentelemetrySpanLogEnabled | **[google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value)**

Enable or disable opentelemetry_span_log system table. Default value: false. ||
|| opentelemetrySpanLogRetentionSize | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum size that opentelemetry_span_log can grow to before old data will be removed. If set to 0 (default),
automatic removal of opentelemetry_span_log data based on size is disabled. ||
|| opentelemetrySpanLogRetentionTime | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum time that opentelemetry_span_log records will be retained before removal. If set to 0,
automatic removal of opentelemetry_span_log data based on time is disabled. ||
|| queryViewsLogEnabled | **[google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value)**

Enable or disable query_views_log system table. Default value: false. ||
|| queryViewsLogRetentionSize | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum size that query_views_log can grow to before old data will be removed. If set to 0 (default),
automatic removal of query_views_log data based on size is disabled. ||
|| queryViewsLogRetentionTime | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum time that query_views_log records will be retained before removal. If set to 0,
automatic removal of query_views_log data based on time is disabled. ||
|| asynchronousMetricLogEnabled | **[google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value)**

Enable or disable asynchronous_metric_log system table. Default value: false. ||
|| asynchronousMetricLogRetentionSize | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum size that asynchronous_metric_log can grow to before old data will be removed. If set to 0 (default),
automatic removal of asynchronous_metric_log data based on size is disabled. ||
|| asynchronousMetricLogRetentionTime | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum time that asynchronous_metric_log records will be retained before removal. If set to 0,
automatic removal of asynchronous_metric_log data based on time is disabled. ||
|| sessionLogEnabled | **[google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value)**

Enable or disable session_log system table. Default value: false. ||
|| sessionLogRetentionSize | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum size that session_log can grow to before old data will be removed. If set to 0 (default),
automatic removal of session_log data based on size is disabled. ||
|| sessionLogRetentionTime | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum time that session_log records will be retained before removal. If set to 0,
automatic removal of session_log data based on time is disabled. ||
|| zookeeperLogEnabled | **[google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value)**

Enable or disable zookeeper_log system table. Default value: false. ||
|| zookeeperLogRetentionSize | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum size that zookeeper_log can grow to before old data will be removed. If set to 0 (default),
automatic removal of zookeeper_log data based on size is disabled. ||
|| zookeeperLogRetentionTime | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum time that zookeeper_log records will be retained before removal. If set to 0,
automatic removal of zookeeper_log data based on time is disabled. ||
|| asynchronousInsertLogEnabled | **[google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value)**

Enable or disable asynchronous_insert_log system table. Default value: false.
Minimal required ClickHouse version: 22.10. ||
|| asynchronousInsertLogRetentionSize | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum size that asynchronous_insert_log can grow to before old data will be removed. If set to 0 (default),
automatic removal of asynchronous_insert_log data based on size is disabled. ||
|| asynchronousInsertLogRetentionTime | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum time that asynchronous_insert_log records will be retained before removal. If set to 0,
automatic removal of asynchronous_insert_log data based on time is disabled. ||
|| backgroundPoolSize | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)** ||
|| backgroundMergesMutationsConcurrencyRatio | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

Sets a ratio between the number of threads and the number of background merges and mutations that can be executed concurrently. For example, if the ratio equals to 2 and background_pool_size is set to 16 then ClickHouse can execute 32 background merges concurrently. This is possible, because background operations could be suspended and postponed. This is needed to give small merges more execution priority. You can only increase this ratio at runtime. To lower it you have to restart the server. The same as for background_pool_size setting background_merges_mutations_concurrency_ratio could be applied from the default profile for backward compatibility.
Default: 2
See in-depth description in [ClickHouse documentation](https://clickhouse.com/docs/en/operations/server-configuration-parameters/settings#background_merges_mutations_concurrency_ratio) ||
|| backgroundSchedulePoolSize | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)** ||
|| backgroundFetchesPoolSize | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

Sets the number of threads performing background fetches for tables with **ReplicatedMergeTree** engines. Default value: 8.

More info see in [ClickHouse documentation](https://clickhouse.com/docs/en/operations/server-configuration-parameters/settings/#background_fetches_pool_size). ||
|| backgroundMovePoolSize | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)** ||
|| backgroundDistributedSchedulePoolSize | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)** ||
|| backgroundBufferFlushSchedulePoolSize | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)** ||
|| backgroundMessageBrokerSchedulePoolSize | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)** ||
|| backgroundCommonPoolSize | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum number of threads that will be used for performing a variety of operations (mostly garbage collection) for *MergeTree-engine tables in a background.
Default: 8
See in-depth description in [ClickHouse documentation](https://clickhouse.com/docs/en/operations/server-configuration-parameters/settings#background_common_pool_size) ||
|| defaultDatabase | **[google.protobuf.StringValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/string-value)**

The default database.

To get a list of cluster databases, see [Yandex Managed ClickHouse documentation](/docs/managed-clickhouse/operations/databases#list-db). ||
|| totalMemoryProfilerStep | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

Sets the memory size (in bytes) for a stack trace at every peak allocation step. Default value: **4194304**.

More info see in [ClickHouse documentation](https://clickhouse.com/docs/en/operations/server-configuration-parameters/settings/#total-memory-profiler-step). ||
|| totalMemoryTrackerSampleProbability | **[google.protobuf.DoubleValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/double-value)** ||
|| queryMaskingRules[] | **[QueryMaskingRule](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.QueryMaskingRule)**

Regexp-based rules, which will be applied to queries as well as all log messages before storing them in server logs, system.query_log, system.text_log, system.processes tables, and in logs sent to the client. That allows preventing sensitive data leakage from SQL queries (like names, emails, personal identifiers or credit card numbers) to logs.
Change of these settings is applied with ClickHouse restart
See in-depth description in [ClickHouse documentation](https://clickhouse.com/docs/en/operations/server-configuration-parameters/settings#query-masking-rules) ||
|| dictionariesLazyLoad | **[google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value)**

Lazy loading of dictionaries.
Default: true
See in-depth description in [ClickHouse documentation](https://clickhouse.com/docs/en/operations/server-configuration-parameters/settings#dictionaries_lazy_load) ||
|| queryCache | **[QueryCache](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.QueryCache)**

[Query cache](https://clickhouse.com/docs/en/operations/query-cache) configuration.
Min version: 23.5
See in-depth description in [ClickHouse documentation](https://clickhouse.com/docs/en/operations/server-configuration-parameters/settings#query_cache) ||
|#

## MergeTree {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.MergeTree}

Options specific to the MergeTree table engine.

#|
||Field | Description ||
|| replicatedDeduplicationWindow | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

Number of blocks of hashes to keep in ZooKeeper. ||
|| replicatedDeduplicationWindowSeconds | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

Period of time to keep blocks of hashes for. ||
|| partsToDelayInsert | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

If table contains at least that many active parts in single partition, artificially slow down insert into table. ||
|| partsToThrowInsert | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

If more than this number active parts in single partition, throw 'Too many parts ...' exception. ||
|| inactivePartsToDelayInsert | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)** ||
|| inactivePartsToThrowInsert | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)** ||
|| maxReplicatedMergesInQueue | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

How many tasks of merging and mutating parts are allowed simultaneously in ReplicatedMergeTree queue. ||
|| numberOfFreeEntriesInPoolToLowerMaxSizeOfMerge | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

If there is less than specified number of free entries in background pool (or replicated queue), start to lower
maximum size of merge to process. ||
|| maxBytesToMergeAtMinSpaceInPool | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

Maximum in total size of parts to merge, when there are minimum free threads in background pool (or entries
in replication queue). ||
|| maxBytesToMergeAtMaxSpaceInPool | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)** ||
|| minBytesForWidePart | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

Minimum number of bytes in a data part that can be stored in **Wide** format.

More info see in [ClickHouse documentation](https://clickhouse.com/docs/en/engines/table-engines/mergetree-family/mergetree/#min_bytes_for_wide_part). ||
|| minRowsForWidePart | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

Minimum number of rows in a data part that can be stored in **Wide** format.

More info see in [ClickHouse documentation](https://clickhouse.com/docs/en/engines/table-engines/mergetree-family/mergetree/#min_bytes_for_wide_part). ||
|| ttlOnlyDropParts | **[google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value)**

Enables or disables complete dropping of data parts where all rows are expired in MergeTree tables.

More info see in [ClickHouse documentation](https://clickhouse.com/docs/en/operations/settings/settings/#ttl_only_drop_parts). ||
|| allowRemoteFsZeroCopyReplication | **[google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value)** ||
|| mergeWithTtlTimeout | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)** ||
|| mergeWithRecompressionTtlTimeout | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)** ||
|| maxPartsInTotal | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)** ||
|| maxNumberOfMergesWithTtlInPool | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)** ||
|| cleanupDelayPeriod | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)** ||
|| numberOfFreeEntriesInPoolToExecuteMutation | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)** ||
|| maxAvgPartSizeForTooManyParts | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The 'too many parts' check according to 'parts_to_delay_insert' and 'parts_to_throw_insert' will be active only if the average part size (in the relevant partition) is not larger than the specified threshold. If it is larger than the specified threshold, the INSERTs will be neither delayed or rejected. This allows to have hundreds of terabytes in a single table on a single server if the parts are successfully merged to larger parts. This does not affect the thresholds on inactive parts or total parts.
Default: 1 GiB
Min version: 22.10
See in-depth description in [ClickHouse GitHub](https://github.com/ClickHouse/ClickHouse/blob/f9558345e886876b9132d9c018e357f7fa9b22a3/src/Storages/MergeTree/MergeTreeSettings.h#L80) ||
|| minAgeToForceMergeSeconds | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

Merge parts if every part in the range is older than the value of min_age_to_force_merge_seconds.
Default: 0 - disabled
Min_version: 22.10
See in-depth description in [ClickHouse documentation](https://clickhouse.com/docs/en/operations/settings/merge-tree-settings#min_age_to_force_merge_seconds) ||
|| minAgeToForceMergeOnPartitionOnly | **[google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value)**

Whether min_age_to_force_merge_seconds should be applied only on the entire partition and not on subset.
Default: false
Min_version: 22.11
See in-depth description in [ClickHouse documentation](https://clickhouse.com/docs/en/operations/settings/merge-tree-settings#min_age_to_force_merge_seconds) ||
|| mergeSelectingSleepMs | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

Sleep time for merge selecting when no part is selected. A lower setting triggers selecting tasks in background_schedule_pool frequently, which results in a large number of requests to ClickHouse Keeper in large-scale clusters.
Default: 5000
Min_version: 21.10
See in-depth description in [ClickHouse documentation](https://clickhouse.com/docs/en/operations/settings/settings#merge_selecting_sleep_ms) ||
|| mergeMaxBlockSize | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The number of rows that are read from the merged parts into memory.
Default: 8192
See in-depth description in [ClickHouse documentation](https://clickhouse.com/docs/en/operations/settings/settings#merge_max_block_size) ||
|| checkSampleColumnIsCorrect | **[google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value)**

Enables the check at table creation, that the data type of a column for sampling or sampling expression is correct. The data type must be one of unsigned [integer types](https://clickhouse.com/docs/en/sql-reference/data-types/int-uint): UInt8, UInt16, UInt32, UInt64.
Default: true
See in-depth description in [ClickHouse documentation](https://clickhouse.com/docs/en/operations/settings/merge-tree-settings#check_sample_column_is_correct) ||
|| maxMergeSelectingSleepMs | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

Maximum sleep time for merge selecting, a lower setting will trigger selecting tasks in background_schedule_pool frequently which result in large amount of requests to zookeeper in large-scale clusters.
Default: 60000
Min_version: 23.6
See in-depth description in [ClickHouse GitHub](https://github.com/ClickHouse/ClickHouse/blob/4add9db84859bff7410cf934a3904b0414e36e51/src/Storages/MergeTree/MergeTreeSettings.h#L71) ||
|| maxCleanupDelayPeriod | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

Maximum period to clean old queue logs, blocks hashes and parts.
Default: 300
Min_version: 23.6
See in-depth description in [ClickHouse GitHub](https://github.com/ClickHouse/ClickHouse/blob/4add9db84859bff7410cf934a3904b0414e36e51/src/Storages/MergeTree/MergeTreeSettings.h#L142) ||
|#

## Compression {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.Compression}

#|
||Field | Description ||
|| method | enum **Method**

Compression method to use for the specified combination of `minPartSize` and `minPartSizeRatio`.

- `METHOD_UNSPECIFIED`
- `LZ4`: [LZ4 compression algorithm](https://lz4.github.io/lz4/).
- `ZSTD`: [Zstandard compression algorithm](https://facebook.github.io/zstd/). ||
|| minPartSize | **int64**

Minimum size of a part of a table. ||
|| minPartSizeRatio | **double**

Minimum ratio of a part relative to the size of all the data in the table. ||
|| level | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)** ||
|#

## ExternalDictionary {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary}

#|
||Field | Description ||
|| name | **string**

Required field. Name of the external dictionary. ||
|| structure | **[Structure](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.Structure)**

Required field. Set of attributes for the external dictionary.
For in-depth description, see [ClickHouse documentation](https://clickhouse.com/docs/en/query_language/dicts/external_dicts_dict_structure/). ||
|| layout | **[Layout](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.Layout)**

Required field. Layout for storing the dictionary in memory.
For in-depth description, see [ClickHouse documentation](https://clickhouse.com/docs/en/query_language/dicts/external_dicts_dict_layout/). ||
|| fixedLifetime | **int64**

Fixed interval between dictionary updates.

Includes only one of the fields `fixedLifetime`, `lifetimeRange`.

Setting for the period of time between dictionary updates.
For details, see [ClickHouse documentation](https://clickhouse.com/docs/en/query_language/dicts/external_dicts_dict_lifetime/). ||
|| lifetimeRange | **[Range](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.Range)**

Range of intervals between dictionary updates for ClickHouse to choose from.

Includes only one of the fields `fixedLifetime`, `lifetimeRange`.

Setting for the period of time between dictionary updates.
For details, see [ClickHouse documentation](https://clickhouse.com/docs/en/query_language/dicts/external_dicts_dict_lifetime/). ||
|| httpSource | **[HttpSource](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.HttpSource)**

HTTP source for the dictionary.

Includes only one of the fields `httpSource`, `mysqlSource`, `clickhouseSource`, `mongodbSource`, `postgresqlSource`.

Description of the source for the external dictionary. ||
|| mysqlSource | **[MysqlSource](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.MysqlSource)**

MySQL source for the dictionary.

Includes only one of the fields `httpSource`, `mysqlSource`, `clickhouseSource`, `mongodbSource`, `postgresqlSource`.

Description of the source for the external dictionary. ||
|| clickhouseSource | **[ClickhouseSource](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.ClickhouseSource)**

ClickHouse source for the dictionary.

Includes only one of the fields `httpSource`, `mysqlSource`, `clickhouseSource`, `mongodbSource`, `postgresqlSource`.

Description of the source for the external dictionary. ||
|| mongodbSource | **[MongodbSource](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.MongodbSource)**

MongoDB source for the dictionary.

Includes only one of the fields `httpSource`, `mysqlSource`, `clickhouseSource`, `mongodbSource`, `postgresqlSource`.

Description of the source for the external dictionary. ||
|| postgresqlSource | **[PostgresqlSource](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.PostgresqlSource)**

PostgreSQL source for the dictionary.

Includes only one of the fields `httpSource`, `mysqlSource`, `clickhouseSource`, `mongodbSource`, `postgresqlSource`.

Description of the source for the external dictionary. ||
|#

## Structure {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.Structure}

#|
||Field | Description ||
|| id | **[Id](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.Structure.Id)**

Single numeric key column for the dictionary. ||
|| key | **[Key](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.Structure.Key)**

Composite key for the dictionary, containing of one or more key columns.
For details, see [ClickHouse documentation](https://clickhouse.com/docs/en/query_language/dicts/external_dicts_dict_structure/#composite-key). ||
|| rangeMin | **[Attribute](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.Structure.Attribute)**

Field holding the beginning of the range for dictionaries with `RANGE_HASHED` layout.
For details, see [ClickHouse documentation](https://clickhouse.com/docs/en/query_language/dicts/external_dicts_dict_layout/#range-hashed). ||
|| rangeMax | **[Attribute](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.Structure.Attribute)**

Field holding the end of the range for dictionaries with `RANGE_HASHED` layout.
For details, see [ClickHouse documentation](https://clickhouse.com/docs/en/query_language/dicts/external_dicts_dict_layout/#range-hashed). ||
|| attributes[] | **[Attribute](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.Structure.Attribute)**

Description of the fields available for database queries.
For details, see [ClickHouse documentation](https://clickhouse.com/docs/en/query_language/dicts/external_dicts_dict_structure/#attributes). ||
|#

## Id {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.Structure.Id}

Numeric key.

#|
||Field | Description ||
|| name | **string**

Required field. Name of the numeric key. ||
|#

## Key {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.Structure.Key}

Complex key.

#|
||Field | Description ||
|| attributes[] | **[Attribute](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.Structure.Attribute)**

Attributes of a complex key. ||
|#

## Attribute {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.Structure.Attribute}

#|
||Field | Description ||
|| name | **string**

Required field. Name of the column. ||
|| type | **string**

Required field. Type of the column. ||
|| nullValue | **string**

Default value for an element without data (for example, an empty string). ||
|| expression | **string**

Expression, describing the attribute, if applicable. ||
|| hierarchical | **bool**

Indication of hierarchy support.
Default value: `false`. ||
|| injective | **bool**

Indication of injective mapping "id -> attribute".
Default value: `false`. ||
|#

## Layout {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.Layout}

Layout determining how to store the dictionary in memory.

#|
||Field | Description ||
|| type | enum **Type**

Required field. Layout type for an external dictionary.

- `TYPE_UNSPECIFIED`
- `FLAT`: The entire dictionary is stored in memory in the form of flat arrays.
Available for all dictionary sources.
- `HASHED`: The entire dictionary is stored in memory in the form of a hash table.
Available for all dictionary sources.
- `COMPLEX_KEY_HASHED`: Similar to HASHED, to be used with composite keys.
Available for all dictionary sources.
- `RANGE_HASHED`: The entire dictionary is stored in memory in the form of a hash table,
with an ordered array of ranges and their corresponding values.
Available for all dictionary sources.
- `CACHE`: The dictionary is stored in a cache with a set number of cells.
Available for MySQL, ClickHouse and HTTP dictionary sources.
- `COMPLEX_KEY_CACHE`: Similar to CACHE, to be used with composite keys.
Available for MySQL, ClickHouse and HTTP dictionary sources. ||
|| sizeInCells | **int64**

Number of cells in the cache. Rounded up to a power of two.
Applicable only for CACHE and COMPLEX_KEY_CACHE layout types. ||
|| maxArraySize | **int64**

Maximum dictionary key size.
Applicable only for FLAT layout type. ||
|#

## Range {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.Range}

#|
||Field | Description ||
|| min | **int64**

Minimum dictionary lifetime. ||
|| max | **int64**

Maximum dictionary lifetime. ||
|#

## HttpSource {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.HttpSource}

#|
||Field | Description ||
|| url | **string**

Required field. URL of the source dictionary available over HTTP. ||
|| format | **string**

Required field. The data format. Valid values are all formats supported by ClickHouse SQL dialect. ||
|| headers[] | **[Header](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.HttpSource.Header)**

HTTP headers. ||
|#

## Header {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.HttpSource.Header}

#|
||Field | Description ||
|| name | **string**

Required field.  ||
|| value | **string**

Required field.  ||
|#

## MysqlSource {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.MysqlSource}

#|
||Field | Description ||
|| db | **string**

Required field. Name of the MySQL database to connect to. ||
|| table | **string**

Required field. Name of the database table to use as a ClickHouse dictionary. ||
|| port | **int64**

Default port to use when connecting to a replica of the dictionary source. ||
|| user | **string**

Name of the default user for replicas of the dictionary source. ||
|| password | **string**

Password of the default user for replicas of the dictionary source. ||
|| replicas[] | **[Replica](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.MysqlSource.Replica)**

List of MySQL replicas of the database used as dictionary source. ||
|| where | **string**

Selection criteria for the data in the specified MySQL table. ||
|| invalidateQuery | **string**

Query for checking the dictionary status, to pull only updated data.
For more details, see [ClickHouse documentation on dictionaries](https://clickhouse.com/docs/en/query_language/dicts/external_dicts_dict_lifetime/). ||
|| closeConnection | **[google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value)**

Should the connection be closed after each request. ||
|| shareConnection | **[google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value)**

Should a connection be shared for some requests. ||
|#

## Replica {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.MysqlSource.Replica}

#|
||Field | Description ||
|| host | **string**

Required field. MySQL host of the replica. ||
|| priority | **int64**

Required field. The priority of the replica that ClickHouse takes into account when connecting.
Replica with the highest priority should have this field set to the lowest number. ||
|| port | **int64**

Port to use when connecting to the replica.
If a port is not specified for a replica, ClickHouse uses the port specified for the source. ||
|| user | **string**

Name of the MySQL database user. ||
|| password | **string**

Password of the MySQL database user. ||
|#

## ClickhouseSource {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.ClickhouseSource}

#|
||Field | Description ||
|| db | **string**

Required field. Name of the ClickHouse database. ||
|| table | **string**

Required field. Name of the table in the specified database to be used as the dictionary source. ||
|| host | **string**

ClickHouse host of the specified database. ||
|| port | **int64**

Port to use when connecting to the host. ||
|| user | **string**

Required field. Name of the ClickHouse database user. ||
|| password | **string**

Password of the ClickHouse database user. ||
|| where | **string**

Selection criteria for the data in the specified ClickHouse table. ||
|| secure | **[google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value)**

Use ssl for connection. ||
|#

## MongodbSource {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.MongodbSource}

#|
||Field | Description ||
|| db | **string**

Required field. Name of the MongoDB database. ||
|| collection | **string**

Required field. Name of the collection in the specified database to be used as the dictionary source. ||
|| host | **string**

MongoDB host of the specified database. ||
|| port | **int64**

Port to use when connecting to the host. ||
|| user | **string**

Required field. Name of the MongoDB database user. ||
|| password | **string**

Password of the MongoDB database user. ||
|| options | **string** ||
|#

## PostgresqlSource {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.ExternalDictionary.PostgresqlSource}

#|
||Field | Description ||
|| db | **string**

Required field. Name of the PostrgreSQL database. ||
|| table | **string**

Required field. Name of the table in the specified database to be used as the dictionary source. ||
|| hosts[] | **string**

Name of the PostrgreSQL host ||
|| port | **int64**

Port to use when connecting to the host. ||
|| user | **string**

Required field. Name of the PostrgreSQL database user. ||
|| password | **string**

Password of the PostrgreSQL database user. ||
|| invalidateQuery | **string**

Query for checking the dictionary status, to pull only updated data.
For more details, see [ClickHouse documentation on dictionaries](https://clickhouse.com/docs/en/query_language/dicts/external_dicts_dict_lifetime/). ||
|| sslMode | enum **SslMode**

Mode of SSL TCP/IP connection to the PostgreSQL host.
For more details, see [PostgreSQL documentation](https://www.postgresql.org/docs/current/libpq-ssl.html).

- `SSL_MODE_UNSPECIFIED`
- `DISABLE`: Only try a non-SSL connection.
- `ALLOW`: First try a non-SSL connection; if that fails, try an SSL connection.
- `PREFER`: First try an SSL connection; if that fails, try a non-SSL connection.
- `VERIFY_CA`: Only try an SSL connection, and verify that the server certificate is issued by a trusted certificate authority (CA).
- `VERIFY_FULL`: Only try an SSL connection, verify that the server certificate is issued by a trusted CA and that the requested server host name matches that in the certificate. ||
|#

## GraphiteRollup {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.GraphiteRollup}

Rollup settings for the GraphiteMergeTree table engine.

#|
||Field | Description ||
|| name | **string**

Required field. Name for the specified combination of settings for Graphite rollup. ||
|| patterns[] | **[Pattern](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.GraphiteRollup.Pattern)**

Pattern to use for the rollup. ||
|| pathColumnName | **string**

The name of the column storing the metric name (Graphite sensor).
Default: Path
See in-depth description in [ClickHouse documentation](https://clickhouse.com/docs/ru/engines/table-engines/mergetree-family/graphitemergetree#required-columns) ||
|| timeColumnName | **string**

The name of the column storing the time of measuring the metric.
Default: Time
See in-depth description in [ClickHouse documentation](https://clickhouse.com/docs/ru/engines/table-engines/mergetree-family/graphitemergetree#required-columns) ||
|| valueColumnName | **string**

The name of the column storing the value of the metric at the time set in time_column_name.
Default: Value
See in-depth description in [ClickHouse documentation](https://clickhouse.com/docs/ru/engines/table-engines/mergetree-family/graphitemergetree#required-columns) ||
|| versionColumnName | **string**

The name of the column storing the version of the metric.
Default: Timestamp
See in-depth description in [ClickHouse documentation](https://clickhouse.com/docs/ru/engines/table-engines/mergetree-family/graphitemergetree#required-columns) ||
|#

## Pattern {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.GraphiteRollup.Pattern}

#|
||Field | Description ||
|| regexp | **string**

Pattern for metric names. ||
|| function | **string**

Required field. Name of the aggregating function to apply to data of the age specified in `retention`. ||
|| retention[] | **[Retention](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.GraphiteRollup.Pattern.Retention)**

Age of data to use for thinning. ||
|#

## Retention {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.GraphiteRollup.Pattern.Retention}

#|
||Field | Description ||
|| age | **int64**

Minimum age of the data in seconds. ||
|| precision | **int64**

Precision of determining the age of the data, in seconds. ||
|#

## Kafka {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.Kafka}

#|
||Field | Description ||
|| securityProtocol | enum **SecurityProtocol**

- `SECURITY_PROTOCOL_UNSPECIFIED`
- `SECURITY_PROTOCOL_PLAINTEXT`
- `SECURITY_PROTOCOL_SSL`
- `SECURITY_PROTOCOL_SASL_PLAINTEXT`
- `SECURITY_PROTOCOL_SASL_SSL` ||
|| saslMechanism | enum **SaslMechanism**

- `SASL_MECHANISM_UNSPECIFIED`
- `SASL_MECHANISM_GSSAPI`
- `SASL_MECHANISM_PLAIN`
- `SASL_MECHANISM_SCRAM_SHA_256`
- `SASL_MECHANISM_SCRAM_SHA_512` ||
|| saslUsername | **string** ||
|| saslPassword | **string** ||
|| enableSslCertificateVerification | **[google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value)** ||
|| maxPollIntervalMs | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)** ||
|| sessionTimeoutMs | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)** ||
|| debug | enum **Debug**

- `DEBUG_UNSPECIFIED`
- `DEBUG_GENERIC`
- `DEBUG_BROKER`
- `DEBUG_TOPIC`
- `DEBUG_METADATA`
- `DEBUG_FEATURE`
- `DEBUG_QUEUE`
- `DEBUG_MSG`
- `DEBUG_PROTOCOL`
- `DEBUG_CGRP`
- `DEBUG_SECURITY`
- `DEBUG_FETCH`
- `DEBUG_INTERCEPTOR`
- `DEBUG_PLUGIN`
- `DEBUG_CONSUMER`
- `DEBUG_ADMIN`
- `DEBUG_EOS`
- `DEBUG_MOCK`
- `DEBUG_ASSIGNOR`
- `DEBUG_CONF`
- `DEBUG_TELEMETRY`
- `DEBUG_ALL` ||
|| autoOffsetReset | enum **AutoOffsetReset**

- `AUTO_OFFSET_RESET_UNSPECIFIED`
- `AUTO_OFFSET_RESET_SMALLEST`
- `AUTO_OFFSET_RESET_EARLIEST`
- `AUTO_OFFSET_RESET_BEGINNING`
- `AUTO_OFFSET_RESET_LARGEST`
- `AUTO_OFFSET_RESET_LATEST`
- `AUTO_OFFSET_RESET_END`
- `AUTO_OFFSET_RESET_ERROR` ||
|#

## KafkaTopic {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.KafkaTopic}

#|
||Field | Description ||
|| name | **string**

Required field.  ||
|| settings | **[Kafka](#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.Kafka)**

Required field.  ||
|#

## Rabbitmq {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.Rabbitmq}

#|
||Field | Description ||
|| username | **string**

[RabbitMQ](https://clickhouse.com/docs/en/engines/table-engines/integrations/rabbitmq/) username ||
|| password | **string**

[RabbitMQ](https://clickhouse.com/docs/en/engines/table-engines/integrations/rabbitmq/) password ||
|| vhost | **string**

[RabbitMQ](https://clickhouse.com/docs/en/engines/table-engines/integrations/rabbitmq/) virtual host ||
|#

## QueryMaskingRule {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.QueryMaskingRule}

#|
||Field | Description ||
|| name | **string**

Name for the rule. ||
|| regexp | **string**

Required field. RE2 compatible regular expression.
Required. ||
|| replace | **string**

Substitution string for sensitive data.
Default: six asterisks ||
|#

## QueryCache {#yandex.cloud.mdb.clickhouse.v1.config.ClickhouseConfig.QueryCache}

#|
||Field | Description ||
|| maxSizeInBytes | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum cache size in bytes.
Default: 1073741824 (1 GiB) ||
|| maxEntries | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum number of SELECT query results stored in the cache.
Default: 1024 ||
|| maxEntrySizeInBytes | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum size in bytes SELECT query results may have to be saved in the cache.
Dafault: 1048576 (1 MiB) ||
|| maxEntrySizeInRows | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum number of rows SELECT query results may have to be saved in the cache.
Default: 30000000 (30 mil) ||
|#

## Resources {#yandex.cloud.mdb.clickhouse.v1.Resources}

#|
||Field | Description ||
|| resourcePresetId | **string**

ID of the preset for computational resources available to a host (CPU, memory etc.).
All available presets are listed in the [documentation](/docs/managed-clickhouse/concepts/instance-types) ||
|| diskSize | **int64**

Volume of the storage available to a host, in bytes. ||
|| diskTypeId | **string**

Type of the storage environment for the host.
Possible values:
* network-hdd - network HDD drive,
* network-ssd - network SSD drive,
* local-ssd - local SSD storage. ||
|#

## Zookeeper {#yandex.cloud.mdb.clickhouse.v1.ClusterConfig.Zookeeper}

#|
||Field | Description ||
|| resources | **[Resources](#yandex.cloud.mdb.clickhouse.v1.Resources)**

Resources allocated to ZooKeeper hosts. ||
|#

## Access {#yandex.cloud.mdb.clickhouse.v1.Access}

#|
||Field | Description ||
|| dataLens | **bool**

Allow to export data from the cluster to DataLens. ||
|| webSql | **bool**

Allow SQL queries to the cluster databases from the management console.

See [SQL queries in the management console](/docs/managed-clickhouse/operations/web-sql-query) for more details. ||
|| metrika | **bool**

Allow to import data from Yandex Metrica and AppMetrica to the cluster.

See [AppMetrica documentation](https://appmetrica.yandex.com/docs/cloud/index.html) for more details. ||
|| serverless | **bool**

Allow access to cluster for Serverless. ||
|| dataTransfer | **bool**

Allow access for DataTransfer ||
|| yandexQuery | **bool**

Allow access for Query ||
|#

## CloudStorage {#yandex.cloud.mdb.clickhouse.v1.CloudStorage}

#|
||Field | Description ||
|| enabled | **bool**

Whether to use Object Storage for storing ClickHouse data. ||
|| moveFactor | **[google.protobuf.DoubleValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/double-value)** ||
|| dataCacheEnabled | **[google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value)** ||
|| dataCacheMaxSize | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)** ||
|| preferNotToMerge | **[google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value)** ||
|#

## MaintenanceWindow {#yandex.cloud.mdb.clickhouse.v1.MaintenanceWindow}

A maintenance window settings.

#|
||Field | Description ||
|| anytime | **[AnytimeMaintenanceWindow](#yandex.cloud.mdb.clickhouse.v1.AnytimeMaintenanceWindow)**

Maintenance operation can be scheduled anytime.

Includes only one of the fields `anytime`, `weeklyMaintenanceWindow`.

The maintenance policy in effect. ||
|| weeklyMaintenanceWindow | **[WeeklyMaintenanceWindow](#yandex.cloud.mdb.clickhouse.v1.WeeklyMaintenanceWindow)**

Maintenance operation can be scheduled on a weekly basis.

Includes only one of the fields `anytime`, `weeklyMaintenanceWindow`.

The maintenance policy in effect. ||
|#

## AnytimeMaintenanceWindow {#yandex.cloud.mdb.clickhouse.v1.AnytimeMaintenanceWindow}

#|
||Field | Description ||
|| Empty | > ||
|#

## WeeklyMaintenanceWindow {#yandex.cloud.mdb.clickhouse.v1.WeeklyMaintenanceWindow}

Weelky maintenance window settings.

#|
||Field | Description ||
|| day | enum **WeekDay**

Day of the week (in `DDD` format).

- `WEEK_DAY_UNSPECIFIED`
- `MON`
- `TUE`
- `WED`
- `THU`
- `FRI`
- `SAT`
- `SUN` ||
|| hour | **int64**

Hour of the day in UTC (in `HH` format). ||
|#

## MaintenanceOperation {#yandex.cloud.mdb.clickhouse.v1.MaintenanceOperation}

A planned maintenance operation.

#|
||Field | Description ||
|| info | **string**

Information about this maintenance operation. ||
|| delayedUntil | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Time until which this maintenance operation is delayed. ||
|#