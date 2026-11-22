# ponytail-rise-embeds

> Branching scenario embeds for Articulate Rise 360, built with Ponytail discipline — vanilla JS, no frameworks, single file per embed.

Self-contained HTML embeds for Articulate Rise 360. Each embed is one HTML file that runs inside a Rise **Embed** block with no external dependencies.

**Audience:** instructional designers and eLearning developers building scenarios, knowledge checks and interactions in Rise 360.

## Using an embed in Rise

New to this? Read the [step-by-step guide for instructional designers](USAGE.md) first.

If you're comfortable with HTML files, the short version:
1. Open the `.html` file, select all, copy.
2. In Rise 360, add an **Embed** block and paste.
3. Set block height to 700px, preview, adjust if needed.

## Customising the scenario data

Each scenario is driven by one `nodes` object in the `<script>` block:

```js
const nodes = {
  d1: {
    n: 1,                              // decision number shown as "Decision 1 of 4"
    text: "Question shown to the learner.",
    choices: [
      { label: "Option text.", points: 1, next: "d2",
        consequence: "Feedback shown after this choice." },
      { label: "Another option.", points: 0, next: "d2",
        consequence: "Why this choice is not quite right." }
    ]
  },
  d2: { n: 2, text: "...", choices: [ /* ... */ ] }
};
```

| Field | Purpose |
|---|---|
| `nodes` key (e.g. `d1`) | Node ID. `"d1"` is the start node. |
| `n` | Decision number shown to the learner. |
| `text` | The scenario prompt. |
| `choices[].label` | Button text. |
| `choices[].points` | `1` = effective, `0` = not quite. Summed into the score. |
| `choices[].next` | Next node ID, or `"end"` to show the summary. |
| `choices[].consequence` | Feedback shown after the choice. Write corrective or elaborative feedback here. |

Rules:

- Every `next` must be an existing node ID or `"end"`. A broken link is logged to the browser console.
- Points are binary (0 or 1) in this version.
- The decision count and score denominator are derived from the longest path through `nodes`, so no manual update is needed. Branches of different lengths use the longest one.

## Current embeds

| Embed | File | Status |
|---|---|---|
| Handling difficult feedback | `difficult-feedback-scenario-v1.html` | v1 |

## Tech approach

- Vanilla JavaScript and CSS in one HTML file.
- No frameworks, no build step, no CDN, no external fonts or scripts.
- One file per embed. Each embed is self-contained and can be pasted into Rise as-is.

## Credits

Coding discipline: [Ponytail](https://github.com/dietrichgebert/ponytail) by Dietrich Gebert — write only what the task needs.

---

## About the author

[Sunil Iyer](https://www.linkedin.com/in/sunil-iyer-b545964/) is a Senior Instructional Designer with 10+ years of experience building eLearning for global organisations. He specialises in AI-powered course development, SCORM/xAPI, and Articulate Rise 360 / Storyline 360.

[GitHub](https://github.com/linuxsunil) · [LinkedIn](https://www.linkedin.com/in/sunil-iyer-b545964/)
