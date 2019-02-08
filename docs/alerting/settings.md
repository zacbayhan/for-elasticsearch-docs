---
layout: default
title: Management
parent: Alerting
nav_order: 2
---

# Management

## Alerting indices

The alerting feature creates several indices and one alias.

Index | Purpose
:--- | :---
`.opendistro-alerts` | Stores ongoing alerts.
`.opendistro-alert-history-<date>` | Stores a history of completed alerts.
`.opendistro-scheduled-jobs` | Stores scheduled jobs (monitors) and when to run them.
`.opendistro-alert-history-write` (alias) | Provides a consistent URI for the `.opendistro-alert-history-<date>` index.


## Alerting settings

We don't recommend changing these settings; the defaults should work well for most use cases.

All settings are available using the Elasticsearch `_cluster/settings` API. None require a restart, and all can be marked `persistent` or `transient`.

Setting | Default | Description
:--- | :--- | :---
`opendistro.alerting.enabled` | true | Whether the alerting plugin is enabled or not. If disabled, all monitors immediately stop running.
`opendistro.alerting.input_timeout` | 30s | How long the monitor can take to issue the search request.
`opendistro.alerting.bulk_timeout` | 120s | How long the monitor can write alerts to the alert index.
`opendistro.alerting.alert_backoff_count` | 2 | Number of retries for writing alerts before the operation fails.
`opendistro.alerting.alert_backoff_millis` | 50ms | The amount of time to wait between retries---increases exponentially after each failed retry.
`opendistro.alerting.alert_history_rollover_period` | 12h | How often completed alerts are rolled over from the `.opendistro-alerts` index to `.opendistro-alert-history-<date>`.
`opendistro.alerting.alert_history_max_age` | 24h | The oldest document the `.opendistro-alert-history-<date>` index should keep.
`opendistro.alerting.alert_history_max_docs` | 1000 | The maximum number of documents the `.opendistro-alert-history-<date>` index should keep.
`opendistro.scheduled_jobs.sweeper.period` | 5m | The rate at which the sweeper checks to see if any scheduled jobs (monitors) have changed and need to be rescheduled.
`opendistro.scheduled_jobs.sweeper.page_size` | 100 | The page size for the sweeper. You shouldn't need to change this value.
`opendistro.scheduled_jobs.sweeper.backoff_millis` | 50ms | The amount of time the sweeper waits between retries---increases exponentially after each failed retry.