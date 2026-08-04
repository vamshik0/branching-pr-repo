# branching-pr-repo

Sandbox git repository used to test ToolJet's git-branching feature
(app + module git-sync, branch create/switch, workspace pull/push).

This repo is not a standalone project — its contents are written and
overwritten by ToolJet git-sync operations. Do not treat any file
here as authoritative or hand-edit it unless you're deliberately
simulating an out-of-band change.

## Structure

Files are laid out by ToolJet's git-sync adapter:

- `apps/<app-name>/` — one folder per app, containing the app's
  serialized definition, pages, components, and queries.
- `modules/<module-name>/` — same layout for modules embedded via
  ModuleViewer.
- `data-sources/<datasource-name>/data-source.json` — one folder per
  datasource, named after the datasource (e.g. `postgresql/`,
  `SEO DB/`), each holding a single `data-source.json`. The file
  carries the datasource `id`, `kind`, `name`, `type`, and per-
  environment `options` (`development` / `staging` / `production`).

Branches on this repo correspond to ToolJet workspace branches. The
default branch mirrors the workspace's default (usually `main`);
feature branches created inside ToolJet are pushed as matching git
branches here.

## What this repo is used for

- Reproducing bugs in git-sync flows (branch switch, pull conflicts,
  coalesced deletion commits, module hydration, pinned versions).
- Testing multi-workspace scenarios where the same repo is pulled
  into a second ToolJet workspace to verify import parity.
- QA test cases against release PRs that touch the git-branching
  feature.
