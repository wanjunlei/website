---
title: "Monitoring"
keywords: 'Kubernetes, KubeSphere, API, Monitoring'
description: 'Monitoring'


weight: 260
---

## API Version

The monitoring API version is bumped to `v1alpha3`.

## Time format

The time format for query parameters must be in Unix timestamp, which is the number of seconds that have elapsed since the Unix epoch. Decimal is no longer allowed. The change affects the parameters `start`, `end` and `time`.

## Deprecated Metrics

In KubeSphere 3.0.0, the metrics on the left have been renamed into the ones on the right.

|V2.0|V3.0|
|---|---|
|workload_pod_cpu_usage | workload_cpu_usage|  
|workload_pod_memory_usage| workload_memory_usage|
|workload_pod_memory_usage_wo_cache | workload_memory_usage_wo_cache|
|workload_pod_net_bytes_transmitted | workload_net_bytes_transmitted|
|workload_pod_net_bytes_received | workload_net_bytes_received|

The following metrics have been deprecated and removed.

|Deprecated Metrics|
|---|
|cluster_workspace_count|
|cluster_account_count|
|cluster_devops_project_count|
|workspace_namespace_count|
|workspace_devops_project_count|
|workspace_member_count|
|workspace_role_count|
|coredns_up_sum|
|coredns_cache_hits|
|coredns_cache_misses|
|coredns_dns_request_rate|
|coredns_dns_request_duration|
|coredns_dns_request_duration_quantile|
|coredns_dns_request_by_type_rate|
|coredns_dns_request_by_rcode_rate|
|coredns_panic_rate|
|coredns_proxy_request_rate|
|coredns_proxy_request_duration|
|coredns_proxy_request_duration_quantile|
|prometheus_up_sum|
|prometheus_tsdb_head_samples_appended_rate|

## Response Fields

In KubeSphere 3.0.0, the response fields `metrics_level`, `status` and `errorType` are removed.

In addition, the field name `resource_name` has been replaced with the specific resource type names. These types are `node`, `workspace`, `namespace`, `workload`, `pod`, `container` and `persistentvolumeclaim`. For example, instead of `resource_name: node1`, you will get `node: node1`. See the example response below:

```json
{
    "results":[
        {
            "metric_name":"node_cpu_utilisation",
            "data":{
                "resultType":"vector",
                "result":[
                    {
                        "metric":{
                            "__name__":"node:node_cpu_utilisation:avg1m",
                            "node":"master"
                        },
                        "value":[
                            1588841175.979,
                            "0.04587499999997817"
                        ]
                    },
                    {
                        "metric":{
                            "__name__":"node:node_cpu_utilisation:avg1m",
                            "node":"node1"
                        },
                        "value":[
                            1588841175.979,
                            "0.06379166666670245"
                        ]
                    },
                    {
                        "metric":{
                            "__name__":"node:node_cpu_utilisation:avg1m",
                            "node":"node2"
                        },
                        "value":[
                            1588841175.979,
                            "0.19008333333367772"
                        ]
                    }
                ]
            }
        }
    ]
}

```



