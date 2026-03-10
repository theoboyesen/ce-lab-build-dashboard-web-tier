# Lab M6.03 - Build Dashboard for Web Tier Health

## Dashboard Design Rationale

The dashboard is designed using a top-down troubleshooting approach so that engineers can quickly assess system health during an incident.

At the top of the dashboard, single-value widgets provide an immediate snapshot of the current system state, including request rate, error rate, latency, and healthy target count. These metrics allow on-call engineers to determine very quickly whether the system is healthy or degraded.

The next section focuses on the **Golden Signals** (Traffic, Errors, Latency, and Saturation). These metrics represent the most important indicators of service health and are commonly used in site reliability engineering to identify performance issues or service degradation.

Below the Golden Signals, the dashboard includes **EC2 resource utilization metrics** such as CPU, memory, network throughput, and disk usage. These help determine whether application issues are caused by infrastructure constraints or resource exhaustion.

Finally, a **correlation view** overlays key metrics (latency, request rate, error rate, and CPU utilization) on a single graph. This helps engineers identify relationships between load, infrastructure usage, and application performance when diagnosing incidents.

This layout supports a natural investigation workflow: start with high-level health indicators, then drill down into resource metrics and correlations to identify root causes.

---

## Widget Explanations

| Widget                              | Type         | Purpose                                                                                                   |
| ----------------------------------- | ------------ | --------------------------------------------------------------------------------------------------------- |
| Current Request Rate                | Single Value | Shows the current volume of incoming requests to the load balancer                                        |
| Error Rate (%)                      | Single Value | Displays the percentage of requests returning 5XX errors                                                  |
| P95 Latency                         | Single Value | Shows high percentile response latency experienced by users                                               |
| Healthy Targets                     | Single Value | Indicates how many backend instances are healthy                                                          |
| Traffic - Request Rate              | Time Series  | Displays request trends over time                                                                         |
| Errors - HTTP Status Codes          | Time Series  | Visualizes 2XX, 4XX, and 5XX responses to identify error patterns                                         |
| Latency - Response Time Percentiles | Time Series  | Shows P50, P95, and P99 latency to track performance changes                                              |
| Target Health                       | Time Series  | Shows healthy vs unhealthy load balancer targets                                                          |
| CPU Utilization                     | Time Series  | Tracks EC2 CPU usage to detect resource saturation                                                        |
| Memory Utilization                  | Time Series  | Shows system memory usage from the CloudWatch Agent                                                       |
| Network In/Out                      | Time Series  | Displays network throughput entering and leaving the instance                                             |
| Disk Usage                          | Time Series  | Monitors disk utilization on the EC2 instance                                                             |
| Correlation View                    | Time Series  | Combines latency, request rate, error rate, and CPU usage to help identify cause-and-effect relationships |

---

## How to Use This Dashboard

1. Start at the **top row**, where single-value widgets provide a quick snapshot of current system health.
2. Review the **Golden Signals section** to identify trends in traffic, errors, latency, and service saturation.
3. If any Golden Signals indicate abnormal behaviour, check the **EC2 Resource Utilization** section to determine whether the issue is related to infrastructure limits such as CPU or memory.
4. Use the **Correlation View** at the bottom of the dashboard to analyze relationships between load, latency, errors, and CPU utilization to help determine the root cause of performance issues.

---

# Submission
