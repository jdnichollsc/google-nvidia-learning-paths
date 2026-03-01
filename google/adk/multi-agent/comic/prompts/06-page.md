# Page 6 - Task 4: SequentialAgent — The Assembly Line

A comic page with 4 panels in tech style (dark backgrounds, circuit patterns, neon accents).

## Panel 1 (Top, wide)
**Scene**: An assembly line metaphor. Three stations on a conveyor belt: Station 1 has Researcher-Bot scanning Wikipedia with its magnifying glass eyes, Station 2 has Writer-Bot crafting a screenplay with its quill pen, Station 3 has a File-Writer robot saving to disk. A document flows along the conveyor belt, getting enriched at each station.
**Narration Box**: "Task 4: SequentialAgent — Agents in a Pipeline"
**Speech Bubble (ADK-Bot)**: "SequentialAgent runs sub-agents one after another — each one builds on the previous!"
**Style**: Assembly line / conveyor belt, three stations, document flowing between them

## Panel 2 (Middle-left)
**Scene**: Close-up of Researcher-Bot at work. It uses the Wikipedia tool (shown as a holographic Wikipedia logo) to gather research on "Ada Lovelace". Data streams flow from Wikipedia into floating note cards that stack up.
**Code Display**: "tools=[wikipedia_tool]"
**Speech Bubble (Researcher-Bot)**: "Gathering facts from Wikipedia... Ada Lovelace, mathematician, first computer programmer!"
**Style**: Research scene, Wikipedia logo, flowing data streams into note cards

## Panel 3 (Middle-right)
**Scene**: Writer-Bot receives the research notes and transforms them into a plot outline. The notes dissolve into the screenplay scroll it's writing. The output_key parameter is shown as a label on the scroll: "PLOT_OUTLINE".
**Code Display**: 'output_key="PLOT_OUTLINE"'
**Speech Bubble (Writer-Bot)**: "A brilliant mathematician defies society to envision the future of computing..."
**Style**: Creative transformation, notes dissolving into screenplay, output_key label

## Panel 4 (Bottom, wide)
**Scene**: The greeter (root_agent) hands off to the SequentialAgent film_concept_team. The code shows the SequentialAgent definition with sub_agents=[researcher, screenwriter, file_writer]. The flow arrows show automatic progression without user input between steps. A movie pitch document emerges from the file_writer.
**Code Display**: 'film_concept_team = SequentialAgent(name="film_concept_team", sub_agents=[researcher, screenwriter, file_writer])'
**Speech Bubble (Dev)**: "No user input between steps — it just flows automatically!"
**Style**: Code + flow diagram hybrid, automatic progression arrows
