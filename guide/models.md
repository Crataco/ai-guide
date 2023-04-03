# Models

### What are models?

A model is your AI. Or to be more specific, its brain.

Models come in all shapes and sizes, and you will see how they differ depending on how big it is, what data was used to train it, and what backend it uses (which most of the time is [Transformers](https://github.com/huggingface/transformers), but that's a can of worms for another time).

### How many models are there?

I've counted 8 different freely-downloadable model series since 2019. These models have been trained on a variety of data, making them a jack-of-all-trades, but I've managed to include further trainings that adapt it for novel writing (i.e. NovelAI) and chatting (i.e. CharacterAI).

Series | Generic model | Novel model | NSFW model | Chat model | My thoughts
:--|:--:|:--:|:--:|:--:|:--:
**GPT-2** | [124M](https://huggingface.co/gpt2) to [1.5B](https://huggingface.co/gpt2-xl) | Novel [774M](https://storage.henk.tech/KoboldAI/Novel%20model%20774M.rar) | Smut [774M](https://storage.henk.tech/KoboldAI/Smut%20model%20774M%2030K.rar) | DialoGPT [124M?](https://huggingface.co/microsoft/DialoGPT-small) to [774M](https://huggingface.co/microsoft/DialoGPT-large) / HourAI [355M?](https://huggingface.co/archmagos/HourAI) | *GPT-2 kickstarted modern AI text generation, and was most notably used for [the original AI Dungeon 2](https://www.reddit.com/r/rpg/comments/e7ladj/someone_made_an_ai_dungeon_master_that_you_can/). can only hold half as much text in memory as every model that followed, and only goes up to 1.5B, so I don't recommend it today.*
**GPT-Neo / GPT-J** | [125M](https://huggingface.co/EleutherAI/gpt-neo-125M) to [20B](https://huggingface.co/EleutherAI/gpt-neox-20b) | Janeway [2.7B](https://huggingface.co/KoboldAI/GPT-Neo-2.7B-Janeway) to [6B](https://huggingface.co/KoboldAI/GPT-J-6B-Janeway) / Horni-LN [2.7B](https://huggingface.co/KoboldAI/GPT-Neo-2.7B-Horni-LN) | Shinen [2.7B](https://huggingface.co/KoboldAI/GPT-Neo-2.7B-Shinen) to [6B](https://huggingface.co/KoboldAI/GPT-J-6B-Shinen) / Horni [2.7B](https://huggingface.co/KoboldAI/GPT-Neo-2.7B-Horni) | ConvoGPT [125M](https://huggingface.co/hakurei/convogpt/tree/main/125m-uft) to [6B](https://huggingface.co/hakurei/convogpt/tree/main/6b-uft) / Pygmalion [2.7B](https://huggingface.co/PygmalionAI/pygmalion-2.7b) to [6B](https://huggingface.co/PygmalionAI/pygmalion-6b) | *EleutherAI's debut model, trained on a public dataset called "The Pile". It's been widely used, and I feel it has most of the community support and finetunes.*
**OPT** | [125M](https://huggingface.co/facebook/opt-125m) to [66B](https://huggingface.co/facebook/opt-66b) | Nerys [350M](https://huggingface.co/KoboldAI/OPT-350M-Nerys-v2) to [13B](https://huggingface.co/KoboldAI/OPT-13B-Nerys-v2) | Erebus [350M](https://huggingface.co/KoboldAI/OPT-350M-Erebus) to [13B](https://huggingface.co/KoboldAI/OPT-13B-Erebus) | Pygmalion [350M](https://huggingface.co/Pygmalion-AI/pygmalion-350m) / ChatSalad [19M](https://huggingface.co/concedo/OPT-19M-ChatSalad) | *A model series by Meta, succeeding Fairseq, their previous. It outperforms Neo in quality by a noticeable margin, but feels slightly different in a way. It comes second to Neo in terms of the sheer quantity of finetunes and community experience.*
**RWKV** | [169M](https://huggingface.co/BlinkDL/rwkv-4-pile-169m) to [14B](https://huggingface.co/BlinkDL/rwkv-4-pile-14b) | Not yet | Not yet | [Raven RWKV 7B](https://huggingface.co/spaces/BlinkDL/Raven-RWKV-7B) | *A promising series trained on Neo's dataset that intends to be faster and lighter without compromising on quality. Quality-wise I believe it's on par with GPT-Neo.*
**BLOOM** | [560M](https://huggingface.co/bigscience/bloom-560m) to [176B](https://huggingface.co/bigscience/bloom) | Not yet | Not yet | [BloomZ](https://huggingface.co/bigscience/bloomz) | *BigScience's BLOOM may be one of the more well-known model series of this list. Unfortunately, hearsay on the KoboldAI Discord server, model evaluation statistics, and [even Pygmalion's 11b](https://huggingface.co/PygmalionAI/pygmalion-6b/discussions/20#6414ac35b6e553f665e1e453) tell me that BLOOM gives lower quality results compared to the other models listed, likely thanks to its multilingual dataset (thus lack of focus on English). I personally don't recommend it, but I've heard some users get good results with it, so knock yourself out!*
**Pythia** | [70M](https://huggingface.co/EleutherAI/pythia-70m-deduped) to [12B](https://huggingface.co/EleutherAI/pythia-12b-deduped) | Not yet | Not yet | Pygmalion [1.3B](https://huggingface.co/Pygmalion-AI/pygmalion-1.3b) / [Lotus 12B](https://huggingface.co/hakurei/lotus-12B) / [OpenAssistant 12B](https://huggingface.co/OpenAssistant/oasst-sft-1-pythia-12b) | *Another model series by EleutherAI. The one I recommend is the "Deduped" series, trained on a "cleaned" Pile and [according to official evaluations it outperforms GPT-Neo and OPT](https://huggingface.co/EleutherAI/pythia-2.8b-deduped#evaluations). Even Harubaru of Waifu Diffusion and ConvoGPT fame [acknowledged](https://cdn.discordapp.com/attachments/1042160561808482304/1068087246118473728/Screenshot_2023-01-26_00-35-43.png) its [potential](https://cdn.discordapp.com/attachments/1042160561808482304/1068087245799686144/Screenshot_2023-01-26_00-35-55.png) and later used it for their Lotus 12B model.*
**LLaMA** | 7B to 65B | Not yet | Not yet | [Alpaca 7B](https://github.com/tloen/alpaca-lora) / [GPT4All](https://github.com/nomic-ai/gpt4all) / [Vicuna](https://vicuna.lmsys.org/) | *New model by Meta. Officially only available to researchers. AI evaluation says 13B is on par with GPT-3 175B, and 7B overtakes even Pythia 12B and OPT 66B. The Transformers version of the model [is available via reuploads](https://huggingface.co/models?search=llama%20hf), and the llama.cpp version can be used by downloading [one of these](https://huggingface.co/maderix/llama-65b-4bit/tree/main), a tokenizer from [here](https://huggingface.co/decapoda-research/llama-7b-hf/tree/main) or [here](https://huggingface.co/nyanko7/LLaMA-7B/tree/main), and converting them.*
**Cerebras** | [111M](https://huggingface.co/cerebras/Cerebras-GPT-111M) to [13B](https://huggingface.co/cerebras/Cerebras-GPT-13B) | Not yet | Not yet | Not yet | *New model in general. According to their description their models use The Pile much like GPT-Neo, Pythia and RWKV, but it isn't deduplicated. I'll likely look into it.*

### Jeez! Which one should I pick?

Depends on what you want to do with your AI, and what your system requirements are.

If you wanna pick by series:

- A generic Pythia (well-supported) or LLaMA (best quality) model if you want something flexible, like GPT-3

- Janeway or Erebus (NSFW) if you want a co-writer, like NovelAI

- Nerys if you want a text adventure, like AI Dungeon

- Pygmalion (NSFW) and Erebus (NSFW) if you want a chatting partner, like Replika or CharacterAI

If you wanna pick by size:

- If you have a standard computer, I'd recommend to start with a ~350M model and slowly work your way up to bigger models, so you can tell how much quality you're willing to gain, and performance you're willing to compromise. [Here's a memory usage chart](https://github.com/Crataco/ai-guide/blob/main/charts/memory-usage.md) I've made, and [another usage chart](https://github.com/oobabooga/text-generation-webui/wiki/System-requirements) by Oobabooga.

- Alternatively, if you have a gaming computer (with NVIDIA cards being the best supported), you can fit the model entirely on the GPU itself, which will typically take up half as much video RAM as it does regular RAM, and be lightning fast. If you don't have enough VRAM, you can also split it between regular RAM and VRAM, but it will be much slower.

If you're an advanced user, you're likely to reduce system requirements quite a lot by looking into [4-bit quantization](https://github.com/oobabooga/text-generation-webui/wiki/LLaMA-model#4-bit-mode) and [other backends](https://github.com/oobabooga/text-generation-webui/wiki/llama.cpp-models). 
