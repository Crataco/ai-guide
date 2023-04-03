*Note: this is taken from my Pastebin post. I use Linux and have an i7-6700 CPU. Results may be incomplete due to my hardware, and the memory requirements may differ depending on which frontend you use; my testing was with Oobabooga's Text Generation Web UI, unless specified otherwise.*

* * *

### GPT-2

Size | Memory
:--|:--:
82M | 682.5 MiB
124M | 870.3 MiB
355M | 1.8 GiB
774M | 3.4 GiB
1.5B | 6.3 GiB

* * *

### GPT-NEO

Size | Memory | Generation speed
:--|:--:|--:
125M | 883.3 GiB | 19.75 tokens / second
350M | 2.0 GiB | 8.79 tokens / second
1.3B | 5.5 GiB | 2.81 tokens / second
2.7B | 12.5 GiB (KoboldAI) | 1.68 tokens / second

* * *

### OPT

Size | Memory | Generation speed
:--|:--:|--:
125M | 973.2 MiB | 20.48 tokens / second
350M | 2.2 GiB | 9.44 tokens / second
1.3B | 6.0 GiB | 3.02 tokens / second

* * *

### RWKV

*(using ChatRWKV v2 as of 2023-03-07. Using default Alice / Bob prompt)*

*(From what I noticed, fp32i8 spikes a bit (i.e. from 4.3 GiB to 5.2 GiB, or 8.8 GiB to 10.5 GiB) when generating. It spikes around, if not higher than fp32's level when loading the model, so you better have some swap space.)*

*(bf16 is much slower than fp32 at the moment; I feel like 430M with bf16 generates a little slower than 1.5B with fp32. I'd argue it's probably faster to fall back to swap memory, but I wouldn't recommend it if you're using microSD-based storage.)*

Size | Memory (fp32) | bf16 | fp32i8 | bf16i8
:--|:--:|:--:|:--:|--:
169M | 1.0 GiB | 743.0 MiB | 856.7 MiB | 877.9 MiB
430M | 2.1 GiB |   1.3 GiB | 1.2 GiB | 2.4 GiB
1.5B | 6.3 GiB |   3.4 GiB | 5.7 GiB | 4.5 GiB
3B | ~16 GiB | 6.1 GiB | 4.3 GiB | ~9.1 GiB
7B | ~32 GiB | ??.? GiB | 8.8 GiB | ??.? GiB
 
* * *
 
### PYTHIA DEDUPED

Size | Memory | Generation speed
:--|:--:|--:
70M | 677.4 MiB | 40.03 tokens / second
160M | 1.2 GiB | 20.33 tokens / second
410M | 2.6 GiB | 8.83 tokens / second
1B | 4.7 GiB | 4.29 tokens / second
1.4B | 6.5 GiB | 2.99 tokens / second
2.8B | 11.7 GiB (KoboldAI) | 1.68 tokens / second
 
### BLOOM

Size | Memory
:--|:--:
560M | 3.0 GiB
1.1B | 5.5 GiB
1.7B | 7.4 GiB
