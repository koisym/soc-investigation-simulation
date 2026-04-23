# SOC Investigation Simulation

## Overview

I created this project to get more hands-on practice with the investigation side of cybersecurity. In my first lab, I focused more on detection. For this project, I wanted to go a step further and work through a full sequence of events to understand what happened and how it would be reviewed in a SOC environment.

The activity in this lab included reconnaissance, failed SSH login attempts, a successful login, and command activity after access. I used Splunk to review the logs, organize the events, and document the findings.

---

## Objective

The goal of this project was to simulate a small security incident and practice how a SOC analyst would investigate it using available log data.

---

## Lab Environment

This lab was built using:

- Kali Linux
- Ubuntu Server
- Splunk Enterprise
- VirtualBox

Primary log source used:

- `/var/log/auth.log`

---

## Scenario

The simulated activity followed this general timeline:

1. A scan was run against the target system
2. Multiple SSH login attempts failed
3. A successful SSH login occurred
4. Basic commands were run after login
5. Logs were reviewed in Splunk

---

## What I Did

### 1. Performed Reconnaissance

I used Nmap to scan the target system and identify open services. <img width="596" height="234" alt="kali-nmap" src="https://github.com/user-attachments/assets/08d4757f-8e61-4859-950e-1326678945c3" />

### 2. Generated Failed Login Attempts

I used Hydra to create repeated failed SSH login attempts so authentication activity would be written to the logs. <img width="625" height="213" alt="kali-hydra-attempts" src="https://github.com/user-attachments/assets/014275fd-a17d-45ef-a5a8-551fb9f70cfd" />

### 3. Logged In Successfully

After the failed attempts, I logged in through SSH using valid credentials. <img width="339" height="177" alt="successful-ssh-logs" src="https://github.com/user-attachments/assets/4df6f45b-b7d4-43a3-bb12-6b1994685cd9" />

### 4. Simulated Post-Login Activity

Once logged in, I ran basic commands that could be associated with basic system discovery, including:

- `whoami`
- `uname -a`
- `pwd`
- `ls /home`
- `cat /etc/passwd | head`

### 5. Investigated in Splunk

Inside Splunk, I reviewed the logs to:

- verify data ingestion <img width="1213" height="764" alt="splunk-log-ingestion" src="https://github.com/user-attachments/assets/f2572caa-524c-4220-bf5b-551cbf025012" />
- find failed login attempts
- identify the successful login
- build an event timeline <img width="1208" height="601" alt="splunk-auth-timeline" src="https://github.com/user-attachments/assets/558dff5f-4363-4cb4-9799-84f9d41d1639" />
- isolate the source IP <img width="1210" height="333" alt="splunk-source-ip" src="https://github.com/user-attachments/assets/bdd9a6c0-4442-4b15-94df-3c8488940eb6" />
- summarize the activity

---

## Results

The logs showed a clear sequence of events from the same source system. I was able to confirm reconnaissance activity, repeated failed authentication attempts, a successful SSH login, and additional commands after access. <img width="694" height="272" alt="investigation-findings" src="https://github.com/user-attachments/assets/3c1baed8-3725-4500-a4c9-30da663514a4" />

This project helped me better understand how separate log events can be tied together during an investigation instead of being viewed one event at a time.

---

## Skills Demonstrated

- Security monitoring
- Log analysis
- Splunk SPL
- Incident investigation
- Timeline analysis
- Source IP identification
- Linux log review
- Basic triage process
- Technical documentation

---

## Challenges I Ran Into

One of the biggest challenges was rebuilding the lab on a different computer and getting the virtual machines communicating again.

I also ran into setup issues with Splunk during installation and startup. Working through those problems was a good reminder that troubleshooting the environment is part of real-world security work too.

---

## Key Takeaways

This project showed me that investigation work is different from simply creating alerts. It requires reviewing multiple events, understanding the order they happened, and explaining the overall story clearly.

It also reinforced how valuable logs are when trying to understand suspicious behavior.

---

## Future Improvements

In future versions of this lab, I would like to:

- Add multiple source IPs
- Include more user activity after login
- Create alerts based on investigation findings
- Add system logs beyond authentication logs
- Build a more formal incident report
- Expand the scenario into a larger attack chain

---

## Screenshots

The screenshots folder includes:

- Splunk log ingestion
- Nmap scan results
- Hydra login attempts
- Authentication timeline
- Source IP analysis
- Investigation summary

---

## Project Status

Completed as a hands-on SOC investigation project and added to my cybersecurity portfolio.
