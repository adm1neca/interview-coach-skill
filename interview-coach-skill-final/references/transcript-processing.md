# Transcript Processing Guide

This guide covers how to clean, parse, and analyze interview transcripts for maximum learning.

---

## Step 1: Clean the Transcript

Raw transcripts from Granola, Otter, Tactiq, or other tools are messy. Clean before analyzing.

### What to Remove
- Filler words: "um," "uh," "like," "you know," "basically"
- False starts: "I was going to— actually, let me say—"
- Duplicated speaker lines (transcription errors)
- Timestamps (unless needed for specific analysis)

### What to Keep
- Speaker labels (Interviewer / Candidate)
- Substantive content, even if awkwardly phrased
- Pauses marked as [pause] if they're meaningful (shows thinking)
- Questions exactly as asked (don't paraphrase)

### Cleaning Prompt

```
TASK: Clean this interview transcript.

INPUT: [paste raw transcript]

INSTRUCTIONS:
- Remove filler words (um, uh, like, you know, basically) without changing meaning
- Remove false starts and self-corrections, keeping the final version
- Fix obvious transcription errors
- Keep speaker labels
- Preserve the actual content and meaning

OUTPUT: Cleaned transcript ready for analysis
```

---

## Step 2: Parse into Q&A Units

Structure the transcript for systematic analysis.

### Parsing Prompt

```
TASK: Parse this transcript into question-answer pairs.

INPUT: [cleaned transcript]

FOR EACH PAIR, CAPTURE:
- question_number (Q1, Q2, etc.)
- question_text (verbatim)
- answer_text (verbatim, trimmed of filler)
- topic: behavioral / technical / strategic / situational / cultural
- competency_tested: leadership / collaboration / problem-solving / communication / technical / etc.
- word_count: number of words in answer
- did_answer_question: Yes / Partial / No
- follow_up_triggered: Yes / No (did interviewer ask for more?)

OUTPUT FORMAT:
1. Table with all Q&A pairs and metadata
2. Summary stats:
   - Total questions: ___
   - Fully answered: ___
   - Partially answered: ___
   - Not answered: ___
   - Average answer length: ___ words
   - Longest answer: ___ words (flag if >300)
   - Follow-ups triggered: ___
```

---

## Step 2.5: Anti-Pattern Scan

Before scoring, scan the transcript against known failure patterns. This provides an objective checklist that doesn't rely on the coach to "notice" problems organically.

### Detection Checklist

| Anti-Pattern | Detection Heuristic | Severity | Fix Reference |
|---|---|---|---|
| **Rambling** | Any answer >3 minutes / >300 words without a check-in or pause | High | Constraint ladder drill |
| **Verbal crutches** | Same filler phrase ("So basically...", "At the end of the day...") appears 3+ times across answers | Medium | Record and playback — awareness is often enough |
| **"We" default** | >50% of action verbs in an answer use "we" instead of "I" | High | I/we audit drill |
| **Never clarifies** | Candidate asks zero clarifying questions across entire interview | Medium | Question-before-answer drill |
| **Conflict avoidance** | Stories about "challenges" contain no actual disagreement, tension, or failure | High | Tension-mining drill |
| **Question dodging** | Answer addresses a related topic but not what was actually asked | High | Question-decoding drill |
| **Over-claiming** | Impact claims without specific role, or "I" replacing obvious team effort | High | Constraint practice (add realistic limitations) |
| **Jargon hiding** | >5 domain-specific terms per 100 words with no plain-language explanation | Medium | "Explain to a 10-year-old" drill |
| **Front-loaded hedge** | Answer starts with "I think maybe...", "It's hard to say but...", "I'm not sure if..." | Medium | Opening line practice |
| **Story recycling** | Same story used for 2+ different questions | Medium | Storybank gap analysis |
| **Abrupt ending** | Answer stops without impact/outcome/takeaway — just trails off | Medium | "Land the plane" drill: practice the last 15 seconds |
| **Monologue mode** | Answers average >2 minutes with no pauses, check-ins, or reads of interviewer signals | Medium | Signal-reading practice |
| **Missing "so what"** | Story has actions but never connects to why it mattered | High | Impact chain drill |
| **Defensive deflection** | When pressed on a weakness, redirects to strengths without acknowledging the gap | Medium | Gap-handling drill |
| **Rehearsed robotics** | Answer sounds memorized — identical phrasing to previous practice, no adaptation to question nuance | Medium | Variation practice: same story, different framings |

After scanning, include detected anti-patterns in the analysis output. Each detected pattern should reference which Q# triggered it and link to the specific fix.

---

## Step 3: Multi-Lens Scoring

Run the parsed transcript through evaluative lenses. **Important**: Which lenses you run depends on the triage decision tree in SKILL.md. If a primary bottleneck is identified after initial scoring, scope the analysis accordingly rather than running all four lenses mechanically.

### Lens 1: Hiring Manager Perspective

The person who'll champion you (or not) in the hiring committee.

```
LENS 1: HIRING MANAGER PERSPECTIVE

INPUTS:
- Role: [title]
- Company: [name]
- Parsed Q&A from above
- Company prep brief (values, priorities)
- Hiring manager LinkedIn (if available)

TASK:
Act as the hiring manager for this role.

For each answer, score 1-5 on:
- Substance
- Structure
- Relevance
- Credibility
- Differentiation

After each answer:
- One concrete improvement (specific missing evidence, numbers, or tradeoffs)
- Root cause pattern (if detected — see rubrics-detailed.md root cause taxonomy)
- Would this answer move candidate forward? Y/N/Maybe + brief why

SUMMARY TABLE:
| Q# | Sub | Str | Rel | Cred | Diff | Avg | Forward? | Root Cause | Top Fix |
|----|-----|-----|-----|------|------|-----|----------|------------|---------|

SIGNAL-READING ANALYSIS:
- Questions where follow-up indicated interest (positive signal):
- Questions where interviewer moved on quickly (likely negative):
- Questions where interviewer redirected (answer wasn't landing):
- Missed signals: moments where the candidate should have adapted but didn't

ANTI-PATTERNS DETECTED:
[List from Step 2.5 scan with Q# references]

FINAL OUTPUT:
- Overall impression: Strong Hire / Hire / Mixed / No Hire
- 3 strongest answers (why they worked)
- 3 weakest answers (specific gaps + root cause patterns)
- Biggest concern about this candidate
- One-sentence justification for your decision
- Primary bottleneck dimension → triage recommendation (see SKILL.md decision tree)
```

### Lens 2: Skeptical Specialist

The senior practitioner checking if you actually know what you're talking about.

```
LENS 2: SKEPTICAL SPECIALIST

INPUTS:
- Candidate's role/discipline: [engineer / PM / designer / data scientist / etc.]
- Parsed Q&A

TASK:
Role-play as a skeptical senior specialist in the candidate's field.

For each technical or domain-specific answer, identify where they:
- Hand-waved technical details
- Skipped constraints or edge cases
- Over-claimed impact without methodology
- Used jargon to hide lack of depth
- Missed obvious alternatives or tradeoffs

For each answer:
- One "dig deeper" question that would expose gaps
- Score 1-5: Technical accuracy
- Score 1-5: Depth vs breadth (1=too shallow, 5=appropriate)
- Score 1-5: Acknowledgment of tradeoffs

FLAG: Answers that would make a specialist skeptical
```

### Lens 3: Company Values Alignment

Checking if the candidate demonstrates the company's specific principles.

```
LENS 3: VALUES ALIGNMENT

INPUTS:
- Company: [name]
- Company values/principles: [list them]
- Parsed Q&A

TASK:
Score each answer on alignment with company principles.

FOR EACH PRINCIPLE:
- Which answers touched it? (list Q#s)
- How explicitly? (implicit mention / direct example)
- Score 1-5: How well the story demonstrates this value

IDENTIFY:
- Principles completely missed
- Principles mentioned but not demonstrated with evidence
- Strongest principle alignment (which answers showed which values best)

SUGGEST:
For each missed principle:
1. Which existing story could have surfaced it?
2. How to weave it into an answer next time (specific insertion point)
```

### Lens 4: Calibration (Brevity & Clarity)

Checking if answers are too long, too jargon-heavy, or meandering.

```
LENS 4: CALIBRATION

INPUTS:
- Parsed Q&A

TASK:
For each answer >150 words, create:
- 30-second version (≤80 words)
- 90-second version (≤220 words)
- "Explain to a 10-year-old" version

ANALYZE:
- Jargon density (domain-specific terms per 100 words)
- Hedging frequency (count: "maybe," "kind of," "sort of," "I think")
- Passive voice usage (flag sentences)
- Meandering score 1-5 (5 = every sentence advances the answer)

FOR EACH ANSWER:
- Core point (one sentence)
- Redundant phrases or tangents to cut
- Where to cut without losing substance

SUMMARY:
- Average answer length: ___ words
- % of answers that meandered (score <3): ___
- Most common filler phrases: ___
- Clarity grade: A / B / C / D
```

---

## Step 4: Synthesize into Interview Delta

Combine all lens outputs into actionable summary.

```
INTERVIEW DELTA SHEET

INTERVIEW: [Company] - [Role] - [Date]

OVERALL SCORES:
Substance: ___ | Structure: ___ | Relevance: ___ | Credibility: ___ | Differentiation: ___
Calibration band: [early career / mid-career / senior / executive]
Hiring Manager Assessment: Strong Hire / Hire / Mixed / No Hire

PRIMARY BOTTLENECK: [dimension]
TRIAGE PATH: [coaching path chosen per SKILL.md decision tree]

ANTI-PATTERNS DETECTED: [list with Q# references]

3 FIXES FOR NEXT TIME (ordered by triage priority):
1. [Specific behavior] - because [evidence from this interview]
   Root cause: [pattern from taxonomy]
   Drill: [exact practice exercise]
2. [Behavior] - because [evidence]
   Root cause: [pattern]
   Drill: [exercise]
3. [Behavior] - because [evidence]
   Root cause: [pattern]
   Drill: [exercise]

2 STORIES TO RETIRE (OR REWORK):
1. [Story title] - Why: overused / thin evidence / low differentiation
2. [Story title] - Why: [reason]

1 NEW STORY TO ADD:
Gap observed: [competency missing]
Suggested source: [which experience could fill this]

CARRY FORWARD:
[One strong behavior from this interview to maintain]

REFLECTION PROMPTS:
- How does this feedback compare to your gut feeling about the interview?
- Of the growth areas above, which feels most within your control?
- What would it look like to practice that this week?

NEXT ACTIONS (co-created with candidate):
[ ] Update storybank: retire [stories], add [new story]
[ ] Run drill: [specific exercise for priority growth area]
[ ] Practice: [weak Q# from this interview] until scores 4+
[ ] Review before next interview: this delta sheet
```

---

## Step 5: Update Tracking (Full System)

After each interview, update the persistent failure mode tracker.

```
FAILURE MODE TRACKER UPDATE

Add this interview's data:

PATTERN METRICS:
- % questions actually answered: ___
- Average scores: Sub ___ | Str ___ | Rel ___ | Cred ___ | Diff ___
- Talk:listen ratio estimate: ___
- Filler word rate: ___ per minute
- Answer length consistency (std dev): ___

COMPETENCY BREAKDOWN:
Top 3 weak competencies:
1. [competency] - avg score ___ across Q#[list]
2. [competency] - avg score ___
3. [competency] - avg score ___

TOP 3 OVERUSED CRUTCHES:
1. [pattern] - appeared in Q#[list]
2. [pattern] - appeared in Q#[list]
3. [pattern] - appeared in Q#[list]

TREND COMPARISON:
vs. Previous interview:
- Improving: [list]
- Stagnant: [list]
- Declining: [list]

CELEBRATION:
What improved since last time: ___

SELF-REFLECTION:
What patterns are you noticing? ___
What feels different now vs. earlier? ___
```

---

## Timing Guidelines

- Clean transcript: 5-10 minutes
- Parse into Q&A: 10 minutes
- Lens 1 (Hiring Manager): 15 minutes
- Lens 2 (Specialist): 10 minutes
- Lens 3 (Values): 10 minutes
- Lens 4 (Calibration): 10 minutes
- Synthesize delta: 10 minutes

**Total: ~60-75 minutes for full analysis**

For Quick Prep users: Run only Lens 1 and skip to delta sheet (~30 minutes).
