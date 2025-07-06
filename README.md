# VulkanIlm – Run LLaMA on Fire

**VulkanIlm** (from _"Vulkan"_ 🔥 and _"Ilm"_ 📚 meaning "knowledge" in Urdu/Arabic) is a lightweight, Pythonic wrapper for running **LLaMA models** on legacy GPUs using the **Vulkan backend** from [`llama.cpp`](https://github.com/ggerganov/llama.cpp).

Designed for developers with older AMD/Intel GPUs, `VulkanIlm` enables blazing-fast local LLM inference without needing CUDA or ROCm.

---

## 🧠 Why VulkanIlm?

> Not everyone has a CUDA-capable GPU. Not everyone should need one to use AI.

`VulkanIlm` is:
- ✅ **Python-first**: No C++/CMake experience required
- 🧵 Built on top of [`llama-cpp-python`](https://github.com/abetlen/llama-cpp-python) – but extended to support **Vulkan**
- 🔥 **GPU-accelerated** inference even on older AMD cards
- 📦 Easy to install, use, and deploy in your own AI apps

---

## 📦 Installation

> **Prerequisites**:
> - Vulkan-capable GPU (e.g. AMD RX 580)
> - Vulkan drivers installed
> - Python 3.8+

```bash
pip install vulkanilm
````

> If Vulkan backend isn't detected, you can manually build `llama.cpp` with Vulkan support and point to it. (See [Build Instructions](#️-vulkan-build-instructions))

---

## 🧑‍💻 Example Usage

```python
from vulkanilm import VulkanLlama

llm = VulkanLlama(model_path="models/mistral.gguf", n_gpu_layers=100)

response = llm.chat("Explain the term 'ilm' in AI context.")
print(response)
```

> ☑️ Uses GPU if available
> ☑️ Falls back gracefully if not
> ☑️ Streamlined `chat()` interface

---

## ⚙️ Vulkan Build Instructions (If Needed)

If your system doesn't detect Vulkan automatically:

1. Clone `llama.cpp` with Vulkan enabled:

```bash
git clone https://github.com/ggerganov/llama.cpp
cd llama.cpp
LLAMA_VULKAN=1 make libllama.so
```

2. In your Python code, load the shared library manually:

```python
llm = VulkanLlama(
    model_path="models/mistral.gguf",
    lib_path="path/to/llama.cpp/build/libllama.so"
)
```

---

## 🌐 Features

* ✨ `chat()` and `generate()` APIs
* 💬 Supports system prompts and role-based formatting
* 🔥 Vulkan-backed token sampling (greedy, top-k/top-p)
* 🧠 Custom `llama_context_params` options
* 📜 Streaming token generation
* 🧹 Memory-managed lifecycle (calls `llama_free()`)

---

## 📍 Roadmap

* [x] LLaMA loading with Vulkan shared lib
* [x] Simple Python wrapper with `llama-cpp-python`
* [ ] Model quantization CLI
* [ ] CLI runner: `vulkanilm chat -m model.gguf`
* [ ] Web UI interface with Gradio

---

## 🧾 Meaning Behind the Name

In South Asian and Islamic culture, **"Ilm" (علم)** means *knowledge*, wisdom, and divine understanding.
Combined with **Vulkan**, a high-performance GPU API, this project stands for **accessible, local AI power** — *knowledge on fire*.

---

## 🙌 Contributing

PRs are welcome! Fork this repo, open issues, and help bring fast, GPU-backed LLMs to everyone.

---

## 📄 License

MIT License – free to use, modify, and share.

---

> *Built with 🔥 by Talha | Running local LLMs on fire for everyone, everywhere.*
