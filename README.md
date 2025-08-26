# 🎬 Automatic Chapter Generation for Hindi-English YouTube Videos

URL: [![Paper](https://img.shields.io/badge/Research%20Paper-JISEM%202024-blue)](https://jisem-journal.com/index.php/journal/article/view/12505)

## 📌 Overview
This repository contains the code, dataset pipeline, and methodology used in our **published research paper**:  
**“Automatic Chapter Generation for Hindi-English YouTube Videos”** (*Journal of Information Systems Engineering and Management, 2024, 9(4s)*).

The project introduces the **first documented attempt** at building an **automatic chaptering system for Hinglish (Hindi-English code-switched) YouTube videos**, addressing a major gap in multilingual video accessibility.



---

## 🏆 Key Contributions
- 📂 **Dataset Creation**: Curated a **20GB medium-scale dataset (437 videos)** featuring natural Hindi-English code-switching (podcasts, educational, discussion videos).
- 🧠 **Novel Pipeline**:
  - **Whisper Medium (ASR)** → Transcribe bilingual speech with timestamps.  
  - **Preprocessing** → Clean filler words, normalize structure.  
  - **mBART Summarization** → Generate refined summaries (in English).  
  - **KeyBERT** → Extract concise, topic-representative titles.  
  - **Dynamic Chapter Merging** → Maintain 5–10 min coherence.  
- 📊 **Evaluation**:
  - BLEU Score = **1.64** (title-summary relevance).  
  - Flesch Reading Ease = **25.06** (academic-level readability).  
  - Avg. chapter length = **~4.7 minutes**.  
  - Human Evaluation = **2.75/5** (relevance & informativeness).  
- 🌍 **Impact**: Improves navigability of Hinglish videos, supports Indian content creators, and lays foundation for inclusive multilingual AI tools.

---
## 🔊 Flask Web Application – Chaptify
Alongside the research, I built a **Flask-based web application** to implement this pipeline practically.

### ⚡ Chaptify – YouTube Video Chaptering & Summarization Tool
Chaptify is an AI-powered Flask web application that takes a YouTube video URL and **automatically generates meaningful chapter-wise summaries and titles** from spoken Hindi or Hinglish content.  

🔹 **Features**:  
- Accepts **YouTube video URL** as input.  
- Uses **OpenAI Whisper** for ASR transcription.  
- Summarizes Hinglish segments with **mBART**.  
- Generates short, relevant titles using **KeyBERT**.  
- Outputs clean, timestamped **JSON files** for easy indexing and navigation.  

👉 Repository Link: [Chaptify – Flask App](https://github.com/avanigupta06/Chaptify)

---

## 🛠️ Methodology
1. **Video & Audio Processing**  
   - Extract audio using `pytube` + `ffmpeg`.  
   - Generate transcripts with **Whisper ASR**.  

2. **Transcript Cleaning & Refinement**  
   - Remove disfluencies, filler words, and artifacts.  
   - Normalize sentences for readability.  

3. **Chaptering & Summarization**  
   - Split segments using pauses, tone shifts, and semantic embeddings.  
   - Summarize with **mBART**, translate Hinglish → English.  

4. **Title Generation**  
   - Apply **KeyBERT** for concise, representative titles.  

5. **Unified Output Format**  
   ```json
   {
     "start_time": "00:10:32",
     "title": "Impact of Technology in Education",
     "summary": "This segment discusses how technology is transforming classrooms..."
   }
