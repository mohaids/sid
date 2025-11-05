+++
date = '2025-11-04T19:43:23-05:00'
draft = false
title = 'RCA + LLM reserach issues'
ShowToc = true
tags = ["research", "issues"]
+++

here are the following issues currently in prod:
- [ ] canary exists for a binary, but initial crash analysis doesn't pick it out.
    - potential solution: doing a `checksec` at the beginning and including that in the final json (`crash_data`). this will also include important information such as `PIE`. 

feature requests:
- [ ] disassembly - pighidra
- [ ] source code integration - sending in the C code to the llm
    - this would be useful for things like figuring out if `alloca` exists (contractor binary)