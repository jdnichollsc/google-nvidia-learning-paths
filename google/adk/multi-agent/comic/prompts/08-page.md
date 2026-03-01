# Page 8 - Task 6: ParallelAgent — Fan Out and Gather

A comic page with 4 panels in tech style (dark backgrounds, circuit patterns, neon accents).

## Panel 1 (Top, wide)
**Scene**: A dramatic "fan out" visualization. The output from the LoopAgent splits into two beams of light going to two agents working simultaneously: Box-Office-Bot (wearing a business suit with charts) analyzes market data on the left, and Casting-Bot (wearing a director's beret with headshot photos) suggests actors on the right. A merge point below gathers their results.
**Narration Box**: "Task 6: ParallelAgent — Fan Out & Gather"
**Speech Bubble (ADK-Bot)**: "ParallelAgent runs sub-agents concurrently — two tasks at once, half the time!"
**Style**: Fan-out beam split, two parallel lanes, merge point below

## Panel 2 (Middle-left)
**Scene**: Box-Office-Bot analyzing holographic charts and graphs. Historical box office data for similar biographical films floats around it. The output_key="box_office_report" is labeled on the output document.
**Speech Bubble (Box-Office-Bot)**: "Based on similar biographical films, projected opening weekend: $42M!"
**Code Display**: 'output_key="box_office_report"'
**Style**: Business charts, financial data, analytical scene

## Panel 3 (Middle-right)
**Scene**: Casting-Bot surrounded by holographic headshot photos of actors. It matches actors to character roles based on similar past performances. The output_key="casting_report" is labeled on the output.
**Speech Bubble (Casting-Bot)**: "For the lead role, actors who excelled in similar period pieces..."
**Code Display**: 'output_key="casting_report"'
**Style**: Headshot photos, matching arrows to character cards, creative scene

## Panel 4 (Bottom, wide)
**Scene**: The complete final architecture now assembled. The file_writer receives three inputs from state: PLOT_OUTLINE (from writers_room), box_office_report (from ParallelAgent), and casting_report (from ParallelAgent). It combines them into one final document with all three sections. Dev holds up the finished movie pitch proudly.
**Code Display**: 'preproduction_team = ParallelAgent(sub_agents=[box_office_researcher, casting_agent])'
**Speech Bubble (Dev)**: "The complete system — research, write, critique, analyze, cast, all automated!"
**Style**: Architecture diagram with all components assembled, final document output
