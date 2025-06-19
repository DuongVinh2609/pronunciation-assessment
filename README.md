# Enhanced Pronunciation Assessment with Wav2Vec2 and BERT

This repository implements a **multi-level automatic pronunciation assessment system** using deep learning. The system leverages **Wav2Vec2** for speech representation and **BERT** for text encoding, enabling fine-grained scoring of utterances and words across multiple pronunciation dimensions.

## 🎯 Objective

To develop a robust and interpretable model that evaluates non-native speech based on:
- **Accuracy**
- **Fluency**
- **Completeness**
- **Prosody**
- **Overall pronunciation quality**

The model further predicts **word-level pronunciation scores** and identifies potential mispronunciations at the phoneme level.

## 🧠 Key Features

- **Wav2Vec2-based Acoustic Embedding**: Extracts contextual speech features from raw waveforms.
- **BERT-based Text Embedding**: Encodes reference transcripts for semantic alignment.
- **MFCC and Prosodic Features**: Combines handcrafted prosody (e.g., pitch, ZCR, pause ratio) with learned representations.
- **Phoneme-Level Analysis**: Segments utterances and evaluates timing and distortion per phoneme.
- **Transformer Encoder Architecture**: Models interdependencies among phoneme, word, and utterance representations.
- **Multi-task Learning**: Simultaneously predicts utterance-level and word-level scores.
- **Cross-modal Attention (optional)**: Aligns speech and text features in a shared latent space.

## 🗃️ Dataset & Preprocessing

This project uses the **[SpeechOcean762](https://www.speechocean.com/datacenter/details/142.html)** dataset — a large-scale corpus for non-native English pronunciation assessment. It includes audio from L2 English learners with diverse proficiency levels.

The model expects data in a **Kaldi-style format**:
- `wav.scp`, `text`, `utt2spk`, `lexicon.txt`, and `text-phone` mappings
- Audio at 16kHz, mono-channel, `.wav` format

Data preprocessing includes:
- Extracting **MFCCs**, **Wav2Vec2 embeddings**, **pitch contours**, and **phoneme durations**
- Computing **distortion metrics** between expected and actual phones
- Building structured feature tensors with masks

> Preprocessed data is saved in `.pt` format for efficient loading.

## ⚙️ Architecture Overview

- **Phone Encoder**: Projects (timing deviation, distortion) vectors into latent space.
- **Word Reconstructor**: Aggregates phones into word-level embeddings.
- **CLS Tokens**: Used to represent global utterance-level semantics.
- **Transformer Encoder**: Encodes token sequences with positional encodings.
- **Regression Heads**: Separate heads predict each pronunciation trait (accuracy, fluency, etc.).

## 🚀 Training

Run:

```python
if __name__ == "__main__":
    train_model(train_path, test_path, text_train_path, text_test_path, num_epochs=20)
```

- Uses `AdamW` optimizer with cosine annealing scheduler
- Supports early stopping and gradient clipping
- Saves the best model based on validation loss

## 📈 Evaluation

Evaluation includes:
- **Utterance-level metrics**: MAE, MSE, R², Pearson correlation
- **Word-level metrics**: Regression + classification (correct vs incorrect)
- **Confusion matrix** for binary correctness at word level

Results are visualized with `seaborn` and `matplotlib`.

## 🧪 Inference & Visualization

Use:
```python
run_inference(checkpoint_path, test_path, text_test_path)
display_inference_results(...)
evaluate_and_visualize(...)
```

Provides:
- Per-sample utterance scores
- Word-level correctness breakdown
- Comparative metrics between predicted and ground-truth scores

## 📚 Dependencies

- `torch`, `torchaudio`, `transformers`, `librosa`, `scikit-learn`
- `fastdtw`, `scipy`, `matplotlib`, `seaborn`

Install using:
```bash
pip install -r requirements.txt
```

## 📌 Notes

- This system is inspired by models like **GOPT** and **CALL** frameworks.
- Suitable for **Computer-Assisted Pronunciation Training (CAPT)** and **language learning applications**.

## 📜 License

MIT License.

## 📖 References

- [SpeechOcean762 Dataset](https://www.speechocean.com/datacenter/details/142.html)
- Microsoft Azure Speech Services - [Pronunciation Assessment API](https://learn.microsoft.com/en-us/azure/cognitive-services/speech-service/how-to-pronunciation-assessment)
- [Automatic Pronunciation Evaluation in CALL Systems](https://aclanthology.org/)
- [Wav2Vec2: Self-Supervised Learning of Speech Representations](https://arxiv.org/abs/2006.11477)
- [BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding](https://arxiv.org/abs/1810.04805)

## ✍️ Author

[Duong Vinh](https://github.com/DuongVinh2609)
