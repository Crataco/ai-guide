![image](https://user-images.githubusercontent.com/55674863/230696024-98ce9e16-f558-4402-ac43-0e7f960c118c.png)

# Models

### What are models?

**TL;DR:** A model is your AI's brain.

To elaborate, a model is an AI that learned how to generate text because it was given a ton of text to learn from, usually from websites and books. These are then released as base models (e.g. LLaMA) of specific sizes (e.g. 7B). They end up being jack-of-all-trades models that can generate almost anything, but requires a bit of work to steer it into the right direction.

This is where finetunes come in, where people train the models on further data. This gives it special knowledge and makes it easier to use it a specific way. An example would be Vicuna 7B, trained on ChatGPT logs to learn from (and mimic) ChatGPT. Or Pygmalion 7B, trained on CharacterAI logs to mimic CharacterAI.

But you need to learn about backends to understand the best model for your hardware.

* * *

### What is a backend?

**TL;DR:** If you're new, just go for GGML.

Backends are different ways to store and use the AI. 

For example, LLaMA 7B is available for the [Transformers](https://huggingface.co/decapoda-research/llama-7b-hf), [GGML](https://huggingface.co/TheBloke/LLaMa-7B-GGML), and [GPTQ/Exllama](https://huggingface.co/camelids/llama-7b-int4-gptq-groupsize128-safetensors/tree/main) backends.

### What does this mean?

- Transformer models are very well-known, but are unoptimized for the average Joe's computers. Models take a lot of storage and memory. For example, LLaMA 7B is about ~13 GB and would approximately take about 32GB of RAM.

- GGML versions, on the other hand, are quantized. This means that unlike Transformers, they take little storage and memory, at the cost of a small decrease in quality. There are different levels of quantization, but the most compatible (q4_0) is available as a ~4 GB model which would take ~4-6 GB of RAM. They're useful if you just have an average computer.

- GPTQ & Exllama are others that also support quantization, but they're only useful if you have a recent graphics card (GPU). You'd have the best luck with NVIDIA GPUs, but with AMD GPUs, your mileage may vary.

This guide will point you to the GGML versions of models whenever possible.

* * *

### What model should I use?

*(For more models, see [here](https://rentry.co/ALLMRR) and [here](https://huggingface.co/TheBloke))*

The guide recommends these models, listed in order of the author's preference and experience using them. Being low on the list doesn't make the models bad, they might even be better for your use case than the higher models. In that case, it's not bad to give them a test if you have the resources, space, and bandwidth to spare.

Also, models are considered "unrestricted" if they don't refuse most requests. They're "restricted" if they refuse most of the same inputs ChatGPT does.

***ATTENTION:** As of August 3rd, 2023, Llama 2 models are very new and experimental. Some may be sensitive to different settings or have repetition problems, as discussed [here](https://old.reddit.com/r/LocalLLaMA/comments/155vy0k/llama_2_too_repetitive/), [here](https://old.reddit.com/r/LocalLLaMA/comments/15gp9fq/chronos13bv2_llama_2_roleplay_storywriting_and/junbr4x/), and [here](https://old.reddit.com/r/LocalLLaMA/comments/15k07ba/anyone_else_is_getting_problems_with_repetition/).*

#### Assistant (like ChatGPT)
*These are "instruct" models, like ChatGPT. Keep in mind that every instruct model has its own "prompt template." You will need to set them in your frontend to get the best responses out of your models. In Oobabooga they're referred to as "instruction templates" and in SillyTavern they go by "Presets" in the formatting tab. [TheBloke usually covers them](https://huggingface.co/TheBloke/guanaco-7B-GGML#prompt-template-guanaco). SillyTavern added a roleplay preset based on Alpaca's template which could give better results.*

- **Nous-Hermes (Llama 2)**\* - [7B](https://huggingface.co/TheBloke/Nous-Hermes-Llama-2-7B-GGML) / [13B](https://huggingface.co/TheBloke/Nous-Hermes-Llama2-GGML) - Guide author's primary choice as an assistant, secondary as a roleplaying and storywriting model. The guide author hasn't tested 7B, but notices 13B is smarter than most LLaMA 1 13B finetunes, following the prompt better. Though it feels less natural and gets into the habit of repeating words like "after all" and "remember", so get ready to edit some chat messages to steer it back on track. The model is an assistant by default and refuses to answer in some _extreme_ edge-cases, but it can still be used for erotic roleplay and storywriting due to its training data. The guide considers this model unrestricted and one of the best models for 13B users, quite possibly great for 7B too.
- **Wizard-Vicuna Uncensored (LLaMA 1)** - [7B](https://huggingface.co/TheBloke/Wizard-Vicuna-7B-Uncensored-GGML) / [13B](https://huggingface.co/TheBloke/Wizard-Vicuna-13B-Uncensored-GGML) / [30B](https://huggingface.co/TheBloke/Wizard-Vicuna-30B-Uncensored-GGML) - A very well-known, widely-received model series which works well as an unrestricted assistant and for roleplay, based on [this model](https://github.com/melodysdreamj/WizardVicunaLM). The guide believes this to be one of the best options for 7B and 30B users.
- **Vicuna (LLaMA 1)** - [7B](https://huggingface.co/TheBloke/vicuna-7B-v1.3-GGML) / [13B](https://huggingface.co/TheBloke/vicuna-13b-v1.3.0-GGML) / [33B](https://huggingface.co/TheBloke/vicuna-33B-GGML) - Probably the most popular assistant model. It's a restricted model, but probably the best option if you want a local AI that replicates the free ChatGPT experience. There are Llama 2 versions: [7B](https://huggingface.co/TheBloke/vicuna-7B-v1.5-GGML) / [13B](https://huggingface.co/TheBloke/vicuna-13B-v1.5-GGML).
- **RWKV-4 Raven** - [1.5B / 3B / 7B / 14B](https://huggingface.co/BlinkDL/rwkv-4-raven) - Included here as an option for resource-constrained hardware. GGML conversions (which work with KoboldCpp) can be found [here](https://huggingface.co/latestissue/rwkv-4-raven-ggml-quantized/tree/main).
- **[LaMini](https://github.com/mbzuai-nlp/lamini-lm#models)** - Included here as an option for resource-constrained hardware.

\* *An employee of Nous [recommends Redmond-Puffin 13B over Nous-Hermes 13B (Llama 2) for roleplay tasks and multi-turn conversations](https://old.reddit.com/r/LocalLLaMA/comments/155wwrj/noushermesllama2_13b_released_beats_previous/jt20234/), though Nous-Hermes is still preferred by many users. A discussion of the two can be found [here](https://old.reddit.com/r/LocalLLaMA/comments/158j9r9/nous_hermes_llama2_vs_redmond_puffin_13b/).*

#### Roleplay (like CharacterAI, Replika, etc) / Storywriting (like NovelAI)
*These are also instruct models, but their roleplaying and storywriting performance stands out, so they have their own category. If you want to ask it to generate a story, it can do that. If you want to co-write with it, it can do that too -- try Oobabooga's notebook interface or Kobold's story mode.*
- **MythoMax (Llama 2)** - [13B](https://huggingface.co/TheBloke/MythoMax-L2-13B-GGML) - A new merged model and guide author's new primary for roleplay and story. The guide author finds this updated model really fun to use for both chatting and storywriting. It feels like a more creative alternative to Nous-Hermes, and even understood [the "internal thoughts" trick](https://rentry.co/kingbri-chara-guide#sillytavern) without much additional prompting.
- **Nous-Hermes (Llama 2)** - [7B](https://huggingface.co/TheBloke/Nous-Hermes-Llama-2-7B-GGML) / [13B](https://huggingface.co/TheBloke/Nous-Hermes-Llama2-GGML) - See above.
- **MythoLogic (LLaMA 1)** - [13B](https://huggingface.co/TheBloke/MythoLogic-13B-GGML) - While it's an instruct model, the guide author has tested 13B and found it great at roleplaying and storywriting, though not as good at following the prompt as Nous-Hermes 2. There are Llama 2 versions: [7B](https://huggingface.co/TheBloke/MythoLogic-Mini-7B-GGML) / [13B](https://huggingface.co/TheBloke/MythoLogic-L2-13B-GGML).
- **Chronos-Hermes 13B (LLaMA 1)** - [13B](https://huggingface.co/TheBloke/chronos-hermes-13B-GGML) - A model that's a merge of [Chronos](https://huggingface.co/TheBloke/chronos-13B-GGML) and Nous-Hermes (LLaMA 1). It tries to keep the great prose of Chronos but with the reasoning/logic and instruction-following capability of Nous-Hermes. Still used and recommended by some users, and the guide author even uses it from time to time. There's a Llama 2 version [here](https://huggingface.co/TheBloke/Chronos-Hermes-13B-v2-GGML).
- **Airoboros-GPT4 (LLaMA 1)** - [7B](https://huggingface.co/TheBloke/airoboros-7B-gpt4-1.4-GGML) / [13B](https://huggingface.co/TheBloke/airoboros-13B-gpt4-1.4-GGML) / [33B](https://huggingface.co/TheBloke/airoboros-33B-gpt4-1.4-GGML) / [65B](https://huggingface.co/TheBloke/airoboros-65B-gpt4-1.4-GGML) - Airoboros, while being an assistant model, doubles as a good model for roleplaying and chatting, in which [it's preferred](https://old.reddit.com/r/LocalLLaMA/comments/14n1p74/airoboros_14_family_of_models/jqa5vw5/). However, some users report the model being ["too nice"](https://old.reddit.com/r/LocalLLaMA/comments/14l1d48/the_best_13b_model_for_rolepay/) and the guide author recalls hearing that Airoboros isn't worth it until 33B/65B. The model is about as unrestricted as the previous three, and is similarly a great model for 7B, 30B, and 65B users. There are Llama 2 versions: [7B](https://huggingface.co/TheBloke/airoboros-l2-7B-gpt4-2.0-GGML) / [13B](https://huggingface.co/TheBloke/airoboros-l2-13b-gpt4-2.0-GGML) / [70B](https://huggingface.co/TheBloke/airoboros-l2-70B-GPT4-2.0-GGML).

#### Special
*These models are here because they take a more classic approach. They aren't meant to be used as "instruct" models.*
- **Holodeck (Llama 2)** - [13B](https://huggingface.co/KoboldAI/LLAMA2-13B-Holodeck-1-GGML) - Storywriting only. It's one of the few contemporary models trained _only_ on stories, succeeding earlier models such as [Nerys](https://huggingface.co/KoboldAI/OPT-13B-Nerys-v2), [Janeway](https://huggingface.co/KoboldAI/GPT-J-6B-Janeway), and [Picard](https://huggingface.co/KoboldAI/GPT-Neo-2.7B-Picard). If you're a classic NovelAI user, the way you use this model may be very familiar to you, and is meant to be used with Oobabooga's notebook interface or KoboldAI/KoboldCpp's story mode.
- **Spring Dragon (LLaMA 1)** - [13B](https://huggingface.co/TheBloke/Spring-Dragon-GGML) - If you're familiar with AI Dungeon, this is a model trained on top of the same dataset, intended to rival AI Dungeon's "Dragon" model from 2020, and works best with Kobold's "Adventure" mode. If you're feeling nostalgic or just curious, this is worth a try!

*Continue into [settings](settings.md)...*
