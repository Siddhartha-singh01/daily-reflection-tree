# Write-up: Daily Reflection Tree

## Why I picked these questions

My main concern when writing the questions was avoiding the thing that kills most reflection tools — questions that are easy to answer without actually thinking. "How productive were you today?" is useless. You click 7/10 and move on. So I wrote every question to have a bit of friction in it. Not uncomfortable, just enough that you pause for a second.

For Axis 1, I opened with a one word descriptor of the day rather than asking about agency directly. The word someone picks tells you something before they even get to the branching questions. "Draining" and "Good" are different frames and the follow-up questions should feel different depending on which frame you're in. On the harder-day path I didn't want to challenge the person. I just wanted to open a crack — "was there even one moment where the choice was yours?" — because in my experience there always is one, even on the worst days, and naming it matters.

For Axis 2 the trickiest part was writing the entitlement-path questions without them feeling accusatory. Nobody thinks they're entitled. So instead of "did you focus too much on recognition?" I asked "what felt most off today?" and let them name it themselves. The follow-up — "was there anything you did today that you didn't need anyone to see?" — is the one I'm most happy with. If the answer is yes and they sit with it, the axis does its job without the tree ever having to say "you were being entitled."

For Axis 3 the opening question "who is in the picture?" was borrowed loosely from perspective-taking exercises in Batson's work. You catch the honest answer before people have time to perform the right one.

---

## How I built the branching

The tree has two layers of branching. The first layer is the routing — Decision nodes D1, D2, D3 split the session into two tonal paths per axis. The second layer is the follow-up questions within each path, which go one level deeper based on what the person already said.

I went back and forth on whether to merge both paths at the Reflection node after just one question per path. An early version did that. It felt too rushed — the reflection arrived before there was enough material to make it land. Two questions per path felt right. By the time you hit the reflection text you've already said two honest things, which means the reflection is working with real material rather than one surface-level answer.

The biggest trade-off was fixed options versus free text. Free text would feel more natural but the whole point of the assignment is deterministic branching — you can't branch on free text without a classifier, and a classifier means an LLM call, which breaks the core rule. So I had to make the fixed options genuinely cover the real range of answers. I went through each question and asked: would someone who is actually in this situation find their real answer here? Where the answer was no I rewrote the options. The entitlement path options took three rewrites before they felt honest rather than loaded.

---

## Psychology sources I used

**Axis 1 — Rotter (1954) and Dweck (2006).** Rotter's locus of control research is the foundation — the basic split between believing your outcomes are shaped by your own actions versus by external circumstance. Dweck's growth mindset work extends this into beliefs about ability specifically. I read summaries of both and the main thing I took from Dweck is that the locus question is not just about what happened but about whether you believe the situation was learnable. That's why Q2a_follow asks whether you nearly stopped — it's testing whether difficulty feels like information or like a verdict.

**Axis 2 — Organ (1988) and Campbell et al. (2004).** Organ's work on organisational citizenship behaviour is about discretionary effort — what people do beyond their formal role. The interesting thing from Campbell is that entitlement is mostly invisible to the person holding it, which is why the questions on that path avoid labelling it. The goal is not for the person to feel judged, it's for them to notice the frame they were operating from.

**Axis 3 — Maslow (1969) and Batson (2011).** Maslow's late paper on self-transcendence is the one most people don't know about — he placed it above self-actualisation in his later thinking. The move from "what do I need" to "what does this situation need from me" is what Axis 3 is trying to nudge. Batson's perspective-taking research is about treating empathy as a cognitive skill rather than just a feeling, which is why the Axis 3 questions ask about specific people rather than people in general.

---

## What I would change with more time

The summary node right now picks from eight fixed closing statements based on your axis combination. It works but it's blunt. What I'd actually want is the summary to pull specific answers back — "you said today was draining, and you still helped someone who was stuck. Hold that." That requires the agent to track answer text across nodes, not just signals. Straightforward to build but I ran out of time.

The other thing I'd add is a history layer. After 10 sessions you could surface a pattern — "this is the third time this week you've landed on the entitlement path" — and that is where a tool like this gets genuinely useful. A single session is a snapshot. Patterns across sessions are the actual data.

I'd also add a "none of these fit" option on every question, routed to a neutral node that just moves forward. Right now if your real answer isn't in the four options you're stuck picking the least wrong one, which creates noise in the signals.
