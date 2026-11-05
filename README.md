# backup-verify

> Turn the backup you have never restored into one you have.

**Status:** 🚧 In development

## Overview

Restore-test a backup into a scratch location and checksum the result, because a backup that has never been restored is a hypothesis, not a backup.

## Features

- Restores into a scratch directory or a throwaway volume, never over the source path
- Compares a manifest of checksums, sizes, ownership and mode against the live tree
- Sampling mode: fully verify N randomly chosen files instead of restoring terabytes nightly
- Drivers for restic, borg, `pg_restore` and plain tar, each shelling out to the real tool
- Records restore wall-clock time, so the RTO number in the runbook is measured rather than assumed
- Non-zero exit with a written report, so it can run from a systemd timer and page on failure

## Stack

Go + cobra, crypto/sha256 for manifests, exec-based drivers for restic, borg and `pg_restore`.

## Usage

```bash
backup-verify run --driver restic --repo /srv/backups/db --scratch /var/tmp/verify --sample 200
```

## License

MIT

---

Archived on 2026-11-05. The idea moved to [opsbox](https://github.com/moveeeax/opsbox/issues/3).
