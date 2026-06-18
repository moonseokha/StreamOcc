<div align="center">

# StreamOcc

## Streaming Dense Voxel Representations for 3D Occupancy Prediction

[**Seokha Moon**](https://moonseokha.github.io)<sup>1,5,†</sup> ·
[**Janghyun Baek**](https://scholar.google.com/citations?user=UJR1YYQAAAAJ&hl=en)<sup>1</sup> ·
[**Yujin Jeong**](https://eugene6923.github.io/)<sup>2</sup> ·
[**Daewon Chae**](https://daewon88.github.io/)<sup>3</sup> ·
[**Giseop Kim**](https://gisbi-kim.github.io/)<sup>4,5,‡</sup> ·
[**Jungbeom Lee**](https://visionai.korea.ac.kr/)<sup>1</sup> ·
[**Jinkyu Kim**](https://visionai.korea.ac.kr/team/jinkyu_kim)<sup>1,&ast;</sup> ·
[**Sunwook Choi**](https://scholar.google.com/citations?user=R3W7dTsAAAAJ&hl=en)<sup>5,&ast;</sup>

<sup>1</sup>Korea University ·
<sup>2</sup>TU Darmstadt & hessian.AI ·
<sup>3</sup>University of Michigan ·
<sup>4</sup>DGIST ·
<sup>5</sup>NAVER LABS

<sup>†</sup>Work done during an internship at NAVER LABS ·
<sup>‡</sup>Work done while at NAVER LABS

<sup>&ast;</sup> Corresponding authors

[![Project Page](https://img.shields.io/badge/Project-Page-2f9e67)](https://moonseokha.github.io/StreamOcc/)
[![ECCV 2026](https://img.shields.io/badge/ECCV-2026-3b82f6)](https://eccv.ecva.net/)
[![arXiv](https://img.shields.io/badge/arXiv-2503.22087-b31b1b)](https://arxiv.org/abs/2503.22087)

</div>

## 🚀 News
- **2026.06.18** — StreamOcc has been accepted to **ECCV 2026**.
- **2025.11.29** — Code released.
- **2025.11.27** — StreamOcc paper has been updated on **[arXiv](https://arxiv.org/abs/2503.22087)**.

## ✨ Highlights
- **StreamOcc** introduces a **dual aggregation strategy** combining *Stream-based Voxel Feature Aggregation (StreamAgg)* and *Query-guided Feature Aggregation (QueryAgg)* for efficient and high-fidelity 3D occupancy prediction.
- Achieves **state-of-the-art performance**:
  - **Occ3D-nuScenes**: 41.9 mIoU (**+2.3** over prior SOTA / in real-time setting)
  - **SurroundOcc dataset**: 23.0 mIoU (**+1.1** over prior SOTA)
- Runs within real-time constraints (**83 ms**) and requires only **2.8 GB** of GPU memory — **over 40% less memory** than competing approaches.


## 💡 Method
![Method](./assets/overview.png)

StreamOcc is composed of two complementary components:

### Stream-based Voxel Feature Aggregation (StreamAgg)
- Aligns and aggregates voxel features over time using motion-aware warping.
- Reduces warping artifacts via a lightweight refinement module (RefineNet).
- Preserves spatially coherent geometry and is particularly effective for static structures, whose positions remain stable after ego-motion compensation—making them inherently suitable for stream-based accumulation.
### Query-guided Feature Aggregation (QueryAgg)
- Extracts semantics of dynamic objects from image features and encodes them into propagated instance queries.
- Injects these instance-level query features into the corresponding voxel regions.
- Complements fine-grained dynamic object details that are difficult to capture through voxel accumulation alone due to motion-induced misalignment, occlusion, or sparse projection.

**StreamAgg and QueryAgg jointly produce a fast, memory-efficient, and high-fidelity 3D occupancy representation.**

## 🎨 Qualitative Results

<p align="center">
  <img src="./assets/qualitative.png" width="98%">
</p>

StreamOcc provides clearer and more consistent 3D occupancy predictions, significantly improving reconstruction of both dynamic objects and fine-grained static structures compared to prior methods.

## 📊 Quantitative Results
<p align="center">
  <img src="./assets/occ3d.png" width="48%">
  <img src="./assets/surroundocc.png" width="48%">
</p>

StreamOcc achieves state-of-the-art performance on Occ3D-nuScenes (**41.9 mIoU**) and SurroundOcc Dataset(**23.0 mIoU**), while running at **83 ms** and using only **2.8 GB** of memory, making it one of the most efficient high-performing occupancy prediction models available. These results highlight StreamOcc’s strong balance of **accuracy, speed, and memory efficiency**, making it highly suitable for real-world autonomous driving.

## 🔧 Getting Started
**Step 1.** Set up the environment:  
➡️ [`Install`](docs/install.md)

**Step 2.** Prepare datasets and PKL files:  
➡️ [`Prepare Data`](docs/prepare_data.md)

## 🏋️ Training & Inference

```bash
# Train
bash local_train.sh StreamOcc
# Test
bash local_test.sh StreamOcc path/to/checkpoint
```

## 🙏 Acknowledgement
This project is not possible without multiple great open-sourced code bases. We list some notable examples below.
- [open-mmlab](https://github.com/open-mmlab)
- [Occ3D](https://github.com/Tsinghua-MARS-Lab/Occ3D)
- [BEVDet](https://github.com/HuangJunJie2017/BEVDet)
- [SurroundOcc](https://github.com/weiyithu/SurroundOcc)
- [FB-OCC](https://github.com/NVlabs/FB-BEV)
- [Sparse4D](https://github.com/HorizonRobotics/Sparse4D)


## 📃 Bibtex
If this work is helpful for your research, please consider citing the following BibTeX entry.
```
@article{moon2025streamocc,
  title={Streaming Dense Voxel Representations for 3D Occupancy Prediction},
  author={Moon, Seokha and Baek, Janghyun and Jeong, Yujin and Chae, Daewon and Kim, Giseop and Lee, Jungbeom and Kim, Jinkyu and Choi, Sunwook},
  journal={arXiv preprint arXiv:2503.22087},
  year={2025}
}
```
