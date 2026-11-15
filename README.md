# brainy

A Claude skill that keeps an AI's memory true when facts change.

AI memory is often right on Monday and quietly wrong by Friday. A new fact gets saved next to the old one, and now the AI holds two answers that can't both be true. brainy is a way of writing memory that fixes this. It isn't a new engine: it runs on [Basic Memory](https://github.com/basicmachines-co/basic-memory), which you may already use.

## How it writes

- **One note per thing**: a project, a person, a product.
- **One fact per line**, each with a date and a source: `- [price] ₹499 (since 2026-11-02, source …) #current`
- **When a fact changes, the old line stays**, marked `#replaced`, with the new one next to it. Each property has one `#current` line, and the history stays readable.

## Does it help?

We tested an early version of these writing rules on the 78 knowledge-update questions of [LongMemEval](https://github.com/xiaowu0162/LongMemEval), the ones where a fact changes partway through a long chat history.

| Claude Haiku answering from | Right (Sonnet judge) |
|---|---|
| Facts written the brainy way, all in the prompt | **69 / 78** |
| The full chat history | 63 / 78 |

Then we fixed the main error (an old value replaced by a fact about a different thing) and re-ran 71 of the 78 questions (the brain went from 63 to 65 of 71 with everything in the prompt). With the brain stored in Basic Memory and Haiku seeing only the top 15 search hits, it got 64 of 71.

Small print: one answer model, one judge, run by us. Vendor numbers (Zep reports 83.3% with GPT-4o) use different models and judges, so they aren't comparable. We'll publish the eval code after re-running it on a second model.

## Tried it?

Tell us if it helped, or where it didn't, in an [issue](https://github.com/topc-social/brainy/issues). One line is enough.

## Install (Claude Code)

1. Install and connect [Basic Memory](https://docs.basicmemory.com), and make a project for your entity.
2. `git clone https://github.com/topc-social/brainy ~/.claude/skills/brainy`
3. Ask Claude something about your entity, or tell it a decision. It reads and writes the brain from then on.

## Licence

MIT. Made by [TOPC](https://topc.social). Fixes and ideas welcome as pull requests.
