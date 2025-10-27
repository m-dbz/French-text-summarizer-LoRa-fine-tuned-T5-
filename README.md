# T5-Base LoRA Fine-tuned for French Text Summarization

This model is a fine-tuned version of Google's T5-Base using LoRA (Low-Rank Adaptation) for French text summarization. It generates concise 3-5 sentence summaries from longer French texts. The target summaries were generated using Mistral-7B-Instruct-v0.2 as the annotation model. The goal is to achieve a similar performance using a much smaller model with fine-tuning. 

## Model Details

### Model Description

This model was fine-tuned using LoRA on a dataset of 5,000 French texts from the instruct_fr_novel19 dataset. The model uses parameter-efficient fine-tuning to adapt T5-Base specifically for French summarization tasks while maintaining only 0.79% trainable parameters (1.8M out of 225M total parameters).

### Model Source

- **Base Repository:** https://huggingface.co/google-t5/t5-base

## Training Details

### Training Data

The model was trained on 5,000 French texts selected from the [instruct_fr_novel19](https://github.com/opinionscience/InstructionFr/blob/main/public_domain/instruct_fr_novel19.json) dataset. The texts were chosen as the longest entries from the dataset, with summaries generated using Mistral-7B-Instruct-v0.2 as the annotation model.

Dataset split:
- Training: 80% (4,000 texts)
- Validation: 10% (500 texts)  
- Test: 10% (500 texts)

## Evaluation

### Testing Data & Metrics

The model was evaluated on the validation set using BERTScore, comparing the fine-tuned model against the base T5 model.

### Results

The fine-tuned model shows improvement over the base model. Quantitatively:

**Base T5 Model:**
- BERTScore F1: ~0.83

**Fine-tuned Model (with LoRA):**
- BERTScore F1: ~0.86

Qualitatively, the fine-tuning process demonstrates measurable improvement in generating French summaries that better align with reference summaries.

## LoRa Impact

Training was performed using LoRA for parameter-efficient fine-tuning, significantly reducing computational requirements compared to full fine-tuning.

- **Parameter efficiency:** Only 0.79% of parameters trained

## Requirements

- Transformers library
- PEFT (Parameter-Efficient Fine-Tuning)
- PyTorch
- BERTScore for evaluation
- Pandas
- PyTorch
