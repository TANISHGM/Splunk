\# Real-Time Log Monitoring with Splunk 



&nbsp;Project Overview

This project demonstrates how to set up "real-time log monitoring" by forwarding logs from a "Kali Linux machine" to "Splunk Enterprise" using "rsyslog".  

The goal is to centralize logs for security monitoring, system auditing, and incident detection.



---



Lab Environment

\- Sender Machine: Kali Linux (log source)

-Receiver Machine: Splunk Enterprise (log collector \& analyzer)

\- Log Forwarder: Rsyslog



---



Configuration Steps



&nbsp;1. Configure Rsyslog on Kali

1\. Install rsyslog (if not already installed):

&nbsp;  ```bash

&nbsp;  sudo apt update \&\& sudo apt install rsyslog -y





Edit rsyslog configuration:



sudo nano /etc/rsyslog.conf





Add the following line at the end (replace <SPLUNK\_IP> with your Splunk server’s IP):



\*.\* @<SPLUNK\_IP>:514





Restart rsyslog service:



sudo systemctl restart rsyslog

sudo systemctl enable rsyslog



-----------------------------------------------------



2\. Configure Splunk to Receive Logs



Log in to Splunk Web.



Navigate to: Settings → Data Inputs → UDP → New Local UDP.



Set the port to 514.



Assign logs to an index (e.g., main).



Save and restart Splunk if required.



✅ Verification



On Kali, run:



logger "Test log from Kali to Splunk"





Then search in Splunk:



index=main "Test log from Kali"





If configured correctly, you’ll see the log in real time.

**-----------------------------------------------------**

Results



Successfully forwarded system logs from Kali to Splunk.



Logs are now centralized for search, dashboards, and alerting.



Enables SOC-style monitoring for endpoint activity.





Future Enhancements



Add multiple endpoints (Ubuntu, Windows) for centralized log collection.



Create Splunk dashboards for visualization.



Set up alerts for critical log events (e.g., failed logins, privilege escalation).



