# Instructions for Claude (scheduled idea check)

When asked to "check the ideas" (e.g. by a scheduled task):

1. Pull the latest default branch and read `IDEAS.md`.
2. Find every idea whose **Status** is `New`. Skip anything marked as an example.
3. For each new idea:
   - Pick a short kebab-case slug (e.g. `shared-shopping-list`).
   - Create `projects/<slug>/OVERVIEW.md` with: summary, target users, core features,
     nice-to-haves, how it would work (screens / user flow), data storage approach,
     open questions.
   - Create `projects/<slug>/BUILD_PLAN.md` with a step-by-step plan for building it as a
     **single self-contained `index.html`** (inline CSS + JS, no build step, works when
     opened from GitHub Pages or locally; use `localStorage` for saving data unless the
     idea needs sharing between people — then note the options).
   - In `IDEAS.md`, change that idea's Status to `Overview written` and add a line
     `- **Project:** [projects/<slug>](projects/<slug>/)`.
4. Do not delete or rewrite anyone's idea text, other than updating Status / Project lines.
5. Commit with a message like `Add overviews for: <idea names>` and push.
6. If there were no new ideas, make no commit.

Only build `index.html` when an idea's Status is changed to `Building` (by a person)
or when explicitly asked.
