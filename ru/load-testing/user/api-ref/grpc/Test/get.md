---
editable: false
sourcePath: en/_api-ref-grpc/loadtesting/api/v1/user/api-ref/grpc/Test/get.md
---

# Load Testing API, gRPC: TestService.Get {#Get}

Returns the specified test.

To get the list of all available tests, make a [List](/docs/load-testing/user/api-ref/grpc/Test/list#List) request.

## gRPC request

**rpc Get ([GetTestRequest](#yandex.cloud.loadtesting.api.v1.GetTestRequest)) returns ([test.Test](#yandex.cloud.loadtesting.api.v1.test.Test))**

## GetTestRequest {#yandex.cloud.loadtesting.api.v1.GetTestRequest}

```json
{
  "testId": "string"
}
```

#|
||Field | Description ||
|| testId | **string**

Required field. ID of the test to return. ||
|#

## test.Test {#yandex.cloud.loadtesting.api.v1.test.Test}

```json
{
  "id": "string",
  "configurations": [
    {
      "configId": "string",
      "agentSelector": {
        // Includes only one of the fields `agentId`, `matchByFilter`, `anonymousAgent`
        "agentId": "string",
        "matchByFilter": "string",
        "anonymousAgent": "bool"
        // end of the list of possible fields
      },
      "files": {
        // Includes only one of the fields `objectStorage`
        "objectStorage": {
          "bucket": "string",
          "name": "string"
        }
        // end of the list of possible fields
      }
    }
  ],
  "details": {
    "name": "string",
    "description": "string",
    "tags": [
      {
        "key": "string",
        "value": "string"
      }
    ],
    "loggingLogGroupId": "string",
    "artifactSettings": {
      // Includes only one of the fields `objectStorageBucket`
      "objectStorageBucket": "string",
      // end of the list of possible fields
      "isArchive": "bool",
      "filterInclude": [
        "string"
      ],
      "filterExclude": [
        "string"
      ]
    }
  },
  "summary": {
    "status": "Status",
    "createdAt": "google.protobuf.Timestamp",
    "createdBy": "string",
    "startedAt": "google.protobuf.Timestamp",
    "finishedAt": "google.protobuf.Timestamp",
    "isFinished": "bool",
    "error": "string",
    "imbalancePoint": {
      "at": "google.protobuf.Timestamp",
      "rps": "int64",
      "comment": "string"
    },
    "assignedAgentId": "string",
    "artifacts": {
      // Includes only one of the fields `objectStorage`
      "objectStorage": {
        "bucket": "string",
        "name": "string"
      }
      // end of the list of possible fields
    }
  },
  "folderId": "string"
}
```

Load Test.

In context of the service, Test represents a single testing task/job.

#|
||Field | Description ||
|| id | **string**

ID of the test. Generated at creation time. ||
|| configurations[] | **[SingleAgentConfiguration](#yandex.cloud.loadtesting.api.v1.test.SingleAgentConfiguration)**

Configuration of the test.

A test can have multiple configurations if it can be
executed on multiple agents simultaneously. For more information, see
[Load testing using multiple agents](docs/load-testing/tutorials/loadtesting-multiply). ||
|| details | **[Details](#yandex.cloud.loadtesting.api.v1.test.Details)**

Test meta information. Name, description, etc. ||
|| summary | **[Summary](#yandex.cloud.loadtesting.api.v1.test.Summary)**

Test execution information. ||
|| folderId | **string**

ID of the folder that the test belongs to. ||
|#

## SingleAgentConfiguration {#yandex.cloud.loadtesting.api.v1.test.SingleAgentConfiguration}

Configuration of a test.

#|
||Field | Description ||
|| configId | **string**

ID of the config. ||
|| agentSelector | **[AgentSelector](#yandex.cloud.loadtesting.api.v1.test.AgentSelector)**

Agent selection criterion. ||
|| files | **[FilePointer](#yandex.cloud.loadtesting.api.v1.test.FilePointer)**

Additional files to be used during test execution, represented as `rel_path:file` pairs.

`rel_path` can be either a simple file name, a relative path, or absolute path. Files are
downloaded by the agent to appropriate location.

Use cases include:
- [Test Data files](/docs/load-testing/concepts/payload).
- Custom Pandora executable.
- JMeter executable or ".jmx" scenario.
- etc. ||
|#

## AgentSelector {#yandex.cloud.loadtesting.api.v1.test.AgentSelector}

Agent selection criterion.

The structure is used by service to determine on which agents a specific test should be executed.

#|
||Field | Description ||
|| agentId | **string**

Selection by agent ID.

Includes only one of the fields `agentId`, `matchByFilter`, `anonymousAgent`. ||
|| matchByFilter | **string**

Selection by filter string.

Includes only one of the fields `agentId`, `matchByFilter`, `anonymousAgent`. ||
|| anonymousAgent | **bool**

Select anonymoud (i.e. not registered) agents.

Includes only one of the fields `agentId`, `matchByFilter`, `anonymousAgent`. ||
|#

## FilePointer {#yandex.cloud.loadtesting.api.v1.test.FilePointer}

Variant-like structure for referencing files in different sources.

#|
||Field | Description ||
|| objectStorage | **[ObjectStorage](#yandex.cloud.loadtesting.api.v1.test.ObjectStorage)**

Reference to a file in Object Storage.

Includes only one of the fields `objectStorage`. ||
|#

## ObjectStorage {#yandex.cloud.loadtesting.api.v1.test.ObjectStorage}

Reference to a file stored in Object Storage.

#|
||Field | Description ||
|| bucket | **string**

Bucket name. ||
|| name | **string**

File name. ||
|#

## Details {#yandex.cloud.loadtesting.api.v1.test.Details}

Test meta information.

#|
||Field | Description ||
|| name | **string**

Name of the test. ||
|| description | **string**

Description of the test. ||
|| tags[] | **[Tag](#yandex.cloud.loadtesting.api.v1.common.Tag)**

Tags assigned to the test. ||
|| loggingLogGroupId | **string**

ID of the logging group to which test artifacts are uploaded. ||
|| artifactSettings | **[ArtifactSettings](#yandex.cloud.loadtesting.api.v1.test.ArtifactSettings)**

Settings which define where to upload test artifacts and which files should be included. ||
|#

## Tag {#yandex.cloud.loadtesting.api.v1.common.Tag}

Tag attached to some entity.

#|
||Field | Description ||
|| key | **string**

Key of the tag. ||
|| value | **string**

Value of the tag. ||
|#

## ArtifactSettings {#yandex.cloud.loadtesting.api.v1.test.ArtifactSettings}

Artifact upload settings.

Defines where to upload test artifacts and which files should be included.

#|
||Field | Description ||
|| objectStorageBucket | **string**

Name of output object storage bucket in test's folder.

Includes only one of the fields `objectStorageBucket`. ||
|| isArchive | **bool**

Setting which defines whether artifact files should be archived prior to uploading. ||
|| filterInclude[] | **string**

Filter strings defining which files should be included to artifacts. GLOB format.

Example:
- ['*'] - all files will be uploaded.
- ['*.log', '*.yaml] - all `.log` and `.yaml` files will be uploaded. ||
|| filterExclude[] | **string**

Filter strings defining which files should be excluded from artifacts. GLOB format.

Example:
- filter_include=['*'], filter_exclude=['phout.log'] - upload all `.log` files excluding `phout.log`. ||
|#

## Summary {#yandex.cloud.loadtesting.api.v1.test.Summary}

Process of test and some results

#|
||Field | Description ||
|| status | enum **Status**

Status of the test.

- `STATUS_UNSPECIFIED`: Status is unspecified.
- `CREATED`: Test has been created, but not started by any agent.
- `INITIATED`: Execution stage: initialization.
- `PREPARING`: Execution stage: data preparation and warm-up.
- `RUNNING`: Execution stage: load generation.
- `FINISHING`: Execution stage: termination.
- `DONE`: Test is done.
- `POST_PROCESSING`: Execution stage: results post-processing.
- `FAILED`: Test has failed due to some error.
- `STOPPING`: Test is being stopped.
- `STOPPED`: Test has been stopped.
- `AUTOSTOPPED`: Test has been stopped automatically by satisfying autostop condition.
- `WAITING`: Execution stage: waiting for a trigger to start.
- `DELETING`: Test is being deleted.
- `LOST`: Test status has not been reported in a while during execution stage.

  Means that either an agent is too busy to send it, got offline, or failed without
reporting a final status. ||
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Creation timestamp. ||
|| createdBy | **string**

UA or SA that created the test. ||
|| startedAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Test start timestamp.

Empty if the test has not been started yet. ||
|| finishedAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Test finish timestamp.

Empty if the test has not been finished yet. ||
|| isFinished | **bool**

Indicates whether the test is finished. ||
|| error | **string**

Error message. ||
|| imbalancePoint | **[ImbalancePoint](#yandex.cloud.loadtesting.api.v1.test.ImbalancePoint)**

Detected imbalance point.

Contains information about a state at the moment it has been
[auto-stopped](/docs/load-testing/concepts/auto-stop).

Empty if no auto-stop occured. ||
|| assignedAgentId | **string**

ID of the agent that executed the test. ||
|| artifacts | **[FilePointer](#yandex.cloud.loadtesting.api.v1.test.FilePointer)**

Test output artifacts.

Link to the artifacts output target containing `.log` and other files collected
during test execution. ||
|#

## ImbalancePoint {#yandex.cloud.loadtesting.api.v1.test.ImbalancePoint}

Test imbalance point.

#|
||Field | Description ||
|| at | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Imbalance moment timestamp. ||
|| rps | **int64**

Imbalance moment RPS. ||
|| comment | **string**

Imbalance reason comment. ||
|#