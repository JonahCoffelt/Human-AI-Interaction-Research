---
tags:
  - "#literature"
title: A risk-based model for human-artificial intelligence conflict resolution in process systems
author: He Wen, Faisal Khan
year: 2024
link: https://www.sciencedirect.com/science/article/pii/S2772508124000565
---

# Summary
The paper proposes a model to quantify and resolve conflicts which result from discrepancies in human and AI observation, interpretation, and action. The mathematical model is based on conventional human conflict resolution mechanisms. The authors claim the model promotes human-AI collaboration with real-time response to human input. 
## Introduction
Although AI has developed human-like skills, their decision making deviates from human expectations. This phenomenon is described as human-AI conflict, which can often be "mistakenly interpreted as faults, failures, or cyberattacks". Because of the anthropomorphic characteristics  of AI decision making, a potential solution could be to use human-human conflict resolutions models such as  the Thomas-Kilmann Instrument (TKI). Currently, control systems "lack the capability to perceive and integrate human observations and actions with the data they collect", which prevents human-AI collaboration in their use cases. With this problem in mind, the paper seeks to address four problems:

1) How to best mathematically represent the evolving conflict between humans and AI?
2) What are the strategies of conflict resolution?
3) How do we measure the conflict risk and link it to resolution strategies?
4) How do we adapt the well-established social conflict resolution strategies to human-AI conflict resolution?

## Methodology
Adapts the TKI model as a risk model. Comprised of three steps

1) Construct the conflict risk representations by measuring the agreement level of interpretations and actions.
2) Propose mathematical equations to measure conflict probability
3) Develop conflict resolution strategies by minimizing the conflict risk.

## The Model
Generally, the model lies on a two axis plane, where the $x$ is the agreement of interpretation and $y$ is agreement of actions. The model proposes a vector for the human $(x_h, y_h)$ and a vector for the AI $(x_a, y_a)$. The angle between these two vectors $\Delta \theta$ is correlated to the probability of conflict $P$, and the difference in magnitude $\Delta y$ is correlated to the severity of a potential conflict $S$. The risk is the sum of the probability and severity of conflict, $R=P+S$.

![](Images/20250203210646.png)

This model suggests that risk may be minimized by minimizing $P$ and $S$.

## Application
The paper detailed a simulation of a two-phase separator for oil and gas separation in which there was a human operator and AI controller. Throughout the simulation, the AI system was detecting normal levels while the human observed the oil rising beyond normal levels. This difference in observations led to a conflict in which the human first fought the AI's action and eventually overrode the AI controller entirely. To minimize the risk of a conflict like this, the AI should be able to receive some input from the human so there is less of a difference in observation. 

# Questions/Note
- Why $R=P+S$ instead of the product as is typical in risk calculation?
- This assumption reflects the current state of AI development, where AI lacks the ability to perceive human value judgments and does not possess human-like perception or cognitive capabilities.
- **Targeted manipulation of data sensors and targeted social engineering.**