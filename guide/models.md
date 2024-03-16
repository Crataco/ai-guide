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

- Transformers has been around for a while and is pretty much a universal standard for AI models, but their models are unoptimized for running on consumer hardware and use *way* more resources than necessary. Approximately, while the average 7B model under GGUF would require over 4GB of RAM, a 7B model under Transformers could require 16GB or more.

- GPTQ, Exllama, and etc. are other backends with their own quantized format, but they're only useful if you have a recent graphics card (GPU). You'd have the best luck with NVIDIA GPUs, but with AMD GPUs, your mileage may vary. This is the option recommended if you have a powerful enough GPU for the model you want to run, but this guide will not cover this option.

This guide will assume users chose GGUF and a frontend that supports it (like KoboldCpp, Oobabooga's Text Generation Web UI, Faraday, or LM Studio).

## Model recommendations
**Last updated:** March 11th, 2024

The following recommendations are based on online anecdotes, personal experience, WolframRavenwolf's LLM tests, and the reported "HellaSwag" (common sense reasoning) scores of models. It also shares how much RAM your computer should have to comfortably run the models at an average quantization level like "Q4_K_M".

If you do not have enough system RAM, but some VRAM to spare, you can split the model between your system RAM and video memory, which often goes by the term "GPU offloading".

Here are two more things to keep in mind:
- Most models work best when you follow a generation format. These are often called "instruct presets" or "prompt templates" and make it clear to the model when the user talks and when it's the AI's turn. Fortunately most frontends let you choose one, and they do the work for you behind the scenes. If you do not know which instruct preset to use, scroll down on the model's page and it will usually be under "prompt template" or similar.
- Settings influence the responses your models give you. A good place to start is to set "Min P" to 0.1 and "Temperature" to 1.0. Lowering Min P could give it more words to choose from, and raising the temperature will make it more likely it'll choose one of the less likely choices, which often translates to creative responses at the cost of some intelligence.

* * *

### General Use (like ChatGPT)
- Mini (~512MB RAM) - **[RWKV-5 World](https://huggingface.co/latestissue/rwkv-5-world-ggml-quantized)** or **[languagemodels](https://github.com/jncraton/languagemodels)**
- 1.1B (~2GB RAM) - **[TinyDolphin 2.8 1.1B](https://huggingface.co/dagbs/TinyDolphin-2.8-1.1b-GGUF)**
- 1.6B (~2GB RAM) - **[StableLM 2 Zephyr 1.6B](https://huggingface.co/second-state/stablelm-2-zephyr-1.6b-GGUF)**
- 3B (~4GB RAM) - **[Dolphin-2.6 Phi-2](https://huggingface.co/TheBloke/dolphin-2_6-phi-2-GGUF)**
- 7B (~8GB RAM) - **[Nous Hermes 2 Mistral 7B DPO](https://huggingface.co/Crataco/Nous-Hermes-2-Mistral-7B-DPO-imatrix-GGUF)**
- 10.7B (~10GB RAM) - **[Nous Hermes 2 SOLAR 10.7B](https://huggingface.co/TheBloke/Nous-Hermes-2-SOLAR-10.7B-GGUF)**
- 8x7B (~32GB RAM) - **[Nous Hermes 2 Mixtral 8x7B DPO](https://huggingface.co/mradermacher/Nous-Hermes-2-Mixtral-8x7B-DPO-i1-GGUF)** or **[Mixtral 8x7B Instruct v0.1](https://huggingface.co/mradermacher/Mixtral-8x7B-Instruct-v0.1-i1-GGUF)**

* * *

### Chat and Roleplay (like CharacterAI, Replika, etc.) and Storywriting (like NovelAI)
*You can also use general-purpose assistants for RP and storytelling, but these models are preferred for balancing creative prose with intelligence.*
- 7B (~8GB RAM) - **[Kunoichi-DPO-V2 7B](https://huggingface.co/brittlewis12/Kunoichi-DPO-v2-7B-GGUF)** (smaller versions available **[here](https://huggingface.co/kalomaze/Kunoichi-DPO-v2-7B-GGUF)**)
- 10.7B (~10GB RAM) - **[Fimbulvetr 11B v2](https://huggingface.co/mradermacher/Fimbulvetr-11B-v2-i1-GGUF)**
- 13B (~16GB RAM) - **[Psyfighter 2 13B](https://huggingface.co/KoboldAI/LLaMA2-13B-Psyfighter2-GGUF)**
- 8x7B (~32GB RAM) - **[BagelMIsteryTour-v2-8x7B](https://huggingface.co/ycros/BagelMIsteryTour-v2-8x7B-GGUF)**
- 70B (~64GB RAM) - **[MiquMaid-v2-70B-DPO-GGUF](https://huggingface.co/NeverSleep/MiquMaid-v2-70B-DPO-GGUF)** (smaller versions available **[here](https://huggingface.co/Kooten/MiquMaid-v2-70B-DPO-Imatrix-GGUF)**)
- 120B (~96GB RAM) - **[Goliath 120B](https://huggingface.co/TheBloke/goliath-120b-GGUF)**\*

\* *This model is an unofficial size, often called a "Frankenstein model" or "Frankenmerge". Its generations can be unreliable compared to models made with "official" sizes, but some in the community prefer them.*

* * *

### Text Adventure (like AI Dungeon)
*These models are trained on human-written text adventures, making it generate Choose Your Own Adventure stories. They work best in "Adventure" mode (Kobold) or with the "Adventure" preset (SillyTavern).*
- 1.5B (~2GB RAM) - **[AI Dungeon 2 Classic](https://huggingface.co/Crataco/AI-Dungeon-2-Classic-GGML)** (via [KoboldCpp](https://github.com/LostRuins/koboldcpp))
- 7B (~8GB RAM) - **[Dans-AdventurousWinds-Mk2-7B](https://huggingface.co/TheBloke/Dans-AdventurousWinds-Mk2-7B-GGUF)**
- 13B (~16GB RAM) - **[Dans-CreepingSenseOfDoom-13B](https://huggingface.co/PocketDoc/Dans-CreepingSenseOfDoom-13b-gguf)** or **[Dans-RetroRodeo-13B](https://huggingface.co/PocketDoc/Dans-RetroRodeo-13b-gguf)** or **[Spring Dragon](https://huggingface.co/TheBloke/Spring-Dragon-GGUF)**
