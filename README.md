# Official Repository of the Paper  
**MixRevDetect: Towards Detecting AI-Generated Content in Hybrid Peer Reviews**

This is the official repository for the paper **"MixRevDetect: Towards Detecting AI-Generated Content in Hybrid Peer Reviews"**. The increasing use of large language models (LLMs) in academic peer review processes has raised significant challenges in distinguishing AI-generated content from human-written feedback. This paper proposes **MixRevDetect**, a novel method for detecting AI-generated sentences in hybrid peer reviews, achieving an F1 score of **88.86%**, significantly outperforming existing AI text detection methods.

Our approach leverages a combination of tail pruning, GPT-4-based completion, and BERTScore for semantic similarity evaluation to accurately identify AI-generated content in peer reviews. This repository contains the code and datasets used to implement and evaluate the proposed method.

---

## Key Contributions

- **Novel Detection Method:** A new approach for detecting AI-generated content in hybrid peer reviews that combines both AI and human feedback.
- **Tail Pruning and Completion:** The method uses a review pruning technique and GPT-4 to generate completions for truncated review comments.
- **High-Accuracy Results:** Our method achieves an **F1 score of 88.86%**, setting a new benchmark in the detection of AI-generated peer review content.

---

## Repository Structure

This repository contains the following directories and files:

### `data/`
- Contains datasets with AI and human sentences at different truncation ratios (0.1, 0.3, 0.5, 0.7, 0.9).

### `src/`
- **`extracting_sentences.ipynb`**: Extract sentences from the dataset.
- **`bertscore_edit_distance.ipynb`**: Calculate BERTScore and Levenshtein distance between human and AI sentences.
- **`evaluation.ipynb`**: Train and evaluate the model using BERTScore and Edit Distance metrics.

---

## Methodology

The methodology in **MixRevDetect** can be summarized as follows:

1. **Tail Pruning:** Each review comment is divided into smaller segments. Tail pruning is applied to simulate incomplete information by removing a portion of each sentence (based on a pruning ratio). The pruned sentences are then passed through a language model for completion.

2. **Completion with GPT-4:** For each tail-pruned sentence, we use GPT-4 to generate the missing content. The pruned review comment, along with the relevant research paper, is used as input to the model, which completes the review comment.

3. **Similarity Evaluation:** The similarity between the generated completion and the tail-pruned sentence is evaluated using **BERTScore**, which measures the semantic similarity between two texts using contextual embeddings from BERT. This results in precision, recall, and F1 score metrics.

4. **Classification:** A classifier is trained to differentiate between AI-generated and human-written sentences. The features for this classifier include BERTScore precision and recall, and the classifier uses a sigmoid activation function to predict whether a sentence is human-written or AI-generated.

---
