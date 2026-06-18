# 📘 ExamBuddy AI — Full Cost & Architecture Document

> **(Self-Hosted + Hybrid AI System)**

---

## 1. 🧠 Overview

ExamBuddy AI is a **self-hosted + hybrid AI education platform** that uses:

* LLM (Llama / Qwen) for core reasoning
* STT (Whisper) for voice input
* TTS (Edge / Piper) for voice output
* RAG (Vector DB) for textbook-based answers
* GPT API only as fallback

👉 Goal:
Deliver scalable AI learning at low cost per student.

---

## 2. 🏗️ System Architecture

### 🔄 Full Flow

```text
User (Voice/Text)
   ↓
API Gateway (FastAPI)
     ↓
STT (Whisper if voice input)
   ↓
Intent Router (decides - Cache / RAG / LLM / Fallback)
   ↓
RAG System (Vector DB retrieval)
   ↓
LLM (Llama / Qwen self-hosted)
   ↓
Fallback (GPT API only if needed)
   ↓
Response Formatter (ExamBuddy rules)
   ↓
TTS Engine (Edge / Piper)
   ↓
Audio / Text Output
```

---

## 3. ⚙️ Core Components

### 3.1 🧠 LLM Layer

* Model: Llama / Qwen (self-hosted)
* Runs on GPU servers
* Handles 80–90% queries

### Cost Driver:

* GPU inference time

---

### 3.2 🎙️ STT Layer

* Whisper / faster-whisper (self-hosted)
* Converts speech → text

### Cost Driver:

* CPU/GPU usage for audio processing

---

### 3.3 🗣️ TTS Layer

* Edge-TTS / Piper / Coqui
* Converts text → speech

### Cost Driver:

* CPU time per audio generation

---

### 3.4 📚 RAG System

* Vector DB: FAISS / Qdrant
* Stores NCERT + Tamil Nadu textbooks

### Cost Driver:

* Low (mostly storage + embeddings)

---

### 3.5 🔁 Fallback System

* GPT / cloud APIs
* Used only for complex queries

### Target usage:

* 5% – 10% of total traffic

---

## 4. 💰 Cost Structure

---

### 4.1 🧠 LLM Cost (BIGGEST COST)

| Scale              | Infrastructure | Monthly Cost |
| ------------------ | -------------- | ------------ |
| MVP (1K users)     | 1 GPU          | ₹25K – ₹50K  |
| Medium (10K users) | 2–4 GPUs       | ₹1L – ₹2L    |
| Large (100K users) | 6–12 GPUs      | ₹4L – ₹10L   |

---

### 4.2 🎙️ STT Cost

| Scale  | Cost        |
| ------ | ----------- |
| MVP    | ₹0 – ₹5K    |
| Medium | ₹5K – ₹20K  |
| Large  | ₹20K – ₹80K |

---

### 4.3 🗣️ TTS Cost

| Scale  | Cost        |
| ------ | ----------- |
| MVP    | ₹0 – ₹3K    |
| Medium | ₹3K – ₹15K  |
| Large  | ₹10K – ₹50K |

---

### 4.4 📚 RAG Cost

| Component             | Cost       |
| --------------------- | ---------- |
| Vector DB             | ₹2K – ₹15K |
| Embeddings (one-time) | ₹5K – ₹30K |
| Storage               | ₹1K – ₹10K |

---

### 4.5 🧩 Infrastructure Cost

| Scale  | Cost        |
| ------ | ----------- |
| MVP    | ₹5K – ₹10K  |
| Medium | ₹10K – ₹30K |
| Large  | ₹30K – ₹1L  |

---

### 4.6 🔁 Fallback API Cost

* Used only when self-hosted model fails

| Usage Level | Impact      |
| ----------- | ----------- |
| 5% traffic  | Low cost    |
| 10% traffic | Medium cost |
| 20% traffic | High cost   |

---

## 5. 📊 Total Monthly Cost

---

### 🟢 MVP (1,000 students)

👉 ₹30,000 – ₹70,000 / month

---

### 🟡 Medium Scale (10,000 students)

👉 ₹1,20,000 – ₹3,00,000 / month

---

### 🔴 Large Scale (100,000 students)

👉 ₹4,00,000 – ₹10,00,000 / month

---

## 6. 💰 Cost per Student

| Scale      | Cost / Student |
| ---------- | -------------- |
| 1K users   | ₹30 – ₹70      |
| 10K users  | ₹10 – ₹30      |
| 100K users | ₹4 – ₹10       |

---

## 7. 💰 Revenue Model

* Pricing: ₹199 / student / month

### Example (10,000 students):

* Revenue: ₹19,90,000 / month
* Cost: ₹1,50,000 – ₹3,00,000 / month

---

## 💡 Profit Margin:

👉 80% – 90% possible (with optimization)

---

## 8. 🔥 Key Cost Drivers

Ranked:

1. 🧠 LLM GPU inference (largest cost)
2. 🎙️ STT processing
3. 🗣️ TTS generation
4. ⚙️ Infrastructure + DB
5. 🔁 Fallback API usage

---

## 9. 🚀 Optimization Strategy

To reduce cost:

* Use Llama (not GPT for everything)
* Use Whisper locally
* Use Edge-TTS / Piper
* Aggressive caching
* Strict RAG filtering
* Reduce token length (without losing meaning)
* Limit fallback to <10%

---

## 10. 🧠 Key Insight

👉 Cost is NOT per student
👉 Cost is based on **GPU + compute usage**

So:

* More students ≠ direct cost increase
* More active usage = higher cost

---

## 11. 🏁 Final Conclusion

ExamBuddy AI is:

✔ Technically scalable
✔ Financially profitable
✔ Self-hostable
✔ Cloud-extendable
✔ Highly optimized for education workloads
