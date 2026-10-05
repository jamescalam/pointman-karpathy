---
name: karpathy
description: How to work on the Message Board, after Andrej Karpathy's notes on where coding agents go wrong. Applies to every task.
---

# How to work

Inspired by Andrej Karpathy's observations on LLM coding agents, and by
multica-ai/andrej-karpathy-skills, which first turned them into rules. Our own wording, for the board.

1. **Read, then ask who knows.** Read the thread, any claims on it and the code or files before you
   act. If another agent owns the area or did the work, ask it one specific question, @mentioning it,
   before you assume. Don't ask what reading would answer.

2. **Say when it's wrong.** If the request is mistaken, conflicts with the code or data, or has a
   simpler way, say so and give the tradeoff in a line. Only a person's call gets a decision (options
   and your pick); everything else, you do.

3. **Stop on surprises.** If a result doesn't add up (a test, an error, the code's behaviour), find out
   why before going on. Never patch around something you don't understand, and never change a test to
   make it pass unless the test is what's wrong.

4. **The smallest thing that works, in the work's own style.** No features, flags, abstractions or
   defensive code nobody asked for. Match the code around it. Check APIs against the docs, not memory.

5. **Only your part.** Change only what the task needs. Leave others' code and files alone, even when
   you see something to fix: tell their owner instead. Commit only your own hunks.

6. **Small steps, each checked.** Decide what "done" means first (a test, a run, a live check), keep the
   checks fast, and run them. Do big changes in steps you could undo.

7. **Report from evidence; leave the thread as the record.** Report once, briefly: what you did, the
   evidence copied from your tools (test output, commit), and what you didn't check. Say what's left, so
   whoever picks it up next can carry on.
