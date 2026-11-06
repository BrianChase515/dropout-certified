# How Dropout Certified exams work

Learning is free and open. The exam is where the certificate is earned, so it's built to be hard to fake. Everything below is public on purpose: you should know exactly how you'll be judged.

## Both tracks

- **Passing:** 75 or more overall, and at least 50% in every domain. Nobody passes on one strength alone.
- **With distinction:** 90 or more.
- **Retakes:** after 7 days, with fresh questions and tasks.
- **The certificate** shows your name, the track and version (for example "AI Essentials v1, Nov 2026"), your overall and per-domain scores, the date, and a unique ID with a public verify page. You can choose to show your graded hands-on work there as a portfolio.
- **Wording:** a Dropout Certified certificate is a certificate of demonstrated skill. It is not a degree, a diploma or an accreditation, and it never claims to be.
- **Appeals:** any hands-on score can be appealed, and a person reviews it.

## AI Essentials v1

| Part | What it is | Time | Share of score |
|---|---|---|---|
| A. Scenarios | 40 multiple-choice questions, mostly "what should you do here?" situations, drawn by domain weight from a private bank much larger than the exam. Some ask you to choose two. | 45 min | 50% |
| B. Hands-on | Two tasks: one where you **build** something with AI (a brief, a reusable instruction, a work plan) and one where you **judge** AI output (find the errors, spot the risks, fix it). You may use any AI tool in Part B. | 60 min | 50% |

**How Part B is scored.** Each task has 4 criteria, each scored 0 to 3:

- **Build tasks:** goal and audience are clear; the right context is supplied; the output was checked against the source; the result is fit to use as is.
- **Judge tasks:** errors and risks are found; you explain why each matters; your corrections are accurate; your corrected version meets the original brief.

A score of 3 means "a demanding manager would accept this without changes." Two independent AI grading passes score your work against the rubric and quote your submission as evidence. Where they disagree, a person decides.

**What the exam rewards:** judgment. Using AI well in Part B is the skill being tested, so what earns points is what you asked for, what you caught, and what you fixed.

## Data Analysis with SQL v1

| Part | What it is | Time | Share of score |
|---|---|---|---|
| A. Queries | 12 tasks on your own freshly generated shop database (same schema as the practice database). Each answer is a single SQLite query. | 75 min | 65% |
| B. Analysis | One business question answered in under 200 words for a manager, with the queries you used. | 40 min | 35% |

**How Part A is graded.** Your query is run against your database *and* against a second, hidden database with different data. It passes only if it returns the right rows on both, so you must write a real query, not paste in numbers. Column names don't matter; the rows and the order (where the task asks for an order) do.

**How Part B is scored.** 4 criteria, each 0 to 3: you define the question before calculating; your numbers are correct and reproducible from your queries; you sanity-check the result (watch for duplicate rows after joins, missing values and outliers); and you state a clear finding with its main caveat.

**AI in the SQL exam.** You may use AI to help write queries, as analysts do on the job. The hidden database and the written analysis mean you still need to understand what your query does.

## How to prepare

Use the Dropout Certified study coach. It won't mark a learning goal as ready until you've shown it on fresh questions, and it won't let you sit a practice exam until every domain is ready. If you pass the coach's practice exam at 80 or more, you're in good shape for the real one.
