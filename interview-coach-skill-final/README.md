# Interview Coach v5

A high-rigor Claude skill for interview coaching — not just prep. It adapts to what you actually need based on your patterns, not a one-size-fits-all assembly line.

This skill is command-driven with conditional logic: after scoring, it branches coaching based on what the data reveals about your specific bottlenecks.

---

## What You Get

- **Adaptive coaching** that triages your bottlenecks and branches accordingly — not the same assembly line for every candidate
- **Five-dimension scoring**: Substance, Structure, Relevance, Credibility, and Differentiation — calibrated to your seniority level
- **Evidence-enforced feedback**: every claim tagged to source, with a hard cap on low-confidence inferences
- **Root cause diagnosis**: scores map to underlying patterns (status anxiety, narrative hoarding, conflict avoidance, etc.) with targeted fixes
- **Storybank with rapid-retrieval drills**: stories you can actually access under pressure, not just a well-organized filing cabinet
- **Full mock interviews**: 4-6 question simulated interviews with holistic arc feedback, not just individual answer scoring
- **Psychological readiness**: pre-interview routines, mid-interview recovery, and post-interview processing
- **Post-offer negotiation coaching**: scripts, strategy, and specific language for compensation conversations
- **Differentiation as a first-class dimension**: earned secrets and spiky POVs integrated into every workflow, not an optional add-on
- **Self-assessment calibration**: tracks the gap between how you think you're doing and how you're actually doing
- **Outcome tracking**: correlates practice scores with real interview results to verify the coaching is working

---

## Quick Start (5 minutes)

### Option 1: Claude Projects (recommended)

1. Clone or download this repo.
2. In Claude, create a project named `Interview Coach`.
3. Upload `SKILL.md` and the `references/` folder to project skills/knowledge.
4. Upload your resume (or paste resume text).
5. Run `/kickoff`.

### Option 2: Single conversation

1. Copy the contents of `SKILL.md`.
2. Start a new Claude chat.
3. Paste `SKILL.md` at the beginning.
4. Upload or paste your resume.
5. Run `/kickoff`.

If your environment does not persist context, repeat steps 2-3 per new session.

---

## Commands

| Command | Purpose | Typical Output |
|---|---|---|
| `/kickoff` | Setup profile, track, and preferences | Kickoff summary + first 7-day plan |
| `/prep [company]` | Build role-specific prep brief (format-aware, culture-aware) | Format guidance, culture read, competencies, predicted Qs, story mapping |
| `/analyze` | Analyze transcript with triage-based coaching | Per-answer 5-dimension scoring + decision tree + interview delta |
| `/practice` | Run drill rounds (with progression gating) | Round debrief + self-assessment delta + targeted adjustment |
| `/mock [format]` | Full simulated interview (4-6 Qs) | Holistic arc feedback, signal-reading notes, energy trajectory |
| `/stories` | Build/manage storybank + rapid-retrieval drill | Story table + earned secrets + gap analysis + retrieval drill |
| `/concerns` | Anticipate interviewer concerns | Concern-counter-evidence map |
| `/questions` | Generate interviewer questions | 5 tailored, non-generic questions |
| `/hype` | Pre-interview confidence + psychological warmup | 60-second reel + 3x3 sheet + focus cue |
| `/thankyou` | Post-interview follow-up drafts | Thank-you note + variants |
| `/progress` | Trends, self-calibration, outcome tracking | Self-assessment delta + outcome correlation + coaching meta-check |
| `/negotiate` | Post-offer negotiation coaching | Offer analysis + strategy + scripts + specific language |
| `/help` | Show command menu | Full command list |

---

## Fast Workflow Examples

### 1) Initial setup

```text
/kickoff
```

Expected output:

- Track selected (`Quick Prep` or `Full System`)
- Profile snapshot (strength signals and concern areas)
- 7-day action plan

### 2) Before an interview

```text
/prep Stripe
```

Then provide:

- Job description
- Role/seniority
- Optional interviewer names or profile links

Expected output:

- `What They Optimize For`
- `Your Best Positioning`
- `Likely Concerns + Counters`
- `Predicted Questions (7-10)`
- `Story Mapping`
- `Questions To Ask Them`

### 3) After an interview

```text
/analyze
```

Then paste transcript text.

Expected output:

- Per-answer score blocks
- `Scorecard`
- `What Is Working`
- `Top 3 Gaps To Close`
- `Storybank Changes`
- `Priority Move (Next 72 Hours)`

### 4) Drill practice

```text
/practice
```

Drills (in progression order — advance when you meet gating thresholds):

- `/practice ladder` — Constraint drills (30s, 60s, 90s, 3min)
- `/practice pushback` — Handle skepticism and interruption
- `/practice pivot` — Redirect when questions don't match prep
- `/practice gap` — Handle "I don't have an example" moments
- `/practice role` — Role-specific specialist scrutiny
- `/practice panel` — Multiple interviewer personas
- `/practice stress` — High-pressure simulation
- `/practice retrieval` — Rapid-fire story matching

Expected output each round:

- `Round Debrief`
- `What Worked`
- `Gaps`
- `Scorecard` (5 dimensions)
- `Self-Assessment Delta`
- `Next Round Adjustment`

### 5) Full mock interview

```text
/mock behavioral Stripe
```

Runs a complete 4-6 question interview simulation with holistic feedback on:

- Overall impression and hiring signal
- Energy trajectory and pacing across the full arc
- Story diversity and selection quality
- Signal-reading (did you adapt to interviewer cues?)
- Per-question scoring + holistic patterns only visible across the full session

### 6) Post-offer negotiation

```text
/negotiate
```

Then provide offer details, competing offers, and ideal outcome. Get:

- Market position analysis
- Negotiation strategy with priority ordering
- Exact scripts for the conversation
- Fallback language for pushback

---

## Tracks

### Quick Prep

Best when interview timeline is short.

- Prep brief
- Focused transcript analysis
- Immediate next actions

### Full System

Best when running a multi-week search.

- Storybank management with rapid-retrieval drills
- Multi-lens transcript analysis with decision tree triage
- Pattern and trend tracking with self-assessment calibration
- Differentiation coaching integrated into all workflows
- Full mock interview simulations
- Outcome tracking (correlate practice with real results)
- Post-offer negotiation coaching
- Drill progression with gating thresholds

Choose during `/kickoff`. You can switch later.

---

## Repository Structure

```text
interview-coach-skill-final/
├── SKILL.md
├── README.md
└── references/
    ├── rubrics-detailed.md
    ├── role-drills.md
    ├── differentiation.md
    ├── transcript-processing.md
    └── storybank-guide.md
```

---

## Best Results

1. Share a real resume (not a high-level summary).
2. Include a full job description for `/prep` — and the interview format if you know it.
3. Use real transcripts for `/analyze`. The more you give it, the better the triage.
4. Keep a living storybank with `/stories`. Extract earned secrets for every story.
5. Run `/progress` weekly — it tracks your self-assessment accuracy, not just scores.
6. After real interviews, log outcomes. The system correlates practice scores with real results.
7. Run `/mock` before important interviews. Individual drills build skills; mocks test the full arc.

---

## FAQ

**Does this only work for tech roles?**
No. Core workflows are role-agnostic; role drills include PM, Engineering, Design, Data Science, Research, Operations, and Marketing.

**Can I use this outside Claude?**
Yes, but it is authored for Claude skill behavior. If using another model, copy `SKILL.md` and adapt as needed.

**Why is the feedback direct?**
The skill is intentionally high-candor and evidence-based. It still uses strengths-first delivery and self-reflection before critique. It also periodically checks whether the coaching is landing and adapts if not.

**What's different about v5?**
v5 adds adaptive triage (coaching branches based on your patterns), a 5th scoring dimension (Differentiation), root cause diagnosis, full mock interviews, drill progression with gating, post-offer negotiation, self-assessment calibration, outcome tracking, psychological readiness, signal-reading coaching, gap-handling frameworks, interviewer archetype simulation, and anti-pattern detection. The core philosophy shifted from "structured output" to "adaptive coaching" — the system now responds to what it observes, not just what you ask it.

---

## Contributing

Open an issue or PR with:

- Repro steps
- Current behavior
- Expected behavior
- Suggested fix (optional)

---

## Credits

Created by [Noam Segal](https://www.linkedin.com/in/noamsegal/).

---

## License

MIT
