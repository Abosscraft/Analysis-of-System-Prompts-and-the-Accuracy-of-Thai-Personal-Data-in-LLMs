# Analysis-of-System-Prompts-and-the-Accuracy-of-Thai-Personal-Data-in-LLMs
Benchmarking hallucination in Thai-language LLM outputs across 4 models, 2 system prompts, and 3 fame levels. Atomic facts verified against Thai Wikipedia. Key finding: niche subjects (athletes) trigger near-total fabrication in smaller models.

Overview
This project investigates hallucination behavior in Large Language Models (LLMs) when generating Thai-language biographies of public figures. We evaluate four models across two system prompt conditions and three subject fame levels, using automated fact verification against Thai Wikipedia as ground truth.
Models Tested
ModelProviderSizeGPT-4o-miniOpenAI~8BMythoMax-L2-13BGryphe13BLlama-3-8B-InstructMeta8BPhi-4Microsoft~14B
Experimental Design
System Prompts

neutral — No special instructions
fact_checker — Model instructed to prioritize factual accuracy

Fame Levels

Singer — Mainstream entertainers
Politician — National-level politicians
Sport — Athletes (niche/low-coverage subjects)

Fact Position
Each biography is split into early, middle, and late thirds to test whether hallucination clusters at any particular position.
Metrics
MetricFormulaFActScoreSupported / (Supported + Not-Supported)Hallucination RateNot-Supported / (Supported + Not-Supported)Abstention RateAbstained / Total Requests
Dataset

12,116 raw rows
4,711 labeled atomic facts (Supported + Not-Supported)
146 unique entities
Ground truth: Thai Wikipedia

Key Findings

Fact-Checker prompt reduces hallucination meaningfully only in GPT-4o-mini (~4pp improvement). Smaller models show little to no response.
Sport subjects have the highest hallucination rate (~87%), significantly above Singer (~76%) and Politician (~76%).
Identity fabrication — When models don't recognize a subject, they invent an entirely different profession. Athletes were commonly described as award-winning novelists or literary critics.
Position effect is model-dependent. GPT-4o-mini hallucinates more in early sections; other models show near-uniform error distribution.

Stack
Python · pandas · OpenRouter API · Wikipedia API · Jupyter Notebook
