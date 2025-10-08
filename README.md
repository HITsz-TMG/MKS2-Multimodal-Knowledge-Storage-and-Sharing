# MKS2-Multimodal-Knowledge-Storage-and-Sharing
The codes of Vision Enhancing LLMs: Multimodal Knowledge Storage and Sharing in LLMs


## Method Description

While most Multimodal LLMs (MLLMs) use language models to process vision ("LLMs for Vision"), we explore the inverse: using visual knowledge to enhance the core capabilities of LLMs ("Vision Enhancing LLMs").

We introduce MKS², a novel method that equips LLMs with Multimodal Knowledge Storage and Sharing. Our approach integrates:

Modular Visual Memory (MVM): Stores rich, open-world visual information directly within the LLM's layers.

Mixture of Multimodal Experts (MoME): A soft routing architecture that dynamically invokes specialized visual knowledge during text generation.

Experiments show that MKS² significantly boosts LLM reasoning on tasks requiring physical and commonsense knowledge, while achieving competitive performance on standard multimodal benchmarks.

