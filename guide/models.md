![image](https://user-images.githubusercontent.com/55674863/230696024-98ce9e16-f558-4402-ac43-0e7f960c118c.png)

# Models

### What are models?

A model is your AI's brain. They come in all shapes and sizes.

**Feel free to skip the upcoming bullet-points!**

A lengthier explanation would be:

- **Model series**. At the time of writing, LLaMA is currently the most popular. Other examples include RedPajama-INCITE, RWKV-4, and Pythia Deduped.
  
- **Size**. These are called "parameters" and are commonly found in the range of 125 million (125M) to 13 billion (13B). A general rule of thumb is that bigger models take up more resources and are smarter, but this isn't always the case, as...

- **The data the model is trained on** influences where the model "leans" (for example, a model trained on novels would be great at writing novels), and with a clean, great-quality dataset, you'll get a great-quality model.

- Lastly, **base models** are the original models, which can be described as a jack-of-all-trades, master-of-none due to their diverse training data. **Finetunes** train the model on more data to get it to act a certain way, or know more things.

The average user would be using a 13B LLaMA model finetuned on top of ChatGPT data (to get it to act just like ChatGPT). Backends are also important information to know.

* * *

### What is a backend?

Backends are just different ways to run AI, each having their own way of storing and using the models.

For example, LLaMA 7B is available for the [Transformers](https://huggingface.co/decapoda-research/llama-7b-hf), [GGML](https://huggingface.co/TheBloke/LLaMa-7B-GGML), and [GPTQ/Exllama](https://huggingface.co/camelids/llama-7b-int4-gptq-groupsize128-safetensors/tree/main) backends.

### What does this mean?

- Transformers has the advantage of being widely available, but its models take up more space and power.

- GGML versions are efficient, using less RAM and hard drive space thanks to quantization, which this guide will explain in a bit. For example, a 13B model that'd take 64GB of RAM through Transformers could take 16GB of RAM through GGML. This is a better idea if you don't have a gaming desktop.

- GPTQ/Exllama, too, supports quantization, but is useful if you have a gaming desktop with an NVIDIA graphics card. For AMD, your mileage may vary.

One way to describe quantization is like lossy compression. Compare it to converting a video from one codec to another, or from 1080p to 720p. You will lose a bit of detail, but you save a ton of space and playing it back will require less processing power.

* * *

### What model should I use?

This guide recommends that you explore the [Open LLM Leaderboard](https://huggingface.co/spaces/HuggingFaceH4/open_llm_leaderboard) and the [r/LocalLLaMA wiki](https://old.reddit.com/r/LocalLLaMA/wiki/models#wiki_models).

Here are some of the guide author's favorite finetunes.

#### Instruct (ChatGPT, Bard)
- [WizardLM 7B](https://huggingface.co/TheBloke/wizardLM-7B-GGML) / [WizardLM 13B](https://huggingface.co/TheBloke/wizardLM-13B-1.0-GGML) - Considered well-known and reliable by the guide author.
- [WizardLM 7B Uncensored](https://huggingface.co/TheBloke/WizardLM-7B-V1.0-Uncensored-GGML) / [WizardLM 13B Uncensored](https://huggingface.co/TheBloke/WizardLM-13B-Uncensored-GGML) - "Uncensored" means that it doesn't refuse to answer questions.
- [Nous-Hermes 13B](https://huggingface.co/TheBloke/Nous-Hermes-13B-GGML) - Another uncensored model, stating to rival GPT-3.5 in terms of performance.
- [Airoboros-GPT4 7B](https://huggingface.co/TheBloke/airoboros-7B-gpt4-1.2-GGML) / [Airoboros-GPT4 13B](https://huggingface.co/TheBloke/airoboros-13B-gpt4-1.2-GGML) - Amazingly coherent, but the guide author had trouble avoiding "as a" in roleplay responses. It's not refusal, just a ChatGPT nuance.
- [LaMini 61M to 1.5B](https://github.com/mbzuai-nlp/lamini-lm#models) - A great option for resource-constrained hardware, but there are no GGML versions at the time of writing.
- [RWKV-4 Raven 1.5B to 14B](https://huggingface.co/latestissue/rwkv-4-raven-ggml-quantized/tree/main) - Another great option for resource-constrained hardware.

#### Roleplay (CharacterAI, Replika, etc)
- [Chronos Hermes 13B](https://huggingface.co/TheBloke/chronos-hermes-13B-GGML) - Guide author's current choice.
- [Manticore-Chat-Pyg 13B](https://huggingface.co/TheBloke/manticore-13b-chat-pyg-GGML) - Guide author's old favorite/fallback.

#### Writing (NovelAI / AI Dungeon)

*These will be Transformers models, since they're relatively old.*

- [Janeway 2.7B](https://huggingface.co/KoboldAI/fairseq-dense-2.7B-Janeway) to [13B](https://huggingface.co/KoboldAI/fairseq-dense-13B-Janeway) - For novel-writing.
- [Nerys 350M](https://huggingface.co/KoboldAI/OPT-350M-Nerys-v2) to [13B](https://huggingface.co/KoboldAI/OPT-13B-Nerys-v2) - For novel-writing and text adventures.
- [Erebus 350M](https://huggingface.co/KoboldAI/OPT-350M-Erebus) to [30B](https://huggingface.co/KoboldAI/OPT-30B-Erebus) - For NSFW erotica. In the past it was also known for having great chatting performance.

An important thing to note is that current AI doesn't have long-term memory. Most models can remember the last 2,048 tokens (~8,000-9,000 characters), so if you want them to remember details from older conversations, there exist a few band-aid solutions.

For the Oobabooga frontend, you have two options: Superbooga (which comes with the program), and [Long-Term Memory](https://github.com/wawawario2/long_term_memory).

For SillyTavern, you have ChromaDB, which is [a part of SillyTavern-extras](https://github.com/SillyTavern/SillyTavern-extras#modules).

For KoboldAI/KoboldCpp and SillyTavern, you have ["World Info"](https://github.com/KoboldAI/KoboldAI-Client/wiki/Memory,-Author%27s-Note-and-World-Info#world-info), a manual solution.

* * *

### How many model series are there?

[See the Spaghetti Guide](https://github.com/Crataco/ai-guide/blob/main/guide/original.md#detailed-information).
