+++
date = '2025-11-02T12:33:42-05:00'
draft = false
title = 'RCA + LLM + Binaries research progress'
ShowToc = true
tags = ["research", "progress"]
+++

**11.27.2025**
Refactoring code hell. Patrick gave the idea of using exploit.py instead of static .poc file.

**11.09.2025**
Task 1: Create a persistent GDB Session. Should be pretty straight-forward to set up.
Task 2: Refactor the code, such that you just use the `master_llm` to spit out plan + commands, then use a helper LLM to summarize said outputs of commands, so that the `master_llm` has a smaller context to worry about.
Task 3: Integrate pighidra
Task 4: Integrate `checksec`

**11.08.2025**
tldr: pain.

**11.05.2025** - Meeting day
Main points:
1. Instead of using this convoluted: master_llm's raw gdb commands + tool_call -> helper llm, which will then reutrn the correct tool_calls, and then the system running the gdb commands. I should instead just ask master_llm to give me the `gdb` commands straight up - like originally done.
2. Also - somehow I lose the notes?? Don't really know what Obsidian did to them.
3. Need to create persistent GDB session.
4. Please, the whole loop must work.

**11.04.2025**
Need to run it through the LLM. Need to decipher whether or not the investigative path it suggests is fruitful. Fingers-crossed it is. 

So far, in terms of completion, haven't quite met all the requirements.
- [ ] making the llm return a logical plan + gdb commands, sending it to a helper llm to call `tool calls`. sending the results of the `tool calls` back to the master llm.
    - issue: the gdb execution part isn't quite working.
- [ ] testing this whole process with a harder ctf to see if the plan it creates is logical, and the technical investigative path seems accurate
    - issue: did it, seems to work overall. however, would be greatly beneficial if source code is added.
- [ ] implement pighidra into the mix.
    - issue: tried to integrate, but running into some issues. probably lower on the priority list to implement.

**11.03.2025**
Just pain - went down a rabbit hole in figuring out how a HTB challenge was solved, but realized all that time was wasted due to the binary, solver.py, or any other libc files was not included 😭

Tried to understand another challenge, successfully did so. Took a while to create the .poc file. Tested it, it crashed, ran initial `crash context gathering` function.

**11.02.2025**
3 main issus I need to fix:
1. making llm return a logical plan, along with tool calls?
    - extract said tool calls, run them in a single persistent session
    - send it back to llm, create loop of this
2. test with harder ctf challenge
3. integrate pighidra
---
interesting observation(s):
1. hallucination of tool calls - in the time when i didn't include tool calls in the message i sent the llm, it hallucinated a tool call instead 😭. to be specific, it talk about there being a `run_gdb` tool call, but it never existed?
2. highly inconsistent responses. when i ran the llm with tool calls, it usually doesn't provide detailed reasoning, however, one time it did, and i was overjoyed. but that only happened once, and its back to just calling tools. or shall i say, a single fucking tool, instead of the multiple it was seemingly instructed to do.

**hypothesis:**
perhaps these issues with the llm only giving one tool call can be solved by asking it to give the gdb commands, extract them commands, send it to a helper llm that can convert the gdb commands to the tool calls, then give back the tool calls, which i will then execute in the gdbmanager session. then append those results back to messages. then call the main llm again asking if it either wants to create the rca report now that it has all the necessary information, or if it wants to continue to investigate. if it wants to continue to investigate, then do the same process over again.

**end of day conclusion**:
there's a time where everyone has all the ambition in the world and eventually all of them reach a point of pragmatism and cut their losses. that is the situation i am at right now.

i revamped the core logic flow of how the ReAct agent will behave. the actual technical implementation of the gdb execution is being a little cumbersome, but i did a major revamp of that too - created a whole new class n stuff. 

the main thing i need to focus on before the day is over is to see how the agent behaves with a much harder ctf binary and is it able to accurately figure out how to make headwinds with it.

i also tried to integrate pighidra with my 