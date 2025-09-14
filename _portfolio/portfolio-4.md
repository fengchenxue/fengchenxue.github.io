---
title: "图形学渲染"
excerpt: "用C++和DX11实现基础光线追踪。<br/><img src='/images/portfolio/MaterialScene_Denoiser.png'>"
collection: portfolio
---

###关键技术

**加速结构**：自建 BVH；场景三角形统一存入 BVH 节点结构。 
**并行化**：分块（tile）多线程渲染，队列派发任务，主线程统一收敛与显示。 
**自适应采样**：从“按 tile 判收敛”改为像素级收敛，仅当 tile 内所有像素都收敛才停止该 tile 的采样。 
**去噪**：集成 Intel OIDN
**环境光照**：经 Distribution2D 重要性采样的经纬度环境贴图
**MIS**：多重重要性采样，结合“光源采样 + BSDF 采样”

![Diffuse_NoDenoiser]({{ "/images/portfolio/Diffuse_NoDenoiser.png" | relative_url }})
![Glass_NoDenoiser]({{ "/images/portfolio/Glass_NoDenoiser.png" | relative_url }})
![MaterialScene_Denoiser]({{ "/images/portfolio/MaterialScene_Denoiser.png" | relative_url }})
