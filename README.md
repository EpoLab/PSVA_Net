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

## Datasets and Data Preparation

The experiments in this work were conducted on the FAIR1M and MAR20 datasets. The original datasets are designed for object detection, whereas this work focuses on fine-grained image classification. We therefore construct classification samples by cropping individual aircraft instances from the original remote sensing images according to the provided target annotations. The cropped aircraft images are then resized to $224 \times 224$ pixels for model training and evaluation.

The original datasets can be obtained from the following official sources:

- **FAIR1M:** [Official benchmark and download page](https://www.gaofen-challenge.com/benchmark)
- **MAR20:** [OneDrive](https://1drv.ms/u/s!AmgKYzARBl5ceGUKiVsRzfxZa_4?e=K21Spg) | [Baidu Netdisk](https://pan.baidu.com/s/1VpQGGoSVTdFCtROVnH4s3A?pwd=wye2) (access code: `wye2`)

Please follow the licenses and terms of use specified by the respective dataset providers.

## Semantic Knowledge Examples

PSVA-Net represents each aircraft category using a category prompt, a global description, and a set of part-level descriptions. The following entries show how the structured semantic knowledge is organized for one representative category from each dataset.

### FAIR1M: A220

```json
{
  "A220": {
    "category_prompt": "a A220 regional jet in an overhead remote sensing image",
    "global_description": "small twin-engine jet regional jet; short and compact narrow fuselage, swept-back wings with moderate wing span for a regional jet, single vertical tail.",
    "part_descriptions": {
      "nose": "Rounded narrow-body nose, positioned at the forward end of the fuselage, with a smooth rounded front contour that transitions into the main fuselage.",
      "fuselage": "Short and compact narrow fuselage, showing compact longitudinal extent in the overhead crop.",
      "wings": "Swept-back wings extending outward and backward from the fuselage, with moderate wing span for a regional jet visible at the aircraft scale.",
      "tail": "Single vertical tail with a simple centered rear silhouette."
    }
  }
}
```

### MAR20: B1B

```json
{
  "B1B": {
    "category_prompt": "a B1B strategic bomber in an overhead remote sensing image",
    "global_description": "large four-engine jet strategic bomber, long streamlined fuselage, variable-sweep wings, single vertical tail.",
    "part_descriptions": {
      "nose": "Long pointed nose with a strong forward direction.",
      "fuselage": "Long streamlined bomber fuselage with a smooth and narrow mid-rear body.",
      "wings": "Variable-sweep wings forming a narrow swept planform when folded backward.",
      "tail": "Single vertical tail with a compact tapered rear outline."
    }
  }
}
```

The complete semantic knowledge bases for FAIR1M and MAR20 will be released together with the project code.

## Experimental Results

PSVA-Net was evaluated on the FAIR1M and MAR20 fine-grained aircraft recognition benchmarks. It achieved:

| Dataset | Top-1 Accuracy | Macro-F1 |
|:--|--:|--:|
| FAIR1M | 49.18% | 43.70% |
| MAR20 | 88.12% | 86.18% |

The results demonstrate the effectiveness and cross-dataset robustness of combining structured semantic knowledge with fine-grained visual-region alignment.

## Code Availability

The project code associated with this paper will be made available as soon as possible.
