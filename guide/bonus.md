_Here's a little extra section. It's not my primary focus, but I wanted to add it here for good measure._

# Finetunes

### What are finetunes?

_Finetunes are AI models trained using another model as a base. This gives it specific knowledge and a leaning towards a specific subject or format._

_Here is my list of finetunes based on the model's target subject. Finetunes aren't exclusive to one use case, though. You can still use, say, a novel-friendly model for chatting purposes, with varying degrees of success._

_Expect this to be messier than my other lists, and I only include notable finetunes. The links may either link to the homepage or the direct download, so be warned._

***

### Adventure-friendly (AI Dungeon)
Finetune | Base model | Link | Thoughts
:--:|:--:|:--:|:--:
AI Dungeon 2 | GPT-2 | 1.5B [(fp32)](https://web.archive.org/web/20211120061227/https://storage.henk.tech/KoboldAI/model_v5_pytorch.zip) / [(fp16)](https://web.archive.org/web/20211120061148/https://storage.henk.tech/KoboldAI/aid-16bit.zip) | _Used by [the original AI Dungeon project](https://github.com/Latitude-Archives/AIDungeon) (confusingly named "AI Dungeon 2" as a successor to an earlier, similar project) before it switched to GPT-3. Trained on the infamous [`text_adventures.txt`](https://gitgud.io/AuroraPurgatio/aurorapurgatio)._
KoboldAI's AID | GPT-Neo | [125M](https://huggingface.co/Merry/AID-Neo-125M), [2.7B](https://huggingface.co/KoboldAI/GPT-Neo-2.7B-AID) | _Early adventure models trained on `text_adventures.txt`._
KoboldAI's Adventure | GPT-Neo, GPT-J | [1.3B](https://huggingface.co/KoboldAI/GPT-Neo-1.3B-Adventure), [6B](https://huggingface.co/KoboldAI/GPT-J-6B-Adventure) | _Later adventure models trained on CYOA stories._
Skein | GPT-J, GPT-NeoX | [6B](https://huggingface.co/KoboldAI/GPT-J-6B-Skein), [20B](https://huggingface.co/KoboldAI/GPT-NeoX-20B-Skein) | _Trained on CYOA stories and light novels._
Nerys V1 | Fairseq | [2.7B](https://huggingface.co/KoboldAI/fairseq-dense-2.7B-Nerys), [13B](https://huggingface.co/KoboldAI/fairseq-dense-13B-Nerys) | _Trained by Mr. Seeker on CYOA stories, ebooks, and light novels. I believe this is meant to be the successor to the Janeway model, which is explained below. It can also be used for novel writing._
Nerys V2 | OPT | [350M](https://huggingface.co/KoboldAI/OPT-350M-Nerys-v2), [2.7B](https://huggingface.co/KoboldAI/OPT-2.7B-Nerys-v2), [6.7B](https://huggingface.co/KoboldAI/OPT-6B-nerys-v2), [13B](https://huggingface.co/KoboldAI/OPT-13B-Nerys-v2) | _Trained by Mr. Seeker on CYOA stories, ebooks, and light novels. Same as before, but cleaned._

### Assistant-friendly (ChatGPT / Bard)
*It should be easy to find reuploads and mirror links of these on [Huggingface](https://huggingface.co/). I don't know too much about LLaMA nor have much interest in assistant models at the moment, so my commentary on these won't be thorough.*
Finetune | Base model | Link | Thoughts
:--:|:--:|:--:|:--:
Open Assistant | Pythia Deduped | [All](https://huggingface.co/OpenAssistant) | _This is a project by Open Assistant, which seems to be some sort of community or foundation dedicated to revolutionizing open-source text generation AI the same way Stable Diffusion revolutionzed open-source image generation. [Here's the link to their page](https://open-assistant.io/)._
Alpaca-LoRA | LLaMA | [7B](https://huggingface.co/chansung/gpt4-alpaca-lora-7b), [13B](https://huggingface.co/chansung/gpt4-alpaca-lora-13b), [30B](https://huggingface.co/chansung/gpt4-alpaca-lora-30b), [65B](https://huggingface.co/chansung/alpaca-lora-65b) | _I can't comment too much on this one, but from what I understand, Alpaca was originally a project by Stanford researchers that wasn't released to the public, and this is an open-source replication. As far as I know it's trained on data from ChatGPT conversations._
GPT4All | LLaMA | [7B](https://github.com/nomic-ai/gpt4all#original-gpt4all-model-based-on-gpl-licensed-llama) | _Filtered/unfiltered. No comment. [They have their own website, though](https://gpt4all.io/index.html)._
GPT4All-J | GPT-J | [6B](https://github.com/nomic-ai/gpt4all#gpt4all-j-an-apache-2-licensed-gpt4all-model) | _Wait, there's a GPT-J one?_
GPT-4 x Alpaca | LLaMA | [13B](https://huggingface.co/chavinlo/gpt4-x-alpaca) | _Unfiltered. This is my favorite model right now. This one follows instructions **very** well, and I've had great success using it for chatbots and text adventures. [Henk717 of KoboldAI also expressed its support for writing fiction](https://old.reddit.com/r/LocalLLaMA/comments/12lksqo/ai_showdown_gpt4xalpaca_vs_vicuna_gpt4_as_the/jg7imd3/) and [NSFW/chat content](https://cdn.discordapp.com/attachments/1092245228028706867/1097350145546387456/Screenshot_2023-04-16_19-37-32.png). In my experience, though, while it's great at chat content, NSFW is hit-and-miss. Try it yourself!_
Vicuna | LLaMA | [7B](https://huggingface.co/lmsys/vicuna-7b-delta-v1.1), [13B](https://huggingface.co/lmsys/vicuna-13b-delta-v1.1) | _Filtered. One of the few LLaMA finetunes I've tested, and it feels like a very ChatGPT-like model. [They have their own website](https://vicuna.lmsys.org/)._
Koala | LLaMA | [All (7B & 13B)](https://huggingface.co/young-geng/koala/tree/main) | _Filtered. No comment. [They have their own website](https://bair.berkeley.edu/blog/2023/04/03/koala/)._
Dolly V1 | GPT-J | [6B](https://huggingface.co/databricks/dolly-v1-6b) | _No comment._
Dolly V2 | Pythia Deduped | [3B](https://huggingface.co/databricks/dolly-v2-3b), [7B](https://huggingface.co/databricks/dolly-v2-7b), [14B](https://huggingface.co/databricks/dolly-v2-12b) | _No comment._
Instruct 12B | Pythia Deduped | [12B](https://huggingface.co/hakurei/instruct-12b) | _An instruct model trained by Hakurei._

### Chat-friendly (Replika / CharacterAI)
Finetune | Base model | Link | Thoughts
:--:|:--:|:--:|:--:
c1-6B | GPT-Neo, GPT-J | Down | _Early chatbot model trained by Hakurei on dialogue and Discord chatlogs. There were both a 1.3B and 6B available. It was later removed [due to privacy concerns](https://cdn.discordapp.com/attachments/1092245228028706867/1096634323718914068/Screenshot_2023-04-14_20-12-52.png). The repository used to reproduce the dataset is [still available here](https://github.com/peng-kevin/convo-dataset)._
convo-6B | GPT-J | Down | _Successor of c1. There was a 6B available, but was taken down._
convoGPT | GPT-Neo, GPT-J | [125M](https://huggingface.co/hakurei/convogpt-staging/tree/main/125m-uft), [1.3B](https://huggingface.co/hakurei/convogpt-staging/tree/main/1.3b-uft), [2.7B](https://huggingface.co/hakurei/convogpt-staging/tree/main/2.7b-uft), [6B](https://huggingface.co/hakurei/convogpt-staging/tree/main/6b-uft) | _New project by Hakurei. It's good for chatting performance, but public documentation is scarce._
Pygmalion | OPT, Pythia Deduped, GPT-Neo, GPT-J | [350M](https://huggingface.co/PygmalionAI/pygmalion-350m), [1.3B](https://huggingface.co/PygmalionAI/pygmalion-1.3b), [2.7B](https://huggingface.co/PygmalionAI/pygmalion-2.7b), [6B](https://huggingface.co/PygmalionAI/pygmalion-6b) | _The most popular chatbot model on this list. Its training data consists of a mix between user-contributed CharacterAI chatlogs and other dialogue, whether real or machine-generated._

### Novel-friendly (NovelAI)
_NovelAI's models are based on actual released models (from what I understand, Euterpe is Fairseq 13B, and Krake is GPT-NeoX 20B), so you're likely to get similar results with a finetune trained on stories._
Finetune | Base model | Link | Thoughts
:--:|:--:|:--:|:--:
Horni | GPT-Neo | [2.7B](https://huggingface.co/KoboldAI/GPT-Neo-2.7B-Horni) | _Trained by Finetuneanon. "One of the oldest models in our collection, tuned on Literotica to produce a Novel style model optimized towards NSFW content. Can still be used for SFW stories but will have a bias towards NSFW content."_ [[Source]](https://web.archive.org/web/20210926141005/https://github.com/koboldai/koboldai-client)
Horni-LN | GPT-Neo | [2.7B](https://huggingface.co/KoboldAI/GPT-Neo-2.7B-Horni-LN) | _Trained by Finetuneanon. "This model is much like the one above, but has been additionally trained on regular light novels. More likely to go SFW and is more focused towards themes found in these light novels over general cultural references. This is a good model for Novel writing especially if you want to add erotica to the mix."_ [[Source]](https://web.archive.org/web/20210926141005/https://github.com/koboldai/koboldai-client)
Picard | GPT-Neo | [2.7B](https://huggingface.co/KoboldAI/GPT-Neo-2.7B-Picard) | _An early version of Janeway, trained by Mr. Seeker. This model is trained on ~1,800 e-books, mostly sci-fi and fantasy._
Shinen | GPT-Neo, GPT-J, Fairseq | [2.7B](https://huggingface.co/KoboldAI/GPT-Neo-2.7B-Shinen), [6B](https://huggingface.co/KoboldAI/GPT-J-6B-Shinen), [6.7B](https://huggingface.co/KoboldAI/fairseq-dense-6.7B-Shinen), [13B](https://huggingface.co/KoboldAI/fairseq-dense-13B-Shinen) | _Early NSFW model trained by Mr. Seeker. It was trained on stories from Sexstories._
Janeway | GPT-Neo | [2.7B](https://huggingface.co/KoboldAI/GPT-Neo-2.7B-Janeway), [6B](https://huggingface.co/KoboldAI/GPT-J-6B-Janeway) | _Trained by Mr. Seeker. This one is instead trained on ~2,210 ebooks and consists of a similar dataset to Picard._
Janeway | Fairseq | [2.7B](https://huggingface.co/KoboldAI/fairseq-dense-2.7B-Janeway), [6.7B](https://huggingface.co/KoboldAI/fairseq-dense-6.7B-Janeway), [13B](https://huggingface.co/KoboldAI/fairseq-dense-13B-Janeway) | _Same as previous but trained on top of Fairseq. They perform slightly differently, and one is neither better or worse than the other._
Erebus | OPT, GPT-NeoX | [350M](https://huggingface.co/KoboldAI/OPT-350M-Erebus), [2.7B](https://huggingface.co/KoboldAI/OPT-2.7B-Erebus), [6.7B](https://huggingface.co/KoboldAI/OPT-6.7B-Erebus), [13B](https://huggingface.co/KoboldAI/OPT-13B-Erebus), [20B](https://huggingface.co/KoboldAI/GPT-NeoX-20B-Erebus), [30B](https://huggingface.co/KoboldAI/OPT-30B-Erebus) | _Trained by Mr. Seeker. The successor to Shinen. It's trained on six different NSFW sources: Literotica, Sexstories, Dataset-G, Doc's Lab, the Pike dataset, and SoFurry. This is a good option for chatting, too. It's currently the latest model trained by him at the moment._
Lotus | Pythia Deduped | [12B](https://huggingface.co/hakurei/lotus-12B) | _A newer model trained by Hakurei. Its training data consists of "2.5GB of a diverse range of light novels, erotica, annotated literature, and public-domain conversations for the purpose of generating novel-like fictional text and conversations." It doubles as a chat-friendly model._

### Remixed models
_These are a little more recent, and combine some of the previous models together into a new product._
Remix | Originals | Link
:--:|:--:|:--:
Nerybus | Erebus, Nerys | [2.7B](https://huggingface.co/KoboldAI/OPT-2.7B-Nerybus-Mix), [6.7B](https://huggingface.co/KoboldAI/OPT-6.7B-Nerybus-Mix), [13B](https://huggingface.co/KoboldAI/OPT-13B-Nerybus-Mix)
Pygway | Pygmalion, Janeway, ppo_hh_gpt-j | [6B](https://huggingface.co/KoboldAI/PPO_Pygway-6b-Mix)
