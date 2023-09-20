![image](https://user-images.githubusercontent.com/55674863/230696024-98ce9e16-f558-4402-ac43-0e7f960c118c.png)

# Models
## What are models?

**TL;DR:** A model is your AI's brain.

A model, in this case, is a text generating AI that predicts the next text based on the patterns it learned from its training data. These are then released as base models (e.g. LLaMA, Llama 2) of specific sizes (e.g. 7B, 13B, 33B, 65B). They end up being jack-of-all-trades models that can generate a variety of topics, but require a bit of work to steer it into the right direction.

This is where finetunes come in, where the models are trained on further data. This gives it special knowledge and makes it easier to use it a specific way. An example would be Vicuna 7B, trained on ChatGPT logs to learn from (and mimic) ChatGPT. Or Pygmalion 7B, trained on CharacterAI logs to mimic CharacterAI.

There are also different ways to run them: enter backends.

## What is a backend?

Backends are different ways to store and use the AI. The most notable ones are Transformers, GGUF, and Exllama. **If you are new, go for GGUF.**

- Transformers has been around ever since the dawn of text generation, but it is not ideal for the average user. Transformers models take a lot of storage and memory. For example, LLaMA 7B is estimated to be around ~13 GB, and would require a computer with approximately 32 GB of RAM, give or take.

- GGUF (formerly GGML) versions can run on most computers thanks to their use of "quantization". For the sake of simplicity, you can consider quantization similar to lossy compression. The quantization levels you can choose range from "q2" (fastest, lightest, worst quality) to "q8" (slowest, heaviest, best quality), but a value of q5_K_M is recommended. [TheBloke](https://huggingface.co/TheBloke) converts many Transformers models into the GGUF format, and scrolling down his pages would bring you to [this chart](https://huggingface.co/TheBloke/Llama-2-7B-GGUF), telling you the size and maximum memory usage of each quantization. **This is the option recommended for most users.**

- GPTQ & Exllama are others that also support quantization, but they're only useful if you have a recent graphics card (GPU). You'd have the best luck with NVIDIA GPUs, but with AMD GPUs, your mileage may vary. This is the option recommended if you have a powerful enough GPU to hold the model you want to run, but this guide will not cover this option.

This guide will focus on GGUF versions of models whenever possible for maximum compatibility with existing systems.

## Model recommendations

Alternative sources for recommendations
- [WolframRavenwolf's New Model Comparison/Test](https://old.reddit.com/r/LocalLLaMA/comments/16kecsf/new_model_comparisontest_part_1_of_2_15_models/) (13B to 70B)
- [Ayumi's LLM Role Play & ERP Ranking](https://rentry.co/ayumi_erp_rating) (7B to 33B) 

The following are the models the guide recommends, ranging from the smallest models to 13B, and the amount of RAM recommended to run them. Larger models (such as LLaMA1 33B and Llama2 70B) exist, but are not covered due to the guide author's lack of extensive testing.

One important thing to keep in mind is that most models work best when you follow a generation format. These are often called "instruct presets" or "prompt templates". If you do not know which one to use, most models on this list (except Holodeck, AI Dungeon Classic and Spring Dragon) will work best with the Alpaca format.

* * *

### General-Purpose Assistant (like ChatGPT)
- Mini (~512MB RAM) - **[LaMini-LM](https://github.com/mbzuai-nlp/LaMini-LM#models) (via [languagemodels](https://github.com/jncraton/languagemodels))**
- 3B (~5GB RAM) - **[Marx 3B V2](https://huggingface.co/NikolayKozloff/Marx-3B-V2-GGUF#provided-files)**
- 7B (~8GB RAM) - **[Nous Hermes Llama 2 7B](https://huggingface.co/TheBloke/Nous-Hermes-Llama-2-7B-GGUF#provided-files)** (uncensored) or **[Vicuna 7B](https://huggingface.co/TheBloke/vicuna-7B-v1.5-GGUF)** (censored)
- 13B (~12GB RAM) - **[Nous Hermes Llama 2 13B](https://huggingface.co/TheBloke/Nous-Hermes-Llama2-GGUF#provided-files)** (uncensored) or **[Vicuna 13B](https://huggingface.co/TheBloke/vicuna-13B-v1.5-GGUF)** (censored)

#### Recommended settings:
*The guide recommends the LLaMA-Precise settings.*

* * *

### Roleplay (like CharacterAI, Replika, etc.) / Storywriting (like NovelAI)
*You can also use general-purpose assistants for RP and storytelling, but these ones specialize in the tasks.*
- 7B (~8GB RAM) - **[Zarablend 7B](https://huggingface.co/TheBloke/Zarablend-L2-7B-GGUF)**
- 13B (~12GB RAM) - **[MythoMax 13B](https://huggingface.co/TheBloke/MythoMax-L2-13B-GGUF)** or **[Mythalion 13B](https://huggingface.co/TheBloke/Mythalion-13B-GGUF)** or **[Holodeck 13B](https://huggingface.co/shadowsword/LLAMA2-13B-Holodeck-1-GGML_K)** (storywriting only)

#### Model descriptions:
- ***MythoMax 13B** is a very popular model merge. One of the best offline models for creative tasks, doing a good job at SFW and NSFW roleplay. Probably the best balance of creativity and coherency that you can get on an average Joe's computer. However, if you like living on the edge, a user has remade MythoMax with upgraded "ingredients": [the ReMM series](https://huggingface.co/models?sort=trending&search=remm+gguf). A popular alternative to MythoMax is **[Stheno](https://huggingface.co/TheBloke/Stheno-L2-13B-GGUF)**.*

- ***Mythalion 13B** is a merge that can best be described as "combining MythoMax’s stability and intelligence with Pygmalion-2’s raw creative power." The guide author finds MythoMax better at maintaining coherency but Mythalion better at prose.*

- ***Holodeck** is one of the few contemporary models trained _only_ on human-written stories, continuing the tradition of earlier models like Picard, Janeway, and Nerys. If you have used NovelAI before, the way you co-write with this model should be very familiar to you. It is meant to be used with Oobabooga's notebook mode or Kobold's story mode. It was also merged with MythoMax into a model called "HoloMax" which can be found [here](https://huggingface.co/KoboldAI/LLaMA2-13B-Holomax-GGML).*

- *Other models exist for 13B roleplay such as **[Pygmalion 2](https://huggingface.co/TheBloke/Pygmalion-2-13B-GGUF)** and the NSFW-oriented **[MLewdBoros](https://huggingface.co/TheBloke/MLewdBoros-L2-13B-GGUF)**.*

#### Recommended settings:
*These descriptions are subjective, so the only way to know how they influence the generations is to try them yourself.*
- ***Space Alien** and **Titanic** are popular options for MythoMax, but regenerated responses may feel same-y. Start with these ones.*
- ***Shortwave** keeps the responses eventful, for better or worse.*
- ***NovelAI Storywriter** tries to keep the conversation "safe", never deviating as much as the others.*
- ***Mirostat** is explained in-depth [here](https://github.com/ggerganov/llama.cpp/blob/master/examples/main/README.md#mirostat-sampling). For `tau`, a value between 4.0 and 8.0 is generally recommended. For `eta`, a value between 0.1 and 0.4 is generally recommended.*

* * *

### Adventure (like AI Dungeon)
*These models are relatively poorer quality due to being trained on AI Dungeon's [infamous dataset](https://gitgud.io/AuroraPurgatio/aurorapurgatio) and/or earlier models than LLaMA. If you are not seeking nostalgia, the guide recommends using an assistant or roleplay model and asking it to start a text adventure.*
- 1.5B (~2GB RAM) - **[AI Dungeon 2 Classic 1.5B](https://huggingface.co/Henk717/ai-dungeon2-classic-ggml)** (via [KoboldCpp](https://github.com/LostRuins/koboldcpp))
- 13B (~12GB RAM) - **[Spring Dragon 13B](https://huggingface.co/TheBloke/Spring-Dragon-GGUF)**

#### Model descriptions:
- ***AI Dungeon Classic** is based on the original open-source AI Dungeon 2 model before it went online-only and was renamed to "AI Dungeon". Since it is a non-LLaMA model (GPT-2), you will need to download `AI-Dungeon-2-Classic.bin` and load it in KoboldCpp.*
- ***Spring Dragon** intends to mimic AI Dungeon's 2020 "Dragon" experience. It works best with a frontend that has an "Adventure" mode, such as the Kobold series. If you are feeling nostalgic or just curious, this is worth a try.*

* * *

*Continue into [settings](settings.md) (outdated)...*
