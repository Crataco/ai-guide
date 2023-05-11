*This is version 2 of the AI guide. Version 1 is [available here](https://github.com/Crataco/ai-guide/blob/main/guide/original.md), which takes a crash course approach and has (outdated) advice on model parameters and settings. I try to keep [character creation](https://github.com/Crataco/ai-guide/blob/main/guide/original.md#chat-mode-create-your-character--browse-for-others) up-to-date.*

![clouds](https://user-images.githubusercontent.com/55674863/233225413-72efd34a-1cfa-4f49-b100-01d6c40287ec.jpg)

# Open-Source Text Generation AI Guide
_<sup>Written by Crataco (at the moment).</sup>_

_This is a guide for Large Language Models (LLMs) that you can run on your own hardware. This includes alternatives to Replika and CharacterAI, ChatGPT, GPT-3, and others._

- _[Click here for **frontends**](https://github.com/Crataco/ai-guide/blob/main/guide/frontends.md)_

- _[Click here for **model series** and **recommendations**](https://github.com/Crataco/ai-guide/blob/main/guide/models.md)_

- _[Click here for **model finetunes**](https://github.com/Crataco/ai-guide/blob/main/guide/finetunes.md)_

* * *

**NEWS:**

- **2023-05-10:** [WizardLM-13B-Uncensored was released by ehartford](https://old.reddit.com/r/LocalLLaMA/comments/13dem7j/wizardlm13buncensored/)
 
- **2023-05-08:** [KoboldCpp has added support for RedPajama GGML models and higher context lengths](https://github.com/LostRuins/koboldcpp/releases/tag/v1.20).

- **2023-05-07:** I just learned about [BluemoonRP](https://huggingface.co/reeducator/bluemoonrp-13b) and [Vicuna 13B Cocktail](https://huggingface.co/reeducator/vicuna-13b-cocktail).

- **2023-05-05:** [The RWKV project started training models on top of the RedPajama dataset](https://huggingface.co/BlinkDL/rwkv-4-pileplus).

- **2023-05-05:** [GPT4All-13B-Snoozy](https://old.reddit.com/r/LocalLLaMA/comments/138szrl/new_llama_13b_model_from_nomicai_gpt4all13bsnoozy/) was released.

- **2023-05-05:** [gpt4-x-vicuna 13B (based on LLaMA) was released by Nous Research](https://twitter.com/NousResearch/status/1654470228967817219) and [is available in both Transformers and GGML thanks to TheBloke](https://huggingface.co/TheBloke).

- **2023-05-05:** [MPT 7B was released by MosaicML](https://www.mosaicml.com/blog/mpt-7b). They claim it matches the quality of LLaMA 7B. They include chat instruct, and storywriting models, and claim to have a context length of up to 84k tokens.

- **2023-05-05:** [RedPajama-INCITE 3B and 7B (based on GPT-NeoX) were released by Together](https://www.together.xyz/blog/redpajama-models-v1). They include chat and instruction models and claim that their 3B is "the strongest model in its class."

* * *

_<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This repository is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>, encouraging forks and pull requests just as long as proper credit is given._
