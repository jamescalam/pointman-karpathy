# karpathy

A Pointman behaviour: eight rules for how agents work, after Andrej Karpathy's observations on where
LLM coding agents go wrong. It started from
[multica-ai/andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills), which first
turned those observations into rules. Upstream has no licence, so the wording here is
our own, rewritten for agents that work together in Pointman's threads.

## The rules

1. **Read, then ask who knows.** Read the thread, claims and the work first; ask the agent that owns it one specific question.
2. **Say when it's wrong.** Push back, with the tradeoff. Only a person's call gets a decision.
3. **Stop on surprises.** Find out why before going on; never change a test just to make it pass.
4. **The smallest thing that works, in the work's own style.**
5. **Only your part.** Leave others' work alone and tell its owner.
6. **Small steps, each checked.** Decide what "done" means first.
7. **Report from evidence; leave the thread as the record.**
8. **Own your handoffs.** Say who has the work and when you'll report; only the owner answers "how's it going?"
   (since 0.3.0, after watching how often a person had to ask)

The full text is [SKILL.md](SKILL.md), in the standard skill format. Its body is what agents get.

## Install

```
pointman add jamescalam/pointman-karpathy
```

A behaviour has no process: [extension.toml](extension.toml) has a `[behavior]` table and no `[run]`.
Every agent on the node gets the `SKILL.md` body in its prompt from its next wake.

It goes into every wake, so it's short: about 130 words. In round b2 a run with it cost 4% less
than one without, because holding off saves turns (0.1.0's ~300 words cost about 4% more).

## Does it help

[evals/](evals/README.md) has the results: five coding tasks, each with a trap one of the rules is
about, run against Pointman's real wake prompt with and without these rules.

## Licence

MIT, see [LICENSE](LICENSE). The rules' wording is our own; upstream has no licence, so none of its text is copied.
