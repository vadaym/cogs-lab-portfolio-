<h1 align=center>Difference between Prometheus/Grafana and SigNoz</h1>

|                 | Prometheus + Grafana                        | SigNoz                                                              |
| --------------- | ------------------------------------------- | ------------------------------------------------------------------- |
| Main purpose    | Metrics monitoring and dashboards           | Full observability (metrics + logs + traces)                        |
| Best at         | "Is something wrong?"                       | "Why is it wrong?"                                                  |
| Data type       | Mainly time-series metrics                  | Metrics, logs, distributed traces                                   |
| Typical users   | SREs, infrastructure teams                  | SREs + application developers                                       |
| Strength        | Fast alerting and infrastructure visibility | Root-cause analysis                                                 |
| Query language  | PromQL                                      | ClickHouse-based queries / OpenTelemetry data                       |
| Common examples | CPU, memory, disk, latency, error rate      | Which service failed, which API call broke, where latency increased |

## During a P1 incident:

- Prometheus + Grafana → Use first to answer "What is broken and how bad is the impact?"
  
        Check alerts, CPU, memory, latency, error rates, traffic, service health.
  
- SigNoz → Use next to answer "Why is it broken?"
  
        Trace requests, find the failing service, API, database call, or dependency.

### Simple flow:

Grafana → Detect & measure impact → SigNoz → Find root cause → Fix & verify
