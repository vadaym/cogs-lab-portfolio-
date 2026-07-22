\# Post-Incident Report (PIR)



\*\*Incident ID:\*\* INC-2026-0722-001



\*\*Date:\*\* 2026-07-22



\*\*Severity:\*\* P2



\*\*Status:\*\* Resolved



\---



\## Incident Summary



At 09:15 IST a financial institution reported that 25 finance department users were unable to receive SMS OTPs. Email OTP worked normally. Investigation found that the Kaleyra sender ID had been blocked due to a TRAI DND enforcement issue. Traffic was switched to a backup sender ID, restoring service. The customer confirmed successful OTP delivery at 11:45 IST.



\---



\## Timeline



| Time | Event |

|------|-------|

|09:15|Customer reported issue|

|09:18|Ticket created|

|09:20|Initial customer response|

|09:35|Kaleyra dashboard checked|

|10:00|Logs reviewed|

|10:30|Escalated to L2|

|11:30|Root cause identified|

|11:40|Backup sender activated|

|11:45|Customer confirmed resolution|



\---



\## Root Cause



Kaleyra's sender ID was flagged under TRAI DND regulations because another sender sharing the same SMS route generated violations. The carrier rejected SMS OTP traffic until the service was switched to a backup sender ID.



\---



\## Impact Assessment



\- Users affected: 25

\- Duration: 2 hours 30 minutes

\- Business Impact: Finance users could not complete MFA authentication, delaying access to internal systems.



\---



\## Resolution Steps



1\. Verified the issue.

2\. Checked Kaleyra dashboard.

3\. Confirmed rejected SMS status.

4\. Escalated to L2.

5\. Activated backup sender ID.

6\. Verified SMS delivery.

7\. Customer confirmed resolution.



\---



\## Prevention Actions



\- \[ ] Configure automated sender ID monitoring.

&#x20; - Owner: Messaging Team

&#x20; - Due: 2026-07-19



\- \[ ] Validate backup SMS routes weekly.

&#x20; - Owner: Infrastructure Team

&#x20; - Due: 2026-07-20



\---



\## Open Items



\- \[ ] Create a Knowledge Base article for SMS sender ID failures.

&#x20; - Owner: Support Team

&#x20; - Due: 2026-07-22

