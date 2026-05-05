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


<svg viewBox="0 0 64 64" xmlns="http://www.w3.org/2000/svg">

  <!-- background -->
  <rect width="64" height="64" rx="12" fill="#f4efe6"/>

  <!-- LEFT: structured system -->
  <rect x="4" y="10" width="18" height="44" rx="3"
        fill="none" stroke="#2f2a24" stroke-width="2"/>

  <line x1="7" y1="18" x2="18" y2="18" stroke="#2f2a24" stroke-width="1.2" stroke-linecap="round"/>
  <line x1="7" y1="25" x2="17" y2="25" stroke="#2f2a24" stroke-width="1.2" stroke-linecap="round"/>
  <line x1="7" y1="32" x2="18" y2="32" stroke="#2f2a24" stroke-width="1.2" stroke-linecap="round"/>

  <rect x="7" y="40" width="3" height="3" fill="none" stroke="#2f2a24" stroke-width="1"/>
  <rect x="12" y="40" width="3" height="3" fill="none" stroke="#2f2a24" stroke-width="1"/>
  <rect x="17" y="40" width="3" height="3" fill="none" stroke="#2f2a24" stroke-width="1"/>

  <!-- RIGHT: free text -->
  <rect x="42" y="10" width="18" height="44" rx="3"
        fill="none" stroke="#2f2a24" stroke-width="2"/>

  <line x1="45" y1="18" x2="58" y2="20" stroke="#2f2a24" stroke-width="1.2" stroke-linecap="round"/>
  <line x1="45" y1="25" x2="56" y2="28" stroke="#2f2a24" stroke-width="1.2" stroke-linecap="round"/>
  <line x1="45" y1="32" x2="59" y2="34" stroke="#2f2a24" stroke-width="1.2" stroke-linecap="round"/>
  <line x1="45" y1="39" x2="55" y2="42" stroke="#2f2a24" stroke-width="1.2" stroke-linecap="round"/>

  <!-- CENTER GAP: clear separation zone -->
  <line x1="26" y1="32" x2="38" y2="32"
        stroke="#2f2a24" stroke-width="1.2"
        stroke-dasharray="2.5 2.5"/>

  <!-- TIME (fully separated, bottom focus) -->
  <circle cx="32" cy="54" r="4"
          fill="none" stroke="#2f2a24" stroke-width="1.6"/>

  <line x1="32" y1="54" x2="32" y2="52"
        stroke="#2f2a24" stroke-width="1.3" stroke-linecap="round"/>
  <line x1="32" y1="54" x2="34" y2="55"
        stroke="#2f2a24" stroke-width="1.3" stroke-linecap="round"/>

</svg>


Clinical visits are often extremely short. Physicians need to maintain eye contact, listen carefully, think clinically, document findings, and continue the conversation naturally — all within a limited timeframe.

Several physicians explained something very similar:

> “If our attention stays on the computer during the entire visit, patients feel ignored.”

And honestly, that makes complete sense.

In real clinical environments, speed and workflow friction matter more than perfect data structures.

This experience completely changed how I think about medical AI and healthcare software systems.

Because it revealed something important:

> "Healthcare data is not messy because engineers failed to structure it properly. It is messy because clinical reality itself is messy."

Human behavior, workflow pressure, time constraints, and patient interaction all shape how medical data is actually produced.