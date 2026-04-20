---
name: effective-commenting-strategies
description: "Write and review code comments that explain intent, not mechanics. Use when adding comments to new code, reviewing existing comments for staleness or redundancy, establishing team commenting conventions, or converting vague inline comments into intent-based explanations."
---

# Effective Commenting Strategies

Write comments that explain *why* code exists, not *what* it does. Apply these strategies when writing new comments or reviewing existing ones.

## When to Use

- Adding comments to new or modified code
- Reviewing pull requests for comment quality
- Refactoring code with stale, misleading, or redundant comments
- Setting team commenting standards

## Decision Workflow

When encountering code that may need a comment:

1. **Is the code self-explanatory?** → No comment needed
2. **Can you make the code clearer instead?** → Refactor first, then reassess
3. **Is there non-obvious intent?** → Write an intent comment
4. **Is there a complex block (5+ lines)?** → Write a summary comment
5. **Is there incomplete work?** → Add a `TODO`/`FIXME` marker

## Comment Types with Examples

### Intent Comments (Preferred)

Explain *why* the code exists at the problem level:

```python
# BAD: repeats the code
# Set retry count to 3
retry_count = 3

# GOOD: explains the why
# Three retries handles transient network failures without overwhelming the server
retry_count = 3
```

### Summary Comments

Condense multi-line blocks into scannable descriptions:

```python
# BAD: no comment on a dense block
tokens = text.split()
tokens = [t.lower() for t in tokens]
tokens = [t for t in tokens if t not in stopwords]
freq = Counter(tokens)

# GOOD: summary at the top
# Tokenize, normalize, and count word frequencies (excluding stopwords)
tokens = text.split()
tokens = [t.lower() for t in tokens]
tokens = [t for t in tokens if t not in stopwords]
freq = Counter(tokens)
```

### Marker Comments

Flag incomplete work with searchable tags:

```python
# TODO(author): Handle pagination once API v2 ships
# FIXME: Race condition when concurrent requests update the same record
# HACK: Workaround for upstream bug #1234 — remove after library v3.0
```

**Rule:** Search for all `TODO`/`FIXME`/`HACK` markers before each release.

## Style Rules

| Rule | Reason |
|------|--------|
| Use `//` for single-line, `/* */` for multi-line | Consistency; multi-line `//` is harder to maintain |
| Avoid decorative boxes (`***`, `+---+`) | Tedious to maintain when text changes |
| Prefer accuracy over aesthetics | A correct one-line comment beats a pretty stale one |

## Density Guideline

Target roughly **1 comment per 10 statements** (IBM research finding). Do not enforce rigid quotas — focus on whether each comment adds value the code alone does not convey.
