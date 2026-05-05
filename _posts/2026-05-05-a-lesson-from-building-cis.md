---
title: "What I Learned Building a Clinical Documentation System"
categories: ["Medical Informatics"]
icon: "/assets/icons/cis.svg"
---

One of the most interesting lessons I learned came from working on a clinical documentation system I previously built.

At the beginning, I designed the medical records in a highly structured way.

The physician interface included separate fields for:

- medications  
- diagnosis  
- treatment plan  
- follow-up  
- clinical observations  

The workflow was heavily inspired by the SOAP format:

- Subjective  
- Objective  
- Assessment  
- Plan  

From a software engineering perspective, this design looked ideal.

Structured fields meant:

- easier querying  
- cleaner analytics  
- better interoperability  
- simpler AI processing  
- more predictable data pipelines  

There was also a free-text description field intended only for additional notes.

But something unexpected happened.

Most physicians ignored the structured sections almost entirely. Instead, they wrote nearly everything inside the free-text note. The structured fields frequently remained empty.

At first, I assumed this was a UX problem.

But after talking with physicians and observing the workflow more closely, the reality became much clearer.

The issue was not that doctors disliked structured systems.

**The issue was time.**

Clinical visits are often extremely short. Physicians need to maintain eye contact, listen carefully, think clinically, document findings, and continue the conversation naturally — all within a limited timeframe.

Several physicians explained something very similar:

> “If our attention stays on the computer during the entire visit, patients feel ignored.”

And honestly, that makes complete sense.

In real clinical environments, speed and workflow friction matter more than perfect data structures.

This experience completely changed how I think about medical AI and healthcare software systems.

Because it revealed something important:

> "Healthcare data is not messy because engineers failed to structure it properly. It is messy because clinical reality itself is messy."

Human behavior, workflow pressure, time constraints, and patient interaction all shape how medical data is actually produced.