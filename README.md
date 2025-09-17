# 🎬 AI-Powered Video Content Analyzer

![LangChain](https://img.shields.io/badge/LangChain-0086CB?style=for-the-badge&logo=langchain) ![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai) ![FAISS](https://img.shields.io/badge/FAISS-0080FF?style=for-the-badge) ![Python](https://img.shields.io/badge/Python-3.10-blue?style=for-the-badge&logo=python)

Hey there! Welcome to my Video Content Analyzer project. I wanted to build something that could "watch" and "listen" to a video and then answer questions about it. This project is my exploration into the world of **multimodal AI**, where I combine different models to understand video, audio, and text.

This entire project is built within a single Jupyter Notebook and demonstrates how to create a simple but powerful tool that can transcribe the audio of a video, analyze its visual frames, and create a searchable knowledge base to answer user questions.

---

### 🤔 The Goal: Making Videos Searchable

I've always found it hard to find specific information within a long video. You either have to skim through it manually or rely on timestamps. My goal was to create a system where you could just ask a question in plain English and get an answer based on the video's content, both spoken and visual.

This is essentially a **Retrieval-Augmented Generation (RAG)** system for video content.

---

### ✨ Core Features I've Implemented

1.  **Audio Transcription**:
    -   I used **OpenAI's Whisper model** to automatically extract and transcribe the entire audio track from a video file. This turns all the spoken content into searchable text.

2.  **Visual Frame Analysis**:
    -   I created a process to capture frames from the video at regular intervals (e.g., every 5 seconds).
    -   Each frame is then analyzed by **OpenAI's GPT-4 Vision model**, which generates a rich text description of what's happening visually in that frame.

3.  **Unified Knowledge Base**:
    -   I combined both the audio transcripts and the visual frame descriptions into a single, unified text corpus.
    -   This text is then split into smaller, manageable chunks suitable for a RAG system.

4.  **Semantic Search with a Vector Store**:
    -   I converted all the text chunks into numerical embeddings using OpenAI's embedding models.
    -   These embeddings are stored in a **FAISS vector store**, creating an in-memory semantic search engine for the video's content.

5.  **Question Answering**:
    -   Finally, I built a simple QA chain. When a user asks a question, the system finds the most relevant text chunks (from both audio and visuals) and uses a powerful LLM to generate a comprehensive answer based on that context.

---

### 🛠️ Tech Stack

-   **Core AI Framework**: LangChain
-   **Models**: OpenAI (Whisper for audio, GPT-4 Vision for images, GPT-4 for text generation, Text Embeddings)
-   **Vector Store**: FAISS (CPU version)
-   **Video/Audio Processing**: `moviepy`, `pydub`
-   **Notebook Environment**: Jupyter

---

### ⚙️ Setup and Installation

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/jsonusuman351/video-content-analyzer.git](https://github.com/jsonusuman351/video-content-analyzer.git)
    cd video-content-analyzer
    ```

2.  **Create and activate a virtual environment:**
    ```bash
    # It is recommended to use Python 3.10 or higher
    python -m venv venv
    .\venv\Scripts\activate
    ```

3.  **Install the required packages:**
    Since I developed this in a Jupyter Notebook, there isn't a `requirements.txt` file. You can install all the necessary libraries by running this command:
    ```bash
    pip install langchain langchain-openai openai faiss-cpu moviepy pydub jupyter python-dotenv
    ```
    You will also need to install **FFmpeg**, which is a dependency for `pydub` and `moviepy`. You can download it from the [official FFmpeg website](https://ffmpeg.org/download.html) and add it to your system's PATH.

4.  **Set Up Your Environment:**
    -   You will need to **provide your own MP4 video file** to analyze. Place it in the same directory as the notebook.
    -   You also need to **securely provide your OpenAI API key**. The notebook uses `dotenv`, so create a file named `.env` in the root directory and add your key:
        ```env
        OPENAI_API_KEY="your-openai-api-key"
        ```

---

### 🚀 How to Use This Project

The entire workflow is contained within the Jupyter Notebook.

1.  **Launch Jupyter:**
    Make sure your virtual environment is active, then run:
    ```bash
    jupyter notebook
    ```
2.  **Open the Notebook:**
    In the Jupyter interface that opens in your browser, click on `video_analyzer.ipynb`.
3.  **Update the Video Path:**
    Before running, make sure to update the notebook cell that specifies the video file to point to your own document.
4.  **Run the Cells:**
    You can run each cell sequentially to see the entire process.

---

### 🔬 A Tour of the Notebook

I've organized this entire project into a single Jupyter Notebook to make it easy to follow the journey from video input to AI-powered answers.

<details>
<summary>Click to view the code layout</summary>

```
video-content-analyzer/
│
└── video_analyzer.ipynb    # The complete end-to-end workflow is in this single notebook
```
</details>

---

---
