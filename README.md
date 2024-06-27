# Usage:

Having one of the following sample scripts in a `method.py` file:

```python
from llmfoundry.eval.eval_ext import evaluate
from transformers import AutoModelForCausalLM

model = AutoModelForCausalLM.from_pretrained("ISTA-DASLab/Llama-3-8B-Instruct-GPTQ-4bit", device_map="auto")
evaluate(
    model, 
    "/path/to/hf_eval.yaml", 
    '/path/to/llm-foundry/scripts')
```

```python
from llmfoundry.eval.eval_ext import evaluate
from hqq.engine.hf import HQQModelForCausalLM

model = HQQModelForCausalLM.from_quantized("PrunaAI/meta-llama-Meta-Llama-3-8B-Instruct-HQQ-4bit-smashed")
evaluate(
    model, 
    "/path/to/hf_eval.yaml", 
    '/path/to/llm-foundry/scripts', 
    tokenizer_name='PrunaAI/meta-llama-Meta-Llama-3-8B-Instruct-HQQ-4bit-smashed')
```

We then run the following command:

```bash
composer method.py
```
