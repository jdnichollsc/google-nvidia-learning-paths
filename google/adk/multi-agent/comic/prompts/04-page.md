# Page 4 - Session State: Sharing Memory Between Agents

A comic page with 4 panels in tech style (dark backgrounds, circuit patterns, neon accents).

## Panel 1 (Top, wide)
**Scene**: ADK-Bot reveals a glowing shared memory vault at the center — the Session State dictionary. Multiple agents surround it, each able to read and write. The vault shows key-value pairs floating inside: {"attractions": ["Sphinx", "Pyramids"]}. Arrows flow in and out from different agents.
**Narration Box**: "Task 3: Session State — Shared Memory for All Agents"
**Speech Bubble (ADK-Bot)**: "Every session has a state dictionary — all agents in the conversation can access it!"
**Style**: Central glowing vault, key-value pairs floating inside, bidirectional arrows

## Panel 2 (Middle-left)
**Scene**: Close-up of the save_attractions_to_state tool function code. The key lines are highlighted: tool_context.state.get("attractions", []) to read, and tool_context.state["attractions"] = ... to write. ToolContext is shown as a special key that opens the vault.
**Code Display**: 'tool_context.state["attractions"] = existing + new'
**Speech Bubble (ADK-Bot)**: "ToolContext is the key — it gives your function access to read and write the session state!"
**Style**: Code with highlighted lines, ToolContext as a glowing key icon

## Panel 3 (Middle-right)
**Scene**: The attractions_planner agent's instruction shows the key templating syntax: `{ attractions? }` with a glowing highlight. An arrow shows this pulling the value from the state vault. The question mark is annotated: "? = don't error if missing".
**Code Display**: '{ attractions? }'
**Narration Box**: "Key Templating"
**Speech Bubble (Dev)**: "Curly braces pull values from state right into the instruction!"
**Style**: Template syntax highlighted, pull arrow from state vault, annotation

## Panel 4 (Bottom, wide)
**Scene**: Dev UI showing the State tab in the sidebar. The state dictionary is visible with attractions: ["The Sphinx", "Valley of the Kings"]. Dev says "What is on my list?" and the agent responds with a bulleted list. The state_delta from a tool event is shown in an inset.
**Speech Bubble (Dev)**: "What is on my list?"
**Agent Response**: "• The Sphinx\n• Valley of the Kings"
**Narration Box**: "View state changes in the Dev UI State tab!"
**Style**: Dev UI mockup with State tab, bulleted response, state_delta inset
