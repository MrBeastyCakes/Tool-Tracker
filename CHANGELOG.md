# Changelog

All notable changes to Tool Track are documented here.

---

## [1.2.0] — 2026-04-10

### Added
- **Tool Journey / History tracking** — every tool now keeps a full event log stored alongside its data
  - `created` — recorded when a tool is added, with which crew it was added to
  - `status` — recorded on every individual checkbox toggle (In Truck, Damaged, Repair, Missing) with the resulting value, so both "marked missing" and "found — no longer missing" appear as distinct entries
  - `checkin` — recorded when a weekly check-in is saved; one entry per tool showing its resulting status
  - `transferred` — recorded when a tool moves between crews, with from/to crew names
  - `assigned` — recorded when the Assigned To field changes, with old and new name
- **Tool Journey modal** — click the `🕐` button that appears on row hover in the crew table to open a tool's full timeline
  - Shows current status (ID, type, brand, crew, colored status pills)
  - Chronological timeline newest-first with color-coded event dots and human-readable labels
  - Exact local date and time for every event
- **Data migration** — existing saved data and imported files are automatically backfilled with empty history arrays so nothing breaks on upgrade

---

## [1.1.0] — 2026-04-09

### Changed
- **Overview page redesigned** with a new visual hierarchy and health indicators

#### Hero section
- Replaced flat row of identical stat cards with a two-tier layout
- Tier 1 — three primary KPI cards (Total Fleet, In Truck, Fleet Health) with icons, subtitle lines, and a dynamic left-border color that tracks fleet health state (green / orange / red)
- Tier 2 — compact secondary cards for Damaged, In Repair, and Missing, each with a 4 px mini bar showing proportion of the total fleet; a fourth Conflicts card appears when conflicts exist and opens the conflict modal on click

#### Conflict treatment
- Conflicts now surface above the hero as a red alert banner (with slide-in animation) so they are impossible to miss
- Banner shows count, "N critical" badge when type mismatches are present, and a preview of the first four conflicting IDs
- "No active conflicts" replaced the lonely centered text with a green left-bordered success bar

#### Crew cards
- Each card now shows a status badge (All Clear / Minor Issues / Needs Attention) color-coded green, orange, or red
- In-truck progress bar with `truck / total` and percentage labels
- Colored issue pill badges for each problem type (damaged, repair, missing, conflicts)
- Footer with last check-in date and a hover arrow that animates in

#### Category section
- Category cards now use a distinct `.cat-card` style — darker background, denser 190 px grid, no hover lift
- Each card has a stacked 5 px health bar showing the truck / damaged / missing proportions in green, red, and orange

#### Section headers
- New `.ov-section-header` component with a colored accent rule and item-count pill replaces the plain uppercase labels throughout the overview

---

## [1.0.0] — 2026-04-08

### Added
- Initial release of Tool Track
- Multi-crew tool inventory management stored entirely in `localStorage` — no backend required
- Crew sidebar with per-crew tool tables (ID, type, brand, assigned to, status checkboxes, notes)
- Status tracking: In Truck, Damaged, Repair, Missing — toggle per tool or via weekly check-in flow
- Tool ID prefix system that auto-detects tool type from ID prefix and learns new prefixes
- Conflict detection — flags duplicate IDs and ID/type mismatches across crews with a resolution modal
- Intentional shared ID support — mark a conflict as an intentional shared ID to hide it from active counts
- Tool transfer between crews
- Overview dashboard with fleet-wide stats, per-crew summary cards, conflicts table, and inventory by category
- Print modal — generate a printable weekly inventory sheet for selected crews
- JSON export / import for backup and data migration
- Dark and light theme with toggle, persisted to `localStorage`
