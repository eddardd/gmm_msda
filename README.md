# Lighter, Better, Faster Multi-Source Domain Adaptation with Gaussian Mixture Models for optimal Transport

In this repository, we provide the source code for our paper "Lighter, Better, Faster Multi-Source Domain Adaptation with Gaussian Mixture Models for optimal Transport", Accepted at the European Conference on Machine Learning and Principles and Practices of Knowledge Discovery in Databases (ECML-PKDD'24), which proposes new tools for multi-source domain adaptation through Gaussian Mixture Model-based OT. Especially, here you will find our source code for reproducing the toy example in Section 4.1 of our main paper.

## Abstract

In this paper, we tackle Multi-Source Domain Adaptation (MSDA), a task in transfer learning where one adapts multiple heterogeneous, labeled source probability measures towards a different, unlabeled target measure. We propose a novel framework for MSDA, based on Optimal Transport (OT) and Gaussian Mixture Models (GMMs). Our framework has two key advantages. First, OT between GMMs can be solved efficiently via linear programming. Second, it provides a convenient model for supervised learning, especially classification, as components in the GMM can be associated with existing classes. Based on the GMM-OT problem, we propose a novel technique for calculating barycenters of GMMs. Based on this novel algorithm, we propose two new strategies for MSDA: GMM-Wasserstein Barycenter Transport (WBT) and GMM-Dataset Dictionary Learning (DaDiL). We empirically evaluate our proposed methods on four benchmarks in image classification and fault diagnosis, showing that we improve over the prior art while being faster and involving fewer parameters.

__Keyword.__ Domain Adaptation, Optimal Transport, Gaussian Mixture Models

## Contributions

We summarize our contributions as follows,

1. We propose a novel strategy for mapping the parameters of GMMs using OT.
2. We propose a novel algorithm for computing mixture-Wasserstein barycenters of GMMs.
3. We propose an efficient parametric extension of the [WBT](https://openaccess.thecvf.com/content/CVPR2021/html/Montesuma_Wasserstein_Barycenter_for_Multi-Source_Domain_Adaptation_CVPR_2021_paper.html?ref=https://giter.site) and [DaDiL](https://arxiv.org/abs/2307.14953) algorithms based on GMMs.

## Results

### Office Home

| Algorithm        | Ar                | Cl                | Pr                | Rw                | Avg. $\uparrow$              |
|------------------|-------------------|-------------------|-------------------|-------------------|------------------------------|
| ResNet101        | 72.90             | 62.20             | 83.70             | 85.00             | 75.95                        |
| M$^{3}$SDA       | 71.13             | 61.41             | 80.18             | 80.64             | 73.34                        |
| LtC-MSDA         | 74.52             | 60.56             | 85.52             | 83.63             | 76.05                        |
| KD3A             | 73.80             | 63.10             | 84.30             | 83.50             | 76.17                        |
| Co-MDA$^{\ddag}$ | 74.40             | 64.00             | 85.30             | 83.90             | 76.90                        |
| WJDOT            | 74.28             | 63.80             | 83.78             | 84.52             | 76.59                        |
| WBT              | 75.72             | 63.80             | 84.23             | 84.63             | 77.09                        |
| DaDiL-E          | __77.16__         | 64.95             | 85.47             | 84.97             | _78.14_                      |
| DaDiL-R          | _75.92_           | _64.83_           | 85.36             | __85.32__         | 77.86                        |
| GMM-WBT          | 75.31             | 64.26             | __86.71__         | _85.21_           | 77.87                        |
| GMM-DaDiL        | __77.16__         | __66.21__         | _86.15_           | __85.32__         | __78.81__                    |

### Office 31

| Algorithm  | A                 | D                 | W                 | Avg. $\uparrow$ |
|------------|-------------------|-------------------|-------------------|------------------------------|
| ResNet50   | 67.50             | 95.00             | 96.83             | 86.40                        |
| M$^{3}$SDA | 66.75             | 97.00             | 96.83             | 86.86                        |
| LtC-MSDA   | 66.82             | 100.00            | 97.12             | 87.98                        |
| KD3A       | 65.20             | __100.0__    | 98.70             | 87.96                        |
| Co-MDA     | 64.80             | _99.83_ | 98.70             | 87.83                        |
| WJDOT      | 67.77             | 97.32             | 95.32             | 86.80                        |
| WBT        | 67.94             | 98.21             | 97.66             | 87.93                        |
| DaDiL-E    | 70.55             | __100.0__   | _98.83_ | 89.79                        |
| DaDiL-R    | _70.90_ | __100.0__   | _98.83_ | __89.91__               |
| GMM-WBT    | 70.13             | 99.11             | 96.49             | 88.54                        |
| GMM-DaDiL  | __72.47__    | __100.0__    | __99.41__    | __90.63__               |

### CWRU


| Algorithm          | A               | B               | C                           | Avg. $\uparrow$ |
|--------------------|------------------------------|------------------------------|------------------------------------------|------------------------------|
| MLP$^{\star}$      | 70.90 $\pm$ 0.40             | 79.76 $\pm$ 0.11             | 72.26 $\pm$ 0.23                         | 74.31                        |
| M3SDA              | 56.86 $\pm$ 7.31             | 69.81 $\pm$ 0.36             | 61.06 $\pm$ 6.35                         | 62.57                        |
| LTC-MSDA$^{\star}$ | 82.21 $\pm$ 8.03             | 75.33 $\pm$ 5.91             | 81.04 $\pm$ 5.45                         | 79.52                        |
| KD3A               | 81.02 $\pm$ 2.92             | 78.04 $\pm$ 4.05             | 74.64 $\pm$ 5.65                         | 77.90                        |
| Co-MDA             | 62.66 $\pm$ 0.96             | 55.78 $\pm$ 0.85             | 76.35 $\pm$ 0.79                         | 64.93                        |
| WJDOT              | 99.96 $\pm$ 0.02             | 98.86 $\pm$ 0.55             | __100.0 $\pm$ 0.00__               | 99.60                        |
| WBT$^{\star}$      | 99.28 $\pm$ 0.18             | 79.91 $\pm$ 0.04             | 97.71 $\pm$ 0.76                         | 92.30                        |
| DaDiL-R$^{\star}$  | __99.86 $\pm$ 0.21__ | __99.85 $\pm$ 0.08__ | __100.00 $\pm$ 0.00__     | _99.90_            |
| DaDiL-E$^{\star}$  | 93.71 $\pm$ 6.50             | 83.63 $\pm$ 4.98             | _99.97 $\pm$ 0.05_ | 92.33                        |
| GMM-WBT            | __100.00 $\pm$ 0.00__   | __99.95 $\pm$ 0.07__    | __100.00 $\pm$ 0.00__               | __99.98__               |
| GMM-DaDiL          | __100.00 $\pm$ 0.00__   | __99.95 $\pm$ 0.04__    | __100.00 $\pm$ 0.00__               | __99.98__               |

### TEP

| Algorithm           | Mode 1          | Mode 2          | Mode 3          | Mode 4          | Mode 5          | Mode 6          | Avg. $\uparrow$ |
|---------------------|------------------------------|------------------------------|------------------------------|------------------------------|------------------------------|------------------------------|------------------------------|
| CNN$^{\dag}$        | 80.82 $\pm$ 0.96             | 63.69 $\pm$ 1.71             | 87.47 $\pm$ 0.99             | 79.96 $\pm$ 1.07             | 74.44 $\pm$ 1.52             | 84.53 $\pm$ 1.12             | 78.48                        |
| M$^{3}$SDA$^{\dag}$ | 81.17 $\pm$ 2.00             | 61.61 $\pm$ 2.71             | 79.99 $\pm$ 2.71             | 79.12 $\pm$ 2.41             | 75.16 $\pm$ 3.01             | 78.91 $\pm$ 3.24             | 75.99                        |
| LtC-MSDA$^{1}$    | -                            | -                            | -                            | -                            | -                            | -                            | -                            |
| KD3A                | 72.52 $\pm$ 3.04             | 18.96 $\pm$ 4.54             | 81.02 $\pm$ 2.40             | 74.42 $\pm$ 1.60             | 67.18 $\pm$ 2.37             | 78.22 $\pm$ 2.14             | 65.38                        |
| Co-MDA              | 64.56 $\pm$ 0.62             | 35.99 $\pm$ 1.21             | 79.66 $\pm$ 1.36             | 72.06 $\pm$ 1.66             | 66.33 $\pm$ 0.97             | 78.91 $\pm$ 1.87             | 66.34                        |
| WJDOT               | 89.06 $\pm$ 1.34             | 75.60 $\pm$ 1.84             | __89.99 $\pm$ 0.86__    | _89.38 $\pm$ 0.77_ | 85.32 $\pm$ 1.29             | 87.43 $\pm$ 1.23             | 86.13                        |
| WBT$^{\dag}$        | __92.38 $\pm$ 0.66__    | 73.74 $\pm$ 1.07             | 88.89 $\pm$ 0.85             | _89.38 $\pm$ 1.26_ | 85.53 $\pm$ 1.35             | 86.60 $\pm$ 1.63             | 86.09                        |
| DaDiL-R$^{\ddag}$   | 91.97 $\pm$ 1.22             | __77.15 $\pm$ 1.32__    | 85.41 $\pm$ 1.69             | __89.39 $\pm$ 1.03__    | 84.49 $\pm$ 1.95             | __88.44 $\pm$ 1.29__    | _86.14_            |
| DaDiL-E$^{\ddag}$   | 90.45 $\pm$ 1.02             | _77.08 $\pm$ 1.21_ | 86.79 $\pm$ 2.14             | 89.01 $\pm$ 1.35             | 84.04 $\pm$ 3.16             | 87.85 $\pm$ 1.06             | 85.87                        |
| GMM-WBT             | _92.23 $\pm$ 0.70_ | 71.81 $\pm$ 1.78             | 84.72 $\pm$ 1.92             | 89.28 $\pm$ 1.55             | __87.51 $\pm$ 1.73__    | 82.49 $\pm$ 1.81             | 84.67                        |
| GMM-DaDiL           | 91.72 $\pm$ 1.41             | 76.41 $\pm$ 1.89             | _89.68 $\pm$ 1.49_ | 89.18 $\pm$ 1.17             | _86.05 $\pm$ 1.46_ | _88.02 $\pm$ 1.12_ | __86.85__               |

## Citation

```
@article{montesuma2024lighter,
  title={Lighter, Better, Faster Multi-Source Domain Adaptation with Gaussian Mixture Models and Optimal Transport},
  author={Montesuma, Eduardo Fernandes and Mboula, Fred Ngol{\`e} and Souloumiac, Antoine},
  journal={arXiv preprint arXiv:2404.10261},
  year={2024}
}
```