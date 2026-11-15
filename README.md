# brainy

A Claude skill that keeps an AI's memory true when facts change.

Every AI memory has the same problem: it's right on Monday and quietly wrong by Friday. A new fact gets saved next to the old one, and now the AI holds two answers that can't both be true. brainy is a way of writing memory that fixes this. It isn't a new engine: it runs on [Basic Memory](https://github.com/basicmachines-co/basic-memory), which you may already use.

## How it writes

- **One note per thing**: a project, a person, a product.
- **One fact per line**, each with a date and a source: `- [price] ₹499 (since 2026-11-02, source …) #current`
- **When a fact changes, the old line stays**, marked `#replaced`, with the new one next to it. The AI always knows what's true now and what it used to be.

## Does it help?

We tested it on the 78 knowledge-update questions of [LongMemEval](https://github.com/xiaowu0162/LongMemEval), the ones where a fact changes partway through a long chat history.

| Claude Haiku answering from | Right (Sonnet judge) |
|---|---|
| A brain written with brainy | **69 / 78** |
| The full chat history | 63 / 78 |

With the brain in Basic Memory and Haiku seeing only the top 15 search hits, it got 64 of 71 (a later run on the same questions).

Small print: one answer model, one judge, 78 questions, run by us. Vendor numbers (Zep reports 83.3% with GPT-4o) use different models and judges, so they aren't comparable. We'll publish the eval code after re-running it on a second model.

## Install (Claude Code)

1. Install and connect [Basic Memory](https://docs.basicmemory.com), and make a project for your entity.
2. `git clone https://github.com/topc-social/brainy ~/.claude/skills/brainy`
3. Ask Claude something about your entity, or tell it a decision. It reads and writes the brain from then on.

## Licence

MIT. Made by [TOPC](https://topc.social). Fixes and ideas welcome as pull requests.
