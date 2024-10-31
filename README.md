# 1 概述

QNRTCKit 是七牛推出的一款适用于 HarmonyOS 平台的音视频通话 SDK，提供了包括音视频通话、单路推流等多种功能，提供灵活的接口，支持高度定制以及二次开发。

# 2 功能列表

- 支持 pc 重连超时、mcu 获取超时时间 
- 支持 mcu 备用域名设置 
- 支持硬件编码
- 支持重连超时配置 
- 支持视频降级默认值区分场景 
- 支持本地和远端视频 stats 回调宽高信息 
- 支持切换摄像头结果回调 
- 支持设置视频在弱网下的降级模式
- 支持日志文件上传 
- 支持动态修改编码配置
- 支持推流固定分辨率
- 支持获取本地或远端音频数据音量等级 
- 支持视频 SEI  
- 支持单路转推
- 支持使用 TCP 传输媒体流  
- 支持音视频分别发布             
- 支持纯音频连麦                 
- 支持码率上下限配置             
- 支持多分辨率编码                
- 支持静音功能                 
- 支持实时状态回调                
- 支持回调连麦房间统计信息
- 支持丰富的连麦消息回调

# 3 方案介绍
七牛实时音视频云支持低延时音视频通话，提供灵活丰富的接口，方便进行二次开发。该系统主要包括服务端和客户端两个部分，其中，服务端主要提供了房间管理、权限验证、信令和媒体数据转发等功能，客户端则提供了媒体数据的采集、编解码、传输、渲染等功能。

### 3.1 系统框图
![](http://docs.qnsdk.com/qnrtc-overview-architecture.png)

整个系统的架构如上图所示，主要分为三个部分：

- <b> 客户端 SDK </b>

  主要负责客户端的音视频采集、渲染、滤镜处理、编解码、传输等工作，客户可以快速集成到自己 App 中，让自己的应用具备音视频通话的能力

- <b> 服务端 REST API 和 SDK </b>

  主要提供房间管理、状态回调等基本的业务功能，另外还提供鉴黄鉴暴、质量分析等配套功能

- <b> 服务器 </b>

  主要负责信令交互、音视频传输、代理加速等工作，保证音视频互动延时低，可用性高
  
### 3.2 交互流程

![](http://docs.qnsdk.com/qnrtc-interactive.png)

实时通话交互流程如上图所示，因此，App 服务端需要开发的工作如下：

- 为用户创建通话房间，并将通话房间和对应主播的 Id 关联起来
- 计算加入房间的 roomToken 并提供给 App，该 roomToken 是结合 userId、roomName 等信息使用七牛的 AccessKey 和 SecretKey 按照一定的规则生成
- 提供通话的业务逻辑，如：通话请求/应答业务逻辑、服务端房间管理和踢人等

关于 roomToken 的计算方法请查阅[《七牛实时音视频云服务端 API 接口规范》](https://developer.qiniu.com/rtc/8805/server-overview)，另外，我们也提供了多种开发语言的 SDK  [服务端开发手册及 SDK 下载](https://developer.qiniu.com/rtc/8812/serversdk)。

### 3.3 房间管理
关于音视频通话房间的 API 主要分为两个部分，一部分在客户端，另一部分在服务端。在客户端 SDK 中，只有加入/离开连麦房间的接口。我们把创建/销毁连麦房间的功能放到了服务端，由 App Server 向七牛的服务器发送请求来完成。关于服务端 API 的详细内容，请查阅[《七牛实时音视频云服务端 API 接口规范》](https://developer.qiniu.com/rtc/8805/server-overview)。

# 4 方案优势
- 实时互动对网络的稳定性和连通性要求非常苛刻，所以必须购买数据中心建设基础网络。而使用七牛的实时音视频云服务，不需要投入大量资金做传输网络的基础建设，按量计费灵活方便。
- 经验丰富的音视频团队提供稳定、易用的客户端 SDK，保证了客户端应用开发的效率和可用性。
- 完整的音视频产品线，使用七牛的实时音视频云服务的同时可以无缝接入七牛其他的所有服务，例如短视频、直播、存储、大数据分析等服务。

# 5 应用场景

## 5.1 主播连麦

- 支持主播之间连麦一起直播，带来与传统单向直播不一样的体验
- 自带美颜滤镜，第三方美颜贴纸、人脸识别，让直播过程更有趣
- 48KHz 采样率、全频带编解码以及对音乐场景的特殊优化保证观众可以听到最优质的声音

## 5.2 视频会议

- 小范围实时音视频互动，提供多种视频通话布局模板，更提供自定义布局方式，保证会议发言者互相之间的实时性，提升普通观众的观看体验
- 提供七牛云自有的直播分发服务，可实现 HLS、RTMP、HTTP 等多种直播分发形式，支持更多人通过拉取直播流收看会议内容，适合大型的企业在线会议
- 支持动态邀人，踢人、禁音，禁视会议权限分级控制
- 客户可以利用七牛实时音视频云轻松做出一款类似 WebEx 的应用

## 5.3 一对一社交

- 客户可以利用七牛实时音视频云实现 QQ、微信、陌陌等社交应用的一对一视频互动
- 提供七牛云自有的直播分发服务，可实现 HLS、RTMP、HTTP 等多种直播分发形式，画面清晰、声音清晰不卡顿
- 自带美颜滤镜，第三方美颜贴纸、人脸识别，让社交更加有趣

## 5.4 狼人杀游戏

- 支持 12 人视频通话，玩家可在游戏中选择只开启语音或同时开启音视频
- 提供七牛云自有的直播分发服务，可实现 HLS、RTMP、HTTP 等多种直播分发形式，音视频体验稳定流畅，不卡麦，不黑麦
- 提供美颜和贴纸等功能，不断增强用户粘性，提升用户的活跃度和 DAU

## 5.5 在线教育

- 自定义的视频布局功能允许开发者按照自己的业务需求调整老师和学生的显示位置
- 旁路直播功能加上直播云的直播功能，实现观众人数无上限，让更多学生享受在线教育的便利
- 搭配使用聊天室功能，文字、语音、图片、视频包括自定义消息等，更多的互动方式有效提升课堂氛围
- 服务端录制对接点播平台，支持课程录制以及在线回放，让优质资源服务更多学生

## 5.6 在线抓娃娃

- 娃娃机端，通过主板或 PC 机连接两个摄像头，采集视频数据
- 通过编码器编码，进行视频流的优化，通过实时流网络进行视频实时传输，最后到达操作端，解码、播放
- 操作端通过业务 Server 将操控指令发送给娃娃机端，通过视频流获得实时反馈
- 采用 WebSocket 技术，结合成熟稳定的直播云端，突破了 HLS 高延迟的技术限制，同时还能保持 H5 的传播便捷特性

## 5.7 在线客服

- 线上开展音视频对话，对客户的资信情况进行审核，方便金融科技企业实现用户在线签约、视频开户验证以及呼叫中心等功能
- 提供云端存储空间及海量数据的处理能力，提供高可用的技术和高稳定的平台

# 6 开发文档

- 可通过 [QNRTCKit 快速入门](https://developer.qiniu.com/rtc/12831/quick_start-HarmonyOS) 了解如何快速搭建音视频通话应用
- 可通过 [QNRTCKit 使用指南](https://developer.qiniu.com/rtc/12837/development_guidelines-HarmonyOS) 了解不同场景的实现方式
- 可通过 [QNRTCKit API 概览](https://developer.qiniu.com/rtc/12830/ApiGuide-HarmonyOS) 了解 SDK 的接口设计及使用姿势

# 7 反馈及意见

当你遇到任何问题时，可以通过在 GitHub 的 repo 提交 issues 来反馈问题，请尽可能的描述清楚遇到的问题，如果有错误信息也一同附带，并且在 Labels 中指明类型为 bug 或者其他。

[通过这里查看已有的 issues 和提交 Bug](https://github.com/pili-engineering/QNRTC-HarmonyOS/issues)

# 8 FAQ

## 8.1 实时通话功能是否收费？

客户端 SDK 不收费，服务端可按照带宽、流量或者时长收费，具体请联系七牛商务或者技术支持。

## 8.2 实时通话对讲延时多大？

正常网络条件下，对讲延时在 200-300ms 左右。

## 8.3 是否有服务端的 SDK 或者 demo 代码可以参考？

有的，请参考： [QNRTC-Server](https://developer.qiniu.com/rtc/8812/serversdk)
