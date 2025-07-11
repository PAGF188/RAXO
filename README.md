<div align="center">

<h1> <a style="color:white; font-weight:bold;" href="https://pagf188.github.io/RAXO/">Superpowering Open-Vocabulary Object Detectors for X-ray Vision</a></h1>
<h2>ICCV 25</h2>

[Pablo Garcia-Fernandez](https://scholar.google.es/citations?user=xbtLSCcAAAAJ&hl=es),
[Lorenzo Vaquero](https://scholar.google.es/citations?user=G0ZcGDYAAAAJ&hl=es&oi=sra),
[Mingxuan Liu](https://scholar.google.com/citations?user=egL5-LsAAAAJ&hl=en),
[Feng Xue](https://scholar.google.com/citations?user=66SeiQsAAAAJ&hl=zh-CN),
[Daniel Cores](https://scholar.google.com/citations?user=pJqkUWgAAAAJ&hl=es)
[Nicu Sebe](https://scholar.google.com/citations?user=stFCYOAAAAAJ&hl=en)
[Manuel Mucientes](https://scholar.google.com/citations?user=raiz6p4AAAAJ)
[Elisa Ricci](https://scholar.google.com/citations?user=xf1T870AAAAJ&hl=en)


[![arXiv](https://img.shields.io/badge/cs.CV-2410.07752-b31b1b?logo=arxiv&logoColor=red)](https://arxiv.org/abs/2503.17071)
[![GitHub](https://img.shields.io/badge/GitHub-RAXO-blue?logo=github)](https://github.com/PAGF188/RAXO)
[![Static Badge](https://img.shields.io/badge/website-RAXO-8A2BE2)](https://pagf188.github.io/RAXO/)
[![Static Badge](https://img.shields.io/badge/DET-COMPASS-8A2BE2)](https://huggingface.co/datasets/PAGF/DET-COMPASS)
</div>

## 📚 Abstract

<div align="center">
  <img src="./assets/teaser.png" alt="Teaser" style="width: 500px; height: auto;">
</div>

Open-vocabulary object detection (OvOD) is set to revolutionize security screening by enabling systems to recognize any item in X-ray scans.
However, developing effective OvOD models for X-ray imaging presents unique challenges due to data scarcity and the modality gap that prevents direct adoption of RGB-based solutions.
To overcome these limitations, we propose **RAXO**, a training-free framework that repurposes off-the-shelf RGB OvOD detectors for robust X-ray detection.
RAXO builds high-quality X-ray class descriptors using a dual-source retrieval strategy.
It gathers relevant RGB images from the web and enriches them via a novel X-ray material transfer mechanism, eliminating the need for labeled databases.
These visual descriptors replace text-based classification in OvOD, leveraging intra-modal feature distances for robust detection.
Extensive experiments demonstrate that RAXO consistently improves OvOD performance, providing an average mAP increase of up to 17.0 points over base detectors.
To further support research in this emerging field, we also introduce DET-COMPASS, a new benchmark featuring bounding box annotations for over 300 object categories, enabling large-scale evaluation of OvOD in X-ray.
Code and dataset will be made available.


## Release
- Our proposed X-ray/RGB [**DET-COMPASS**](https://huggingface.co/datasets/PAGF/DET-COMPASS) dataset is now available.
- The precomputed visual descriptors (both in-house and web), along with the initial detections from the detectors (G-DINO, VLDet, Detic, and CoDET), are available [**here**](https://nubeusc-my.sharepoint.com/:f:/g/personal/pablogarcia_fernandez_usc_es/EmSHyj8g6LlHhpHVLCdd67sBwumUlchoCoJS_vH69jtJ1w?e=MhS3Ex).
- The dataset’s test annotations in COCO format are available [**here**](https://nubeusc-my.sharepoint.com/:f:/g/personal/pablogarcia_fernandez_usc_es/EmSHyj8g6LlHhpHVLCdd67sBwumUlchoCoJS_vH69jtJ1w?e=MhS3Ex)


## Set-up

1. Clone this repository
```bash
git clone https://github.com/PAGF188/RAXO
```
2. We use Docker Hub to share the environment. You can find the images [**here**](https://hub.docker.com/repository/docker/pagf18/dinov2/tags/iccv25_v2/sha256-a8330f054b23275611b2c92822bd11d4937695bdddf77fca378d9febe1188368).
3. You need to download the 6 datasets. Some of them are not in COCO format. For ease of use, we provide the COCO-format annotations for the test split [**here**](https://nubeusc-my.sharepoint.com/:f:/g/personal/pablogarcia_fernandez_usc_es/EmSHyj8g6LlHhpHVLCdd67sBwumUlchoCoJS_vH69jtJ1w?e=MhS3Ex).
   - [**PIXray**](https://github.com/Mbwslib/DDoAS)
   - [**PIDray**](https://github.com/bywang2018/security-dataset)
   - [**CLCXray**](https://github.com/GreysonPhoenix/CLCXray)
   - [**DvXray**](https://ieeexplore.ieee.org/document/10458082)
   - [**HiXray**](https://github.com/DIG-Beihang/XrayDetection)
   - [**DET-COMPASS**](https://huggingface.co/datasets/PAGF/DET-COMPASS)
4. You need to download the 4 detectors and obtain the initial set of proposals. **IMPORTANT: For ease of use, we directly share these initial detections [**here**](https://nubeusc-my.sharepoint.com/:f:/g/personal/pablogarcia_fernandez_usc_es/EmSHyj8g6LlHhpHVLCdd67sBwumUlchoCoJS_vH69jtJ1w?e=MhS3Ex).**
    - [**G-DINO**](https://github.com/open-mmlab/mmdetection)
    - [**VLDet**](https://github.com/clin1223/VLDet)
    - [**Detic**](https://github.com/facebookresearch/Detic)
    - [**CoDet**](https://github.com/CVMI-Lab/CoDet)

## Inference with precomputed descriptors
To simplify execution, we provide precomputed visual descriptors for both the in-house and web-retrieval components. You can download them [**here**](https://nubeusc-my.sharepoint.com/:f:/g/personal/pablogarcia_fernandez_usc_es/EmSHyj8g6LlHhpHVLCdd67sBwumUlchoCoJS_vH69jtJ1w?e=MhS3Ex).

### Running the Method (100/0 Setting)

To run the classification using only in-house descriptors (i.e., the 100/0 setting), execute the following script:
```bash
bash run_method_database_branch_v2.sh
```
Before running the script, make sure to update the following variables to match your local paths:
```bash
RESULTS_PATH=/models/ICCV25_experimentation/
DATASET_PATH="/datasets/xray-datasets/"
```
Additionally, update line 74 in the script to point to the correct path for the in-house descriptors:
```bash
--prototypes /models/ICCV25_experimentation/known_prototypes_sam2.pt \
```

### Running the Method (0/100 Setting)
To run the classification using only web descriptors (i.e., the 0/100 setting), execute the following script:
```bash
bash run_method_web_branch_v2.sh
```
Before running the script, make sure to also update the variables to match your local paths.  
Additionally, this script includes a function that computes all intermediate settings (80/20, 50/50, 20/80), provided that the results for 100/0 and 0/100 have already been generated:

```bash
bash python raxo/final_cocoapi.py
```

## Computing Visual Descriptors

### In-house descriptors
To obtain the in-house descriptors, check **Step 2** in the `run_method_database_branch_v2.sh` script.  
We release [**here**](https://nubeusc-my.sharepoint.com/:f:/g/personal/pablogarcia_fernandez_usc_es/EmSHyj8g6LlHhpHVLCdd67sBwumUlchoCoJS_vH69jtJ1w?e=MhS3Ex) the images used to build these descriptors by combining the six datasets, along with their COCO-format annotations.

### Web descriptors
To obtain the in-house descriptors, check **Step 1** in the `run_method_web_branch_v2.sh` script.

**Critical**: You will need a configured Google Custom Search API to retrieve the images, and a GPT-4 API key to run the material-transfer.


## Citation

If you find RAXO useful for your research and applications, please cite using this BibTeX:
```bibtex

@inproceedings{garcia2025superpowering,
      title={Superpowering Open-Vocabulary Object Detectors for X-ray Vision}, 
      author={Garcia-Fernandez, Pablo and Vaquero, Lorenzo and Liu, Mingxuan and Xue, Feng and Cores, Daniel and Sebe, Nicu and Mucientes, Manuel and Ricci, Elisa},
      booktitle={ICCV},
      year={2025},
}
```


