# Paper Pal

A small AI agent that answers questions about research papers on arXiv. I built it to learn the words people use for AI in production: harness, tool calling, memory, guardrails, evals, and more.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/shivangraikar/paper-pal/blob/main/paper_pal.ipynb)

Companion notebook for my article: **[Harness, Evals, Guardrails: I Built One Small Agent to Learn the Words Everyone Uses](link)**

## What's inside

One notebook, `paper_pal.ipynb`, that builds the agent step by step:

- **Model:** Qwen2.5-3B-Instruct, an open-weight model that runs on Colab's free GPU
- **Tools:** search arXiv, read a paper's abstract, save and list notes
- **Harness:** the agent loop in plain Python, no framework
- **Memory:** notes saved to a JSON file and read back in later conversations
- **Guardrails:** a tool allowlist, plus a fake paper that tries to hijack the agent
- **Evals:** 10 questions with known answers, scored for correct and grounded answers
- **Three versions:** baseline, a better prompt (v2), then rules enforced in code (v3)

## How to run

1. Click **Open in Colab** above.
2. Go to **Runtime → Change runtime type → T4 GPU**.
3. Go to **Runtime → Run all**.

No API key needed. The model downloads in about two minutes. No GPU? Set `MODE = "dry_run"` in the first code cell.

## Results from one run

| Version | Correct | Grounded |
|---|---|---|
| Baseline | 9/10 | 8/10 |
| v2 (better prompt) | 8/10 | 7/10 |
| v3 (rules in code) | 8/10 | 8/10 |

Your numbers will vary between runs. With only 10 questions, a difference of one or two is mostly noise.

## Notes

- arXiv may rate-limit you (HTTP 429) if you run the notebook several times in a row. The notebook waits, retries, and falls back to a small set of bundled papers if it has to.
- `MODE = "claude"` runs the same agent on a hosted Claude model. It needs your own Anthropic API key and is the only part that costs money.
