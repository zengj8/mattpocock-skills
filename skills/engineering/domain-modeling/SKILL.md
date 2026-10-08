---
name: domain-modeling
description: Build and sharpen a project's domain model. Use when discussing codebase terminology, writing or editing the repo glossary, or recording or editing an ADR.
---

# Domain Modeling

Actively build and sharpen the project's domain model as you design. This is the *active* discipline: challenging terms, inventing edge-case scenarios, and writing the glossary and decisions down the moment they crystallise. (Merely *reading* the glossary for vocabulary is not this skill: that's a one-line habit any skill can do. This skill is for when you're changing the model, not just consuming it.)

## Resolve the glossary file

Before challenging a term or writing one, read the repo's domain-docs pointer and take the glossary file it names.

1. Read the Domain docs section of `CLAUDE.md` or `AGENTS.md`.
2. Read the doc that section points at (usually `docs/agents/domain.md`).
3. The glossary file is the one that pointer names. One context names one file. A map names one file per context; use the context this topic belongs to, and ask when that is unclear.

Done when you can name the file you will read and write. A resolved term goes into that file, in the format in [GLOSSARY-FORMAT.md](./GLOSSARY-FORMAT.md), as it is resolved.

When the pointer names no glossary file, the glossary file is a root `GLOSSARY.md`, created when the first term is resolved. When no `docs/adr/` exists, create it when the first ADR is needed. Create a file only when you have something to write.

## During the session

### Challenge against the glossary

When the user uses a term that conflicts with the existing language in the glossary file, call it out immediately. "Your glossary defines 'cancellation' as X, but you seem to mean Y. Which is it?"

### Sharpen fuzzy language

When the user uses vague or overloaded terms, propose a precise canonical term. "You're saying 'account': do you mean the Customer or the User? Those are different things."

### Discuss concrete scenarios

When domain relationships are being discussed, stress-test them with specific scenarios. Invent scenarios that probe edge cases and force the user to be precise about the boundaries between concepts.

### Cross-reference with code

When the user states how something works, check whether the code agrees. If you find a contradiction, surface it: "Your code cancels entire Orders, but you just said partial cancellation is possible. Which is right?"

### Update the glossary inline

When a term is resolved, update the glossary file right there. Don't batch these up: capture them as they happen. Use the format in [GLOSSARY-FORMAT.md](./GLOSSARY-FORMAT.md).

The glossary file should be totally devoid of implementation details. Do not treat it as a spec, a scratch pad, or a repository for implementation decisions. It is a glossary and nothing else.

### Offer ADRs sparingly

Only offer to create an ADR when all three are true:

1. **Hard to reverse**: the cost of changing your mind later is meaningful
2. **Surprising without context**: a future reader will wonder "why did they do it this way?"
3. **The result of a real trade-off**: there were genuine alternatives and you picked one for specific reasons

If any of the three is missing, skip the ADR. Use the format in [ADR-FORMAT.md](./ADR-FORMAT.md).
