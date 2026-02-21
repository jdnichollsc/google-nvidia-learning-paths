# Choosing the right format for your AI model: A comprehensive guide to AI inference formats

By: Ekaterina Sirazitdinova, NVIDIA and Ivan Nardini, Google Cloud

![Hero image showing AI model format logos including Safetensors, GGUF, PyTorch, ONNX, JAX, and TensorRT](https://d2yds90mtvelsl.cloudfront.net/original/3X/f/7/f75565533bc2a0d7d673d0fece6e57b824d8ca3d.jpeg)

**TL;DR:** A technical guide to AI model formats for [AI inference](https://cloud.google.com/discover/what-is-ai-inference?e=48754805&hl=en). Learn the trade-offs: use Safetensors for fast, secure serialization (replacing .bin), GGUF for quantized local/CPU inference (e.g., llama.cpp), TensorRT for compiled, high-performance NVIDIA GPU engines, and ONNX for graph-level framework interoperability.

This post is part of the [Intro to Inference: How to Run AI Models on a GPU](https://developers.google.com/learn/pathways/ai-models-on-gpu-intro) learning pathway. Check out the full pathway to get hands-on with foundational inference workloads on Google Cloud and earn a badge!

Training your AI model is just the beginning. The critical next step is packaging it for saving, sharing, and running [AI inference](https://cloud.google.com/discover/what-is-ai-inference?e=48754805&hl=en) in real-world applications. This requires choosing the optimal AI model export format to move your model beyond its training environment.

![A flowchart illustrates the AI model lifecycle, beginning with training the model, followed by packaging or exporting it, and concluding with running inference in applications.](https://d2yds90mtvelsl.cloudfront.net/original/3X/e/4/e411af8fee65a619f20e1e5b6cc1b42ac7500140.png)

Selecting the correct AI model format is paramount. It directly impacts your AI model’s portability across frameworks, loading speed, security, and operational efficiency on diverse hardware. This guide demystifies the current landscape of AI model formats, enabling you to make informed decisions for your AI projects and [AI inference](https://cloud.google.com/discover/what-is-ai-inference?e=48754805&hl=en) deployments.

## Why model formats matter

When we train a large language model (LLM), what we end up with is essentially a massive collection of weights, biases, and associated metadata — the distilled ‘knowledge’ of the training run. To make these values useful beyond the training environment, they need to be stored in a format that other systems can understand. That’s where model formats come in.

![A diagram illustrates the process from LLM training output, including weights, biases, and metadata, through various model formats like .bin, .gguf, .trt, and .onnx, to inference engines such as NVIDIA TensorRT, ONNX Runtime, and vLLM.](https://d2yds90mtvelsl.cloudfront.net/original/3X/6/b/6b7093b48abbc01c8f7c88b99c001e779239b767.png)

A format defines how a model’s parameters are serialized (converted into a stream of bytes) and reused: it specifies tensor layouts, layer descriptions, and how auxiliary information (like tokenizer configurations or architecture details) is bundled.

In today’s open-source LLM ecosystem, formats are what make weight sharing possible. Community checkpoints on [Hugging Face](https://huggingface.co/), GGUF-compressed models for laptops, or TensorRT-optimized engines for GPUs — they’re all different ways of packaging the same fundamental values for reuse during inference.

Without formats, there would be no portability between frameworks, no way to optimize for new hardware, and no thriving ecosystem of shared, remixable models.

## Why do different model formats exist?

At first glance, it might seem odd that we have so many model formats floating around. Wouldn’t one universal standard be enough? In practice, the AI ecosystem is too diverse for a single format to cover every use case. As the following diagram illustrates, different needs — technical and organizational — have shaped the formats we use today.

![This diagram explains why different model formats exist, citing reasons such as ecosystem silos, hardware diversity, optimization goals, and backward compatibility.](https://d2yds90mtvelsl.cloudfront.net/original/3X/6/6/662a6edb8bc8d4fc213e973e454bd30fad76b2ef.png)

### Ecosystem silos

Each deep learning framework began by inventing its own serialization. PyTorch saved models as .pt or .pth, TensorFlow used .pb, .h5, and SavedModel, [MXNet](https://mxnet.apache.org/) relied on .params, JAX leaned on [NumPy](https://numpy.org/) checkpoints, and [Caffe](https://caffe.berkeleyvision.org/) used .caffemodel files. These formats were built for internal convenience, not interoperability — which left developers with isolated ‘islands’ of models.

As AI spread to more platforms, the need for portability became obvious. The real turning point came with [ONNX](https://onnx.ai/), the first widely adopted universal format. ONNX gave developers a common language to export from one framework and import into another, creating the foundation for today’s model-sharing culture.

### Hardware diversity

A model optimized for a GPU isn’t necessarily ready to run on a CPU, mobile chip, or a custom accelerator. Different hardware targets expect different numerical representations, memory layouts, and operator support. Formats evolved to bridge this gap and make the same weights usable across a range of devices.

### Optimization goals

Exported models are rarely just ‘raw weights.’ As the following diagram illustrates, they often need graph fusions, operator pruning, quantization, or memory-efficient layouts to meet real-time inference demands. Specialized formats emerged to encapsulate these optimizations — like TensorRT .plan and .engine formats for NVIDIA GPUs.

### Backward compatibility

Finally, AI moves fast, and old formats can’t always handle new operations or architectural patterns. As transformer-based models exploded, earlier serialization methods lacked the primitives to represent them. New formats had to be created to capture these advances without breaking existing deployments.

## Modern formats for LLM checkpoints

The way we package models has matured dramatically in the LLM era. Checkpoints are no longer just about ‘saving weights’ — they’re about safe sharing, efficient loading, portability, and hardware-specific optimization. Here are the formats you’ll see most often today:

### [Safetensors (Hugging Face)](https://huggingface.co/docs/safetensors/en/index)

![Safetensors logo](https://d2yds90mtvelsl.cloudfront.net/original/3X/a/f/af14a7f9d2560ac77564ffbefb0912cd0d13e215.png)

The modern replacement for raw PyTorch .bin files, Safetensors is both faster and safer. Weights are memory-mapped (directly accessible from memory) for efficient loading, and the format prevents arbitrary code execution on load. That matters when you’re pulling down 30B-parameter models from the internet. Today, Hugging Face defaults to safetensors for most large checkpoints.

### [GGUF (successor to GGML)](https://huggingface.co/docs/hub/en/gguf)

A community-driven format that powers the explosion of ‘run LLMs on your laptop’ projects. GGUF is compact, supports multiple [quantization schemes](https://huggingface.co/docs/optimum/en/concept_guides/quantization), and is designed to work smoothly with [llama.cpp](https://github.com/ggml-org/llama.cpp) and similar lightweight runtimes.

### [TensorRT Engines](https://docs.nvidia.com/deeplearning/tensorrt/latest/architecture/architecture-overview.html)

![TensorRT Engines](https://d2yds90mtvelsl.cloudfront.net/original/3X/c/f/cf1c72a86c913adfcb259b13cdf2ea1ed30da1aa.png)

TensorRT-LLM is a high-performance backend designed for accelerating LLM inference on NVIDIA GPUs.
It works by compiling engines for specific models ahead of time. Each engine is tuned for fixed parameters such as GPU architecture (e.g., A100, L40), maximum batch size, input/output token lengths, and beam width.

Once compiled (using tools like [Optimum-NVIDIA](https://github.com/huggingface/optimum-nvidia) or via [Triton’s TensorRT-LLM backend](https://github.com/triton-inference-server/tensorrtllm_backend)), these engines encode optimizations like custom kernels and memory layouts tailored for the target hardware. During serving inference, the pre-compiled engine then bypasses much of the overhead from dynamic graph interpretation or operator dispatch, delivering much lower latency and higher throughput.

### [ONNX](https://onnx.ai/)

![ONNX logo](https://d2yds90mtvelsl.cloudfront.net/original/3X/6/f/6f6e46b167040b27df7bcb736d7066d34a00e1df.png)

ONNX was created to be the universal bridge between frameworks, and it’s still one of the most widely recognized exchange formats. For classic CV and NLP models, it remains a solid choice — especially if you need to move from [PyTorch](https://pytorch.org/) or [TensorFlow](https://www.tensorflow.org/) into runtimes like [ONNX Runtime](https://onnxruntime.ai/), [OpenVINO](https://www.intel.com/content/www/us/en/developer/tools/openvino-toolkit/overview.html), or [TensorRT](https://developer.nvidia.com/tensorrt). However, in the LLM world, ONNX isn’t always the default anymore. Many modern workflows skip straight to framework-native exports (e.g., safetensors) or hardware-specific compilers (e.g., TensorRT-LLM).

ONNX is most useful when targeting heterogeneous environments (CPU + GPU + accelerator mix), requiring intermediate graph optimization before further compilation, or needing a long-term archival format not tied to a single vendor. In other words, ONNX is less the everyday checkpoint format for LLMs, and more the ‘bridge’ when portability across diverse runtimes really matters.

### Framework-native (still alive)

![Framework native formats](https://d2yds90mtvelsl.cloudfront.net/original/3X/a/6/a64125d9f970fae65b970771e5a7e91f3543978e.png)

PyTorch .pt / .pth and [JAX](https://jax.readthedocs.io/en/latest/)/Flax .npz remain the go-to for training and research checkpoints. Most models start here before being exported to one of the formats above for sharing or deployment.

## Summary & key takeaways

Model formats are the invisible infrastructure that makes the LLM ecosystem work. At their core, all checkpoints are just weights, biases, and metadata. However, how those values are stored determines whether a model can be easily shared, optimized, and deployed.

*   **Different formats exist because the ecosystem is diverse:** frameworks, hardware, and optimization pipelines each have their own requirements.
*   **Framework-native formats** like .pt and .npz remain the starting point, but they don’t travel well on their own.
*   **Safetensors** has become the default for open-source weight sharing — fast, secure, and compatible with the Hugging Face ecosystem.
*   **GGUF** powers local inference, bringing LLMs to laptops and edge devices with lightweight quantization.
*   **TensorRT engines** and other vendor-specific binaries deliver peak performance in production, though at the cost of portability.
*   **ONNX** still matters as a bridge, especially when targeting heterogeneous environments or long-term archiving.

**The takeaway:** there’s no single ‘best’ format — the right one depends on where the model is in its lifecycle. As summarized in the table below, research favors framework-native, open-source sharing prefers safetensors, local inference thrives on GGUF, and production deployments demand optimized engines.

| Lifecycle Stage | Favored Format(s) | Primary Use Case |
|---|---|---|
| Research & Training | Framework-native (.pt, .pth, .npz) | Creating, training, and iterating on models within a specific ecosystem (like PyTorch or JAX). |
| Open-Source Sharing | Safetensors | Safely and quickly sharing model weights with the community. This is the modern default on platforms like Hugging Face. |
| Local Inference | GGUF | Running models efficiently on consumer hardware (laptops, CPUs) with lightweight quantization. |
| Production Deployment | TensorRT Engines, ONNX | Achieving maximum performance, lowest latency, and highest throughput on specific server hardware (e.g., NVIDIA GPUs). |

Looking ahead, compiler-driven intermediate representations (IRs) and hardware abstraction layers may reduce the visibility of formats to developers. For now, however, understanding these ‘passports’ is essential for getting models across borders: from training labs to real-world inference, and from large training infrastructure to the edge.

## What’s next

To further your understanding of AI model formats and [AI inference](https://cloud.google.com/discover/what-is-ai-inference?e=48754805&hl=en), check out the “[Intro to Inference: How to Run AI Models on a GPU](https://developers.google.com/learn/pathways/ai-models-on-gpu-intro)” learning pathway.

Also, explore additional resources and subscribe to the [NVIDIA community](https://developers.google.com/community/nvidia) for updates on related content.
