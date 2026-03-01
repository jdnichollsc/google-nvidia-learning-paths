# Page 5 - Task 3: Deploying to Cloud Run as A2A Server

A comic page with 4 panels in tech style (dark backgrounds, circuit patterns, neon accents).

## Panel 1 (Top, wide)
**Scene**: A dramatic deployment sequence. Dev types the `adk deploy cloud_run --a2a` command. A rocket launches from the terminal carrying the illustration_agent code. It flies toward a Cloud Run server rack in the sky. Cloud-Runner (muscular robot) catches it and places it into position.
**Narration Box**: "Deploying as an A2A Server"
**Terminal Text**: "$ adk deploy cloud_run --project ... --a2a illustration_agent"
**Speech Bubble (Dev)**: "One command deploys our agent to the cloud as an A2A server!"
**Style**: Rocket launch metaphor, terminal to cloud, dramatic deployment

## Panel 2 (Middle-left)
**Scene**: The --a2a flag shown as a special wrapper being applied around the agent. The A2aAgentExecutor is visualized as a translator robot standing between two worlds: on one side "ADK Events" (green), on the other side "A2A Tasks & Messages" (purple). It converts between them.
**Narration Box**: "The --a2a Flag"
**Speech Bubble (ADK-Bot)**: "The --a2a flag wraps your agent with A2aAgentExecutor — it translates between ADK and A2A!"
**Style**: Wrapper/translator visualization, two-sided color coding

## Panel 3 (Middle-right)
**Scene**: The deployment output in the terminal showing success. The Service URL appears in glowing green text. An arrow from the URL points to the Agent Card being automatically hosted at the /.well-known/agent.json endpoint.
**Terminal Text**: "Service URL: https://illustration-agent-...run.app"
**Terminal Text**: "Agent Card: .../a2a/illustration_agent/.well-known/agent.json"
**Speech Bubble (Dev)**: "The Agent Card is automatically hosted alongside the agent!"
**Style**: Terminal success output, green URL, auto-hosted badge

## Panel 4 (Bottom, wide)
**Scene**: The deployed agent now lives in Cloud Run. Cloud-Runner holds it up proudly. The agent is wrapped in the A2aAgentExecutor layer (shown as a purple shell). An antenna on top broadcasts the Agent Card to nearby agents who pick up the signal. The "5-10 minutes" deployment time is shown as a clock.
**Speech Bubble (ADK-Bot)**: "Your agent is live! It's wrapped in A2A, discoverable, and ready for remote calls."
**Speech Bubble (Cloud-Runner)**: "I'll keep it running 24/7!"
**Style**: Cloud deployment, wrapped agent, broadcasting antenna, clock
