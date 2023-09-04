![image](https://user-images.githubusercontent.com/55674863/230696024-98ce9e16-f558-4402-ac43-0e7f960c118c.png)

# Models

### What are models?

**TL;DR:** A model is your AI's brain.

To elaborate, a model, in this case, is an AI that knows what text to generate because it was given a ton of text to learn from, usually from websites and books. These are then released as base models (e.g. LLaMA) of specific sizes (e.g. 7B). They end up being jack-of-all-trades models that can generate almost anything, but requires a bit of work to steer it into the right direction.

This is where finetunes come in, where people train the models on further data. This gives it special knowledge and makes it easier to use it a specific way. An example would be Vicuna 7B, trained on ChatGPT logs to learn from (and mimic) ChatGPT. Or Pygmalion 7B, trained on CharacterAI logs to mimic CharacterAI.

But there are different ways to run them: enter backends.

* * *

### What is a backend?

**TL;DR:** If you're new, just go for GGUF / GGML.

Backends are different ways to store and use the AI. 

For example, LLaMA 7B is available for the [Transformers](https://huggingface.co/decapoda-research/llama-7b-hf), [GGML](https://huggingface.co/TheBloke/LLaMa-7B-GGML), and [GPTQ/Exllama](https://huggingface.co/camelids/llama-7b-int4-gptq-groupsize128-safetensors/tree/main) backends.

### What does that mean?

- Transformers has been around for a while, but it's not great for the average Joe. Models take a lot of storage and memory. For example, LLaMA 7B is about ~13 GB and would approximately take about 32GB of RAM.

- GGUF (formerly GGML) versions, on the other hand, are quantized. This means that unlike Transformers, they take little storage and memory, at the cost of a small decrease in quality. There are different levels of quantization, but for LLaMA 7B, the most compatible quantization (q4_0) is available as a ~4 GB model which would take ~4-6 GB of RAM. They're useful if you just have an average computer.

- GPTQ & Exllama are others that also support quantization, but they're only useful if you have a recent graphics card (GPU). You'd have the best luck with NVIDIA GPUs, but with AMD GPUs, your mileage may vary.

This guide will point you to the GGML versions of models whenever possible.

* * *

### Model recommendations

These are the models the guide author recommends for specific tasks. Most models have their generations formatted differently, and work best when generations follow those formats. These are often called "instruct presets" or "prompt templates".

Also, Llama 2 models are better than LLaMA 1, but occasionally have their own repetition issues. [[1]](https://old.reddit.com/r/LocalLLaMA/comments/155vy0k/llama_2_too_repetitive/)[[2]](https://old.reddit.com/r/LocalLLaMA/comments/15gp9fq/chronos13bv2_llama_2_roleplay_storywriting_and/junbr4x/)[[3]](https://old.reddit.com/r/LocalLLaMA/comments/15k07ba/anyone_else_is_getting_problems_with_repetition/)[[4]](https://old.reddit.com/r/LocalLLaMA/comments/15pa5zd/i_think_im_ready_to_call_llama2_almost_unusable/)

#### Assistant (ChatGPT)
- **Nous-Hermes (Llama 2)** - [7B](https://huggingface.co/TheBloke/Nous-Hermes-Llama-2-7B-GGML) / [13B](https://huggingface.co/TheBloke/Nous-Hermes-Llama2-GGML) / [70B](https://huggingface.co/TheBloke/Nous-Hermes-Llama2-70B-GGML) - A pretty good "universal" model for both assistant tasks and SFW/NSFW storywriting/roleplay. It wasn't trained on multi-turn conversations, so you may need to hold its hand a bit at first. [Redmond-Puffin has been recommended by an employee over Nous-Hermes](https://old.reddit.com/r/LocalLLaMA/comments/155wwrj/noushermesllama2_13b_released_beats_previous/jt20234/), though Nous-Hermes is still preferred by many users. A discussion of the two can be found [here](https://old.reddit.com/r/LocalLLaMA/comments/158j9r9/nous_hermes_llama2_vs_redmond_puffin_13b/).

#### Roleplay (CharacterAI, Replika, etc) / Storywriting (NovelAI)
*If you're using SillyTavern, you'll have good results with the Alpaca instruct preset, but if you prefer lengthier responses, the simple-proxy-for-tavern instruct preset is great.*
- **MythoMax (Llama 2)** - [13B](https://huggingface.co/TheBloke/MythoMax-L2-13B-GGML) - One of the best offline CharacterAI-like models. Probably the best balance of creativity and coherency that you can get on your computer.
- **Stheno (Llama 2)** - [13B](https://huggingface.co/TheBloke/Stheno-L2-13B-GGUF) - A new model merge rivaling MythoMax.
- **Zarablend (Llama 2)** - [7B](https://huggingface.co/TheBloke/Zarablend-L2-7B-GGML) - A great model if you can't run MythoMax and Stheno because you lack the hardware to do so.
- **Airoboros (Llama 2)** - [7B](https://huggingface.co/TheBloke/Airoboros-L2-7B-2.1-GGUF) / [13B](https://huggingface.co/TheBloke/Airoboros-L2-13B-2.1-GGUF) / [33B (LLaMA 1)](https://huggingface.co/TheBloke/Airoboros-33B-2.1-GGUF) / [70B](https://huggingface.co/TheBloke/Airoboros-L2-70B-2.1-GGUF) - For comfortable use, 33B requires about 32GB RAM and 70B requires about 64GB RAM. If you have a supported GPU, you can split the model between the RAM and GPU VRAM, and you can use smaller quantizations such as q2 and q3 to lessen the hardware requirements.
- **Holodeck (Llama 2)** - [13B](https://huggingface.co/KoboldAI/LLAMA2-13B-Holodeck-1-GGML) - Storywriting only. It's one of the few contemporary models trained _only_ on stories. If you've used NovelAI before, the way you interact with this model will be very familiar. It's meant to be used with Oobabooga's notebook interface or Kobold's story mode. It was also merged with MythoMax into a model called "HoloMax" intended for co-writing, which can be found [here](https://huggingface.co/KoboldAI/LLaMA2-13B-Holomax-GGML).

#### Adventure (AI Dungeon)
- **Spring Dragon (LLaMA 1)** - [13B](https://huggingface.co/TheBloke/Spring-Dragon-GGML) - If you're familiar with AI Dungeon, this is a model trained on top of the same dataset, intended to replicate AI Dungeon's 2020 "Dragon" experience, and works best with KoboldAI/KoboldCpp's "Adventure" mode. If you're feeling nostalgic or just curious, this is worth a try.
- **AI Dungeon Classic (GPT-2)** - [1.5B](https://huggingface.co/Henk717/ai-dungeon2-classic-ggml) - Based on the original open-source AI Dungeon 2 model before it went online-only and was renamed to "AI Dungeon". Works perfectly in KoboldCpp.

#### Low-low-end Models
- **RWKV-4 Raven** - [1.5B / 3B / 7B / 14B](https://huggingface.co/latestissue/rwkv-4-raven-ggml-quantized/tree/main) - Assistant model. Can be used via [KoboldCpp](https://github.com/LostRuins/koboldcpp).
- **[LaMini](https://github.com/mbzuai-nlp/lamini-lm#models)** - Assistant model. Can be used via [languagemodels](https://github.com/jncraton/languagemodels).

*Continue into [settings](settings.md)...*
