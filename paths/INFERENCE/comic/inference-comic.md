# Intro to Inference: How to Run AI Models on a GPU — Comic Interpretation

## Overview
- **Source**: Google Cloud x NVIDIA Learning Path — Intro to Inference
- **Art Style**: Tech (futuristic, circuit patterns, neon accents)
- **Pages**: 10 + Cover
- **Characters**: Dr. Nova (Mentor), Kai (Student), Tensor (GPU mascot)
- **Generated on**: 2026-02-21

## Comic Pages

### Cover
![Cover](./00-cover.png)

**INTRO TO INFERENCE: How to Run AI Models on a GPU**
A Google Cloud x NVIDIA Learning Path

---

### Page 1 — Two Phases of AI
![Page 1](./01-page.png)

**Content**: Kai meets Dr. Nova and learns that every AI model has two phases: Training (learning from data) and Inference (applying that learning to make predictions). Inference is what users interact with.

---

### Page 2 — Training: The Full Loop
![Page 2](./02-page.png)

**Content**: The training loop explained — Forward Pass makes predictions, Loss Computation measures error against ground truth, Backward Pass adjusts weights. The cycle repeats until the model learns.

---

### Page 3 — Inference: Forward Pass Only
![Page 3](./03-page.png)

**Content**: Inference is much simpler — just the forward pass with frozen weights. But serving millions of users raises three key questions: speed, scale, and compute requirements.

---

### Page 4 — Why GPUs?
![Page 4](./04-page.png)

**Content**: Tensor (GPU mascot) demonstrates parallel processing by juggling hundreds of data orbs simultaneously, while a CPU character struggles one at a time. GPUs make large-scale inference practical.

---

### Page 5 — The Inference Pipeline
![Page 5](./05-page.png)

**Content**: The 6-step pipeline visualized as a futuristic assembly line: Preprocessing (tokenization) → Batching & Padding → Forward Pass → Decoding → Postprocessing → Serving.

---

### Page 6 — Model Formats: The Passport
![Page 6](./06-page.png)

**Content**: Models need a "passport" (format) to travel from training to deployment. Different formats exist because of ecosystem silos, hardware diversity, optimization goals, and backward compatibility.

---

### Page 7 — The Format Landscape
![Page 7](./07-page.png)

**Content**: Four modern formats compared — Safetensors (safe sharing), GGUF (LLMs on laptops), TensorRT (peak NVIDIA GPU performance), and ONNX (cross-framework bridge). The right format depends on the model's lifecycle stage.

---

### Page 8 — Performance Metrics
![Page 8](./08-page.png)

**Content**: Four key metrics: Total Latency (end-to-end time), Time to First Token (how fast the first word appears), Inter-Token Latency (streaming rhythm), and Throughput (requests per second).

---

### Page 9 — Percentiles: The Truth Behind Averages
![Page 9](./09-page.png)

**Content**: Averages hide the truth. Percentiles (P50, P90, P99) reveal the real distribution — most users may be fast, but tail latencies show the worst-case experiences that matter for fairness.

---

### Page 10 — The Knee Point: Finding Balance
![Page 10](./10-page.png)

**Content**: The latency-throughput tradeoff visualized with the knee point chart. Different applications optimize for different metrics. The wrap-up: percentiles + knee point + UX = fast, reliable AI.

---

## Core Knowledge Points

1. **Training vs Inference**: Training uses forward + backward passes to learn; inference uses only the forward pass with frozen weights.
2. **GPU Acceleration**: GPUs parallelize matrix multiplications across thousands of cores, making large-scale inference practical.
3. **The Inference Pipeline**: Preprocessing → Batching & Padding → Forward Pass → Decoding → Postprocessing → Serving.
4. **Model Formats**: Safetensors (safe sharing), GGUF (local/laptop), TensorRT (peak GPU performance), ONNX (cross-framework bridge).
5. **Performance Metrics**: Total Latency, TTFT, ITL, Throughput — measured with percentiles (P50, P90, P99), not averages.
6. **The Knee Point**: The optimal batch size where throughput and latency are best balanced for user experience.

## How to Generate Images

Use the `genimg-gemini-web` skill to generate all comic pages. Run from the `paths/INFERENCE/comic/` directory:

```bash
SKILL_DIR="$HOME/.claude/skills/genimg-gemini-web"
SESSION_ID="comic-inference-$(date +%s)"

# Step 1: Generate character reference sheet
npx -y bun "$SKILL_DIR/scripts/main.ts" \
  --promptfiles ../../.claude/skills/paper-comic/references/base-prompt.md \
                ../../.claude/skills/paper-comic/references/styles/tech.md \
                characters/characters.md \
  --image characters/characters.png \
  --sessionId "$SESSION_ID"

# Step 2: Generate cover
npx -y bun "$SKILL_DIR/scripts/main.ts" \
  --promptfiles ../../.claude/skills/paper-comic/references/base-prompt.md \
                ../../.claude/skills/paper-comic/references/styles/tech.md \
                prompts/00-cover.md \
  --image 00-cover.png \
  --sessionId "$SESSION_ID"

# Step 3: Generate pages 1-10
for i in $(seq -w 1 10); do
  npx -y bun "$SKILL_DIR/scripts/main.ts" \
    --promptfiles ../../.claude/skills/paper-comic/references/base-prompt.md \
                  ../../.claude/skills/paper-comic/references/styles/tech.md \
                  prompts/${i}-page.md \
    --image ${i}-page.png \
    --sessionId "$SESSION_ID"
done
```

**Important**: Use the same `--sessionId` for all runs to maintain character consistency across pages.
