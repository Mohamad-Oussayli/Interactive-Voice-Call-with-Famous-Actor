<div align="center">

# Interactive Voice Call with Maguy Bou Ghosn

A portfolio project demonstrating two pipelines for conversational voice interaction in Lebanese Arabic dialect.

</div>

---

## 📁 Project Structure

```
/approach-whisper-edge-rvc          # Approach 1: Whisper → Gemma3 → EdgeTTS → RVC
/approach-whisper-gemini-11labs     # Approach 2: Whisper → Gemini → ElevenLabs
README.md                           # This overview file
```

---

## 📝 Project Overview

Maguy Bou Ghosn is represented through a voice-bot that listens in colloquial Lebanese Arabic and responds in her voice. Each approach uses a distinct combination of ASR, LLM, TTS, and voice-conversion components to achieve natural interactions:

| Component        | Approach 1                             | Approach 2                               |
| ---------------- | -------------------------------------- | ---------------------------------------- |
| ASR              | OpenAI Whisper                         | OpenAI Whisper                           |
| LLM              | Gemma 3 (fine-tuned via LoRA)          | Google Gemini (prompt injection)         |
| TTS              | Microsoft EdgeTTS (MSA audio)          | ElevenLabs (fine-tuned Lebanese dialect) |
| Voice Conversion | Retrieval-based Voice Conversion (RVC) | N/A (direct custom TTS)                  |
| Interface        | Gradio                                 | Gradio                                   |

---

## 🚀 Approach 1: Whisper → Gemma3 → EdgeTTS → RVC

**Notebook:**
[Interactive Voice Call with Famous Actor.ipynb](approach-whisper-edge-rvc/Interactive_Voice_Call_with_Famous_Actor.ipynb)

**Demo:**
[Run Approach 1 in Colab](https://colab.research.google.com/drive/1a8S8cqiVpaz2R4PCb7eH6zZbHiXvPIJF)

**Key Points:**

* **Gemma 3 LLM**: Fine-tuned on Maguy data for personalized style.
* **EdgeTTS → RVC**: Use Microsoft’s MSA TTS, then convert to Lebanese dialect via RVC model.
* **Separate RVC notebook** for voice conversion: [RVC.ipynb](approach-whisper-edge-rvc/RVC.ipynb).

**Notes:**

* Memory constraints require 4B variant of Gemma for integrated pipeline.
* MSA-to-dialect conversion adds latency (\~5–8 s).

---

## 🚀 Approach 2: Whisper → Gemini → ElevenLabs

**Notebook:**
[Run Approach 2 in Colab](https://colab.research.google.com/drive/1OLPctrVLVyocPHtYTYdmCGLBGkZO3ddY?usp=sharing)

**Hugging Face Space:**
[https://huggingface.co/spaces/moussayli-ai/maguy-voice-chat](https://huggingface.co/spaces/moussayli-ai/maguy-voice-chat)

**Key Points:**

* **Google Gemini** driven by `maguy_knowledge_base/` (biography, interviews, catchphrases).
* **Custom ElevenLabs TTS**: Generates Lebanese-dialect speech in Maguy’s timbre directly.
* **Gradio UI**: Record → preview → "Send to Maguy" → playback.

**Important Notes:**

* ElevenLabs custom-voice subscription is active **until July 2, 2025**; service stops thereafter (portfolio demo only).
* On Hugging Face (CPU): expect **60–80 s** response time; on Colab (GPU): **3–5 s**.
* **Gradio audio quirk**: after recording, wait **2–3 s** for the widget to refresh before clicking "Send to Maguy." Only refreshed audio can be transmitted.

---

