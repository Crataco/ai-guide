![sewers](https://github.com/Crataco/ai-guide/assets/55674863/5cc25346-4dfd-44be-b29d-e371a53e022c)
# Settings

This guide was created because the author feels there's not enough coverage on settings, which can make or break your experience just as well as using a different model.

### What are settings?

Settings (also known as "parameters", not to be confused with the same term used for model sizes) are the values you can tweak that can change the way your AI will generate. Presets come with their own values, are the easiest way to get your feet wet, and are available in the major frontends (Oobabooga, SillyTavern, etc).

If you want to tweak them yourself and make your own preset, some common values include:

- **Temperature:** This influences how well the AI can stay on-topic. A low temperature means something boring and predictable, while a high temperature would mean something a little out of your control. The guide author finds 0.7 to be a good value, but some models do well with 1.0 or higher.
- **Repetition penalty:** This changes how "repetitive" the AI can get. Just like temperature, you need to find a good balance. Too low and the AI may start to repeat itself or start to use the same word. Too high and the AI will go off the rails. The guide author finds 1.1-1.2 to be a good value, but older models do well with 1.5-2.0.
- **Context tokens:** In Oobabooga, this is known as `Truncate the prompt up to this length`. This represents how much text the model is able to remember. Most models support up to 2,048 tokens. LLaMA 2 models support up to 4,096 tokens. However, if you find it using too much memory, you can decrease it.
- **Output length:** In Oobabooga, this is known as `max_new_tokens`. This describes how long the AI's generation can be before it stops, either on its own or after hitting the limit.

There are advanced values that also influence which words the AI will generate next. These are "samplers," such as `top-p` (1 = disabled), `top-k` (0 = disabled), `top-a` (0 = disabled), Typical Sampling (1 = disabled), and Mirostat (0 = disabled). This guide suggests that you leave these alone and keep `top-p` to 0.85 or 0.9. Alternatively, you can use Mirostat, which will ignore the samplers and attempt to keep the model on its feet (explained [here](https://github.com/ggerganov/llama.cpp/blob/master/examples/main/README.md#mirostat-sampling)).
* * *
### The guide's recommended settings
These are settings the author has tested out on numerous occasions and mostly stuck with.
#### Assistant ("LLaMA-Precise")
- **Temperature:** 0.7
- **Repetition penalty:** 1.176 (rounded to 1.18)
- **top-p:** 0.1
- **top-k:** 40

#### Chat / Roleplay #1
- **Temperature:** 0.7 - 1.0, depending on the results you get from the model
- **Repetition penalty:** 1.1 - 1.2, depending on the results you get from the model
- **top-p:** 0.85

#### Chat / Roleplay #2 (using Mirostat)
- **Temperature:** 1.0
- **Repetition penalty:** 1.0-1.2. The guide author uses 1.2, but isn't sure if repetition penalty is respected with Mirostat enabled.
- **mirostat_mode:** 2
- **mirostat_tau:** 3.5
- **mirostat_eta:** 0.2
