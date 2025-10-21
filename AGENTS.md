# Repository Guidelines

## Project Structure & Module Organization
- `public/` holds the production-ready static site. `public/index.html` centralizes markup, inline styles, and minimal scripting; add new assets inside `public/assets/` and reference them with absolute paths to keep rewrites working.
- `firebase.json` configures Firebase Hosting to serve everything through `index.html`. Update rewrites or cache rules here when introducing new routes or service workers.

## Build, Test, and Development Commands
- `firebase emulators:start --only hosting` runs the site locally with Hosting rewrites applied. Use this before deploying any structural change.
- `firebase deploy --only hosting` publishes the current `public/` snapshot. Always review the emulator output first.
- `npx serve public` is a lightweight alternative for quick HTML/CSS checks when you do not need Firebase-specific behavior.

## Coding Style & Naming Conventions
- Match the existing 4-space indentation and keep HTML attributes in lowercase. Favor semantic tags (`section`, `main`, `article`) over generic `<div>` wrappers where possible.
- Extend the design tokens declared in the root `:root` block; introduce new colors as additional CSS variables instead of hardcoding values.
- Name new files and assets in kebab-case (e.g., `daily-summary.png`) to align with current references.

## Testing Guidelines
- There is no automated test suite. Validate markup through the W3C validator and run Lighthouse (Chrome DevTools) to confirm accessibility and performance regressions.
- For behavior changes, exercise primary user journeys in the Firebase emulator: initial load, scrolling, and outbound links. Log issues in the PR if a manual check is skipped.

## Commit & Pull Request Guidelines
- Follow the short, imperative subject style seen in history (`Update canonical URL...`, `publish`). Keep subjects under 72 characters and include context in the body when needed.
- Reference related issues in the description (`Closes #12`) and attach before/after screenshots or screen recordings for visual updates.
- Ensure the PR summary lists: scope of change, validation performed (commands run, browsers tested), and any follow-up work.
