# sargam_token_prediction

# Sargam-BERT: AI for Indian Classical Music Notation

Sargam-BERT is a deep learning project that leverages the power of the BERT model to understand the relationship between musical lyrics and Sargam, the Indian classical music notation system. The project provides two main functionalities:

1.  **Classification**: A fine-tuned model that can predict whether a given `sargam` sequence is a correct notation for a line of `lyrics`.
2.  **Generation/Correction**: A masked language model that can suggest the most probable sargam notes (`sa`, `re`, `ga`, etc.) to fill in a blank in a sargam sequence, based on the context provided by the lyrics.

This project serves as a powerful tool for musicians, students, and enthusiasts for validating and composing sargam notations.

## ✨ Key Features

-   **Lyric-Sargam Pair Classification**: Classifies if a sargam notation correctly matches the corresponding lyrics (True/False).
-   **Intelligent Note Suggestion**: Suggests missing sargam notes in a sequence using a masked language modeling approach.
-   **Pre-trained Multilingual Model**: Built on top of `google-bert/bert-base-multilingual-uncased`, allowing it to handle diverse, multilingual lyrics.
-   **Easy to Use**: A single script to handle data preparation, training, evaluation, and inference.
-   **Performance Evaluation**: Generates a confusion matrix and classification report to visualize model performance.

## ⚙️ How It Works

The project uses two different BERT-based models for its two distinct tasks:

1.  **Classifier Model (`BertForSequenceClassification`)**: This model is fine-tuned on a dataset of (lyrics, sargam) pairs. It learns to understand the contextual and semantic relationship between the two text inputs. The input is formatted as `[CLS] lyrics [SEP] sargam [SEP]`, and the model outputs a single prediction: `1` (correct match) or `0` (incorrect match).

2.  **Note Suggestion Model (`BertForMaskedLM`)**: This is a Masked Language Model. It's trained to predict missing tokens in a sequence. We leverage this by providing it with lyrics and a sargam sequence containing a `[MASK]` token (e.g., `sa sa ga ga ma ma [MASK]`). The model predicts the most likely tokens to fill the mask, which we then filter to only show valid sargam syllables.

## 🚀 Getting Started

### Prerequisites

-   Python 3.7+
-   PyTorch
-   Hugging Face Transformers

### 1. Clone the Repository

```bash
git clone [https://github.com/your-username/sargam-bert.git](https://github.com/your-username/sargam-bert.git)
cd sargam-bert
