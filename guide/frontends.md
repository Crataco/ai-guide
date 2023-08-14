![image](https://user-images.githubusercontent.com/55674863/230695241-04ebc080-8fff-4d7e-9e8c-8d5168390150.png)

*"Buckle your seat belt, Dorothy, 'cause Kansas is going bye-bye."*

# Frontends

### What are frontends?

A frontend is the interface you use to run and interact with your AI. To avoid confusion, this guide separates them into two categories: standalone and proxy.

**Standalone** frontends work on their own, and are used to interact with the models. Examples of standalone frontends include:

- **[LM Studio](https://lmstudio.ai)** *(supports the GGML backend\*, including non-LLaMA models)*
- **[KoboldCpp](https://github.com/LostRuins/koboldcpp)** *(supports the GGML backend, including non-LLaMA models)*
- **[KoboldAI](https://github.com/KoboldAI/KoboldAI-Client)** *(supports the Transformers backend)*
- **[Oobabooga's Text Generation Web UI](https://github.com/oobabooga/text-generation-webui)** *(supports various backends)*
- **[MLC-LLM](https://mlc.ai/mlc-llm)** *(runs on mobile devices)*

\* *(The importance of Transformers, RWKV, GGML and GPTQ are explained in the [next page](models.md#what-is-a-backend) of this guide.)*

**Proxy** frontends require a standalone frontend running in the background to connect to. They can connect to Kobold, Oobabooga, and online services like OpenAI and NovelAI. Examples of proxy frontends include:

- **[SillyTavern](https://github.com/Cohee1207/SillyTavern)**
- **[TavernAI](https://github.com/TavernAI/TavernAI)**
- **[LiteVN](https://laika-ch.itch.io/laikas-litevn-ui-for-koboldai)**
- **[miku.gg](https://github.com/miku-gg/miku)**

*(The guide recommends LM Studio if you're new. The guide author uses Oobabooga and SillyTavern.)*

*Continue into [models](models.md)...*
