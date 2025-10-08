# MKS2-Multimodal-Knowledge-Storage-and-Sharing
The codes of Vision Enhancing LLMs: Multimodal Knowledge Storage and Sharing in LLMs

## 🚀 News

``2025.10.7`` We created a code repository and released a technical report


## 📚 Method Description

While most Multimodal LLMs (MLLMs) use language models to process vision ("LLMs for Vision"), we explore the inverse: using visual knowledge to enhance the core capabilities of LLMs ("Vision Enhancing LLMs").

We introduce MKS², a novel method that equips LLMs with Multimodal Knowledge Storage and Sharing. Our approach integrates:

Modular Visual Memory (MVM): Stores rich, open-world visual information directly within the LLM's layers.

Mixture of Multimodal Experts (MoME): A soft routing architecture that dynamically invokes specialized visual knowledge during text generation.

![The detailed architecture of MKS2](/figures/model_new.png)

Experiments show that MKS² significantly boosts LLM reasoning on tasks requiring physical and commonsense knowledge, while achieving competitive performance on standard multimodal benchmarks.

## 🔧 Model Training

The training codes will be released soon.

## 📈 Evaluation

### Model Performance on NLP tasks

| Models↓ Types → | COQA | StrategyQA | Social IQA | OBQA | PIQA | RS | MMLU | Avg |
|---|---|---|---|---|---|---|---|---|
| KOSMOS-2 [76] | - | - | - | - | 72.9 | - | - | - |
| Llama-2-13b-chat<sup>+</sup> [47] | 37.02 | 37.80 | 49.46 | 42.89 | 67.29 | 27.45 | 47.69 | 44.23 |
| Vicuna-Llama-2-13b<sup>+</sup> [77] | 58.21 | 38.82 | 55.85 | 55.46 | 67.01 | 37.02 | **50.96** | 51.90 |
| Llama-2-13b-INST-LoRA<sub>r=16</sub> | 57.68 | 63.73 | 63.80 | 58.6 | 71.98 | 38.51 | 46.70 | 57.28 |
| **MKS2-Llama-2-13b** | **62.10** | 74.68 | **65.71** | **67.6** | **76.11** | **41.03** | 48.83 | **62.30** |
| w/o Multimodal-SFT | 58.77 | **74.73** | 64.56 | 60.6 | 75.03 | 38.74 | 48.44 | 60.12 |
| w/o (Multimodal-SFT & MoMEs) | 54.81 | 68.21 | 62.25 | 54.0 | 67.95 | 35.08 | 46.50 | 55.54 |
| Llama-2-7b-chat<sup>+</sup> [47] | 31.62 | 36.83 | 42.37 | 35.3 | 64.90 | 23.53 | 37.05 | 38.82 |
| Vicuna-Llama-2-7b<sup>+</sup> [77] | 42.58 | 67.58 | 39.71 | 38.2 | 55.62 | 29.32 | 38.94 | 44.56 |
| Llama-2-7b-INST-LoRA<sub>r=16</sub> | 41.93 | 74.10 | 54.65 | 39.4 | 53.42 | 27.01 | 38.68 | 47.02 |
| **MKS2-Llama-2-7b** | **49.38** | 76.15 | **58.51** | **54.0** | **68.19** | **33.20** | **39.27** | **54.10** |
| w/o Multimodal-SFT | 44.06 | **76.46** | 57.72 | 50.5 | 67.10 | 28.99 | 37.45 | 51.84 |
| w/o (Multimodal-SFT & MoMEs) | 42.84 | 70.46 | 55.42 | 37.0 | 60.71 | 25.27 | 37.71 | 47.06 |

### Model Performance on VQA tasks

| Models | NumImg | VQAv2 | OK-VQA | STVQA | OCR-VQA | TextVQA | DocVQA | Avg |
|---|---|---|---|---|---|---|---|---|
| Flamingo [62] | >1B | 49.2 | 41.2 | 19.3 | 27.8 | 29.0 | 5.0 | 28.6 |
| MiniGPT-4 (Vicuna-7b) [5] | 5M | 44.3 | 32.1 | 14.0 | 11.5 | 18.7 | 3.0 | 20.6 |
| OFA-Large [63] | 20M | 40.2 | 19.3 | - | - | - | - | - |
| FROMAGE (OPT-6.7b) [87] | 3.3M | 44.1 | 20.1 | - | - | - | - | - |
| mPLUG-Owl<sup>+</sup> [4] | 11B | - | - | 29.3 | 28.6 | 40.3 | 6.9 | - |
| KOSMOS-2 [76] | >2B | 45.6 | - | - | - | - | - | - |
| ViperGPT (>11B) [89] | >129M | - | 48.1 | - | - | - | - | - |
| ImageBind-LLM (Chinese-LLama-7B) [86] | >3M | - | 51.7 | 15.5 | 23.2 | 24.0 | 4.0 | - |
| REVEAL (2B) [90] | >12M | - | 59.1 | - | - | - | - | - |
| InstructBLIP<sup>+</sup> (FlanT5xL) [88] | 129M | 62.6 | 50.1 | 23.9 | 39.7 | 33.1 | 3.8 | 46.0 |
| BLIP-2 (OPT-6.7b) [7] | 129M | 50.1 | 36.4 | 13.4 | 10.6 | 21.2 | 0.8 | 22.1 |
| BLIP-2 (FlanT5xL) [7] | 129M | 42.8 | 25.6 | 15.8 | 26.6 | 25.2 | 2.9 | 23.2 |
| BLIP-2 (FlanT5xL-11B) [7] | 129M | 45.4 | 27.8 | 21.7 | 30.7 | 32.2 | 4.9 | 27.1 |
| LLaVAR (Vicuna-13b) [9] | 1M | 54.2 | 44.9 | 30.2 | 23.4 | 39.5 | 6.2 | 33.1 |
| MKS2-Llama-2-13b | 2.3M | 54.4 | 45.1 | 28.4 | 35.8 | 37.2 | 6.8 | 34.6 |
| LLaVA (Vicuna-7b) [6] | 0.6M | 53.5 | 43.2 | 22.1 | 11.4 | 28.9 | 4.5 | 27.3 |
| LLaVAR (Vicuna-7b) [9] | 1M | 51.3 | 40.6 | 28.9 | 24.9 | 35.8 | 6.2 | 31.3 |
| MKS2-Llama-2-7b | 2.3M | 53.3 | 42.1 | 22.3 | 25.2 | 33.1 | 6.7 | 30.5 |
| w/o Text-SFT | 2.3M | 50.2 | 40.8 | 21.5 | 36.5 | 34.2 | 7.4 | 31.7 |
| w/o (Text-SFT & MoMEs) | 2.3M | 50.1 | 41.2 | 21.4 | 35.3 | 34.3 | 7.3 | 31.6 |
| LLaVA-v1.5<sup>+</sup> (Vicuna-7b) [99] | 1M | 78.4 | 59.8 | 51.3 | 53.1 | 53.1 | 22.4 | 53.0 |
| MKS2-Llama-2-7b<sup>+</sup> | 1M | **83.3** | **64.7** | **51.6** | **54.8** | **53.2** | **22.8** | **55.1** |


