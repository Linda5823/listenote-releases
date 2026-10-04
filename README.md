**English** | [简体中文](README.zh-CN.md)

# Listenote

Listenote records the audio playing on your Windows computer and shows a live transcript
while you listen. Online classes, meetings, podcasts, videos: press Start, follow along,
and keep both the recording and the text for later. Speech is transcribed on your own
computer, so nothing you record is uploaded.

**[Download the latest version](../../releases/latest)**

## Features

- **Records system audio**: whatever plays through your speakers or headphones, with your
  microphone mixed in if you turn it on.
- **Live transcription on your device** with OpenAI's Whisper speech models, through
  whisper.cpp.
- **Eight spoken languages**: English, Chinese, Spanish, French, German, Japanese, Korean
  and Portuguese.
- **Saved as you record**: the audio and the transcript are written to disk continuously,
  so even if the app or the computer stops unexpectedly, the recording is kept up to the
  last few seconds.
- **Export to TXT** with timestamps, and reopen any past recording later to read or
  export it again.
- **Interface in the same eight languages**, following your Windows display language
  unless you choose another in Settings.

## Editions

Listenote comes in two editions. They can be installed side by side and share the same
recordings and models.

| | Listenote | Listenote GPU |
|---|---|---|
| Transcribes with | The processor (CPU) | The graphics card, through Vulkan |
| Speech models | Whisper base, Whisper small | Whisper base, Whisper small, Whisper large-v3-turbo |
| Best for | Any recent PC | PCs with a graphics card or a recent integrated GPU, when accuracy matters most |
| Installer size | About 2 MB | About 7 MB |

## System requirements

- Windows 10 or Windows 11, 64-bit.
- A processor with AVX2 support, which most PCs from 2015 onward have. Some low-cost
  Celeron and Pentium processors lack it and cannot run transcription.
- Listenote GPU only: a graphics driver with Vulkan support. Up-to-date drivers for most
  Intel, AMD and NVIDIA graphics from recent years include it.
- Disk space for one or more speech models (141 MB to 547 MB) and for recordings, which
  take roughly 0.6 to 0.7 GB per hour at Standard quality.

## Getting started

1. [Download](../../releases/latest) the installer for the edition you want, and run it.
2. Windows may show "Windows protected your PC", because the installer is not code-signed.
   Click **More info**, then **Run anyway**.
3. Open Listenote, click **Settings**, choose the spoken language, and download the
   suggested speech model. This happens once; transcription then works offline.
4. Click **Start**. Turn on the microphone if you want your own voice included.
5. When you are done, click **Stop**, then **Export TXT** to save the transcript.

## Speech models

Models are downloaded from [Hugging Face](https://huggingface.co/ggerganov/whisper.cpp)
the first time you choose them, checked against their published SHA-256 hashes, and can be
deleted again in Settings.

| Model | Size | How text appears | Suggested for |
|---|---|---|---|
| Whisper base | 141 MB | Within a few seconds, with a gray first guess | Most languages |
| Whisper small | 465 MB | In passages, about every 30 seconds; more accurate | Chinese, Japanese and Korean in Listenote |
| Whisper large-v3-turbo | 547 MB | In passages, about every 30 seconds; most accurate | Chinese, Japanese and Korean in Listenote GPU |

Listenote remembers the model you choose for each spoken language.

## Where your files are

Everything is kept in the **Listenote** folder inside your **Documents** folder:

| Folder | Contents |
|---|---|
| `Recordings` | The audio of each recording (`.wav`) and its transcript (`.transcript.json`) |
| `Models` | Downloaded speech models |
| `Exports` | The suggested place for exported TXT files |

Uninstalling Listenote keeps this folder. Delete it yourself if you no longer need it.
Recordings deleted from inside the app go to the Recycle Bin.

## Privacy

Audio and transcripts never leave your computer. Listenote has no accounts and no
telemetry. The only time it connects to the internet is to download a speech model you
asked for.

## Good to know

- If the computer cannot transcribe as fast as the audio plays, Listenote skips some
  audio to stay current and marks the skipped parts in the transcript. A faster model,
  or Listenote GPU, avoids this.
- Accuracy depends on the audio: clear speech with little background noise works best.
- Please make sure you are allowed to record what you record, and follow the consent and
  copyright rules that apply where you are.

## License

Listenote is free to use but is not open source; this repository only hosts its
installers. See [LICENSE](LICENSE) for the terms.

It is built on open-source software, including [whisper.cpp](https://github.com/ggerganov/whisper.cpp)
(MIT), [Tauri](https://tauri.app) (MIT or Apache 2.0) and [React](https://react.dev) (MIT),
and uses OpenAI's [Whisper](https://github.com/openai/whisper) models (MIT).
