[![ReadyStack](https://readystack.dev/logo.svg)](https://readystack.dev)

**Stable, Open-source Releases, Automated** · [readystack.dev](https://readystack.dev)

[![Docker Hub](https://img.shields.io/badge/Docker%20Hub-readystack%2Fmysql-2496ED?logo=docker&logoColor=white)](https://hub.docker.com/r/readystack/mysql) [![Docker pulls](https://img.shields.io/docker/pulls/readystack/mysql)](https://hub.docker.com/r/readystack/mysql) [![Grade at release](https://img.shields.io/badge/grade%20at%20release-A%20%2894%25%29-2ea44f)](https://readystack.dev/products/mysql) [![Signed: cosign](https://img.shields.io/badge/signed-cosign-2ea44f)](https://readystack.dev/keys/cosign.pub) ![SBOM: SPDX](https://img.shields.io/badge/SBOM-SPDX-2ea44f) ![Provenance: SLSA v1](https://img.shields.io/badge/provenance-SLSA%20v1-2ea44f) ![Offline rebuild: verified](https://img.shields.io/badge/offline%20rebuild-verified-2ea44f)

# MySQL: ReadyStack build kit

The offline build kit for the Docker image `readystack/mysql:9.7.4-CE-ubuntu24.04-r6`. It holds what the image is built from (upstream source, base images, toolchain, pinned dependencies) and the documents, so the image can be rebuilt with no network access (`docker build --network=none`).

- Release: [9.7.4-CE-ubuntu24.04-r6](https://github.com/readystack-dev/mysql/releases/tag/9.7.4-CE-ubuntu24.04-r6)
- Image: [`docker.io/readystack/mysql:9.7.4-CE-ubuntu24.04-r6`](https://hub.docker.com/r/readystack/mysql/tags), manifest digest `sha256:b37e1407399a326725734783af3e128c91d291f04338b492a3d8c83dfe75a987`
- Product page: https://readystack.dev/products/mysql
- Source and build recipe: https://readystack.dev/products/mysql/recipe
- Build trail: https://readystack.dev/products/mysql/trail/9.7.4-CE-ubuntu24.04-r6
- Defects: this repository's Issues (defects recorded from 25 November 2026 on) and https://readystack.dev/defects.html?product=mysql

## The image

Single container. MySQL Community Server 9.7.4 (9.7 LTS) compiled from the upstream source tag with CMake and installed in /usr/local/mysql. The image is the whole database server: there is no external database and no sidecar. mysqld runs in the foreground as the non-root mysql user. On the first start with an empty data directory the entrypoint creates the data directory in /var/lib/mysql and sets the root password before the server opens a network port.

## Who uses MySQL and why

Developers and database administrators who need a relational SQL database for web and business applications.

MySQL is a relational database server. Data lives in tables that applications add to, query and change with SQL, through a wide range of client libraries and APIs.

A typical use: An online store keeps its products, customers and orders in MySQL tables. The web application reads and writes them with SQL through a client library for its language, and administrators manage the server, its users and its databases with MySQL's own tools.

From the upstream project's own description: https://github.com/mysql/mysql-server, https://dev.mysql.com/doc/refman/8.4/en/what-is-mysql.html.

## This release

- Docker Scout policy grade at release: **A** (94%), graded 2026-11-22 with `docker scout policy` (CLI 1.26.0, docker-default configuration).
  - Docker Scout counts 21 packages with copyleft licences (GPL, LGPL, MPL), all of them operating-system packages (it counts only packages whose licence it can read; the SBOM lists every component).
- Signed with ReadyStack's release key (fingerprint `04daa92344a52dbc`): https://readystack.dev/keys/cosign.pub.
- Runs as a non-root user (`mysql`).
- Attestations on the image: an SPDX SBOM and SLSA provenance v1.
- Rebuilt from this kit with network egress blocked on 2026-11-22; the rebuilt image digest is the published one.
- Base: Ubuntu 24.04.

The current grade, measured again every day, is on https://readystack.dev/products/mysql.

MySQL is distributed under its upstream licence (GPL-2.0-only); the kit contains upstream's source under that licence, and each vendored component under its own.

## Download

From the [9.7.4-CE-ubuntu24.04-r6 release](https://github.com/readystack-dev/mysql/releases/tag/9.7.4-CE-ubuntu24.04-r6): `ReadyStack-mysql-9.7.4-CE-ubuntu24.04-r6.tar.gz` (1.4 GB), SHA-256 `efe14ba32f0463a85455059ab87376f0d19d45dc1782bf3615438b6367b4e70f`.

```sh
sha256sum --check --ignore-missing SHA256SUMS
```

## Verify and rebuild

The rebuild statement is signed with the ReadyStack release key. Check the signature before you rely on it:

```sh
cosign verify-blob --key https://readystack.dev/keys/cosign.pub \
  --bundle ReadyStack-mysql-9.7.4-CE-ubuntu24.04-r6.rebuild.json.sigstore ReadyStack-mysql-9.7.4-CE-ubuntu24.04-r6.rebuild.json
```

Unpack with `-p` so file modes are kept, then follow the kit's own README.md and docs/REBUILD.md:

```sh
tar -xpzf ReadyStack-mysql-9.7.4-CE-ubuntu24.04-r6.tar.gz
cd 9.7.4-CE-ubuntu24.04-r6
less README.md docs/REBUILD.md
```

The build trail (`ReadyStack-mysql-9.7.4-CE-ubuntu24.04-r6.trail.json`, signed the same way, and its Markdown copy) records how this release was built and checked.

## This repository

`recipe/` holds the kit's recipe files (Dockerfiles, build scripts, pins) as published at https://readystack.dev/products/mysql/recipe. The complete kit is the release download. Each release is a tag here. How to report a vulnerability: [SECURITY.md](SECURITY.md).

## About ReadyStack

**Stable, Open-source Releases, Automated.** ReadyStack releases popular open-source apps every week with every available critical and high security fix applied, plus full documentation, reference data, tests and a build recipe that recreates each release bit-for-bit. Each release is rebuilt from its pinned inputs with the network off, checked against its published digest, signed, and scanned and graded again every day. The images and build kits are free, and ReadyStack is soon to be a nonprofit.

[readystack.dev](https://readystack.dev) · [All products](https://readystack.dev/products.html) · [Build kits on GitHub](https://github.com/readystack-dev) · [Defect log](https://readystack.dev/defects.html) · contact@readystack.dev

— ReadyStack · https://readystack.dev
