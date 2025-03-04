<div align="center">
  <img src="./docs/images/logo.png"alt="VideoCaptioner Logo" width="100">
  <p>卡卡字幕助手</p>
  <h1>VideoCaptioner</h1>
  <p>一款基于大语言模型(LLM)的视频字幕处理助手，支持语音识别、字幕断句、优化、翻译全流程处理</p>

  简体中文 / [正體中文](./docs/README_TW.md) / [English](./docs/README_EN.md)
  
</div>

## 📖 项目介绍

卡卡字幕助手（VideoCaptioner）操作简单且无需高配置，支持网络调用和本地离线（支持调用GPU）两种方式进行语音识别，利用可用通过大语言模型进行字幕智能断句、校正、翻译，字幕视频全流程一键处理！为视频配上效果惊艳的字幕。

最新版本已经支持 VAD 、 人声分离、 字级时间戳 批量字幕等实用功能

- 🎯 无需GPU即可使用强大的语音识别引擎，生成精准字幕
- ✂️ 基于 LLM 的智能分割与断句，字幕阅读更自然流畅
- 🔄 AI字幕多线程优化与翻译，调整字幕格式、表达更地道专业
- 🎬 支持批量视频字幕合成，提升处理效率
- 📝 直观的字幕编辑查看界面，支持实时预览和快捷编辑
- 🤖 消耗模型 Token 少，且内置基础 LLM 模型，保证开箱即用

## 📸 界面预览

<div align="center">
  <img src="https://h1.appinn.me/file/1731487405884_main.png" alt="软件界面预览" width="90%" style="border-radius: 5px;">
</div>

![页面预览](https://h1.appinn.me/file/1731487410170_preview1.png)
![页面预览](https://h1.appinn.me/file/1731487410832_preview2.png)


## 🧪 测试

全流程处理一个14分钟1080P的 [B站英文 TED 视频](https://www.bilibili.com/video/BV1jT411X7Dz)，调用本地 Whisper 模型进行语音识别，使用 `gpt-4o-mini` 模型优化和翻译为中文，总共消耗时间约 **3 分钟**。

 近后台计算，模型优化和翻译消耗费用不足 ￥0.01（以OpenAI官方价格为计算）

具体字幕和视频合成的效果的测试结果图片，请参考 [TED视频测试](./docs/test.md)


## 🚀 快速开始

### Windows 用户

软件较为轻量，打包大小不足 60M,已集成所有必要环境，下载后可直接运行。

1. 从 [Release](https://github.com/WEIFENG2333/VideoCaptioner/releases) 页面下载最新版本的可执行程序。或者：[蓝奏盘下载](https://wwwm.lanzoue.com/idzKZ2hjcimb)

2. 打开安装包进行安装

3. （可选）LLM API 配置，选择是否启用字幕优化或者字幕翻译

4. 拖拽视频文件到软件窗口，即可全自动处理

提示：每一个步骤均支持单独处理，均支持文件拖拽。

<details>
<summary>MacOS 用户</summary>
 
 
由于本人缺少 Mac，所以没法测试和打包，暂无法提供 MacOS 的可执行程序。

Mac 用户请自行使用下载源码和安装 python 依赖运行。（本地 Whisper 功能暂不支持 MacOS）

1. 安装 ffmpeg 和 Aria2 下载工具
```bash
brew install ffmpeg
brew install aria2
brew install python@3.**
```

2. 克隆项目
```bash
git clone https://github.com/WEIFENG2333/VideoCaptioner.git
cd VideoCaptioner
```

3. 安装依赖
```bash
python3.** -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

4. 运行程序
```bash
python main.py
```
</details>

<details>
<summary>Docker 部署（beta）</summary>

目前应用较为简略，欢迎各位PR贡献。

### 1. 克隆项目

```bash
git clone https://github.com/WEIFENG2333/VideoCaptioner.git
cd VideoCaptioner
```

### 2. 构建镜像

```bash
docker build -t video-captioner .
```

### 3. 运行容器

使用自定义API配置运行：
```bash
docker run -d \
  -p 8501:8501 \
  -v $(pwd)/temp:/app/temp \
  -e OPENAI_BASE_URL="你的API地址" \
  -e OPENAI_API_KEY="你的API密钥" \
  --name video-captioner \
  video-captioner
```

### 4. 访问应用

打开浏览器访问：`http://localhost:8501`

### 注意事项

- 容器内已预装ffmpeg等必要依赖
- 如需使用其他模型，请通过环境变量配置

</details>

## ✨ 主要功能

软件充分利用大语言模型(LLM)在理解上下文方面的优势，对语音识别生成的字幕进一步处理。有效修正错别字、统一专业术语，让字幕内容更加准确连贯，为用户带来出色的观看体验！

#### 1. 多平台视频下载与处理
- 支持国内外主流视频平台（B站、Youtube等）
- 自动提取视频原有字幕处理

#### 2. 专业的语音识别引擎
- 提供多种接口在线识别，效果媲美剪映（免费、高速）
- 支持本地Whisper模型（保护隐私、可离线）

#### 3. 字幕智能纠错
- 自动优化专业术语、代码片段和数学公式格式
- 上下文进行断句优化，提升阅读体验
- 支持文稿提示，使用原有文稿或者相关提示优化字幕断句

#### 4. 高质量字幕翻译
- 结合上下文的智能翻译，确保译文兼顾全文
- 通过Prompt指导大模型反思翻译，提升翻译质量
- 使用序列模糊匹配算法、保证时间轴完全一致

#### 5. 字幕样式调整
- 丰富的字幕样式模板（科普风、新闻风、番剧风等等）
- 多种格式字幕视频（SRT、ASS、VTT、TXT）


## ⚙️ 基本配置

### 1. LLM API 配置说明 （可选）

| 配置项 | 说明 |
|--------|------|
| 内置模型 | 软件内置基础大语言模型（`gpt-4o-mini`），无需配置即可使用 |
| API支持 | 支持标准 OpenAI API 格式。兼容 [SiliconCloud](https://cloud.siliconflow.cn/i/HF95kaoz)、[DeepSeek](https://platform.deepseek.com/) 、 [Ollama](https://ollama.com/blog/openai-compatibility) 等。<br>配置方法请参考[配置文档](./docs/llm_config.md) |

推荐模型: 追求更高质量可选用 `Claude-3.5-sonnet` 或 `gpt-4o`


### 2. 本地 Whisper 语音识别配置（需软件内下载）

Whisper 版本有 WhisperCpp 和 fasterWhisper 两种，后者效果更好，都需要自行在软件内下载模型。

| 模型 | 磁盘空间 | 内存占用 | 说明 |
|------|----------|----------|------|
| Tiny | 75 MiB | ~273 MB | 转录很一般，仅用于测试 |
| Small | 466 MiB | ~852 MB | 英文识别效果已经不错 |
| Medium | 1.5 GiB | ~2.1 GB | 中文识别建议至少使用此版本 |
| Large-v1/v2 | 2.9 GiB | ~3.9 GB | 效果好，配置允许情况推荐使用 |
| Large-v3 | 2.9 GiB | ~3.9 GB | 社区反馈可能会出现幻觉/字幕重复问题 |

注：以上模型国内网络可直接在软件内下载；支持GPU也支持核显调用。


### 3. 文稿匹配

- 在"字幕优化与翻译"页面，包含"文稿匹配"选项，支持以下**一种或者多种**内容，辅助校正字幕和翻译:

| 类型 | 说明 | 填写示例 |
|------|------|------|
| 术语表 | 专业术语、人名、特定词语的修正对照表 | 机器学习->Machine Learning<br>马斯克->Elon Musk<br>打call -> 应援<br>图灵斑图<br>公交车悖论 |
| 原字幕文稿 | 视频的原有文稿或相关内容 | 完整的演讲稿、课程讲义等 |
| 修正要求 | 内容相关的具体修正要求 | 统一人称代词、规范专业术语等<br>填写**内容相关**的要求即可，[示例参考](https://github.com/WEIFENG2333/VideoCaptioner/issues/59#issuecomment-2495849752) |

- 如果需要文稿进行字幕优化辅助，全流程处理时，先填写文稿信息，再进行开始任务处理
- 注意: 使用上下文参数量不高的小型LLM模型时，建议控制文稿内容在1千字内，如果使用上下文较大的模型，则可以适当增加文稿内容。


### 4. 语音识别接口说明

| 接口名称 | 支持语言 | 运行方式 | 说明 |
|---------|---------|---------|------|
| B接口 | 仅支持中文、英文 | 在线 | 免费、速度较快 |
| J接口 | 仅支持中文、英文 | 在线 | 免费、速度较快 |
| WhisperCpp | 中文、日语、韩语、英文等 99 种语言，外语效果较好 | 本地 | （实际使用不稳定）需要下载转录模型<br>中文建议medium以上模型<br>英文等使用较小模型即可达到不错效果。 |
| fasterWhisper | 中文、英文等多99种语言，外语效果优秀，时间轴更准确 | 本地 | （🌟极力推荐🌟）需要下载程序和转录模型<br>支持CUDA,速度更快，转录准确。<br>建议优先使用👍 |


### 5. Cookie 配置说明

但你需要URL下载功能时，如果遇到以下情况:
1. 下载的视频需要登录信息
2. 只能下载较低分辨率的视频
3. 网络条件较差时需要验证

- 请参考 [Cookie 配置说明](./docs/get_cookies.md) 获取Cookie信息，并将cookies.txt文件放置到软件的 `AppData` 目录下，即可正常下载高质量视频。

## 💡 软件流程介绍

程序简单的处理流程如下:
```
语音识别 -> 字幕断句 -> 字幕优化翻译(可选) -> 字幕视频合成
```

安装软件的主要目录结构说明如下：
```
VideoCaptioner/
├── runtime/                    # 运行环境目录（不用更改）
├── resources/               # 软件资源文件目录（界面、图标等,不用更改）
├── work-dir/               # 工作目录，处理完成的视频和字幕文件保存在这里
├── AppData/                    # 应用数据目录
    ├── cache/              # 缓存目录，临时数据
    ├── models/              # 存放 Whisper 模型文件
    ├── logs/               # 日志目录，记录软件运行状态
    ├── settings.json          # 存储用户设置
    └──  cookies.txt           # 视频平台的 cookie 信息
└── VideoCaptioner.exe      # 主程序执行文件
```

## 📝 说明

1. 字幕断句的质量对观看体验至关重要。为此我开发了 [SubtitleSpliter](https://github.com/WEIFENG2333/SubtitleSpliter)，它能将逐字字幕智能重组为符合自然语言习惯的段落，并与视频画面完美同步。

2. 在处理过程中，仅向大语言模型发送纯文本内容，不包含时间轴信息，这大大降低了处理开销。

3. 在翻译环节，我们采用吴恩达提出的"翻译-反思-翻译"方法论。这种迭代优化的方式不仅确保了翻译的准确性。

## 🤝 贡献指南

作者是一名大三学生，个人能力和项目都还有许多不足，项目也在不断完善中，如果在使用过程遇到的Bug，欢迎提交 [Issue](https://github.com/WEIFENG2333/VideoCaptioner/issues) 和 Pull Request 帮助改进项目。

## 更新日志

<details>
<summary>2024.1.22</summary>

### 核心功能增强
- 完整重构代码架构，优化整体性能
- 字幕优化与翻译功能模块分离，提供更灵活的处理选项
- 新增批量处理功能：支持批量字幕、批量转录、批量字幕视频合成
- 全面优化 UI 界面与交互细节

### AI 模型与翻译升级
- 扩展 LLM 支持：新增 SiliconCloud、DeepSeek、Ollama、Gemini、ChatGLM 等模型
- 集成多种翻译服务：DeepLx、Bing、Google、LLM
- 新增 faster-whisper-large-v3-turbo 模型支持
- 新增多种 VAD（语音活动检测）方法
- 支持自定义反思翻译开关
- 字幕断句支持语义/句子两种模式
- 字幕断句、优化、翻译提示词的优化
- 字幕、转录缓存机制的优化
- 优化中文字幕自动换行功能
- 新增竖屏字幕样式
- 改进字幕时间轴切换机制，消除闪烁问题

### Bug 修复与其他改进
- 修复 Whisper API 无法使用问题
- 新增多种字幕视频格式支持
- 修复部分情况转录错误的问题
- 优化视频工作目录结构
- 新增日志查看功能
- 新增泰语、德语等语言的字幕优化
- 修复诸多Bug...

</details>


<details>
<summary>2024.12.07</summary>

- 新增 Faster-whisper 支持，音频转字幕质量更优
- 支持Vad语音断点检测，大大减少幻觉现象
- 支持人声音分离，分离视频背景噪音
- 支持关闭视频合成
- 新增字幕最大长度设置
- 新增字幕末尾标点去除设置
- 优化和翻译的提示词优化
- 优化LLM字幕断句错误的情况 
- 修复音频转换格式不一致问题

</details>

<details>
<summary>2024.11.23</summary>

- 新增 Whisper-v3 模型支持，大幅提升语音识别准确率
- 优化字幕断句算法，提供更自然的阅读体验 
- 修复检测模型可用性时的稳定性问题
</details>

<details>
<summary>2024.11.20</summary>

- 支持自定义调节字幕位置和样式
- 新增字幕优化和翻译过程的实时日志查看
- 修复使用 API 时的自动翻译问题
- 优化视频工作目录结构,提升文件管理效率
</details>

<details>
<summary>2024.11.17</summary>

- 支持双语/单语字幕灵活导出
- 新增文稿匹配提示对齐功能
- 修复字幕导入时的稳定性问题
- 修复非中文路径下载模型的兼容性问题
</details>

<details>
<summary>2024.11.13</summary>

- 新增 Whisper API 调用支持
- 支持导入 cookie.txt 下载各大视频平台资源
- 字幕文件名自动与视频保持一致
- 软件主页新增运行日志实时查看
- 统一和完善软件内部功能
</details>

## ⭐ Star History

[![Star History Chart](https://api.star-history.com/svg?repos=WEIFENG2333/VideoCaptioner&type=Date)](https://star-history.com/#WEIFENG2333/VideoCaptioner&Date)

## 💖 支持作者

如果觉得项目对你有帮助，可以给项目点个Star，这将是对我最大的鼓励和支持！

<div align="center">
  <img src="./docs/images/alipay.jpg" alt="支付宝二维码" width="30%">
  <img src="./docs/images/wechat.jpg" alt="微信二维码" width="30%">
</div>
