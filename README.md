# Usage:

Having one of the following sample scripts in a `method.py` file:

```python
from llmfoundry.eval.eval_ext import evaluate
from transformers import AutoModelForCausalLM

model = AutoModelForCausalLM.from_pretrained("ISTA-DASLab/Llama-3-8B-Instruct-GPTQ-4bit", device_map="auto")
evaluate(
    model, 
    "/nfs/scistore19/alistgrp/amoeini/llm-foundry/scripts/eval/yamls/hf_eval.yaml", 
    '/nfs/scistore19/alistgrp/amoeini/llm-foundry/scripts')
```

```python
from llmfoundry.eval.eval_ext import evaluate
from hqq.engine.hf import HQQModelForCausalLM
import sys

model = HQQModelForCausalLM.from_quantized("PrunaAI/meta-llama-Meta-Llama-3-8B-Instruct-HQQ-4bit-smashed")
evaluate(
    model, 
    "/nfs/scistore19/alistgrp/amoeini/llm-foundry/scripts/eval/yamls/hf_eval.yaml", 
    '/nfs/scistore19/alistgrp/amoeini/llm-foundry/scripts', 
    tokenizer_name='PrunaAI/meta-llama-Meta-Llama-3-8B-Instruct-HQQ-4bit-smashed', config_overrides=sys.argv[1:])
```

We then run the following command:

```bash
composer method.py
```