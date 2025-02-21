---
tags:
  - "#literature"
title: "AI Agents Under Threat: A Survey of Key Security Challenges and Future Pathways"
author: Zehang Deng, Yongjian Guo, Changzhou Han, Wanlun Ma, Junwu Xiong, Sheng Wen, Yang Xiang
year: 2024
link: https://arxiv.org/abs/2406.02630
---
# Summary
The paper identifies four knowledge gaps in AI agent security:
1. Unpredictability of multi-step user inputs
	- User inputs may be inadequately described or involve multiple steps. Insufficient specification can lead to failed tasks, unintentional results, or security threats. Malicious users may also attempt to influence the AI agent to execute unsafe code or action.
2. Complexity in internal executions
	- Internal executions are often complex chain-loop structures. It can be difficult to observe the internal state and detect threats in a timely manner.
3. Variability of operational environments
	- Variability in the environment the AI agent is acting, specifically from development to deployment, in can produce inconsistent and potentially dangerous results.
4. Interactions with untrusted external entities
	- Current AI agent interaction processes assumes a trusted external agent. This opens may attack surfaces, such as prompt injection.

# Terminology
In relation to an AI agent:
- **Input Formatter**: A tool used to enhance the quality of input. Used in perception
- **Reasoning**: An LLM designed to analyze and deduce information to draw conclusions from given prompts. 
- **Planning**: An LLM designed to devise strategies and make decisions by evaluating possible outcomes. 
- **Brain**: The combination of reasoning and planning LLMs.

# Intra-execution Security
