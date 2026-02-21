# Intro to Inference — Comic Storyboard

## Metadata
- **Title**: Intro to Inference: How to Run AI Models on a GPU
- **Art Style**: Tech (futuristic, circuit patterns, neon accents)
- **Pages**: 10 + Cover
- **Characters**: Dr. Nova (Mentor), Kai (Student), Tensor (GPU mascot)
- **Based on**: Google Cloud x NVIDIA Learning Path — Intro to Inference

---

## Cover

**Title**: "INTRO TO INFERENCE: How to Run AI Models on a GPU"
**Subtitle**: "A Google Cloud x NVIDIA Learning Path"
**Scene**: Dr. Nova and Kai stand in front of a massive holographic GPU architecture. Tensor floats between them, arms juggling glowing data orbs. Behind them, streams of light particles flow through a pipeline visualization. The Google Cloud and NVIDIA logos appear subtly in the lower corners.
**Color mood**: Deep blue background fading to black, cyan and neon green highlights.

---

## Page 1 — "Two Phases of AI" (Introduction)

**Narrative goal**: Introduce Training vs Inference as the two fundamental phases of every AI model.

### Panel 1 (Wide, top half)
- **Scene**: Kai walks into Dr. Nova's lab, looking at a holographic display showing a chatbot interface.
- **Kai**: "Dr. Nova, I've been using ChatGPT and other LLMs all day... but I have no idea how they actually work behind the scenes."
- **Dr. Nova**: "Great question, Kai! Every AI model has two phases: Training and Inference."

### Panel 2 (Left, bottom)
- **Scene**: Holographic split-screen. Left side shows a brain icon absorbing data streams (labeled "Training").
- **Narration box**: "Training is when the model learns from data — adjusting its internal weights through millions of examples."
- **Dr. Nova**: "Think of training as studying for an exam..."

### Panel 3 (Right, bottom)
- **Scene**: Right side of the split-screen shows the same brain icon now outputting predictions (labeled "Inference").
- **Dr. Nova**: "...and inference is taking the exam. The model applies what it learned to make predictions."
- **Kai**: "So inference is the part that users actually interact with!"

---

## Page 2 — "Training: The Full Loop" (Introduction)

**Narrative goal**: Explain the training loop — forward pass, loss, backward pass, weight updates.

### Panel 1 (Wide, top)
- **Scene**: Dr. Nova activates a holographic flowchart showing the training loop. The diagram floats in 3D.
- **Dr. Nova**: "Training has two key steps: a Forward Pass and a Backward Pass."

### Panel 2 (Center, large)
- **Scene**: The holographic training loop diagram is fully visible:
  - Training Dataset flows into Forward Pass (blue glowing box)
  - Forward Pass outputs Predicted Insights
  - Predicted Insights + Ground Truth Labels feed into Loss Computation (gear icon)
  - Loss Computation feeds into Backward Pass (blue glowing box)
  - Backward Pass updates the AI Network (brain icon with "Weights Updated" label)
  - AI Network loops back to Forward Pass
- **Narration box**: "The forward pass makes predictions. The backward pass compares them to the truth, computes the error, and adjusts the weights."

### Panel 3 (Bottom)
- **Scene**: Kai looks at the loop, realization dawning.
- **Kai**: "So the model keeps going around this loop, getting better each time?"
- **Dr. Nova**: "Exactly! But once training is done, inference is much simpler..."

---

## Page 3 — "Inference: Forward Pass Only" (Introduction)

**Narrative goal**: Show how inference is simpler — just a forward pass with frozen weights. Introduce the key production questions.

### Panel 1 (Top half, wide)
- **Scene**: Dr. Nova swipes the holographic display to show the inference diagram — much simpler than training.
  - Training Dataset + AI Network (with "Weights Frozen" label) feed into Forward Pass
  - Forward Pass outputs Predicted Insights
  - No backward pass, no loss computation
- **Dr. Nova**: "Inference is just the forward pass. No backward pass, no weight updates. The model's knowledge is frozen."

### Panel 2 (Bottom left)
- **Scene**: Kai holds up his tablet showing millions of user icons sending requests.
- **Kai**: "But if millions of people are using an LLM at once, how does it handle all that?"

### Panel 3 (Bottom right)
- **Scene**: Dr. Nova raises three fingers, holographic text appears for each:
  1. "How fast can we respond?"
  2. "How many users at once?"
  3. "How much compute do we need?"
- **Dr. Nova**: "Those are the three big questions of serving AI in production. And that's where GPUs come in!"

---

## Page 4 — "Why GPUs?" (Exploration)

**Narrative goal**: Introduce GPUs vs CPUs and why parallel processing matters for AI inference.

### Panel 1 (Top, wide)
- **Scene**: Tensor (the GPU mascot) zooms into frame, all arms extended. A CPU chip character (single arm, looking tired) stands next to it for contrast.
- **Tensor**: "I'm built for parallel processing! Thousands of cores working simultaneously!"
- **Narration box**: "GPUs are hardware accelerators designed for massive mathematical operations."

### Panel 2 (Middle left)
- **Scene**: The CPU character tries to juggle data orbs one at a time, dropping them.
- **Narration box**: "CPUs are generalists — they process data sequentially, one operation at a time."
- **CPU**: "One... at... a... time..."

### Panel 3 (Middle right)
- **Scene**: Tensor juggles hundreds of glowing orbs simultaneously with all its arms, looking effortless.
- **Tensor**: "I handle thousands of matrix multiplications in parallel!"
- **Narration box**: "GPUs with thousands of parallel cores multiply and add tensors at scale."

### Panel 4 (Bottom, wide)
- **Scene**: Dr. Nova and Kai watch the demonstration. Behind them, a data center visualization glows.
- **Dr. Nova**: "Without GPU acceleration, modern LLMs wouldn't be practical. But raw power isn't enough — we need a structured pipeline."
- **Kai**: "A pipeline?"

---

## Page 5 — "The Inference Pipeline" (Core)

**Narrative goal**: Walk through the 6 steps of the LLM inference pipeline.

### Panel 1 (Top, establishing shot)
- **Scene**: Dr. Nova projects a holographic conveyor belt / assembly line with 6 stations, each glowing a different color. Kai watches, fascinated.
- **Dr. Nova**: "The inference pipeline is a structured sequence of steps that turns raw input into useful output."

### Panel 2 (Station 1 — Preprocessing)
- **Scene**: Raw text flows into a station where it's broken into glowing tokens.
- **Label**: "1. Preprocessing"
- **Narration box**: "Tokenization: breaking text into tokens the model can understand."

### Panel 3 (Station 2 — Batching)
- **Scene**: Multiple token streams are grouped and padded into neat rectangular grids.
- **Label**: "2. Batching & Padding"
- **Narration box**: "Converting inputs into rectangular tensors for efficient GPU processing."

### Panel 4 (Station 3 — Forward Pass)
- **Scene**: The tensor batches flow through a glowing neural network (the core of the pipeline). Tensor is inside, arms working.
- **Label**: "3. Model Forward Pass"
- **Narration box**: "The trained network computes predictions from the inputs."

### Panel 5 (Stations 4-6 — Decoding, Postprocessing, Serving)
- **Scene**: Outputs flow through final stations: logits become tokens (Decoding), tokens become readable text (Postprocessing), and results stream out to user icons (Serving).
- **Labels**: "4. Decoding → 5. Postprocessing → 6. Serving"
- **Kai**: "So the pipeline takes my question and delivers an answer through all these steps!"

---

## Page 6 — "Model Formats: The Passport" (Core)

**Narrative goal**: Explain why model formats matter — they're how models travel between training and deployment.

### Panel 1 (Top, wide)
- **Scene**: Dr. Nova holds up a holographic "passport" — it looks like a file icon with format labels (.bin, .gguf, .trt, .onnx).
- **Dr. Nova**: "Once a model is trained, it needs a 'passport' — a format — to travel from the training lab to production."
- **Narration box**: "Model formats define how weights, biases, and metadata are stored and shared."

### Panel 2 (Middle)
- **Scene**: A holographic diagram shows: LLM Training Output (weights, biases, metadata) → Model Format (.bin, .gguf, .trt, .onnx) → Inference Engine (TensorRT, ONNX Runtime, vLLM).
- **Kai**: "Why can't we just use one format for everything?"

### Panel 3 (Bottom)
- **Scene**: Dr. Nova projects four icons representing the reasons: Ecosystem Silos, Hardware Diversity, Optimization Goals, Backward Compatibility.
- **Dr. Nova**: "Different frameworks, hardware, and optimization needs all demand different formats. There's no one-size-fits-all."

---

## Page 7 — "The Format Landscape" (Core)

**Narrative goal**: Introduce the 4 main modern formats: Safetensors, GGUF, TensorRT, ONNX.

### Panel 1 (Top left — Safetensors)
- **Scene**: A glowing shield icon with the Safetensors logo. A lock symbol indicates security.
- **Label**: "Safetensors"
- **Narration box**: "Fast, secure. The default for sharing models on Hugging Face. Prevents code execution on load."

### Panel 2 (Top right — GGUF)
- **Scene**: A laptop icon with a tiny LLM running on it. Compression arrows show quantization.
- **Label**: "GGUF"
- **Narration box**: "Compact, quantized. Powers 'LLMs on your laptop' with llama.cpp."

### Panel 3 (Bottom left — TensorRT)
- **Scene**: A rocket engine icon with the NVIDIA logo. Speed lines and flame effects.
- **Label**: "TensorRT Engines"
- **Narration box**: "Compiled for NVIDIA GPUs. Maximum performance, lowest latency."
- **Tensor**: "This is MY favorite!"

### Panel 4 (Bottom right — ONNX)
- **Scene**: A bridge icon connecting different framework logos (PyTorch, TensorFlow, etc.).
- **Label**: "ONNX"
- **Narration box**: "The universal bridge. Best for heterogeneous environments with mixed hardware."

### Panel 5 (Bottom strip)
- **Scene**: Kai looks at his tablet showing a lifecycle table.
- **Kai**: "So the right format depends on where the model is in its lifecycle — research, sharing, local use, or production!"

---

## Page 8 — "Performance Metrics: What Really Matters" (Core)

**Narrative goal**: Introduce the key inference metrics: latency, TTFT, ITL, and throughput.

### Panel 1 (Top, wide)
- **Scene**: Dr. Nova and Kai stand in front of a large holographic dashboard showing real-time metrics.
- **Dr. Nova**: "Now let's talk about how we measure inference performance."
- **Kai**: "Why do some AI apps feel instant while others lag?"

### Panel 2 (Left column — Latency)
- **Scene**: A stopwatch icon. A user sends a message, waits, gets a response. The total time is highlighted.
- **Label**: "Total Latency"
- **Narration box**: "End-to-end response time — from request to complete answer."

### Panel 3 (Right column — TTFT)
- **Scene**: A user sends a message. The very first token appears quickly (highlighted with a flash).
- **Label**: "Time to First Token (TTFT)"
- **Narration box**: "How fast the first word appears. Critical for chatbots."

### Panel 4 (Left bottom — ITL)
- **Scene**: Tokens stream out one by one in a steady rhythm, like a heartbeat monitor.
- **Label**: "Inter-Token Latency (ITL)"
- **Narration box**: "The rhythm of tokens after the first. Smooth flow = natural experience."

### Panel 5 (Right bottom — Throughput)
- **Scene**: Multiple user icons sending requests simultaneously. A meter shows requests/second.
- **Label**: "Throughput"
- **Narration box**: "How many requests or tokens per second the system can serve."

---

## Page 9 — "Percentiles: The Truth Behind Averages" (Core)

**Narrative goal**: Explain why averages lie and percentiles reveal the real user experience.

### Panel 1 (Top, wide)
- **Scene**: Dr. Nova points at a holographic chart showing an "average latency" bar. Kai looks satisfied.
- **Kai**: "Average latency is 50ms — that's great!"
- **Dr. Nova**: "Not so fast. Averages hide the truth."

### Panel 2 (Middle, large)
- **Scene**: The chart expands to show a distribution. Most requests are fast, but a long tail of slow requests extends to the right. Three markers appear:
  - P50 (median): "The typical experience"
  - P90: "1 in 10 users waits this long"
  - P99: "1 in 100 users gets STUCK"
- **Narration box**: "Percentiles reveal the real distribution. P50 is the median, P90 and P99 show the worst cases."

### Panel 3 (Bottom)
- **Scene**: Kai imagines himself as the P99 user, frustrated, staring at a loading spinner while everyone else gets instant responses.
- **Kai**: "So even if most users are happy, some are having a terrible experience?"
- **Dr. Nova**: "Exactly. Tail latencies (P90, P99) ensure fairness — no user should get stuck waiting."

---

## Page 10 — "The Knee Point: Finding Balance" (Summary)

**Narrative goal**: Explain the latency-throughput tradeoff and the knee point. Wrap up with real-world applications.

### Panel 1 (Top, wide)
- **Scene**: A holographic chart shows two crossing curves:
  - Blue line (latency): starts low, curves up as batch size increases
  - Red line (throughput, inverted): starts high, drops as batch size increases
  - A glowing orange dot marks where they cross: "Sweet Spot ~ BS 32"
- **Dr. Nova**: "Throughput and latency pull in opposite directions. The Knee Point is where you get the best balance."

### Panel 2 (Middle left)
- **Scene**: Beyond the knee point, a user icon looks frustrated (high latency). Tensor is overloaded.
- **Narration box**: "Past the knee point, you gain little throughput while latency skyrockets."

### Panel 3 (Middle right)
- **Scene**: Four application cards float holographically:
  - Chatbots: "Low TTFT" (lightning icon)
  - Translation: "High Throughput" (conveyor icon)
  - Streaming: "Steady ITL" (heartbeat icon)
  - On-device AI: "Small Footprint" (mobile icon)
- **Narration box**: "Different applications optimize for different metrics."

### Panel 4 (Bottom, wide — finale)
- **Scene**: Dr. Nova, Kai, and Tensor stand together in front of the holographic pipeline, now fully lit up and running.
- **Dr. Nova**: "Percentiles reveal the real distribution. The knee point balances throughput and latency. Together with great UX, that's how we make AI fast and reliable."
- **Kai**: "I'm ready to build my own inference pipeline!"
- **Tensor**: (giving a thumbs up with multiple arms) "Let's go parallel!"
- **Narration box**: "Training teaches the model. Inference applies it. Now go build something amazing."

---

## Core Knowledge Points

1. **Training vs Inference**: Training uses forward + backward passes to learn; inference uses only the forward pass with frozen weights.
2. **GPU Acceleration**: GPUs parallelize matrix multiplications, making large-scale inference practical.
3. **The Inference Pipeline**: Preprocessing → Batching → Forward Pass → Decoding → Postprocessing → Serving.
4. **Model Formats**: Safetensors (safe sharing), GGUF (local/laptop), TensorRT (peak GPU performance), ONNX (cross-framework bridge).
5. **Performance Metrics**: Latency, TTFT, ITL, Throughput — measured with percentiles (P50, P90, P99), not averages.
6. **The Knee Point**: The optimal batch size where throughput and latency are best balanced for user experience.
