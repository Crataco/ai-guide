![image](https://user-images.githubusercontent.com/55674863/230696024-98ce9e16-f558-4402-ac43-0e7f960c118c.png)

# Models
## What are models?
A **model**, sometimes called a "weight", is the core -- or brain -- of your AI.

There are two main types of models. The first is a **base model**. Give it text and it'll predict what comes next. This was common for years until ChatGPT popularized the second type, **instruct models**, which start from base models, but are trained on question-and-answer and conversational data.

## How are models stored?
Models are stored in different **formats**.

The most popular format is **GGUF**. It is recommended because it can run on pretty much anything. Other formats assume you already have an expensive GPU to use.

GGUF also supports **quantization**. Quantizing a model means shrinking it down to a certain level, like "Q2_K" (small), "Q4_K_M" (medium), or "Q6_K" (large). Like storing images at lower resolutions, it takes up less space and resources while sacrificing some of its quality. Quantization is *mandatory* for PCs with less memory.

## Where do I find models?

- **Check [Hugging Face](https://huggingface.co/models)** and search for uploads containing "gguf" in their name.
- When on the page of the model you want, **click on the "Files and versions" tab**. You should see a list of all the levels the model has been quantized to.
- **Choose a level**. Q4_K_M is usually good enough, but depending on how much RAM is available when you run the model, you may want a smaller (Q2-Q3) or bigger (Q5-Q8) quantization. After picking one out, click on the file and go to "download".

There are several sources recommended for being up-to-date on the latest releases:
- [**Chatbot Arena Leaderboard**](https://leaderboard.lmsys.org/)
- [**MMLU Pro Leaderboard**](https://huggingface.co/spaces/TIGER-Lab/MMLU-Pro)
- Communities, like [**r/SillyTavernAI**](https://old.reddit.com/r/SillyTavernAI/) on Reddit (roleplay-focused), and Discord servers for [**TheBloke**](https://discord.com/invite/Jq4vkcDakD), [**KoboldAI**](https://koboldai.org/discord), and [**SillyTavern**](https://discord.com/invite/SillyTavern)
- In the case of roleplay models, [**Lewdiculous' personal favorites**](https://huggingface.co/collections/Lewdiculous/personal-favorites-65dcbe240e6ad245510519aa)

As of May 21st, 2024, this guide recommends the following general-purpose models:

- [**Llama 3 8B**](https://huggingface.co/bartowski/Meta-Llama-3-8B-Instruct-GGUF) on computers with 8 GB RAM or more
- [**Phi-3 Mini**](https://huggingface.co/bartowski/Phi-3-mini-4k-instruct-GGUF) on computers with less than 8 GB RAM
- You may or may not have success with [**Phi-3 Medium**](https://huggingface.co/bartowski/Phi-3-medium-4k-instruct-GGUF) on computers with 16 GB RAM or more. The guide author assumes the model to be smart, but not good enough for roleplaying, and pretty slow compared to the previous two.

## *Optional: Tips for Power Users*

- If your computer is made for gaming, it's likely you have a GPU you can use, and if so, **use it**. The GPU's VRAM can be seen as extra memory, in which you're encouraged to split (offload) the model onto, or if the model's small enough, fit it into the GPU entirely.
  - CUDA acceleration only works with NVIDIA cards, but is supported by most, if not all frontends.
  - Vulkan acceleration should include most GPUs made within the last 10 years, but is currently only supported by [llama.cpp](https://github.com/ggerganov/llama.cpp?tab=readme-ov-file#vulkan) and [KoboldCpp](https://github.com/LostRuins/koboldcpp?tab=readme-ov-file#osx-and-linux-manual-compiling).
  - If you want to get your hands dirty, Intel GPUs (including integrated) have support for OneAPI acceleration, but is currently only supported by [llama.cpp](https://github.com/ggerganov/llama.cpp/blob/master/README-sycl.md).

- For low-end phones and budget hardware (like a Raspberry Pi), there are many tiny models, including [**TinyLlama 1.1B**](https://huggingface.co/TheBloke/TinyLlama-1.1B-Chat-v1.0-GGUF), [**StableLM 2 Chat 1.6B**](https://huggingface.co/Crataco/stablelm-2-1_6b-chat-imatrix-GGUF), or those uploaded by [Felladrin](https://huggingface.co/Felladrin). They are fun to toy around with, but are unrecommended to be used for anything that requires factual accuracy or reasoning.

- When picking out a model, it's recommended to find uploads that mention "**importance matrix**" or "**imatrix**" in their name or description. An "importance matrix" minimizes the quality loss that quantized models have. Some notable users that upload quantized models with "imatrix" are [mradermacher](https://huggingface.co/mradermacher) and [bartowski](https://huggingface.co/bartowski).

- Make sure you know the **prompt template** or **instruct preset** of your model. It tells your frontend when you speak and when the AI will speak. For example, ChatML is a commonly-used template, but most Llama 3 models may work best with Llama 3's official template.

- **Settings**. If your frontend has settings (sometimes called "generation parameters"), change **Min-P** to 0.1, **Temperature** to 1, and disable everything else if possible. Those work as sensible defaults for tweaking.
  - Lower Min-P values will give the AI more words to choose from, while higher Min-P values means it'd have less.
  - Lower temperature means that of those words, it'll choose the more likely, predictable word, while higher temperature means it'll pick less likely, more unpredictable words.
  - It's great if the model you use isn't supported by the community, or you want to find a sweet spot for creative, less-repetitive responses from the AI.
