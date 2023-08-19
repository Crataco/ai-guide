A spiritual successor of the chatbot comparison seen [here](https://github.com/Crataco/ai-guide/blob/main/guide/original.md#screenshots), with a more complex character prompt (taken from [here](https://github.com/harubaru/eliza/blob/main/config/discord_reimu.json)). Oobabooga was used, with the Alpaca prompt template and chat-instruct mode.

Not really representative of real-world performance (since LLMs are heavily luck-based). Just thought it'd be neat.

### Generic models (chat)
TBA

### Finetuned models (chat-instruct)
**Model / Screenshot** | **Finetuned on** | **Settings**
:--|:--:|--:
[`Marx-3B.ggmlv3.q5_1.bin`](https://cdn.discordapp.com/attachments/1092245228028706867/1142516508984086578/mirostat_5_w_marx_3b.png) | OpenLLaMA 3B V2 | Mirostat 2, 5, 0.1
[`nous-hermes-llama2-7B.ggmlv3.q6_K.bin`](https://cdn.discordapp.com/attachments/1092245228028706867/1142505069821042738/nous-hermes_2_7b.png) | LLaMA 2 7B | Mirostat 2, 5, 0.1
[`zarablend-l2-7b.ggmlv3.q6_K.bin`](https://cdn.discordapp.com/attachments/1092245228028706867/1142516249570586834/zarablend_7b.png) | LLaMA 2 7B | Mirostat 2, 5, 0.1
