# MySQL 9.7.4 — ReadyStack release `9.7.4-CE-ubuntu24.04-r6`

Generated 2026-11-22 from this release's build records and strategy. Statements that come from a single record name it in brackets; the others come from this release's strategy and build log.

## Release

- **Image:** `readystack/mysql:9.7.4-CE-ubuntu24.04-r6` (linux/amd64). Index digest `sha256:f134058f07f4570b62426c0e369d61784e92594eef3679d7c1360e73287ef044` [`docs/provenance/LOCKED_DIGEST.txt`].
- **Image manifest digest:** `sha256:b37e1407399a326725734783af3e128c91d291f04338b492a3d8c83dfe75a987` [`TARGET_DIGEST.txt`].
- **Upstream:** MySQL 9.7.4 built from source at `mysql-9.7.4` of https://github.com/mysql/mysql-server — upstream notes: https://github.com/mysql/mysql-server/releases/tag/mysql-9.7.4 [`docs/provenance/BUILD_RECIPE.json`].
- **Base image:** none (`FROM scratch`): a chiselled Ubuntu 24.04 runtime, the files Canonical's chisel cut from Ubuntu's own packages (`vendored/chisel/slices.txt`, `vendored/chisel/packages.tsv`); runtime user `mysql`.
- **Build:** `source-rebuild-c`, compiled offline with `--network=none`.
- **Supersedes:** ReadyStack release `9.7.4-CE-ubuntu24.04-r5`.

## What changed in this release

- Upstream version unchanged (9.7.4); ReadyStack rebuild.
- MySQL 9.7.4 is unchanged from the release this supersedes (9.7.4-CE-ubuntu24.04-r5); this release rebuilds it. Changes: the image is rebuilt on the current ubuntu:24.04 image (sha256:9c7f200c07e3…), which its maintainers updated after 9.7.4-CE-ubuntu24.04-r5 was built on sha256:2198e4c65076…. Settings, ports and data volumes are those of 9.7.4-CE-ubuntu24.04-r5: replace the container with this image on the same volumes.

## Security status at release (measured 2026-11-20)

- **Docker Scout:** 0 fixable critical/high vulnerabilities; runs as `mysql` (non-root); SBOM + provenance attestations present (SPDX SBOM + SLSA v1) [`docs/provenance/SCOUT_VERDICT.json`].
- **OSV cross-check:** no fixable critical/high vulnerability beyond Docker Scout's findings.
- **Signature:** cosign signature verified by ReadyStack's release gate before publishing; check it yourself with `cosign verify --key https://readystack.dev/keys/cosign.pub readystack/mysql:9.7.4-CE-ubuntu24.04-r6` (signatures are recorded in the public Sigstore transparency log).
- **ReadyStack release check at release:** passed (ReadyStack's own test, not a Docker Scout grade). Vulnerabilities are disclosed every day and the image never changes, so it is re-checked daily, beside Docker Scout's own dated grade, at https://readystack.dev/queue.
- **Before exposing this service:** MYSQL_ROOT_HOST defaults to %, so root can log in over the network with its password; set MYSQL_ROOT_HOST=localhost on the first start to create no network root account, or restrict it to an address or subnet.
- **Before exposing this service:** The TLS certificate the server generates on its first start is self-signed; clients that verify certificates need your own certificate, configured with ssl_cert and ssl_key in a file under /etc/mysql/conf.d/.
- **Before exposing this service:** Keep ports 3306 and 33060 on a private network: both accept password logins for every account with a network host.

## Reproducibility

Rebuilds offline from this archive to the identical image digest `sha256:b37e1407399a326725734783af3e128c91d291f04338b492a3d8c83dfe75a987`: run `./BUILD_OFFLINE.sh`, then `./VERIFY_OFFLINE.sh` (add `--online` to confirm the Docker Hub tag holds the same digest). Before publishing, ReadyStack rebuilt the kit with `./BUILD_OFFLINE.sh` and compared the result with the published digest [`docs/provenance/REPRO_VERIFICATION.json`], then ran `./BUILD_OFFLINE.sh` and `./VERIFY_OFFLINE.sh` from this archive (without `--online`).

## Validation

- 10 of 10 use cases passed (10 authored) against the running image [`docs/validation/test-results.json`].

## Known issues

- **medium** (ReadyStack package): The seed-data record says the product has no SQL database ('config/CRD-native product') [`RSD-mysql-934031fd27`] (carried from `9.7.2-CE-ubuntu24.04-r1`, recorded there as `RSD-mysql-32ebd4863e`)

## Defects fixed

- 27 problems found before release and fixed before it shipped (27 by review); each is listed in `docs/defects/defects.json`.

## Verify this archive

```
sha256sum -c CHECKSUMS.sha256
./BUILD_OFFLINE.sh && ./VERIFY_OFFLINE.sh --online
cosign verify --key https://readystack.dev/keys/cosign.pub readystack/mysql:9.7.4-CE-ubuntu24.04-r6
```

ReadyStack records every signature in the public Sigstore transparency log (Rekor), so the command needs no extra flags.

