# Page 7 - Task 5: LoopAgent — Iterative Refinement

A comic page with 4 panels in tech style (dark backgrounds, circuit patterns, neon accents).

## Panel 1 (Top, wide)
**Scene**: A circular track with three agents running in a loop: Researcher-Bot researches, Writer-Bot writes a draft, Critic-Bot reviews and decides whether to loop again or exit. Glowing arrows connect them in a circle. The loop iteration counter shows "Iteration 2/5". Critic-Bot holds its hand near the red EXIT button on its chest.
**Narration Box**: "Task 5: LoopAgent — Refine Until Perfect"
**Speech Bubble (ADK-Bot)**: "LoopAgent repeats the sequence until the Critic says it's good enough!"
**Style**: Circular track, three agents in motion, iteration counter, loop arrows

## Panel 2 (Middle-left)
**Scene**: Critic-Bot examines the current draft with its monocle. A holographic checklist floats beside it: "Three-act structure? ✓", "Engaging characters? ✗", "Historical accuracy? ✓", "Incorporates research? ✗". Two items failing means it writes CRITICAL_FEEDBACK to state using append_to_state tool.
**Speech Bubble (Critic-Bot)**: "Not quite there — characters need more depth. Another round!"
**Code Display**: 'tools=[append_to_state, exit_loop]'
**Style**: Inspection scene, holographic checklist with check/X marks

## Panel 3 (Middle-right)
**Scene**: Critic-Bot decides the draft is ready and dramatically presses the red EXIT button on its chest. The loop breaks open like a portal. The improved document glows brightly as it escapes the loop and floats toward the next stage.
**Speech Bubble (Critic-Bot)**: "This draft is excellent — EXIT THE LOOP!"
**Code Display**: "exit_loop()"
**Style**: Loop breaking open, dramatic exit effect, glowing document escaping

## Panel 4 (Bottom, wide)
**Scene**: The code for the LoopAgent definition is shown alongside the visual loop. Key parameters highlighted: sub_agents=[researcher, screenwriter, critic] and max_iterations=5 (shown as a safety cap/ceiling above the loop). The updated SequentialAgent now starts with writers_room (LoopAgent) then goes to file_writer.
**Code Display**: 'writers_room = LoopAgent(name="writers_room", sub_agents=[researcher, screenwriter, critic], max_iterations=5)'
**Speech Bubble (Dev)**: "max_iterations is a safety net — even if the critic never exits, it stops after 5 rounds!"
**Style**: Code + loop diagram, safety cap visualization, updated architecture
