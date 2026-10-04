[English](README.md) | **简体中文**

# Listenote

Listenote 能录下 Windows 电脑上正在播放的声音，并在你听的同时实时显示转录文字。
网课、线上会议、播客、视频都可以：按"开始"，边听边看文字，录音和文字都会保存下来供以后回看。
语音在你自己的电脑上转录，录下的任何内容都不会上传。

**[下载最新版本](../../releases/latest)**

## 功能

- **录制系统声音**：扬声器或耳机里播放的任何声音都能录下；打开麦克风，还能把你自己的声音一起录进去。
- **本机实时转录**：使用 OpenAI 的 Whisper 语音模型，通过 whisper.cpp 在本机运行。
- **支持 8 种语音语言**：英语、中文、西班牙语、法语、德语、日语、韩语、葡萄牙语。
- **边录边保存**：音频和转录文本持续写入磁盘，即使应用或电脑意外停止，录音也会保留到停止前几秒。
- **导出 TXT**：带时间戳；以后随时可以重新打开任何一段录音，查看或再次导出。
- **界面同样支持这 8 种语言**：默认跟随 Windows 显示语言，也可以在设置里手动选择。

## 两个版本

Listenote 有两个版本，可以同时安装，共用同一批录音和模型。

| | Listenote | Listenote GPU |
|---|---|---|
| 转录用的硬件 | 处理器（CPU） | 显卡（通过 Vulkan） |
| 语音模型 | Whisper base、Whisper small | Whisper base、Whisper small、Whisper large-v3-turbo |
| 适合 | 任何较新的电脑 | 有独立显卡或较新集成显卡、最看重准确率的电脑 |
| 安装包大小 | 约 2 MB | 约 7 MB |

## 系统要求

- Windows 10 或 Windows 11，64 位。
- 处理器需要支持 AVX2，2015 年以后的电脑大多支持。少数低端 Celeron、Pentium 处理器不支持，无法使用转录。
- 仅 Listenote GPU：显卡驱动需要支持 Vulkan。近几年 Intel、AMD、NVIDIA 显卡的最新驱动基本都支持。
- 磁盘空间：语音模型每个 141 MB 到 547 MB；录音按标准质量每小时约 0.6 到 0.7 GB。

## 开始使用

1. [下载](../../releases/latest)你需要的版本的安装包并运行。
2. 因为安装包没有代码签名，Windows 可能会提示"Windows 已保护你的电脑"。点 **更多信息**，再点 **仍要运行**。
3. 打开 Listenote，点 **设置**，选择语音语言，下载推荐的语音模型。只需下载一次，之后转录完全离线。
4. 点 **开始**。想把自己的声音也录进去，就打开麦克风。
5. 录完后点 **停止**，再点 **导出 TXT** 保存转录文本。

## 语音模型

模型在你第一次选用时从 [Hugging Face](https://huggingface.co/ggerganov/whisper.cpp) 下载，
下载后会用官方公布的 SHA-256 校验，也可以在设置里删除。

| 模型 | 大小 | 文字出现方式 | 推荐用于 |
|---|---|---|---|
| Whisper base | 141 MB | 几秒内出现，先显示灰色的初步结果 | 大多数语言 |
| Whisper small | 465 MB | 按段落出现，大约每 30 秒一段；更准确 | Listenote 的中文、日语、韩语 |
| Whisper large-v3-turbo | 547 MB | 按段落出现，大约每 30 秒一段；最准确 | Listenote GPU 的中文、日语、韩语 |

Listenote 会记住你为每种语音语言选择的模型。

## 文件保存在哪里

所有文件都在 **文档** 文件夹里的 **Listenote** 文件夹中：

| 文件夹 | 内容 |
|---|---|
| `Recordings` | 每段录音的音频（`.wav`）和转录文本（`.transcript.json`） |
| `Models` | 下载的语音模型 |
| `Exports` | 导出 TXT 时默认保存的位置 |

卸载 Listenote 不会删除这个文件夹，不再需要时请手动删除。在应用里删除的录音会进入回收站。

## 隐私

音频和转录文本永远不会离开你的电脑。Listenote 没有账号，也不收集任何使用数据。
只有在下载你选择的语音模型时才会联网。

## 注意事项

- 如果电脑转录的速度跟不上播放速度，Listenote 会跳过一部分音频以跟上进度，并在转录文本里标出跳过的部分。换用更快的模型或 Listenote GPU 可以避免这种情况。
- 准确率取决于音频质量：说话清晰、背景噪音少时效果最好。
- 请确认你有权录制所录的内容，并遵守当地关于录音许可和版权的规定。

## 许可证

Listenote 可以免费使用，但不是开源软件；这个仓库只用来发布安装包。具体条款见 [LICENSE](LICENSE)（英文）。

它基于开源软件构建，包括 [whisper.cpp](https://github.com/ggerganov/whisper.cpp)（MIT）、
[Tauri](https://tauri.app)（MIT 或 Apache 2.0）和 [React](https://react.dev)（MIT），
并使用 OpenAI 的 [Whisper](https://github.com/openai/whisper) 模型（MIT）。
