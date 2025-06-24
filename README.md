<div align="center">

# Interactive Voice Call with Maguy Bou Ghosn

[![Colab](https://img.shields.io/badge/Colab-Interface-blue?style=for-the-badge&logo=googlecolab)](https://colab.research.google.com/drive/1a8S8cqiVpaz2R4PCb7eH6zZbHiXvPIJF) [![Colab](https://img.shields.io/badge/Colab-RVC_DEMO-blue?style=for-the-badge&logo=googlecolab)](https://colab.research.google.com/drive/16xpJLQ87Nqv3VWVTyxKgfLuZnI3ST9zi)


</div>

---

### 📝 Project Overview
This project creates a real-time, voice-based conversational experience with famous Lebanese actress Maguy Bou Ghosn. The system uses advanced AI technologies to enable natural voice interactions in authentic Lebanese Arabic dialect.
The system combines four key components to create a seamless voice interaction pipeline:

- **Speech Recognition (STT):** Converts user's spoken Lebanese Arabic to text. 
- **Language Model (LLM):** Generates contextually appropriate responses in Maguy's style of speaking.
- **Text-to-Speech (TTS):** Converts text responses to speech.
- **Voice Conversion:** Transforms the generated speech to match Maguy's voice characteristics.

---

### 💻 Technical Implementation

- **WhisperSTT:** Speech recognition using **OpenAI's Whisper** with optional Gemini-based text correction.
- **GemmaLLM:** Fine-tuned **Gemma 3** model using LoRA (Low-Rank Adaptation) for efficient training.
- **EdgeTTS:** Microsoft's **Edge TTS** for high-quality Arabic speech synthesis.
- **VoiceConverter:** Voice conversion using **Retrieval-based Voice Conversion (RVC)** technology.
- **Gradio Interface:** User-friendly web interface for interactive conversations.

---
### 📂 Project Files

- **`Interactive_Voice_Call_with_Famous_Actor.ipynb`:** Main notebook containing the complete implementation of the interactive voice system
- **`RVC.ipynb`:** Separate notebook for voice conversion implementation using Retrieval-based Voice Conversion

---

### 🚀 How to Run the Interactive Voice Call System

1. **Open the Interactive_Voice_Call_with_Famous_Actor.ipynb in Google Colab.**
2. **Set up your Gemini API key** (optional, but improves transcription accuracy):

    - Get your API key from [Google AI Studio](https://aistudio.google.com/app/apikey)
    - Add it to Colab secrets by clicking the key icon in the left sidebar
    - Create a new secret with name `GEMINI_API_KEY` and your API value

3. **Run the installation cells** to install the required dependencies.

4. **Initialize the system components** - Whisper, Gemma LLM, EdgeTTS, and Voice Converter.
   - The notebook uses Gemma 3 12B by default
   - If you encounter memory issues, you can reduce memory usage by changing:
     - Base model to: `unsloth/gemma-3-4b-it-unsloth-bnb-4bit`
     - Adapter path to: `lara1510/gemma-3-4b-lora`

5. **Launch the Gradio interface** and use the public link to start the conversation.

6. **Speak in Arabic** and the system will respond as Maguy Abou Ghosn.

---
### 🚀 How to Run the Voice Conversion (RVC)

1. **Download Maguy's voice model files**:
   - Get the model files from [Hugging Face](https://huggingface.co/lara1510/maguy-rvc-model/tree/main)
   - You'll need both the `.pth` model file and the `.index` file
2. **Open the RVC.ipynb in Google Colab.**
3. **Mount your Google Drive** to access model files.
4. **Install the Advanced-RVC-Inference package and dependencies.**
5. **Load Maguy's voice model files (.pth & .index)** from Google Drive or upload them directly.
6. **Initialize the VoiceConverter and launch the Gradio interface.**
7. **Record your voice and hear it transformed into Maguy's voice.**

---
### 📚 Colabs Used

**For Fine-Tuning Gemma 3:**
[![Colab](https://img.shields.io/badge/Colab-Fine_Tuning_Gemma3-blue?style=for-the-badge&logo=googlecolab)](https://colab.research.google.com/drive/1APBoaFOu3wSQ0So36Ywy0_0XYBtkBgOL)

**For RVC Training:**
[![Colab](https://img.shields.io/badge/Colab-RVC%20Training-blue?style=for-the-badge&logo=googlecolab)](https://colab.research.google.com/drive/106MklbvwvtxhhYS-RWoPLt6cM3UydQwO)

---
### 🔧 Implementation Challenges

The project faced several technical challenges that shaped our implementation approach:

1. **Model Integration:** Due to dependency conflicts, the RVC voice conversion component was implemented in a separate notebook
2. **Memory Constraints:** While Gemma 3 12B model demonstrated superior Lebanese dialect generation, we used the 4B variant for integration with other components due to GPU memory limitations
3. **Lebanese Dialect TTS:** No available TTS models specifically support Lebanese dialect, requiring a two-stage approach with standard Arabic TTS and voice conversion
4. **Processing Latency:** The complete pipeline introduces some latency in the conversation flow
---

### 📖 Technical Blog 
[![Blog](https://img.shields.io/badge/Blog-green?style=for-the-badge)](https://docs.google.com/document/d/1J6nGi1uhthOtjjDsdFo1wpmQly7amVwb/edit?usp=drive_link&ouid=114670945440585118955&rtpof=true&sd=true)
