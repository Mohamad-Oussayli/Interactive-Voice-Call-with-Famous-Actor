<div align="center">

# Interactive Voice Call with Maguy Bou Ghosn

**Approach 2: Whisper → Gemini Prompt Injection → ElevenLabs Fine-Tune**

[![Open in Colab](https://img.shields.io/badge/Colab-Run%20Approach%202-blue?style=for-the-badge\&logo=googlecolab)](https://colab.research.google.com/drive/1OLPctrVLVyocPHtYTYdmCGLBGkZO3ddY?usp=sharing)

</div>

---

### 📝 Project Overview

This pipeline delivers a conversational experience in authentic Lebanese Arabic dialect using Maguy Bou Ghosn’s persona and voice. It stitches together:

1. **Speech Recognition (STT):** OpenAI Whisper captures user speech in Lebanese Arabic.
2. **LLM Response:** Google Gemini processes the transcript, guided by a prompt folder (`maguy_knowledge_base/`) containing Maguy’s biography, interviews, and catchphrases.
3. **Custom TTS:** ElevenLabs generates Arabic speech, fine-tuned on Maguy’s voice recordings for natural intonation.
4. **Gradio Interface:** Offers a seamless browser UI for recording, previewing, and sending user audio.

---

### 💻 Technical Implementation

* **Whisper STT**

  * Model: `openai/whisper-large-v2` (Lebanese-dialect mode).
* **Gemini Prompt Injection**

  * Prompt folder: `maguy_knowledge_base/`.
  * System instructions enforce colloquial Lebanese phrasing and limit replies to 2–3 sentences.
* **ElevenLabs TTS**

  * Fine-tune: Custom voice model trained on Maguy’s recordings via ElevenLabs API.
  * Output: Lebanese-dialect Arabic speech in Maguy’s timbre.
* **Gradio Frontend**

  * Components: `gr.Audio`, `gr.Button`, `gr.Textbox`.
  * Flow: Record → preview → “Send to Maguy” → playback response.

---

### 🚀 How to Run in Colab

1. **Open the Colab Notebook**
   [Run Approach 2 in Colab](https://colab.research.google.com/drive/1OLPctrVLVyocPHtYTYdmCGLBGkZO3ddY?usp=sharing)
2. **Install Dependencies**

   ```bash
   pip install -r requirements.txt
   ```
3. **Mount & Upload**

   * Ensure the folder `maguy_knowledge_base/` is present in the working directory with all prompt files.
4. **Initialize & Launch**

   * Run all cells → Launch Gradio UI → Copy public link.

---

### 🔗 Hugging Face Space

* **Live Demo:** [https://huggingface.co/spaces/moussayli-ai/maguy-voice-chat](https://huggingface.co/spaces/moussayli-ai/maguy-voice-chat)
* **Note on Performance:**

  * Runs on CPU: expect **60–80 seconds** response latency.
  * Colab GPU runs in **3–5 seconds**.

---

### 📌 Important Notes

* **API Subscription:** Your ElevenLabs custom-voice subscription is pre-configured and active **until July 2, 2025**. After that date, custom TTS will no longer function; we will not renew as this is a portfolio demonstration.

* **Gradio Audio Behavior:** After recording and before clicking **Send to Maguy**, wait **2–3 seconds** for the audio widget to disappear and reappear. This delay is a standard Gradio rendering quirk—only once it reappears can the audio be sent correctly.

---
