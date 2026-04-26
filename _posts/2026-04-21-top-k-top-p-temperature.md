---
title: "Top-k, Top-p, and Temperature in LLMs Explained Simply"
categories: AI
---

When working with large language models, you’ll often hear three terms: **temperature**, **top-k**, and **top-p (nucleus sampling)**.

They all control one thing:

> How the model chooses the next word from a set of possibilities.

Even though the model calculates probabilities, these settings decide how that probability is used.



## Temperature: How “random” the model is

Temperature controls how confident or creative the model is when picking the next token.

- Low temperature : more predictable, repetitive, stable
- High temperature : more diverse, creative, sometimes risky

### Simple intuition

Imagine the model predicts next words like this:


"coffee":

```text
morning : 0.70
evening : 0.20
moon : 0.10
```

### Low temperature (e.g. 0.2)

The model almost always picks:


morning


### High temperature (e.g. 1.0+)

Now it might pick:


morning / evening / moon


Even low-probability choices become more likely.

### Example

Prompt:

```text
Write a short sentence about coffee.
```

Low temperature output:

```text
I drink coffee every morning.
```

High temperature output:

```text
Coffee tastes like warm memory in a quiet room.
```

Same prompt. Different behavior.



## Top-k: Limit to top K options

Top-k sampling restricts the model to only the **K most likely tokens**.

Instead of considering all possibilities, it trims the list.

### Example

Probabilities:

```text
morning: 0.40
evening: 0.25
night: 0.20
moon: 0.10
banana: 0.05
```

If **top-k = 3**, only these are allowed:


morning, evening, night


Everything else is ignored.

### Effect

- Reduces weird outputs
- Keeps responses more focused
- Still allows some randomness



## Top-p (Nucleus Sampling): Probability cutoff

Top-p is more dynamic.

Instead of picking a fixed number of tokens, it selects the smallest set whose total probability reaches **p**.

### Example

Probabilities:

```text
morning: 0.40
evening: 0.25
night: 0.20
moon: 0.10
banana: 0.05
```

If **top-p = 0.80**, we include:

```text
morning (0.40)
evening (0.25)
night (0.20)
```

Total = 0.85 : stop here

So only these tokens are considered.

### Why it’s useful

- Adapts to context automatically
- More flexible than top-k
- Common in modern LLM systems



## How they work together

In practice, these are often combined:

- Temperature adjusts randomness
- Top-k limits candidate size
- Top-p filters by probability mass

Think of it like a funnel:

```text
All tokens
↓ 
top-k / top-p filters
↓ 
Filtered tokens
↓ 
temperature reshapes probability
↓ 
Final sampling choice
```



## Real-world behavior example

Prompt:

```text
Explain what programming is in one sentence.
```

### Low temperature + top-p

```text
Programming is the process of writing instructions for a computer to follow.
```

### High temperature + top-p

```text
Programming is like teaching a machine how to think through structured language.
```

### Higher randomness

```text
Programming is a way humans whisper logic into machines using code.
```

Same meaning direction — different expression styles.



## When to use what

Not rules, just intuition:

- **Temperature 0–0.3**
  - factual answers
  - code generation
  - structured outputs

- **Temperature 0.7–1.0**
  - writing
  - brainstorming
  - explanations

- **Top-k 1-100 (sometimes up to 200+)**
  - avoids extreme randomness

- **Top-p 0-1.0**
  - general-purpose control, usually preferred



## Final intuition

You are not changing what the model *knows*.

You are changing:

> how far it is allowed to explore its probability space before choosing a word.

That’s the real power of these parameters.