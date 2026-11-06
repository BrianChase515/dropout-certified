# AI Essentials v1: learning goals

Version 1, November 2026. These are exactly what the exam tests. Everything here is tool-neutral: it applies to Claude, ChatGPT, Gemini, Copilot or any similar assistant.

Each goal has an ID (for example `AI3.4`) that practice questions, exam questions and progress tracking all refer to.

| Domain | Weight |
|---|---|
| AI1. How AI works | 15% |
| AI2. Choosing what to hand off | 15% |
| AI3. Giving context and instructions | 25% |
| AI4. Judging the output | 20% |
| AI5. Using it responsibly | 15% |
| AI6. Reusable workflows | 10% |

## AI1. How AI works (15%)

- **AI1.1** Explain in plain words that a language model predicts likely next text from patterns in its training data, and why that makes it fluent but not automatically correct.
- **AI1.2** Explain tokens and the context window: the model only "sees" what's in the conversation plus what it was trained on, and very long inputs can push out or dilute earlier material.
- **AI1.3** Explain the knowledge cutoff, and how web search, uploaded files and connectors give a model newer or private information.
- **AI1.4** Explain why models sometimes state false things confidently (made-up facts, citations, quotes, numbers), and which kinds of request make that more likely.
- **AI1.5** Explain why the same prompt can give different answers, and what that means for checking and repeating work.
- **AI1.6** Tell apart a chat assistant, an assistant using tools (search, code, files) and an agent that takes multi-step actions, and what each can and can't verify on its own.

## AI2. Choosing what to hand off (15%)

- **AI2.1** Identify tasks AI does well (drafting, summarizing, restructuring, explaining, brainstorming, first-pass analysis, code) and tasks where it is weak or risky (exact recall of facts, arithmetic without tools, current events without search, decisions needing accountability).
- **AI2.2** Choose between three ways of working: **automation** (AI does it, you check), **augmentation** (you work together step by step) and **agency** (AI acts on your behalf with tools), and justify the choice for a task.
- **AI2.3** Decide when *not* to use AI: when errors are costly and hard to catch, when the data can't leave your control, or when doing it yourself is the point (learning, judgment, relationships).
- **AI2.4** Break a large task into steps and decide which steps to hand off and which to keep.
- **AI2.5** Estimate whether checking AI output will take longer than doing the task yourself, and choose accordingly.

## AI3. Giving context and instructions (25%)

- **AI3.1** Turn a vague request into a clear brief that states the goal, the audience and what "done" looks like.
- **AI3.2** Supply the context the model can't guess: source material, numbers, constraints, definitions, prior decisions.
- **AI3.3** Specify the output: format, length, structure, tone, and what to leave out.
- **AI3.4** Use examples well: show one good example of the output you want, and say which features of it matter.
- **AI3.5** Ask the model to state assumptions, ask clarifying questions, or flag uncertainty instead of guessing.
- **AI3.6** Iterate: diagnose what went wrong in an output (missing context, unclear goal, wrong format) and fix the instruction rather than just asking again.
- **AI3.7** Give the model its source material directly (paste, upload, connect) rather than relying on its memory when accuracy matters.
- **AI3.8** Split a complex request into stages (outline, then draft, then check) when one-shot results are poor.

## AI4. Judging the output (20%)

- **AI4.1** Check factual claims, numbers, quotes and citations against original sources before using them.
- **AI4.2** Recognize the warning signs of made-up content: precise-sounding specifics with no source, citations that can't be found, quotes that are too neat.
- **AI4.3** Check an output against the brief: did it answer the actual question, follow the constraints, and include everything required?
- **AI4.4** Spot weak reasoning: unsupported leaps, missing alternatives, one-sided framing, and confident tone covering thin evidence.
- **AI4.5** Recognize bias and blind spots: whose perspective is missing, what was assumed about the audience, and where the training data might skew answers.
- **AI4.6** Verify AI-written code or calculations by running or re-deriving them, not by reading them.

## AI5. Using it responsibly (15%)

- **AI5.1** Decide what data may go into which AI tool: confidential, personal, customer and regulated data, and the difference between approved work tools and personal accounts.
- **AI5.2** Recognize prompt injection: instructions hidden in emails, web pages or documents that try to redirect an AI tool, and respond safely.
- **AI5.3** Apply basic copyright and ownership sense: don't ask AI to reproduce protected work, and check whether outputs closely copy a source.
- **AI5.4** Be open about AI's role when it matters: disclosure norms at work, school and in publishing, and taking ownership of the final result.
- **AI5.5** Know that organizations using AI may have legal duties, for example the EU AI Act's requirement that staff have sufficient AI literacy, and follow your organization's AI policy.
- **AI5.6** Recognize higher-risk uses (hiring, lending, health, legal, safety) where AI decisions need human review and extra care.

## AI6. Reusable workflows (10%)

- **AI6.1** Recognize a repeated task worth turning into a reusable prompt, template, skill or automation.
- **AI6.2** Write a reusable instruction that holds up for different inputs: inputs, steps, output format, rules and one example.
- **AI6.3** Know what tool use, connectors and agents add to a workflow, and the extra checks they need.
- **AI6.4** Measure whether an AI workflow actually helps: time saved, error rate, rework, and what the checking costs.
