---
title: "类吸血鬼幸存者"
excerpt: "基于C++和DX11开发的类吸血鬼幸存者游戏。<br/><img src='/images/portfolio/survivor.png'>"
collection: portfolio
---

![survivor]({{ "/images/portfolio/survivor.png" | relative_url }})

### 我做了什么
- **虚拟相机跟随**：相机跟随玩家，屏幕外刷怪，难度随时间提升
- **4 类敌人**：（含远程静止射击）：最近敌人自动攻击 + **对高血量前 N 名 AOE**
- **碰撞系统**：圆/矩形重叠与推离；仅处理视野内对象
- **瓦片地图**：读取 `tiles.txt`；支持无限平铺与固定边界两版
- **存档/读档**：关闭/死亡/ESC 自动保存恢复
- **对象池与容器**：`EnemyPool/BulletPool`；指针vector `myVector<T*>`（原地指针交换、低拷贝）

### 工程与算法亮点
- **自研容器与对象池**： Vec2 与 指针数组实现的 myVector（T** Data），无 STL；acquire()/erase() 支持快速取用/回收，operator[] 返回 T*& 以便原地交换指针，减少拷贝与移动开销。用来实现EnemyPool/BulletPool 对象池，包含活跃/未激活列表管理，减少频繁构造/析构。
- **堆与选择算法**：使用 小顶堆（min-heap） 在 O(M log N) 时间内选出 血量最高的 N 个敌人用于 AOE。
- **性能细节**：距离比较使用 distance² 避免 sqrt开方；瓦片与实体视野裁剪；绘制/碰撞只处理视野内对象。

<div style="max-width:960px;margin:16px auto">
  <video
    controls
    playsinline
    preload="metadata"
    style="width:100%;height:auto"
    poster='{{ "/images/portfolio/survivor.png" | relative_url }}'>
    <source src='{{ "/video/survivor.mp4" | relative_url }}' type="video/mp4">
    Your browser does not support HTML5 video.
  </video>
  <p style="text-align:right;margin:.25rem 0 0">
    <a href='{{ "/video/survivor.mp4" | relative_url }}'>下载/单独打开 MP4</a>
  </p>
</div>


github链接：https://github.com/fengchenxue/PFA_Game