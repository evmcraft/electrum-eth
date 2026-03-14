# Electrum ETH

[![Runtime](https://img.shields.io/badge/Runtime-Python_3.8%2B-1f2937?style=for-the-badge&labelColor=111827)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-374151?style=for-the-badge&labelColor=111827)](./LICENCE)
[![Profile](https://img.shields.io/badge/Profile-ElectrumX_Server-4b5563?style=for-the-badge&labelColor=111827)](#runtime-shape)

Electrum ETH is the server side of the stack: it talks to a blockchain node, builds an indexed view of chain state, tracks mempool changes, and serves that data over the Electrum protocol.

![Electrum ETH setup screen](screen/setup.jpg)

## Why It Exists

This repository is for running infrastructure, not for holding funds.

If you need a process that:

- follows the chain continuously
- keeps transaction history queryable
- exposes Electrum-compatible network services
- survives behind a local or remote daemon

then this is the part you deploy.

## Runtime Shape

The codebase stays close to the classic ElectrumX server model:

- core implementation lives in `electrumx/`
- event loop model is `asyncio`
- package name is `e-x`
- current source version is `1.16.0`

Supported service types include `tcp`, `ssl`, `ws`, `wss`, and internal `rpc`.

## Fast Bring-Up

Install dependencies and the package itself:

```bash
pip install -r requirements.txt
pip install .
```

Minimal environment:

```bash
export COIN=<coin-class-name>
export DB_DIRECTORY=/var/lib/electrumx
export DAEMON_URL=http://user:pass@127.0.0.1:<node-rpc-port>/
export SERVICES=tcp://0.0.0.0:50001
```

`COIN` has to match the coin class name available to your deployment.

Start the server:

```bash
electrumx_server
```

## Included Tools

The repo ships with a small operator-facing toolset:

- `electrumx_server`: main service process
- `electrumx_rpc`: administrative and runtime RPC access
- `electrumx_compact_history`: history compaction utility

## What You Can Tune

Most operational behavior is environment-driven rather than CLI-driven.

Common knobs:

- storage backend selection via LevelDB or RocksDB
- service exposure over plain TCP or TLS/WebSocket variants
- daemon connectivity and failover routing
- cache sizing and session/resource limits

Template configs and helper assets live under `contrib/`.

## Repo Landmarks

- `docs/` contains the protocol and operations documentation
- `tests/` covers protocol, storage, daemon, and parsing behavior
- `electrumx/lib/` contains shared primitives, hashing, scripts, and coin definitions
- `electrumx/server/` contains the long-running server components

## License

MIT. See `LICENCE`.
