# Question Answeing

This repository contains is implementation of Question Answering use case.

# README

## Finetuning distilbert-base-uncased for Question Answering Downstream task

This repository contains code for finetuning the distilbert/distilbert-base-uncased on Question Answering task with a dataset consisting of questions posed by crowdworkers on a set of Wikipedia articles.

### Task
- **Question Answering**: The task involves Answering the questions, based on the context.

### Model
- **google/t5-small**: DistilBERT, a model within the Transformers framework, is designed to be more compact and efficient compared to BERT. It underwent pretraining on the same dataset using a self-supervised approach, where the BERT base model served as its guiding "teacher." This entailed training solely on raw textual data without any human annotations, thereby enabling the utilization of extensive publicly accessible datasets.

### Dataset
- **Dataset**: The dataset used is Truncated version of Squad dataset. Squad is a dataset designed for reading comprehension tasks. It comprises questions crafted by crowdsourced workers based on a collection of Wikipedia articles. Each question is formulated such that the answer can be found within a specific segment of text, known as a span, from the corresponding passage. Additionally, some questions may be unanswerable based on the provided passages.

### Libraries Used
- `transformers`: For utilizing and fine-tuning the Roberta-base model.
- `huggingface-hub`: For accessing the model and tokenizer from the Hugging Face model hub.
- `datasets`: For handling and processing the dataset.
- `numpy`: For numerical computations.
- `torch`: For building and training neural networks.

### Training Details
- **Pretrained Model**: distilbert-base-uncased
- **Weight Decay**: 0.01
- **Learning Rate**: 2e-5
- **Batch Size**: 32
- **Number of Epochs**: 10

### Results 

Here's the provided data formatted into a tabular format:

| Training Loss | Epoch | Step | Validation Loss |
|---------------|-------|------|-----------------|
| No log        | 1.0   | 65   | 3.4665          |
| No log        | 2.0   | 130  | 2.8392          |
| No log        | 3.0   | 195  | 2.4838          |
| No log        | 4.0   | 260  | 2.3667          |
| No log        | 5.0   | 325  | 2.3424          |
| No log        | 6.0   | 390  | 2.2847          |
| No log        | 7.0   | 455  | 2.3560          |
| 2.1356        | 8.0   | 520  | 2.3636          |
| 2.1356        | 9.0   | 585  | 2.3655          |
| 2.1356        | 10.0  | 650  | 2.3978          |

Each row represents a different step or epoch, and the corresponding values are placed under their respective columns.

### Usage
```
from transformers import pipeline

question = "What is rama's friend name?"
context = "My name is rama. My friend name is raju."

question_answerer = pipeline("question-answering", model="likhith231/distilbert-base-uncased-finetuned-squad")
question_answerer(question=question, context=context)


```
