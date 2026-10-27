# Text Summarization Using Transformers

## Overview

This project explores automatic text summarization using pretrained
transformer models and an extractive summarization algorithm.
The CNN/DailyMail dataset is used for experimentation.

## Objectives

- Generate abstractive summaries using pretrained BART.
- Evaluate summaries using ROUGE metrics.
- Implement extractive summarization using TextRank.
- Fine-tune BART on a small subset of CNN/DailyMail.
- Compare the summarization approaches.

## Methods

### 1. Original BART

Model: `facebook/bart-large-cnn`

BART generates new summaries from news articles. Long inputs are
truncated to fit the model's input limit.

### 2. TextRank

TextRank is an extractive method that selects important sentences
from the source article.

### 3. Fine-tuned BART

The pretrained BART model was fine-tuned on 200 training articles
for one epoch, with 30 validation examples used for validation.

This is a small-scale demonstration rather than a production model.

## Dataset

CNN/DailyMail version 3.0.0

Dataset source: `abisee/cnn_dailymail`

- 500 articles selected for the initial training subset.
- 100 articles selected for the initial test subset.
- 200 articles used for the fine-tuning experiment.
- 30 articles used for fine-tuning validation.

The fine-tuned model used a maximum input length of 512 tokens
and a maximum target length of 128 tokens.

## Evaluation

ROUGE-1, ROUGE-2, ROUGE-L and ROUGE-Lsum are used to measure
overlap between generated summaries and reference summaries.

The initial method comparison uses the same 10 test articles
for Original BART and TextRank. The fine-tuned model is also
evaluated on those 10 articles.

See `final_summarization_comparison.csv` and
`final_summarization_comparison.png` for the results.

## Results and Limitations

The evaluation sample contains only 10 articles, and the
fine-tuning experiment uses 200 training examples for one epoch.
Results are preliminary and should not be treated as a definitive
benchmark.

ROUGE measures text overlap and does not directly measure
factual correctness, readability, or usefulness.

## Project Outputs

- `bart_summarization_results.csv`
- `bart_rouge_scores.json`
- `bart_rouge_scores.png`
- `textrank_summarization_results.csv`
- `textrank_rouge_scores.json`
- `bart_vs_textrank_comparison.csv`
- `bart_vs_textrank_rouge.png`
- `final_summarization_comparison.csv`
- `final_summarization_comparison.png`

## Technologies

- Python
- Google Colab
- PyTorch
- Hugging Face Transformers
- Hugging Face Datasets
- Evaluate / ROUGE
- Sumy / TextRank
- Pandas
- Matplotlib

## Reproducibility

The experiment was developed in Google Colab. The notebook should
be included in the repository to document the complete workflow.

## Fine-Tuned Model

The fine-tuned BART model is hosted on Hugging Face:

[View the fine-tuned model](https://huggingface.co/stew29/bart-cnn-dailymail-finetuned)

The model was fine-tuned on a small subset of the CNN/DailyMail dataset for one epoch as an educational experiment. Evaluation was performed on a small test subset, so the results should be interpreted as preliminary rather than representative of full-dataset performance.

## Disclaimer

This project is for educational purposes. Summaries can omit
important context or contain inaccuracies and should be checked
when factual precision is important.
