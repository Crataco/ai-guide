![image](https://user-images.githubusercontent.com/55674863/230696024-98ce9e16-f558-4402-ac43-0e7f960c118c.png)

# Models

### What are models?

A model is your AI's brain.
- They're usually released as a base model of a series, and have a specific size. An example would be LLaMA 7B. LLaMA is the series, and 7B is the size. The size influences how much storage and resources the model uses, and usually, how smart it is.
- Communities and companies finetune the base models. This is training them on more data to make them better with specific tasks. An example would be Vicuna 7B, based on the LLaMA 7B model, but trained to be an assistant.
- They are converted to different formats that can be used by different backends.

* * *

### What is a backend?

Backends are just different ways to run AI, each having their own way of storing and using the models.

For example, LLaMA 7B is available for the [Transformers](https://huggingface.co/decapoda-research/llama-7b-hf), [GGML](https://huggingface.co/TheBloke/LLaMa-7B-GGML), and [GPTQ/Exllama](https://huggingface.co/camelids/llama-7b-int4-gptq-groupsize128-safetensors/tree/main) backends.

### What does this mean?

- Transformers has the advantage of being widely available, but its models take up more space and power.

- GGML versions are efficient, using less RAM and hard drive space thanks to quantization, which this guide will explain in a bit. For example, a 13B model that'd take 64GB of RAM through Transformers could take 16GB of RAM through GGML. This is a better idea if you don't have a powerful gaming or cloud computer.

- GPTQ/Exllama, too, supports quantization, but is useful if you have a gaming desktop with an NVIDIA graphics card. For AMD, your mileage may vary.

One way to describe quantization is like compressing an image to JPEG. You lose some detail as it gets noisier and blockier, but the image ultimately ends up taking less space, and (in this case) doesn't require much power to render.

* * *

### What model should I use?

This guide recommends that you:
1. See what people are up to on [r/LocalLLaMA](https://old.reddit.com/r/LocalLLaMA) and what new models are added to [its wiki](https://old.reddit.com/r/LocalLLaMA/wiki/models).
2. Read TheBloke's RAM usage graphs to see what level of quantization (q2, q3, q4, q5, q6) you should get for a [7B model](https://huggingface.co/TheBloke/guanaco-7B-GGML#provided-files), [13B model](https://huggingface.co/TheBloke/guanaco-13B-GGML#provided-files), and others, depending on how much system memory you have.
3. (Roleplay) Check out model benchmarks such as [ALLMRR](https://rentry.co/ALLMRR) and [Ayumi ERP](https://rentry.co/ayumi_erp_rating). While you're at it, feel free to grab a character from [Chub.ai](https://www.chub.ai/) (NSFW warning) to use for Oobabooga, Tavern, or SillyTavern.

Here are some of the guide's recommended finetunes, listed in order of the author's preference and experience using them. But don't just take their word for it: if you have the bandwidth and space to spare, try them yourself.

#### Instruct / Assistant (like ChatGPT)
*Keep in mind that every instruct model has its own "prompt template." You will need to set them in your frontend to get the best responses out of your models. In Oobabooga they're referred to as "instruction templates" and in SillyTavern they go by "Presets" in the formatting tab. [TheBloke usually covers them](https://huggingface.co/TheBloke/guanaco-7B-GGML#prompt-template-guanaco).*

*Models are "unrestricted" if they don't refuse most requests. They're "restricted" if they're largely trained on the same refusals as ChatGPT.*
- [Nous-Hermes 13B (Llama 2)](https://huggingface.co/TheBloke/Nous-Hermes-Llama2-GGML) - Guide author's primary choice as an assistant, and secondary choice for roleplaying. [Trained on high-quality GPT-4 datasets (and some others)](https://huggingface.co/NousResearch/Nous-Hermes-Llama2-13b#model-training), the guide author feels like this is smarter than most LLaMA 1 finetunes, following the prompt better, though at the cost of possibly feeling less "natural." The model is an assistant by default and refuses to answer in some _extreme_ edge-cases, but it can still be used for erotic roleplay and storywriting due to its training data. The guide considers this model unrestricted and one of the best models for 13B users.

\* *An employee of Nous [recommends Redmond-Puffin 13B over Nous-Hermes 13B (Llama 2) for roleplay tasks](https://old.reddit.com/r/LocalLLaMA/comments/155wwrj/noushermesllama2_13b_released_beats_previous/jt20234/), though in the guide author's findings, the community still seems to prefer Nous-Hermes. A discussion of the two can be found [here](https://old.reddit.com/r/LocalLLaMA/comments/158j9r9/nous_hermes_llama2_vs_redmond_puffin_13b/).*

- [Guanaco 7B](https://huggingface.co/TheBloke/guanaco-7B-GGML) / [Guanaco 13B](https://huggingface.co/TheBloke/guanaco-13B-GGML) / [Guanaco 33B](https://huggingface.co/TheBloke/guanaco-33B-GGML) / [Guanaco 65B](https://huggingface.co/TheBloke/guanaco-65B-GGML) - Finetuned on top of [the OpenAssistant dataset](https://huggingface.co/timdettmers/guanaco-13b#model-card). The guide author's secondary favorite assistant model. It's also usable for roleplay and storywriting, but the guide author hasn't tested it out nor heard many recommendations to use it for such. In testing with 13B, this model is similarly unrestricted.
- [Wizard-Vicuna 7B Uncensored](https://huggingface.co/TheBloke/Wizard-Vicuna-7B-Uncensored-GGML) / [Wizard-Vicuna 13B Uncensored](https://huggingface.co/TheBloke/Wizard-Vicuna-13B-Uncensored-GGML) / [Wizard-Vicuna 30B Uncensored](https://huggingface.co/TheBloke/Wizard-Vicuna-30B-Uncensored-GGML) - This model was included in [this guide](https://rentry.org/local_LLM_guide_models). In the guide author's testing, roleplaying performance is good, but may need some tweaking. It's also one of the few model series available for 7B and, again, is similarly unrestricted. The guide considers this one of the best models for 30B users.
- [Airoboros-GPT4 7B](https://huggingface.co/TheBloke/airoboros-7B-gpt4-1.4-GGML) / [Airoboros-GPT4 13B](https://huggingface.co/TheBloke/airoboros-13B-gpt4-1.4-GGML) / [Airoboros-GPT4 33B](https://huggingface.co/TheBloke/airoboros-33B-gpt4-1.4-GGML) / [Airoboros-GPT4 65B](https://huggingface.co/TheBloke/airoboros-65B-gpt4-1.4-GGML) - Airoboros, while being an assistant model, also doubles as a decent model for roleplaying and chatting. However, some users report the model being ["too nice"](https://old.reddit.com/r/LocalLLaMA/comments/14l1d48/the_best_13b_model_for_rolepay/) and the guide author recalls hearing that Airoboros isn't worth it until 33B/65B. The model is about as unrestricted as the previous three, and is similarly one of the best models for 7B, 30B, and 65B users.
- [Vicuna 7B](https://huggingface.co/TheBloke/vicuna-7B-v1.3-GGML) / [Vicuna 13B](https://huggingface.co/TheBloke/vicuna-13b-v1.3.0-GGML) / [Vicuna 33B](https://huggingface.co/TheBloke/vicuna-33B-GGML) - A well-known assistant model, though restricted. r/LocalLLaMA's wiki describes this as "the most similar experience" you'll get to ChatGPT's gpt-3.5-turbo.
- [LaMini 61M to 1.5B](https://github.com/mbzuai-nlp/lamini-lm#models) - Included here as an option for resource-constrained hardware.
- [RWKV-4 Raven 1.5B to 14B](https://huggingface.co/latestissue/rwkv-4-raven-ggml-quantized/tree/main) - Included here as an option for resource-constrained hardware.
- [TinyStories Instruct 1M](https://huggingface.co/roneneldan/TinyStories-Instruct-1M) / [TinyStories Instruct 3M](https://huggingface.co/roneneldan/TinyStories-Instruct-3M) / [TinyStories Instruct 8M](https://huggingface.co/roneneldan/TinyStories-Instruct-8M) / [TinyStories Instruct 28M](https://huggingface.co/roneneldan/TinyStories-Instruct-28M) / [TinyStories Instruct 33M](https://huggingface.co/roneneldan/TinyStories-Instruct-33M) - Included here as an option for resource-constrained hardware. [[Paper]](https://arxiv.org/abs/2305.07759)

#### Roleplay (like CharacterAI, Replika, etc)
*Some of these are instruct models that just have great roleplaying performance.*
- [MythoLogic Mini 7B](https://huggingface.co/TheBloke/MythoLogic-Mini-7B-GGML) / [MythoLogic 13B](https://huggingface.co/TheBloke/MythoLogic-13B-GGML) - Guide author's current choice, tied with Nous-Hermes 13B (Llama 2). While it's an instruct model, they've tested 13B and it's great at roleplaying and storywriting. The guide author believes this to have the best blend of personality, reasoning and erotic language from all of the models they've tested. 7B is a merge of Nous-Hermes (Llama 2), Stable Beluga, and Kimiko. 13B is a merge of Chronos, Nous-Hermes (LLaMA 1), and Wizard-Vicuna-Uncensored models. If you have the hardware and bandwidth, try both MythoLogic 13B and Nous-Hermes 13B (Llama 2).
- [Chronos 13B](https://huggingface.co/TheBloke/chronos-13B-GGML) / [Chronos 33B](https://huggingface.co/TheBloke/chronos-33b-GGML) - A model trained mostly on chatting and storywriting. It may not be as good as other models when it comes to reasoning and logic, but in the guide author's testing of 13B, it (fortunately) lacks the robotic, formal overtone of many assistant models.
- [Chronos-Hermes 13B](https://huggingface.co/TheBloke/chronos-hermes-13B-GGML) - A model that's a merge of Chronos and Nous-Hermes (LLaMA 1). It tries to keep the great prose of Chronos but with the reasoning/logic and instruction-following capability of Nous-Hermes. Still used by some users.
- [Manticore-13B-Chat-Pyg](https://huggingface.co/TheBloke/manticore-13b-chat-pyg-GGML) - Trained on top of many datasets, including a deduplicated version of Pygmalion's. An old favorite of the guide author.
- [Manticore-13B-Chat-Pyg-Guanaco](https://huggingface.co/mindrage/Manticore-13B-Chat-Pyg-Guanaco-GGML) - Similar in spirit to MythoLogic and Chronos-Hermes, it's a merge with Guanaco to boost its reasoning capability. Still used by some users.
- [Pygmalion 7B](https://huggingface.co/models?search=pygmalion%207b%20ggml) / [Pygmalion 13B](https://huggingface.co/Neko-Institute-of-Science/Pygmalion-13B-GGML) - Early chat model. Its dataset includes a significant amount of user-contributed CharacterAI chatlogs. The guide author hasn't seen anyone use these models in a while, so they've likely fallen out of favor. Included here for historical reasons.

#### Writing (like NovelAI)
*Models like MythoLogic seem to do a good job with writing. These are writing models with no instruct functionality.*
- [LLAMA2 13B Holodeck](https://huggingface.co/KoboldAI/LLAMA2-13B-Holodeck-1-GGML) - A recent model created for novel-writing, based on Llama 2.
- [TinyStories 1M](https://huggingface.co/roneneldan/TinyStories-1M) to [33M](https://huggingface.co/roneneldan/TinyStories-33M) - Included here as an option for resource-constrained hardware. [[Paper]](https://arxiv.org/abs/2305.07759)

#### General-purpose (base models)
*These models, by default, are good at one thing: generating text.*
- [Llama 2 7B](https://huggingface.co/TheBloke/Llama-2-7B-GGML) / [Llama 2 13B](https://huggingface.co/TheBloke/Llama-2-13B-GGML) / [Llama 2 70B](https://huggingface.co/TheBloke/Llama-2-70B-GGML)
- [LLaMA 1 7B](https://huggingface.co/TheBloke/LLaMa-7B-GGML) / [LLaMA 1 13B](https://huggingface.co/TheBloke/LLaMa-13B-GGML) / [LLaMA 1 30B](https://huggingface.co/TheBloke/LLaMa-30B-GGML) / [LLaMA 1 65B](https://huggingface.co/TheBloke/LLaMa-65B-GGML)
- [RedPajama-INCITE Base 3B](https://huggingface.co/rustformers/redpajama-3b-ggml) / [RedPajama-INCITE Base 7B](https://huggingface.co/rustformers/redpajama-7b-ggml)
- [OpenLLaMA 3B](https://huggingface.co/SlyEcho/open_llama_3b_v2_ggml) / [OpenLLaMA 7B](https://huggingface.co/SlyEcho/open_llama_7b_v2_ggml) / [OpenLLaMA 13B](https://huggingface.co/SlyEcho/open_llama_13b_ggml)

An important thing to note is that current AI doesn't have infinite memory. LLaMA 1 and most other models can remember the last 2,048 tokens (~8,000-9,000 characters). Llama 2 models can remember up to 4,096 tokens. If you want them to remember details from older conversations, there are a few band-aid solutions.

For the Oobabooga frontend, you have two options: Superbooga (which comes with the frontend), and [Long-Term Memory](https://github.com/wawawario2/long_term_memory).

For SillyTavern, you have ChromaDB, which is [a part of SillyTavern-extras](https://github.com/SillyTavern/SillyTavern-extras#modules).

For KoboldAI/KoboldCpp and SillyTavern, you have ["World Info"](https://github.com/KoboldAI/KoboldAI-Client/wiki/Memory,-Author%27s-Note-and-World-Info#world-info), a manual solution.

*Continue into [settings](settings.md)...*
