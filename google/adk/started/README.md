# Get Started with Agent Development Kit (ADK)

## Overview: Benefits of Agent Development Kit

Agent Development Kit offers several key advantages for developers building agentic applications:

1. **Multi-Agent Systems**: Build modular and scalable applications by composing multiple specialized agents in a hierarchy. Enable complex coordination and delegation.

2. **Rich Tool Ecosystem**: Equip agents with diverse capabilities: use pre-built tools (Search, Code Execution, etc.), create custom functions, integrate tools from third-party agent frameworks (LangChain, CrewAI), or even use other agents as tools.

3. **Flexible Orchestration**: Define workflows using workflow agents (`SequentialAgent`, `ParallelAgent`, and `LoopAgent`) for predictable pipelines, or leverage LLM-driven dynamic routing (`LlmAgent` transfer) for adaptive behavior.

4. **Integrated Developer Experience**: Develop, test, and debug locally with a powerful CLI and an interactive dev UI. Inspect events, state, and agent execution step-by-step.

5. **Built-in Evaluation**: Systematically assess agent performance by evaluating both the final response quality and the step-by-step execution trajectory against predefined test cases.

6. **Deployment Ready**: Containerize and deploy your agents anywhere – run locally, scale with Vertex AI Agent Engine, or integrate into custom infrastructure using Cloud Run or Docker.

While other Gen AI SDKs or agent frameworks also allow you to query models and even empower them with tools, dynamic coordination between multiple models requires a significant amount of work on your end.

Agent Development Kit offers a higher-level framework than these tools, allowing you to easily connect multiple agents to one another for complex but easy-to-maintain workflows.

```
Easy to use
        ▲
        │  ┌─────────────────────────────────┐
        │  │ Solutions: Agentspace and       │
        │  │ Conversational Agents           │
        │  └─────────────────────────────────┘
        │  ┌ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ┐
        │    Agent-specific framework:
        │  │                                                 │
        │    ┌──────────────────────────────┐  • Smolagent
        │  │ │ Google Agent Development Kit │  • CrewAI      │
        │    │ Balance of deterministic     │  • LangGraph
        │  │ │ control and convenience      │  • AG2/Autogen │
        │    └──────────────────────────────┘                                    
        │  └ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ┘
        │          ┌───────────────────────────────┐
        │          │ Low-level orchestration       │
        │          │ framework: LangChain, GenKit  │
        │          └───────────────────────────────┘
        │                  ┌───────────────────────────────────┐
        │                  │ Build your own: Use function      │
Hard to use                │ calling to build your own agent   │
        │                  │ framework                         │
        │                  └───────────────────────────────────┘
        └──────────────────────────────────────────────────────────►
    Low flexibility                              High flexibility
```

Additionally, it allows you to deploy these complex systems of agents to a fully-managed endpoint in Agent Engine, so you can focus on the agents' logic while infrastructure is allocated and scaled for you.

## Objectives

In this lab, you will create a single agent that can use a search tool. You will test agents in ADK's browser UI, from a CLI chat interface, and programmatically from within a script.

You will consider:

- The key capabilities of Agent Development Kit
- The core concepts of ADK
- How to structure project directories for ADK
- The most fundamental parameters of agents in ADK, including how to specify model names and tools
- Some features of ADK's browser UI
- How to control the output schema of an agent
- How to run agents in three ways (via the browser UI, programmatically, and via the CLI chat interface)

## Setup and requirements

### Before you click the Start Lab button

Read these instructions. Labs are timed and you cannot pause them. The timer, which starts when you click **Start Lab**, shows how long Google Cloud resources will be made available to you.

This Qwiklabs hands-on lab lets you do the lab activities yourself in a real cloud environment, not in a simulation or demo environment. It does so by giving you new, temporary credentials that you use to sign in and access Google Cloud for the duration of the lab.

### What you need

To complete this lab, you need:

- Access to a standard internet browser (Chrome browser recommended).
- Time to complete the lab.

> **Note:** If you already have your own personal Google Cloud account or project, do not use it for this lab.

> **Note:** If you are using a Pixelbook, open an Incognito window to run this lab.

## Task 1. Install ADK and set up your environment

> **Note:** Using an Incognito browser window is recommended for most Qwiklabs to avoid confusion between your Qwiklabs student account and other accounts logged into Google Cloud. If you are using Chrome, the easiest way to accomplish this is to close any Incognito windows, then right click on the **Open Google Cloud console** button at the top of this lab and select **Open link in Incognito window**.

### Enable Vertex AI recommended APIs

1. In this lab environment, the **Vertex AI API has been enabled for you**. If you were to follow these steps in your own project, you could enable it by navigating to Vertex AI and following the prompt to enable it.

### Prepare a Cloud Shell Editor tab

1. With your Google Cloud console window selected, open Cloud Shell by pressing the G key and then the S key on your keyboard. Alternatively, you can click the Activate Cloud Shell button in the upper right of the Cloud console.

2. Click **Continue**.

3. When prompted to authorize Cloud Shell, click **Authorize**.

4. In the upper right corner of the Cloud Shell Terminal panel, click the **Open in new window** button.

5. Click the **Open Editor** pencil icon at the top of the pane to view files.

6. At the top of the left-hand navigation menu, click the Explorer icon to open your file explorer.

7. Click the **Open Folder** button.

8. In the Open Folder dialog that opens, click **OK** to select your Qwiklab student account's home folder.

9. Close any additional tutorial or Gemini panels that appear on the right side of the screen to save more of your window for your code editor.

10. Throughout the rest of this lab, you can work in this window as your IDE with the Cloud Shell Editor and Cloud Shell Terminal.

### Download and install the ADK and code samples for this lab

1. Paste the following command into the Cloud Shell Terminal to copy a project directory with code for this lab from a Cloud Storage bucket:

   ```bash
   gcloud storage cp -r gs://YOUR_GCP_PROJECT_ID-bucket/adk_project .
   ```

2. Update your `PATH` environment variable to include your user's local environment and **install ADK & other lab requirements** by running the following commands in the Cloud Shell Terminal.

   ```bash
   export PATH=$PATH:"/home/${USER}/.local/bin"
   python3 -m pip install google-adk -r adk_project/requirements.txt
   ```

### Core Concepts of Agent Development Kit

Google ADK is built around a few core concepts that make it powerful and flexible:

- **Agent**: Agents are core building blocks designed to accomplish specific tasks. They can be powered by LLMs to reason, plan, and utilize tools to achieve goals, and can even collaborate on complex projects.
- **Tools**: Tools give agents abilities beyond conversation, letting them interact with external APIs, search information, run code, or call other services.
- **Session Services**: Session services handle the context of a single conversation (`Session`), including its history (`Events`) and the agent's working memory for that conversation (`State`).
- **Callbacks**: Custom code snippets you provide to run at specific points in the agent's process, allowing for checks, logging, or behavior modifications.
- **Artifact Management**: Artifacts allow agents to save, load, and manage files or binary data (like images or PDFs) associated with a session or user.
- **Runner**: The engine that manages the execution flow, orchestrates agent interactions based on Events, and coordinates with backend services.

## Task 2. Review the structure of Agent Development Kit project directories

1. In the Cloud Shell Editor's file explorer pane, find the **adk_project** folder. Click it to toggle it open.

2. This directory contains three other directories: **my_google_search_agent**, **app_agent**, and **llm_auditor**. Each of these directories represents a separate agent. Separating agents into their own directories within a project directory provides organization and allows Agent Development Kit to understand what agents are present.

3. Click on the **my_google_search_agent** to explore an agent directory.

4. Notice that the directory contains an `__init__.py` file and an `agent.py` file. An `__init__.py` file is typically used to identify a directory as a Python package that can be imported by other Python code. Click the **init.py file** to view its contents.

5. Notice that the **init.py** file contains a single line, which imports from the **agent.py** file. ADK uses this to identify this directory as an agent package:

   ```python
   from . import agent
   ```

6. Now click on the **agent.py** file. This file consists of a simple agent. You will equip it with a powerful tool: the ability to search the internet using Google Search. Notice a few things about the file:

   - Notice the imports from `google.adk`: the `Agent` class and the `google_search` tool from the `tools` module

   - Read the code comments that describe the parameters that configure this simple agent.

7. To use the imported `google_search` tool, it needs to be passed to the agent. Paste the following line into the **agent.py** file where indicated at the end of the `Agent` object creation:

   ```python
   tools=[google_search]
   ```

8. **Save** the file.

> Tools enable an agent to perform actions beyond generating text. In this case, the `google_search` tool allows the agent to decide when it would like more information than it already has from its training data. It can then write a search query, use Google Search to search the web, and then base its response to the user on the results. When a model bases its response on additional information that it retrieves, it is called "grounding," and this overall process is known as "retrieval-augmented generation" or "RAG."
>
> You can learn more about how to use tools with ADK in the lab *Empower ADK agents with tools*.

## Task 3. Run the agent using the ADK's Dev UI

ADK includes a development UI designed to run locally to help you develop and test your agents. It can help you visualize what each agent is doing and how multiple agents interact with one another. You will explore this interface in this task.

> When you run an agent, the ADK needs to know who is requesting the model API calls. You can provide this information in one of two ways. You can:
>
> 1. Provide a [Gemini API key](https://aistudio.google.com/apikey).
>
> 2. Authenticate your environment with Google Cloud credentials and associate your model API calls with a Vertex AI project and location.
>
> In this lab, you will take the Vertex AI approach.

1. In the Cloud Shell Terminal, run the following to write a `.env` file which will be read to set environment variables instructing the agent to use your project and the global endpoint:

   ```bash
   cd ~/adk_project
   cat << EOF > my_google_search_agent/.env
   GOOGLE_GENAI_USE_VERTEXAI=TRUE
   GOOGLE_CLOUD_PROJECT=YOUR_GCP_PROJECT_ID
   GOOGLE_CLOUD_LOCATION=global
   MODEL=gemini_flash_model_id
   EOF
   ```

2. **Save** the file.

> These variables play the following roles:
>
> - `GOOGLE_GENAI_USE_VERTEXAI=TRUE` indicates that you will use Vertex AI for authentication as opposed to Gemini API key authentication.
> - `GOOGLE_CLOUD_PROJECT` and `GOOGLE_CLOUD_LOCATION` provide the project and location with which to associate your model calls.
> - `MODEL` is not required, but is stored here so that it can be loaded as another environment variable. This can be a convenient way to try different models in different deployment environments.
>
> When you test your agent using ADK's dev UI or the command-line chat interface, they will load and use an agent's `.env` file if one is present or else look for environment variables with the same names as those set here.

6. In the Cloud Shell Terminal, ensure you are in the **adk_project** directory where your agent subdirectories are located by running:

   ```bash
   cd ~/adk_project
   ```

7. **Launch the Agent Development Kit Dev UI** with the following command:

   ```bash
   adk web
   ```

   **Output**
   ```bash
   INFO:     Started server process [2434]
   INFO:     Waiting for application startup.
   +-------------------------------------------------------+
   | ADK Web Server started                                |
   |                                                       |
   | For local testing, access at http://localhost:8000.   |
   +-------------------------------------------------------+   
   INFO:     Application startup complete.
   INFO:     Uvicorn running on http://127.0.0.1:8000 (Press CTRL+C to quit)
   ```

8. To view the web interface in a new tab, click the **http://127.0.0.1:8000** link in the Terminal output, which will link you via proxy to this app running locally on your Cloud Shell instance.

9. A new browser tab will open with the ADK Dev UI.

10. From the **Select an agent** dropdown on the left, select **my_google_search_agent**.

11. In order to encourage the agent to use its Google Search tool, enter the question:

    ```
    What is some recent global news?
    ```

12. You will notice from the results that the agent is able to use Google Search to get up-to-date information, rather than having its information stop on the date when its model was trained.

    > A response using grounding with Google search includes ready-to-display HTML "Search Suggestions" like those you see at the bottom of the agent's response. When you use grounding with Google Search, you are required to display these suggestions, which help users follow up on the information the model used for its response.

13. Notice that in the left side bar, you are in the **Trace** tab by default. Click on your last query text (`What is some recent global news?`) to see a trace of how long different parts of your query took to execute. You can use this to debug more complex executions involving tool calls to understand how various processes contribute to the latency of your responses.

    ```
    What is some recent global news?

    Invocation ID:
    e-fc714684-1a71-4f1f-b969-ea8690f89ff9

    |→ invocation                        4963.50ms
       🏃 agent_run [google_sear...      4962.82ms
          💬 call_llm                     4847.93ms
    ```

14. Click the agent icon next to the agent's response (or an event from the list on the **Events** tab) to inspect the event returned by the agent, which includes the `content` returned to the user and `groundingMetadata` which details the search results that the response was based on.

15. When you are finished exploring the dev UI, close this browser tab and return to your browser tab with the Cloud Shell Terminal, click on the terminal's pane, and press `CTRL + C` to stop the web server.

## Task 4. Run an agent programmatically

While the dev UI is great for testing and debugging, it is not suitable for presenting your agent to multiple users in production.

To run an agent as part of a larger application, you will need to include a few additional components in your **agent.py** script that the web app handled for you in the previous task. Proceed with the following steps to open a script with these components to review them.

1. You can set environment variables for all of your agents to use if they do not have .env files in their directories. In the Cloud Shell Terminal run the following commands to export environment variables:

   ```bash
   export GOOGLE_GENAI_USE_VERTEXAI=TRUE
   export GOOGLE_CLOUD_PROJECT=YOUR_GCP_PROJECT_ID
   export GOOGLE_CLOUD_LOCATION=global
   export MODEL=gemini_flash_model_id
   ```

2. In the Cloud Shell Editor file browser, select the **adk_project/app_agent** directory.

3. Select the **agent.py** file in this directory.

4. This agent is designed to run as part of an application. Read the commented code in **agent.py**, paying particular attention to the following components in the code:

   | Component | Feature | Description |
   |-----------|---------|-------------|
   | `InMemoryRunner()` | Oversight of agent execution | The Runner is the code responsible for receiving the user's query, passing it to the appropriate agent, receiving the agent's response event and passing it back to the calling application or UI, and then triggering the following event. You can read more in the [ADK documentation about the event loop](https://google.github.io/adk-docs/runtime/event-loop/). |
   | `runner.session_service.create_session()` | Conversation history & shared state | Sessions allow an agent to preserve state, remembering a list of items, the current status of a task, or other 'current' information. This class creates a local session service for simplicity, but in production this could be handled by a database. |
   | `types.Content()` and `types.Part()` | Structured, multimodal messages | Instead of a simple string, the agent is passed a Content object which can consist of multiple Parts. This allows for complex messages, including text and multimodal content to be passed to the agent in a specific order. |

   > When you ran the agent in the dev UI, it created a session service, artifact service, and runner for you. When you write your own agents to deploy programmatically, it is recommended that you provide these components as external services rather than relying on in-memory versions.

5. Notice that the script includes a hardcoded query, which asks the agent: `"What is the capital of France?"`

6. Run the following command in the Cloud Shell Terminal to run this agent programmatically:

   ```bash
   python3 app_agent/agent.py
   ```

   **Selected Output**:

   ```
   trivia_agent: The capital of France is Paris.
   ```

7. You can also define specific input and/or output schema for an agent.

   You will now add imports for the [Pydantic schema classes](https://docs.pydantic.dev/) `BaseModel` and `Field` and use them to define a schema class consisting of just one field, with a key of "capital" and a string value intended for the name of a country's capital city. You can paste these lines into your **app_agent/agent.py** file, just after your other imports:

   ```python
   from pydantic import BaseModel, Field

   class CountryCapital(BaseModel):
       capital: str = Field(description="A country's capital.")
   ```

8. In your `root_agent`'s `Agent` definition, set the `output_schema` parameter to use the `CountryCapital` schema you defined above:

   ```python
   output_schema=CountryCapital,
   ```

9. Run the agent script again to see the response following the `output_schema`:

   ```bash
   python3 app_agent/agent.py
   ```

   **Selected Output**:

   ```
   ** User says: {'parts': [{'text': 'What is the capital of France?'}], 'role': 'user'}
   ** trivia_agent: {"capital": "Paris"}
   ```

## Task 5. Chat with an agent via the command-line interface

You can also chat with an agent in your local development environment by using the command line interface. This can be very handy for quickly debugging and testing agents as you develop them.

Like the web interface, the command line interface also handles the creation of the session service, artifact service, and runner for your agent.

To run an interactive session using the command line interface:

1. **Run** the following in Cloud Shell Terminal:

   ```bash
   adk run my_google_search_agent
   ```

   **Output**:

   ```
   Log setup complete: /tmp/agents_log/agent.20250322_010300.log
   To access latest log: tail -F /tmp/agents_log/agent.latest.log
   Running agent basic_search_agent, type exit to exit.
   user:
   ```

2. Input the following message:

   ```
   what are some new movies that have been released in the past month in India?
   ```

   **Example output (yours may be a little different):**
   ```
   [google_search_agent]: Here are some of the movies that have been released in India in the past month (January 2026 to early February 2026):
   *   **January 16, 2026**: *Bihu Attack*, *Happy Patel: Khatarnak Jasoos*.
   *   **January 23, 2026**: *Border 2*.
   *   **January 30, 2026**: *Mardaani 3*, *Mayasabha - The Hall of Illusion*.
   *   **February 5, 2026**: *Vadh 2*, *Haunted 3D: Ghosts Of The Past*.
   *   **February 13, 2026**: *Tu Yaa Main*, *O'Romeo*, *Swayambhu*,.
   *   **February 19, 2026**: *Veer Murarbaji*, *Do Deewane Seher Mein*.
   *   **February 20, 2026**: *Epic: Elvis Presley In Concert*, *Hamnet*.
   *   **February 26, 2026**: *The Kerala Story 2 Goes Beyond*.
   ```

3. When you are finished chatting with the command line interface, enter exit at the next user prompt to end the chat.

## Task 6. Preview a multi-agent example

You will learn more about building multi-agent systems in the lab *Build multi-agent systems with ADK*, but because multi-agent capabilities are core to the Agent Development Kit experience, you can explore one multi-agent system now.

This agentic system evaluates and improves the factual grounding of responses generated by LLMs. It includes:
- a `critic_agent` to serve as an automated fact-checker
- a `reviser_agent` to rewrite responses if needed to correct inaccuracies based on verified findings

To explore this agent:

1. To explore this multi-agent system's code, use the Cloud Shell Editor file explorer to navigate to the directory **adk_project/llm_auditor**.

2. Within the **llm_auditor** directory, select the **agent.py** file.

3. Here are a few things to notice about this multi-agent example:

   - Notice the import and use of the `SequentialAgent` class. This is an example of a **workflow class** which passes control of the conversation from one agent to the next in order without awaiting a user turn in-between. When you run the agent, you will see responses from both the `critic_agent` and the `reviser_agent`, in that order, without waiting for a user turn.

   - Notice that these sub-agents are each imported from their own directories within a `sub_agents` directory.

   - In the sub-agents' directories, you will see the `__init__.py` and `agent.py` files like those you explored in the directory structure earlier, along with a `prompt.py` file, which provides a dedicated place for a complete, well-structured prompt to be stored and edited before it is imported into the `agent.py` file.

4. Create a .env file for this agent and launch the dev UI again by running the following in the Cloud Shell Terminal:

   ```
   cd ~/adk_project
   cat << EOF > llm_auditor/.env
   GOOGLE_GENAI_USE_VERTEXAI=TRUE
   GOOGLE_CLOUD_PROJECT=YOUR_GCP_PROJECT_ID
   GOOGLE_CLOUD_LOCATION=global
   MODEL=gemini_flash_model_id
   EOF

   adk web
   ```

   > **Note:** If you did not shut down your previous adk web session, the default port of 8000 will be blocked, but you can launch the Dev UI with a new port by using adk web --port 8001, for example.

5. Click the **http://127.0.0.1:8000** link in the Terminal output. A new browser tab will open with the ADK Dev UI.

6. From the **Select an agent** dropdown on the left, select **llm_auditor**.

7. Start the conversation with the following false statement:

   ```
   Double check this: Earth is further away from the Sun than Mars.
   ```

8. You should see two responses from the agent in the chat area:

   - First, a detailed response from the `critic_agent` checking the truthfulness of the statement based on fact-checking with Google Search.

   - Second, a short revised statement from the `reviser_agent` with a corrected version of your false input statement, for example, "Earth is closer to the Sun than Mars."

9. Next to each response, click on the agent icon to open the event panel for that response (or find the corresponding numbered event on the Events panel and select it). At the top of the event view, there is a graph that visualizes the relationships between the agents and tools in this multi-agent system. The agent responsible for this response will be highlighted.

10. Feel free to explore the code further or ask for other fact-checking examples in the dev UI. Another example you can try is:

    ```
    Q: Why is the sky blue? A: Because the sky reflects the color of the ocean.
    ```

11. If you would like to reset the conversation, use the **+ New Session** link at the top right of the ADK Dev UI to restart the conversation.

12. When you are finished asking questions of this agent, close the browser tab and press **CTRL + C** in the Terminal to stop the server.

> **Human-in-the-loop pattern** Even though this example uses a `SequentialAgent` workflow agent, you can think of this pattern as a human-in-the-loop pattern. When the `SequentialAgent` ends its sequence, the conversation goes back to its parent, the `llm_auditor` in this example, to get a new input turn from the user and then pass the conversation back around to the other agents.

## Congratulations!

In this lab, you've learned:

- The key capabilities of Agent Development Kit
- The core concepts of ADK
- How to structure project directories for ADK
- The most fundamental parameters of agents in ADK, including how to specify model names and tools
- Some features of ADK's browser UI
- How to control the output schema of an agent
- How to run agents in three ways (via the browser UI, programmatically, and via the CLI chat interface)

## Next Steps

To learn more about building and deploying agents using Agent Development Kit, check out these labs:

- Empower ADK agents with tools
- Build multi-agent systems with ADK
- Deploy ADK agents to Agent Engine

Find more information about ADK in the documentation and GitHub repository:

- [Agent Development Kit Documentation](https://google.github.io/adk-docs/)
- [`adk-docs` GitHub repository](https://github.com/google/adk-docs)