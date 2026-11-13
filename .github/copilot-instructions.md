# Copilot instructions

## Build, test, and lint

- The quiz is a single static `index.html`; no install, build, server, test runner, or linter is configured.
- Run it by opening `index.html` in a browser. On Windows, `Start-Process .\index.html` opens the default browser.
- For a focused manual check, answer one question and verify the feedback, score, progress, and Next button state. To check the results screen, complete all 10 questions; reload to reset.
- There is no automated single-test command. Use the integrated browser for browser-level checks.

## Architecture

- The markup, styles, and application logic all live in `index.html`. The page works directly from a `file://` URL.
- The `questions` array is the quiz data source. Each entry has a question, four answers, a zero-based `correct` answer index, and an explanatory `fact`.
- Quiz state is held in `current`, `score`, and `answered`. `renderQuestion()` draws the current question, `chooseAnswer()` locks choices and updates score/feedback, and `showResults()` displays the final score. `restart()` resets the quiz.
- CSS custom properties define the shared palette; setting `data-theme="dark"` on the root switches the theme. The decorative hex grid is an inline SVG behind the quiz content.

## Codebase conventions

- Keep the app self-contained in `index.html`; there are no framework components or module boundaries.
- Preserve the answer-index mapping in `questions` when editing quiz content, and keep the Next button disabled until an answer is selected.
- Use native buttons for quiz actions. Keep progress exposed as a `progressbar` and question/feedback changes announced through the existing live region.
- Theme-specific styling belongs in the root CSS variables and `[data-theme="dark"]` overrides. Use the existing DM Sans and Space Grotesk font stack, with system fallbacks.
