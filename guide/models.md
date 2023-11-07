![image](https://user-images.githubusercontent.com/55674863/230696024-98ce9e16-f558-4402-ac43-0e7f960c118c.png)

# Models
## What are models?

**TL;DR:** A model is your AI's brain.

In this guide, a model is the AI that generates text. They are trained on top of pre-existing text and then released, often as base models (e.g. LLaMA) of specific sizes (e.g. 7B, 13B, 33B, and 70B). These base models are simple: given an input (e.g. "hello"), they complete it with their own output (", world!"). They're often referred to as "glorified autocomplete" models.

Finetunes are used to train the models are trained on further data, making it easier to use them like an assistant or chatting partner.

There are also different ways people run models: these are called backends.

## What is a backend?

Backends are different ways to store and run the AI model. The most notable ones are Transformers, GGUF, and Exllama. **The option recommended for most users is GGUF.**

- GGUF / GGML versions run on most computers thanks to quantization. For the sake of simplicity, you can consider "quantization" a way to cut down on size, often making the AI slightly dumber. It has "levels" that range from "q2" (lightest, worst quality) to "q8" (heaviest, best quality), but a value of q4_K_M is ideal for most situations. [TheBloke](https://huggingface.co/TheBloke) converts many Transformers models into the GGUF format, and scrolling down his pages would bring you to [this chart](https://huggingface.co/TheBloke/Llama-2-7B-GGUF#provided-files), telling you the size and how much RAM the model would use under a certain level.

- Transformers has been around for a while and is pretty much a universal standard for AI models, but their models are unoptimized for running on consumer hardware and use *way* more resources than necessary. Approximately, while a 7B model under GGUF would require 8GB of RAM, a 7B model under Transformers would require 24-32GB of RAM.

- GPTQ, Exllama, and etc. are other backends with their own quantized format, but they're only useful if you have a recent graphics card (GPU). You'd have the best luck with NVIDIA GPUs, but with AMD GPUs, your mileage may vary. This is the option recommended if you have a powerful enough GPU for the model you want to run, but this guide will not cover this option.

This guide will assume users chose GGUF and a frontend that supports it (like KoboldCpp, Faraday or LM Studio).

## Model recommendations

Sources:
- [WolframRavenwolf's 7B-70B General Test](https://old.reddit.com/r/LocalLLaMA/comments/17fhp9k/huge_llm_comparisontest_39_models_tested_7b70b/) (2023-10-24)
- [WolframRavenwolf's 7B-20B Roleplay Test](https://old.reddit.com/r/LocalLLaMA/comments/17kpyd2/huge_llm_comparisontest_part_ii_7b20b_roleplay/) (2023-10-31)

The following are the models this guide recommends, and the amount of RAM recommended for your computer to run them. If you do not have enough system RAM, but some VRAM to spare, you can "offload" the model's "layers," splitting the model between your system RAM and video memory.

One important thing to keep in mind is that most models work best when you follow a generation format. These are often called "instruct presets" or "prompt templates". If you do not know which one to use, most models on this list will use the de-facto standard "Alpaca" preset unless specified otherwise.

* * *

### General-Purpose (like ChatGPT)
- Mini (~512MB RAM) - **[LaMini-LM](https://github.com/mbzuai-nlp/LaMini-LM#models)** (via [languagemodels](https://github.com/jncraton/languagemodels))
- 1.1B (~2GB RAM) - **[TinyLlama 1.1B Chat](https://huggingface.co/TheBloke/TinyLlama-1.1B-Chat-v0.3-GGUF)**
- 3B (~4GB RAM) - **[Nous-Capybara-3B-V1.9](https://huggingface.co/afrideva/Nous-Capybara-3B-V1.9-GGUF)** (experimental)
- 7B (~8GB RAM) - **[OpenHermes 2.5 7B](https://huggingface.co/TheBloke/OpenHermes-2.5-Mistral-7B-GGUF)** (uses the "ChatML" instruct preset)
- 13B (~16GB RAM) - **[Xwin-MLewd 13B](https://huggingface.co/TheBloke/Xwin-MLewd-13B-v0.2-GGUF)**
- 70B (~64GB RAM) - **[Xwin-LM 70B](https://huggingface.co/TheBloke/Xwin-LM-70B-V0.1-GGUF)**

#### Recommended settings:
- **Deterministic** is the guide author's preference, and the choice of some users [such as WolframRavenwolf](https://old.reddit.com/r/LocalLLaMA/comments/17e446l/my_current_favorite_new_llms_synthia_v15_and/k68v3z7/).
- **Divine Intellect** or **LLaMA-Precise** may be preferred by some users.

* * *

### Chat and Roleplay (like CharacterAI, Replika, etc.) and Storywriting (like NovelAI)
*You can also use general-purpose assistants for RP and storytelling, but these models are better known for their focus on them.*
- 1.3B (~2GB RAM) - **[Metharme 1.3B](https://huggingface.co/Crataco/Metharme-1.3B-GGML)**
- 7B (~8GB RAM) - **[Dolphin 2.2.1 7B](https://huggingface.co/TheBloke/dolphin-2.2.1-mistral-7B-GGUF)** or **[OpenHermes 2.5 7B](https://huggingface.co/TheBloke/OpenHermes-2.5-Mistral-7B-GGUF)** (both use the "ChatML" instruct preset)
- 13B (~16GB RAM) - **[Tiefighter 13B](https://huggingface.co/KoboldAI/LLaMA2-13B-Tiefighter-GGUF)** or **[MythoMax 13B](https://huggingface.co/TheBloke/MythoMax-L2-13B-GGUF)**
- 20B (~20GB RAM) - **[MXLewd-L2 20B](https://huggingface.co/TheBloke/MXLewd-L2-20B-GGUF)**\*
- 70B (~64GB RAM) - **[lzlv 70B](https://huggingface.co/TheBloke/lzlv_70B-GGUF)** or **[Euryale 1.3 70B](https://huggingface.co/TheBloke/Euryale-1.3-L2-70B-GGUF)**

\* *This model is an unofficial 20B, often referred to as a "Frankenstein model" or "Frankenmerge". Its generations are unreliable compared to the 7B and 13B models, but some in the community prefer their vocabulary.*

#### Recommended settings:
*The only way to know how they influence the generations is to try them yourself. These descriptions are subjective.*
- **RecoveredRuins** is the guide author's preference for tweaking. It's the default selected by SillyTavern if it's connected to Kobold.
- **Storywriter (NovelAI)** feels safe, but boring. It is the official recommendation for Pygmalion 2.
- **Space Alien** and **Titanic** were popular options for MythoMax, but you don't get much variety in regenerated responses (especially with Titanic).

* * *

### Text Adventure (like AI Dungeon)
*These models are trained on human-written text adventures, making it generate Choose Your Own Adventure stories. They work best in "Adventure" mode (Kobold) or with the "Adventure" preset (SillyTavern).*
- 1.5B (~2GB RAM) - **[AI Dungeon 2 Classic](https://huggingface.co/Crataco/AI-Dungeon-2-Classic-GGML)** (via [KoboldCpp](https://github.com/LostRuins/koboldcpp))
- 7B (~8GB RAM) - **[Dans-AdventurousWinds-7B](https://huggingface.co/TheBloke/Dans-AdventurousWinds-7B-GGUF)**
- 13B (~16GB RAM) - **[Dans-CreepingSenseOfDoom-13B](https://huggingface.co/PocketDoc/Dans-CreepingSenseOfDoom-13b-gguf)** (uses the "Metharme" instruct preset) or **[Dans-RetroRodeo-13B](https://huggingface.co/PocketDoc/Dans-RetroRodeo-13b-gguf)** or **[Spring Dragon](https://huggingface.co/TheBloke/Spring-Dragon-GGUF)**

* * *

*Continue into [settings](settings.md) (outdated)...*
