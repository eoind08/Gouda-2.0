# Gouda-2.0
Gouda-2.0 is the second generation family of models from GoudaAI all trained in less than 24 GPU hours (on a 4090 rtx). We release 4 open models ranging from 24m-302m parameters:
- Ricotta (24m)
- Gruyere (63m)
- Gouda (132m)
- Cheddar (302m) (IN PROGRESS)

## 24 GPU Hours
Each model had a self-imposed 24 GPU hour limit meaning the number of tokens the model sees gets smaller as the models get larger. For pre-training we targeted a conservative 18 hour run. Pretraining occurred on a 4090 RTX with SFT on a 3080 RTX:

| Model                     | Parameters (m) | Tokens (m) | GPU Time (h) | Final Validation Loss |
|---------------------------|----------------|------------|--------------|-----------------------|
| Ricotta-2.0               | 24.1           | 20,701     | 16.94        | 3.21                  |
| Gruyere-2.0               | 62.9           | 8,987      | 16.50        | 2.96                  |
| Gouda-2.0                 | 132.2          | 5,597      | 17.82        | 2.85                  |
| Cheddar-2.0 (In Progress) | 302            | -          | -            | -                     |


## Eval Results
Across evaluation benchmarks, the gouda both pretrained and instruct models display results comparable to models of a similar size despite having a substantially smaller token-base.


### PRETRAINED MODELS - Name (Parameters / Tokens)
| Task | Ricotta-2.0 (24m / 20.70B) | Gruyère-2.0 (63m / 8.99B) | Gouda-2.0 (132m / 5.60B) | Cheddar-2.0 (302m / ~2.8B) |
|---|---:|---:|---:|---:|
| LAMBADA (OpenAI) | 0.213 +- 0.006 |0.248 +- 0.020 | 0.266 +- 0.006 | — |
| PIQA | 0.596 +- 0.011 | 0.620 +- 0.011 | 0.626 +- 0.011 | — |
| WinoGrande | 0.513 +- 0.014 | 0.522 +- 0.014 | 0.512 +- 0.014 | — |
| WSC | 0.535 +- 0.03 | 0.535 +- 0.030 | 0.553 +- 0.030 | — |
| ARC - Easy | 0.403 +- 0.010 | 0.439 +- 0.010 | 0.458 +- 0.010 | — |
| ARC - Challenge | 0.226 +- 0.012 | 0.242 +- 0.013 | 0.255 +- 0.013 | — |
| SciQ | 0.612 +- 0.015 | 0.644 +- 0.015 | 0.669 +- 0.015 | — |
| HellaSwag | 0.283 +- 0.004 | 0.312 +- 0.005 | 0.326 +- 0.005 | — |
| OpenBookQA | 0.286 +- 0.020 | 0.284 +- 0.020 | 0.294 +- 0.020 | — |
| BoolQ | 0.490 +- 0.009 | 0.607 +- 0.009 | 0.546 +- 0.009 | — |
| COPA | 0.57 +- 0.050 | 0.62 +- 0.049 | 0.66 +- 0.048 | — |
| TruthfulQA (MC2) | 0.454 +- 0.015 | 0.422 +- 0.015 | 0.411 +- 0.015 | — |
| WikiText (PPL ↓) | 77.9 | 44.8 | 38.9 | — |

### INSTRUCT MODELS - Name (Parameters / SFT Tokens)
| Task | Ricotta-2.0-Instruct (24m / 64.7m) | Gruyère-2.0-Instruct (63m / 64.7m) | Gouda-2.0-Instruct (132m / 64.7m) | Cheddar-2.0-Instruct (302m / ~64.7m) |
|---|---:|---:|---:|---:|
| LAMBADA (OpenAI) | 0.231 +- 0.006 | 0.265 +- 0.006 | 0.292 +- 0.006 | — |
| PIQA | 0.603 +- 0.011 | 0.613 +- 0.011 | 0.633 +- 0.011 | — |
| WinoGrande | 0.515 +- 0.014 | 0.505 +- 0.014 | 0.524 +- 0.014 | — |
| WSC | 0.520 +- 0.030 | 0.549 +- 0.030 | 0.520 +- 0.030 | — |
| ARC - Easy | 0.393 +- 0.010 | 0.428 +- 0.010 | 0.418 +- 0.010 | — |
| ARC - Challenge | 0.230 +- 0.012 | 0.236 +- 0.012 | 0.270 +- 0.013 | — |
| SciQ | 0.568 +- 0.016 | 0.628 +- 0.015 | 0.626 +- 0.015 | — |
| HellaSwag | 0.282 +- 0.004 | 0.307 +- 0.005 | 0.328 +- 0.005 | — |
| OpenBookQA | 0.282 +- 0.020 | 0.298 +- 0.020 | 0.314 +- 0.021 | — |
| BoolQ | 0.516 +- 0.009 | 0.608 +- 0.009 | 0.523 +- 0.009 | — |
| COPA | 0.58 +- 0.050 | 0.6 +- 0.049 | 0.6 +- 0.049 | — |
| TruthfulQA (MC2) | 0.434 +- 0.015 | 0.411 +- 0.015 | 0.393 +- 0.015 | — |
| WikiText (PPL ↓) | 89.9 | 52.6 | 44.5 | — |
