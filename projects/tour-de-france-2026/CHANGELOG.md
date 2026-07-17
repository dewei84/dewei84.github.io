# Changelog — Tour de France 2026 stage tracker

All notable changes to this page are documented here.

## 2026-07-16

### Added

- **Stage winner on the collapsed card** — each completed stage shows the winner's name and team on its own line beneath the terrain/date/time row.
- **Podium in the expanded view** — a 1–2–3 finish with each rider's team and time gap to the winner.
- **Jersey wearers in the expanded view** — all four classification leaders after each stage: Yellow (GC), Green (points), Polka-dot (KOM), and White (young rider), each with name and team.
- **"Today's stage" button** in the filter bar — resets to *All*, then scrolls to, opens, and briefly flashes today's stage. Today's stage also gets a persistent "Today" tag and yellow border. Driven by the viewer's real date, so it tracks the race automatically (exact-day match, falling back to the most recent stage on rest days and after the race).
- **Stage 12 result** (Circuit Nevers Magny-Cours → Chalon-sur-Saône): Tim Merlier's hat-trick win ahead of Olav Kooij and Jasper Philipsen, plus jersey standings.
- **Favicon** generated from the Tour de France map/cyclist logo (`favicon.ico`, 16/32px PNGs, 180px Apple touch icon), linked from the page head.

### Changed

- Rebuilt the results data model to carry team names, full podiums with gaps, and per-stage jersey holders.
- Replaced previously fabricated results with verified data for Stages 1–12, sourced from Wikipedia, ProCyclingStats, Cyclingnews and CyclingUpToDate — including corrected 2026 team affiliations (e.g. Kooij → Decathlon CMA CGM, Ayuso → Lidl-Trek, Alpecin → Alpecin-Premier Tech).
- Stage 1 (team time trial) now correctly shows no individual winner — the podium lists the three teams and their times.
- Polka-dot jersey card: replaced the solid red left border with 45° alternating red/white bands to evoke the KOM jersey.

### Fixed

- Corrected the polka-dot (mountains) leader for Stages 10–11 from Juan Ayuso to Tadej Pogačar. Stages 11–12 are flat, so the KOM leader could not have changed, and the Stage 12 classification report confirms Pogačar leads on 42 pts ahead of Vingegaard, with Ayuso not in contention. The earlier value came from a misread of Wikipedia's classification table columns.
- Raised the expanded drawer's max-height (480px → 1200px) so the taller podium + jersey content no longer clips.
- Moved the "today" highlight ring from the header button to the whole stage container so it wraps the full card when expanded.
- Podium cards: rider name and team now stack on separate lines instead of running together (inline spans were ignoring the intended `margin-top`).

### Known limitations

- Results data currently covers Stages 1–12; Stage 13 onward has route/profile/notes but no podium or jerseys yet.
- The first-week polka-dot (mountains) leader for a stage or two is a best-effort reconciliation where sources disagreed.
