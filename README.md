# Interactive Voice Call with Maguy Bou Ghosn

A portfolio project demonstrating two pipelines for conversational voice interaction in Lebanese Arabic dialect.

---

## 📁 Project Structure

```
/approach-whisper-edge-rvc          # Approach 1: Whisper → Gemma3 → EdgeTTS → RVC
/approach-whisper-gemini-11labs     # Approach 2: Whisper → Gemini → ElevenLabs
README.md                           # This overview file
```

---

## 📝 Project Overview

Maguy Bou Ghosn is represented through a voice-bot that listens in colloquial Lebanese Arabic and responds in her voice. Each approach uses a distinct combination of ASR, LLM, TTS, and (if needed) voice-conversion components to achieve natural interactions.

| Component            | Approach 1                             | Approach 2                               |
| -------------------- | -------------------------------------- | ---------------------------------------- |
| **ASR**              | OpenAI Whisper                         | OpenAI Whisper                           |
| **LLM**              | Gemma 3 (fine-tuned via LoRA)          | Google Gemini (prompt injection)         |
| **TTS**              | Microsoft EdgeTTS (MSA audio)          | ElevenLabs (fine-tuned Lebanese dialect) |
| **Voice Conversion** | Retrieval-based Voice Conversion (RVC) | N/A (direct custom TTS)                  |
| **Interface**        | Gradio                                 | Gradio                                   |

---

## 🚀 Approach 1: Whisper → Gemma3 → EdgeTTS → RVC

**Notebooks (in `approach-whisper-edge-rvc/`):**

* `Interactive_Voice_Call_with_Famous_Actor.ipynb`
* `RVC.ipynb`

**Demo:**
[Run Approach 1 in Colab](https://colab.research.google.com/drive/1a8S8cqiVpaz2R4PCb7eH6zZbHiXvPIJF)

**Key Points:**

* **Gemma 3 LLM** fine-tuned on Maguy’s data for personalized style.
* **EdgeTTS → RVC**: Microsoft’s MSA TTS output converted to Lebanese dialect via RVC.
* Use the 4B variant of Gemma when GPU memory is limited.
* Combined TTS + conversion latency: \~5–8 s.

---

## 🚀 Approach 2: Whisper → Gemini → ElevenLabs

**Notebook:**
[Run Approach 2 in Colab](https://colab.research.google.com/drive/1OLPctrVLVyocPHtYTYdmCGLBGkZO3ddY?usp=sharing)

**Hugging Face Space:**
[Visit the Hugging Face Space](https://huggingface.co/spaces/moussayli-ai/maguy-voice-chat)

**Key Points:**

* **Google Gemini** driven by the `maguy_knowledge_base/` folder (biography, interviews, catchphrases).
* **Custom ElevenLabs TTS** generates Lebanese-dialect speech in Maguy’s timbre directly.
* **Gradio UI**: Record → preview → “Send to Maguy” → playback.

**Important Notes:**

* **Subscription Expiry:** ElevenLabs custom-voice is active **until July 2, 2025**. After that, custom TTS will no longer function (portfolio demo only).
* **Performance:**

  * CPU (HF Space): 60–80 s response time.
  * GPU (Colab): 3–5 s response time.
* **Gradio Audio Quirk:** After recording, wait 2–3 s for the widget to refresh before clicking **Send to Maguy**. Only refreshed audio can be transmitted.

---
