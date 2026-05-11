# Encoded PowerShell Detection

## Objective
Simulate and detect encoded PowerShell execution in a Windows environment using Sysmon telemetry.

---

## Attack Simulation

Example command:

```powershell
powershell.exe -enc <base64_string>
```

---

## What happens?

Encoded PowerShell hides the command content, but:
- process creation is still visible
- command line is logged (if Sysmon enabled)

---

## Telemetry Source
- Sysmon Event ID 1 (Process Creation)
- Optional: PowerShell Script Block Logging

---

## MITRE ATT&CK
T1059.001 - PowerShell

---

## Detection Idea
We look for:
- powershell.exe
- "-enc" or "-encodedcommand"
- suspicious long base64 strings in command line

---

## What I learned 
- Sysmon is essential for process visibility
- encoded commands are obfuscation, not invisibility
- command-line logging is critical in SOC detection
- Sysmon is essential for process visibility
- encoded commands are obfuscation, not invisibility
- command-line logging is critical in SOC detection
