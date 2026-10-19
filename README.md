# Sonorus AI (`sonorus-ai`)

[![PyPI version](https://badge.fury.io/py/sonorus-ai.svg)](https://pypi.org/project/sonorus-ai/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)

**Sonorus AI** is an enhanced speech recognition library built on top of OpenAI's Whisper, optimized for Indian multilingual contexts:

- 🇮🇳 **Native Hinglish Transcription:** Transcribes Hindi speech directly into clean, phonetic Roman English script (`--language Hinglish`).
- ✍️ **Phonetic Corrections:** Built-in dictionary post-processing to fix common transliteration slips (e.g., `bina bikhar`, `mohabbat`, `guroor`).
- 📁 **Organized Outputs:** Automatically saves transcriptions into sorted folders (`outputs/Hinglish/`, `outputs/Hindi/`, `outputs/English/`) in `.txt` format without cluttering your project root.

---

## ⚡ Quick Start

### 1. Installation

Install via PyPI:
```bash
pip install sonorus-ai
```

Or install the latest version directly from GitHub:
```bash
pip install git+https://github.com/Krishnanshu3708/sonorus-ai.git
```

> **Prerequisite:** Make sure [`ffmpeg`](https://ffmpeg.org/) is installed on your system:
> - **Windows (Chocolatey):** `choco install ffmpeg`
> - **Windows (Scoop):** `scoop install ffmpeg`
> - **Mac (Homebrew):** `brew install ffmpeg`
> - **Ubuntu/Debian:** `sudo apt update && sudo apt install ffmpeg`

---

## 🚀 Usage

### Option A: In Python

```python
import sonorus

# 1. Load the model (turbo, tiny, base, small, medium, large)
model = sonorus.load_model("turbo")

# 2. Transcribe Hindi speech directly into Hinglish (Roman English script)
result = model.transcribe("hindi_meeting.mp3", language="Hinglish")
print(result["text"])

# Standard English / Multilingual transcription
result_en = model.transcribe("english_podcast.mp3")
print(result_en["text"])
```

### Option B: Command Line (CLI)

Transcribe directly from your terminal using `sonorus`:

```bash
# Transcribe Hinglish with automated phonetic correction & clean folder organization
sonorus "audio.mp4" --model turbo --language Hinglish

# Transcribe standard English/Multilingual
sonorus "lecture.mp3" --model turbo

# Transcribe multiple files at once
sonorus audio1.flac audio2.mp3 --model turbo
```

To see all available CLI options:
```bash
sonorus --help
```

---

## 📊 Available Models

| Size | Parameters | Multilingual Model | Required VRAM | Relative Speed | Recommended For |
| :---: | :---: | :---: | :---: | :---: | :--- |
| **tiny** | 39 M | `tiny` | ~1 GB | ~10x | Fast testing / CPU |
| **base** | 74 M | `base` | ~1 GB | ~7x | Low-spec devices |
| **small** | 244 M | `small` | ~2 GB | ~4x | Balanced accuracy & speed |
| **medium** | 769 M | `medium` | ~5 GB | ~2x | High accuracy & translation |
| **large** | 1550 M | `large` | ~10 GB | 1x | Best quality |
| **turbo** | 809 M | `turbo` | ~6 GB | ~8x | **Recommended for Hinglish & English** |

---

## 🛠️ Local Development

If you want to contribute or build from source:

```bash
git clone https://github.com/Krishnanshu3708/sonorus-ai.git
cd sonorus-ai
pip install -e .
```

Run tests:
```bash
pytest
```

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).
