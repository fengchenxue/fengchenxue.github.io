---
title: "UE5太空球（Zorbing)游戏"
excerpt: "基于UE5开发的太空球Demo,实现了基于物理的移动，场景破坏以及metahuman的应用。<br/><img src='/images/portfolio/chaoseffect.png'>"
collection: portfolio
---

3C（角色/相机/操控）：SpringArm+CameraLag 平滑视角；外层透明球+内层球材质；基于力矩的物理滚动，Physical Material 反复标定（摩擦/弹性），完成输入到运动链路。


玩法流程：在 GameMode / GameState / HUD / GameInstance 中集中管理关卡开始/结束、计时与消息流；实现 Checkpoint/Endpoint 触发。


Chaos 可破坏：Fracture → Geometry Collection → 蓝图粒子与定时回收，完成可演示的破坏区域与实机展示。


MetaHuman：从照片到 MetaHuman Creator，导入项目、设置 Leader Pose、驱动动画并在关卡起点/终点配置演出。


关卡改造：森林图程序化植被参数优化（密度/类型）、小型树木与原木取消碰撞；地形坡度调整；可破坏物补可玩性。


![fractureMode]({{ "/images/portfolio/fractureMode.png" | relative_url }})
![chaoseffect]({{ "/images/portfolio/chaoseffect.png" | relative_url }})
![metahuman]({{ "/images/portfolio/metahuman.png" | relative_url }})
![metahumandancing]({{ "/images/portfolio/metahumandancing.png" | relative_url }})

<div style="max-width:960px;margin:16px auto">
  <video
    controls
    playsinline
    preload="metadata"
    style="width:100%;height:auto"
    poster='{{ "/images/portfolio/chaoseffect.png" | relative_url }}'>
    <source src='{{ "/video/Zorbing.mp4" | relative_url }}' type="video/mp4">
    Your browser does not support HTML5 video.
  </video>
  <p style="text-align:right;margin:.25rem 0 0">
    <a href='{{ "/video/Zorbing.mp4" | relative_url }}'>下载/单独打开 MP4</a>
  </p>
</div>
