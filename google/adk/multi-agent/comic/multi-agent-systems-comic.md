# Build Multi-Agent Systems with ADK - Comic

## Overview
- **Lab**: Build Multi-Agent Systems with ADK
- **Art Style**: Tech
- **Pages**: 4 (Cover + 3 pages)
- **Generated on**: 2026-03-01

## Comic Pages

### Cover
![Cover](00-cover.png)

### Page 1 - Agent Hierarchies & Transfers
![Page 1](01-page.png)

**Content**: Why multi-agent systems beat single agents for complex tasks. The hierarchical agent tree structure with root_agent, sub-agents, and peer transfers. Session state management with key templating `{ attractions? }`.

### Page 2 - SequentialAgent: The Assembly Line
![Page 2](02-page.png)

**Content**: Building a movie pitch system with SequentialAgent. The researcher uses Wikipedia tools, the screenwriter creates plot outlines with `output_key`, and the file_writer saves the final document — all running automatically in sequence.

### Page 3 - LoopAgent & ParallelAgent
![Page 3](03-page.png)

**Content**: LoopAgent iterates through researcher -> screenwriter -> critic until the critic calls `exit_loop`. ParallelAgent runs box_office_researcher and casting_agent concurrently. The complete system architecture combines all three workflow types.

## Core Knowledge Points
1. **Hierarchical Agent Tree** - Organize agents in parent/sub-agent relationships for controlled information flow
2. **Agent Transfers** - Parent agents route to sub-agents based on descriptions; peer transfers allowed by default
3. **Session State** - Shared dictionary accessible to all agents via `ToolContext`; key templating loads values
4. **SequentialAgent** - Executes sub-agents linearly; output of one feeds the next
5. **LoopAgent** - Iterative refinement with `max_iterations` and `exit_loop` tool
6. **ParallelAgent** - Concurrent execution for independent tasks; "fan out and gather" pattern

## Characters
- **ADK-Bot** - Friendly robot mentor with Google colors
- **Dev** - Young developer learning multi-agent orchestration
- **The Crew** - Researcher-Bot, Writer-Bot, and Critic-Bot representing workflow sub-agents
