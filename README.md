# MySQL: ReadyStack build kit

The offline build kit for the Docker image `readystack/mysql:9.7.4-CE-ubuntu24.04-r6`. It holds what the image is built from (upstream source, base images, toolchain, pinned dependencies) and the documents, so the image can be rebuilt with no network access (`docker build --network=none`).

- Release: [9.7.4-CE-ubuntu24.04-r6](https://github.com/readystack-dev/mysql/releases/tag/9.7.4-CE-ubuntu24.04-r6)
- Image: [`docker.io/readystack/mysql:9.7.4-CE-ubuntu24.04-r6`](https://hub.docker.com/r/readystack/mysql/tags), manifest digest `sha256:b37e1407399a326725734783af3e128c91d291f04338b492a3d8c83dfe75a987`
- Product page: https://readystack.dev/products/mysql
- Defects: this repository's Issues (defects recorded from 25 November 2026 on) and https://readystack.dev/defects.html?product=mysql

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

`recipe/` holds the kit's recipe files (Dockerfiles, build scripts, pins) as published at https://readystack.dev/products/mysql/recipe. The complete kit is the release download. Each release is a tag here.
