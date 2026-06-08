---
title: "From Clinical Reality to AI-Ready Data"
categories: ["AI Engineering", "Medical Informatics"]
icon: "/assets/icons/structured.svg"
---

# From Clinical Reality to AI-Ready Data

In a previous article, [_What I Learned Building a Clinical Documentation System_](https://keikaavousi.com/blog/a-lesson-from-building-cis/), I described an unexpected lesson from healthcare software development.

Although the system provided structured fields for diagnoses, medications, treatment plans, and clinical observations, many physicians still preferred documenting most information in free-text notes.

At first, this seemed like a design problem.

Over time, it became clear that the real reason was much simpler: _clinical workflows prioritize patient interaction and efficiency over perfect data structures_.

Healthcare data is not messy because software engineers failed to structure it properly.

Healthcare data is messy because clinical reality itself is messy.

That observation eventually led me to another challenge:

> How can AI systems work effectively with information that was never designed for machines in the first place?

## The Gap Between Clinical Workflows and AI Systems

Modern AI systems perform best when data is consistent, structured, and predictable.

Clinical notes are often the opposite.

A single note may contain:

- abbreviations
- shorthand terminology
- incomplete sentences
- inconsistent formatting
- duplicated information
- physician-specific writing styles

For a clinician, interpreting this information is usually effortless.

For an AI system, these variations can significantly impact retrieval quality and downstream results.

Consider a simplified example:

```text
Pt c/o chest pain.
Hx HTN.
Metf 500mg daily.
```

Most healthcare professionals can immediately understand the meaning.

An AI system may not.

Before retrieval, embeddings, or language models become useful, the information often needs additional processing.

## Why I Focused on the Data Layer

One of the most common discussions in AI engineering revolves around models.

- Which LLM should be used?

- Which embedding model performs best?

- Which vector database scales better?

While these decisions matter, my experience has repeatedly shown that data quality frequently has a greater impact than model selection.

A sophisticated AI system built on inconsistent data will still produce inconsistent results.

A simpler system built on well-structured information often performs surprisingly well.

This became especially apparent when working with clinical documentation.

The challenge was not generating answers.

The challenge was creating a reliable representation of the information before retrieval even began.

## Building a Text Structuring Layer

Rather than forcing physicians to change how they document information, I became interested in a different approach:

Accept the reality of free-text documentation and improve the data after it is created.

This led to the design of a text structuring layer between clinical notes and downstream AI systems.

The goal was not to replace clinical judgment or fully automate interpretation.

The goal was to make unstructured information more consistent and searchable.

### Step 1: Cleaning the Input

The first step focused on removing unnecessary noise while preserving clinically relevant content.

This included:

- formatting inconsistencies
- duplicated fragments
- non-clinical metadata
- irrelevant text artifacts

The objective was simple:

Preserve meaning while reducing variability.

### Step 2: Normalizing Clinical Terminology

Medical documentation contains a large number of abbreviations and shorthand expressions.

For example:

| Raw Term | Normalized Term     |
| -------- | ------------------- |
| HTN      | Hypertension        |
| DM       | Diabetes Mellitus   |
| SOB      | Shortness of Breath |
| Metf     | Metformin           |

Although clinicians understand these terms instantly, normalization helps create a more consistent representation for search and retrieval systems.

### Step 3: Creating Structured Concepts

After normalization, terms can be mapped into meaningful categories.

For example:

```json
{
	"symptoms": ["chest pain"],
	"conditions": ["hypertension"],
	"medications": ["metformin"]
}
```

This structure is significantly easier to process than raw text alone.

More importantly, it creates a foundation for downstream AI applications.

## Preparing Data for Retrieval-Augmented Generation (RAG)

One of the most interesting applications of structured clinical information is Retrieval-Augmented Generation (RAG).

RAG systems rely heavily on the quality of the information they retrieve.

If the underlying data contains inconsistent terminology, duplicated concepts, or poorly structured notes, retrieval quality can suffer regardless of which language model is used.

By introducing a text structuring layer before indexing, retrieval systems can work with more consistent representations of clinical information.

In practice, improvements often appear in areas such as:

- retrieval relevance
- search consistency
- context quality
- knowledge organization

The result is not necessarily a smarter model. instead, it is a cleaner foundation that helps the model make better use of available information.

## An Important Lesson About AI Engineering

This project reinforced a lesson that extends beyond healthcare.

Many AI discussions focus on prompts, models, and frameworks.

Those components are important, but they are often not where the hardest problems exist.

In many real-world systems, the most valuable engineering work happens before the model is ever called.

- Data cleaning

- Normalization

- Knowledge organization

- Information retrieval

These layers rarely receive the same attention as large language models, yet they often determine the quality of the final outcome.

## Final Thoughts

The most interesting part of healthcare AI is not teaching machines to understand perfectly structured data.

It is helping machines work with the imperfect, messy, and highly human data produced during real clinical workflows.

Physicians should not have to document information for the convenience of an AI system.

Instead, AI systems should adapt to the realities of clinical practice.

For me, that shift in perspective has become one of the most valuable lessons from working at the intersection of software engineering, medical informatics, and AI.
