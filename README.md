# Google Cloud x NVIDIA Learning Paths

> **An open-source learning companion for Google Cloud and NVIDIA technologies**

<table>
  <tr>
    <td>
      Google Cloud x NVIDIA Learning Paths
    </td>
  </tr>
  <tr>
    <td>
      <a href="./paths/INFERENCE/comic/INFERENCE.pdf">
        <img src="./paths/INFERENCE/comic/00-cover.png" width="300">
      </a>
    </td>
  </tr>
</table>

This repository is a hands-on guide for developers who want to understand and work with AI infrastructure — from running inference on GPUs to optimizing model performance at scale. Each learning path combines explanations, diagrams, and runnable Jupyter notebooks so you can learn by doing.

Whether you're new to AI deployment or looking to deepen your understanding of GPU-accelerated workloads, this repo gives you a structured starting point with real code and practical examples.

## Learning Paths

### [Intro to Inference: How to Run AI Models on a GPU](./paths/INFERENCE/)

Learn how to set up and run AI inference on GPUs in Google Cloud. This pathway covers:

- **Training vs. Inference** — Understand the fundamental differences and how the inference pipeline works
- **Foundations of Inference** — Build a step-by-step inference pipeline: preprocessing, batching, forward pass, decoding, and postprocessing
- **Model Formats** — Choose the right format (Safetensors, GGUF, TensorRT, ONNX) for your deployment scenario
- **Performance Metrics** — Measure latency, throughput, TTFT, and learn why percentiles matter more than averages

**Notebooks:**
- [`01_foundations_of_inference.ipynb`](./paths/INFERENCE/01_foundations_of_inference.ipynb) — CPU vs GPU inference, pipeline components, batching fundamentals
- [`02_performance_metrics.ipynb`](./paths/INFERENCE/02_performance_metrics.ipynb) — Latency, throughput, and finding the knee point

**Articles:**
- [Choosing the right format for your AI model](./paths/INFERENCE/INFERENCE_FORMATS_GUIDE.md) — A comprehensive guide to AI inference formats

> More learning paths coming soon — contributions welcome!

## AI-Powered Research Tools

This repo includes a set of AI skills (powered by [Claude Code](https://claude.com/claude-code)) that help you go deeper into any topic:

| Skill | What it does |
|---|---|
| **Paper2Code** | Converts research papers into executable Python code through a 4-stage pipeline |
| **Deep Research** | Generates comprehensive, cited research reports with evidence tracking |
| **Paper Comic** | Turns dense academic papers into educational visual comics |
| **Paper Analyzer** | Parses PDFs with high precision (formulas, tables, figures) and rewrites them in different styles |
| **Visual Architect** | Transforms paper methodology into structural visual schemas |
| **GenImg Gemini Web** | Image generation backend powered by Google Gemini |

### Quick Start

1. **Clone the repository**
    ```bash
    git clone https://github.com/jdnichollsc/google-nvidia-learning-paths.git
    cd google-nvidia-learning-paths
    ```

2. **Explore a learning path**
    ```bash
    cd paths/INFERENCE
    jupyter notebook
    ```

3. **Use the AI skills** (optional — requires [Claude Code](https://claude.com/claude-code))
    ```bash
    # The skills/ folder is auto-detected by Claude Code
    # Try: "Implement this paper" or "Generate a research report on LLM inference"
    ```

## Project Structure

```
paths/
└── INFERENCE/              # Intro to Inference learning path
    ├── README.md           # Path overview and notes
    ├── INFERENCE_FORMATS_GUIDE.md
    ├── 01_foundations_of_inference.ipynb
    └── 02_performance_metrics.ipynb

skills/                     # AI-powered research & learning tools
├── deep-research/
├── paper2code/
├── paper-comic/
├── paper-analyzer/
├── genimg-gemini-web/
└── visual-architect/
```

## Resources

- [Google Cloud x NVIDIA Developer Community](https://developers.google.com/community/nvidia)
- [Google Cloud AI Inference](https://cloud.google.com/discover/what-is-ai-inference)
- [NVIDIA TensorRT Documentation](https://docs.nvidia.com/deeplearning/tensorrt/latest/)
- [Hugging Face Model Hub](https://huggingface.co/models)

## Contributing

Contributions are welcome! Whether it's adding notes to an existing path, creating a new learning path, or improving the AI skills — open a PR.

## Credits

- AI research skills based on [Claude Code skills for academic papers](https://github.com/zsyggg/paper-craft-skills)

## Happy learning!
Made with <3

<img width="150px" src="https://avatars0.githubusercontent.com/u/28855608?s=200&v=4" align="right">
