# Viewing cluster logs

{{ mmy-name }} lets you [get a cluster log snippet](#get-log) for the selected period and [view logs in real time](#get-log-stream).

## Getting a cluster log {#get-log}

{% list tabs %}

- Management console

   1. Go to the folder page and select **{{ mmy-name }}**.
   1. Click the name of the desired cluster and select the ![image](../../_assets/logs.svg) **Logs** tab.
   1. Specify the time period for which you want to display logs: enter it manually or select it in the calendar by clicking on the date field.
   1. Select the type of events to display. By default, the `MYSQL_ERROR` type is used.
   1. If necessary, select the hosts and logging level in the drop-down lists next to the date input field.

   A list of log entries for the selected time period will be displayed. To view detailed information about an event, click on the respective entry in the list.

   If there are too many records and only some of them are displayed, click the **Load more** link at the end of the list.

- CLI

   {% include [cli-install](../../_includes/cli-install.md) %}

   {% include [default-catalogue](../../_includes/default-catalogue.md) %}

   1. View a description of the CLI command to view cluster logs:

      ```bash
      {{ yc-mdb-my }} cluster list-logs --help
      ```

   1. Run the command to get cluster logs (the example does not contain a complete list of available parameters):

      ```bash
      {{ yc-mdb-my }} cluster list-logs <cluster name or ID> \
         --limit <record number limit> \
         --columns <list of columns to display information> \
         --filter <record filter settings> \
         --since <left boundary of time range> \
         --until <right boundary of time range>
      ```

      Where:

      * {% include [logs output limit](../../_includes/cli/logs/limit.md) %}
      * `--service-type`: Type of service to output records for (`mysql-error`, `mysql-general`, `mysql-slow-query`, or `mysql-audit`).
      * `--columns`: List of columns to display information:
         * `hostname`: [Name of the host](hosts.md#list-hosts).
         * `id`: Query ID.
         * `message`: Message output by the service.
         * `status`: Message status, such as `Note` or `Warning`.

         {% note info %}

         The example only contains the main columns. A list of columns to output depends on the `--service-type` selected.

         {% endnote %}

      * {% include [logs filter](../../_includes/cli/logs/filter.md) %}
      * {% include [logs since time](../../_includes/cli/logs/since.md) %}
      * {% include [logs until time](../../_includes/cli/logs/until.md) %}

   You can request a cluster name and ID with a [list of clusters in the folder](cluster-list.md#list-clusters).

- API

   Use the [listLogs](../api-ref/Cluster/listLogs.md) API method and pass the cluster ID in the `clusterId` request parameter.

   To find out the cluster ID, [get a list of clusters in the folder](cluster-list.md#list-clusters).

{% endlist %}

## Getting a cluster log stream {#get-log-stream}

This method lets you get cluster logs in real time.

{% list tabs %}

- CLI

   {% include [cli-install](../../_includes/cli-install.md) %}

   {% include [default-catalogue](../../_includes/default-catalogue.md) %}

   To view cluster logs as they become available, run the command:

   ```bash
   {{ yc-mdb-my }} cluster list-logs <cluster name or ID> --follow
   ```

   You can request a cluster name and ID with a [list of clusters in the folder](cluster-list.md#list-clusters).

- API

   Use the [streamLogs](../api-ref/Cluster/streamLogs.md) API method and pass the cluster ID in the `clusterId` request parameter.

   To find out the cluster ID, [get a list of clusters in the folder](cluster-list.md#list-clusters).

{% endlist %}