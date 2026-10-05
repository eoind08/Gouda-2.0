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
| LAMBADA (OpenAI) | — |0.248 +- 0.020 | 0.266 +- 0.006 | — |
| PIQA | — | 0.620 +- 0.011 | 0.626 +- 0.011 | — |
| WinoGrande | - | 0.522 +- 0.014 | 0.512 +- 0.014 | — |
| WSC | — | 0.535 +- 0.030 | 0.553 +- 0.030 | — |
| ARC - Easy | — | 0.439 +- 0.010 | 0.458 +- 0.010 | — |
| ARC - Challenge | - | 0.242 +- 0.013 | 0.255 +- 0.013 | — |
| SciQ | — | 0.644 +- 0.015 | 0.669 +- 0.015 | — |
| HellaSwag | — | 0.312 +- 0.005 | 0.326 +- 0.005 | — |
| OpenBookQA | — | 0.284 +- 0.020 | 0.294 +- 0.020 | — |
| BoolQ | — | 0.607 +- 0.009 | 0.546 +- 0.009 | — |
| COPA | — | 0.62 +- 0.049 | 0.66 +- 0.048 | — |
| TruthfulQA (MC2) | — | 0.422 +- 0.015 | 0.411 +- 0.015 | — |
| WikiText (PPL ↓) | — | 44.8 | 38.9 | — |

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
