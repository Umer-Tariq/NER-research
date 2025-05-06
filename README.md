# Neural Architectures for Named Entity Recognition

This repository contains the implementation and evaluation of various neural network architectures for Named Entity Recognition (NER) on the Few-NERD dataset.

## 📋 Overview

Named Entity Recognition (NER) is a fundamental task in natural language processing that involves identifying and classifying entities in text. This project presents a comprehensive comparison of multiple neural network architectures for NER.

## 🔍 Models Evaluated

We evaluated five neural architectures with increasing complexity:

1. **SimpleRNN**: A baseline model with a unidirectional RNN layer
2. **LSTM**: Leveraging LSTM cells to better capture long-range dependencies
3. **Bi-RNN**: A bidirectional RNN to incorporate both left and right context
4. **Bi-LSTM**: Combining bidirectional processing with LSTM cells
5. **BERT**: A pre-trained transformer-based model with contextual representations

## 📊 Results

Here's a summary of our experimental results on the Few-NERD test set:

| Model | Precision | Recall | F1-score |
|-------|-----------|--------|----------|
| BERT | **0.9497** | **0.9496** | **0.9496** |
| Bi-LSTM | 0.9320 | 0.9311 | 0.9313 |
| Bi-RNN | 0.9220 | 0.9240 | 0.9227 |
| LSTM | 0.9120 | 0.9115 | 0.9110 |
| SimpleRNN | 0.9040 | 0.8994 | 0.9008 |

Key findings:
- **Performance Progression**: Our experiments demonstrate a clear progression in performance from simpler to more advanced architectures
- **Bidirectionality**: Bidirectional architectures consistently outperform unidirectional ones
- **Contextual Representations**: BERT's pre-trained contextual representations significantly enhance performance, especially for challenging entity types
- **Entity Type Analysis**: The performance gap between architectures is more pronounced for difficult entity types

## 🏗️ Model Architectures

### SimpleRNN
- Embedding layer (dimension = 100)
- Unidirectional RNN layer (hidden dimension = 256)
- Dropout layer (rate = 0.5)
- Linear layer for classification

### LSTM
- Embedding layer (dimension = 100)
- Unidirectional LSTM layer (2 layers, hidden dimension = 256)
- Dropout layer (rate = 0.5)
- Linear layer for classification

### Bi-RNN
- Embedding layer (dimension = 100)
- Bidirectional RNN layer (2 layers, hidden dimension = 256)
- Dropout layer (rate = 0.5)
- Linear layer for classification (input size = 2 * hidden dimension)

### Bi-LSTM
- Embedding layer (dimension = 100)
- Bidirectional LSTM layer (2 layers, hidden dimension = 256)
- Dropout layer (rate = 0.5)
- Linear layer for classification (input size = 2 * hidden dimension)

### BERT
- Pre-trained BERT-base-cased model (12 layers, 768 hidden size)
- Token classification head (linear layer)

## 📈 Performance by Entity Type

BERT consistently outperforms all other models across all entity types. The performance gap is particularly significant for challenging entity types.

| Entity Type | BERT | Bi-LSTM | Bi-RNN | LSTM | SimpleRNN |
|-------------|------|---------|--------|------|-----------|
| TAG_0 (Non-entity) | **0.9807** | 0.9736 | 0.9709 | 0.9700 | 0.9666 |
| TAG_1 | **0.8347** | 0.7756 | 0.7080 | 0.6835 | 0.6312 |
| TAG_2 | **0.7665** | 0.7224 | 0.6994 | 0.5491 | 0.5220 |
| TAG_3 | **0.7759** | 0.7313 | 0.7139 | 0.6387 | 0.6022 |
| TAG_4 | **0.8596** | 0.8118 | 0.7968 | 0.7537 | 0.7256 |
| TAG_5 | **0.8111** | 0.7560 | 0.7262 | 0.6636 | 0.6376 |
| TAG_6 | **0.7604** | 0.6840 | 0.6225 | 0.5868 | 0.5299 |
| TAG_7 | **0.9286** | 0.8555 | 0.8408 | 0.8049 | 0.8014 |
| TAG_8 | **0.7703** | 0.6653 | 0.5904 | 0.5742 | 0.4226 |

## 💾 Dataset

We conducted our experiments using the [Few-NERD dataset](https://paperswithcode.com/dataset/few-nerd), a large-scale, fine-grained named entity recognition dataset with:
- 188,200 sentences
- 491,711 entities
- 4,601,223 tokens
- 8 coarse-grained entity types
- 66 fine-grained entity types

## 💡 Recommendations

Based on our results, we recommend:

- For high-performance NER systems with sufficient computational resources, BERT or other pre-trained transformer models should be used.
- For resource-constrained environments, Bi-LSTM provides a good balance between performance and efficiency.
- For extremely resource-limited scenarios, even a simple Bi-RNN can achieve reasonable performance, especially for common entity types.



## 📚 References

- Ding, N., Xu, G., Chen, Y., Wang, X., Han, X., Xie, P., Zheng, H., & Liu, Z. (2021). Few-NERD: A Few-shot Named Entity Recognition Dataset.
- Devlin, J., Chang, M.-W., Lee, K., & Toutanova, K. (2019). BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding.
- Hochreiter, S., & Schmidhuber, J. (1997). Long Short-Term Memory.
- Graves, A., & Schmidhuber, J. (2005). Framewise phoneme classification with bidirectional LSTM and other neural network architectures.
- Elman, J. L. (1990). Finding structure in time.

