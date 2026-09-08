# decision-model — a Model Meets Reality starter

**derives a person's decision function from their completed choices**

A *model* here is not neural weights. It is a short document stating premises, a
mechanism, at least one falsifiable consequence with a date, and a deletion
clause naming when you would retire it. This repo is a starting point for one of
the eleven kinds.

## What makes this kind a kind

**Premise shape**

```
Given <recurring decision situation>, <actor> chooses <option A> over <option B>. Revealed by: <2+ completed, announced decisions>. Violated by: <a future choice that breaks the ordering>.
```

**What would prove it wrong:** a future choice, in the named situation, that takes the other option


**Banned:** Psychology. 'X is loyal / ruthless / insecure' admits no future observation that settles it. Only orderings over choices.
**Scope:** Public figures acting in public roles, professional decisions only. Tag --sensitivity contested.

**Tier: PROVEN** — a discipline worked out against real instances.

## Agentic reasoning

Models here are not static documents. The engine runs each one against live
sources on a schedule: it searches, reads what it finds, and writes dated claims
that later get graded. Every citation is validated against what the search
actually returned, so a fabricated source is dropped rather than recorded.

What the pass asks is specific to this kind:

> Observe ONLY completed, announced decisions -- signed contracts, executed instructions, confirmed changes. Ignore rumour, 'reportedly considering', and statements of intent: the model's whole claim is that actions reveal what statements conceal. For each premise, report whether a decision since the model was written CONFORMS TO or VIOLATES the stated ordering, and say plainly if no qualifying decision has occurred.

And when a claim comes due:

> Did a completed decision in the named situation take the predicted option? A decision that never arose is UNRESOLVABLE, not a miss.

## Start

```bash
git clone https://github.com/shaelsrv/ModelMeetsReality my-copilot   # the engine (anonymous clone, no gh CLI needed)
cd my-copilot
rm -rf .git               # detach: a clone still points at the engine's remote
git config --global --add safe.directory "$PWD"   # if git says "dubious ownership"
git init && git add -A && git commit -m "main instance"
cp .env.example .env      # set OPENROUTER_API_KEY, or LLM_BACKEND=claude-code

python -m suites.new_model my-model --kind decision-model \
    --title "My Model" --domain "what it models, in a sentence"

# then EDIT ../my-model/watch.json -- the scaffold placeholder is refused
# and write real premises into MODEL.md; the scaffold is empty by design
python -m suites.model_watch --repo my-model --predict
```

The engine refuses to run against the scaffold placeholder, on purpose: running
it as-is spends a web search and returns either nothing or claims about a target
you did not choose.

`rm -rf .git` matters: a fresh clone is already a git repo whose `origin` is the
engine, so without it the `git init` is a no-op and a later `git push` would send
your private premises to the engine repo. Your main should be yours — one initial
commit, no remote.

## Engine

Pinned to `56a33c1` of [ModelMeetsReality](https://github.com/shaelsrv/ModelMeetsReality). The engine
is shared across all eleven kinds; only the discipline above differs. Update
deliberately rather than tracking latest.
