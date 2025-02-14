---
tags:
  - "#literature"
  - "#multi-agent"
title: "Flow: A Modular Approach to Automated Agentic Workflow Generation"
author: Boye Niu, Yiliao Song, Kai Lian, Yifan Shen, Yu Yao, Kun Zhang, Tongliang Liu
year: 2025
link: https://arxiv.org/abs/2501.07834
---
# Take Away Points
- 

# Summary
Flow introduces a multi-agent workflow that dynamically assigns tasks and creates agent topology. The model emphasizes a modular approach which maximizes parallelism and minimizes task interdependency and complexity. This approach allows the workflow to adapt to challenges and conditions in real-time. Results of the model show improved workflow efficiency. 

# Method

## AOV (Activity on Vertex) Graph
AOV graphs are a type of directed acyclic graphs where vertices represent tasks and edges denote precedence relations. We denote the graph as such:
$$G=(V, E, A)$$
- $V$: the set of all sub-tasks (nodes)
- $E$: the set of directed edges indicating sub-task dependencies
- $A$: the set of all agents

### Parallelism
Let $S_t$ represent the set of tasks executed at step $t$. The degree of parallelism at a step is given by the ratio