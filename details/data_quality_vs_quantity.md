# The Data Quality vs. Quantity Dilemma

Early alignment strategies focused on scaling up dataset sizes (e.g., millions of training examples). However, recent research indicates that high-quality data is far superior.

## Concept
The "Less Is More for Alignment" (LIMA) paper demonstrated that training on a small subset (e.g., 1,000 to 10,000 instances) of highly curated, clean, and diverse prompt-response examples produces alignment competitive with models trained on massive, noisy datasets.

```mermaid
flowchart TD
    subgraph Mass Scaling (Noisy)
        NoisyData[1,000,000 noisy samples] --> Train1[Full Parameter SFT]
        Train1 --> Model1[Repetitive / Low-quality alignment]
    end
    subgraph Quality Scaling (Curated)
        CuratedData[10,000 clean, diverse samples] --> Train2[Curated SFT]
        Train2 --> Model2[State-of-the-Art aligned model]
    end
```

## Mitigation
Move away from raw crowd-sourced data toward algorithmic scoring filters, perplexity pruning, and structural schema validation to retain only the highest-quality tokens.

[← Back to README](../README.md)
