# Page 10 — "The Knee Point: Finding Balance"

## Page Description
Final page. Explain the latency-throughput tradeoff and the knee point chart. Show real-world applications. End with an inspiring wrap-up.

## Panel Layout (4 panels)

### Panel 1 (Top, wide)
A holographic chart dominates the panel — the Latency vs Throughput knee point chart:
- X-axis: "Batch Size" (0, 50, 100, 150, 200, 250)
- Y-axis: "Normalized Metric (0-1)"
- BLUE line (p50_latency): starts low-left, curves up to top-right as batch size increases
- RED line (throughput, inverted): starts high-left, drops sharply, then flattens near zero
- A large glowing ORANGE dot marks where the lines cross, around batch size 32, labeled "Sweet Spot ~ BS 32"
- The area left of the sweet spot is green (good zone), right is red (danger zone)

**Speech bubble (Dr. Nova)**: "Throughput and latency pull in opposite directions. The Knee Point is where you get the best balance."

### Panel 2 (Middle left)
Past the knee point visualization: Tensor is overloaded, juggling too many orbs, some sparking and overheating. A user icon above looks frustrated (high latency). The throughput meter barely budges despite more load.

**Narration box**: "Past the knee point, throughput gains flatten while latency skyrockets. Users suffer."

### Panel 3 (Middle right)
Four holographic application cards float in the air, each with an icon and metric priority:
1. **Chatbots** — lightning bolt icon — "Low TTFT: instant response"
2. **Translation** — conveyor belt icon — "High Throughput: handle massive workloads"
3. **Streaming** — heartbeat icon — "Steady ITL: natural flow"
4. **On-device AI** — mobile phone icon — "Small Footprint: speed + low power"

**Narration box**: "Different applications optimize for different metrics."

### Panel 4 (Bottom, wide — Grand Finale)
Dr. Nova, Kai, and Tensor stand together triumphantly in front of the fully illuminated inference pipeline. The entire pipeline visualization stretches behind them — from input tokens flowing in on the left to user responses streaming out on the right. Everything glows with life and energy.

**Speech bubble (Dr. Nova)**: "Percentiles reveal the real distribution. The knee point balances throughput and latency. That's how we make AI fast AND reliable."
**Speech bubble (Kai)** (pumping his fist): "I'm ready to build my own inference pipeline!"
**Speech bubble (Tensor)** (giving thumbs up with multiple arms): "Let's go parallel!"
**Narration box** (bottom, final): "Training teaches the model. Inference applies it. Now go build something amazing."

## Style
Tech style. The knee point chart should be the visual centerpiece of Panel 1 — matching the style of the original latency vs throughput chart (blue and red lines on dark background). The finale panel is bright, energetic, and optimistic. Cyan, neon green, and warm highlights. Dark background.

## Characters
- Dr. Nova: confident, wrapping up the lesson
- Kai: excited, ready to apply what he's learned
- Tensor: celebratory, multiple thumbs-up
