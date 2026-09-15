# MI-FGSM CVPR 2018 Reproduction

Reproduction of:

Dong et al.,
"Boosting Adversarial Attacks with Momentum",
CVPR 2018.

## Experiment

Table 1: Inc-v3 → Inc-v4

Settings:
- Dataset: 1000 ImageNet images
- Source model: Inception-v3
- Target model: Inception-v4
- epsilon: 16/255
- iterations: 10
- momentum: 1.0
- Loss: MainLoss + 0.4 × AuxLogitsLoss

## Result

| Source | Target | Paper | Reproduced |
|---|---|---:|---:|
| Inc-v3 | Inc-v4 | 48.8% | 50.97% |

## Notes

The initial implementation achieved only 4.92%.
After inspecting the official implementation, I found that
the auxiliary classifier loss was missing.

Adding:

MainLoss + 0.4 × AuxLogitsLoss

increased the transfer attack success rate to 50.97%.
