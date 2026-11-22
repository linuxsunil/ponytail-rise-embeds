# How to use these scenario embeds in Rise 360

## What this is

An embed is a short scenario where the learner makes decisions and sees feedback on each one. It runs inside an Articulate Rise 360 lesson. You don't need to build anything from scratch. You copy a file into Rise, and you can change the words in it to suit your topic.

## What you need

- An Articulate Rise 360 account, with a lesson you can edit.
- A text editor. Notepad is fine.
- That's it.

## How to add it to Rise

1. Open the embed's HTML file (for example, `difficult-feedback-scenario-v1.html`) in Notepad.
2. Click inside the file, press **Ctrl + A** to select everything, then press **Ctrl + C** to copy.
3. In Rise 360, click **+** to add a block, then choose **Embed**.
4. Click into the code field and press **Ctrl + V** to paste.
5. Set the block height to **700px** to start.
6. Click **Preview**. If the bottom of the scenario is cut off, increase the height by 50px and preview again. Repeat until the whole scenario fits.

## How to change the scenario topic

The scenario text lives in one place: the line that starts with `d1:` near the top of the script section. In the file, it looks like this:

```
d1: { n: 1, text: "You lead a team of six. Priya has missed two project deadlines this month, and your manager has asked you to address it. Where do you give the feedback?",
```

Here is the same line changed to a compliance topic:

```
d1: { n: 1, text: "You manage a team of six. Sam has been saving client files to a personal USB drive. Where do you raise it?",
```

What changed: only the words between the quote marks after `text:`. Everything else on the line stayed exactly the same.

**Only change the text inside the quote marks, nothing else.**

Rules for the text inside the quotes:

- Don't type a double quote mark (") inside the sentence. It will break the embed. Use single quotes or rephrase instead, for example "Sam's files" is fine.
- Keep the sentence on the same line.
- Keep it short enough to read on a phone.

After you edit the file, save it in Notepad, then copy the whole file again (Ctrl + A, Ctrl + C) and paste it into the Rise embed code field, replacing the old code.

## How to change the choices and feedback

Each choice has three parts: the button text (`label`), the points, and the feedback (`consequence`). Here is the first choice from the same decision, before:

```
{ label: "Book a private one-to-one this week.", points: 1, next: "d2",
  consequence: "Effective. A private setting lets Priya respond without an audience, which makes an honest conversation more likely." }
```

And after, for the compliance topic:

```
{ label: "Speak to Sam privately and ask them to move the files to the approved system today.", points: 1, next: "d2",
  consequence: "Effective. A private conversation with a clear instruction and deadline fixes the risk without embarrassing Sam." }
```

What changed: the words inside the quotes after `label:` and `consequence:`. The `points: 1` stayed as it was. Points are `1` for the right answer and `0` for a wrong one. Don't change them unless you mean to change which answer counts as right.

Same rule as before: only change the text inside the quote marks.

## What NOT to touch

- Anything inside the `<script>` section that isn't a quote-mark text. That includes words like `function`, `const`, `if`, `else`, and anything with brackets `{ }`, `( )` or `[ ]`.
- The line that says `const nodes = {` and the closing `};` after it. Don't delete or rename them.
- The commas and brackets at the ends of lines. Each line ends the way it started.
- The `next:` values (`"d2"`, `"d3"`, `"end"`). They tell the scenario where to go next. Only change one if you are also changing the structure, and get help first.
- Anything outside the script section, such as the styling at the top of the file. You don't need to change it to change the content.

If you break something by accident, press **Ctrl + Z** in Notepad to undo, or copy the file again from the original.

## Mobile

The scenario works on phones and tablets. Still, test it before you publish. Open the lesson on a real phone (the preview link from Rise works on a phone's browser). Check that:

- The choice buttons are easy to tap.
- The text doesn't run off the screen.
- The whole scenario fits in the block height.

If it doesn't fit on a phone, increase the block height in steps of 50px.

## Getting help

If something doesn't work, or you want a new feature, open an issue on the project's GitHub page:

https://github.com/linuxsunil/ponytail-rise-embeds/issues

Include the file name, what you changed, and what you expected to happen. A screenshot of the Rise preview helps too.
