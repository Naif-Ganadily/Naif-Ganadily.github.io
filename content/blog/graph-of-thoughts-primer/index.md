---
title: 'Before You Read "Graph of Thoughts"'
subtitle: 'A primer on graph-based prompting for large language models'
summary: A comprehensive primer on understanding Graph of Thoughts (GoT) paper, covering what came before GoT, the mathematical intuition, and how to approach graph-based reasoning in LLMs.
authors:
  - admin
tags:
  - Large Language Models
  - Prompting
  - Graph of Thoughts
  - AI Research
categories:
  - Research
  - Tutorial
date: '2025-06-23T00:00:00Z'
lastmod: '2025-06-23T00:00:00Z'
featured: true
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Placement options: 1 = Full column width, 2 = Out-set, 3 = Screen-width
# Focal point options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
image:
  placement: 2
  caption: 'Graph-based prompting for LLMs'
  focal_point: 'Smart'
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []

links:
  - icon: brands/medium
    icon_pack: fas
    name: Read on Medium
    url: https://medium.com/@ganadilynaif/before-you-read-graph-of-thoughts-3631a9e42dc9
---

## Introduction 👋

You're here because you're about to read the **Graph of Thoughts (GoT)** paper or attend a presentation about it. Either way, jumping straight into GoT may not be ideal without a primer like this one. I hope this article gives you what you need before reading the paper.

This article is your **mental calibration**. We'll cover:
- What came before GoT
- What those methods tried to solve
- Why they weren't enough
- The mathematical intuition underlying the methods

By the time graph-based reasoning starts, you'll already have the tools to understand it.

## Let's Start Simple: Prompting Basics

### 🟣 Basic Input-Output (IO)

This is the most basic interaction with a language model:

**Prompt → Output**

There are no intermediate steps, branching logic, or reasoning trail you can inspect.

### 🧮 Mathematical Thinking

You can think of this as a **black-box function**:

> You provide an input, get an output, but have no visibility into the reasoning in between. The model's internals are opaque — all we see is how inputs map to outputs.

While the function is stochastic (outputs may vary), it often behaves as if **deterministic**, producing consistent completions for common prompts due to high-probability token paths.

You provide input `x`, and the model returns `f(x)` — typically the most probable sequence continuation given its training.

---

## Read the Full Article

This is just a preview! Read the complete article with all the mathematical intuitions, diagrams, and explanations on Medium:

**[Before You Read "Graph of Thoughts" - Full Article on Medium](https://medium.com/@ganadilynaif/before-you-read-graph-of-thoughts-3631a9e42dc9)**

The full article covers:
- Chain of Thought (CoT) reasoning
- Self-Consistency and sampling strategies
- Tree of Thoughts (ToT) 
- The evolution to Graph of Thoughts (GoT)
- Mathematical frameworks behind each approach
- When to use each method

Happy reading! 🚀
