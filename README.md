# EmojiMood - IBM GenAI Emoji Generator

## 📋 Overview

EmojiMood is an AI-powered application that analyzes the sentiment of user input text and generates corresponding emoji representations. It combines transformer-based sentiment analysis with keyword-based emotion detection to create personalized emoji responses.

transformers>=4.53.0 torch>=2.6.0 gradio>=5.31.0 huggingface-hub>=0.30.0

Code

## 🚀 Installation & Setup

### 1. Install Required Packages

```bash
pip install transformers torch gradio
2. Run in Google Colab
The notebook is configured to run in Google Colab with:

GPU acceleration (T4 recommended)
Automatic package installation
Pre-configured environment variables
💻 Usage
Basic Text-to-Emoji Conversion
Python
from transformers import pipeline

# Initialize sentiment pipeline
sentiment_pipeline = pipeline("sentiment-analysis")

# Generate emojis for your text
input_text = "I'm really happy today!"
emojis = generate_emojis(input_text)
print(f"Your emoji mood: {emojis}")
Web Interface
Launch the interactive Gradio interface:

Python
import gradio as gr

def emoji_mood(input_text):
    emojis = generate_emojis(input_text)
    return emojis

gr.Interface(
    fn=emoji_mood, 
    inputs="text", 
    outputs="text",
    title="EmojiMood"
).launch()
🎨 Emoji Mapping
Sentiment-Based Mapping
Sentiment	Emojis
POSITIVE	😃 😊 😄 🤗 😍 ❤️ 🐣
NEGATIVE	😒 😕 😞 😢 😠 ❤️ 🐣
NEUTRAL	😐 😑 😶 🙄 🙃
Keyword-Based Emotion Detection
Keyword	Emojis
happy	😃 😊 😄 🤗
love	❤️ 😍 😘
angry	😠 😡 🤬
sad	😢 😞 😔
frustrated	😒 😤 🤬
excited	😜 😝 🤩
📊 Model Details
Base Model: DistilBERT (distilled version of BERT)
Training: Fine-tuned on SST-2 (Stanford Sentiment Treebank) dataset
Task: Binary text classification (Positive/Negative with Neutral support)
Inference Device: CUDA GPU (if available) or CPU fallback
🔄 Workflow
Code
User Input Text
    ↓
Sentiment Analysis (DistilBERT)
    ↓
Sentiment Classification (POS/NEG/NEU)
    ↓
Sentiment-based Emoji Selection
    ↓
Keyword Matching & Additional Emojis
    ↓
Merge & Deduplicate
    ↓
Output: Emoji String
📝 Example Usage
Python
# Example 1: Positive sentiment
generate_emojis("This is wonderful!")  # Output: 😊 🤗 😄

# Example 2: Negative sentiment
generate_emojis("I'm really upset")    # Output: 😞 😢 😒

# Example 3: Happy + Excited
generate_emojis("I'm so happy and excited!")  # Output: 😃 😜 🤗
⚙️ Configuration
GPU Setup (Google Colab)
Python
from torch import cuda
print(f"GPU Available: {cuda.is_available()}")
print(f"Device: {cuda.get_device_name(0) if cuda.is_available() else 'CPU'}")
Running Locally
For local execution, ensure you have:

NVIDIA GPU with CUDA 12.4+ (optional but recommended)
PyTorch with CUDA support
Sufficient disk space (~5GB for model downloads)
🐛 Troubleshooting
Common Issues
ImportError with llama_index: Use updated import paths

Python
from llama_index.core import SimpleDirectoryReader
Out of Memory (OOM): The model runs efficiently on T4 GPU but may need CPU offloading on smaller GPUs

Model Download Timeout: Set Hugging Face cache directory

bash
export HF_HOME=/path/to/cache
🔮 Future Enhancements
 Fine-tune model on emoji-specific datasets
 Multi-language support
 RAG integration for contextual emoji suggestions
 User preference learning
 API deployment on Hugging Face Spaces
 Mobile app integration
📄 License
This project is part of IBM's GenAI initiative. Please refer to the repository's main LICENSE file.

👤 Author
Created by: vivek-fjchx

🤝 Contributing
Contributions are welcome! Please feel free to submit pull requests for:

Bug fixes
New emoji mappings
Model improvements
Documentation enhancements
📚 References
Hugging Face Transformers
DistilBERT Model
Gradio Documentation
PyTorch
