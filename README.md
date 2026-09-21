# PSVA-Net

## From Part Semantics to Discriminative Visual Representations: Fine-Grained Aircraft Recognition in Remote Sensing Images via Adaptive Part-Semantic Alignment and Category-Conditioned Fusion

## Overview

Fine-grained aircraft recognition in remote sensing imagery is challenging because aircraft targets are often small, different aircraft types can have highly similar silhouettes, and changes in pose or imaging viewpoint can produce substantial intra-class variation.

PSVA-Net (**Part Semantic-Guided Visual Alignment Network**) addresses these challenges by jointly modeling multi-scale visual representations and structured aircraft knowledge. It establishes fine-grained correspondences between visual regions and part-level semantics, adapts semantic prototypes to the remote sensing domain, and dynamically controls the contribution of semantic evidence to the final prediction.

## Highlights

- **Hybrid visual encoding:** combines ConvNeXt and Swin Transformer features to capture local details and global structural relationships.
- **Structured part-semantic knowledge:** represents aircraft categories using both global descriptions and part-level attributes.
- **Adaptive semantic prototypes:** improves task adaptability while preserving the structure of the original semantic knowledge.
- **Part-semantic-guided visual alignment:** associates domain-specific part semantics with relevant local visual regions.
- **Category-conditioned fusion:** dynamically adjusts the contribution of part-level evidence for each candidate category.

## Experimental Results

PSVA-Net was evaluated on the FAIR1M and MAR20 fine-grained aircraft recognition benchmarks. It achieved:

| Dataset | Top-1 Accuracy | Macro-F1 |
|:--|--:|--:|
| FAIR1M | 49.18% | 43.70% |
| MAR20 | 88.12% | 86.18% |

The results demonstrate the effectiveness and cross-dataset robustness of combining structured semantic knowledge with fine-grained visual-region alignment.

## Code Availability

The project code associated with this paper will be made available as soon as possible.
