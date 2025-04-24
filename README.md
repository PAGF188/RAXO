# RAXO

This is the official repository of [**Superpowering Open-Vocabulary Object Detectors for X-ray Vision**](https://arxiv.org/abs/2503.17071).

We propose **RAXO**, a training-free method that seamlessly adapts RGB OvOD models to X-ray

<div align="center">
  <img src="./assets/teaser.png" alt="Teaser">
</div>


## 📚 Abstract

Open-vocabulary object detection (OvOD) is set to revolutionize security screening by enabling systems to recognize any item in X-ray scans.
However, developing effective OvOD models for X-ray imaging presents unique challenges due to data scarcity and the modality gap that prevents direct adoption of RGB-based solutions.
To overcome these limitations, we propose **RAXO**, a training-free framework that repurposes off-the-shelf RGB OvOD detectors for robust X-ray detection.
RAXO builds high-quality X-ray class descriptors using a dual-source retrieval strategy.
It gathers relevant RGB images from the web and enriches them via a novel X-ray material transfer mechanism, eliminating the need for labeled databases.
These visual descriptors replace text-based classification in OvOD, leveraging intra-modal feature distances for robust detection.
Extensive experiments demonstrate that RAXO consistently improves OvOD performance, providing an average mAP increase of up to 17.0 points over base detectors.
To further support research in this emerging field, we also introduce DET-COMPASS, a new benchmark featuring bounding box annotations for over 300 object categories, enabling large-scale evaluation of OvOD in X-ray.
Code and dataset will be made available.
