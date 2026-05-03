---
title: "Single-Shot vs Few-Shot Prompting"
categories: ["AI"]
icon: "/assets/icons/prompting.svg"
---

Prompting LLMs usually falls into two practical styles: single-shot and few-shot. The difference is simple, but the impact on output quality and behavior can be huge.

## Single-Shot Prompting

Single-shot prompting gives the model only one instruction (or sometimes no example at all) and expects it to generalize. It relies heavily on the model’s pre-trained knowledge and your ability to describe the task clearly.

It works best when:

- The task is well-defined
- The output format is structured
- You want minimal overhead and fast iteration

But it can fail when the task is ambiguous or requires specific patterns the model hasn’t strongly inferred.

### Example

You give one instruction, no examples:

```text
Classify the sentiment of this sentence as Positive, Negative, or Neutral.

Sentence: "I waited 40 minutes for the bus and it never came."
```

Expected output: Negative

Here, the model relies only on the instruction and its internal understanding of sentiment.

## Few-Shot Prompting

Few-shot prompting provides multiple examples of input-output pairs. Instead of just telling the model what to do, you show it how to do it.

This improves consistency because the model starts to detect patterns:

- Input and Output structure becomes clearer
- Edge cases are implicitly demonstrated
- Output style becomes more stable

However, it also increases prompt size and can introduce bias if examples are poorly chosen.

### Example

Now you provide a few examples before the actual task:

```text
Classify the sentiment as Positive, Negative, or Neutral.

Sentence: "I love this phone, it works perfectly."
Sentiment: Positive

Sentence: "The app keeps crashing every time I open it."
Sentiment: Negative

Sentence: "The weather is okay today."
Sentiment: Neutral

Sentence: "I waited 40 minutes for the bus and it never came."
Sentiment:
```

Expected output: Negative

## Key Trade-off

Single-shot is about **clarity and precision**.  
Few-shot is about **pattern reinforcement and stability**.

In practice, good prompt engineering is not choosing one over the other; it’s knowing when the model needs guidance versus when it can generalize on its own.

The better you understand the task, the fewer examples you actually need.
