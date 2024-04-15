---
title: 帮助信息
layout: page
---

### 运行方法

1. 下载压缩包并解压。
2. 配置 AI 模型：

   1. 使用本地(Local)模型，需要获取 Mortal 模型文件 （pth 文件），放到 'models' 目录中。本项目使用兼容 Akagi 的模型文件，获取模型请参见<a href="https://github.com/shinkuan/Akagi" target="_blank"> Akagi Github </a> 或者
   2. 使用在线模型（MJAPI 支持自动注册）
4. 运行 MahjongCopilot，点击雀魂按钮，在内置浏览器中启动雀魂客户端。

### 使用帮助：

1. 软件使用中间人 (MITM) 代理获取游戏客户端和服务器之间传输的信息。推荐使用内置的浏览器进行游戏。
   
   1. “上游代理”选项：如果你需要通过代理服务器连接雀魂服务器，可在此填写代理服务器的地址（如：```http://1.2.3.4:5555```）
   2. 打开浏览器时，显示“不安全”，无法连接雀魂服务器时，可能是由于没有管理员权限运行程序导致 MITM 的证书安装失败。可以到 mitm_config 目录下，手动安装扩展名 cer 的证书至“根证书”目录。
   3. 首次加载网页客户端，或游戏有更新时，会因为下载游戏素材而导致网页加载时间变长或疑似卡住。
   4. 如果需要使用其他客户端，可以用代理软件 (如 Proxifier) 使客户端流量通过代理```http://localhost:{mitm端口}```访问。其他客户端暂不支持自动打牌。
2. 界面和设置项说明：
   
   1. 网页 HUD 开关: 在网页上覆盖显示信息和 AI 选项。关闭此项可略微提升自动打牌流畅度。
   2. AI 模型类型：可选择不同的模型，分别支持不同的麻将模式（三麻、四麻）
      
      - Local: 兼容 Akagi 的本地 Mortal 模型，支持三麻和四麻。需要获取模型文件(.pth文件)放到 models 目录下；三麻和四麻模型需要分别获取各自的模型文件。三麻模型，还需要额外下载libriichi3p相关文件库文件（pyd文件），放到libriichi3p目录下。模型支持的游戏类型会显示在状态栏，模型后的方括号内。详情请参见 Akagi Discord 中的说明。
      - MJAPI: (作者 9ns4esyx) 开发的在线麻将 AI API. 使用 MJAPI 时，可以填写已有的用户名和密钥。或者，将用户名和密钥 (Secret) 留空，软件会自动注册新用户并登录。MJAPI 有不同模型可选择，登陆后会刷新模型选项，并显示 API 用量。4月13日更新的 MJAPI 地址：（临时域名有总连接数限制，而且不保证长久有效，之后也可能会变。）
        临时域名：`https://cdt-authentication-consultation-significance.trycloudflare.com`
        稳定域名：`https://mjai.7xcnnw11phu.eu.org`
   3. 自动打牌设置：
      
      - 自动打牌：自动化操作的总开关，关闭后将停止所有自动化操作。
      - 鼠标移动随机化：鼠标点击前，随机移动几次，避免被检测为自动化操作。还有概率以鼠标拖拽出牌。
      - 鼠标空闲移动：鼠标空闲时（比如他人回合）一定概率随机移动。
      - 鼠标拖拽出牌：使用鼠标拖动代替点击来出牌。
      - AI选项随机化（去重）：自动打牌时，根据模型推荐的前三选项，按概率（权重）随机选取其中之一。可以在分析牌谱时，降低模型重合率。0 为关闭（仅选择权重最高项），5 为最高（按概率权重选择），1-4 的随机性位于中间。计算方式：取原概率的(5/n)次方，再归一概率，按概率选择。
      - 基础延迟随机范围：自动打牌前的延迟。根据场况和打的牌，会在基础延迟上增加额外延迟（例如：东家第一巡会加几秒钟延迟，让理牌动画完成）。
      - 自动加入：自动加入下一局游戏，根据选择的级别和游戏模式。自动加入操作需要从主菜单或者游戏中开始。
3. 状态栏中，主程序和浏览器均会附加显示刷新率作为性能参考。通常数值在 100 以上说明程序运行流畅。进行自动打牌操作时，浏览器刷新率会下降。
4. 在帮助窗口中，可以进行自动更新（暂时支持 Windows）。Mac 用户需要自助从 Python 源代码运行本程序。
5. 长时间使用自动打牌可能会导致账户被封禁。关闭自动打牌和 HUD 显示功能可以减少账号封禁风险。请合法使用本程序。使用者需要承担潜在风险和责任。

## 鸣谢 / Credit

- 基于 Mortal 模型和 MJAI 协议:
  <a href="https://github.com/Equim-chan/Mortal" target="_blank"> Mortal Github </a>

- 设计和功能实现基于 Akagi:
  <a href="https://github.com/shinkuan/Akagi" target="_blank"> Akagi Github </a>
- 参考项目: <a href="https://github.com/MahjongRepository/mahjong_soul_api" target="_blank"> Mahjong Soul API </a>

- MJAI协议参考:
  <a href="https://mjai.app" target="_blank"> mjai.app </a>