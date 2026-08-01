# CHANGE-001 Rollback Record



## Status

ROLLED BACK SUCCESSFULLY



## Rollback Trigger

Invalid Nginx configuration detected during validation.



## Failure Test



Command:



sudo nginx -t



Result:



unknown directive "ssl_protocolz"



Configuration test failed.



## Rollback Action



Restored previous working configuration:



sudo cp /etc/nginx/sites-available/lab-tls.backup /etc/nginx/sites-available/lab-tls



## Validation



Command:



sudo nginx -t



Result:



Configuration syntax ok.

Test successful.



## Service Verification



Command:



curl -k https://localhost



Result:



HTTPS service restored successfully.



## Final Status



Service operational after rollback.

