---
tags:
  - "#literature"
  - "#multi-agent"
title: "Flow: A Modular Approach to Automated Agentic Workflow Generation"
author: Boye Niu, Yiliao Song, Kai Lian, Yifan Shen, Yu Yao, Kun Zhang, Tongliang Liu
year: 2025
link: https://arxiv.org/abs/2501.07834
---
# Summary
Flow introduces a multi-agent workflow that dynamically assigns tasks and creates agent topology. The model emphasizes a modular approach which maximizes **parallelism** and minimizes task **dependency complexity**. This approach allows the workflow to adapt to challenges and conditions in real-time. Results of the model show improved workflow efficiency. 

# Method

## AOV (Activity on Vertex) Graph
AOV graphs are a type of directed acyclic graphs where vertices represent tasks and edges denote precedence relations. We denote the graph as such:
$$G=(V, E, A)$$
- $V$: the set of all sub-tasks (nodes)
- $E$: the set of directed edges indicating sub-task dependencies
- $A$: the set of all agents

### Parallelism
Let $S_t$ represent the set of tasks executed at step $t$. The degree of parallelism at a step is given by the ratio of the number of tasks in that step to the total number of tasks.
$$P(t) = \frac{|S_t|}{|V|}$$
We may capture the parallelism of a given AOV graph by averaging $P(t)$ over all steps
$$P_{avg} = \frac1T \sum_{t=1}^{T}P(t)$$
### Dependency Complexity
The measure of parallelism alone does not capture the modularity of tasks which can be completed independently of others. For each task $v_i$, the degree $deg(v_i)$ will be the number of connections the node has in the graph $G$. Like we did with parallelism, we will average the degree of all tasks to find $\overline d$:
$$\overline d = \frac{1}{|V|} \sum_{v_i\in V} deg(v_i)$$
The complexity of task dependencies is then quantified by the standard deviation of the degree distribution:
$$C_{dependency} = \sqrt{\frac{1}{|V|} \sum_{v_i\in V} (deg(v_i) - \overline d)^2}$$
### Initial AOV
The authors use an LLM to generate a set of candidate graphs $\{G_1, G_2, ...\}$. The initial graph is chosen first by the highest parallelism score, then by the lowest dependency complexity. Parallelism is prioritized in the early stages to avoid sequential workflows which would hinder the modularity in the long term.

### Execution Plan
A topological sort is used to produce a linear ordering of steps containing tasks which may be completed in parallel. Agents are then assigned tasks based on their capabilities (Not sure what this means, I think it is a prompt thing though?). 

### Workflow Refinement and Dynamic Updating
The authors use another LLM as an inspector to update the AOV. The LLM is given requirements, the current graph, and data containing the status of tasks and output. The LLM continuously monitors tasks progression and updates the workflow as needed. The update is a similar process to the initial generation, where LLM produces a set of candidates and the best one is chosen. 

![](Pasted%20image%2020250214002956.png)

## Experiments and Results
The authors applied their model to three design workflows: 1) Website development 2) LaTeX Beamer slide creation, and 3) interactive game development. In all cases, the model was able to outperform current workflow models. See the paper for specific details on results.

### Relevance to our Topic
- **Model Adaptations:** Their model incorporates many AI agents in a unified and efficient workflow, but they do not consider the introduction of a human agent into the workflow. It could be interesting to see how this model could be modified to better implement human-AI workflows. The focus on modularity could certainly help to distinguish human tasks from AI tasks and allow for these agents to work together as the AI agents did.
- **Information and Interface presentation**: The paper's experiments include the consideration of how data, information, and interfaces are presented to human users. For example, the game created by the agents included UI that was tailored for humans. It could be interesting to see how these types of antigenic workflows could improve AI-Human communication.