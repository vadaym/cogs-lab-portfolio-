# Change ID: CHANGE-001



## Type

Normal Change



## Description

Update Nginx TLS configuration to prefer TLS 1.3.



## Justification

TLS 1.3 is faster and more secure. This change aligns with current security best practices.



## Execution Steps



1. Backup current Nginx TLS configuration.

2. Update ssl_protocols line in Nginx site configuration.

3. Test configuration using nginx -t.

4. Reload Nginx service.

5. Verify TLS 1.3 is working.

6. Verify TLS 1.2 is disabled.



## Rollback Trigger



Rollback will be triggered if:

- TLS verification fails.

- HTTPS service becomes unreachable.

- Nginx configuration test fails.



## Rollback Steps



1. Restore the Nginx configuration backup.

2. Test Nginx configuration.

3. Reload Nginx.

4. Verify HTTPS service.



## Rollback Command



```bash

sudo cp /etc/nginx/sites-available/lab-tls.backup /etc/nginx/sites-available/lab-tls

sudo nginx -t && sudo systemctl reload nginx

