# Dropout Certified

**Knowledge is power. Decentralize it.**

Dropout Certified is a free skills credential. No tuition, no enrollment, no gatekeepers: learn for free, then prove what you can do on an exam that's hard to fake and easy to verify.

This repository is the **study coach**: a Claude skill that teaches you to a mastery standard and tells you honestly when you're ready.

## Tracks

| Track | What you'll be able to do |
|---|---|
| **AI Essentials v1** | Choose what to hand to AI, brief it well, catch its mistakes, use it safely, and build reusable workflows. Tool-neutral: Claude, ChatGPT, Gemini, Copilot. |
| **Data Analysis with SQL v1** | Query, clean, join and aggregate real (messy) data, avoid the classic traps, and turn results into findings a manager can act on. |

Every learning goal is published in full: [AI Essentials](skills/dropout-certified/references/ai-essentials/learning-goals.md) and [SQL](skills/dropout-certified/references/sql/learning-goals.md).

## Why it's not easy

- **Mastery, not exposure.** The coach marks a goal ready only after you get it right on fresh questions in two separate sessions, and it brings goals back for spaced review.
- **Hints before answers.** You try first. The coach asks why, not just what.
- **Graded on real work.** Half of the AI Essentials exam is hands-on: build something with AI, then audit AI output for errors. The SQL exam runs your queries against a hidden second database, so pasted-in answers fail.
- **Published standards.** [How the exams work and how they're scored](skills/dropout-certified/references/exam-guide.md) is public. The exam questions are not.

## What's in here

- `skills/dropout-certified/SKILL.md`: the coach's instructions.
- `references/ai-essentials/`: learning goals and a 35-question practice bank with an explanation for every wrong option.
- `references/sql/`: learning goals, a practice shop database (deliberately messy, like real data), and 32 exercises whose answers were checked by running them.
- `references/exam-guide.md`: exam format, scoring rubrics and pass rules.

The coach only reads these files and, for SQL practice, runs queries on a local practice database. It contacts no outside services and sends no data anywhere. If you allow it, it keeps your progress in a Markdown file in your own folder.

## Install

**Claude apps (claude.ai, desktop):** download [`dropout-certified.zip`](https://github.com/BrianChase515/dropout-certified/raw/downloads/dropout-certified.zip) and upload it under Customize > Skills. Then say "teach me AI Essentials" or "quiz me on SQL joins."

**Claude Code**
```
/plugin marketplace add BrianChase515/dropout-certified
/plugin install dropout-certified@dropout-certified
```

## The certificate

Practice results from the coach are always labeled self-assessed. The real certificate comes from a separate hosted exam with a public verify link for every certificate. It's in an invite-only pilot first. A Dropout Certified certificate is a certificate of demonstrated skill; it is not a degree, diploma or accreditation.

## More by the same author

[Skill Spotter](https://github.com/BrianChase515/skill-spotter) · [Blindspot](https://github.com/BrianChase515/blindspot) · [Reading Companion](https://github.com/BrianChase515/reading-companion)

## Author

Built by [Brian Chase](https://github.com/BrianChase515). MIT licensed.
