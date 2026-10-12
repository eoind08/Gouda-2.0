# Gouda-2.0
Gouda-2.0 is the second generation family of models from GoudaAI all trained in less than 24 GPU hours (on a 4090 rtx). We release 4 open models ranging from 24m-302m parameters:
- Ricotta-2.0 (24m) - [huggingface](https://huggingface.co/GoudaAI)
- Gruyere-2.0 (63m) - [huggingface](https://huggingface.co/GoudaAI)
- Gouda-2.0 (132m) - [huggingface](https://huggingface.co/GoudaAI)
- Cheddar-2.0 (302m) [huggingface](https://huggingface.co/GoudaAI)

And their instruct versions:
- Ricotta-2.0-Instruct - [huggingface](https://huggingface.co/GoudaAI)
- Gruyere-2.0-Instruct - [huggingface](https://huggingface.co/GoudaAI)
- Gouda-2.0-Instruct - [huggingface](https://huggingface.co/GoudaAI)
- Cheddar-2.0-Instruct [huggingface](https://huggingface.co/GoudaAI)

Instruct versions are avaliable for chat on [gouda-ai](https://gouda-ai.vercel.app)

Training Code is available here: 
- Source Code: [eoind08/GoudaCore-v2](https://github.com/eoind08/GoudaCore-v2)
- SFT Code: [eoind08/UltrachatSFT-gouda](https://github.com/eoind08/UltrachatSFT-gouda)

## Pre Training
Each model had a self-imposed 24 GPU hour limit meaning the number of tokens the model sees gets smaller as the models get larger. For pre-training we targeted a conservative 18 hour run. Pretraining occurred on a 4090 RTX:

| Model                     | Parameters (m) | Tokens (m) | GPU Time (h) | Final Validation Loss |
|---------------------------|----------------|------------|--------------|-----------------------|
| Ricotta-2.0               | 24.1           | 20,701     | 16.94        | 3.21                  |
| Gruyere-2.0               | 62.9           | 8,987      | 16.50        | 2.96                  |
| Gouda-2.0                 | 132.2          | 5,597      | 17.82        | 2.85                  |
| Cheddar-2.0               | 302.1          | 2,809      | 17.97        | 2.88                  |

## SFT
SFT took place on a fixed 0.25 epoch run of UltraChat-200k with 20% decay, this run was trained on a 3080 RTX. Overall, UltraChat was likely a poor choice, long conversations are not necessarily suitable for such small models. Later generations of Gouda will use Smol-Smoltalk, designed specifically for small models. Below are the GPU times, final val loss and tokens for each model:

| Model                     | Parameters (m) | Tokens (m) | GPU Time (h) | Final Validation Loss |
|---------------------------|----------------|------------|--------------|-----------------------|
| Ricotta-2.0               | 24.1           | 64.7       | 0.167        | 2.09                  |
| Gruyere-2.0               | 62.9           | 64.7       | 0.334        | 1.84                  |
| Gouda-2.0                 | 132.2          | 64.7       | 0.583        | 1.73                  |
| Cheddar-2.0               | 302            | 64.6       | 1.325        | 1.74                  |

## Gouda-2.1
For 2.1 there will be 2 major changes:
- Dataset: Since Gouda-0.0.1, we have used the same 10b token dataset of fineweb-edu (as done by Andrej Karparthy). Of course the logical idea may be to simply extend it to a 20b corpus or larger however whilst we are no longer imposing a strict 18 hour training target, it would be preferable to have a smaller amount of high quality data rather than blasted the models with billions of tokens. As such we are moving to a custom 10b token corpus made up of more specific datasets to hopefully produce better factual recall and ability, at the potential sacrifice of coherence and linguistic ability.
- SFT & DPO: For the instruct models we have previously only used a randomly selected 50k conversations from UltraChat-200k as more conversations produced a degrading affect on the models eval scores and a tendency to default to "Sorry I cannot do X". For 2.1 we plan to use Smol-Smoltalk specifically designed for models around the Gouda suite size followed by DPO on UltraFeedback. More research will need to be done into the use of Smol-Smoltalk as early experiments on Ricotta-2.0 found worse benchmark and qualiative results when compared with Ricotta-2.0-Instruct (UltraChat)

## Eval Results
Across evaluation benchmarks, the gouda both pretrained and instruct models display results comparable to models of a similar size despite having a substantially smaller token-base.

### Gouda-2.0 (132m, 5.6B tokens) vs Pythia-160m (300B tokens), raw_acc
| Task          | Gouda-2.0 | Pythia-160m | Gap  |
|---------------|-----------|-------------|------|
| ARC-Easy      | .511      | .435        | +7.6 |
| ARC-Challenge | .226      | .188        | +3.8 |
| SciQ          | .754      | .741        | +1.3 |
| PIQA          | .629      | .627        | +0.2 |
| WinoGrande    | .512      | .531        | -1.9 |
| LAMBADA       | .266      | .328        | -6.2 |


### PRETRAINED MODELS - Name (Parameters / Tokens)
| Task | Ricotta-2.0 (24m / 20.70B) | Gruyère-2.0 (63m / 8.99B) | Gouda-2.0 (132m / 5.60B) | Cheddar-2.0 (302m / 2.8B) |
|---|---:|---:|---:|---:|
| LAMBADA (OpenAI) | 0.213 +- 0.006 |0.248 +- 0.020 | 0.266 +- 0.006 | 0.262 +- 0.006 |
| PIQA (acc_norm) | 0.596 +- 0.011 | 0.620 +- 0.011 | 0.626 +- 0.011 | 0.624 +- 0.011 |
| WinoGrande | 0.513 +- 0.014 | 0.522 +- 0.014 | 0.512 +- 0.014 | 0.515 +- 0.014 |
| WSC | 0.535 +- 0.03 | 0.535 +- 0.030 | 0.553 +- 0.030 | 0.520 +- 0.030 |
| ARC - Easy (acc_norm) | 0.403 +- 0.010 | 0.439 +- 0.010 | 0.458 +- 0.010 | 0.459 +- 0.010 |
| ARC - Challenge (acc_norm) | 0.226 +- 0.012 | 0.242 +- 0.013 | 0.255 +- 0.013 | 0.257 +- 0.013 |
| SciQ (acc_norm) | 0.612 +- 0.015 | 0.644 +- 0.015 | 0.669 +- 0.015 | 0.654 +- 0.015 |
| HellaSwag (acc_norm) | 0.283 +- 0.004 | 0.312 +- 0.005 | 0.326 +- 0.005 | 0.327 +- 0.005 |
| OpenBookQA (acc_norm) | 0.286 +- 0.020 | 0.284 +- 0.020 | 0.294 +- 0.020 | 0.316 +- 0.021 |
| BoolQ | 0.490 +- 0.009 | 0.607 +- 0.009 | 0.546 +- 0.009 | 0.571 +- 0.009 |
| COPA | 0.57 +- 0.050 | 0.62 +- 0.049 | 0.66 +- 0.048 | 0.600 +- 0.049 |
| TruthfulQA (MC2) | 0.454 +- 0.015 | 0.422 +- 0.015 | 0.411 +- 0.015 | 0.413 + 0.015 |
| WikiText (PPL ↓) | 77.9 | 44.8 | 38.9 | 38.9 |

### INSTRUCT MODELS - Name (Parameters / SFT Tokens)
| Task | Ricotta-2.0-Instruct (24m / 64.7m) | Gruyère-2.0-Instruct (63m / 64.7m) | Gouda-2.0-Instruct (132m / 64.7m) | Cheddar-2.0-Instruct (302m / 64.6m) |
|---|---:|---:|---:|---:|
| LAMBADA (OpenAI) | 0.231 +- 0.006 | 0.265 +- 0.006 | 0.292 +- 0.006 | 0.283 +- 0.006 |
| PIQA (acc_norm) | 0.603 +- 0.011 | 0.613 +- 0.011 | 0.633 +- 0.011 | 0.643 +- 0.011 |
| WinoGrande | 0.515 +- 0.014 | 0.505 +- 0.014 | 0.524 +- 0.014 | 0.515 +- 0.014 |
| WSC | 0.520 +- 0.030 | 0.549 +- 0.030 | 0.520 +- 0.030 | 0.550 +- 0.030 |
| ARC - Easy (acc_norm) | 0.393 +- 0.010 | 0.428 +- 0.010 | 0.418 +- 0.010 | 0.455 +- 0.010 |
| ARC - Challenge (acc_norm) | 0.230 +- 0.012 | 0.236 +- 0.012 | 0.270 +- 0.013 | 0.272 +- 0.013 |
| SciQ (acc_norm) | 0.568 +- 0.016 | 0.628 +- 0.015 | 0.626 +- 0.015 | 0.653 +- 0.0151 |
| HellaSwag (acc_norm) | 0.282 +- 0.004 | 0.307 +- 0.005 | 0.328 +- 0.005 | 0.330 +- 0.005 |
| OpenBookQA (acc_norm) | 0.282 +- 0.020 | 0.298 +- 0.020 | 0.314 +- 0.021 | 0.310 +- 0.021 |
| BoolQ | 0.516 +- 0.009 | 0.608 +- 0.009 | 0.523 +- 0.009 | 0.601 +- 0.009 |
| COPA | 0.58 +- 0.050 | 0.6 +- 0.049 | 0.6 +- 0.049 | 0.65 +- 0.048 |
| TruthfulQA (MC2) | 0.434 +- 0.015 | 0.411 +- 0.015 | 0.393 +- 0.015 | 0.406 +- 0.015 |
| WikiText (PPL ↓) | 89.9 | 52.6 | 44.5 | 42.0 |
