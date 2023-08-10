![image](https://user-images.githubusercontent.com/55674863/230696024-98ce9e16-f558-4402-ac43-0e7f960c118c.png)

# Models

### What are models?

**TL;DR:** A model is your AI's brain.

To be more specific: a model is an AI that learned how to generate text because it was given a ton of text to learn from, usually from websites and books. They are then released as base models (think LLaMA 7B), a jack-of-all-trades model that can generate almost anything, but requires a bit of work to steer it into the right direction.

This is where finetunes come in, where people train the models on further data. This gives it specalized knowledge and makes it easier to use it a specific way. An example would be Vicuna 7B, trained on ChatGPT logs to learn from (and mimic) ChatGPT.

But you can't run a model without a backend.

* * *

### What is a backend?

Backends are different ways to store and use the AI. 

For example, LLaMA 7B is available for the [Transformers](https://huggingface.co/decapoda-research/llama-7b-hf), [GGML](https://huggingface.co/TheBloke/LLaMa-7B-GGML), and [GPTQ/Exllama](https://huggingface.co/camelids/llama-7b-int4-gptq-groupsize128-safetensors/tree/main) backends.

### What does this mean?

- Transformer models are very well-known, but are unoptimized for the average Joe's computers. Models take a lot of storage and memory. For example, LLaMA 7B is about ~13 GB and (I estimate) would take about 32GB of RAM.

- GGML versions, on the other hand, are quantized. Think of it like file compression: unlike Transformers, they take little storage and memory, at the cost of a small decrease in quality. There are different levels of quantization, and the most compatible -- q4_0 -- is available as a ~4 GB model which would take about 4-6 GB of RAM. They're useful if you just have an average computer.

- GPTQ & Exllama are others that also support quantization, but they're only useful if you have a GPU that can take advantage of them. You'd have the best luck with NVIDIA GPUs, but with AMD GPUs, your mileage may vary.

This guide will link to the GGML versions of models whenever possible. The easiest way to get them running is to download [KoboldCpp](https://github.com/LostRuins/koboldcpp/releases) and your model of choice, then run the executable you've downloaded and select the model from your menu.

* * *

### What model should I use?

First of all, this guide recommends that you:
1. See what people are up to on [r/LocalLLaMA](https://old.reddit.com/r/LocalLLaMA) and what new models are added to [its wiki](https://old.reddit.com/r/LocalLLaMA/wiki/models).
2. Read TheBloke's RAM usage graphs to see what level of quantization (q2, q3, q4, q5, q6) you should get for a [7B model](https://huggingface.co/TheBloke/guanaco-7B-GGML#provided-files), [13B model](https://huggingface.co/TheBloke/guanaco-13B-GGML#provided-files), and others, depending on how much system memory you have. The higher the number, the better the model, but also the more demanding it'll be.
3. (Roleplay / CAI refugees) Check out model benchmarks such as [ALLMRR](https://rentry.co/ALLMRR) and [Ayumi ERP](https://rentry.co/ayumi_erp_rating). While you're at it, feel free to grab a character from [Chub.ai](https://www.chub.ai/) (NSFW warning) to use for Oobabooga, Tavern, or SillyTavern.

Here are some of the guide's recommended finetunes, listed in order of the author's preference and experience using them. Being low on the list doesn't make the models bad, they might even be better for your use case than the higher models. In that case, it's not bad to give them a test if you have the resources, space, and bandwidth to spare.

***ATTENTION:** As of August 3rd, 2023, Llama 2 models are very new and experimental. Some may be sensitive to different settings or have repetition problems, as discussed [here](https://old.reddit.com/r/LocalLLaMA/comments/155vy0k/llama_2_too_repetitive/), [here](https://old.reddit.com/r/LocalLLaMA/comments/15gp9fq/chronos13bv2_llama_2_roleplay_storywriting_and/junbr4x/), and [here](https://old.reddit.com/r/LocalLLaMA/comments/15k07ba/anyone_else_is_getting_problems_with_repetition/).*

#### Instruct / Assistant (like ChatGPT)
*Keep in mind that every instruct model has its own "prompt template." You will need to set them in your frontend to get the best responses out of your models. In Oobabooga they're referred to as "instruction templates" and in SillyTavern they go by "Presets" in the formatting tab. [TheBloke usually covers them](https://huggingface.co/TheBloke/guanaco-7B-GGML#prompt-template-guanaco).*

*Models are "unrestricted" if they don't refuse most requests. They're "restricted" if they refuse most of the same inputs ChatGPT does.*
- **Nous-Hermes (Llama 2)**\* - [7B](https://huggingface.co/TheBloke/Nous-Hermes-Llama-2-7B-GGML) / [13B](https://huggingface.co/TheBloke/Nous-Hermes-Llama2-GGML) - Guide author's primary choice as an assistant _and_ for roleplaying. The guide author hasn't tested 7B, but feels like 13B is smarter than most LLaMA 1 13B finetunes, following the prompt better, though at the cost of feeling less natural and repeating words like "after all" and "remember", so get ready to edit some chat messages to steer it back on track. The model is an assistant by default and refuses to answer in some _extreme_ edge-cases, but it can still be used for erotic roleplay and storywriting due to its training data. The guide considers this model unrestricted and one of the best models for 13B users, quite possibly great for 7B too.
- **Wizard-Vicuna Uncensored** - [7B](https://huggingface.co/TheBloke/Wizard-Vicuna-7B-Uncensored-GGML) / [13B](https://huggingface.co/TheBloke/Wizard-Vicuna-13B-Uncensored-GGML) / [30B](https://huggingface.co/TheBloke/Wizard-Vicuna-30B-Uncensored-GGML) - A very well-known, widely-received model series which works well as an unrestricted assistant and for roleplay, based on [this model](https://github.com/melodysdreamj/WizardVicunaLM). The guide believes this to be one of the best options for 7B and 30B users.
- **Vicuna (LLaMA 1)** - [7B](https://huggingface.co/TheBloke/vicuna-7B-v1.3-GGML) / [13B](https://huggingface.co/TheBloke/vicuna-13b-v1.3.0-GGML) / [33B](https://huggingface.co/TheBloke/vicuna-33B-GGML) - Probably the most popular assistant model. It's a restricted model, but probably the best option if you want a local AI that replicates the free ChatGPT experience.
- **Vicuna (LLaMA 2)** - [7B](https://huggingface.co/TheBloke/vicuna-7B-v1.5-GGML) / [13B](https://huggingface.co/TheBloke/vicuna-13B-v1.5-GGML) - Same as previous model, but trained on top of Llama 2, which doubles the AI's memory from 2K to 4K tokens and potentially increases the quality of the AI. There are 16K token (context / memory) versions available for [7B](https://huggingface.co/TheBloke/vicuna-7B-v1.5-16K-GGML) and [13B](https://huggingface.co/TheBloke/vicuna-13B-v1.5-16K-GGML). Guide author's secondary choice as an assistant.
- **Guanaco (LLaMA 1)** - [7B](https://huggingface.co/TheBloke/llama-2-7B-Guanaco-QLoRA-GGML) / [13B](https://huggingface.co/TheBloke/llama-2-13B-Guanaco-QLoRA-GGML) / [70B](https://huggingface.co/TheBloke/llama-2-70b-Guanaco-QLoRA-GGML) - Another camelid model series that can be used as both an assistant and roleplaying partner. Here's [a Reddit post](https://old.reddit.com/r/LocalLLaMA/comments/13rthln/guanaco_7b_13b_33b_and_65b_models_by_tim_dettmers/) on it, in which it was compared with WizardLM-uncensored (predecessor to Wizard-Vicuna-Uncensored).
- **Guanaco (LLaMA 2)** - [7B](https://huggingface.co/TheBloke/llama-2-7B-Guanaco-QLoRA-GGML) / [13B](https://huggingface.co/TheBloke/llama-2-13B-Guanaco-QLoRA-GGML) / [33B]() / [65B](https://huggingface.co/TheBloke/guanaco-65B-GGML) - Same as previous model, but trained on top of Llama 2, which doubles the AI's memory to 4K tokens and potentially increases the quality of the AI.
- **[LaMini 61M to 1.5B](https://github.com/mbzuai-nlp/lamini-lm#models)** - Included here as an option for resource-constrained hardware.
- **RWKV-4 Raven** - [1.5B / 3B / 7B / 14B](https://huggingface.co/BlinkDL/rwkv-4-raven)** - Included here as an option for resource-constrained hardware. GGML conversions (which work with KoboldCpp) can be found [here](https://huggingface.co/latestissue/rwkv-4-raven-ggml-quantized/tree/main).
- **TinyStories Instruct** - [1M](https://huggingface.co/roneneldan/TinyStories-Instruct-1M) / [3M](https://huggingface.co/roneneldan/TinyStories-Instruct-3M) / [8M](https://huggingface.co/roneneldan/TinyStories-Instruct-8M) / [28M](https://huggingface.co/roneneldan/TinyStories-Instruct-28M) / [33M](https://huggingface.co/roneneldan/TinyStories-Instruct-33M) - Included here as an option for resource-constrained hardware. [[Paper]](https://arxiv.org/abs/2305.07759)

\* *An employee of Nous [recommends Redmond-Puffin 13B over Nous-Hermes 13B (Llama 2) for roleplay tasks and multi-turn conversations](https://old.reddit.com/r/LocalLLaMA/comments/155wwrj/noushermesllama2_13b_released_beats_previous/jt20234/), though in the guide author's findings, the community still seems to prefer Nous-Hermes. A discussion of the two can be found [here](https://old.reddit.com/r/LocalLLaMA/comments/158j9r9/nous_hermes_llama2_vs_redmond_puffin_13b/).*

#### Roleplay (like CharacterAI, Replika, etc)
*Some of these are instruct models that just have great roleplaying/storywriting performance.*
- **MythoMix (Llama 2)** - [13B](https://huggingface.co/TheBloke/MythoMix-L2-13B-GGML) - A new model, a merge of MythoLogic-L2 and Huginn (which itself is a merge of "Hermes, Beluga, Airoboros, Chronos, and LimaRP". In initial testing, the guide author finds it good. Damn good. For now, it'll be pinned at the top of this section to encourage further exploration by other users.
- **MythoLogic (LLaMA 1)** - [13B](https://huggingface.co/TheBloke/MythoLogic-13B-GGML) - Guide author's secondary choice for roleplay, tied with Nous-Hermes 13B (Llama 2). While it's an instruct model, they've tested 13B and it's great at roleplaying and storywriting. The guide author believes this to have the best blend of personality, reasoning and erotic language from all of the models they've tested, though it feels like it follows the prompt slightly less than Nous 2 does. 7B is a merge of Nous-Hermes (Llama 2), Stable Beluga, and Kimiko. 13B is a merge of Chronos, Nous-Hermes (LLaMA 1), and Wizard-Vicuna-Uncensored models. If you have the hardware and bandwidth, try both MythoLogic 13B and Nous-Hermes 13B (Llama 2) and see which one you like more.
- **MythoLogic (Llama 2)** - [7B](https://huggingface.co/TheBloke/MythoLogic-Mini-7B-GGML) / [13B](https://huggingface.co/TheBloke/MythoLogic-L2-13B-GGML) - Similar to its LLaMA 1 counterpart, it's a merge of Nous-Hermes, Chronos, and *Airoboros*.
- **Chronos-Hermes 13B (LLaMA 1)** - [13B](https://huggingface.co/TheBloke/chronos-hermes-13B-GGML) - A model that's a merge of Chronos and Nous-Hermes (LLaMA 1). It tries to keep the great prose of Chronos but with the reasoning/logic and instruction-following capability of Nous-Hermes. Still used and recommended by some users, and the guide author even uses it from time to time.
- **Chronos-Hermes 13B (Llama 2)** - [13B](https://huggingface.co/TheBloke/Chronos-Hermes-13B-v2-GGML)
- **Chronos (LLaMA 1)** - [13B](https://huggingface.co/TheBloke/chronos-13B-GGML) / [33B](https://huggingface.co/TheBloke/chronos-33b-GGML) - A model trained mostly on chatting and storywriting. It may not be as good as other models when it comes to reasoning, logic, and following the prompt/character description, but in the guide author's testing of 13B, it (fortunately) lacks the robotic, formal overtone of many other models.
- **Chronos (Llama 2)** - [13B](https://huggingface.co/TheBloke/Chronos-13B-v2-GGML) - An alternative to Chronos 13B (LLaMA 1) trained on top of LLaMA 2. Pretty fresh but needs further testing. Opens the door for Llama 2 versions of Chronos-Hermes and MythoLogic.
- **Airoboros-GPT4 (LLaMA 1)** - [7B](https://huggingface.co/TheBloke/airoboros-7B-gpt4-1.4-GGML) / [13B](https://huggingface.co/TheBloke/airoboros-13B-gpt4-1.4-GGML) / [33B](https://huggingface.co/TheBloke/airoboros-33B-gpt4-1.4-GGML) / [65B](https://huggingface.co/TheBloke/airoboros-65B-gpt4-1.4-GGML) - Airoboros, while being an assistant model, doubles as a good model for roleplaying and chatting, in which [it's preferred](https://old.reddit.com/r/LocalLLaMA/comments/14n1p74/airoboros_14_family_of_models/jqa5vw5/). However, some users report the model being ["too nice"](https://old.reddit.com/r/LocalLLaMA/comments/14l1d48/the_best_13b_model_for_rolepay/) and the guide author recalls hearing that Airoboros isn't worth it until 33B/65B. The model is about as unrestricted as the previous three, and is similarly a great model for 7B, 30B, and 65B users.
- **Airoboros-GPT4 (Llama 2)** - [7B](https://huggingface.co/TheBloke/airoboros-l2-7B-gpt4-2.0-GGML) / [13B](https://huggingface.co/TheBloke/airoboros-l2-13b-gpt4-2.0-GGML) / [70B](https://huggingface.co/TheBloke/airoboros-l2-70B-GPT4-2.0-GGML) - Same as previous model, but trained on top of Llama 2, which doubles the AI's memory to 4K tokens and potentially increases the quality of the AI. [It's under debate.](https://old.reddit.com/r/LocalLLaMA/comments/15gr3oz/new_vicunia_model_based_on_llama2/jukt7vq/) This one is trained on a new dataset. An alternative version is available for [7B](https://huggingface.co/TheBloke/airoboros-l2-7B-gpt4-m2.0-GGML) and [13B](https://huggingface.co/TheBloke/airoboros-l2-13b-gpt4-m2.0-GGML) that is also trained on old data.
- **Manticore-13B-Chat-Pyg (LLaMA 1)** - [13B](https://huggingface.co/TheBloke/manticore-13b-chat-pyg-GGML) - Trained on top of many datasets, including a deduplicated version of Pygmalion's. An old favorite of the guide author.
- **Manticore-13B-Chat-Pyg-Guanaco (LLaMA 1)** - [13B](https://huggingface.co/mindrage/Manticore-13B-Chat-Pyg-Guanaco-GGML) - Similar in spirit to MythoLogic and Chronos-Hermes, it's a merge with Guanaco to boost its reasoning capability. Still used and ecommended by some users, so it's worth looking into.
- **Pygmalion (LLaMA 1)** - [7B](https://huggingface.co/models?search=pygmalion%207b%20ggml) / [13B](https://huggingface.co/Neko-Institute-of-Science/Pygmalion-13B-GGML) - Early chat model. Its dataset includes a significant amount of user-contributed CharacterAI chatlogs. The guide author hasn't seen anyone use these models in a while, so they've likely fallen out of favor. Included here for historical reasons.

#### Writing (like NovelAI)
*While models like Nous-Hermes and MythoLogic do a good job with writing, these are writing models with no instruct functionality.*
- **Holodeck (Llama 2)** - [13B](https://huggingface.co/KoboldAI/LLAMA2-13B-Holodeck-1-GGML) - A recent model created for novel-writing, based on Llama 2.
- **TinyStories** - [1M](https://huggingface.co/roneneldan/TinyStories-1M)** / [3M](https://huggingface.co/roneneldan/TinyStories-3M)** / [8M](https://huggingface.co/roneneldan/TinyStories-8M)** / [28M](https://huggingface.co/roneneldan/TinyStories-28M)**/ [33M](https://huggingface.co/roneneldan/TinyStories-33M) - Included here as an option for resource-constrained hardware. [[Paper]](https://arxiv.org/abs/2305.07759)

#### General-purpose (base models)
*These models are jack-of-all-trades, requiring some real manual prompting to get the results you seek. Think of it as the base Stable Diffusion v1.5 of text generation.*
- **Llama 2** - [7B](https://huggingface.co/TheBloke/Llama-2-7B-GGML) / [13B](https://huggingface.co/TheBloke/Llama-2-13B-GGML) / [70B](https://huggingface.co/TheBloke/Llama-2-70B-GGML)
- **LLaMA** - [7B](https://huggingface.co/TheBloke/LLaMa-7B-GGML) / [13B](https://huggingface.co/TheBloke/LLaMa-13B-GGML) / [30B](https://huggingface.co/TheBloke/LLaMa-30B-GGML) / [65B](https://huggingface.co/TheBloke/LLaMa-65B-GGML)
- **RWKV-4 World** - [~100M / ~400M / 1.5B / 3B / 7B](https://huggingface.co/BlinkDL/rwkv-4-world) - One of the few options if you don't need a 3B+ model. GGML conversions (which work with KoboldCpp) can be found [here](https://huggingface.co/latestissue/rwkv-4-world-ggml-quantized/tree/main).
- **RWKV-5 World** - [~100M / ~400M / 1.5B / 3B / 7B](https://huggingface.co/BlinkDL/rwkv-5-world) - Currently training, will eventually succeed RWKV-4-World.
- **RedPajama-INCITE Base** - [3B](https://huggingface.co/rustformers/redpajama-3b-ggml) / [7B](https://huggingface.co/rustformers/redpajama-7b-ggml)
- **OpenLLaMA** - [3B](https://huggingface.co/SlyEcho/open_llama_3b_v2_ggml) / [7B](https://huggingface.co/SlyEcho/open_llama_7b_v2_ggml) / [13B](https://huggingface.co/SlyEcho/open_llama_13b_ggml)
- **Pythia Deduped** - [70M](https://huggingface.co/EleutherAI/pythia-70m-deduped) / [160M](https://huggingface.co/EleutherAI/pythia-160m-deduped) / [410M](https://huggingface.co/EleutherAI/pythia-410m-deduped) / [1B](https://huggingface.co/EleutherAI/pythia-1b-deduped) / [1.4B](https://huggingface.co/EleutherAI/pythia-70m-deduped) / [2.8B](https://huggingface.co/EleutherAI/pythia-70m-deduped) / [6.9B](https://huggingface.co/EleutherAI/pythia-70m-deduped) / [12B](https://huggingface.co/EleutherAI/pythia-70m-deduped) - A pretty late pre-LLaMA model. Included here for legacy reasons, but also because it's one of the few widely-trained models available in pint sizes. GGML conversions (which work on KoboldCpp) for 70M to 2.8B can be found [here](https://huggingface.co/Merry/ggml-pythia-deduped/tree/main).

An important thing to note is that current AI doesn't have infinite memory. LLaMA 1 and most other models can remember the last 2,048 tokens (~8,000-9,000 characters). Llama 2 models can remember up to 4,096 tokens. If you want them to remember details from older conversations, there are a few band-aid solutions.

For the Oobabooga frontend, you have two options: Superbooga (which comes with the frontend), and [Long-Term Memory](https://github.com/wawawario2/long_term_memory).

For SillyTavern, you have ChromaDB, which is [a part of SillyTavern-extras](https://github.com/SillyTavern/SillyTavern-extras#modules).

For KoboldAI/KoboldCpp and SillyTavern, you have ["World Info"](https://github.com/KoboldAI/KoboldAI-Client/wiki/Memory,-Author%27s-Note-and-World-Info#world-info), a manual solution.

*Continue into [settings](settings.md)...*
