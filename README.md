# Koemaru / 声丸 🎙️

**A Japanese voice-interactive desk companion built with M5Stack CoreS3 (ESP32-S3) and Stack-chan.**

> **Status:** Active personal R&D. A working English wake-word prototype is available; a dedicated Japanese wake word is the next milestone.

## About the project

**Koemaru (声丸 / こえまる)** is an experimental voice assistant designed to be called by its own name. The goal is a small, expressive device that listens for a wake word, accepts a spoken question, replies aloud, and returns to a ready state.

This is an independent hobby project, not a commercial product.

## What currently works

- **On-device wake-word recognition:** Espressif ESP-SR WakeNet9, using the existing **“Hi, StackChan”** model, has been demonstrated on an actual M5Stack CoreS3.
- **Voice interaction:** A wake event can initiate a spoken exchange, followed by a return to the ready state.
- **Touch interaction:** Touch-initiated conversation is also functioning.
- **Local detection:** The wake-word detector runs on the ESP32-S3. Subsequent conversational processing uses a separate host/gateway.

These are limited prototype milestones, **not** claims of production-grade recognition accuracy or long-term reliability. The entire assistant does not run offline.

## The Japanese wake word we want

| Property | Requested value |
| --- | --- |
| Wake word | **こえまる** (also written **声丸**) |
| Romanization | Koemaru |
| Pronunciation | **ko-e-ma-ru** (four Japanese morae; no “Hi” prefix) |
| Language | Japanese |
| Target | M5Stack CoreS3 / ESP32-S3 |
| Audio input | 16 kHz, signed 16-bit, mono PCM |
| Goal | Local, always-ready wake detection |

We have evaluated experimental wake-word approaches using recordings captured on the device. They did not meet the project's recognition-quality targets. **A Japanese “こえまる” model has not yet been obtained or deployed.**

### Request for an Espressif community WakeNet model

We are interested in a **Japanese TTS-trained WakeNet model for “こえまる”** through the Espressif community program.

Our working prototype uses WakeNet9, so **WakeNet9 compatibility would be ideal**. We can also consider WakeNet10 if that is the supported route, subject to adapting and validating the runtime.

The currently tested development baseline is:

| Component | Version / specification |
| --- | --- |
| M5Stack Arduino core | 3.2.5 |
| Bundled ESP-IDF | 5.4.2 |
| Bundled ESP-SR | 1.9.5 |
| Working reference wake model | `wn9_histackchan_tts3` |
| Device memory | 16 MB Flash / 8 MB PSRAM |

We would appreciate guidance on supported model generation, ESP-SR version, model files/packaging, mono input, detection mode, resource requirements, and applicable license.

Any model supplied in the future would undergo new, independent tests on the real hardware before integration.

## Next steps

1. Request a Japanese community wake-word model for **こえまる**.
2. Verify ESP-SR/runtime compatibility on CoreS3.
3. Evaluate real-world detections, similar-sounding phrases, and environmental false triggers.
4. Integrate it while preserving the existing wake and touch conversation paths.

Until a Japanese model passes acceptance, **“Hi, StackChan”** and touch-based interaction remain our working baseline.

## Privacy and source availability

**This is a public project overview, not the development source repository.** The actual development repository remains private.

No personal voice recordings, audio datasets, model weights, API keys, network details, device credentials, or private application source code are published here. This page does not offer a downloadable custom wake model or firmware.

Koemaru is independent and is not affiliated with or endorsed by M5Stack or Espressif.

## 日本語での紹介

**声丸（こえまる）**は、M5Stack CoreS3とStack-chanを用いて個人開発している音声対話アシスタントです。

現在は公式WakeNet9の既存モデル「Hi, StackChan」による呼びかけ起動、音声応答、READY状態への復帰、タッチ起動による会話を実機で確認しています。

次の目標は、**日本語の「こえまる！」という呼びかけだけで起動できること**です。独自方式も実音声で検証しましたが、実用水準に届かなかったため、Espressifの日本語カスタムWakeNetモデルの提供を希望しています。

本リポジトリは公開用の紹介ページのみです。開発コード、本人音声、認証情報などは公開しません。

## Related links

- [Espressif ESP-SR](https://github.com/espressif/esp-sr)
- [M5Stack CoreS3](https://docs.m5stack.com/en/core/CoreS3)
- [M5Stack StackChan](https://github.com/m5stack/StackChan)

For questions about the public project overview, please open an issue in this repository.
