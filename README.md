# Cowrie SSH Honeypot Lab

## Overview
Deployed a Cowrie SSH honeypot on a local Ubuntu virtual machine (VirtualBox) to simulate, capture, and analyze attacker behavior in a controlled environment.

## Environment
- **Host OS:** Windows 11
- **VM:** Ubuntu 24 (VirtualBox)
- **Honeypot:** Cowrie 2.9.17
- **Port:** 2222 (simulated SSH)

## What Cowrie Does
Cowrie is a medium-interaction SSH honeypot that presents attackers with a fake shell environment. It logs all connection attempts, credentials used, and commands executed — and saves any files attackers attempt to download.

## Session Findings (session1.json)
- **Attack vector:** SSH brute-force
- **Credential captured:** root / password123
- **Commands executed by attacker:** whoami, ls, cat /etc/passwd, wget
- **File download attempt:** http://something.com — captured and hashed (SHA-256)
- **Session duration:** 305.8 seconds

## Key Observations
- Attacker immediately ran whoami and ls to establish system context — standard post-exploitation reconnaissance
- Attempted to read /etc/passwd to enumerate user accounts
- Issued a wget command to simulate malware download — Cowrie captured the file and logged its SHA-256 hash for analysis
- All activity logged in structured JSON format for threat intelligence review

## Skills Demonstrated
- Honeypot deployment and configuration on a Linux VM
- SSH threat detection and session logging
- Attacker TTP analysis (MITRE ATT&CK: Discovery, Command and Control)
- Log analysis and threat intelligence documentation
