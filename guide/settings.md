![sewers](https://github.com/Crataco/ai-guide/assets/55674863/5cc25346-4dfd-44be-b29d-e371a53e022c)
# Settings

This guide was created because the author feels there's not enough coverage on settings, which can make or break your experience just as well as using a different model.

### What are settings?

Settings (also known as "parameters", not to be confused with the same term used for model sizes) are the values you can tweak that can change the way your AI will generate. Setting presets are the easiest way to get your feet wet.

If you're just getting started, use the presets your frontend comes with. The default preset may even be fine enough for you. Currently, the guide author flips between the "TFS-with-Top-A", "Shortwave" and "Mirostat" presets for roleplay, and "LLaMA-Precise" for assistant models.

* * *

But if you want to tweak them yourself and make your own, some common values include:

- **Temperature:** This influences how well the AI can stay on-topic. A low temperature means something boring and predictable, while a high temperature would mean something a little out of your control. The guide author finds 0.7 to be a good value, but some models do well with 1.0 or higher.
- **Repetition penalty:** This changes how "repetitive" the AI can get. Just like temperature, you need to find a good balance. Too low and the AI may start to repeat itself or start to use the same word. Too high and the AI will go off the rails. 1.1 to 1.2 are often good values.
- **Context tokens:** In Oobabooga, this is known as `Truncate the prompt up to this length`. This represents how much text the model is able to remember. LLaMA 1 models can remember 2,048 tokens, and Llama 2 models can remember 4,096 tokens. A token is about 4 characters on average [(source)](https://novelai.net/tokenizer). However, if you find it using too much memory, you can decrease it.
- **Output length:** In Oobabooga, this is known as `max_new_tokens`. This describes how long the AI's generation can be before it stops, either on its own or after hitting the limit.

There are advanced values that also influence which words the AI will generate next. These are called "samplers," and include:
- **`top-p`** (1 = disabled)
- **`top-k`** (0 = disabled)
- **`top-a`** (0 = disabled)
- **`typical_p`** (1 = disabled)
- **[`mirostat_mode`](https://github.com/ggerganov/llama.cpp/blob/master/examples/main/README.md#mirostat-sampling)** (0 = disabled)
