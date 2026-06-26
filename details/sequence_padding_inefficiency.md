# The Sequence Padding Inefficiency Barrier

In standard mini-batch training, sequences of varying lengths are padded to match the longest sequence. This introduces massive computational waste.

## The Problem
If a batch contains one 4096-token sequence and several 128-token sequences, the 128-token sequences must be padded with `[PAD]` tokens. The model still processes these padding tokens, wasting up to 50% of GPU compute time on empty tokens.

## Mitigation: Document Packing
Document Packing concatenates multiple short sequences together up to the model's maximum context length, separating them with end-of-sequence tokens. A specialized block-diagonal attention mask prevents attention from crossing sequence boundaries.

```mermaid
flowchart TD
    subgraph Padded Batch
        S1[Sequence 1: 128 tokens + 3968 PAD tokens]
        S2[Sequence 2: 4096 tokens]
    end
    subgraph Packed Batch
        Packed[Seq 1 (128) + Seq 2 (128) + Seq 3 (2048) ... concatenated to 4096]
    end
    PaddedBatch --> Waste[50% Compute Wasted]
    PackedBatch --> Efficient[~100% Compute Utilized]
```

[← Back to README](../README.md)
