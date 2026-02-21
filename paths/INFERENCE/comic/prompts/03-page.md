# Page 3 — "Inference: Forward Pass Only"

## Page Description
Show how inference is simpler than training — just a forward pass with frozen weights. Introduce the three key production questions.

## Panel Layout (3 panels)

### Panel 1 (Top half, wide)
Dr. Nova swipes the holographic display, and the complex training loop dissolves. A much simpler diagram appears:
- "Training Dataset" and "AI Network" (with a snowflake/lock icon and label "*Weights Frozen*") both connect to a single blue "Forward Pass" box
- Forward Pass connects to "Predicted Insights"
- No backward pass, no loss computation — the right side of the diagram is empty/faded
- The simplicity is striking compared to the previous page

**Speech bubble (Dr. Nova)**: "Inference is just the forward pass. No backward pass, no weight updates. The model's knowledge is frozen."

### Panel 2 (Bottom left)
Kai holds up his tablet. The screen shows a visualization of millions of tiny user icons sending glowing request beams toward a central server. The scale is overwhelming.

**Speech bubble (Kai)**: "But if millions of people are using an LLM at once, how does it handle all that?"

### Panel 3 (Bottom right)
Dr. Nova raises three fingers. Next to each finger, holographic text materializes:
1. "How FAST can we respond?" (with a speedometer icon)
2. "How MANY users at once?" (with a crowd icon)
3. "How MUCH compute?" (with a GPU chip icon)

**Speech bubble (Dr. Nova)**: "Those are the three big questions of serving AI in production. And that's where GPUs come in!"

## Style
Tech style. The simplified inference diagram should feel clean and minimal compared to the training loop. Frozen weights shown with ice/snowflake visual. Dark background, cyan holographic elements.

## Characters
- Dr. Nova: confident, explaining with gestures
- Kai: curious, holding up tablet
