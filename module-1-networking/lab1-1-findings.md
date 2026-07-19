# lab1-1-findings.md template
# Lab 1.1 Findings
## My VM Details
- Provider: AWS
- Region: eu-north-1c
- OS: Ubuntu 26.04

## Experiment Results
### Ping to 8.8.8.8
- Average RTT: 3.313 ms
- TTL value observed: 118
- What does TTL tell us about the path? - TTL (Time To Live) indicates the remaining hop count when the packet reaches the destination. A value of 118 suggests the packet has traversed several routers (approximately 10 hops if the initial TTL was 128), helping prevent routing loops.

### Traceroute to google.com
- Number of hops: 6
- Any * * * hops? At which hop number? - Yes. There is a * * * at hop 2 (which is common due to firewall or ICMP filtering)

### DNS Comparison
- Result from default DNS: 216.58.201.206
- Result from 1.1.1.1: 216.58.207.110
- Are they different? Why might they differ? - Yes. The IP addresses are different because Google uses DNS load balancing. Different DNS resolvers may return different IP addresses for the same domain.

### google.com TLS Certificate
- Issuer: Google Trust Services (CN=WR2)
- CN: *.google.com
- Expiry date: Sep 21 08:40:12 2026 GMT
- TLS version used: TLS 1.3

### nmap localhost
- open ports: 22 (for ssh)
