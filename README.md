# MI-FGSM CVPR 2018 Reproduction

Reproduction of:

Dong et al.,
"Boosting Adversarial Attacks with Momentum",
CVPR 2018.

## References

- Paper: Dong et al., "Boosting Adversarial Attacks with Momentum", CVPR 2018.
- Official implementation: https://github.com/dongyp13/Non-Targeted-Adversarial-Attacks

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

## Reproduction Process

| Version | Inc-v3 → Inc-v4 |
|---|---:|
| Initial implementation | 4.92% |
| + AuxLogits loss | 50.97% |
| Paper | 48.8% |

The large discrepancy in the initial implementation was traced
to the missing auxiliary classifier loss.

## Result

| Source | Target | Paper | Reproduced |
|---|---|---:|---:|
| Inc-v3 | Inc-v4 | 48.8% | 50.97% |

## Notes

The initial implementation achieved only 4.92%.
After inspecting the official implementation, I found that the
auxiliary classifier loss was missing from the attack objective.

Adding:

MainLoss + 0.4 × AuxLogitsLoss

increased the Inc-v3 → Inc-v4 transfer attack success rate
from 4.92% to 50.97%, compared with 48.8% reported in the paper.
