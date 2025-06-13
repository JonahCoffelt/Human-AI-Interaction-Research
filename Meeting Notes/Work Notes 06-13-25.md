# Interesting Findings
## Hallucinations and Error Reporting
I was getting errors related to LLM hallucinations. This would easily occur if a task would require the use of a resource that did not exist. The LLM would try to request the resource and receive an error telling them that it does not exist. However, with seemingly no alternative, the LLM would intentionally hallucinate a value in place of the missing resource to complete the task. 

Example:
```python
import framework as fmk

ctx = fmk.Context()
user = fmk.Agent()
llm = fmk.LLMAgent()

x = fmk.Resource("x", 3)

task1 = fmk.Task("task 1", "add the values of resources x and y", output_type=float)

user.call_tool("message", receiver=llm.address, content="Do task 'task 1'")
```

To fix this issue, I added the option for the LLM to report errors to the context. This gave the LLM a correct and clearly defined response in situations where it is not clear what it should do. This immediately stopped the AI from hallucinating. Even more interesting than this, without being directly prompted to, the AI would also mark the task as failed, and report the task failure as a separate error. 

Now when running the above script, I get `LLM reporting error: The resource y does not exist.`

An error that stemmed from this solution was error over-reporting, so I had to prompt engineer a little bit on the general LLM prompt to only report errors it cannot resolve and attempt to resolve errors if possible. 
## Recursive Workflow Problem Solving
In an effort to test how the LLM would respond to unexpected situations, especially with the newly added error reporting. I created a situation in which a task A relies on the completion of a task B for input, but I would ask the LLM to complete task B when task A was incomplete. I expected the LLM to simply report this error, but to my surprise, when the LLM noticed that task A was not complete and it needed it in order to progress, it actually went and solved task A then solved task B without reporting any errors. 

Because I thought this was an interesting display of problem solving, I decided to give it a harder challenge with a chain of multi-dependent tasks. Here is the example I used:

```python
import framework as fmk

ctx = fmk.Context()
user = fmk.Agent()
llm = fmk.LLMAgent()

x = fmk.Resource("x", 2)
y = fmk.Resource("y", 4)

A = fmk.Task("A", "Add the values of resource x and y. ", output_type=float)
B = fmk.Task("B", "Multiply this tasks input by 2. ", [A], output_type=float)
C = fmk.Task("C", "Subtract 4 from this tasks input. ", [B], output_type=float)
D = fmk.Task("D", "Divide this tasks input by 4. ", [B], output_type=float)
E = fmk.Task("E", "Multiply the inputs of this task. ", [C, D], output_type=float)
```

I first tested this by requesting the task be completed in a valid ordering, and the results came back correct as expected. When I just asked the LLM to do task E, leaving all other tasks incomplete, the LLM recursively solved all of the tasks in the correct order, producing the same output as the series of sequential requests. I think this is a really interesting display of problem solving. 

There is a potential objection to this outcome that we do not want the LLM to do tasks it is not asked to do. A clear solution to this is to simply use the root to limit what tasks the LLM is able to access and interact with, thus preventing this behavior. I do not have roots implemented yet, but my suspicion is that this would result in the reporting of an error, since the LLM would have no way to resolve the error.  