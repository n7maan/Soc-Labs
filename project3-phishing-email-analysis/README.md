# Project 3 – Phishing Email Analysis (IOC Extraction)

## Objective
The objective of this project was to analyze a suspicious email in Gmail and extract IOCs (sender details, authentication results, and the phishing link), similar to how a Junior SOC Analyst would document a phishing ticket.

## Environment
- Email platform: Gmail (Web)
- Tools used: Gmail “Show original”, browser hover/copy link
- Documentation: GitHub (SOC Labs)

## Scenario Overview
I found a suspicious email that claimed my cloud account was locked and my photos/videos would be removed. The email was trying to scare me into clicking a link. I checked the email details in Gmail and collected IOCs without clicking anything.

## Steps Performed
1. Opened the suspicious email in Gmail.
2. Clicked the 3 dots menu and opened “Show original”.
3. Noted the From address/domain, sending IP, and email authentication results.
4. Copied the link address from the email (did not click it).
5. Added all IOCs into an IOC table and saved screenshots as proof.

## Key Findings
- The email used urgency/fear to push me to click fast.
- The sender domain looked random and not related to a real cloud provider.
- Gmail showed DKIM = FAIL and DMARC = FAIL, which is a strong phishing sign.
- The phishing page was hosted on storage.googleapis.com with a suspicious path (legit hosting site, abused by attacker).

## IOCs
Full IOC list: `iocs/iocs.csv`

Important IOCs I collected:
- Sender email: tlcqsupportdn@mxmfcbxinzbskbJwofdirad.com
- Sender domain: mxmfcbxinzbskbJwofdirad.com
- Sending IP: 38.111.111.223
- Auth results: DKIM FAIL, DMARC FAIL
- Phishing URL:
  https://storage.googleapis.com/vcxbiuouioui/IMd02.html#/cuprraa.html?od=...
- URL domain: storage.googleapis.com

## Evidence (Screenshots)
Saved in: `screenshots/`
- gmail-original-message-summary.png
- phishing-link-hover.png

## SOC Analyst Perspective
If this was a real SOC alert, I would:
- Block the phishing URL/path and the suspicious sender domain.
- Search for other emails with the same sender/domain or similar subject text.
- If anyone clicked, recommend password reset + sign out of sessions (depending on what was entered).

## What I Learned
- How to use Gmail “Show original” to check SPF/DKIM/DMARC quickly.
- What phishing emails look like when they use fear/urgency.
- How to safely extract IOCs without interacting with the link.
- Even trusted domains (like cloud hosting) can still be used to host phishing pages.
