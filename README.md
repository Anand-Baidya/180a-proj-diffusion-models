# EDM Diffusion Models on CIFAR-10 and MNIST

DSC-180A, Fall 2026, Section D32

This repository contains images generated from CIFAR-10 dataset with NVIDIA's pretrained EDM network, applies classifier-free guidance (CFG), and varies the guidance weight $w$ to measure FID score.

## NA-RFM Replication on CIFAR-10 (Table 2)
- Paper: *Noise-Aligned RFM Steering*, Wang, Belkin and Wang, 2026 ([arXiv 2602.11395](https://arxiv.org/abs/2602.11395))
- Replicates: Table 2, CIFAR-10 label guidance

## Setup
- GPU: NVIDIA A100 on Google Colab
- Run time: 3 to 4 hours
- Google Drive: `class_k.pt` (Denoisers and RFM directions), scores, and generated images are saved to `MyDrive/dsc180_narfm`

## How to run
1. Open the notebook in Google Colab
2. Change runtime type to NVIDIA A100 GPU (Requires Google Colab Pro plan)
3. Run cells in sequential order

## Where each result comes from

| Result | Sec. |
|---|---|
| Gaussian denoisers, all ten classes | 5a |
| RFM directions and AUCs, all ten classes | 5a |
| Images: unguided, RFM only, NA-RFM | 5b |
| Images: noise alignment only, $\lambda$ = 3 and 8 | 5b |
| FID | 5c |
| Seconds per image | 5c |
| Comparison with the paper's Table 2 | 5d|
| Image grids | 5d |
| What matches and what does not | 5d |

## Results
256 images per class, 100 sampling steps.

| Setting | Our accuracy (%) | Paper's accuracy (%) | Our FID; 256 images per class | Paper's FID; 2048 images per class | Our seconds per image | Paper's seconds per batch of 16 images |
| --- | --- | --- | --- | --- | --- | --- |
| Unguided | 10.0 | not reported | 157.9 | not reported | 0.067 | not reported |
| Noise alignment only, $\lambda$ = 3 | 61.8 | 62.0 | 91.0 | 99.0 | 0.067 | 5.8 |
| Noise alignment only, $\lambda$ = 8 | 79.7 | 80.0 | 111.0 | 120.0 | 0.066 | 5.8 |
| RFM only | 96.2 | 94.8 | 93.1 | 40.3 | 0.131 | 6.8 |
| NA-RFM | 96.4 | 96.6 | 92.8 | 41.4 | 0.113 | 6.2 |


## Acknowledgement of AI Use:
I used Google Gemini to understand the important points of the EDM paper before I started reading it. 