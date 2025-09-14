---
title: "小型聊天室"
excerpt: "使用 WinSock + ImGui 实现带公网服务器的聊天室（广播/私聊/心跳/提示音）。<br/><img src='/images/portfolio/public_chat.png'>"
collection: portfolio
---

- **客户端/服务器**：多并发连接、消息路由、优雅上线/下线，公共频道 + 私聊窗口。
- **身份体系**：每客户端生成 UUID（id.txt），用于唯一标识与私聊会话关联；昵称可编辑并广播变更。
- **在线状态**：心跳机制（客户端 30s 发送 ping；服务器 60s 清理不活跃连接）。
- **提示音**：普通消息 / 私信使用不同音效；离线用户不缓存历史（设计取舍）。
- **公网部署**：租用阿里云 2C2G 服务器跑服务端；额外写 monitor.bat 守护进程异常退出。


![public_chat]({{ "/images/portfolio/public_chat.png" | relative_url }})


![chat]({{ "/images/portfolio/chat.png" | relative_url }})


![connection_workflow]({{ "/images/portfolio/connection_workflow.png" | relative_url }})


![disconnection_workflow]({{ "/images/portfolio/disconnection_workflow.png" | relative_url }})


![heaerbeat_dection_workflow]({{ "/images/portfolio/heaerbeat_dection_workflow.png" | relative_url }})


![messgae_workflow]({{ "/images/portfolio/messgae_workflow.png" | relative_url }})


Github(客户端): https://github.com/fengchenxue/GamesEngineering_Network_Client


Github(服务器)：https://github.com/fengchenxue/GamesEngineering_Network_Server