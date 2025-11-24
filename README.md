# PII NER Submission — Anvit Kumar

**Files included**
- src/ : model training & prediction code
- scripts/ : data generation script
- out/dev_pred.json : model predictions on dev set (if present)

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

```text
pii-ner-assignment/
│
├── scripts/
│   └── generate_stt_data.py
│
├── src/
│   ├── dataset.py
│   ├── train.py
│   └── predict_and_postprocess.py
│
├── out/
│   └── distil_baseline/
│
├── data/
│   ├── train.jsonl
│   └── dev.jsonl
│
├── dev_pred.json
├── metrics.json
├── README.md
└── PII_NER_submission.zip
```


