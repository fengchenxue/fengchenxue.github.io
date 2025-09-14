---
title: "基于机器学习的分线段线性NDF的G1加速计算（硕士毕设）"
excerpt: "对于最新的分线段NDF，使用神经网络来预测Microfacet模型中的G1部分，来加速其计算，并于传统方案和查表法作比较。<br/><img src='/images/portfolio/HEAD_HeadZ64_256x128x64_relu_do0.00_s4_i7185.png'>"
collection: portfolio
---

### 背景
“Microfacet BSDFs Generated from NDFs and Explicit Microgeometry”这篇论文，提出了一种分线段表示NDF的方法，
这相比传统的Beckmann和GGX等方法有更加灵活的表达性。不过这种先进的研究并没有落地到实际游戏引擎中，原因在于其计算代价较大，无法应用在实时渲染中。
我经过一段时间研究，发现两个可以改进的点，一个是G1项，一个是多次散射补偿L2+的压缩。

### 方案
最终本研究聚焦于G1项的加速计算，对三种方案的性能与精度进行对比：1）传统计算 2）神经网络 3）LUT查表。
其中神经网络部分，包括FCNN、CNN及多种变体、Encoder-head。

### 结果
下图是一些神经网络的预测结果示例。
![Encoder-Head1 结果]({{ "/images/portfolio/FULL_Encoder_0_s1_i7185.png" | relative_url }})
![Encoder-Head2 结果]({{ "/images/portfolio/FULL_Encoder_1_s3_i7185.png" | relative_url }})
![Encoder-Head3 结果]({{ "/images/portfolio/HEAD_HeadZ64_256x128x64_relu_do0.00_s4_i7185.png" | relative_url }})

虽然在大批量预测时，神经网络优于传统计算，但是在精度和速度上还是比不过查表法。
但是Encoder-head类神经网络的预烘焙速度却比LUT查表法快，所以神经网络有自己的独特优势领域，那就是开发过程。
开发时，开发者需要频繁调整材质属性，此时如果用查表法烘焙G1，有一点慢，而神经网络Encoder则要快的多。
所以神经网络可以用在游戏开发过程，而最终打包时则使用LUT查表法。