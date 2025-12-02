# Legal Judgment Prediction for U.S. Appellate Courts

Evaluating LLM performance on predicting appellate court outcomes using district court rulings.

**Blog post:** [An Experiment in Legal Judgment Prediction](https://sgull.bearblog.dev/an-experiment-in-legal-judgement-prediction/)

## Key Findings

- GPT-5.1 achieved MCC 0.29 / F1 0.51 on 3-class prediction (AFFIRM/MIXED/REVERSE)
- Performance drops significantly without appeal arguments as input
- Using appellate opinion summaries inflates MCC to 0.67, demonstrating information leakage in prior LJP research

## Dataset

121 U.S. appellate cases (post-October 2024) sourced from CourtListener, filtered for:
- De novo review standards
- Sufficient district court reasoning
- Single docket (non-consolidated)

```
data/
├── {case_name}.yaml           # Case metadata + appeal reasons
├── {case_name}_ruling.txt     # District court opinion (model input)
└── appellate_rulings_parsed/  # Parsed appellate opinions
```

## Approaches Evaluated

| Approach | Input | Purpose |
|----------|-------|---------|
| Single-Stage | DC ruling + appeal reasons | Main evaluation |
| Single-Stage (no appeal reasons) | DC ruling only | Ablation |
| Two-Stage | DC ruling + appeal reasons | Reduce AFFIRM bias |
| Appellate Summary | Appellate opinion | Demonstrate leakage |

## Usage

The main analysis is in `ljp.ipynb`. Prompts are in `prompts/`.

## License

MIT
