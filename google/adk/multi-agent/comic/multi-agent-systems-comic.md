# Build Multi-Agent Systems with ADK - Comic

## Overview
- **Lab**: Build Multi-Agent Systems with ADK
- **Art Style**: Tech
- **Pages**: 10 (Cover + 9 pages)
- **Generated on**: 2026-03-01

## Comic Pages

### Cover
![Cover](00-cover.png)

### Page 1 - Why Multi-Agent Systems?
![Page 1](01-page.png)

**Content**: The problem with single-agent approaches, benefits of multi-agent systems (easier design, specialization, organization, maintainability, modularity), and lab objectives.

### Page 2 - The Hierarchical Agent Tree
![Page 2](02-page.png)

**Content**: Tree structure starting with root_agent, parent-to-sub-agent relationships via `sub_agents=[]`, benefits (real-world teams, intuitive, control), and the travel agent tree example.

### Page 3 - Agent Transfers in Action
![Page 3](03-page.png)

**Content**: Description-based transfers, explicit transfer instructions mentioning sub-agents by name, peer transfers between siblings, and `disallow_transfer_to_peers` control.

### Page 4 - Session State: Sharing Memory
![Page 4](04-page.png)

**Content**: Session state dictionary accessible by all agents, ToolContext for reading/writing state, key templating `{ attractions? }`, and viewing state in the Dev UI.

### Page 5 - Workflow Agents Introduction
![Page 5](05-page.png)

**Content**: Three workflow types (Sequential, Loop, Parallel), use cases (Plan & Execute, Research & Write, Draft & Revise), movie pitch system concept, and complete architecture overview.

### Page 6 - SequentialAgent: The Assembly Line
![Page 6](06-page.png)

**Content**: Linear pipeline execution (researcher → screenwriter → file_writer), Wikipedia tool usage, output_key for state saving, and automatic progression without user input.

### Page 7 - LoopAgent: Iterative Refinement
![Page 7](07-page.png)

**Content**: Circular workflow (researcher → screenwriter → critic), Critic-Bot's exit_loop tool, critical feedback via append_to_state, and max_iterations safety cap.

### Page 8 - ParallelAgent: Fan Out and Gather
![Page 8](08-page.png)

**Content**: Concurrent execution (box_office_researcher + casting_agent), output_key for each parallel agent, fan-out and gather pattern, and complete system assembly.

### Page 9 - Advanced Concepts & Callbacks
![Page 9](09-page.png)

**Content**: output_key automatic state saving, before/after model callbacks for monitoring, CustomAgent for custom workflows, and triumphant completion of the full system.

## Core Knowledge Points
1. **Multi-Agent Benefits** - Easier design, specialization, organization, maintainability, modularity
2. **Hierarchical Agent Tree** - root_agent → sub_agents, tree-like delegation
3. **Agent Transfers** - Description-based, instruction-guided, peer transfers
4. **Session State** - Shared dictionary via ToolContext, key templating
5. **SequentialAgent** - Linear pipeline, automatic progression
6. **LoopAgent** - Iterative refinement with exit_loop and max_iterations
7. **ParallelAgent** - Concurrent execution, fan-out and gather pattern
8. **output_key** - Automatic response saving to state
9. **Callbacks** - before_model_callback, after_model_callback for monitoring
10. **CustomAgent** - Build your own workflow logic
