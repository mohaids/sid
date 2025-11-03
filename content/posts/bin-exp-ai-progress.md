+++
date = '2025-11-02T12:33:42-05:00'
draft = false
title = 'RCA + LLM + Binaries research progress'
ShowToc = true
tags = ["research", "progress"]
+++

**11.02.2025**
3 main issus I need to fix:
1. making llm return a logical plan, along with tool calls?
    - extract said tool calls, run them in a single persistent session
    - send it back to llm, create loop of this
2. test with harder ctf challenge
3. integrate pighidra

interesting observation(s):
1. hallucination of tool calls - in the time when i didn't include tool calls in the message i sent the llm, it hallucinated a tool call instead 😭. to be specific, it talk about there being a `run_gdb` tool call, but it never existed?
2. highly inconsistent responses. when i ran the llm with tool calls, it usually doesn't provide detailed reasoning, however, one time it did, and i was overjoyed. but that only happened once, and its back to just calling tools. or shall i say, a single fucking tool, instead of the multiple it was seemingly instructed to do.

**hypothesis:**
perhaps these issues with the llm only giving one tool call can be solved by asking it to give the gdb commands, extract them commands, send it to a helper llm that can convert the gdb commands to the tool calls, then give back the tool calls, which i will then execute in the gdbmanager session. then append those results back to messages. then call the main llm again asking if it either wants to create the rca report now that it has all the necessary information, or if it wants to continue to investigate. if it wants to continue to investigate, then do the same process over again.