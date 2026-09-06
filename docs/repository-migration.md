# Standalone repository migration

The user authorized separating the former agent-plugins repository into
independent agent-tui and agent-memory repositories and removing Git ownership
from their parent directory. Teams is being moved separately by the user.

This candidate promotes `agent-tui/` from upstream commit
`51f457bca7f8aa84dbf9bea45362e29ea679f146` to the repository root. It preserves
upstream ancestry with a normal commit, without rewriting published history.
Other projects remain in the previous commit and the retained legacy repository;
their removal from this repository is part of the requested separation.

Runtime source, tests, package identity, dependency lock, and child AppSDK
contracts are preserved. Root-relative hooks, CI, ignored build/worktree paths,
and the lifecycle candidate diff scope are adjusted for the standalone root.

Validation on this candidate: typecheck, runtime build, runtime boundaries,
public exports, all 398 tests, and clean-install validation pass. This migration
does not claim a new live deployment.

`appsdk verify .` reports `INVALID_SDK_MIGRATION_RECORD` in both the original
upstream child directory and this standalone candidate with unchanged AppSDK
files. This pre-existing governance failure remains open; migration does not
rewrite its records or claim AppSDK admission, freeze, or promotion.
