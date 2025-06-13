# Interesting Findings
## Hallucinations and Error Reporting
I was getting errors related to LLM hallucinations. This would easily occur if a task would require the use of a resource that did not exist. The LLM would try to request the resource and receive an error telling them that it does not exist. However, with seemingly no alternative, the LLM would intentionally hallucinate a value in place of the missing resource to complete the task. 

```py
import framework as fmk

ctx = fmk.Context()
user = fmk.Agent()
llm = fmk.LLMAgent()

x = fmk.Resource("x", 3)
y = fmk.Resource("y", 5)

task1 = fmk.Task("task 1", "add two numbers. the numbers to add are resources x and y. output should be the result of summation (x + y).", output_type=float)
```

To fix this issue, I added the option for the LLM to report errors to the context. This gave the LLM a correct and clearly defined response in situations where it is not clear what it should do. This immediately stopped the AI from hallucinating. Even more interesting than this, without being directly prompted to, the AI would also mark the task as failed, and report the task failure as a separate error. 

An error that stemmed from this solution was error over-reporting, so I had to prompt engineer a little bit on the general LLM prompt to only report errors it cannot resolve and attempt to resolve errors if possible. 
## Recursive Workflow Problem Solving. 