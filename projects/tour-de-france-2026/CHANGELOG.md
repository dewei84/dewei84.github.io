# Changelog — Tour de France 2026 stage tracker

All notable changes to this page are documented here.

## 2026-07-16

### Added
- **Stage winner on the collapsed card** — each completed stage shows the winner's name and team on its own line beneath the terrain/date/time row.
- **Podium in the expanded view** — a 1–2–3 finish with each rider's team and time gap to the winner.
- **Jersey wearers in the expanded view** — all four classification leaders after each stage: Yellow (GC), Green (points), Polka-dot (KOM), and White (young rider), each with name and team.
- **"Today's stage" button** in the filter bar — resets to *All*, then scrolls to, opens, and briefly flashes today's stage. Today's stage also gets a persistent "Today" tag and yellow border. Driven by the viewer's real date, so it tracks the race automatically (exact-day match, falling back to the most recent stage on rest days and after the race).

### Changed
- Rebuilt the results data model to carry team names, full podiums with gaps, and per-stage jersey holders.
- Replaced previously fabricated results with verified data for Stages 1–11, sourced from Wikipedia, ProCyclingStats, and Cyclingnews — including corrected 2026 team affiliations (e.g. Kooij → Decathlon CMA CGM, Ayuso → Lidl-Trek, Alpecin → Alpecin-Premier Tech).
- Stage 1 (team time trial) now correctly shows no individual winner — the podium lists the three teams and their times.

### Fixed
- Raised the expanded drawer's max-height (480px → 1200px) so the taller podium + jersey content no longer clips.
- Moved the "today" highlight ring from the header button to the whole stage container so it wraps the full card when expanded.

### Known limitations
- Results data currently covers Stages 1–11; Stage 12 onward has route/profile/notes but no podium or jerseys yet.
- The first-week polka-dot (mountains) leader for a stage or two is a best-effort reconciliation where sources disagreed.
