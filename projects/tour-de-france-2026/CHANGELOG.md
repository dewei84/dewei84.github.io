# Changelog — Tour de France 2026 stage tracker

All notable changes to this page are documented here.

## 2026-07-20

### Added

- **Stage 15 result** (Champagnole → Plateau de Solaison): Remco Evenepoel (Soudal Quick-Step) beat Tadej Pogačar in a reduced sprint at the top of the first-ever Tour finish on the Plateau de Solaison, with Isaac del Toro (UAE Team Emirates-XRG) 6 seconds back in third. Jonas Vingegaard abandoned earlier in the stage after a crash that fractured his collarbone. Pogačar keeps yellow and polka-dot, Mads Pedersen still leads green, and Isaac del Toro takes the white jersey from Paul Seixas.

### Changed

- Footer results note now reads "through Stage 15 · 19 Jul 2026".

### Known limitations

- Results data now covers Stages 1–15; Stage 16 onward has route/profile/notes but no podium or jerseys yet.

## 2026-07-19

### Added

- **Stage 14 result** (Mulhouse → Le Markstein): Tadej Pogačar (UAE Team Emirates-XRG) attacked on the Col du Haag inside the final 7km to solo to his fourth stage win of this Tour, 38 seconds ahead of teammate Isaac del Toro and Paul Seixas (Decathlon CMA CGM), who crossed together. Pogačar extends his overall lead and keeps the polka-dot jersey; Paul Seixas takes the white jersey from Juan Ayuso. Mads Pedersen still leads green.

### Changed

- Footer results note now reads "through Stage 14 · 18 Jul 2026".

### Known limitations

- Results data now covers Stages 1–14; Stage 15 onward has route/profile/notes but no podium or jerseys yet.

## 2026-07-17

### Added

- **Stage 13 result** (Dole → Belfort): Mauro Schmid (Team Jayco AlUla) won a two-up sprint from the breakaway ahead of Harold Tejada (XDS Astana Team), with Tom Pidcock (Q36.5 Pro Cycling) taking third at +2s and vaulting to 4th overall. Jersey standings unchanged at the top: Tadej Pogačar leads yellow and polka-dot, Mads Pedersen leads green, Juan Ayuso leads white.

### Changed

- Added `Team Jayco AlUla` (`JAY`) to the team-name constants for Mauro Schmid's stage 13 win.
- Footer results note now reads "through Stage 13 · 17 Jul 2026".

### Known limitations

- Results data now covers Stages 1–13; Stage 14 onward has route/profile/notes but no podium or jerseys yet.

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
