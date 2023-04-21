![image](https://user-images.githubusercontent.com/55674863/230695241-04ebc080-8fff-4d7e-9e8c-8d5168390150.png)

# Frontends

### What are frontends?

_A frontend is the interface you use to run and interact with your AI models. To save any confusion, I'll split them into two categories: standalone and proxy._

_**Standalone** frontends work on their own and exist to make it easier to interact with the models. Examples of standalone frontends include:_

- *[KoboldAI](https://github.com/KoboldAI/KoboldAI-Client)* *(supports the [Transformers](https://github.com/huggingface/transformers) backend)* - [Google Colab](https://colab.research.google.com/github/KoboldAI/KoboldAI-Client/blob/main/colab/TPU.ipynb)
- *[KoboldCpp](https://github.com/LostRuins/koboldcpp)* *(supports [llama.cpp](https://github.com/ggerganov/llama.cpp) and similar backends)*
- *[Oobabooga's Text Generation Web UI](https://github.com/oobabooga/text-generation-webui)* *(supports Transformers, [RWKV](https://github.com/oobabooga/text-generation-webui/wiki/RWKV-model), [GPTQ](https://github.com/oobabooga/text-generation-webui/wiki/LLaMA-model), and [llama.cpp](https://github.com/oobabooga/text-generation-webui/wiki/llama.cpp-models))* - [Google Colab](https://colab.research.google.com/github/oobabooga/AI-Notebooks/blob/main/Colab-TextGen-GPU.ipynb)
- *[OpenPlayground](https://github.com/nat/openplayground)* *(supports Transformers, llama.cpp, and others)*

_**Proxy** frontends depend on a standalone frontend running in the background so it can connect to it. Usually they connect to KoboldAI's API, but sometimes it also includes online services such as OpenAI or NovelAI. These are usually developed so you could use the standalone frontends in the style of a chat interface. Examples of proxy frontends include:_

- *[TavernAI](https://github.com/TavernAI/TavernAI)* - [Google Colab](https://colab.research.google.com/github/TavernAI/TavernAI/blob/main/colab/GPU.ipynb)
- *[SillyTavern](https://github.com/Cohee1207/SillyTavern)* - [Google Colab](https://colab.research.google.com/github/SillyLossy/TavernAI-extras/blob/main/colab/GPU.ipynb)
- *[Project Akiko](https://github.com/Project-Akiko/Project-Akiko)*
- *[miku.gg](https://github.com/miku-gg/miku)*
- *[LiteVN](https://laika-ch.itch.io/laikas-litevn-ui-for-koboldai)*
- *[Magi LLM GUI](https://github.com/shinomakoi/magi_llm_gui)*

_Browse through the frontends and find the one you like. I personally prefer Oobabooga's Text Generation Web UI due to its bleeding-edge features, and the Silly TavernAI Mod because of its extensions and settings._

_However, you may prefer KoboldAI if you expect [a more professional interface](https://cdn.discordapp.com/attachments/1092245228028706867/1093288888728047706/Screenshot_2023-04-05_at_14-39-30_sample_story_-_KoboldAI_Client.png) (currently only in [the United branch](https://github.com/henk717/KoboldAI)), and a more natural interface for storywriting and text adventures._

_If you want to look further into these projects outside of their GitHub repositories:_

- _KoboldAI has [an in-depth wiki](https://github.com/KoboldAI/KoboldAI-Client/wiki), [a subreddit](https://old.reddit.com/r/KoboldAI/) and [a Discord community](https://discord.gg/XuQWadgU9k)_
- _Oobabooga's Text Generation Web UI has [documentation](https://github.com/oobabooga/text-generation-webui/wiki) and [a subreddit](https://old.reddit.com/r/Oobabooga/)_
- _TavernAI has [an installation guide](https://github.com/TavernAI/TavernAI/wiki/How-to-install), [includes donations](https://boosty.to/tavernai), and its own channel in the KoboldAI Discord_
- _Project Akiko has [a Discord community](https://discord.gg/Pdhd7dEqHp)_
- _miku.gg has [documentation](https://docs.miku.gg/), [a Discord community](https://discord.gg/3XPdpUdGgV), and its own channel in the KoboldAI Discord_
- _LiteVN has its own channel in the KoboldAI Discord_

*Continue into [models](models.md)...*
