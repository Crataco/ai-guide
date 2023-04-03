# Frontends

### What are frontends?

A frontend is the interface you use to run and interact with AI models. To clear up any confusion, I'll split them into two categories: standalone and proxy.

**Standalone** frontends work on their own and exist to make it easier to interact with the AI backend. Examples of standalone frontends include:
- [KoboldAI](https://github.com/KoboldAI/KoboldAI-Client)
- [Oobabooga's Text Generation Web UI](https://github.com/oobabooga/text-generation-webui)

**Proxy** frontends depend on a standalone frontend running in the background so it can connect to it. Usually this is KoboldAI, but sometimes it also includes online services such as OpenAI or NovelAI. These are usually developed so you could use the standalone frontends in the style of a chat interface. Examples of proxy frontends include:

- [TavernAI](https://github.com/TavernAI/TavernAI) and the [Silly TavernAI Mod](https://github.com/SillyLossy/TavernAI)
- [Project Akiko](https://github.com/Project-Akiko/Project-Akiko)
- [miku.gg](https://github.com/miku-gg/miku)
- [LiteVN](https://laika-ch.itch.io/laikas-litevn-ui-for-koboldai)
