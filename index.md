---
layout: default
---

![](assets/images/teaser.png)

## Abstract

Recent advances in full-head reconstruction have been obtained by optimizing a neural field through differentiable surface or volume rendering to represent a single scene. While these techniques achieve an unprecedented accuracy, they take several minutes, or even hours, due to the expensive optimization process required. In this work, we introduce InstantAvatar, a method that recovers full-head avatars from few images (down to just one) in a few seconds on commodity hardware. In order to speed up the reconstruction process, we propose a system that combines, for the first time, a voxel-grid neural field representation with a surface renderer. Notably, a naive combination of these two techniques leads to unstable optimizations that do not converge to valid solutions. In order to overcome this limitation, we present a novel statistical model that learns a prior distribution over 3D head signed distance functions using a voxel-grid based architecture. The use of this prior model, in combination with other design choices, results into a system that achieves 3D head reconstructions with comparable accuracy as the state-of-the-art with a 100x speed-up.

## Method

Combined with some techniques derived from a few key insights, our instant 3D reconstruction pipeline builds on top of [IDR](https://arxiv.org/abs/2003.09852) and [H3D-Net](https://arxiv.org/abs/2107.12512). We find that surface rendering is more computationally efficient than volumetric rendering since its sampling size is considerably smaller. Therefore, we show that using grid-based representations together with this efficient rendering increase the speed of convergence significantly. However, both of these concepts make the optimization process more challenging in terms of stability. In order to diminish these side effects: we employ a statistical shape prior for guiding the optimization first steps through a valid latent space; using progressive key schedules to make proper usage of each level-of-detail (similar to concurrent work [Neuralangelo](https://arxiv.org/abs/2306.03092/)); and supervising with normal cues for increasing its robustness.

![](assets/images/method.png)

## Results

We next evaluate our 3D reconstruction on multiple real-world portrait photos from the datasets  [H3DS](https://openaccess.thecvf.com/content/ICCV2021/html/Ramon_H3D-Net_Few-Shot_High-Fidelity_3D_Head_Reconstruction_ICCV_2021_paper.html), 3DFAW and CelebA-HQ.

The proposed method outperforms parametric model-based methods like [Feng et al.](https://dl.acm.org/doi/abs/10.1145/3450626.3459936) and [Dib et al.](https://openaccess.thecvf.com/content/ICCV2021/html/Dib_Towards_High_Fidelity_Monocular_Face_Reconstruction_With_Rich_Reflectance_Using_ICCV_2021_paper.html) in 3D face reconstruction from only 1 view, and per scene optimitzation approaches like [H3D-Net](https://openaccess.thecvf.com/content/ICCV2021/html/Ramon_H3D-Net_Few-Shot_High-Fidelity_3D_Head_Reconstruction_ICCV_2021_paper.html) in full head reconstruction.

SIRA recovers the geometry of the head, including hair and shoulders, yielding 3D shapes that clearly retain the identity of the person. Next, we show full head 3D reconstructions from a single input image.

<p align="center">
  <img src="assets/images/comp_3d.png" width="700" />
</p>

<p align="center">
  <img src="assets/images/1 view - 34f084f75deb512f.gif" width="350" />
  <img src="assets/images/3 views - 5d0e87f3adb80226.gif" width="350" />
  <img src="assets/images/6 views - 797a46725454b9c0.gif" width="350" />
</p>

## BibTeX

```latex
@InProceedings{canela2024instantavatar,
  title={InstantAvatar: Efficient 3D Head Reconstruction via Surface Rendering},
  author={Canela, Antonio and Caselles, Pol and Malik, Ibrar and Ramon, Eduard and Garcia, Jaime and Sanchez-Riera, Jordi and Triginer, Gil and Moreno-Noguer, Francesc},
  booktitle = {International Conference on 3D Vision (3DV)},
  year={2024}
}
```
