# PII NER Submission — Anvit Kumar

**Files included**
- src/ : model training & prediction code
- scripts/ : data generation script
- out/dev_pred.json : model predictions on dev set (if present)
- IIT Madras assignment PDF (uploaded): /mnt/data/IIT Madras __ Assignment 2025 (1).pdf
- metrics.json : final PII precision/recall/F1 on dev set
- README.md : this file

**Contact / Submission form fields**  
Email: anvitkumars2001@gmail.com

## Model & tokenizer
- Model: distilbert-base-uncased (DistilBERT)
- Tokenizer: DistilBERT fast tokenizer (HuggingFace AutoTokenizer)
- Head: token classification head (num_labels = token classes)

## Key hyperparameters
- epochs = 2
- batch_size = 8
- data collator = DataCollatorForTokenClassification (pads labels)

## Final metrics (dev)
{
  "TP": 126,
  "FP": 0,
  "FN": 0,
  "precision": 1.0,
  "recall": 1.0,
  "f1": 1.0
}

## How to run
1. Open the Colab notebook (PII_NER_Colab_Beginner.ipynb).
2. Run cells in order. The trained model is saved to out/distil_baseline.
3. Predictions written to out/dev_pred.json
4. For latency run: python src/measure_latency_simple.py --model_dir out/distil_baseline --input data/dev.jsonl --runs 50

## Loom script (what to say)
- Final results: PII precision 1.0, recall 1.0, F1 1.0.
- Code base: src/ contains dataset conversion, train.py, predict_and_postprocess.py, eval_span_simple.py
- Model: distilbert-base-uncased with token classification head
- Key hyperparameters: epochs=2, batch_size=8; DataCollatorForTokenClassification used for label padding
- Latency: run measure_latency_simple.py for p50/p95 on your CPU
- Demo: run a short demo showing one input and model predicted spans