![sewers](https://github.com/Crataco/ai-guide/assets/55674863/5cc25346-4dfd-44be-b29d-e371a53e022c)
# Settings

This guide was created because the author feels there's not enough coverage on settings, which can make or break your experience just as well as using a different model.

### What are settings?

Settings (also known as "parameters", not to be confused with the same term used for model sizes) are the values you can tweak that can change the way your AI will generate. Presets come with their own values, are the easiest way to get your feet wet, and are available in the major frontends (KoboldAI, Oobabooga, SillyTavern, etc).

If you're just getting started, use the presets your frontend comes with. The default preset may even be fine enough for you.

But if you want to tweak them yourself and make your own, some common values include:

- **Temperature:** This influences how well the AI can stay on-topic. A low temperature means something boring and predictable, while a high temperature would mean something a little out of your control. The guide author finds 0.7 to be a good value, but some models do well with 1.0 or higher.
- **Repetition penalty:** This changes how "repetitive" the AI can get. Just like temperature, you need to find a good balance. Too low and the AI may start to repeat itself or start to use the same word. Too high and the AI will go off the rails. The guide author finds 1.1-1.2 to be a good value.
- **Context tokens:** In Oobabooga, this is known as `Truncate the prompt up to this length`. This represents how much text the model is able to remember. Most models support up to 2,048 tokens. LLaMA 2 models support up to 4,096 tokens. A token, as mentioned in the previous guide, is about 4 characters on average [(source)](https://novelai.net/tokenizer). However, if you find it using too much memory, you can decrease it.
- **Output length:** In Oobabooga, this is known as `max_new_tokens`. This describes how long the AI's generation can be before it stops, either on its own or after hitting the limit.

There are advanced values that also influence which words the AI will generate next. These are "samplers," such as
- `top-p` (1 = disabled)
- `top-k` (0 = disabled)
- `top-a` (0 = disabled)
- `typical_p` (1 = disabled)
- `mirostat_mode` (0 = disabled) (and other related settings, like `mirostat_tau` and `mirostat_eta`)

This guide suggests that you leave these alone and keep `top-p` to 0.85 or 0.9. Alternatively, you can use Mirostat, which will ignore the rest of the samplers and try to keep the model's generations fresh ([explained here](https://github.com/ggerganov/llama.cpp/blob/master/examples/main/README.md#mirostat-sampling)), but the guide author heard that it may slow down generation speed.
* * *
### The guide's recommended settings
These are settings the author has tested out extensively and mostly stuck with.
#### Assistant ("LLaMA-Precise" via Oobabooga) - The guide author uses this for precise answers from assistants.
- **Temperature:** 0.7
- **Repetition penalty:** 1.176 (rounded to 1.18)
- **top-p:** 0.1
- **top-k:** 40
#### Chat / Roleplay / Storywriting #1 (based off of Oobabooga's "Naive" preset; works well for most models)
- **Temperature:** 0.7 - 1.0, depending on the results you get from the model
- **Repetition penalty:** 1.1 - 1.2, depending on the results you get from the model
- **top-p:** 0.85
#### Chat / Roleplay / Storywriting #2 (Mirostat; tries to keep things fresh)
- **Temperature:** 0.6 - 0.9. The author hasn't noticed temperature make much of an impact, but it seems other users have.
- **Repetition penalty:** 1.1 - 1.2 (1.2 with Nous-Hermes, 1.1 with MythoMax)
- **mirostat_mode:** 2
- **mirostat_tau:** 3.0 - 5.0. The guide recommends 3.5, but the author is testing 5.0. Lower is more coherent and higher is more diverse.
- **mirostat_eta:** 0.1 - 0.4. The guide recommends 0.2. It feels like a nice balance between 0.1 being too predictable and 0.3+ going off-topic/derailing stories, but 0.15 was used in [another guide](https://rentry.org/freellamas) and there are users okay with a higher eta value. Author is currently testing 0.4.
