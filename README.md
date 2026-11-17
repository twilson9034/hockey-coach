# 8u-hockey-coach
Roster rotation 

## Player development

Enable **Settings → Player development** to show the development page. Skills
follow the selected age division; Custom game rules retain the last skill age and
show an explicit age selector. The library contains coaching examples, not an
official association curriculum. Earlier foundational skills remain available.

Assess one skill across the roster with a date, coach name, rating, and optional
notes. Unchanged players receive no assessment. Practice and game observations
are separate. Team overview shows the latest dated assessment; Player progress
retains history across divisions and supports removing mistaken observations.
Team skills and practice PDF guides can be added with manual skill links. PDFs
are limited to 1.5 MB total to keep device backups manageable; remove older guides
when needed. No automatic PDF parsing or opponent matchup scoring is included.

Development data is a `type: 'player-development'` record in `practiceSessions`.
This deliberately uses the existing practice cloud RPC section and permissions
without requiring a database migration. Goalie practice counts, rotation and
history exclude this record. JSON backups include development and PDF data;
disabling the feature preserves it. Assistant editing uses the **practice**
permission; enabling the feature uses **settings** permission. Existing cloud
version-conflict handling also applies to development updates.

Validation:

- `node --check app.js` and `node --check development.js`
- `node tests/development-unit.cjs` (no dependencies)
- Browser smoke test: install Playwright, serve this directory on port 8765,
  then `node tests/development.cjs`. Set `CHROMIUM_PATH` if Chromium is elsewhere.
  This smoke test stubs cloud access; test actual assistant permissions and
  cross-device sync with a test cloud team before merging.
