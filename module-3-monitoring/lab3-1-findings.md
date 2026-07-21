<h2 align=center>Map Uptime Kuma monitor types to Site24x7 monitor types</h2>

| Uptime Kuma monitor type  | Site24x7 equivalent monitor type                             | Use case                                                   |
| ------------------------- | ------------------------------------------------------------ | ---------------------------------------------------------- |
| HTTP(s) Monitor           | Website Monitor / URL Monitor                                | Check a web URL, login page, API endpoint, health endpoint |
| TCP Port Monitor          | TCP/Port Monitor                                             | Check whether a service port is reachable                  |
| Ping Monitor              | Ping Monitor                                                 | Check host availability via ICMP                           |
| DNS Monitor               | DNS Monitor                                                  | Validate DNS resolution                                    |
| Keyword Monitor           | Website Content Check                                        | Confirm expected text exists on a webpage                  |
| HTTP(s) Keyword Monitor   | Website Monitor + Content Check                              | Validate page content/API response                         |
| Docker Monitor            | Server Monitoring (Docker/Container monitoring)              | Monitor containers and hosts                               |
| MQTT Monitor              | MQTT Monitoring (via custom monitoring/API where applicable) | IoT messaging checks                                       |
| Push Monitor              | Heartbeat Monitor                                            | Receive availability signals from applications             |
| Steam/Game Server Monitor | Custom TCP/UDP monitoring                                    | Game/service availability checks                           |


## For an InstaSafe Gateway

An InstaSafe Gateway is typically a network access/security gateway (for example, a VPN/ZTNA gateway). The right Site24x7 monitor depends on what you want to verify:

- Gateway is reachable
  
    Use: Ping Monitor

    Uptime Kuma equivalent: Ping Monitor

- VPN/ZTNA gateway service port is open
  
    Use: TCP Port Monitor

    Uptime Kuma equivalent: TCP Port Monitor

    Example checks: gateway IP + required service port
