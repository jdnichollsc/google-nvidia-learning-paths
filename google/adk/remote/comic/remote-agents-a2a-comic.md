# Connect to Remote Agents with ADK and A2A - Comic

## Overview
- **Lab**: Connect to Remote Agents with ADK and the Agent2Agent (A2A) SDK
- **Art Style**: Tech
- **Pages**: 3 (Cover + 2 pages)
- **Generated on**: 2026-03-01

## Comic Pages

### Cover
![Cover](00-cover.png)

### Page 1 - The A2A Vision & The Illustration Agent
![Page 1](01-page.png)

**Content**: The problem of isolated AI frameworks and how A2A solves it with standardized communication. The five A2A pillars: JSON-RPC 2.0, Agent Discovery, Rich Data Exchange, Flexible Interaction, and Enterprise-Ready. Exploring the illustration_agent that generates Corporate Memphis-style images using Gemini and Cloud Storage.

### Page 2 - Deploy as A2A Server & Remote Connection
![Page 2](02-page.png)

**Content**: Creating an Agent Card (agent.json) to describe capabilities. Deploying to Cloud Run with `adk deploy cloud_run --a2a` which wraps the agent with A2aAgentExecutor. Using `RemoteA2aAgent` to connect a slide_content_agent to the remote illustration_agent as a sub-agent.

## Core Knowledge Points
1. **A2A Protocol** - Standardized communication (JSON-RPC 2.0 over HTTPS) enabling cross-framework agent collaboration
2. **Agent Cards** - JSON identity documents describing agent name, skills, URL, and capabilities
3. **A2A Deployment** - `adk deploy cloud_run --a2a` wraps agents with A2aAgentExecutor bridging ADK events to A2A tasks/messages
4. **RemoteA2aAgent** - ADK class that reads Agent Cards and treats remote agents as local sub-agents
5. **Deploy Once, Use Anywhere** - One team maintains the agent; multiple teams use it remotely without code duplication

## Characters
- **ADK-Bot** - Friendly robot mentor with Google colors
- **Dev** - Young developer learning remote agent orchestration
- **Art-Agent** - Easel-shaped robot representing the deployed illustration_agent
- **Card-Sprite** - Holographic JSON card representing the Agent Card identity
