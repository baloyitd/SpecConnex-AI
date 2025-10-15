## 1. Improve Generate Draft UX and Model Loading

Task
- Stream sections as they are generated; do not wait for full document before showing sections.
- Preload AI models at app startup; select the correct model at Generate Draft click.
- Add clear visual progress indicators and per-section status (queued, generating, done, failed).

Acceptance criteria
- Each section appears in the UI immediately when its generation completes.
- A progress bar or per-section spinner shows real-time status and percentage.
- Models are loaded on app init (with status displayed) and selection happens instantly when the button is clicked.
- Generate Draft triggers section-by-section generation rather than a single long blocking call.
- Failures in one section do not block display of other completed sections.

Implementation steps (short)
1. Preload models on startup; expose model status in a Model Status Bar.
2. Change generation controller to generate sections sequentially or concurrently but stream results back to the UI as each completes.
3. Add per-section status states and UI components: queued → generating → done → error.
4. Add a global progress indicator (overall %) and per-section spinners; update incrementally.
5. Ensure model selection logic chooses the correct preloaded model per task before each section run.
6. Add unit/integration tests to validate streaming behavior, status transitions, model preloading, and failure isolation.

Deliverables
- Model preload hook and status UI.
- Streaming section generator and controller.
- Per-section UI components and global progress indicator.
- Tests asserting sections are rendered on completion and model selection occurs without delay.

