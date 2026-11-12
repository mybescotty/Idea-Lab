# TestRun — Build Plan

Goal: one self-contained `projects/test-run/index.html` (inline CSS + JS, no build step,
no external libraries). It must work opened locally (`file://`) or from GitHub Pages.

> Only build this when the idea's Status in `IDEAS.md` is changed to `Building`.

## Step 1 — Page skeleton
- `<!doctype html>`, `<meta charset="utf-8">`,
  `<meta name="viewport" content="width=device-width, initial-scale=1">`,
  `<title>TestRun — Pipeline Check</title>`.
- Sections: `<header>`, `#details`, `#stages`, `#visits`.

## Step 2 — Styling (inline `<style>`)
- CSS variables on `:root` for colours; a `@media (prefers-color-scheme: dark)` override.
- Centered column, `max-width: 640px`, 16px side padding so it fits on phones.
- Green success banner; simple cards with rounded corners.

## Step 3 — Static content
- Banner: "✅ Idea Lab pipeline is working".
- Details card: Idea "TestRun", submitted by Scott Davis, 2026-11-11.

## Step 4 — Storage helpers (inline `<script>`)
- `const KEY = 'testrun.v1'`.
- `load()` → parse JSON from `localStorage` (inside `try/catch`), falling back to
  `{ visits: [], stages: {} }`.
- `save(state)` → `JSON.stringify` into `localStorage` (inside `try/catch`, so the page
  still works if storage is blocked, e.g. in a private window).

## Step 5 — Visit log
- On page load, push `new Date().toISOString()` to `state.visits` and save.
- Render the list newest first using `toLocaleString()`, plus "Opened N times".
- "Clear log" button → `confirm()` → empty `visits`, save, re-render.

## Step 6 — Stage checklist (nice-to-have)
- Four checkboxes: New, Overview written, Building, Done.
- On change, store in `state.stages` and save; restore checked state on load.

## Step 7 — Copy test report (nice-to-have)
- Button builds text such as
  `TestRun check — opened 5 times, last at <time>, stages done: New, Overview written`
  and calls `navigator.clipboard.writeText`, with a fallback of selecting text in a
  `<textarea>` if the clipboard API isn't available.

## Step 8 — Test
- Open the file directly in a browser: the banner shows, the visit count goes up on refresh.
- Tick stages, refresh: ticks stay.
- Clear log: the list empties.
- Check on a phone-width screen (around 375px): no sideways scrolling.
- Optionally enable GitHub Pages and open `/projects/test-run/` to confirm it works there.

## Step 9 — Finish
- Commit `index.html`, set the idea's Status to `Done` in `IDEAS.md`.
