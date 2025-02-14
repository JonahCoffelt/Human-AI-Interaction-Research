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
Let $S_t$ represent the set of tasks executed at step $t$. The degree of parallelism at a step is given by the ratio of the number of tasks in that step to the total number of tasks.
$$P(t) = \frac{|S_t|}{|V|}$$
We may capture the parallelism of a given AOV by averaging $P(t)$ over all steps
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

![](Pasted%20image%2020250214002956.png)

