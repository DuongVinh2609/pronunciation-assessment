# Pronunciation Assessment Model

This repository contains a Google Colab-based implementation of an **automatic pronunciation assessment** system using Microsoft's **Azure Speech Services**. The model provides multi-level feedback on spoken language input by evaluating various dimensions of pronunciation quality.

## 🎯 Objective

The primary objective of this project is to evaluate the **pronunciation proficiency** of a speaker by comparing their spoken input to a reference text. The system returns detailed feedback across several linguistic dimensions and hierarchical levels, including:

- **Overall accuracy**
- **Completeness**
- **Fluency**
- **Phoneme-level and word-level correctness**
- **(Optional) Prosody metrics** such as rhythm, intonation, and stress

## 🧠 Key Features

- **Azure Integration**: Interfaces with Azure's Speech SDK to process spoken input and retrieve rich assessment results.
- **Multi-level Scoring**: Returns evaluation at the utterance, word, syllable, and phoneme levels.
- **Configurable Modes**: Supports both *scripted* and *unscripted* pronunciation assessment tasks.
- **Real-time Analysis**: Capable of working with audio from microphone input or pre-recorded files.
- **Output Format**: Outputs detailed JSON structures including scores and phonetic error analysis.

## ⚙️ Technologies Used

- Programming Language: **Python**
- Runtime Environment: **Google Colab**
- Speech Engine: **Azure Cognitive Services - Speech SDK**
- File Parsing and Processing: `nbformat`, `json`, `matplotlib` (for visualization)

## 📝 Getting Started

### 1. Clone or open the notebook

You may open the notebook directly via [Google Colab](https://colab.research.google.com/) or clone this repository locally.

### 2. Install dependencies

```python
!pip install azure-cognitiveservices-speech nbformat
```

### 3. Set up Azure credentials

Replace the placeholders with your actual Azure API credentials:

```python
speech_key = "YOUR_AZURE_SPEECH_KEY"
service_region = "YOUR_SERVICE_REGION"
```

### 4. Configure the reference text and audio input

Provide a target sentence for pronunciation and either:
- Record audio via microphone
- Upload an audio file in `.wav` format (mono, 16kHz recommended)

### 5. Run the evaluation pipeline

Execute the remaining cells to:
- Send audio to Azure Speech API
- Receive pronunciation feedback in structured JSON
- Visualize scores (optional)

### 6. Optional: Enable Prosody Scoring

```python
enable_prosody = True
```

This enables feedback related to **intonation**, **stress patterns**, and **speech rhythm**.

## 📂 Project Structure

```
.
├── Pronunciation_assessment_model.ipynb    # Main notebook
├── README.md                               # Project documentation
└── [optional files: audio samples, helper scripts, configs]
```

## 📊 Sample Evaluation Output

Each evaluation returns:

- **OverallScore**: Composite score based on pronunciation accuracy
- **Word-level feedback**: Correctness, stress, timing
- **Phoneme-level feedback**: Mispronunciation detection, substitution, omission
- **(Optional) Prosody**: Evaluation of suprasegmental features

## 🔬 Potential Applications

- Computer-Assisted Language Learning (CALL) systems
- English pronunciation training for non-native speakers
- Automated speaking assessments (e.g., TOEFL, IELTS practice tools)
- Research on speech intelligibility and accent detection

## 📚 References

- Microsoft Azure Speech Services - [Pronunciation Assessment API](https://learn.microsoft.com/en-us/azure/cognitive-services/speech-service/how-to-pronunciation-assessment)
- [Automatic Pronunciation Evaluation in CALL Systems](https://aclanthology.org/)
- Suprasegmental analysis using speech prosody models in L2 evaluation

---

> *For academic use, please cite or acknowledge the use of Azure’s Pronunciation Assessment API as the core speech engine.*

---

**Author**: [Duong Vinh](https://github.com/DuongVinh2609)  
**License**: MIT License (unless otherwise specified)
