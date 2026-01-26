+++
date = '2025-11-01T19:17:45-04:00'
draft = false
title = 'RCA (Root Cause Analysis) of Binaries AI Research'
ShowToc = true
tags = ["research", "binary exploitation"]
+++

# Still a WIP (Work - In - Progress)

It was early September, when I reached out to Professor Yener expressing my interest to be involved in security research. Now, a few months into this RCA research, I'm glad through happenstance I reached out.

# Objective
Given a binary, is it possible to create a RCA (Root Cause Analysis) of a binary, given a PoC (Proof of Concept)

# Background
First, what does RCA even mean? 

RCA, also known as Root Cause Analysis, is a consise report of why a system encountered an issue. In this research, the system will be a binary, and the issue will be a crash triggered by a PoC. This PoC will be either static, in the form of a `.poc` file, or it'll be dynamic, in form of a `.py` file. Ideally, for a closed-loop, better system, 

# Cursory Research
During the initial weeks, Patrick invited me to perform some cursory research on the current state of LLMs creating RCAs. At first, I tried to search for papers that were directly `RCA + LLMs + binary exploitation`. However, after turning empty-handed, I expanded my search to any `RCA + LLM` paper. Using [arXiv](https://arxiv.org/), I found two papers that caught my eye:

1. RCAgent: Cloud Root Cause Analysis by Autonomous Agents with Tool-Augmented Large Language Models
2. ChatDBG: Augmenting Debugging with Large Language Models

## Paper 1: RCAgent
This paper pertains to RCA and LLMs in cloud systems - specifically Alibaba cloud. This paper comes up with a `RCAgent`, a "tool-augmented LLM autonomous agent framework". What makes it different than the typical `ReAct` agent?

To answer this question, one must first understand what `ReAct` agents even are.

ReAct, also known as `Reasoning + Acting`, is a framework of autonomous agents powered by LLMs. It is essentially supposed to be a loop where the agent:
1. thinks about what to do next
2. acts, by calling a tool/api/api-via-mcp server
3. observes the feedback from said action
4. repeats the cycle

This allows the agent the ability to solve complex tasks using step-by-step reasoning and evidence-gathering, rather than just generating the answer in a single-pass.

Knowing this, RCAgent employes a few key upgrades:
1. privacy-conscious (but also, not a requirement) - the paper uses locally deployed models, such as Vicuna
2. a suite of tools utilized for context management
    - introduces "observation snapshot key (obsk), which is compresses lengthy observations using key-value store
    - it only shows the "head" to the agent, with hash-ids for the full data
    - > check out the image below to see a visual representation
3. enhanced tool system
> [insert things here]
4. a suite of stabiling tools
    - jsonregen
    - error handling
5. advanced aggregation methods
ReAct:
RCAgent: self-consistency for action trajectories

![rcagent overview pic](/rcagent-overview.png)

Performance metrics (RCAgent vs ReAct)

![performance metrics overview pic](/performance-research.png)

### Understanding Different Performance Metrics

### Understanding TSC Aggregation in Detail



## Paper 2: ChatDBG




# Creating A Idealized System Overview



# Iteration 1: The Sanity Check

![iteration-one-also-known-as-the-sanity-check](/iter1.png)


# Iteration 2: Attempt At Future-Proofing

![second-attempt](/iter2.png)


# Iteration 3: The Unintentional Over-engineering

![third-attempt](/iter3.png)


# Iteration 4: Back-To-Basics

![fourth-attempt](/iter1.png)


# Case Analysis (HTB Cyber Apocolypse 2025)



# What's for Future

![possible-attempt](/future-iter.png)

# 2. Testing With Local Models




# 3. Testing With Bigger Models via [openrouter.com](www.openrouter.com)




# High-level overview
1. Professor / Master Agent
2. Student   / Slave Agent(s)