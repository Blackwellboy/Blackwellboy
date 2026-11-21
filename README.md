# Blackwellboy

![DGX Spark x6](https://img.shields.io/badge/DGX%20Spark-x6%20GB10-7b2ff7) ![RTX 5090](https://img.shields.io/badge/RTX-5090-9b59b6) ![EXL3 first](https://img.shields.io/badge/quant-EXL3%20first-a855f7) ![Raw data](https://img.shields.io/badge/raw%20data-published-6d28d9)

**Independent testing and deployment engineering for local AI models.** Six DGX Sparks (GB10), one RTX 5090 box and an M-series Mac. I serve big open models at home, measure them properly, and publish the numbers with the conditions and raw data. Losers too.

## Start here

| If you want… | Go to |
|---|---|
| The traps that make serving benchmarks lie | **[model-serving-minefield](https://github.com/Blackwellboy/model-serving-minefield)** (registry) · [hermes-minefield](https://github.com/Blackwellboy/hermes-minefield) (Hermes plugin) · [evidence](https://github.com/Blackwellboy/model-serving-minefield-evidence) |
| Uncensored DeepSeek-V4.1-Flash on two Sparks | **[DeepSeek-V4.1-Flash-1017-BLACKFOLD-TP2](https://github.com/Blackwellboy/DeepSeek-V4.1-Flash-1017-BLACKFOLD-TP2)** |
| Why one benchmark number misleads | **[qwen38-27b-is-not-one-number](https://github.com/Blackwellboy/qwen38-27b-is-not-one-number)** |
| A full study: sweep, 12 h soak, thinking-gate dose-response | **[laguna-s21-lab](https://github.com/Blackwellboy/laguna-s21-lab)** |
| Which Hugging Face models quietly vanished | **[hf-vanished](https://github.com/Blackwellboy/hf-vanished)** |

## Model recipes and results

| Repo | Model | Hardware |
|---|---|---|
| [DeepSeek-V4.1-Flash-1017-BLACKFOLD-TP2](https://github.com/Blackwellboy/DeepSeek-V4.1-Flash-1017-BLACKFOLD-TP2) | DeepSeek-V4.1-Flash-1017, uncensored, TensorFold TP2 | 2× DGX Spark |
| [qwen38-27b-is-not-one-number](https://github.com/Blackwellboy/qwen38-27b-is-not-one-number) | Qwen3.8-27B across engines and quants | RTX 5090 + 3× Spark |
| [laguna-s21-lab](https://github.com/Blackwellboy/laguna-s21-lab) | Laguna S 2.1 NVFP4 | DGX Spark |
| [Hy3-295B-NVFP4-MTP-Dual-DGX-Spark](https://github.com/Blackwellboy/Hy3-295B-NVFP4-MTP-Dual-DGX-Spark) | Tencent Hy3-295B NVFP4 + MTP | 2× DGX Spark |
| [MiniMax-M3-2x-DGX-Spark-stock-driver](https://github.com/Blackwellboy/MiniMax-M3-2x-DGX-Spark-stock-driver) | MiniMax-M3 428B, stock driver | 2× DGX Spark |
| [minicpm-v47-35b-rtx5090](https://github.com/Blackwellboy/minicpm-v47-35b-rtx5090) | MiniCPM-V 4.7 35B-A3B: AWQ vs GGUF | RTX 5090 |

## Engines I test and patch

[REXL3](https://github.com/Blackwellboy/REXL3) (Rust EXL3 server) · [TensorFold](https://github.com/Blackwellboy/TensorFold) (GLM TP4 / DeepSeek TP2 branches) · [vllm-exl3](https://github.com/Blackwellboy/vllm-exl3) · [vllm](https://github.com/Blackwellboy/vllm) (DSV4 sparse-MLA branches). Findings go upstream as issues with repro steps.

## Other things

[little-chits](https://github.com/Blackwellboy/little-chits): a tiny civilisation you can watch, with any LLM in their minds. Site: [blackwellboy.github.io](https://blackwellboy.github.io).

## The method

Every model on the fleet gets the same battery, in the same engine as its baseline:

1. **Speed**: engine-labelled tok/s (plain decode *and* real work), TTFT at two depths, peak VRAM, draft acceptance
2. **Quality**: frozen suite (exact-answer, sign probes, GSM8K, MMLU-Pro, IFEval), fixed seed, SHA-pinned
3. **BB packs**: gotchas, smarts, instruct, tools, context, reliability; never averaged into one number
4. **ProgramBench** for real coding work, and **fresh-text BPB** as a cheap damage check for edits and quants
5. **Refusal audit** for uncensored builds, with a harmless control set
6. **Soak**: long sustained load with degradation detection

Rules: the token limit is big enough for full answers including thinking, and every result reports its cap-hit count. A run with meaningful cap hits is invalid and is never a headline. Conditions sit beside every figure. Negative results get published.

## Support

If the numbers here saved you a week on your own Spark or 5090: GitHub Sponsors or Buy Me a Coffee (links in the sidebar).
