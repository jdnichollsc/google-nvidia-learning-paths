# Connect to Remote Agents with ADK and the Agent2Agent (A2A) SDK

## Overview

The [Agent2Agent (A2A) protocol](https://a2a-protocol.org/) addresses a critical challenge in the AI landscape: enabling Gen AI agents, built on diverse frameworks by different companies running on separate servers, to communicate and collaborate effectively - as agents, not just as tools. A2A aims to provide a common language for agents, fostering a more interconnected, powerful, and innovative AI ecosystem.

A2A is built around a few core concepts that make it powerful and flexible:

- **Standardized Communication:** JSON-RPC 2.0 over HTTP(S).
- **Agent Discovery:** Agent Cards detail an agent's capabilities and connection info, so agents can discover each other and learn about each other's capabilities.
- **Rich Data Exchange:** Handles text, files, and structured JSON data.
- **Flexible Interaction:** Supports synchronous request/response, streaming (SSE), and asynchronous push notifications.
- **Enterprise-Ready:** Designed with security, authentication, and observability in mind.

## Objectives

In this lab, you will:

- Deploy an ADK agent as an A2A Server.
- Prepare a JSON Agent Card to describe an A2A agent's capabilities.
- Enable another ADK agent to read the Agent Card of your deployed A2A agent and use it as a sub-agent.

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

### How to start your lab and sign in to the Google Cloud console

1. Click the **Start Lab** button. If you need to pay for the lab, a dialog opens for you to select your payment method. On the left is the Lab Details pane with the following:

   - The Open Google Cloud console button
   - Time remaining
   - The temporary credentials that you must use for this lab
   - Other information, if needed, to step through this lab

2. Click **Open Google Cloud console** (or right-click and select **Open Link in Incognito Window** if you are running the Chrome browser).

   The lab spins up resources, and then opens another tab that shows the Sign in page.

   *Tip:* Arrange the tabs in separate windows, side-by-side.

   > **Note:** If you see the **Choose an account** dialog, click **Use Another Account**.

3. If necessary, copy the **Username** below and paste it into the **Sign in** dialog.

   ```
   "Username"
   ```

   You can also find the Username in the Lab Details pane.

4. Click **Next**.

5. Copy the **Password** below and paste it into the **Welcome** dialog.

   ```
   "Password"
   ```

   You can also find the Password in the Lab Details pane.

6. Click **Next**.

   > **Important:** You must use the credentials the lab provides you. Do not use your Google Cloud account credentials.

   > **Note:** Using your own Google Cloud account for this lab may incur extra charges.

7. Click through the subsequent pages:

   - Accept the terms and conditions.
   - Do not add recovery options or two-factor authentication (because this is a temporary account).
   - Do not sign up for free trials.

After a few moments, the Google Cloud console opens in this tab.

> **Note:** To access Google Cloud products and services, click the Navigation menu or type the service or product name in the Search field.

## Task 1. Install ADK and set up your environment

In this lab environment, the **Vertex AI API** and **Cloud Run API** have been enabled for you. If you were to follow these steps in your own project, you would enable them by navigating to Vertex AI and following the prompt to enable it.

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

1. Download code for this lab and install ADK and other requirements by running the following in the Cloud Shell Terminal:

   ```bash
   gcloud storage cp -r gs://YOUR_GCP_PROJECT_ID-bucket/adk_and_a2a .
   export PATH=$PATH:"/home/${USER}/.local/bin"
   python3 -m pip install --upgrade google-adk a2a-sdk google-genai
   ```

Click **Check my progress** to verify the objective. *Install ADK and set up your environment.*

## Task 2. Explore the ADK agent you will make available remotely

For the purposes of this lab, imagine you work for a stadium maintenance company: **Cymbal Stadiums**. As part of a recent project, you developed an image generation-agent that can create illustrations according to your brand guidelines. Now, several different teams in your organization want to use it too.

If you were to copy the code for use as a sub-agent by many agents, it would be very difficult to maintain and improve all of these copies.

Instead, you can deploy the agent once as an agent wrapped with an A2A server, and the other teams' agents can incorporate it by querying it remotely.

1. In the Cloud Shell Editor's file explorer pane, navigate to the **adk_and_a2a/illustration_agent** directory. This directory contains the ADK agent you will make available remotely. Click the directory to toggle it open.

2. Open the **agent.py** file on this directory and scroll to the section labeled `# Tools`.

3. Notice the `generate_image()` function, which will be used as a tool by this agent. It receives a prompt and performs a two-step process. First, it uses the **Google Gen AI SDK** to call `generate_content()`, which returns the raw image data directly in the response. Second, the function uses the **Cloud Storage library** to upload these image bytes to a GCS bucket. Finally, the tool returns a URL for the newly created image file.

4. Notice that the `instruction` provided to the `root_agent` provides specific instructions to the agent to use image-generation prompts that respect the company's brand guidelines. For example, it specifies:

   - a specific illustration style: ([Corporate Memphis](https://en.wikipedia.org/wiki/Corporate_Memphis))
   - a color palette (purples and greens on sunset gradients)
   - examples of stadium/sports and maintenance imagery because it is a stadium maintenance company

5. To see it in action, you'll first need to write a **.env** file to set environment variables needed by ADK agents. Run the following in the Cloud Shell Terminal to write this file in this directory.

   ```bash
   cd ~/adk_and_a2a
   cat << EOF > illustration_agent/.env
   GOOGLE_GENAI_USE_VERTEXAI=TRUE
   GOOGLE_CLOUD_PROJECT=YOUR_GCP_PROJECT_ID
   GOOGLE_CLOUD_LOCATION=global
   MODEL=gemini_flash_model_id
   IMAGE_MODEL=gemini_flash_image_model_id
   EOF
   ```

6. Run the following to copy the `.env` to another agent directory you'll use in this lab:

   ```bash
   cp illustration_agent/.env slide_content_agent/.env
   ```

7. Now from the Cloud Shell Terminal, launch the ADK dev UI with:

   ```bash
   adk web
   ```

   **Output:**

   ```
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

8. To view the web interface in a new tab, click the **http://127.0.0.1:8000** link at the bottom of the Terminal output.

9. A new browser tab will open with the ADK Dev UI.

10. From the **Select an agent** dropdown on the left, select the **illustration_agent** from the dropdown.

11. Query the agent with some text that could be used in a recruitment slide deck:

   ```
   By supporting each other, we get big things done!
   ```

12. After about 10 seconds, the agent should respond with the prompt it generated and a URL to preview the image. **Click the image URL** to preview the image, then click **Back** in your browser to return to the Dev UI.

    > **Note:** If you get a **Forbidden Error 403**, you may have multiple accounts signed into your Incognito session. Try incrementing the value of the `authuser` value at the end of the URL, for example changing it from `authuser=0` to `authuser=1`, `authuser=2`, etc. In production you could handle this with a service account creating a Signed URL.

13. Notice that the prompt you provided to the agent didn't mention sports, stadiums, or maintenance work, but the agent took your text and the brand guidelines and combined them into a single prompt for the image generation model.

    When you are finished exploring the base agent, close the browser tab.

14. Click on the Cloud Shell Terminal pane and press **CTRL + C** to stop the server.

Click **Check my progress** to verify the objective. *Explore the ADK agent.*

## Task 3. Deploy the agent as an A2A Server

You'll now take the steps to deploy this agent as a remote A2A agent.

1. An A2A Agent identifies itself and its capabilities by serving an [Agent Card](https://a2a-protocol.org/latest/topics/agent-discovery/#the-role-of-the-agent-card). Run the following to create an **agent.json** file.

   ```bash
   touch illustration_agent/agent.json
   ```

2. Open the `agent.json` file within the `adk_and_a2a/illustration_agent` directory and paste in the following contents:

   ```json
   {
       "name": "illustration_agent",
       "description": "An agent designed to generate branded illustrations for Cymbal Stadiums.",
       "defaultInputModes": ["text/plain"],
       "defaultOutputModes": ["application/json"],
       "skills": [
       {
           "id": "illustrate_text",
           "name": "Illustrate Text",
           "description": "Generate an illustration to illustrate the meaning of provided text.",
           "tags": ["illustration", "image generation"]
       }
       ],
       "url": "https://illustration-agent-Project Number.GCP_LOCATION.run.app/a2a/illustration_agent",
       "capabilities": {},
       "version": "1.0.0"
   }
   ```

3. **Save** the file.

4. Review the JSON in the **agent.json** file. Notice that it gives the agent a `name` and `description` and identifies some `skills`. It also indicates a `url` where the agent itself can be called.

   The agent's `url` is constructed to be its Cloud Run service URL once you have deployed it following the instructions in this lab.

   While similar in name to `skills`, the parameter `capabilities` here is reserved to indicate abilities like streaming.

5. Run the following to create a `requirements.txt` file in the `illustration_agent` directory.

   ```bash
   touch illustration_agent/requirements.txt
   ```

6. Open the `requirements.txt` file, and paste the following into the file.

   ```
   google-adk
   a2a-sdk
   ```

7. **Save** the file.

8. In the following command, you will use `adk deploy cloud_run` with the `--a2a` flag to deploy your agent to Cloud Run as an A2A server. You can learn more about deploying agents to Cloud Run by searching for the lab "Deploy ADK agents to Cloud Run". In this command:

   - the `--project` and `--region` define the project and region in which your Cloud Run service will be deployed
   - the `--service_name` defines the name for the Cloud Run service
   - the `--a2a` flag indicates it should be hosted as an A2A agent. This means two things:
     - your agent will be wrapped by a class which bridges ADK and A2A agents: the [A2aAgentExecutor](https://github.com/google/adk-python/blob/main/src/google/adk/a2a/executor/a2a_agent_executor.py). This class translates A2A Protocol's language of [tasks and messages](https://a2a-protocol.org/latest/topics/key-concepts/#fundamental-communication-elements) to an ADK Runner in its language of [events](https://google.github.io/adk-docs/events/).
     - the Agent Card will be hosted as well at `CLOUD_RUN_URL/a2a/AGENT_NAME/.well-known/agent.json`. **Note:** While this version of the card will be usable soon, the dynamic rewriting of the agent's url currently does not work with Cloud Run, so we won't use it in this version of this lab.

9. Deploy the agent to Cloud Run as an A2A server with the following command:

   ```bash
   adk deploy cloud_run \
       --project YOUR_GCP_PROJECT_ID \
       --region GCP_LOCATION \
       --service_name illustration-agent \
       --a2a \
       illustration_agent
   ```

10. You will be prompted to allow unauthenticated responses for this container. For the sake of lab testing, enter `Y` into the Cloud Shell Terminal (for "yes") and **press return**.

    > **Note:** Deployment should take about 5-10 minutes. If you encounter a `PERMISSION_DENIED` error, try running the above command again.

    **Expected output:**

    You will see steps relating to building a Dockerfile and deploying the container, then deploying the service, followed by:

    ```
    Service [illustration-agent] revision [illustration-agent-00001-xpp] has been deployed and is serving 100 percent of traffic.
    Service URL: https://illustration-agent-Project Number.GCP_LOCATION.run.app
    ```

Click **Check my progress** to verify the objective. *Deploy the Agent as an A2A Server.*

## Task 4. Enable another ADK agent to call this agent remotely

In this task, you will provide a second ADK agent the ability to identify your illustration agent's capabilities and call it remotely. This second agent will be an agent tasked with creating contents for slides. It will write a headline and a couple of sentences of body text, then transfer to the illustration agent to generate an image to illustrate that text.

1. In the Cloud Shell Terminal, **run the following command** to copy the Agent Card JSON file to your `adk_and_a2a` directory and change its name to indicate that it represents the `illustration_agent`.

   ```bash
   cp illustration_agent/agent.json illustration-agent-card.json
   ```

2. In the Cloud Shell Editor's file explorer pane, navigate to the `adk_and_a2a/slide_content_agent` and open the `agent.py` file.

3. Review this agent's `instruction` to see that it will take a user's suggestion for a slide, use that to write a headline & body text, and then request that your A2A agent provides an illustration for the slide.

4. **Paste the following code** under the `# Agents` header to add the remote agent using the [`RemoteA2aAgent`](https://github.com/google/adk-python/blob/main/src/google/adk/agents/remote_a2a_agent.py) class from ADK:

   ```python
   illustration_agent = RemoteA2aAgent(
       name="illustration_agent",
       description="Agent that generates illustrations.",
       agent_card=(
           "illustration-agent-card.json"
       ),
   )
   ```

5. Add the **illustration_agent** as a sub-agent of the **root_agent** by adding the following parameter to the `root_agent`:

   ```python
   sub_agents=[illustration_agent]
   ```

6. **Save** the file.

7. Launch the UI from the Cloud Shell Terminal with:

   ```bash
   cd ~/adk_and_a2a
   adk web
   ```

8. Once again, click the **http://127.0.0.1:8000** link in the Terminal output. A new browser tab will open with the ADK Dev UI.

9. From the **Select an agent** dropdown on the left, select the **slide_content_agent** from the dropdown.

10. Query the agent with an idea for a slide:

    ```
    Create content for a slide about our excellent on-the-job training.
    ```

11. You should see the following output:

    - A headline and body text written by the **slide_content_agent** itself
    - A call to **transfer_to_agent**, indicating a transfer to the **illustration_agent**
    - The response from the **illustration_agent** with a link you can click on to see the new image.

    > **Note:** As before, if you get a Forbidden Error 403, you may have multiple accounts signed into your Incognito session. Try incrementing the value of the `authuser` value at the end of the URL, for example changing it from `authuser=0` to `authuser=1`, `authuser=2`, etc. In production you could handle this with a service account creating a Signed URL.

Click **Check my progress** to verify the objective. *Enable another ADK agent to call the agent remotely.*

## Congratulations!

In this lab, you've deployed an ADK agent as an A2A Server, prepared a JSON Agent Card to describe an A2A agent's capabilities, and enabled another ADK agent to read the Agent Card of your deployed A2A agent and use it as a sub-agent.
