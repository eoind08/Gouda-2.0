# Gouda-2.0
Gouda-2.0 is the second generation family of models from GoudaAI all trained in less than 24 GPU hours (on a 4090 rtx). We release 3 open models ranging from 24m-132m parameters:
- Ricotta (24m)
- Gruyere (63m)
- Gouda (132m)

## 24 GPU Hours
Each model had a self-imposed 24 GPU hour limit meaning the number of tokens the model sees gets smaller as the models get larger

## Eval Results
Across evaluation benchmarks, the gouda both pretrained and instruct models display results comparable to models of a similar size despite having a substantially smaller token-base.


### PRETRAINED MODELS
| Task | Ricotta-2.0 | Gruyère-2.0 | Gouda-2.0 | Cheddar-2.0 |
|---|---:|---:|---:|---:|
| LAMBADA (OpenAI) | — | — | — | — |
| PIQA | — | — | — | — |
| WinoGrande | — | — | — | — |
| WSC | — | — | — | — |
| ARC - Easy | — | — | — | — |
| ARC - Challenge | — | — | — | — |
| SciQ | — | — | — | — |
| HellaSwag | — | — | — | — |
| OpenBookQA | — | — | — | — |
| BoolQ | — | — | — | — |
| COPA | — | — | — | — |
| TruthfulQA (MC2) | — | — | — | — |
| WikiText (PPL ↓) | — | — | — | — |

### INSTRUCT MODELS
| Task | Ricotta-2.0-Instruct | Gruyère-2.0-Instruct | Gouda-2.0-Instruct | Cheddar-2.0-Instruct |
|---|---:|---:|---:|---:|
| LAMBADA (OpenAI) | — | — | — | — |
| PIQA | — | — | — | — |
| WinoGrande | — | — | — | — |
| WSC | — | — | — | — |
| ARC - Easy | — | — | — | — |
| ARC - Challenge | — | — | — | — |
| SciQ | — | — | — | — |
| HellaSwag | — | — | — | — |
| OpenBookQA | — | — | — | — |
| BoolQ | — | — | — | — |
| COPA | — | — | — | — |
| TruthfulQA (MC2) | — | — | — | — |
| WikiText (PPL ↓) | — | — | — | — |
