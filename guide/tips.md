# Tips

An extra page that's not really a part of the main guide, but intended for users who already got their feet wet and want to explore a little more. This'll be a little... informal.

### Internal thoughts
You can give your AI "internal thoughts". I find that it adds more depth and a sense of intent behind the AI's every message. The llama.cpp frontend has [a script](https://github.com/ggerganov/llama.cpp/blob/master/examples/Miku.sh#L33) with a prompt that works exactly this way. There's [a Reddit post for Oobabooga](https://old.reddit.com/r/CharacterAi_NSFW/comments/13mrq2q/secret_thoughts_oobabooga/) and [a guide for SillyTavern](https://rentry.co/kingbri-chara-guide#advanced-character-thoughts). It's considered "advanced" by this guide because it could take some prompt engineering and a few example messages to get it working. So far my best attempt is on SillyTavern, adding this in the character's description:
```
{{char}} will ponder internally before responding. Present {{char}}'s response in this format:
<{{char}}'s thoughts: "thoughts leading up to {{char}}'s response"> {{char}}'s response
```
and adding `<{{char}}'s thoughts: "` to "Start Reply With" to give it an extra nudge.
