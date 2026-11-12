# TestRun — Project Overview

> Source idea: "TestRun" in [`IDEAS.md`](../../IDEAS.md), submitted by Scott Davis on 2026-11-11.
> The idea's own description: *"this is to see if clade runs correctly."*

## Summary
TestRun is a check that the Idea Lab pipeline works from start to finish: an idea added to
`IDEAS.md` gets picked up by the scheduled Claude run, which writes a project folder and
updates the idea's status. Its only must-have is "output project". To give that
output something you can open and see, this overview treats TestRun as a tiny
**"Pipeline Check" page**: a single `index.html` that shows the project was created and
records when someone last opened it.

## Target users
- The submitter (Scott), confirming the scheduled idea check works.
- Anyone setting up a similar repo who wants a known-good example to compare against.

## Core features
1. **Output project** (the stated must-have): this folder, with `OVERVIEW.md` and
   `BUILD_PLAN.md`, and the idea's Status changed to `Overview written`.
2. A simple `index.html` (built later, when Status is set to `Building`) that:
   - shows a clear "✅ Idea Lab pipeline is working" message,
   - shows the idea's name, submitter and date,
   - keeps a visit log (date/time of each time it's opened) saved in `localStorage`,
   - has a "Clear log" button.

## Nice-to-haves
- A checklist of the pipeline stages (`New` → `Overview written` → `Building` → `Done`),
  where you tick the stage you've reached.
- A "Copy test report" button that copies a short text summary to the clipboard.
- Light/dark mode that follows the device setting.

## How it would work (screens / user flow)
One screen:
1. **Header:** "TestRun — Pipeline Check" with a green success banner.
2. **Idea details card:** name, submitter, date, current stage.
3. **Stage checklist** (nice-to-have): four tickable steps, saved between visits.
4. **Visit log:** newest first, with a count ("Opened 5 times") and a *Clear log* button.

Flow: open the page (on GitHub Pages or locally) → the visit is logged automatically →
tick off stages as the idea moves along → clear the log when finished testing.

## Data storage approach
`localStorage` only, under one key (e.g. `testrun.v1`), holding
`{ visits: [ISO timestamps], stages: { overview: true, building: false, ... } }`.
No sharing between people is needed, so no server or database.

## Open questions
- Is this just a one-off test that can be marked `Done` once the overview appears, or
  should the `index.html` page actually be built?
- The second must-have feature was left as the template placeholder (`<feature>`). Was
  there another feature you meant to add?
- Should test ideas like this be removed from `IDEAS.md` (or marked as examples) once
  the pipeline is confirmed working?
