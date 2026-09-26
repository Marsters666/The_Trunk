# The Trunk — project backups

Source backups for Mike Marsters, prepared September 26, 2026.

| Project | Version | Backup |
| --- | --- | --- |
| Signal Tracker and SideKick | 72 | [Download source](backups/2026-09-26/signal-tracker-and-sidekick.zip) |
| Notifier Logic Decoder (Notifier Report Manager) | 13 | [Download source](backups/2026-09-26/notifier-logic-decoder.zip) |

SideKick is included with Signal Tracker because the laptop and phone interfaces share one application.

## Restore
1. Download and extract the desired ZIP. Each ZIP contains its own project folder, including source, assets, dependency lockfile, database schema/migrations, and project instructions.
2. Use Node.js 22.13.0 or newer and the pnpm version specified in the project's package.json. Install dependencies with `pnpm install --frozen-lockfile`.
3. Follow the project README and hosting configuration to reconnect hosting and database bindings. For restoration in ChatGPT Sites, provide the backup and ask to restore the existing project; do not create a replacement Site unintentionally.
4. Restore required secrets separately. Signal Tracker requires `COWORKER_PASSCODE` and `ACCESS_SIGNING_KEY`. Their values are not in this public repository.
5. Recover database records and imported customer reports separately if needed. Validate the restored application before field use.

## Scope and limitations
These are source snapshots, not full live-service/database backups. They do not contain live sessions, cloud database contents, uploaded reports, browser-local saved data, runtime credentials, dependency folders, build output, or prior Git history.

Two customer report files embedded in the decoder source were deliberately excluded from this public repository: `public/data.json` and `public/shared-project.json`. Recover those files from the original private copy when restoring the exact preloaded dataset; the decoder backup is therefore not byte-for-byte identical to its complete original checkout.

Signal Tracker's existing revision history is included in `lib/revisions.json`. Its release-process document describes an earlier GitHub access failure; this dated backup supersedes that status without modifying the original source snapshot.

The [manifest](backups/2026-09-26/backup-manifest.json) records original source commits, excluded files, and SHA-256 checksums for every included file. The backup operation does not deploy or change either live application. No new physical-panel testing was performed.
