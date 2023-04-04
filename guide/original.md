# Crataco's guide to locally runnable, unfiltered open-source AI.

![A screenshot of a then-paranoid Crataco from three years ago, saying that they don't feel comfortable talking to online-based chatbots.](https://user-images.githubusercontent.com/55674863/229701829-ce014683-c9ca-43f4-9e62-f9128d9d7f4d.png)

# PREFACE

**TL;DR for chat users: [Pygmalion](https://rentry.org/pygmalion-ai) and [its community](https://old.reddit.com/r/PygmalionAI/) is a good place to start.**

**If you're here because you want to know more about AI frontends, models and tips, and want to get it running on your own PC, scroll down and start at "INTRODUCTION". The important stuff will be highlighted in bold at the beginning of most paragraphs to make them less overwhelming.**

I began this post before I learned about Pygmalion. This guide is strictly for all the solutions I know of, usually open-source, that you can run and host on your own computer. I'm not here to recommend other online services unless you can, too, run them offline, like [KoboldAI Lite](https://lite.koboldai.net/).

I highly recommend to take a look at the documentation for each of the frontends I explained in my own guide, and I would love for you to be a part of ***their*** communities to ask and answer questions, or just to check and see what developments are happening:

- [Pygmalion Guide and FAQ](https://rentry.org/pygmalion-ai) (profanity warning) - [Discord](https://discord.gg/ZHXEa3yywq) /  r/PygmalionAI

- [Miku.gg Documentation](https://docs.miku.gg/) - [Discord](https://discord.com/invite/XgXjvP6h)

- [Oobabooga's web UI documentation](https://github.com/oobabooga/text-generation-webui) - r/oobabooga

- [KoboldAI's documentation](https://github.com/KoboldAI/KoboldAI-Client/wiki) - [Discord](https://koboldai.org/discord) / r/KoboldAI

- [TavernAI's documentation](https://github.com/TavernAI/TavernAI) - *They have a channel in the KoboldAI Discord server*

* * *

# INTRODUCTION

**This post will list AI frontends and models that can be downloaded and run on your PC. I try my best to make this post beginner-friendly, even for those whose computers are not up to snuff. It includes information on frontends, models, character creation, model settings, how to contribute, and interesting findings.**

Chat users may be familiar with Replika, Character.AI, Kajiwoto, Anima, Chai, SimSimi, Paradot, or Mitsuku (Kuki).

Novel/Adventure users may be familiar with NovelAI and AI Dungeon.

You may also have an easier time understanding if you know about Stable Diffusion.

I want this to be a crash course and not an organized encyclopedia, so pardon if it seems lengthy. I hope for this to be a stepping stone for people to learn, try, and contribute with their own guides. My target demographic is the "average" user, but I'm trying to make it useful for everyone.

* * *

# FRONTENDS

**A frontend is the interface. There are three of them officially supported by this post: KoboldAI, TavernAI, and Oobabooga, with several others (including Project Akiko and LiteVN) that I've yet to test thoroughly. I refer to them as "standalone" if you can use them on their own, or "gateway" if they depend on another.**

**If your computer can't run the model you want to use, you can use Google Colab, an online service which allows you to use Google's cloud computers for free for a while, making them perfect for trying out bigger models. You usually still have an option to save conversations on your Google Drive and download them for offline use.**

### STANDALONE FRONTENDS

- **[Oobabooga's Text Generation Web UI](https://github.com/oobabooga/text-generation-webui) - [[screenshot using OPT 2.7B Erebus with "Sphinx Moth" preset]](https://cdn.discordapp.com/attachments/1042160561808482304/1081314051889578014/oobabooga.png) Standalone frontend with bleeding-edge model support and a brutalist UI. You'll feel right at home if [you're familiar with AUTO1111's Stable Diffusion UI](https://github.com/AUTOMATIC1111/stable-diffusion-webui/blob/master/screenshot.png), but it's not very user-friendly. You can run it locally or on [Colab](https://colab.research.google.com/github/oobabooga/AI-Notebooks/blob/main/Colab-TextGen-GPU.ipynb).**

- **[KoboldAI](https://github.com/koboldai/koboldai-client) - [[screenshot of OPT 6.7B Erebus on KoboldAI dev version]](https://cdn.discordapp.com/attachments/696416030410670124/1047134689133084762/Screenshot_2022-11-29_04-59-11.png) Standalone frontend with a professional exterior and a sweet community. KAI was created as an AI co-writer similar to NovelAI. They later included a chat setting, and more recently a Discord-esque chat UI as pictured. While it's more user-friendly than Oobabooga's, I find the "pretty" chat mode to be pretty buggy, so if you intend on using it for chatting, combine it with a gateway frontend (I recommend TavernAI). You can run it locally or on [Colab](https://colab.research.google.com/github/KoboldAI/KoboldAI-Client/blob/main/colab/TPU.ipynb).**

### GATEWAY FRONTENDS

- **[TavernAI](https://github.com/TavernAI/TavernAI) - Gateway frontend with a pretty, friendly chat-optimized interface. Supports KoboldAI, NovelAI, and OpenAI. I feel its main advantage is its "anchors" that are added to every message, which will help avoid standalone KAI's message-shortening pitfalls on non-Pygmalion models. I tried it again recently and learned that it even includes an [online character database](https://cdn.discordapp.com/attachments/1092245228028706867/1092245308651610222/Screenshot_2023-04-02_at_17-30-30_Tavern.AI.png). You can run it locally or on [Colab](https://colab.research.google.com/github/TavernAI/TavernAI/blob/main/colab/GPU.ipynb).**

- **[Silly TavernAI Mod](https://github.com/SillyLossy/TavernAI) - [[screenshot of Pygmalion 6B (experiment 7 part 4/10)]](https://cdn.discordapp.com/attachments/1069432262036295681/1092016634585157652/Screenshot_2023-04-02_02-16-26.png) - A fork of TavernAI. It's a huge rewrite with [extensions](https://github.com/SillyLossy/TavernAI-extras), group chats, and even support for Oobabooga's frontend.**

- [Project Akiko](https://github.com/Project-Akiko/Project-Akiko) - [[official screenshot]](https://user-images.githubusercontent.com/26259870/229264860-5632fe81-af11-4463-8e46-9707296b4d51.png) Both standalone(?) and gateway frontend, with its interface taking inspiration from visual novels. Just discovered this one via the KoboldAI Discord server. It's a very recent project that seems to go above and beyond for an open-source chatbot frontend, with planned support for Live2D, text-to-speech, multi-chat, and Discord. It reminds me of miku.gg, but with a more open ecosystem. I might bump this up as "supported" once I give it a shot, but it's too early to tell what direction the project's going to go in.

- [Laika's LiteVN UI for KoboldAI](https://laika-ch.itch.io/laikas-litevn-ui-for-koboldai) - [[official screenshot]](https://img.itch.zone/aW1hZ2UvMTk3NDg0My8xMTYxMzg0Ny5wbmc=/original/rvEmrz.png) Gateway frontend with a VN-esque interface. Compatible with KoboldAI. Also discovered this one via KoboldAI's Discord server. Much like Miku and Akiko, it takes a more visual novel-esque approach to talking to your AI companion. Pretty cool! Its source code is available to download and it's developed in Godot (think Unity but open-source), but the ready-to-run download looks to be Windows-only at the moment. I'll try it out.

There are other projects (such as [Gravital](https://github.com/johnnymcmike/Gravital), [Eliza](https://github.com/harubaru/eliza), [rwkv_chatbot](https://github.com/harrisonvanderbyl/rwkv_chatbot), [ChatRWKV](https://github.com/BlinkDL/ChatRWKV)), and [miku.gg](https://docs.miku.gg/) (as mentioned earlier)), but they're beyond the scope of this post due to their lack of community, complicated setup, or dependence on closed-source infrastructure.

* * *

# MODELS

**TL;DR: A model is the AI brain that generates your responses. Each model has different knowledge based on what data they were trained on. Bigger models are usually smarter, but require better hardware.**

**My recommendations:**

- **Jack-of-All-Trades (GPT-3) - [Pythia Deduped](https://huggingface.co/models?search=eleutherai/pythia%20deduped) and [LLaMA](https://huggingface.co/models?search=llama%20hf)**

- **Chatbot (Replika/CAI) - [Pygmalion](https://huggingface.co/PygmalionAI) (NSFW) / [Erebus](https://huggingface.co/models?sort=downloads&search=KoboldAI%2FErebus) (NSFW) / [ConvoGPT](https://huggingface.co/hakurei/convogpt-staging/tree/main)**

- **Assistant (ChatGPT) - [Open-Assistant](https://huggingface.co/OpenAssistant/oasst-sft-1-pythia-12b) / [GPT4All](https://github.com/nomic-ai/gpt4all)**

- **Co-Writer (NovelAI) -  [Janeway](https://huggingface.co/models?search=janeway) / [Erebus](https://huggingface.co/models?sort=downloads&search=KoboldAI%2FErebus) (NSFW)**

- **Text Adventure (AI Dungeon) - [Nerys](https://huggingface.co/models?search=nerys) / [Skein](https://huggingface.co/KoboldAI/GPT-J-6B-Skein) / Adventure [1.3B](https://huggingface.co/KoboldAI/GPT-Neo-1.3B-Adventure) / [2.7B](https://huggingface.co/KoboldAI/GPT-Neo-2.7B-AID) / [6B](https://huggingface.co/KoboldAI/GPT-J-6B-Adventure)**

- **Budget Users - [Pythia Deduped](https://huggingface.co/models?search=eleutherai/pythia%20deduped) / [OPT](https://huggingface.co/models?search=facebook/opt) / [llama.cpp (advanced)](https://github.com/ggerganov/llama.cpp)**

For more clarification, there are different "types" of models. What I say is *very* simplified:

- **Transformers** types are widely-used on most major frontends (KAI/TAI and Oobabooga). They have the best compatibility and most models available (GPT-2, GPT-Neo, BLOOM, Pythia, etc), include most finetunes like Pygmalion, and are likely your first go-to. CPU users get "32-bit" models and GPU users can cut them down to "16-bit". The "bits" are how accurate the model is at the cost of RAM/VRAM usage.

- The **RWKV** type is exclusive to the RWKV model series, but as far as I know it works on Oobabooga's interface and KoboldAI. It can hold more in its memory, and has support for compressing the model down to 8-bit precision, cutting down RAM usage substantially.

- The **llama.cpp** type is currently exclusive to llama.cpp, but it has been included in [Oobabooga](https://github.com/oobabooga/text-generation-webui/wiki/llama.cpp-models) and a [Kobold-like interface](https://github.com/LostRuins/llamacpp-for-kobold). It's developed to work in "4-bit" on CPU, saving model space *and* memory usage. To the point that on my computer with 16GB RAM, I was able to run 7B and 13B without a problem (with 30B being my "upper limit"), which are models that I believe would consume *eight times as much* if it were Transformers-based.

* * *

### DETAILED INFORMATION

Here are all of the major model series usable on most frontends, and finetunes:

Series | Generic model | Novel model | NSFW model | Chat model | My thoughts
:--|:--:|:--:|:--:|:--:|:--:
**GPT-2** | [124M](https://huggingface.co/gpt2) to [1.5B](https://huggingface.co/gpt2-xl) | Novel [774M](https://storage.henk.tech/KoboldAI/Novel%20model%20774M.rar) | Smut [774M](https://storage.henk.tech/KoboldAI/Smut%20model%20774M%2030K.rar) | DialoGPT [124M?](https://huggingface.co/microsoft/DialoGPT-small) to [774M](https://huggingface.co/microsoft/DialoGPT-large) / HourAI [355M?](https://huggingface.co/archmagos/HourAI) | *GPT-2 kickstarted modern AI text generation, and was most notably used for [the original AI Dungeon 2](https://www.reddit.com/r/rpg/comments/e7ladj/someone_made_an_ai_dungeon_master_that_you_can/). You can finetune smaller models on the weakest of hardware. It can only hold half as much text in memory as every model that followed, and only goes up to 1.5B, so I don't recommend it today.*
**GPT-Neo / GPT-J** | [125M](https://huggingface.co/EleutherAI/gpt-neo-125M) to [20B](https://huggingface.co/EleutherAI/gpt-neox-20b) | Janeway [2.7B](https://huggingface.co/KoboldAI/GPT-Neo-2.7B-Janeway) to [6B](https://huggingface.co/KoboldAI/GPT-J-6B-Janeway) / Horni-LN [2.7B](https://huggingface.co/KoboldAI/GPT-Neo-2.7B-Horni-LN) | Shinen [2.7B](https://huggingface.co/KoboldAI/GPT-Neo-2.7B-Shinen) to [6B](https://huggingface.co/KoboldAI/GPT-J-6B-Shinen) / Horni [2.7B](https://huggingface.co/KoboldAI/GPT-Neo-2.7B-Horni) | ConvoGPT [125M](https://huggingface.co/hakurei/convogpt/tree/main/125m-uft) to [6B](https://huggingface.co/hakurei/convogpt/tree/main/6b-uft) / Pygmalion [2.7B](https://huggingface.co/PygmalionAI/pygmalion-2.7b) to [6B](https://huggingface.co/PygmalionAI/pygmalion-6b) | *EleutherAI's debut model, trained on a public dataset called "The Pile". It's the "ol' reliable" of text generation. I feel like Neo has most of the community support and finetunes.*
**OPT** | [125M](https://huggingface.co/facebook/opt-125m) to [66B](https://huggingface.co/facebook/opt-66b) | Nerys [350M](https://huggingface.co/KoboldAI/OPT-350M-Nerys-v2) to [13B](https://huggingface.co/KoboldAI/OPT-13B-Nerys-v2) | Erebus [350M](https://huggingface.co/KoboldAI/OPT-350M-Erebus) to [13B](https://huggingface.co/KoboldAI/OPT-13B-Erebus) | Pygmalion [350M](https://huggingface.co/Pygmalion-AI/pygmalion-350m) / ChatSalad [19M](https://huggingface.co/concedo/OPT-19M-ChatSalad) | *A model series by Meta, succeeding Fairseq, their previous. It outperforms Neo in quality by a noticeable margin, but feels slightly different in a way. It comes second to Neo in terms of the sheer quantity of finetunes and community experience.*
**RWKV** | [169M](https://huggingface.co/BlinkDL/rwkv-4-pile-169m) to [14B](https://huggingface.co/BlinkDL/rwkv-4-pile-14b) | Not yet | Not yet | Not yet | *A promising series trained on Neo's dataset that intends to be faster and lighter without compromising on quality. Quality-wise I believe it's on par with GPT-Neo.*
**BLOOM** | [560M](https://huggingface.co/bigscience/bloom-560m) to [176B](https://huggingface.co/bigscience/bloom) | Not yet | Not yet | [BloomZ](https://huggingface.co/bigscience/bloomz) (ChatGPT-esque) | *BigScience's BLOOM may be one of the more well-known model series of this list. Unfortunately, hearsay on the KoboldAI Discord server, model evaluation statistics, and [even Pygmalion's 11b](https://huggingface.co/PygmalionAI/pygmalion-6b/discussions/20#6414ac35b6e553f665e1e453) tell me that BLOOM gives lower quality results compared to the other models listed, likely thanks to its multilingual dataset (thus lack of focus on English). I personally don't recommend it, but I've heard some users get good results with it, so knock yourself out!*
**Pythia** | [70M](https://huggingface.co/EleutherAI/pythia-70m-deduped) to [12B](https://huggingface.co/EleutherAI/pythia-12b-deduped) | Not yet | Not yet | Pygmalion [1.3B](https://huggingface.co/Pygmalion-AI/pygmalion-1.3b) / [Lotus 12B](https://huggingface.co/hakurei/lotus-12B) / [OpenAssistant 12B](https://huggingface.co/OpenAssistant/oasst-sft-1-pythia-12b) | *Another model series by EleutherAI. The one I recommend is the "Deduped" series, trained on a "cleaned" Pile and [according to official evaluations it outperforms GPT-Neo and OPT](https://huggingface.co/EleutherAI/pythia-2.8b-deduped#evaluations). Even Harubaru of Waifu Diffusion and ConvoGPT fame [acknowledged](https://cdn.discordapp.com/attachments/1042160561808482304/1068087246118473728/Screenshot_2023-01-26_00-35-43.png) its [potential](https://cdn.discordapp.com/attachments/1042160561808482304/1068087245799686144/Screenshot_2023-01-26_00-35-55.png) and later used it for their Lotus 12B model.*
**LLaMA** | 7B to 65B | Not yet | Not yet | [Alpaca 7B](https://github.com/tloen/alpaca-lora) / [GPT4All](https://github.com/nomic-ai/gpt4all) / [Vicuna](https://vicuna.lmsys.org/) | *New model by Meta. Officially only available to researchers. AI evaluation says 13B is on par with GPT-3 175B, and 7B overtakes even Pythia 12B and OPT 66B. The Transformers version of the model [is available via reuploads](https://huggingface.co/models?search=llama%20hf), and the llama.cpp version can be used by downloading [one of these](https://huggingface.co/maderix/llama-65b-4bit/tree/main), a tokenizer from [here](https://huggingface.co/decapoda-research/llama-7b-hf/tree/main) or [here](https://huggingface.co/nyanko7/LLaMA-7B/tree/main), and converting them.*
**Cerebras** | [111M](https://huggingface.co/cerebras/Cerebras-GPT-111M) to [13B](https://huggingface.co/cerebras/Cerebras-GPT-13B) | Not yet | Not yet | Not yet | *New model in general. According to their description their models use The Pile much like GPT-Neo, Pythia and RWKV, but it isn't deduplicated. I'll likely look into it.*

* * *

### SCREENSHOTS

Generic models:

**Model screenshot** | **Settings** | **Comments**
:--|:--:|:--:
[BLOOM 1.1B](https://cdn.discordapp.com/attachments/1042160561808482304/1087637541315956786/bloom-1b1.png) | ["Naive" preset](https://github.com/oobabooga/text-generation-webui/blob/45b7e53565ee0151cdbe2aa5760cfdf05f696d5c/presets/Naive.txt) with rep_penalty of 1.1 | Sometimes it's there. Sometimes it's not.
[BLOOM 1.7B](https://cdn.discordapp.com/attachments/1042160561808482304/1087638876413239296/bloom-1b7.png) | "Naive" preset with rep_penalty of 1.05 | This one actually surprised me, as I rarely ever use BLOOM and doubted its capabilities.
[BLOOM 3B](https://cdn.discordapp.com/attachments/1042160561808482304/1087641824321097738/bloom-3b.png) | "Naive" preset with rep_penalty of 1.02; may need to be between 1.03-1.04 | The AI is a bit hit-and-miss, but that's to be expected for a 3B model. I was caught off-guard by its acknowledgement of My Hero Academia.
[GPT-Neo 1.3B](https://cdn.discordapp.com/attachments/1042160561808482304/1068341177419571352/neo-1.3b.png) | In screenshot | This, too, surprised me; I remember GPT-Neo 1.3B being much worse. This does a decent job at following conversation.
[GPT-Neo 2.7B](https://cdn.discordapp.com/attachments/1042160561808482304/1088509745859670036/Screenshot_2023-03-23_10-08-45.png) | "Naive" preset with rep_penalty of 1.5 | Somehow as bad as I remember. It could just be the settings, though.
[LLaMA 7B (HF)](https://cdn.discordapp.com/attachments/1042160561808482304/1087680050121429014/llama-7b-naive.png) | "Naive" preset | Naive preset plays it safe, but the responses are short. I notice LLaMA doesn't require repetition penalty as much as other models do; 1.0 is just fine here.
[LLaMA 7B (HF)](https://cdn.discordapp.com/attachments/1042160561808482304/1087683927080177744/llama-7b-sphinx.png) | "Sphinx Moth" preset | The Sphinx Moth preset is the opposite: the responses are lengthy yet very risk-taking (it hallucinated websites that don't exist, but I just went with it). I might need to find a preset that's kind of in-between.
[LLaMA 13B (GPTQ)](https://cdn.discordapp.com/attachments/1092245228028706867/1092524304811442176/Screenshot_2023-04-03_12-01-06.png) | "Naive" preset | Unusual case. I had to use GPTQ and a quantized version of the model to run it on my hardware (in my experience, LLaMA 7B GPTQ gave worse results than HF). So far, this one does the best job at following the character's introduction prompt (as Alice introduces herself as a fairy). The results are decent, but I feel like "Naive" keeps it too safe.
[LLaMA 13B (GPTQ)](https://cdn.discordapp.com/attachments/1092245228028706867/1092528952691666955/Screenshot_2023-04-03_12-19-48.png) | [Custom preset](https://cdn.discordapp.com/attachments/1092245228028706867/1092526311114821652/Screenshot_2023-04-03_12-09-21.png) | Results are great, but need further tweaking.
[LLaMA 13B (GPTQ)](https://cdn.discordapp.com/attachments/1092245228028706867/1092530174760849512/Screenshot_2023-04-03_12-24-42.png) | Custom preset | I've turned up top-p to 1.0. The responses seem longer, but it went off the rails REAL quick.
[LLaMA 13B (GPTQ)](https://cdn.discordapp.com/attachments/1092245228028706867/1092533241375883375/Screenshot_2023-04-03_12-36-50.png) | Custom preset | To make up for it, I lowered the temperature to 0.6 and raised the repetition penalty to 1.05. Temperature might need to be lowered some more since it keeps making up new things, but that's to be expected with the little information I've given the AI. (I think top-k 1.0 contributes to longer messages at the cost of making more assumptions?)
[Pythia 70M Deduped](https://cdn.discordapp.com/attachments/1042160561808482304/1068266121679085649/Screenshot_2023-01-26_at_20-27-23_Gradio.png) | In screenshot | Unusable.
[Pythia 160M Deduped](https://cdn.discordapp.com/attachments/1042160561808482304/1068267846406258849/Screenshot_2023-01-26_12-31-37.png) | In screenshot | I might've just gotten lucky with this one.
[Pythia 410M Deduped](https://cdn.discordapp.com/attachments/1042160561808482304/1068269127808073830/Screenshot_2023-01-26_12-39-36.png) | In screenshot | I think it's getting better!
[Pythia 1B Deduped](https://cdn.discordapp.com/attachments/1042160561808482304/1068272690667978805/Screenshot_2023-01-26_at_20-53-28_Gradio.png) | In screenshot | Probably the smallest model I can use that feels like a decent conversational partner. Quality is on par (maybe *slightly* better than) GPT-Neo 1.3B.
[Pythia 1.4B Deduped](https://cdn.discordapp.com/attachments/1042160561808482304/1068275944592265357/paste2.png) | In screenshot | *No comment.*
[Pythia 2.8B Deduped](https://cdn.discordapp.com/attachments/1042160561808482304/1068336717700018186/Screenshot_2023-01-26_17-05-53.png) | In screenshot | *No comment.*
[Pythia 6.9B Deduped](https://cdn.discordapp.com/attachments/1042160561808482304/1068357188147482634/6.9B.png) | In screenshot | It may just be me, but I notice a decline in Pythia's performance and start to prefer, say, GPT-J 6B and LLaMA 7B.
[Pythia 12B Deduped](https://cdn.discordapp.com/attachments/1042160561808482304/1079874544505987183/pythia-12b-deduped.png) | "Sphinx Moth" preset | May be the most impressive results I've ever gotten with an open-source, self-hostable chatbot.

Chat-friendly models:

**Model screenshot** | **Finetuned on** | **Settings** | **Comments**
:--|:--:|:--:|:--:
[ConvoGPT 1.3B](https://cdn.discordapp.com/attachments/1042160561808482304/1088515534510899261/Screenshot_2023-03-23_10-30-27.png) | GPT-Neo 1.3B | "Default" preset | Surprisingly good, but may just be luck.
[ConvoGPT 2.7B](https://cdn.discordapp.com/attachments/1042160561808482304/1088513752724418580/Screenshot_2023-03-23_10-24-47.png) | GPT-Neo 2.7B | "Default" preset | 2.7B is barely an upgrade. I don't think it warrants twice as much RAM usage.
[ConvoGPT 6B](https://cdn.discordapp.com/attachments/1042160561808482304/1088505891294302299/Screenshot_2023-03-23_09-53-35.png) | GPT-J 6B | "Default" preset | Short responses, but never goes off-topic. I might retest ConvoGPT 6B soon with a better prompt.
[ConvoGPT 6B](https://cdn.discordapp.com/attachments/1042160561808482304/1088507680093642902/Screenshot_2023-03-23_10-00-38.png) | GPT-J 6B | "Sphinx Moth" preset | Responses are a little longer. High temperature means it also goes off-topic.
[Pygmalion 6B](https://cdn.discordapp.com/attachments/1042160561808482304/1090065571225272421/image.png) | GPT-J 6B | [Pygmalion preset](https://github.com/oobabooga/text-generation-webui/blob/3ffd7d36fd2a268367b73a5601404319841222e1/presets/Pygmalion.txt) | Experiment 2, the current "main" version. This is the first time I give Pygmalion a proper test, and so far it surprised me.
[Pygmalion 6B](https://cdn.discordapp.com/attachments/1042160561808482304/1090073097073328228/image.png) | GPT-J 6B | Pygmalion preset | Experiment 7, Part 4/10. Pretty good!

[Prompts used.](https://pastebin.com/1G816dPQ)

For more information on generation quality and memory usage:

**[[Model evaluation statistics]](https://pastebin.com/M3uESsyZ)** (higher is better)

**[[Memory and performance benchmark]](https://pastebin.com/VjJuRjMd)**

**[[Memory usage (Oobabooga's UI)]](https://github.com/oobabooga/text-generation-webui/wiki/System-requirements)**

* * *

**The community's recommendations:**

- [PygmalionAI's models](https://huggingface.co/PygmalionAI). They're the closest we've got to an open-source CharacterAI. Their model is still training and relies on user contributions. It has been updated several times and is available in two branches: the [main branch](https://huggingface.co/PygmalionAI/pygmalion-6b/tree/main) and the [development branch](https://huggingface.co/PygmalionAI/pygmalion-6b/tree/dev). They also document their training progress via [logbooks](https://github.com/PygmalionAI/logbooks).

- [Mr. Seeker's Erebus models](https://huggingface.co/models?search=koboldai%20erebus), available in sizes as small as [350M](https://huggingface.co/KoboldAI/OPT-350M-Erebus) for weak hardware, to as big as [20B](https://huggingface.co/KoboldAI/GPT-NeoX-20B-Erebus) for cloud computers. It was popular in the KoboldAI community for NSFW writing and even chatting because of its manually-curated NSFW dataset, and thus its better understanding of intimacy compared to generic models. If Pygmalion doesn't work too well for your use case, Erebus is worth trying out instead.

**Other ones I've toyed around with:**

- [Pythia Deduped](https://huggingface.co/models?other=pythia) is my primary choice if I value coherence and have limited hardware. I've seen good results as early as 1B [[screenshot]](https://cdn.discordapp.com/attachments/1042160561808482304/1068272690667978805/Screenshot_2023-01-26_at_20-53-28_Gradio.png). Or 410M [[screenshot]](https://cdn.discordapp.com/attachments/1042160561808482304/1068269127808073830/Screenshot_2023-01-26_12-39-36.png). Or maybe even 160M [[screenshot]](https://cdn.discordapp.com/attachments/1042160561808482304/1068267846406258849/Screenshot_2023-01-26_12-31-37.png)? It's trained on a cleaner dataset, and its low-end models are the best I've seen (if you have an old, slow, or exotic computer like a Pi or an Android phone running [Termux](https://termux.dev/en/)). It's a generic model, a jack-of-all-trades and master of none, meaning it's not trained on a chat-oriented dataset. It may require a push in the right direction for it to chat how you want it to. But it's *usually* going to be "smarter" than a Neo model of the same size (6.9B is debatable, as I've had better luck with GPT-J).

- [RWKV-4](https://huggingface.co/models?search=blinkdl/rwkv) is one I'm currently experimenting with. Oobabooga's Web UI recently added mostly-complete support for it, but it hasn't been getting much attention. It but introduces some great features such as bigger context length (memory) and experimental quantization (which saves memory). From my personal testing, performance seems closer to GPT-Neo's.

- [convoGPT](https://huggingface.co/hakurei/convogpt-staging) (trained on top of GPT-Neo/GPT-J) if I value better conversational knowledge and/or have better hardware. convoGPT 6B is strangely-enough referred to as "litv2-6B-rev2" (with "Lit" being harubaru's novel model) in its config. But yeah, I'd consider it tied with Erebus. It feels like the spiritual successor of the older "convo-6B" model released by the same person, and [was used as the base model for Pygmalion](https://huggingface.co/PygmalionAI/pygmalion-6b). While I'm at it, [Lotus 12B](https://huggingface.co/hakurei/lotus-12B) may count as part of the same series, if not a successor, but it's reached nowhere near the popularity Pygmalion has.

- [GPT-J 6B Janeway](https://huggingface.co/KoboldAI/GPT-J-6B-Janeway) is my previous secondary. [It's oddly satisfying using a model trained on literature.](https://cdn.discordapp.com/attachments/1042160561808482304/1067256974439362610/Screenshot_2023-01-23_17-37-28.png)

If you don't speak English or instead prefer to speak in your native tongue, Oobabooga's text generation web UI has an extension supporting on-the-fly Google Translate so you can take advantage of the English-focused models. [This is a screenshot with Pythia 1.4B Deduped](https://cdn.discordapp.com/attachments/1042160561808482304/1079117202445303848/test.png) using the Google Translate extension for Japanese. The alternative would be to search for models in your native language (i.e. [Spanish](https://huggingface.co/models?pipeline_tag=text-generation&language=es&sort=downloads) or [Japanese](https://huggingface.co/models?pipeline_tag=text-generation&language=ja&sort=downloads) for starters).

* * *

# CREATE YOUR CHARACTER / BROWSE FOR OTHERS

**TL;DR: I believe these work best with TavernAI and Oobabooga with the Pygmalion model:**

- [Zoltan's "Character Creator"](https://zoltanai.github.io/character-editor/)

- [oobabooga's Pygmalion Character Creator](https://oobabooga.github.io/character-creator.html)

- [YuriFag's Pygmalion Character Creation Tips](https://rentry.org/PygTips) (NSFW)

- [Pygmalion Character Card Gallery](https://booru.plus/+pygmalion) (NSFW)

- [YuriFag's Pygmalion Bot Prompts](https://rentry.org/pygbotprompts) (NSFW) (found on /aicg/)

- [BotPrompts.net](https://botprompts.net/) (NSFW) (found on /aicg/)

**The following is my own guide, and applies to KoboldAI and non-Pygmalion models.**

There are two primary methods to create characters (let's call her "Alice" for the sake of this example). You type these in the model's "memory" or "context":

- Everyday language. "Alice is an android woman. She's cheerful and loves video games." It's a universally understood format, and Pygmalion models prefer them, referring to it as the character's "persona." - [[Example on KoboldAI]](https://cdn.discordapp.com/attachments/1042160561808482304/1066237741932761249/Screenshot_2023-01-20_22-07-27.png)

- Programming-style syntax (W++). Most models trained on The Pile (GPT-Neo, likely OPT and Pythia too) are said to follow it better than everyday language. - [[Example on KoboldAI]](https://cdn.discordapp.com/attachments/1042160561808482304/1066237101823242312/Screenshot_2023-01-20_22-04-54.png)

*To learn more about W++, the KoboldAI GitHub [has a write-up on it](https://github.com/KoboldAI/KoboldAI-Client/wiki/Pro-Tips), and if you aren't using United's built-in W++ editor, Noli provides an [online interface](https://nolialsea.github.io/Wpp/) you can use to easily create characters with said syntax.*

After creating the character, you'll have to provide an example conversation. This means simulating a conversation beforehand, with you talking with and for the character, giving you slightly more control in advance on how you want your character to talk, how lengthy you want their sentences to be, etc. You may be lucky, but [I cannot stress this enough -- writing a short example conversation is important if you want the AI to have an idea on how you want your companion to talk.](https://cdn.discordapp.com/attachments/1042160561808482304/1069412502905028678/Screenshot_2023-01-29_16-18-32.png)

Also, as an extra precautionary measure, I like to add this into the context (AI's memory):

> *This is a conversation between you and Alice.*

or, if you prefer to use your own chat name:

> *This is a conversation between <your chat name> and Alice.*

If the AI makes too much assumptions on your behalf (i.e. talking about meeting you at school, working for a company), I'd imagine it'd help to add something like:

> *This conversation is the first time you and Alice meet.*

Or something a little more IRC-like, but I haven't done any testing:

> *You entered the chat.*
>
> *Alice entered the chat.*

* * *

# MODEL SETTINGS

**TL;DR: You can influence how the models generate by changing your settings. For well-supported models, try the defaults. If not the defaults, try the presets (I've had talkative -- and at times, unpredictable -- results with Sphinx Moth and Ouroburos while testing Erebus 2.7B, ConvoGPT 6B and Pythia 12B Deduped). But if you're a DIY user, tweak with the settings, which I describe to the best of my knowledge in this section.**

This guide focuses on the settings present in KoboldAI/TavernAI (via KAI). They're also available in the Text Generation UI, but instead go by their [Huggingface codenames](https://huggingface.co/docs/transformers/main_classes/text_generation#transformers.GenerationConfig).

- **"Temperature"** (`temperature`), which affects how creative the AI's responses are. If the AI plays it too safe for you, turn it up. If the AI is too chaotic, turn it down. On KoboldAI, I find 0.5-0.7 a good balance for GPT-Neo and OPT. On oobabooga's text UI, I was able to get good results as high as 2.0 using larger Pythia models just as long as `top-k` is enabled (without it I get word salad).

- **"Repetition penalty"** (`repetition_penalty`). If you find the AI repeating you or itself, turn it up and regenerate. If the AI starts spouting random garbage like a run-on sentence, turn it down and regenerate. Sometimes, you may want to tweak it just to give the AI a bit more diversity even if it isn't repeating a sentence. Back when I used KoboldAI I found 1.75-2.0 to be good for GPT-Neo 2.7B, 1.2 to be good for GPT-J, 1.1 to be good for OPT, and smaller values (between 1.0 to 1.1) to be good for Pythia Deduped.

- **"Context Tokens"** (KoboldAI) refers to how much of the conversation ("tokens") the AI will remember. [A token is about ~4 characters.](https://old.reddit.com/r/NovelAi/comments/nohvse/can_someone_explain_what_exactly_is_an_ai_token/) The max is 2,048 (about ~8,000-9,000 characters) for all models (excluding GPT-2), and while you can increase the maximum tokens beyond that, it is unsupported and will likely break.

- **"Output Length"** (`max_new_tokens`) is the upper limit of how long the AI's response can be, in tokens.

- **"Gens Per Action"** (KoboldAI) is how many messages the AI will generate, which you can then choose between. Much like CAI's "swiping" feature.

- **"Typical sampling"** (`typical_p`). Definitely not the most talked-about setting, but my favorite. My understanding is that with the setting below 1, the AI chooses less-likely words, which keep its sentences diverse and less predictable. It gives me a better illusion of "intelligence" by making a slight impact into the AI's vocabulary. While the research paper recommends a value of 0.2, I find 0.9/0.95 being good enough for most models I've used.

- Others (such as top-p, top-k, top-a, and tail-free sampling) can also influence your output, but are difficult to explain. These settings all change which words the AI would predict next, I should think.

* * *

# [CONTRIBUTING](https://i.kym-cdn.com/photos/images/original/002/182/171/eb0.jpg)

After doing quite a bit of research, [PygmalionAI actually has some documentation](https://rentry.org/pygmalion-ai) and [tells you how you can contribute your CharacterAI chatlogs](https://rentry.org/chatlog-dumping). You have the option whether or not you want to include your data as part of their private dataset, or a public dataset. You can help advance the effort this way and make their Pygmalion models functionally close to CharacterAI as it is now (minus the "Chat Errors"), even if the quality isn't perfectly on par.

If you have some Python knowledge, you could always contribute to the projects I've listed above, and if you don't, you could always report bugs via its GitHub. You could also participate in [Kobold's Discord](https://koboldai.org/discord/) and, if you're somewhat knowledgeable, you could help people out, or report your results when investigating new models, like the new Pythia or Pygmalion models.

And lastly, if you know how to finetune, have a dataset and the right hardware, you can contribute your own finetunes to [Hugging Face](https://huggingface.co/).

* * *

# SPECIAL THANKS!

*I've created this section to give a shout-out to those who I feel my post wouldn't have been the same without:*

- u/DarthReplicant for laying the foundation of open-source chatbots by creating Project Replikant

- u/mrseeker for active contribution to the open-source AI community by openly releasing Janeway, Nerys, Erebus, etc.

- u/aid_throwaway for creating KoboldAI, u/henk717 (former developer of AI Dungeon 2 Unleashed) for maintaining it, and the rest of the KoboldAI developers and community for keeping the project alive and up-to-date

- u/bo_peng for developing and training RWKV, which motivated me to add a "Special Thanks" section

- u/Udongeein for training and releasing c1-6B, convo-6B, and the convoGPT model series

- 0x000011b (not sure of their Reddit) for developing the CharacterAI Dumper and for playing a big part in the Pygmalion project

That's about it. Thanks for reading!
