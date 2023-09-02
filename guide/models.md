![image](https://user-images.githubusercontent.com/55674863/230696024-98ce9e16-f558-4402-ac43-0e7f960c118c.png)

# Models

### What are models?

**TL;DR:** A model is your AI's brain.

To elaborate, a model, in this case, is an AI that knows what text to generate because it was given a ton of text to learn from, usually from websites and books. These are then released as base models (e.g. LLaMA) of specific sizes (e.g. 7B). They end up being jack-of-all-trades models that can generate almost anything, but requires a bit of work to steer it into the right direction.

This is where finetunes come in, where people train the models on further data. This gives it special knowledge and makes it easier to use it a specific way. An example would be Vicuna 7B, trained on ChatGPT logs to learn from (and mimic) ChatGPT. Or Pygmalion 7B, trained on CharacterAI logs to mimic CharacterAI.

But there are different ways to run them: enter backends.

* * *

### What is a backend?

**TL;DR:** If you're new, just go for GGML.

Backends are different ways to store and use the AI. 

For example, LLaMA 7B is available for the [Transformers](https://huggingface.co/decapoda-research/llama-7b-hf), [GGML](https://huggingface.co/TheBloke/LLaMa-7B-GGML), and [GPTQ/Exllama](https://huggingface.co/camelids/llama-7b-int4-gptq-groupsize128-safetensors/tree/main) backends.

### What does that mean?

- Transformers has been around for a while, but it's not great for the average Joe. Models take a lot of storage and memory. For example, LLaMA 7B is about ~13 GB and would approximately take about 32GB of RAM.

- GGML versions, on the other hand, are quantized. This means that unlike Transformers, they take little storage and memory, at the cost of a small decrease in quality. There are different levels of quantization, but for LLaMA 7B, the most compatible quantization (q4_0) is available as a ~4 GB model which would take ~4-6 GB of RAM. They're useful if you just have an average computer.

- GPTQ & Exllama are others that also support quantization, but they're only useful if you have a recent graphics card (GPU). You'd have the best luck with NVIDIA GPUs, but with AMD GPUs, your mileage may vary.

This guide will point you to the GGML versions of models whenever possible.

* * *

### What model should I use?

*(For a better variety of models, see [here](https://rentry.org/ayumi_erp_rating), [here](https://rentry.co/ALLMRR), and [here](https://huggingface.co/TheBloke).)*

The guide recommends these models for specific tasks, but they are likely to change as the author hears about and tests many more.

***ATTENTION:** Llama 2 finetunes are reported to be smarter than LLaMA 1, but are experimental. They may be sensitive to different settings or have repetition problems, as discussed [here](https://old.reddit.com/r/LocalLLaMA/comments/155vy0k/llama_2_too_repetitive/), [here](https://old.reddit.com/r/LocalLLaMA/comments/15gp9fq/chronos13bv2_llama_2_roleplay_storywriting_and/junbr4x/), [here](https://old.reddit.com/r/LocalLLaMA/comments/15k07ba/anyone_else_is_getting_problems_with_repetition/), and [here](https://old.reddit.com/r/LocalLLaMA/comments/15pa5zd/i_think_im_ready_to_call_llama2_almost_unusable/). Being trained on GPT-4, most Llama 2 models also have "catchphrase words" you may see often, such as "after all," "remember," and "don't worry".*

### Assistant (ChatGPT)
*One more note: every model has their generations formatted differently and work best with those formats. These are often called "Presets" or "prompt templates".*
- **Nous-Hermes (Llama 2)** - [7B](https://huggingface.co/TheBloke/Nous-Hermes-Llama-2-7B-GGML) / [13B](https://huggingface.co/TheBloke/Nous-Hermes-Llama2-GGML) / [70B](https://huggingface.co/TheBloke/Nous-Hermes-Llama2-70B-GGML) - A pretty good "universal" model for both assistant tasks and SFW/NSFW storywriting/roleplay. An employee of Nous [recommends Redmond-Puffin over Nous-Hermes for roleplay tasks and multi-turn conversations](https://old.reddit.com/r/LocalLLaMA/comments/155wwrj/noushermesllama2_13b_released_beats_previous/jt20234/), though Nous-Hermes is still preferred by many users. A discussion of the two can be found [here](https://old.reddit.com/r/LocalLLaMA/comments/158j9r9/nous_hermes_llama2_vs_redmond_puffin_13b/).
- **RWKV-4 Raven** - [1.5B / 3B / 7B / 14B](https://huggingface.co/latestissue/rwkv-4-raven-ggml-quantized/tree/main) - Included here as an option for resource-constrained hardware. Can be used via [KoboldCpp](https://github.com/LostRuins/koboldcpp).
- **[LaMini](https://github.com/mbzuai-nlp/lamini-lm#models)** - Included here as an option for resource-constrained hardware. Can be used via [languagemodels](https://github.com/jncraton/languagemodels).

### Roleplay (CharacterAI, Replika, etc) / Storywriting (NovelAI)
- **MythoMax (Llama 2)** - [13B](https://huggingface.co/TheBloke/MythoMax-L2-13B-GGML) - A new merged model and the guide author's new primary for roleplay and story. Great at following character attributes and knows erotic language. Best used with the Alpaca preset. So far this is the closest you can get to an uncensored CharacterAI-esque experience on local hardware.
- **Zarablend (Llama 2)** - [7B](https://huggingface.co/zarakiquemparte/zarablend-l2-7b) - A new merged model and the guide author's go-to if they're unable to run MythoMax 13B.
- **Airoboros (Llama 2)** - [7B](https://huggingface.co/TheBloke/airoboros-l2-7b-gpt4-1.4.1-GGML) / [13B](https://huggingface.co/TheBloke/airoboros-l2-13B-gpt4-1.4.1-GGML) / [33B (LLaMA 1)](https://huggingface.co/TheBloke/airoboros-33B-gpt4-1.4-GGML) / [70B](https://huggingface.co/TheBloke/airoboros-l2-70B-gpt4-1.4.1-GGML) - Another model series the guide author's been testing. It's an *okay* choice for 7B and 13B users, but it's currently one of the best choices for 33B/70B users alongside [Airochronos 33B](https://huggingface.co/TheBloke/airochronos-33B-GGML). 1.4 and 1.4.1 were trained on older GPT-4 data, while m2.0 (continuation of 1.4) and 2.0 (from scratch) were trained on newer GPT-4 data (in case you didn't know, there's a rumor going around that GPT-4's response quality worsened). This guide links to the Llama 2 versions of 1.4/1.4.1.
- **Holodeck (Llama 2)** - [13B](https://huggingface.co/KoboldAI/LLAMA2-13B-Holodeck-1-GGML) - Storywriting only. It's one of the few contemporary models trained _only_ on stories, succeeding earlier models such as [Nerys](https://huggingface.co/KoboldAI/OPT-13B-Nerys-v2), [Janeway](https://huggingface.co/KoboldAI/GPT-J-6B-Janeway), and [Picard](https://huggingface.co/KoboldAI/GPT-Neo-2.7B-Picard). If you're a KoboldAI/NovelAI user, the way you use this model will be very familiar to you. It's meant to be used with Oobabooga's notebook interface or KoboldAI/KoboldCpp's story mode. It was recently merged with MythoMax into a model called "HoloMax" intended for co-writing, which can be found [here](https://huggingface.co/KoboldAI/LLaMA2-13B-Holomax-GGML).

### Adventure (AI Dungeon)
- **Spring Dragon (LLaMA 1)** - [13B](https://huggingface.co/TheBloke/Spring-Dragon-GGML) - If you're familiar with AI Dungeon, this is a model trained on top of the same dataset, intended to replicate AI Dungeon's 2020 "Dragon" experience, and works best with KoboldAI/KoboldCpp's "Adventure" mode. If you're feeling nostalgic or just curious, this is worth a try.
- **AI Dungeon Classic (GPT-2)** - [1.5B](https://huggingface.co/Henk717/ai-dungeon2-classic-ggml) - Based on the original open-source AI Dungeon 2 model before it went online-only and was renamed to "AI Dungeon". Works perfectly in KoboldCpp.
  

*Continue into [settings](settings.md)...*
