# Machine translation for songs (EN-TH)

## Introduction
- Motivation: Why is this task interesting or important?
- What other people have done? What models have previous work have used? What did they miss? (1-2 paragraph)
- Summarize your idea
- Summarize your results

## Approach/Methodology/Model
Explain your model here how it works.
- Input is ...
- Output is ...
- Model description
- Equation as neccessary e.g. $\alpha_3$

## Dataset
- Annotation guidelines
- Results total how many tokens, sentences, etc.
- Label distribution

| Label | Frequency |
|-------|-----------|
| good | 60% |
| bad | 40% |

## Experiment Setup
- Which pre-trained model? How did you pretrain embeddings?
- Computer. How long?
- Hyperparameter tuning? Dropout? How many epochs?

## Results
How did it go? + Interpret results.

## Model Comparison
| Model | Accuracy |
|-----------| ----------|
| fairseq | 46.7|
| **T5** | **55.7** |

| English Lyrics |We 40 deep in the lobby|
|-----------| ----------|
| Gold |เพราะเรามากัน40คนในล็อบบี้|
| Fairseq |เราดื่มเหล้ากันในล็อบบี้|
| T5 |เราอยู่ในล็อบบี้|
| SCB-MT |พวกเรา40ลึกลงไปในล็อบบี้|


## Conclusion
- What task? What did we do?
- Summary of results
