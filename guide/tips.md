![image](https://github.com/Crataco/ai-guide/assets/55674863/61c24c74-c484-4b52-ba95-fdec1377eead)
# Tips

An extra page that's not really a part of the main guide, but intended for users who already got their feet wet and want to explore a little more.

### Extended context length (tested on Oobabooga w/ llama.cpp)
Use at your own risk. At the cost of little quality loss, you can extend the AI's memory from 4K tokens to 8K tokens with a bit of a hack: load your model with `--alpha_value 2.6` and `--n-ctx 8192`. The guide author still hasn't found a reliable source that describes alpha value in detail, only recommendations between 2.4 and 2.6.

### Internal thoughts
You can give your AI "internal thoughts". I find that it adds more depth and a sense of intent behind the AI's every message. The llama.cpp frontend has [a script](https://github.com/ggerganov/llama.cpp/blob/master/examples/Miku.sh#L33) with a prompt that works exactly this way. There's [a Reddit post for Oobabooga](https://old.reddit.com/r/CharacterAi_NSFW/comments/13mrq2q/secret_thoughts_oobabooga/) and [a guide for SillyTavern](https://rentry.co/kingbri-chara-guide#advanced-character-thoughts). It's considered "advanced" by this guide because it could take some prompt engineering and a few example messages to get it working.

I've fiddled with several different prompts, such as:
```
{{char}} can think for herself by beginning her message like this:
<{{char}}'s thoughts: "{{char}}'s thoughts here"> {{char}}'s response here
She uses this to reason about the world and to think about what she should say next.
```
but it's not really needed since text generation models are usually pretty good at following patterns, so you can just add the character's thoughts in your opening message, and add `<{{char}}'s thoughts: "` to "Start Reply With" to give the AI a nudge in the right direction.

On SillyTavern, as mentioned by the guide above, you could also take advantage of the "Regex" option in the Extensions tab and add `/<([^>]*)>/g` to regex. Make sure it affects "AI Output" and the Replacement Strategy is set to "Overlay", like in [this screenshot](https://cdn.discordapp.com/attachments/1092245228028706867/1136566365797498890/image.png). This will hide the AI's thoughts from you, unless you have text streaming enabled or go to edit their message.
