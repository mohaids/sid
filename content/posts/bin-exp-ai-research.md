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

# Necessary Background Definitions
First, what does RCA even mean? 

RCA, also known as Root Cause Analysis, is a consise report of why a system encountered an issue. In this research, the system will be a binary, and the issue will be a crash triggered by a PoC. This PoC will be either static, in the form of a `.poc` file, or it'll be dynamic, in form of a `.py` file. Ideally, for a closed-loop, better system, 


# Background
> What is root-cause analysis, specifically of binaries?

# Cursory Research
During the initial weeks, Patrick invited me to perform some cursory research on the current state of LLMs creating RCAs. At first, I tried to search for papers that were directly `RCA + LLMs + binary exploitation`. However, after turning empty-handed, I expanded my search to any `RCA + LLM` paper. Using [arXiv](https://arxiv.org/), I found two papers that caught my eye:
1. RCAgent: Cloud Root Cause Analysis by Autonomous Agents with Tool-Augmented Large Language Models
2. ChatDBG: Augmenting Debugging with Large Language Models

## Paper 1: RCAgent
This paper pertains to RCA and LLMs in cloud systems - specifically Alibaba cloud. This paper comes up with a `RCAgent`, a "tool-augmented LLM autonomous agent framework". What makes it different than the typical `ReAct` agent? RCAgent employes a few key upgrades:
1. self-Consistency for action trajectories
2. a suite of tools utilized for context management

![rcagent overview pic](/rcagent-overview.png)


### Understanding TSC Aggregation

## Paper 2: ChatDBG




# Creating A Idealized System Overview



# Iteration 1: The Sanity Check

![iteration-one-also-known-as-the-sanity-check](/iter1.png)


# Iteration 2: Attempt At Future-Proofing




# Iteration 3: The Unintentional Over-engineering




# Iteration 4: Back-To-Basics




# Case Analysis (HTB Cyber Apocolypse 2025)



# What's for Future



# 2. Testing With Local Models




# 3. Testing With Bigger Models via [openrouter.com](www.openrouter.com)




# High-level overview
1. Professor / Master Agent
2. Student   / Slave Agent(s)