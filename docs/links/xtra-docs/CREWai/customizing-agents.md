# Customizing Agents in CrewAI - crewAI
![](Customizing-Agents.png)      


Crafting an efficient CrewAI team hinges on the ability to dynamically tailor your AI agents to meet the unique requirements of any project. This section covers the foundational attributes you can customize.

### Key Attributes for Customization[¶](https://docs.crewai.com/how-to/Customizing-Agents/#key-attributes-for-customization)

* **Role**: Specifies the agent's job within the crew, such as 'Analyst' or 'Customer Service Rep'.
* **Goal**: Defines what the agent aims to achieve, in alignment with its role and the overarching objectives of the crew.
* **Backstory**: Provides depth to the agent's persona, enriching its motivations and engagements within the crew.
* **Tools** *(Optional)*: Represents the capabilities or methods the agent uses to perform tasks, from simple functions to intricate integrations.
* **Cache** *(Optional)*: Determines whether the agent should use a cache for tool usage.
* **Max RPM**: Sets the maximum number of requests per minute (`max_rpm`). This attribute is optional and can be set to `None` for no limit, allowing for unlimited queries to external services if needed.
* **Verbose** *(Optional)*: Enables detailed logging of an agent's actions, useful for debugging and optimization. Specifically, it provides insights into agent execution processes, aiding in the optimization of performance.
* **Allow Delegation** *(Optional)*: `allow_delegation` controls whether the agent is allowed to delegate tasks to other agents. This attribute is now set to `False` by default.
* **Max Iter** *(Optional)*: The `max_iter` attribute allows users to define the maximum number of iterations an agent can perform for a single task, preventing infinite loops or excessively long executions. The default value is set to 25, providing a balance between thoroughness and efficiency.
* **Max Execution Time** *(Optional)*: `max_execution_time` Sets the maximum execution time for an agent to complete a task.
* **System Template** *(Optional)*: `system_template` defines the system format for the agent.
* **Prompt Template** *(Optional)*: `prompt_template` defines the prompt format for the agent.
* **Response Template** *(Optional)*: `response_template` defines the response format for the agent.
* **Use System Prompt** *(Optional)*: `use_system_prompt` controls whether the agent will use a system prompt for task execution. Agents can now operate without system prompts.
* **Respect Context Window**: `respect_context_window` renames the sliding context window attribute and enables it by default to maintain context size.
* **Max Retry Limit**: `max_retry_limit` defines the maximum number of retries for an agent to execute a task when an error occurs.

⠀
## Advanced Customization Options[¶](https://docs.crewai.com/how-to/Customizing-Agents/#advanced-customization-options)

Beyond the basic attributes, CrewAI allows for deeper customization to enhance an agent's behavior and capabilities significantly.

### Language Model Customization[¶](https://docs.crewai.com/how-to/Customizing-Agents/#language-model-customization)

Agents can be customized with specific language models (`llm`) and function-calling language models (`function_calling_llm`), offering advanced control over their processing and decision-making abilities. It's important to note that setting the `function_calling_llm` allows for overriding the default crew function-calling language model, providing a greater degree of customization.

## Performance and Debugging Settings[¶](https://docs.crewai.com/how-to/Customizing-Agents/#performance-and-debugging-settings)

Adjusting an agent's performance and monitoring its operations are crucial for efficient task execution.

### Verbose Mode and RPM Limit[¶](https://docs.crewai.com/how-to/Customizing-Agents/#verbose-mode-and-rpm-limit)

* **Verbose Mode**: Enables detailed logging of an agent's actions, useful for debugging and optimization. Specifically, it provides insights into agent execution processes, aiding in the optimization of performance.
* **RPM Limit**: Sets the maximum number of requests per minute (`max_rpm`). This attribute is optional and can be set to `None` for no limit, allowing for unlimited queries to external services if needed.

⠀
### Maximum Iterations for Task Execution[¶](https://docs.crewai.com/how-to/Customizing-Agents/#maximum-iterations-for-task-execution)

The `max_iter` attribute allows users to define the maximum number of iterations an agent can perform for a single task, preventing infinite loops or excessively long executions. The default value is set to 25, providing a balance between thoroughness and efficiency. Once the agent approaches this number, it will try its best to give a good answer.

Agents are customized by defining their attributes and tools during initialization. Tools are critical for an agent's functionality, enabling them to perform specialized tasks. The `tools` attribute should be an array of tools the agent can utilize, and it's initialized as an empty list by default. Tools can be added or modified post-agent initialization to adapt to new requirements.

```
pip install 'crewai[tools]'
```

```
import os
from crewai import Agent
from crewai_tools import SerperDevTool

# Set API keys for tool initialization
os.environ["OPENAI_API_KEY"] = "Your Key"
os.environ["SERPER_API_KEY"] = "Your Key"

# Initialize a search tool
search_tool = SerperDevTool()

# Initialize the agent with advanced options
agent = Agent(
 role='Research Analyst',
 goal='Provide up-to-date market analysis',
 backstory='An expert analyst with a keen eye for market trends.',
 tools=[search_tool],
 memory=True, # Enable memory
 verbose=True,
 max_rpm=None, # No limit on requests per minute
 max_iter=25, # Default value for maximum iterations
)
```

## Delegation and Autonomy[¶](https://docs.crewai.com/how-to/Customizing-Agents/#delegation-and-autonomy)

Controlling an agent's ability to delegate tasks or ask questions is vital for tailoring its autonomy and collaborative dynamics within the CrewAI framework. By default, the `allow_delegation` attribute is now set to `False`, disabling agents to seek assistance or delegate tasks as needed. This default behavior can be changed to promote collaborative problem-solving and efficiency within the CrewAI ecosystem. If needed, delegation can be enabled to suit specific operational requirements.

### Example: Disabling Delegation for an Agent[¶](https://docs.crewai.com/how-to/Customizing-Agents/#example-disabling-delegation-for-an-agent)

```
agent = Agent(
 role='Content Writer',
 goal='Write engaging content on market trends',
 backstory='A seasoned writer with expertise in market analysis.',
 allow_delegation=True # Enabling delegation
)
```

## Conclusion[¶](https://docs.crewai.com/how-to/Customizing-Agents/#conclusion)

Customizing agents in CrewAI by setting their roles, goals, backstories, and tools, alongside advanced options like language model customization, memory, performance settings, and delegation preferences, equips a nuanced and capable AI team ready for complex challenges.

[Customizing Agents in CrewAI - crewAI](https://docs.crewai.com/how-to/Customizing-Agents/)

