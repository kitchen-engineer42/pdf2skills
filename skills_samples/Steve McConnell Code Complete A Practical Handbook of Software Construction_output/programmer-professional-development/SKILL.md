---
name: programmer-professional-development
description: "Create personalized learning plans, identify skill gaps, and design practice exercises for programmer growth. Use when the user wants to upskill in a new language or framework, plan a structured learning path, assess their current skill level, or establish ongoing development habits."
---

# Programmer Professional Development

Generate actionable, personalized development plans based on a programmer's current skill level, target goals, and available time.

## When to Use

- User asks for a learning plan or skill roadmap
- User wants to learn a new language, framework, or domain
- User asks for book or resource recommendations
- User wants to assess their skill level or identify gaps

## Workflow

### 1. Assess Current Level

Ask targeted questions and classify the user:

| Level | Indicators |
|-------|-----------|
| **Beginner** | Uses basic features of one language; writes simple classes, loops, conditionals |
| **Intermediate** | Proficient in 1-2 languages; understands frameworks but not internals |
| **Advanced** | Deep expertise in a language/environment; understands framework internals |
| **Expert** | Writes code primarily for human readers; mentors others; contributes to ecosystem |

### 2. Identify Skill Gaps

Compare current skills against the target role or project:

```markdown
## Skill Gap Analysis: <user-name>

**Current:** Python (intermediate), SQL (basic), no frontend experience
**Target:** Full-stack web developer

| Skill Area | Current | Target | Gap |
|-----------|---------|--------|-----|
| Python | Intermediate | Advanced | Practice design patterns, async |
| JavaScript/TypeScript | None | Intermediate | Start from fundamentals |
| React/Vue | None | Intermediate | Build 2-3 projects |
| SQL | Basic | Intermediate | Joins, indexing, query optimization |
| HTTP/REST APIs | Basic | Advanced | Build and consume APIs |
```

### 3. Generate Learning Plan

Produce a time-boxed plan with concrete actions:

```markdown
## 12-Week Learning Plan

### Weeks 1-4: JavaScript Fundamentals
- [ ] Complete: "JavaScript: The Good Parts" (35 pages/week)
- [ ] Build: Todo app with vanilla JS (DOM manipulation practice)
- [ ] Experiment: Write 3 test programs exploring closures, promises, async/await

### Weeks 5-8: React Basics
- [ ] Complete: Official React tutorial
- [ ] Build: Weather dashboard consuming a public API
- [ ] Review: Read source code of one small, well-regarded React library

### Weeks 9-12: Integration
- [ ] Build: Full-stack app with Python backend + React frontend
- [ ] Review: Request code review from experienced full-stack developer
- [ ] Reflect: Document 3 mistakes made and lessons learned
```

### 4. Design Practice Exercises

For each skill gap, create a concrete exercise:

```markdown
### Exercise: Async/Await Deep Dive
**Goal:** Understand Python's async model
**Task:** Build a script that fetches 10 URLs concurrently using aiohttp
**Validation:** Must complete in <2s (vs. ~10s sequential)
**Stretch:** Add retry logic with exponential backoff
```

### 5. Recommend Reading Strategy

- **One technical book every two months** (~35 pages/week)
- **Weekly:** Browse documentation for one library relevant to current work
- **Monthly:** Read and annotate code from a respected open-source project
- **Per mistake:** Write a brief post-mortem (what happened, why, how to prevent)

## Key Principle

> Programming is 15% communication with computers and 85% communication with people.

Guide users toward writing code for human readers — clear naming, good structure, and meaningful documentation — not just making tests pass.
