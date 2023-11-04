![image](https://user-images.githubusercontent.com/55674863/230696024-98ce9e16-f558-4402-ac43-0e7f960c118c.png)

# Models
## What are models?

**TL;DR:** A model is your AI's brain.

A model, in this case, is a text generating AI that predicts the next text based on the patterns it learned from its training data. These are then released as base models (e.g. LLaMA, Llama 2) of specific sizes (e.g. 7B, 13B, 33B, 65B). They end up being jack-of-all-trades models that can generate a variety of topics, but require a bit of work to steer it into the right direction.

This is where finetunes come in, where the models are trained on further data. This gives it special knowledge and makes it easier to use it a specific way. An example would be Vicuna 7B, trained on ChatGPT logs to learn from (and mimic) ChatGPT. Or Pygmalion 7B, trained on CharacterAI logs to mimic CharacterAI.

There are also different ways to run them: enter backends.

## What is a backend?

Backends are different ways to store and use the AI model. The most notable ones are Transformers, GGUF, and Exllama. **The option recommended for most users is GGUF.**

- GGUF (formerly GGML) versions can run on most computers thanks to their use of "quantization". For the sake of simplicity, you can consider quantization a way to cut down on size at the cost of slight quality loss. It has "levels" that range from "q2" (lightest, worst quality) to "q8" (heaviest, best quality), but a value of q5_K_M is ideal for most situations. [TheBloke](https://huggingface.co/TheBloke) converts many Transformers models into the GGUF format, and scrolling down his pages would bring you to [this chart](https://huggingface.co/TheBloke/Llama-2-7B-GGUF#provided-files), telling you the size and maximum memory usage of each level.

- Transformers has been around for a while, but it is not ideal for the average user. Transformers models take a lot of storage and memory. For example, LLaMA 7B is estimated to be around ~13 GB, and would require a computer with approximately 32 GB of RAM, give or take.

- GPTQ, Exllama, and etc. are other backends with their own quantized format, but they're only useful if you have a recent graphics card (GPU). You'd have the best luck with NVIDIA GPUs, but with AMD GPUs, your mileage may vary. This is the option recommended if you have a powerful enough GPU to hold the model you want to run, but this guide will not cover this option.

This guide will focus on GGUF versions of models, which most computers can run.

## Model recommendations

Sources:
- [WolframRavenwolf's 7B-70B General Test](https://old.reddit.com/r/LocalLLaMA/comments/17fhp9k/huge_llm_comparisontest_39_models_tested_7b70b/) (2023-10-24)
- [WolframRavenwolf's 7B-20B Roleplay Test](https://old.reddit.com/r/LocalLLaMA/comments/17kpyd2/huge_llm_comparisontest_part_ii_7b20b_roleplay/) (2023-10-31)

The following are the models the guide recommends, and the amount of RAM recommended for your computer to run them. If you do not have enough system RAM, but some VRAM to spare, you can "offload" the model's "layers," splitting the model between your system RAM and video memory.

One important thing to keep in mind is that most models work best when you follow a generation format. These are often called "instruct presets" or "prompt templates". If you do not know which one to use, most models on this list will use the Alpaca format unless specified otherwise.

* * *

### General-Purpose (like ChatGPT)
- Mini (~512MB RAM) - **[LaMini-LM](https://github.com/mbzuai-nlp/LaMini-LM#models)** (via [languagemodels](https://github.com/jncraton/languagemodels))
- 1.1B (~2GB RAM) - **[TinyLlama 1.1B Chat v0.3](https://huggingface.co/TheBloke/TinyLlama-1.1B-Chat-v0.3-GGUF)**
- 3B (~5GB RAM) - **[Marx 3B V2](https://huggingface.co/NikolayKozloff/Marx-3B-V2-GGUF#provided-files)**
- 7B (~8GB RAM) - **[OpenHermes 2.5 7B](https://huggingface.co/TheBloke/OpenHermes-2.5-Mistral-7B-GGUF)** (uses the "ChatML" instruct preset)
- 13B (~12GB RAM) - **[Xwin-MLewd 13B V0.2](https://huggingface.co/TheBloke/Xwin-MLewd-13B-v0.2-GGUF)**
- 70B (~64GB RAM) - **[Xwin-LM 70B V0.1](https://huggingface.co/TheBloke/Xwin-LM-70B-V0.1-GGUF)**

#### Recommended settings:
*The guide author uses "Deterministic". Some users may prefer "Divine Intellect" or "LLaMA-Precise" presets.*

* * *

### Chat and Roleplay (like CharacterAI, Replika, etc.) and Storywriting (like NovelAI)
*You can also use general-purpose assistants for RP and storytelling, but these models are better known for their focus on them.*
- 1.3B (~2GB RAM) - **[Metharme 1.3B](https://huggingface.co/Crataco/Metharme-1.3B-GGML)**
- 7B (~8GB RAM) - **[OpenHermes 2.5 7B](https://huggingface.co/TheBloke/OpenHermes-2-Mistral-7B-GGUF)**
- 13B (~16GB RAM) - **[Tiefighter 13B](https://huggingface.co/KoboldAI/LLaMA2-13B-Tiefighter-GGUF)** (newer, promising) or **[MythoMax 13B](https://huggingface.co/TheBloke/MythoMax-L2-13B-GGUF)** (older, well-known)
- 20B (~20GB RAM) - **[MXLewd-L2 20B](https://huggingface.co/TheBloke/MXLewd-L2-20B-GGUF)**\*
- 70B (~64GB RAM) - **[lzlv 70B](https://huggingface.co/TheBloke/lzlv_70B-GGUF)**

\* *This model is an unofficial 20B, often referred to as a "Frankenstein model" or "Frankenmerge". Its generations are unreliable compared to the 7B and 13B models, but some in the community prefer them for prose.*

#### Recommended settings:
*The only way to know how they influence the generations is to try them yourself. These descriptions are subjective.*
- **RecoveredRuins** is the guide author's preference for tweaking. It's the default selected by SillyTavern if it's connected to Kobold.
- **Storywriter (NovelAI)** feels safe, but boring. It is the official recommendation for Pygmalion 2.
- **Space Alien** and **Titanic** were popular options for MythoMax, but regenerated responses may feel same-y.

* * *

### Text Adventure (like AI Dungeon)
*These models are trained on human-written text adventures, making it generate Choose Your Own Adventure stories. They work best in "Adventure" mode (Kobold) or with the "Adventure" preset (SillyTavern).*
- 1.5B (~2GB RAM) - **[AI Dungeon 2 Classic 1.5B](https://huggingface.co/Crataco/AI-Dungeon-2-Classic-GGML)** (via [KoboldCpp](https://github.com/LostRuins/koboldcpp))
- 7B (~8GB RAM) - **[Dans-AdventurousWinds-7b](https://huggingface.co/TheBloke/Dans-AdventurousWinds-7B-GGUF)**
- 13B (~12GB RAM) - **[Dans-CreepingSenseOfDoom-13b](https://huggingface.co/PocketDoc/Dans-CreepingSenseOfDoom-13b-gguf)** (uses the "Metharme" instruct preset) or **[Dans-RetroRodeo-13b](https://huggingface.co/PocketDoc/Dans-RetroRodeo-13b-gguf)** or **[Spring Dragon 13B](https://huggingface.co/TheBloke/Spring-Dragon-GGUF)**

* * *

*Continue into [settings](settings.md) (outdated)...*
