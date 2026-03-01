# Page 3 - Agent Transfers in Action

A comic page with 4 panels in tech style (dark backgrounds, circuit patterns, neon accents).

## Panel 1 (Top-left)
**Scene**: CLI terminal showing a conversation. User says "hello", steering agent greets and asks if they have a destination. User says "I could use some help deciding." The response shows [travel_brainstormer] has taken over. A glowing transfer arrow arcs from steering to travel_brainstormer.
**Narration Box**: "Task 2: Transfers Based on Description"
**Terminal Text**: "[steering]: Do you have a country in mind?"
**Terminal Text**: "[user]: I could use some help deciding."
**Terminal Text**: "[travel_brainstormer]: I can help!"
**Style**: Terminal with transfer arrow overlay, green text

## Panel 2 (Top-right)
**Scene**: ADK-Bot shows how to add explicit transfer instructions to the root_agent's instruction string. The instruction text floats as holographic text: "If they need help deciding, send them to 'travel_brainstormer'." Arrows connect the instruction text to the agent names.
**Speech Bubble (ADK-Bot)**: "You can also guide transfers explicitly in the instructions — mention sub-agents by name!"
**Style**: Floating instruction text, connection arrows to agents

## Panel 3 (Bottom-left)
**Scene**: User says "I would like to go to Japan" and is transferred to attractions_planner, which lists attractions (Tokyo, Kyoto, etc.). Then user says "Actually I don't know" and gets transferred to travel_brainstormer. A bi-directional arrow between the two agents shows peer transfer.
**Narration Box**: "Peer Transfers"
**Speech Bubble (Dev)**: "Agents can transfer to siblings too — not just back to the parent!"
**Style**: Two agents with bi-directional transfer arrow, conversation flow

## Panel 4 (Bottom-right)
**Scene**: ADK-Bot shows a toggle switch labeled "disallow_transfer_to_peers". When ON (red), the arrow between peer agents is blocked with an X. When OFF (green, default), transfers flow freely between peers.
**Code Display**: "disallow_transfer_to_peers=True"
**Speech Bubble (ADK-Bot)**: "Need more control? Block peer transfers with a single parameter!"
**Style**: Toggle switch metaphor, blocked vs. open transfer arrows
