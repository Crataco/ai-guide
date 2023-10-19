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

Alternative sources for recommendations:
- [WolframRavenwolf's posts](https://old.reddit.com/r/LocalLLaMA/comments/178nf6i/mistral_llm_comparisontest_instruct_openorca/) (7B to 70B)
- [Ayumi's LLM Role Play & ERP Ranking](https://rentry.co/ayumi_erp_rating) (3B to 33B)

The following are the models the guide recommends, ranging from the smallest models to 13B, and the amount of RAM recommended for your computer to run them.

One important thing to keep in mind is that most models work best when you follow a generation format. These are often called "instruct presets" or "prompt templates". If you do not know which one to use, most models on this list (except Mistral, Holodeck, AI Dungeon Classic and Spring Dragon models) will work best with the Alpaca format.

* * *

### General-Purpose (like ChatGPT)
- Mini (~512MB RAM) - **[LaMini-LM](https://github.com/mbzuai-nlp/LaMini-LM#models) (via [languagemodels](https://github.com/jncraton/languagemodels))**
- 3B (~5GB RAM) - **[Marx 3B V2](https://huggingface.co/NikolayKozloff/Marx-3B-V2-GGUF#provided-files)**
- 7B (~8GB RAM) - **[Mistral 7B OpenOrca](https://huggingface.co/TheBloke/Mistral-7B-OpenOrca-GGUF)** or **[OpenHermes 7B](https://huggingface.co/TheBloke/OpenHermes-2-Mistral-7B-GGUF)** (both use the "ChatML" instruct preset)
- 13B (~12GB RAM) - **[Nous Hermes Llama 2 13B](https://huggingface.co/TheBloke/Nous-Hermes-Llama2-GGUF#provided-files)** (uncensored) or **[Vicuna 13B](https://huggingface.co/TheBloke/vicuna-13B-v1.5-GGUF)** (censored)

#### Recommended settings:
*The guide recommends "Divine Intellect" or "LLaMA-Precise" settings. The guide author uses "Deterministic".*

* * *

### Chat and Roleplay (like CharacterAI, Replika, etc.) / Storywriting (like NovelAI)
*You can also use general-purpose assistants for RP and storytelling, but these models are better known for their focus on them.*
- 1.3B (~2GB RAM) - **[Metharme 1.3B](https://huggingface.co/Crataco/Metharme-1.3B-GGML)**
- 7B (~8GB RAM) - **Same as in the "General Purpose" section. [Zarablend 7B](https://huggingface.co/TheBloke/Zarablend-L2-7B-GGUF) is worth a mention, but it's a little dated.**
- 13B (~16GB RAM) - **[MythoMax 13B](https://huggingface.co/TheBloke/MythoMax-L2-13B-GGUF)** or **[Mythalion 13B](https://huggingface.co/TheBloke/Mythalion-13B-GGUF)** or **[Holodeck 13B](https://huggingface.co/shadowsword/LLAMA2-13B-Holodeck-1-GGML_K)** (storywriting only)
- 20B (~20GB RAM) - **[MLewd-ReMM-L2-Chat 20B](https://huggingface.co/TheBloke/MLewd-ReMM-L2-Chat-20B-GGUF)**
- 70B (~64GB RAM) - **[Xwin 70B](TheBloke/Xwin-LM-70B-V0.1-GGUF)**

#### Model descriptions:
- ***MythoMax 13B** (as of writing) remains the most popular model for roleplay, and rightfully so. It's one of the best offline models for creative tasks, doing a good job at SFW and NSFW RP. Probably the best balance of creativity, coherency, and resource usage that you can get on a 16GB computer.*
- ***Zarablend 7B** is arguably the "MythoMax of 7B", which can run on devices that MythoMax can't.*
- ***Mythalion 13B** is a merge that can best be described as "combining MythoMax’s stability and intelligence with Pygmalion-2’s raw creative power." The guide author finds MythoMax more reliable while Mythalion has more creativity. A discussion of MythoMax and Mythalion can be found [here](https://old.reddit.com/r/SillyTavernAI/comments/16mz6tw/mythomax_and_its_popular_merge/).*
- ***MLewd-ReMM-L2-Chat 20B** is currently the guide author's favorite model. It sometimes feels less reliable than MythoMax, but has **very** colorful prose, and is heaven when compared with Mirostat settings.*
- ***XWin 70B** is a very demanding model that, in the author's testing, is also very intelligent, but lacks the colorful vocabulary present in other creativity-focused models.*
- ***Holodeck 13B** is one of the few contemporary models trained entirely on human-written stories, continuing the tradition of earlier models like Picard, Janeway, and Nerys. If you have used NovelAI before, the way you co-write with this model should be very familiar to you. It is meant to be used with Oobabooga's notebook mode or Kobold's story mode. It was also merged with MythoMax into a model called "HoloMax" [which can be found here](https://huggingface.co/KoboldAI/LLaMA2-13B-Holomax-GGUF).*

#### Recommended settings:
*These descriptions are subjective, so the only way to know how they influence the generations is to try them yourself.*
- ***Storywriter (NovelAI)** is the official recommendation for Pygmalion 2. The guide author considers this preset safe, but boring.*
- ***Space Alien** and **Titanic** are popular options for MythoMax, but regenerated responses may feel same-y. Start with these ones.*
- ***Shortwave** keeps the responses eventful, for better or worse.*
- ***Mirostat** is explained in-depth [here](https://github.com/ggerganov/llama.cpp/blob/master/examples/main/README.md#mirostat-sampling). For `tau`, a value between 4.0 and 8.0 is generally recommended. For `eta`, a value between 0.1 and 0.4 is generally recommended. The guide author's choice is a `tau` of 5.0 and an `eta` of 1.0.*

* * *

### Text Adventure (like AI Dungeon)
*These models are trained on human-written text adventures, making it generate Choose Your Own Adventure stories. They work best in "Adventure" mode (Kobold) or with the "Adventure" preset (SillyTavern).*
- 1.5B (~2GB RAM) - **[AI Dungeon 2 Classic 1.5B](https://huggingface.co/Crataco/AI-Dungeon-2-Classic-GGML)** (via [KoboldCpp](https://github.com/LostRuins/koboldcpp))
- 7B (~8GB RAM) - **[Dans-AdventurousWinds-7b](https://huggingface.co/TheBloke/Dans-AdventurousWinds-7B-GGUF)**
- 13B (~12GB RAM) - **[Dans-CreepingSenseOfDoom-13b](https://huggingface.co/PocketDoc/Dans-CreepingSenseOfDoom-13b-gguf)** (Metharme instruct preset) or **[Dans-RetroRodeo-13b](https://huggingface.co/PocketDoc/Dans-RetroRodeo-13b-gguf)** or **[Spring Dragon 13B](https://huggingface.co/TheBloke/Spring-Dragon-GGUF)**

#### Model descriptions:
- ***AI Dungeon 2 Classic** is based on the original open-source AI Dungeon 2 model, trained on [the infamous `text_adventures.txt`](https://gitgud.io/AuroraPurgatio/aurorapurgatio), before it became an online service and was subsequently renamed to "AI Dungeon". Since it is a non-LLaMA model (GPT-2), you will need to download your file of choice and load it in KoboldCpp.*
- ***Spring Dragon** is trained on the same dataset and intends to mimic AI Dungeon's 2020 "Dragon" experience. It works best with a frontend that has an "Adventure" mode, such as the Kobold series. If you are feeling nostalgic or just curious, this is worth a try.*
- ***Dan's Models** are trained on top of other curated text adventure datasets, modified from KoboldAI's early [Skein](https://huggingface.co/KoboldAI/GPT-J-6B-Skein) dataset.*

* * *

*Continue into [settings](settings.md) (outdated)...*
