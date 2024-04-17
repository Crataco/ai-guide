![image](https://user-images.githubusercontent.com/55674863/230696024-98ce9e16-f558-4402-ac43-0e7f960c118c.png)

# Models
## What are models?
A **model** (sometimes called a "weight") is the AI you run, or more specifically its brain.

A variety of models exist, by different "brands" (Llama 2, Mistral, Yi), released under various sizes (7B, 13B, 33B, 70B).

They start off as a base, with no real task other than to predict the text that comes after what you write, like a smart autocomplete. But hobbyists and companies train these ripe models further on a corpus of conversational data. ChatGPT popularized this practice, but it has been around since the days of AI Dungeon.

## How are models stored?
**Model formats**. The most popular model format is **GGUF**, provided by the "llama.cpp" project. Support for it is included in most non-proxy frontends, making it a de-facto standard. If your frontend doesn't allow you to download models, they can be found on [Hugging Face](https://huggingface.co/models?search=gguf).

One of the things that make GGUF perfect for home computers is **quantization**. You can download models that are lossily compressed (think of it as a "lower resolution" model). It saves plenty of bandwidth, disk space, and memory use, compared to storing and running an untouched (PyTorch format) version of the model, but it comes at the cost of quality.

Quantization is provided in **levels,** ranging from the smallest (Q1 or Q2) to the largest (Q6 or Q8). **Q4_K_M** is recommended for most cases, unless you have plenty of RAM to spare, which Q5 would be preferred.

Lastly, if you lack RAM and don't mind the loss in quality, keep an eye out on "**importance matrix**" models (usually "iMat", "i1" or "imatrix"). It uses a different method of quantization that squeezes the most out of its level. It also provides its own special "IQ" models, but they're slower on CPU than regular "K" models, and it's recommended not to go below IQ2.

## What else should I know before I begin?
These are for the power users. You shouldn't have to touch any of these if using a more casual frontend.

- Make sure you know the **prompt template** or **instruct preset** of your model. It tells your frontend when you speak and when the AI will speak. ChatML is a commonly-used template, but you should read the model's description to be sure.

- **Settings**. If your frontend has settings (sometimes "generation parameters"), disable as much as you can. Afterwards, if it's available, change **Min-P** to 0.1 and **Temperature** to 1. It can work as sensible defaults and a foundation for tweaking. Min-P values will give the AI more words to choose from, while higher Min-P values means it'd have less. Lower temperature means it'll choose likely words more often, while higher temperature means it'll choose less likely words more often. It's great if you're trying a lesser-supported model, or just want to hit a sweet spot for creative writing or roleplaying.

- If you have a video card for gaming, it's not a bad idea to take advantage of **GPU offloading** to fit as much of the model as you can into your GPU. It'll save some RAM from your main system and be much faster. NVIDIA (or "CuBLAS" under KoboldCpp) are the best supported, but some frontends have support for any Vulkan-supported GPU.

* * *

## Model recommendations
**Last updated:** April 16th, 2024

This assumes you're running a Q4_K_M GGUF model. You may be able to squeeze some more out of your hardware if you explore Q3 or Q2.

### General Use (like ChatGPT)
- Potato - **[RWKV-5 World 0.1B/0.4B](https://huggingface.co/latestissue/rwkv-5-world-ggml-quantized)** or **[languagemodels](https://github.com/jncraton/languagemodels)**
- 2 GB RAM - **[TinyDolphin 2.8 1.1B](https://huggingface.co/Crataco/TinyDolphin-2.8-1.1b-imatrix-GGUF)** or **[StableLM 2 1.6B Chat](https://huggingface.co/Crataco/stablelm-2-1_6b-chat-imatrix-GGUF)**
- 4 GB RAM - **[Phi-2 Orange](https://huggingface.co/Crataco/phi-2-orange-v2-imatrix-GGUF)**
- 8 GB RAM - The **Nous-Hermes** series: **[Hermes 2 DPO](https://huggingface.co/Crataco/Nous-Hermes-2-Mistral-7B-DPO-imatrix-GGUF)** and **[Hermes 2 Pro](https://huggingface.co/qwp4w3hyb/Hermes-2-Pro-Mistral-7B-iMat-GGUF)**. Hermes 2 DPO has the best score, while Hermes 2 Pro is the latest as of writing.
- 20 GB RAM - **[Beyonder 4x7B v3](https://huggingface.co/mradermacher/Beyonder-4x7B-v3-i1-GGUF)**
- 32 GB RAM - **[Mixtral 8x7B Instruct v0.1](https://huggingface.co/mradermacher/Mixtral-8x7B-Instruct-v0.1-i1-GGUF)**
  
### Chat/Roleplay (like CharacterAI, Replika, etc) and Storywriting (like NovelAI)
You can also use general-use models, but these are trained on data that balances creative prose with intelligence.
- 8 GB RAM - **[Kunoichi 7B](https://huggingface.co/Lewdiculous/Kunoichi-DPO-v2-7B-GGUF-Imatrix)** for a great all-round experience, or **[Erosumika 7B](https://huggingface.co/Lewdiculous/Erosumika-7B-v3-0.2-GGUF-IQ-Imatrix)** for creative prose
- 10 GB RAM - **[Fimbulvetr 11B v2](https://huggingface.co/mradermacher/Fimbulvetr-11B-v2-i1-GGUF)**
- 32 GB RAM - **[BagelMIsteryTour-v2-8x7B](https://huggingface.co/ycros/BagelMIsteryTour-v2-8x7B-GGUF)**
