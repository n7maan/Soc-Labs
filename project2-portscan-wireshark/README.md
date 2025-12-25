# Project 2 – Port Scan Detection Using Wireshark (SYN Scan)

## Objective
The objective of this project was to simulate a basic port scan and identify the scan behavior in a packet capture using Wireshark, similar to how a SOC analyst would recognize reconnaissance activity on a network.

## Environment
- Operating System: Windows 11
- Tools Used: Wireshark, Nmap
- Capture Interface: Wi-Fi

## Scenario Overview
A SYN scan was generated using Nmap against a local target. The resulting traffic was captured in Wireshark and filtered to highlight SYN packets consistent with port scanning / reconnaissance behavior.

## Steps Performed
1. Started a live capture in Wireshark on the active Wi-Fi interface.
2. Ran a SYN scan using Nmap in a controlled lab scenario:
   - `nmap -sS 127.0.0.1`
3. Stopped the capture after the scan completed.
4. Applied a Wireshark display filter to isolate SYN packets (without ACK) commonly seen during scanning:
   - `tcp.flags.syn == 1 && tcp.flags.ack == 0`
5. Observed a burst of SYN packets within a short time window, consistent with reconnaissance / port scan behavior.

## Key Findings
- A SYN scan produces many TCP packets with the SYN flag set as the scanner probes ports.
- Filtering for SYN packets without ACK helps highlight scan-like behavior in packet captures.
- This pattern can help SOC analysts quickly identify potential reconnaissance activity for further triage.

## Evidence
Redacted screenshot(s) are available here:
- [Screenshots folder](./screenshots)
