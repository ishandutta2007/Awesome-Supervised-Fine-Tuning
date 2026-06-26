# Process-Oriented Reasoning SFT

Process-Oriented Reasoning SFT focuses on teaching models *how to think* step-by-step, rather than just matching a final outcome.

## Concept
In process-oriented training, intermediate steps (reasoning traces) are generated and evaluated. Models are trained on data where each logical step is explicitly laid out and verified. This serves as a critical "cold-start" alignment phase for reasoning architectures prior to RL optimization.

```mermaid
flowchart TD
    Prompt[Problem Prompt] --> Step1[Step 1: Initial Logic]
    Step1 --> Verify1[Verify Step 1]
    Verify1 --> Step2[Step 2: Sub-problem Resolution]
    Step2 --> Verify2[Verify Step 2 / Self-Correct]
    Verify2 --> Step3[Step 3: Final Output]
    Step3 --> TrainData[Save Step-by-Step Chain of Thought]
    TrainData --> ModelSFT[Tuning the Model]
```

[← Back to README](../README.md)
