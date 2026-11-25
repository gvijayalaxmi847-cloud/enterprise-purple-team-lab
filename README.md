# Enterprise Purple Team Lab (Project CrossFire)

An automated, open-source cyber range simulating an enterprise network with continuous **CIS Benchmark compliance**, **adversary emulation**, and **SOAR-driven remediation**.

## 🏗️ Enterprise Network Architecture & Subnets

`mermaid
graph TD
    Internet((External / Internet)) -->|NAT / WAN| FW[OPNsense Zero-Trust Firewall]
    FW -->|10.10.10.1/24 - intnet-red| RED[Red Team / Attack Zone<br/>Kali Linux: 10.10.10.10]
    FW -->|10.10.20.1/24 - intnet-prod| PROD[Corp-Prod Zone<br/>Ubuntu Server: 10.10.20.10]
    FW -->|10.10.30.1/24 - intnet-soc| SOC[SOC-Defense Zone<br/>Wazuh & Shuffle: 10.10.30.10]
    
    RED -.->|Simulated Attacks| PROD
    PROD -->|Telemetry & CIS Logs| SOC
    SOC -.->|API Auto-Block| FW
`

| VirtualBox Network Mode | Internal Network Name | Subnet CIDR | Gateway (OPNsense) | Zone & Purpose |
| :--- | :--- | :--- | :--- | :--- |
| **NAT** | *(Default NAT)* | DHCP | WAN Interface | Provides internet access for OS/tool updates only. |
| **Internal Network** | intnet-red | 10.10.10.0/24 | 10.10.10.1 | **Red Team Zone:** Kali Linux, Nuclei, MITRE Caldera. |
| **Internal Network** | intnet-prod | 10.10.20.0/24 | 10.10.20.1 | **Corp-Prod Zone:** Hardened Ubuntu target & web apps. |
| **Internal Network** | intnet-soc | 10.10.30.0/24 | 10.10.30.1 | **SOC-Defense Zone:** Wazuh SIEM/SCA & Shuffle SOAR. |

## 📂 Repository Structure
- **ed-team/**: Offensive simulations, attack playbooks, and TTPs
- **lue-team/**: Detection rules (SIEM/EDR), log analysis, and defensive baselines
- **purple-exercises/**: Joint attack-and-detect validation reports
- **docs/**: Architecture diagrams, lab setup notes, and network topology
