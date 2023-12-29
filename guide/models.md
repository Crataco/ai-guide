![image](https://user-images.githubusercontent.com/55674863/230696024-98ce9e16-f558-4402-ac43-0e7f960c118c.png)

# Models
## What are models?

**TL;DR:** A model is your AI's brain.

A heavily dumbed-down explanation is that a model is the AI that generates text.

The models are trained on top of pre-existing text and then released, often as base models (e.g. LLaMA) of specific sizes (e.g. 7B, 13B, 33B, and 70B). These base models are simple and often referred to as "glorified autocomplete" or "text completion" models, because they generate text after the user's input.

Finetunes are used to train the models are trained on further data, making it easier to use them like an assistant or chatting partner.

There are also different ways people run models: these are called backends.

## What is a backend?

Backends are different ways to store and run the AI model. The most notable ones are Transformers, GGUF, and Exllama. **The option recommended for most users is GGUF.**

- GGUF / GGML versions run on most computers thanks to quantization. You can consider "quantization" a way to cut down on model size and resource usage with small quality loss. It has "levels" that range from "q2" (lightest, worst quality) to "q8" (heaviest, best quality). A level of q5_K_M is ideal for most situations unless you have more or less RAM to spare. [TheBloke](https://huggingface.co/TheBloke) converts many Transformers models into the GGUF format, and scrolling down his pages would bring you to [this chart](https://huggingface.co/TheBloke/Llama-2-7B-GGUF#provided-files), telling you the size and the most RAM the model would use under different quantization levels.

- Transformers has been around for a while and is pretty much a universal standard for AI models, but their models are unoptimized for running on consumer hardware and use *way* more resources than necessary. Approximately, while the average 7B model under GGUF would require 8GB of RAM, a 7B model under Transformers would require 24-32GB of RAM.

- GPTQ, Exllama, and etc. are other backends with their own quantized format, but they're only useful if you have a recent graphics card (GPU). You'd have the best luck with NVIDIA GPUs, but with AMD GPUs, your mileage may vary. This is the option recommended if you have a powerful enough GPU for the model you want to run, but this guide will not cover this option.

This guide will assume users chose GGUF and a frontend that supports it (like KoboldCpp, Oobabooga's Text Generation Web UI, Faraday, or LM Studio).

## Model recommendations

Recommendations are based heavily on WolframRavenwolf's LLM tests:
- [WolframRavenwolf's 7B-70B General Test](https://old.reddit.com/r/LocalLLaMA/comments/17fhp9k/huge_llm_comparisontest_39_models_tested_7b70b/) (2023-10-24)
- [WolframRavenwolf's 7B-20B Roleplay Test](https://old.reddit.com/r/LocalLLaMA/comments/17kpyd2/huge_llm_comparisontest_part_ii_7b20b_roleplay/) (2023-10-31)

The following are the models this guide recommends, and the amount of RAM recommended for your computer to run them. If you do not have enough system RAM, but some VRAM to spare, you can "offload" the model's "layers," splitting the model between your system RAM and video memory.

There are two things to keep in mind:
- Most models work best when you follow a generation format. These are often called "instruct presets" or "prompt templates" and make it clear to the model when the user talks and when the AI talks. If you do not know which one to use, scroll down on the model's page and it will usually be under "prompt template."
- Settings influence the responses your models give you. A good place to start is to set "Min P" to 0.1 and "Temperature" to 1.0. Lowering Min P will give the AI more tokens to choose from, and raising the temperature will make it more likely it'll choose one of the lesser likely tokens.

* * *

### General Use (like ChatGPT)
- Mini (~512MB RAM) - **[RWKV-4 World](https://huggingface.co/Crataco/RWKV-4-World-Series-GGML)**
- 1.1B (~2GB RAM) - **[TinyLlama 1.1B Chat](https://huggingface.co/TheBloke/TinyLlama-1.1B-Chat-v0.3-GGUF)**
- 3B (~4GB RAM) - **[Nous-Capybara-3B-V1.9](https://huggingface.co/afrideva/Nous-Capybara-3B-V1.9-GGUF)**
- 7B (~8GB RAM) - **[OpenHermes 2.5 7B](https://huggingface.co/TheBloke/OpenHermes-2.5-Mistral-7B-GGUF)**
- 13B (~16GB RAM) - **[Xwin-MLewd 13B](https://huggingface.co/TheBloke/Xwin-MLewd-13B-v0.2-GGUF)**
- 34B (~32GB RAM) - **[Nous-Hermes 2 Yi-34B](https://huggingface.co/TheBloke/Nous-Hermes-2-Yi-34B-GGUF)**
- 8x7B (~32GB RAM) - **[Mixtral-8x7B Instruct](https://huggingface.co/TheBloke/Mixtral-8x7B-Instruct-v0.1-GGUF)**
- 70B (~64GB RAM) - **[Xwin-LM 70B](https://huggingface.co/TheBloke/Xwin-LM-70B-V0.1-GGUF)**

* * *

### Chat and Roleplay (like CharacterAI, Replika, etc.) and Storywriting (like NovelAI)
*You can also use general-purpose assistants for RP and storytelling, but these models are better known for their focus on them.*
- 1.3B (~2GB RAM) - **[Metharme 1.3B](https://huggingface.co/Crataco/Metharme-1.3B-GGML)**
- 7B (~8GB RAM) - **[Dolphin 2.2.1 7B](https://huggingface.co/TheBloke/dolphin-2.2.1-mistral-7B-GGUF)**
- 13B (~16GB RAM) - **[Noromaid 13B](https://huggingface.co/TheBloke/Noromaid-13B-v0.2-GGUF)**
- 20B (~20GB RAM) - **[Noromaid 20B](https://huggingface.co/TheBloke/Noromaid-20B-v0.1.1-GGUF)**\*
- 70B (~64GB RAM) - **[lzlv 70B](https://huggingface.co/TheBloke/lzlv_70B-GGUF)** or **[Euryale 1.3 70B](https://huggingface.co/TheBloke/Euryale-1.3-L2-70B-GGUF)**
- 120B (~80GB RAM) - **[Goliath 120B](https://huggingface.co/TheBloke/goliath-120b-GGUF)**\*

\* *These models (Noromaid 20B and Goliath 120B) are an unofficial size, often referred to as a "Frankenstein model" or "Frankenmerge". Its generations are unreliable compared to the 7B and 13B models, but some in the community prefer their vocabulary.*

* * *

### Text Adventure (like AI Dungeon)
*These models are trained on human-written text adventures, making it generate Choose Your Own Adventure stories. They work best in "Adventure" mode (Kobold) or with the "Adventure" preset (SillyTavern).*
- 1.5B (~2GB RAM) - **[AI Dungeon 2 Classic](https://huggingface.co/Crataco/AI-Dungeon-2-Classic-GGML)** (via [KoboldCpp](https://github.com/LostRuins/koboldcpp))
- 7B (~8GB RAM) - **[Dans-AdventurousWinds-Mk2-7B](https://huggingface.co/TheBloke/Dans-AdventurousWinds-Mk2-7B-GGUF)**
- 13B (~16GB RAM) - **[Dans-CreepingSenseOfDoom-13B](https://huggingface.co/PocketDoc/Dans-CreepingSenseOfDoom-13b-gguf)** or **[Dans-RetroRodeo-13B](https://huggingface.co/PocketDoc/Dans-RetroRodeo-13b-gguf)** or **[Spring Dragon](https://huggingface.co/TheBloke/Spring-Dragon-GGUF)**
