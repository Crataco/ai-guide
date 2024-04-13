![image](https://user-images.githubusercontent.com/55674863/230696024-98ce9e16-f558-4402-ac43-0e7f960c118c.png)

# Models
## What are models?

**TL;DR:** A model is your AI's brain.

To be more specific, a model is the AI that generates text.

The models are trained on top of pre-existing text and then released, often as base models (e.g. LLaMA) in specific sizes (e.g. 7B, 13B, 33B, and 70B). These base models are simple and often referred to as "glorified autocomplete" or "text completion" models, because they generate text after the user's input.

Finetunes are used to train the models are trained on further data, making it easier to use them like an assistant or chatting partner.

There are also different ways people run models: these are called backends.

## What is a backend?

Backends are different ways to store and run the AI model. The most notable ones are Transformers, GGUF, and Exllama. **If you're just starting, I recommend GGUF.**

- GGUF models run on most computers thanks to quantization. You can consider "quantization" a way to cut down on model size and resource usage with variable quality loss. It has "levels" that range from "q2" (smallest, worst quality) to "q8" (biggest, best quality). A level of q4_K_M is ideal for most situations unless you have more or less RAM to spare. [TheBloke](https://huggingface.co/TheBloke) converts many Transformers models into the GGUF format, and scrolling down his pages would bring you to [this chart](https://huggingface.co/TheBloke/Llama-2-7B-GGUF#provided-files), telling you the size and the most RAM the model would use under different quantization levels.

- Transformers has been around for a while and is pretty much a universal standard for AI models, but their models are unoptimized for running on consumer hardware and use *way* more resources than necessary. Approximately, while the average 7B model under GGUF would require over 4GB of RAM, a 7B model under Transformers could require 16GB or more.

- GPTQ, Exllama, and etc. are other backends with their own quantized format, but they're only useful if you have a recent graphics card (GPU). You'd have the best luck with NVIDIA GPUs, but with AMD GPUs, your mileage may vary. This is the option recommended if you have a powerful enough GPU for the model you want to run, but this guide will not cover this option.

This guide will assume users chose GGUF and a frontend that supports it (like KoboldCpp, Oobabooga's Text Generation Web UI, Faraday, or LM Studio).

## List of models to start with
**Last updated:** April 13th, 2024

Here are three things to keep in mind:
- Most models work best when you follow a generation format. These are often called "instruct presets" or "prompt templates" and make it clear to the model when the user talks and when it's the AI's turn. Fortunately most frontends let you choose one, and they do the work for you behind the scenes. If you do not know which instruct preset to use, scroll down on the model's page and it will usually be under "prompt template" or similar. Common ones include ChatML, Alpaca and Mistral.
- Settings influence the responses your models give you. A good place to start is to set "Min P" to 0.1 and "Temperature" to 1.0. Lowering the value of Min P can give the model a wider vocabulary, and raising the temperature will make it more likely it'll choose one of the less likely choices, which often translates to creative responses at the cost of some intelligence.
- If you do not have enough system RAM, but some VRAM to spare, you can split the model between your system RAM and video memory, which often goes by the term "GPU offloading".

* * *

### General Use (like ChatGPT)
- Mini (~512MB RAM) - **[RWKV-5 World](https://huggingface.co/latestissue/rwkv-5-world-ggml-quantized)** or **[languagemodels](https://github.com/jncraton/languagemodels)**
- 1.1B (~2GB RAM) - **[TinyDolphin 2.8 1.1B](https://huggingface.co/Crataco/TinyDolphin-2.8-1.1b-imatrix-GGUF)**
- 1.6B (~2GB RAM) - **[StableLM 2 1.6B Chat](https://huggingface.co/Crataco/stablelm-2-1_6b-chat-imatrix-GGUF)**
- 3B (~4GB RAM) - **[Phi-2 Orange](https://huggingface.co/Crataco/phi-2-orange-v2-imatrix-GGUF)**
- 7B (~8GB RAM) - **[Mistral 7B Instruct v0.2](https://huggingface.co/TheBloke/Mistral-7B-Instruct-v0.2-GGUF)** or **[Nous Hermes 2 Mistral 7B DPO](https://huggingface.co/Crataco/Nous-Hermes-2-Mistral-7B-DPO-imatrix-GGUF)**
- 8x7B (~32GB RAM) - **[Mixtral 8x7B Instruct v0.1](https://huggingface.co/mradermacher/Mixtral-8x7B-Instruct-v0.1-i1-GGUF)** or **[Nous Hermes 2 Mixtral 8x7B DPO](https://huggingface.co/mradermacher/Nous-Hermes-2-Mixtral-8x7B-DPO-i1-GGUF)**

* * *

### Chat/Roleplay (like CharacterAI, Replika, etc) and Storywriting (like NovelAI)
*You can also use general-purpose assistants for RP and storytelling, but these models balance creative prose with intelligence.*
- 7B (~8GB RAM) - **[Kunoichi 7B](https://huggingface.co/Lewdiculous/Kunoichi-DPO-v2-7B-GGUF-Imatrix)** for a great all-round experience, or **[Erosumika 7B](https://huggingface.co/Lewdiculous/Erosumika-7B-v3-0.2-GGUF-IQ-Imatrix)** for human-like responses
- 10.7B (~10GB RAM) - **[Fimbulvetr 11B v2](https://huggingface.co/mradermacher/Fimbulvetr-11B-v2-i1-GGUF)**
- 8x7B (~32GB RAM) - **[BagelMIsteryTour-v2-8x7B](https://huggingface.co/ycros/BagelMIsteryTour-v2-8x7B-GGUF)**

## General suggestions for CPU users based on RAM
**Last updated:** April 10th, 2024

To see how RAM influences which model + quant combination you can run. **Speed** means a small, fast and relatively dumb model that can run in the background. **Quality** means a relatively smart model that may use all of your available RAM and is slower. **Balanced** is somewhere in-between.
### 2GB RAM
- Balanced: [stablelm-2-1_6b-chat.Q4_K_M.imx.gguf](https://huggingface.co/Crataco/stablelm-2-1_6b-chat-imatrix-GGUF/blob/main/stablelm-2-1_6b-chat.Q4_K_M.imx.gguf)
- Quality: [phi-2-orange-v2.IQ2_M.imx.gguf](https://huggingface.co/Crataco/phi-2-orange-v2-imatrix-GGUF/blob/main/phi-2-orange-v2.IQ2_M.imx.gguf)
### 8GB RAM
- Speed: [phi-2-orange-v2.Q4_K_M.imx.gguf](https://huggingface.co/Crataco/phi-2-orange-v2-imatrix-GGUF/blob/main/phi-2-orange-v2.Q4_K_M.imx.gguf)
- Balanced: [nous-hermes-2-mistral-7b-dpo.Q5_K_M.imx.gguf](https://huggingface.co/Crataco/Nous-Hermes-2-Mistral-7B-DPO-imatrix-GGUF/blob/main/nous-hermes-2-mistral-7b-dpo.Q5_K_M.imx.gguf)
### 16GB RAM
- Speed: [phi-2-orange-v2.Q4_K_M.imx.gguf](https://huggingface.co/Crataco/phi-2-orange-v2-imatrix-GGUF/blob/main/phi-2-orange-v2.Q4_K_M.imx.gguf)
- Balanced: [nous-hermes-2-mistral-7b-dpo.Q5_K_M.imx.gguf](https://huggingface.co/Crataco/Nous-Hermes-2-Mistral-7B-DPO-imatrix-GGUF/blob/main/nous-hermes-2-mistral-7b-dpo.Q5_K_M.imx.gguf)
- Quality: [Beyonder-4x7B-v3.i1-IQ3_S.gguf](https://huggingface.co/mradermacher/Beyonder-4x7B-v3-i1-GGUF/blob/main/Beyonder-4x7B-v3.i1-IQ3_S.gguf)
