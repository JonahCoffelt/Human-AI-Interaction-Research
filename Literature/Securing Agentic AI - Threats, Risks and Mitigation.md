---
tags:
  - "#literature"
title: Securing Agentic AI - Threats, Risks and Mitigation
author: S M Zia Ur Rashid, Irfanul Montasir, Ashfaqul Haq
year: 2025
link: https://www.researchgate.net/profile/S-M-Zia-Ur-Rashid/publication/388493552_Securing_Agentic_AI_Threats_Risks_and_Mitigation/links/679ad00352b58d39f25b9aad/Securing-Agentic-AI-Threats-Risks-and-Mitigation.pdf
---
# Introduction
The paper identifies potential securities risks that arise from the increased use of AI in enterprise applications. The paper seeks to lays these risks out to lay the groundwork for further research in the topic. 

[OWASP](https://owasp.org/www-project-top-ten/)
# Attack Vectors
## Hallucination Exploitation
Adversaries may make AI suggest or provide suggestions which lead to security risks. For example, the AI may suggest the use of non-existent software library. An attacker may develop an interface under this name and have it integrated into the system, potentially giving the attacker access servers or back end systems. 

## Knowledge Base Poisoning
Internal or external attackers could feed AI " contaminated or detrimental data into the knowledge base so that it produces wrong or unsolicited outcomes.". This could result in exploitable vulnerabilities in the platforms or result in altered AI agent behavior in systems. 
## Jailbreaking and Control Hijacking
Attackers could use prompts that bypass the security measures and restrictions placed on an AI model. This can allow the attacker to execute unlawful commands. This presents threats to autonomous vehicles, smart home devices, privacy, and financial/medical records. An example of this is the [Alexa vs Alexa](https://www.ava-attack.org/) attack which enabled attackers to infiltrate home automation systems. 

## Memory and Context Manipulation
Memory poisoning or context erasure could make the agent forget important contextual information. "Such exploits may include making insecure session states or other improper resource management that leads to memory overflow or directly defeats security provisions and impacts system services."

## Multi-Agent Exploitation
Multi-agent systems are susceptible to probing, repudiation, flooding, impersonation and denial of service (DoS) attacks. The failure of a single agent could undermine the entire system. 
- It could be interesting to see how [Flow](Flow%20–%20A%20Modular%20Approach%20to%20Automated%20Agentic%20Workflow%20Generation.md) as a modular approach could potentially help to mitigate this issue.
- More information on this topic in [Security of Multi-Agent Cyber-Physical Systems](Security%20of%20Multi-Agent%20Cyber-Physical%20Systems.md) 