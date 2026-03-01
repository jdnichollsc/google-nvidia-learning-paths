# Page 9 - Advanced Concepts & Callbacks

A comic page with 4 panels in tech style (dark backgrounds, circuit patterns, neon accents).

## Panel 1 (Top-left)
**Scene**: ADK-Bot shows the output_key concept as a simple pipeline. An agent speaks, and its response text automatically flows into a state box labeled with the output_key name. Versus the manual approach of using tools to write to state. Side-by-side comparison.
**Narration Box**: "Output Key — Automatic State Saving"
**Code Display**: 'output_key="casting_report"'
**Speech Bubble (ADK-Bot)**: "output_key saves the agent's entire response to state automatically — no tools needed!"
**Style**: Simple pipeline comparison, automatic vs manual, clean arrows

## Panel 2 (Top-right)
**Scene**: Two callback hooks shown as checkpoint gates in the agent pipeline. before_model_callback is a gate BEFORE the agent's brain processes (logging the input), after_model_callback is a gate AFTER (logging the output). The gates have small monitor screens showing log data.
**Narration Box**: "Callbacks — Monitor & Control"
**Code Display**: "before_model_callback=log_query"
**Code Display**: "after_model_callback=log_response"
**Speech Bubble (ADK-Bot)**: "Callbacks let you log, monitor, or even modify requests before and after the model acts!"
**Style**: Checkpoint gates in pipeline, monitor screens showing logs

## Panel 3 (Bottom-left)
**Scene**: A mysterious silhouette of CustomAgent — shown as a robot with a question mark on its chest and a blank blueprint in its hand. Around it, gears and logic gates float, suggesting programmable behavior. A "Coming Soon" vibe.
**Narration Box**: "CustomAgent — Build Your Own Workflow"
**Speech Bubble (ADK-Bot)**: "When Sequential, Loop, and Parallel aren't enough — CustomAgent lets you define any workflow logic!"
**Style**: Mysterious silhouette, question mark, floating gears and logic gates

## Panel 4 (Bottom-right, wide)
**Scene**: Dev stands proudly in front of the complete movie pitch system architecture, now fully operational with all agents working in harmony. Documents fly between agents, the loop spins, parallel lanes process simultaneously. The final movie pitch document floats in Dev's hands, complete with title, plot, box office analysis, and casting suggestions.
**Speech Bubble (Dev)**: "From a single confused agent to a full production team — that's the power of multi-agent systems!"
**Narration Box**: "Next: Take your agents remote with A2A! →"
**Style**: Triumphant scene, full system in action, completed document
