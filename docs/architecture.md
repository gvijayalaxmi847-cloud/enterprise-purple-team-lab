# Lab Architecture - Project CrossFire

## Network Topology
- **Attacker Machine (Red):** Kali Linux (192.168.56.10)
- **Victim Endpoint (Target):** Windows 10/11 Enterprise or Windows Server (192.168.56.20)
- **SIEM / Log Server (Blue):** Wazuh / Elastic / Splunk (192.168.56.30)

## Telemetry & Logging Sources
- Sysmon (SwiftOnSecurity or Olaf Hartong config)
- Windows Security & PowerShell Operational Logs
- SIEM Agent forwarding logs to central collector
