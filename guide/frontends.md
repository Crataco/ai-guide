![image](https://user-images.githubusercontent.com/55674863/230695241-04ebc080-8fff-4d7e-9e8c-8d5168390150.png)

# Frontends

### What are frontends?

A frontend is the interface you use to run and interact with your AI. To avoid confusion, this guide separates them into two categories: standalone and proxy.

**Standalone** frontends work on their own and make it easier to interact with the models. Examples of standalone frontends include:

- *[KoboldCpp](https://github.com/LostRuins/koboldcpp)* *(supports the GGML backend)*
- *[KoboldAI](https://github.com/KoboldAI/KoboldAI-Client)* *(supports the [Transformers](https://github.com/huggingface/transformers) backend)* - [Google Colab](https://colab.research.google.com/github/KoboldAI/KoboldAI-Client/blob/main/colab/TPU.ipynb)
- *[Oobabooga's Text Generation Web UI](https://github.com/oobabooga/text-generation-webui)* *(supports Transformers, [RWKV](https://github.com/oobabooga/text-generation-webui/blob/main/docs/RWKV-model.md), [GPTQ](https://github.com/oobabooga/text-generation-webui/blob/main/docs/GPTQ-models-(4-bit-mode).md), and [GGML (LLaMA-only)](https://github.com/oobabooga/text-generation-webui/blob/main/docs/llama.cpp-models.md))* - [Google Colab](https://colab.research.google.com/github/oobabooga/AI-Notebooks/blob/main/Colab-TextGen-GPU.ipynb)
- *[llama.cpp](https://github.com/ggerganov/llama.cpp)* *(supports GGML (LLaMA-only))*
- *[OpenPlayground](https://github.com/nat/openplayground)* *(supports Transformers, GGML (LLaMA-only), and others)*

*(The importance of Transformers, RWKV, GGML and GPTQ are explained in the [next page](models.md#what-is-a-backend) of this guide.)*

**Proxy** frontends require a standalone frontend running in the background to connect to. What they can connect to includes Kobold, Oobabooga, and online services like OpenAI and NovelAI. Examples of proxy frontends include:

- *[TavernAI](https://github.com/TavernAI/TavernAI)* - [Google Colab](https://colab.research.google.com/github/TavernAI/TavernAI/blob/main/colab/GPU.ipynb)
- *[SillyTavern](https://github.com/Cohee1207/SillyTavern)* - [Google Colab](https://colab.research.google.com/github/SillyTavern/SillyTavern/blob/main/colab/GPU.ipynb)
- *[Project Akiko](https://github.com/Project-Akiko/Project-Akiko)*
- *[miku.gg](https://github.com/miku-gg/miku)*
- *[LiteVN](https://laika-ch.itch.io/laikas-litevn-ui-for-koboldai)*
- *[Magi LLM GUI](https://github.com/shinomakoi/magi_llm_gui)*

Browse through the frontends and find the one you like. The guide author's preference is Oobabooga's Text Generation Web UI + SillyTavern, but they have a preference for KoboldCpp when running more exotic models.

If you want to look further into these projects outside of their GitHub repositories:

- _KoboldAI has [an in-depth wiki](https://github.com/KoboldAI/KoboldAI-Client/wiki), [a subreddit](https://old.reddit.com/r/KoboldAI/) and [a Discord community](https://discord.gg/XuQWadgU9k)_
- _Oobabooga's Text Generation Web UI has [documentation](https://github.com/oobabooga/text-generation-webui/wiki), [a subreddit](https://old.reddit.com/r/Oobabooga/), and [a Discord community](https://discord.com/invite/u27RhJECcW)_
- _TavernAI has [an installation guide](https://github.com/TavernAI/TavernAI/wiki/How-to-install), [accepts donations](https://boosty.to/tavernai), and its own channel in the KoboldAI Discord_
- _SillyTavern has [an installation guide](https://github.com/SillyTavern/SillyTavern#installation) and [in-depth documentation](https://docs.sillytavern.app/)_
- _miku.gg has [documentation](https://docs.miku.gg/), [a Discord community](https://discord.gg/3XPdpUdGgV), and its own channel in the KoboldAI Discord_
- _LiteVN has its own channel in the KoboldAI Discord_

*Continue into [models](models.md)...*
