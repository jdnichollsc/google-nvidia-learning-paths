# Page 2 - Deploy as A2A Server & Remote Connection

A comic page with 4 panels in tech style (dark backgrounds, circuit patterns, neon accents).

## Panel 1 (Top-left)
**Scene**: ADK-Bot holds up a glowing Agent Card (Card-Sprite) — a holographic JSON document floating in mid-air. The card shows key fields: "name", "description", "skills", and "url" all rendered as glowing JSON text. Dev examines it like a passport, tilting it to see the holographic details.
**Narration Box**: "Task 3: The Agent Card"
**Speech Bubble (ADK-Bot)**: "Every A2A agent needs an Agent Card — its identity and capabilities in JSON!"
**Caption**: 'agent.json: { "name": "illustration_agent", "skills": [...], "url": "..." }'
**Style**: Holographic ID card, JSON text glow, passport inspection pose

## Panel 2 (Top-right)
**Scene**: Art-Agent stands on a launch platform. ADK-Bot presses a glowing button labeled "adk deploy cloud_run --a2a". A rocket-like beam shoots Art-Agent upward into the cloud (represented as a glowing Cloud Run container in the sky). The A2aAgentExecutor is shown as a glowing bridge/wrapper forming around Art-Agent during launch, translating "events" on one side to "tasks & messages" on the other.
**Narration Box**: "Deploy to Cloud Run as A2A Server"
**Speech Bubble (ADK-Bot)**: "The --a2a flag wraps your agent with A2aAgentExecutor — bridging ADK events to A2A messages!"
**Style**: Rocket launch metaphor, cloud deployment, bridge/wrapper visualization

## Panel 3 (Bottom-left)
**Scene**: Back in the lab, Dev creates a new agent — Slide-Content-Bot (a small robot with a presentation slide for a head). Dev connects it to Art-Agent's Agent Card using a RemoteA2aAgent class shown as a glowing tether extending from the lab up into the cloud where Art-Agent now lives. The code snippet shows: RemoteA2aAgent(agent_card="illustration-agent-card.json").
**Narration Box**: "Task 4: Connect Remotely"
**Speech Bubble (Dev)**: "RemoteA2aAgent reads the Agent Card and treats the remote agent as a local sub-agent!"
**Style**: Lab-to-cloud connection, tether beam, local-remote bridge

## Panel 4 (Bottom, wide)
**Scene**: The complete flow shown as a cinematic sequence from left to right. Slide-Content-Bot writes a headline ("By supporting each other, we get big things done!") which appears as floating text. An arrow labeled "transfer_to_agent" arcs through the cloud to Art-Agent. Art-Agent creates a Corporate Memphis illustration of stadium workers supporting each other. The finished slide content — headline, body text, and illustration — assembles into a beautiful presentation slide floating in the center. Dev and ADK-Bot admire the result.
**Speech Bubble (Dev)**: "One agent writes content, the other illustrates — across different servers!"
**Speech Bubble (ADK-Bot)**: "Deploy once, use from anywhere. That's the power of A2A!"
**Style**: Left-to-right cinematic flow, cloud connection, finished slide assembly, triumphant finale
