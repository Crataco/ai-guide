![image](https://github.com/Crataco/ai-guide/assets/55674863/61c24c74-c484-4b52-ba95-fdec1377eead)
# Tips

An extra page that's not really a part of the main guide, but intended for users who already got their feet wet and want to explore a little more.

### Internal thoughts
You can give your AI "internal thoughts". I find that it adds more depth and a sense of intent behind the AI's every message. The llama.cpp frontend has [a script](https://github.com/ggerganov/llama.cpp/blob/master/examples/Miku.sh#L33) with a prompt that works exactly this way. There's [a Reddit post for Oobabooga](https://old.reddit.com/r/CharacterAi_NSFW/comments/13mrq2q/secret_thoughts_oobabooga/) and [a guide for SillyTavern](https://rentry.co/kingbri-chara-guide#advanced-character-thoughts). It's considered "advanced" by this guide because it could take some prompt engineering and a few example messages to get it working. So far my best attempt is on SillyTavern, adding this in the character's description:
```
{{char}} will ponder internally before responding. Present {{char}}'s response in this format:
<{{char}}'s thoughts: "thoughts leading up to {{char}}'s response"> {{char}}'s response
```
and adding `<{{char}}'s thoughts: "` to "Start Reply With" to give it an extra nudge. It understands this best with few-shot examples, i.e. by incorporating it into the AI's opening message or example messages.

On SillyTavern, as mentioned by the guide above, you could also take advantage of the "Regex" option in the Extensions tab and add `/<([^>]*)>/g` to regex. Make sure it affects "AI Output" and the Replacement Strategy is set to "Overlay", like in [this screenshot](https://cdn.discordapp.com/attachments/1092245228028706867/1136566365797498890/image.png). This will hide the AI's thoughts from you, unless you have text streaming enabled or go to edit their message.
