# ponytail-rise-embeds

> Branching scenario embeds for Articulate Rise 360, built with Ponytail discipline — vanilla JS, no frameworks, single file per embed.

Self-contained HTML embeds for Articulate Rise 360. Each embed is one HTML file that runs inside a Rise **Embed** block with no external dependencies.

**Audience:** instructional designers and eLearning developers building scenarios, knowledge checks and interactions in Rise 360.

## Using an embed in Rise

1. Open the embed's `.html` file and copy the whole file contents.
2. In Rise 360, add an **Embed** block to your lesson and paste the HTML into the embed code field.
3. Set the block height to fit the embed (the scenario is designed for a 640px-wide column; 700px height is a sensible start, then preview on mobile and adjust).
4. Preview the lesson and complete the embed once to check the summary screen.

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

Built by [Sunil](https://github.com/linuxsunil), Senior Instructional Designer.

Coding discipline: [Ponytail](https://github.com/dietrichgebert/ponytail) by Dietrich Gebert — write only what the task needs.
