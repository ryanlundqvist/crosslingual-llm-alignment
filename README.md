# XEthicsBench (crosslingual-llm-alignment)

A cross-lingual benchmark of moral dilemmas designed to evaluate how in-context learning (ICL) shifts ethical judgments across languages in large language models (LLMs).

---

## Prerequisites

- Python 3.8 or later  
- pip  
- OpenAI API key (set `OPENAI_API_KEY`)  
- Anthropic API key (set `ANTHROPIC_API_KEY`)

---

## Installation

1. Clone or unzip this repository.  
2. *(Optional)* Create and activate a virtual environment:

   ```bash
   python3 -m venv venv
   source venv/bin/activate

## Usage
### 1. Running the Claude 3 Pipeline
Open crosslingual_claude.ipynb.

Use the XEthicsBench dataset json file found in the data folder.
Ensure ANTHROPIC_API_KEY is set in your environment. (If you do not API access, just skip this step and use our claude_benchmark_results.json in data)

Run all cells.

The notebook will generate data/claude_benchmark_results.json.

### 2. Running the GPT-4o Pipeline
Open crosslingual_gpt.ipynb.

Use the XEthicsBench dataset json file found in the data folder.
Ensure OPENAI_API_KEY is set. (If you do not API access, just skip this step and use our gpt4o_benchmark_results.json in data)

Run all cells.

The notebook will generate data/gpt4o_benchmark_results.json.

### 3. Evaluating Results
Open evaluate_results.ipynb.

In the first cell, set JSON_FILE to either:
"data/gpt4o_benchmark_results.json" or "data/claude_benchmark_results.json"

Run all cells.

The notebook will output tables and summary statistics for:

- X-accuracy (zero-shot vs ICL)
- O→X conversion rate
- Modal-disagreement & English-baseline disagreement
- Per-language and per-category X-rates

