# Daily Reflection Tree

An end-of-day reflection tool built as a decision tree.
No LLM runs during the session. Same answers always give the same path.

---

## What it does

Asks an employee a short set of questions at the end of the day.
They pick from fixed options. The tree branches based on what they pick.
At the end it gives a short summary personalised to the path they took.

The questions cover three things in order:

1. **Locus** — did you feel like an agent in your day or a passenger in it
2. **Orientation** — did you focus more on what you gave or what you got
3. **Radius** — were you thinking mostly about yourself or also about the people around you

---

## Files


---

## How to read the tree

Open `reflection-tree.json`. Every object in the `nodes` array has an `id` and a `type`.

**Types:**
- `start` — entry point, has a `next` pointing to the first question
- `question` — shows text and 3 to 5 options, each option has a `signal` and the agent uses it to route
- `decision` — no text shown, just a routing rule that picks the next node based on collected signals
- `reflection` — shows a short piece of text, no input needed, auto-advances via `next`
- `bridge` — transition line between axes, auto-advances
- `summary` — final node, combines axis signals to pick a closing line

**To trace a path manually:**
Start at `START`, follow `next` to `Q1`, pick an option, note its `signal`, then follow the decision node rule to the next question. Continue until you reach `SUMMARY`.

---

## Two example paths

**Path 1 — good day, gave a lot, thought about others:**

START > Q1(Good) > D1 > Q2a > Q2a_follow > R1

BRIDGE1 > Q3(helped someone) > D2 > Q4a > Q4a_follow > R2
BRIDGE2 > Q5(team) > D3 > Q6a > Q6a_follow > R3 > R_CLOSE > D4 > SUMMARY


**Path 2 — hard day, felt unrecognised, focused inward:**

START > Q1(Draining) > D1 > Q2b > Q2b_follow > R1

BRIDGE1 > Q3(effort unnoticed) > D2 > Q4b > Q4b_follow > R2
BRIDGE2 > Q5(just me) > D3 > Q6b > Q6b_follow > R3 > R_CLOSE > D4 > SUMMARY



---

## Node count

| type | count | requirement |
|---|---|---|
| total | 27 | 25+ |
| question | 15 | 8+ |
| decision | 4 | 4+ |
| reflection | 4 | 4+ |
| bridge | 2 | 2+ |
| summary | 1 | 1+ |
| axes covered | 3 | all 3 |

---

## Rules the tree follows

No LLM at runtime — the tree runs on simple if/else logic, no API calls.
Fixed options only — no free text input from the user.
No moralising — someone on the harder path should leave feeling clearer, not worse.
Axes run in sequence — each one builds on what the previous one surfaced.

---

Submitted by Siddhartha Singh
AI Internship — DeepThought CultureTech Ventures
Deadline 30 April 2026
