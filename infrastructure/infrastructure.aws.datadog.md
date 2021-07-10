---
id: 244fa2dd-3a6a-4e6e-98b5-f93853d0016a
title: Datadog
desc: ""
updated: 1625873828470
created: 1622173257348
---

## Datadog

## controlling cost by using Autodiscovery

https://github.com/DataDog/helm-charts/blob/master/charts/datadog/README.md

datadog.containerExclude string nil Exclude containers from the Agent Autodiscovery, as a space-sepatered list
datadog.containerExcludeLogs string nil Exclude logs from the Agent Autodiscovery, as a space-separated list
datadog.containerExcludeMetrics string nil Exclude metrics from the Agent Autodiscovery, as a space-separated list

https://docs.datadoghq.com/getting_started/tagging/unified_service_tagging/?tab=kubernetes
https://docs.datadoghq.com/agent/cluster_agent/clusterchecks/

## setting up aws

https://app.datadoghq.com/account/settings#integrations/amazon-web-services
https://app.datadoghq.com/account/settings#api
![](/assets/images/2021-05-27-22-42-37.png)

Installing the AWS Integration could increase the number of servers and Lambda functions that Datadog monitors. For more information on how this may affect your billing, visit the Billing FAQ page.
https://docs.datadoghq.com/account_management/billing/
Datadog uses CloudWatch APIs to monitor your AWS resources every 10 minutes. See the AWS Integration FAQ for more information.
Enabling the AWS X-Ray integration increases the amount of Indexed Spans which can impact your bill.
