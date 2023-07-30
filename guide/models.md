![image](https://user-images.githubusercontent.com/55674863/230696024-98ce9e16-f558-4402-ac43-0e7f960c118c.png)

# Models

### What are models?

A model is your AI's brain. They come in all shapes and sizes.

**Feel free to skip the upcoming bullet-points.**

Explaining it in more detail:

- **Model series**. At the time of writing, LLaMA is currently the most popular. Other examples include Llama 2, RedPajama-INCITE, RWKV-4, Pythia Deduped, and GPT-Neo/GPT-J.
  
- **Size**. These are called "parameters" and are commonly found in the range of 7 billion (7B) to 65 billion (65B). Sometimes smaller (125M), sometimes bigger (175B). A general rule of thumb is that bigger models take up more resources and act smarter, but this isn't always the case, as...

- **The data the model is trained on** influences where the model "leans". For example, a model trained on novels would be great at writing novels. With a great-quality dataset, you'll likely get a great-quality model.

- Lastly, **base models** are the original models, which can be described as a jack-of-all-trades, master-of-none due to their diverse training data. **Finetunes** train the model on more data to get it to act a certain way, or know more things.

As an example, a user could be using a 13B LLaMA model finetuned on top of ChatGPT data (to get it to act just like ChatGPT). Backends are also important information to know.

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
1. See what people are up to on [r/LocalLLaMA](https://old.reddit.com/r/LocalLLaMA)
2. Read TheBloke's RAM usage graphs to see what level of quantization (q2, q3, q4, q5, q6) you should get for a [7B model](https://huggingface.co/TheBloke/guanaco-7B-GGML#provided-files), [13B model](https://huggingface.co/TheBloke/guanaco-13B-GGML#provided-files), and others, depending on how much system memory you have.
3. (Roleplay) Check out model benchmarks such as [ALLMRR](https://rentry.co/ALLMRR) and [Ayumi ERP](https://rentry.co/ayumi_erp_rating). While you're at it, feel free to grab a character from [Chub.ai](https://www.chub.ai/) to use for Oobabooga, Tavern, or SillyTavern.

Here are some of the guide's recommended finetunes, listed in order of the author's preference and experience using them. But don't just take their word for it: if you have the bandwidth and space to spare, try them yourself.

#### Instruct (like ChatGPT)
*Keep in mind that every instruct model has its own "prompt template." You will need to set them in your frontend to get the best responses out of your models. In Oobabooga they're referred to as "instruction templates" and in SillyTavern they go by "Presets" in the formatting tab. [TheBloke usually covers them](https://huggingface.co/TheBloke/guanaco-7B-GGML#prompt-template-guanaco).*
- [Guanaco 7B](https://huggingface.co/TheBloke/guanaco-7B-GGML) / [Guanaco 13B](https://huggingface.co/TheBloke/guanaco-13B-GGML) / [Guanaco 33B](https://huggingface.co/TheBloke/guanaco-33B-GGML) / [Guanaco 65B](https://huggingface.co/TheBloke/guanaco-65B-GGML) - The guide author's favorite assistant model. It may be usable for roleplaying, but the guide author hasn't tested it out nor heard many recommendations to use it for such.
- [Airoboros 7B](https://huggingface.co/TheBloke/airoboros-7B-gpt4-1.4-GGML) / [Airoboros 13B](https://huggingface.co/TheBloke/airoboros-13B-gpt4-1.4-GGML) / [Airoboros 33B](https://huggingface.co/TheBloke/airoboros-33B-gpt4-1.4-GGML) / [Airoboros 65B](https://huggingface.co/TheBloke/airoboros-65B-gpt4-1.4-GGML) - The guide author's secondary favorite assistant model. It also doubles as a decent model for roleplaying and chatting, and probably the best option 7B users have. However, some users report the model being ["too nice"](https://old.reddit.com/r/LocalLLaMA/comments/14l1d48/the_best_13b_model_for_rolepay/).
- [Wizard-Vicuna 7B Uncensored](https://huggingface.co/TheBloke/Wizard-Vicuna-7B-Uncensored-GGML) / [Wizard-Vicuna 13B Uncensored](https://huggingface.co/TheBloke/Wizard-Vicuna-13B-Uncensored-GGML) / [Wizard-Vicuna 30B Uncensored](https://huggingface.co/TheBloke/Wizard-Vicuna-30B-Uncensored-GGML) - The guide author didn't test this out much, but heard this was (and likely still is) a good model, being included in [this guide](https://rentry.org/local_LLM_guide_models). It's also one of the few model series available for 7B.
- [Vicuna 7B](https://huggingface.co/TheBloke/vicuna-7B-v1.3-GGML) / [Vicuna 13B](https://huggingface.co/TheBloke/vicuna-13b-v1.3.0-GGML) / [Vicuna 33B](https://huggingface.co/TheBloke/vicuna-33B-GGML) - An old favorite, though the guide author remembers Vicuna refusing to answer certain questions, thus being a "restricted" model.
- [LaMini 61M to 1.5B](https://github.com/mbzuai-nlp/lamini-lm#models) - Included here as an option for resource-constrained hardware.
- [RWKV-4 Raven 1.5B to 14B](https://huggingface.co/latestissue/rwkv-4-raven-ggml-quantized/tree/main) - Included here as an option for resource-constrained hardware.
- [TinyStories Instruct 1M](https://huggingface.co/roneneldan/TinyStories-Instruct-1M) / [TinyStories Instruct 3M](https://huggingface.co/roneneldan/TinyStories-Instruct-3M) / [TinyStories Instruct 8M](https://huggingface.co/roneneldan/TinyStories-Instruct-8M) / [TinyStories Instruct 28M](https://huggingface.co/roneneldan/TinyStories-Instruct-28M) / [TinyStories Instruct 33M](https://huggingface.co/roneneldan/TinyStories-Instruct-33M) - Included here as an option for resource-constrained hardware. [[Paper]](https://arxiv.org/abs/2305.07759)

#### Roleplay (like CharacterAI, Replika, etc)
*Some of these are instruct models that shine best when used to talk to the AI like a human or character.*
- [MythoLogic Mini 7B](https://huggingface.co/TheBloke/MythoLogic-Mini-7B-GGML) / [MythoLogic 13B](https://huggingface.co/TheBloke/MythoLogic-13B-GGML) - Guide author's current choice. While it's an instruct model, they've tested 13B and it's great at roleplaying and storywriting. The guide author believes this to have the best blend of personality, reasoning and erotic language from all of the models they've tested. 7B is a merge of Nous-Hermes (Llama 2), Stable Beluga, and Kimiko. 13B is a merge of Chronos, Nous-Hermes (LLaMA 1), and Wizard-Vicuna-Uncensored models. The creator also made [MythoBoros](https://huggingface.co/Gryphe/MythoBoros-13b).
- [Nous-Hermes 13B (Llama 2)](https://huggingface.co/TheBloke/Nous-Hermes-Llama2-GGML) - Guide author's secondary choice. Also an instruct model with great performance at roleplaying, storywriting, and erotic roleplay, maybe even better than MythoLogic 13B (LLaMA 1). The guide author feels like this is "smarter" than most LLaMA 1 finetunes, but its vocabulary tends to be a hit-and-miss? If you have the hardware and bandwidth, try both MythoLogic 13B and Nous-Hermes 13B (Llama 2).
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
