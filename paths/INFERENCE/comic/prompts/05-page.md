# Page 5 — "The Inference Pipeline"

## Page Description
Walk through the 6 steps of the LLM inference pipeline as a futuristic assembly line / conveyor belt visualization.

## Panel Layout (5 panels)

### Panel 1 (Top, establishing shot)
Dr. Nova projects a holographic conveyor belt that stretches across the lab. It has 6 distinct glowing stations, each a different color. Kai watches, fascinated. Tensor hovers near the pipeline, ready to help.

**Speech bubble (Dr. Nova)**: "The inference pipeline is a structured sequence that turns raw input into useful output."

### Panel 2 (Station 1 — Preprocessing)
Close-up of the first station. Raw text ("How does AI work?") flows in as a stream of characters. The station breaks them into individual glowing tokens: ["How", "does", "AI", "work", "?"]. Each token is a small glowing cube.

**Label**: "1. PREPROCESSING"
**Narration box**: "Tokenization: breaking text into tokens the model understands."

### Panel 3 (Station 2 — Batching & Padding)
Multiple streams of tokens from different users are gathered together and arranged into a neat rectangular grid. Shorter sequences get padding tokens (shown as dim/transparent cubes) added to fill the grid evenly.

**Label**: "2. BATCHING & PADDING"
**Narration box**: "Multiple requests are grouped into rectangular tensors for efficient GPU processing."

### Panel 4 (Station 3 — Forward Pass)
The rectangular tensor batches flow into a massive glowing neural network structure — layers of connected nodes pulsing with energy. Tensor is inside the network, all arms working, routing data through the layers.

**Label**: "3. MODEL FORWARD PASS"
**Narration box**: "The trained network computes predictions from the batched inputs."

### Panel 5 (Bottom, wide — Stations 4-6)
The output flows through three final stations in sequence:
- Station 4 (Decoding): Logits (probability bars) are converted into tokens step by step
- Station 5 (Postprocessing): Tokens are assembled back into readable text
- Station 6 (Serving): Completed responses stream out to multiple user icons

**Labels**: "4. DECODING → 5. POSTPROCESSING → 6. SERVING"
**Speech bubble (Kai)**: "So the pipeline takes my question and delivers an answer through all these steps!"

## Style
Tech style. The conveyor belt is a futuristic assembly line with glowing stations. Each station has a distinct accent color. Data flows as light particles along neon paths. Dark background with grid floor.

## Characters
- Dr. Nova: presenting the pipeline
- Kai: watching from the side
- Tensor: inside the Forward Pass station, working
