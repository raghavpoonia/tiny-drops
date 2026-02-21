# Cross-AI Prompt Template

Use this in ChatGPT/Claude/Gemini when starting new chats.

---

## Context

I'm building a multi-year knowledge compounding system called "tiny-drops".

**Format**: 30-60s reads, one concept per entry  
**Scope**: DS, Algo, Patterns, Security, Systems  
**Languages**: Python, Go, C, Rust (implementation-focused)

## Current Inventory

[MANUALLY LIST YOUR DROPS HERE - UPDATE AS YOU ADD MORE]

**DS**: Hash Map  
**Algo**: Binary Search  
**Security**: JWT Internals

## Task

Suggest 5 new concepts that:
1. Don't duplicate existing entries
2. Build progressively on what I have
3. Are implementation-focused
4. Have security/systems relevance

## Output Format

For each:
- **Concept**: Name
- **Category**: ds|algo|patterns|security|systems
- **Difficulty**: 1-5
- **Why Now**: How it builds on existing
- **Real-World**: Production example
- **Prerequisites**: Which existing drops to review

Then write the first one using the template from README.md.

## Constraints

- Max 60 seconds read
- Runnable code required
- Security context preferred (I work in cloud security, 450k systems)
- Link to existing drops when relevant

---

Paste updated inventory and get 5 progressive suggestions.
