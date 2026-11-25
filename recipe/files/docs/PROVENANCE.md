# Provenance — MySQL (`9.7.4-CE-ubuntu24.04-r6`)

Every item below is copied from a record in this archive; the record is named in brackets.

## Source

- Upstream repository: https://github.com/mysql/mysql-server
- Revision built: `mysql-9.7.4` (commit `780b506e8296a61f2a7067bf2087d32c78e0bb76`)
- Source tree: `02f5225b63b5b77b31042a137b38d1f4c7f72df8625acf796f051157bdfdc557` over 59201 files [`docs/provenance/SOURCE_TREE_HASH.json`]
- Community Edition only: enterprise code is removed or refused before the build (CE audit at acquire).

## Build

- Method: `source-rebuild-c`; base image `scratch + a chiselled Ubuntu 24.04 runtime (vendored/chisel/slices.txt, packages.tsv)`
- Compiled with `--network=none` from vendored source, dependencies and base images; BuildKit pinned to `moby/buildkit:v0.31.2` (shipped in `toolchain/`).
- SOURCE_DATE_EPOCH: `1795161132` [`SOURCE_DATE_EPOCH.txt`]
- Frozen inputs: [`docs/provenance/FREEZE_MANIFEST.json`], build recipe: [`docs/provenance/BUILD_RECIPE.json`].

## Output

- Published image: `readystack/mysql:9.7.4-CE-ubuntu24.04-r6` — index digest `sha256:f134058f07f4570b62426c0e369d61784e92594eef3679d7c1360e73287ef044` [`docs/provenance/LOCKED_DIGEST.txt`]
- linux/amd64 image digest `sha256:b37e1407399a326725734783af3e128c91d291f04338b492a3d8c83dfe75a987` — reproduced from this archive before publishing [`docs/provenance/REPRO_VERIFICATION.json`].

## Attestations and signature

- SBOM + SLSA provenance attached to the image: attached: an SPDX SBOM and SLSA v1 provenance [`docs/provenance/SCOUT_VERDICT.json`]
- cosign signature by the ReadyStack release key: verified before publishing. Check it: `cosign verify --key https://readystack.dev/keys/cosign.pub readystack/mysql:9.7.4-CE-ubuntu24.04-r6`

## Pinned inputs, and why

- 23 pinned inputs, each with where it came from, why this one, how it was checked and when it was decided: `docs/PINS.md` [`docs/provenance/PINS.json`] (upstream source 2, base and build images 3, image digests 2, dependency versions readystack sets 3, pins in the kit's dockerfiles 5, readystack's build engine 6, dependencies upstream chose 2).

## Build trail

- How this release passed through the ReadyStack harness, record by record (every chain, drive, stage, review round, defect and check, each naming the record it is copied from): `ReadyStack-mysql-9.7.4-CE-ubuntu24.04-r6.trail.json`, published beside this archive and signed with the release key (`ReadyStack-mysql-9.7.4-CE-ubuntu24.04-r6.trail.json.sigstore`), and readable at https://readystack.dev/products/mysql/trail/9.7.4-CE-ubuntu24.04-r6.

