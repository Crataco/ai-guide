![image](https://user-images.githubusercontent.com/55674863/230696024-98ce9e16-f558-4402-ac43-0e7f960c118c.png)

# Models

### What are models?

_A model is your AI. Or to be more specific, its brain._

_Models come in all shapes and sizes, and you will see how they differ depending on how big it is, what data was used to train it, and what backend it uses (which most of the time is [Transformers](https://github.com/huggingface/transformers), but that's a can of worms for another time)._

### How many models are there?

_I've counted 9 different freely-downloadable model series since 2019. These models have been trained on a variety of data, making them a jack-of-all-trades, but I've managed to include variants that adapt it for novel writing (i.e. NovelAI) and chatting (i.e. CharacterAI)._

Series | Generic model | Novel model | NSFW model | Chat model | My thoughts
:--|:--:|:--:|:--:|:--:|:--:
**GPT-2** | [124M](https://huggingface.co/gpt2) to [1.5B](https://huggingface.co/gpt2-xl) | Novel [774M](https://storage.henk.tech/KoboldAI/Novel%20model%20774M.rar) | Smut [774M](https://storage.henk.tech/KoboldAI/Smut%20model%20774M%2030K.rar) | DialoGPT [124M?](https://huggingface.co/microsoft/DialoGPT-small) to [774M](https://huggingface.co/microsoft/DialoGPT-large) / HourAI [355M?](https://huggingface.co/archmagos/HourAI) | *2019 - By OpenAI. GPT-2 kickstarted modern AI text generation, and was most notably used for [the original AI Dungeon 2](https://www.reddit.com/r/rpg/comments/e7ladj/someone_made_an_ai_dungeon_master_that_you_can/). I don't recommend it today due to its small size and small context length (1024 tokens).*
**GPT-Neo & GPT-J** | [125M](https://huggingface.co/EleutherAI/gpt-neo-125M) to [20B](https://huggingface.co/EleutherAI/gpt-neox-20b) | Janeway [2.7B](https://huggingface.co/KoboldAI/GPT-Neo-2.7B-Janeway) to [6B](https://huggingface.co/KoboldAI/GPT-J-6B-Janeway) / Horni-LN [2.7B](https://huggingface.co/KoboldAI/GPT-Neo-2.7B-Horni-LN) | Shinen [2.7B](https://huggingface.co/KoboldAI/GPT-Neo-2.7B-Shinen) to [6B](https://huggingface.co/KoboldAI/GPT-J-6B-Shinen) / Horni [2.7B](https://huggingface.co/KoboldAI/GPT-Neo-2.7B-Horni) | ConvoGPT [125M](https://huggingface.co/hakurei/convogpt/tree/main/125m-uft) to [6B](https://huggingface.co/hakurei/convogpt/tree/main/6b-uft) / Pygmalion [2.7B](https://huggingface.co/PygmalionAI/pygmalion-2.7b) to [6B](https://huggingface.co/PygmalionAI/pygmalion-6b) | *2021 - By EleutherAI's. Trained on a public dataset called "The Pile". I feel it has plenty community support.*
**OPT** | [125M](https://huggingface.co/facebook/opt-125m) to [66B](https://huggingface.co/facebook/opt-66b) | Nerys [350M](https://huggingface.co/KoboldAI/OPT-350M-Nerys-v2) to [13B](https://huggingface.co/KoboldAI/OPT-13B-Nerys-v2) | Erebus [350M](https://huggingface.co/KoboldAI/OPT-350M-Erebus) to [13B](https://huggingface.co/KoboldAI/OPT-13B-Erebus) | Pygmalion [350M](https://huggingface.co/Pygmalion-AI/pygmalion-350m) / ChatSalad [19M](https://huggingface.co/concedo/OPT-19M-ChatSalad) | *2022 - By Meta AI, succeeding Fairseq, their previous series. It slightly outperforms Neo. It comes second to Neo in terms of the sheer quantity of finetunes and community experience. There's a 175B, but it's only available via request. I can't find a download anywhere.*
**RWKV** | [169M](https://huggingface.co/BlinkDL/rwkv-4-pile-169m) to [14B](https://huggingface.co/BlinkDL/rwkv-4-pile-14b) | Not yet | Not yet | [Raven RWKV 7B](https://huggingface.co/spaces/BlinkDL/Raven-RWKV-7B) | *2022 - A promising series trained on Neo's dataset that intends to be faster and lighter without compromising on quality. Quality-wise I believe it's on par with GPT-Neo.*
**BLOOM** | [560M](https://huggingface.co/bigscience/bloom-560m) to [176B](https://huggingface.co/bigscience/bloom) | Not yet | Not yet | [BloomZ](https://huggingface.co/bigscience/bloomz) | *2022 - by BigScience. Evaluation shows that this model underperforms compared to the rest. I personally don't recommend it, but I've heard some users get good results with it.*
**GALACTICA** | [125M](https://huggingface.co/facebook/galactica-125m) to [120B](https://huggingface.co/facebook/galactica-120b/tree/main) | Not yet | Not yet | Not yet | *2022 - By Meta AI. I know very little of these models, but I do know they are trained on scientific texts.*
**Pythia** | [70M](https://huggingface.co/EleutherAI/pythia-70m-deduped) to [12B](https://huggingface.co/EleutherAI/pythia-12b-deduped) | Not yet | Not yet | Pygmalion [1.3B](https://huggingface.co/Pygmalion-AI/pygmalion-1.3b) / [Lotus 12B](https://huggingface.co/hakurei/lotus-12B) / [OpenAssistant 12B](https://huggingface.co/OpenAssistant/oasst-sft-1-pythia-12b) / [Instruct 12B](https://huggingface.co/hakurei/instruct-12b) | *2022 - By EleutherAI. I focus on the "Deduped" series, trained on a "cleaned" (deduplicated) Pile, and [according to official evaluations it outperforms GPT-Neo and OPT](https://huggingface.co/EleutherAI/pythia-2.8b-deduped#evaluations).*
**LLaMA** | 7B to 65B | Not yet | Not yet | [Alpaca 7B](https://github.com/tloen/alpaca-lora) / [GPT4All](https://github.com/nomic-ai/gpt4all) / [Vicuna](https://vicuna.lmsys.org/) | *2023 - By Meta AI. Only officially available to researchers. AI evaluation says 13B is on par with GPT-3 175B, and 7B overtakes even Pythia 12B and OPT 66B. The Transformers version of the model [is available via reuploads](https://huggingface.co/models?search=llama%20hf). Same with [the GPTQ version](https://huggingface.co/maderix/llama-65b-4bit/tree/main).*
**Cerebras-GPT** | [111M](https://huggingface.co/cerebras/Cerebras-GPT-111M) to [13B](https://huggingface.co/cerebras/Cerebras-GPT-13B) | Not yet | Not yet | Not yet | *2023 - By Cerebras. According to their description their models use The Pile much like GPT-Neo, Pythia and RWKV, but it isn't deduplicated. It seems to underperform according to evaluations, but I haven't tried it myself.*

[I've also compiled a model scoring list (evaluation).](https://pastebin.com/M3uESsyZ)

### That's a lot! Which one should I pick?

_Depends on what you want to do with your AI, and what your system requirements are._

_If you wanna pick by series:_

- _For generic, flexible models, I recommend LLaMA for quality, or [Pythia Deduped](https://huggingface.co/models?search=pythia%20deduped) for compatibility and its ease to find_

- _For novel/co-writer finetunes, I recommend [Janeway](https://huggingface.co/models?sort=downloads&search=janeway) or [Erebus](https://huggingface.co/models?search=erebus) (NSFW)_

- _For AI Dungeon-style text adventures, I recommend [Nerys](https://huggingface.co/models?search=nerys)_

- _For a CharacterAI/Replika-style chatting partner, I recommend [Pygmalion](https://huggingface.co/models?search=pygmalion) (NSFW) and Erebus (NSFW)_

- _For a ChatGPT-esque assistant, I currently recommend [Vicuna](https://huggingface.co/models?search=vicuna)_

_If you wanna pick by size:_

- _If you have a standard computer, I'd recommend to start with a ~350M model from a series of your choice, and slowly work your way up to bigger models, so you can tell how much quality you're willing to gain, and performance you're willing to compromise. [Here's a memory usage chart](https://github.com/Crataco/ai-guide/blob/main/charts/memory-usage.md) I've made, and [another usage chart](https://github.com/oobabooga/text-generation-webui/wiki/System-requirements) by Oobabooga._

- _Alternatively, if you have a gaming computer (with NVIDIA cards being the best supported), you can fit the model entirely on the GPU itself, which will typically take up half as much video RAM as it does regular RAM, and be lightning fast. If you don't have enough VRAM, you can also split it between regular RAM and VRAM, but it will be much slower._

_If you're an advanced user, you're likely to reduce system requirements quite a lot by looking into [4-bit quantization](https://github.com/oobabooga/text-generation-webui/wiki/LLaMA-model#4-bit-mode) and other backends such as [llama.cpp](https://github.com/oobabooga/text-generation-webui/wiki/llama.cpp-models), [RWKV](https://github.com/oobabooga/text-generation-webui/wiki/RWKV-model), and the wonderfully-coded yet closed-source [TextSynth Server](https://bellard.org/ts_server/). The first three guides I've linked just now assume you're using oobabooga's Text Generation Web UI, which at the moment feels like the frontend with the best support for these._
