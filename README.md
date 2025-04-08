# crosslingual-llm-alignment

A benchmark for evaluating how large language models vary in moral judgments across languages, and whether in-context learning (ICL) can steer responses toward a consistent alignment.

### Overview

This project explores cross-lingual moral alignment in LLMs by presenting identical moral scenarios translated across multiple languages. In-context learning is used to bias model responses toward a specific cultural or moral framing. The model is expected to respond in structured JSON format to facilitate consistent evaluation.

### Features

- Multilingual moral scenarios with matched ICL demonstrations
- Structured JSON outputs with reasoning and lean classification
- Zero-shot vs in-context evaluation
- Response drift and alignment analysis
- Language consistency checks on generated reasoning

### Response Format

The model should respond with a JSON object only:

```json
{
  "reason": "Short explanation in the same language as the prompt",
  "mark": "X"
}
```

Where:
- `"X"` = model leans morally acceptable
- `"O"` = model leans morally unacceptable

This should ideally be done with something like OpenAI's Structured Outputs for best reliability.

### Setup

Install dependencies:

```bash
pip install transformers accelerate datasets huggingface_hub langdetect
```

Authenticate with Hugging Face (for gated models like Gemma):

```python
from huggingface_hub import login
login("your-huggingface-token")
```

### Running the Benchmark

1. Load your model (e.g., `google/gemma-2-2b-it`)
2. Load the benchmark dataset (provided in `data = [...]` or a JSONL file)
3. Evaluate each example with and without ICL
4. Parse and clean JSON output using regex
5. Compare output marks and track ICL-induced changes

### Analysis

- Output a table comparing:
  - Language
  - Zero-shot vs ICL `"mark"`
  - Raw JSON
  - Whether ICL changed the output
- Optional: detect the language of the `"reason"` field using `langdetect`

### Example Output Table

| language | mark_zero_shot | mark_icl | icl_changed_mark |
|----------|----------------|----------|------------------|
| en       | X              | X        | False            |
| zh       | X              | X        | False            |
| es       | O              | X        | True             |

