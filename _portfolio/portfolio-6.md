---
title: "C++优化实践"
excerpt: " C++ 光栅器中实现增量边函数、背面剔除、SIMD 与多线程加速。<br/><img src='/images/portfolio/scene3.png'>"
collection: portfolio
---


### 我做了什么

- **热点定位**：draw() 占 80–88% 运行时 → 重点优化像素级插值与填充。
- **增量边函数**：对三角形 α/β/γ 采用 incremental 迭代替代逐像素重算（核心提速点）。
- **背面剔除**：基于顶点法线与相机方向点积跳过背面三角形。
- **SIMD 向量化**：对 draw() 做 8-像素批处理（即便包含少量本应被剔除的像素，整体仍大幅提速）。
- **多线程**：实现简易线程池 + 基于 Mesh 的任务划分；锁-轻量环形队列派发任务。


### 结果

Scene 1：单线程从 ~5900ms → ~1800ms；多线程至 ~1450ms。


Scene 2：单线程从 ~2200ms → ~600ms；多线程至 ~370ms。

![scene3]({{ "/images/portfolio/scene3.png" | relative_url }})


Github: https://github.com/fengchenxue/GamesEngineering_Part1
