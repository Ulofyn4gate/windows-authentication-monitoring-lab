# windows-authentication-monitoring-lab
Windows Authentication Monitoring Lab

This project demonstrates a centralized Windows authentication monitoring pipeline using Elastic Stack and Winlogbeat.

The lab was designed to simulate a basic SOC-style workflow:

* Collect Windows Security Event logs
* Forward telemetry to a SIEM
* Analyze authentication activity
* Investigate failed and successful login events

The environment was built using Docker on macOS with a Windows VM endpoint.

⸻

Architecture

Windows VM
↓
Winlogbeat
↓
Elasticsearch
↓
Kibana

⸻

Technologies Used

* Docker
* Elasticsearch 8.12
* Kibana 8.12
* Winlogbeat
* Windows Event Logs
* UTM Virtualization
* macOS (Apple Silicon)

⸻

Project Objectives

* Deploy a functional SIEM environment
* Ingest Windows authentication logs into Elasticsearch
* Visualize security events in Kibana
* Investigate login activity using Event IDs 4624 and 4625
* Understand endpoint-to-SIEM telemetry flow

⸻

Log Sources

Windows Security Events

Event ID 4624

Successful logon event.

Event ID 4625

Failed logon event.

These events were used to analyze authentication activity and simulate brute-force style login behavior.

⸻

Lab Setup

SIEM Server

Hosted on macOS using Docker containers:

* Elasticsearch
* Kibana

Endpoint

Windows VM running:

* Winlogbeat agent

⸻

Key Challenges Encountered

Elasticsearch Memory Failures

Elasticsearch initially exited with code 137 due to insufficient Docker memory allocation on Apple Silicon.

Resolution

* Increased Docker memory allocation
* Reduced JVM heap allocation:
    -Xms1g -Xmx1g

⸻

PowerShell Script Execution Restrictions

Windows blocked Winlogbeat installation scripts due to execution policy restrictions.

Resolution

* Updated PowerShell execution policy
* Unblocked downloaded scripts manually

⸻

Endpoint Connectivity Validation

Verified endpoint-to-SIEM communication by accessing Elasticsearch from the Windows VM before configuring Winlogbeat.

⸻

Screenshots

Add screenshots here:

* Kibana Discover view
* Event ID 4624 logs
* Event ID 4625 logs
* Docker containers running
* Dashboard visualizations

⸻

Future Improvements

* Enable Elastic alerting and rule creation
* Add Sysmon telemetry
* Implement detection rules
* Integrate MITRE ATT&CK mapping
* Simulate PowerShell attack activity
* Add automated alert notifications

⸻

Skills Demonstrated

* SIEM deployment
* Docker container management
* Windows log ingestion
* Authentication event analysis
* Security telemetry troubleshooting
* Endpoint monitoring
* Basic detection engineering concepts
