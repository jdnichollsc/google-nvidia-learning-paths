# Page 3 - Task 2: Exploring the Illustration Agent

A comic page with 4 panels in tech style (dark backgrounds, circuit patterns, neon accents).

## Panel 1 (Top, wide)
**Scene**: Art-Agent revealed in full glory — an easel-shaped robot with paintbrush arm, wearing a purple-and-green artist smock. It stands in its studio surrounded by Corporate Memphis style illustrations: flat geometric characters, bold purple/green gradients, stadium imagery. Floating examples of its art style surround it.
**Narration Box**: "Task 2: Meet the Illustration Agent"
**Speech Bubble (ADK-Bot)**: "This agent generates branded illustrations following Cymbal Stadiums' style guide!"
**Style**: Artist studio reveal, Corporate Memphis art examples, purple/green palette

## Panel 2 (Middle-left)
**Scene**: Close-up of the generate_image() tool function as a two-step pipeline. Step 1: Google Gen AI SDK icon receives a prompt and outputs raw image bytes (shown as a stream of colorful pixels). Step 2: Cloud Storage bucket icon receives the bytes and returns a URL.
**Narration Box**: "The Two-Step Image Pipeline"
**Speech Bubble (Art-Agent)**: "Gemini generates the image, Cloud Storage hosts it!"
**Code Display**: "Step 1: generate_content() → image bytes"
**Code Display**: "Step 2: upload to GCS → image URL"
**Style**: Two-step pipeline, pixel stream, bucket icon

## Panel 3 (Middle-right)
**Scene**: The agent's instruction shown as a style guide poster on the wall. It lists: "Corporate Memphis style", "Purple & green palette", "Sunset gradients", "Stadium/sports imagery", "Maintenance themes". Small example illustrations demonstrate each rule.
**Narration Box**: "Brand Guidelines in the Instruction"
**Speech Bubble (Dev)**: "The instruction enforces the brand — even generic text gets the Cymbal treatment!"
**Style**: Style guide poster, example illustrations, brand rules

## Panel 4 (Bottom, wide)
**Scene**: Dev UI showing the illustration agent in action. Dev types "By supporting each other, we get big things done!" and the agent responds with a Corporate Memphis illustration of stadium workers helping each other, plus the image URL. The image preview shows purple/green characters in flat design.
**Speech Bubble (Dev)**: "I just gave it generic text and it created on-brand stadium art!"
**Speech Bubble (ADK-Bot)**: "The instructions guide the model to always match the brand."
**Style**: Dev UI mockup with chat and image preview, Corporate Memphis result
