![image](https://user-images.githubusercontent.com/55674863/230695241-04ebc080-8fff-4d7e-9e8c-8d5168390150.png)

*"Buckle your seat belt, Dorothy, 'cause Kansas is going bye-bye."*

# Frontends

### What are frontends?

A frontend is the interface you use to run and interact with your AI. To avoid confusion, this guide separates them into two categories: standalone and proxy.

**Standalone** frontends work on their own, and are used to interact with the models.

Good standalone frontends for beginners include:
- **[Faraday](https://faraday.dev/)** *(for friendly chat and roleplay) (closed-source, but offline)*
- **[LM Studio](https://lmstudio.ai)** *(for assistant chat)*

These standalone frontends are more popular and flexible, but have a bit of a learning curve:
- **[KoboldCpp](https://github.com/LostRuins/koboldcpp)** *(for story co-writing, friendly chat and roleplay, assistant chat, and text adventure)*
- **[Oobabooga's Text Generation Web UI](https://github.com/oobabooga/text-generation-webui)** *(for story co-writing, friendly chat and roleplay, and assistant chat)*

*(Users of Stable Diffusion's AUTOMATIC1111 interface may feel right at home with Oobabooga's Text Generation Web UI.)*

**Proxy** frontends require a standalone frontend running in the background to connect to. They may be able to connect to KoboldCpp, Text Generation Web UI, and online services like OpenAI and NovelAI. All of these proxy frontends target chat and roleplay:
- **[SillyTavern](https://github.com/Cohee1207/SillyTavern)**
- **[TavernAI](https://github.com/TavernAI/TavernAI)**
- **[LiteVN](https://laika-ch.itch.io/laikas-litevn-ui-for-koboldai)**
- **[miku.gg](https://github.com/miku-gg/miku)**

*Continue into [models](models.md)...*
