# Electrum ETH

[![Runtime](https://img.shields.io/badge/Runtime-Python_3.8%2B-1f2937?style=for-the-badge&labelColor=111827)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-374151?style=for-the-badge&labelColor=111827)](./LICENCE)
[![Profile](https://img.shields.io/badge/Profile-ElectrumX_Server-4b5563?style=for-the-badge&labelColor=111827)](#system-profile)

```text
Electrum ETH :: asynchronous indexer and Electrum protocol service layer
```

![Electrum ETH setup screen](screen/setup.jpg)

## System Profile

Python service for blockchain indexing, mempool tracking, and Electrum-compatible client access.

| Scope | Value |
| --- | --- |
| Implementation | `electrumx/` |
| Runtime model | `asyncio` |
| Package | `e-x` |
| Source version | `1.16.0` |

## Functional Surface

- Address and transaction history indexing
- Electrum protocol request handling
- TCP, SSL, WS, and WSS service exposure
- Multi-daemon RPC failover
- LevelDB and RocksDB backend support
- Auxiliary RPC and history maintenance tooling

## Bring-Up

| Requirement | Value |
| --- | --- |
| Python | `3.8+` |
| Install deps | `pip install -r requirements.txt` |
| Install package | `pip install .` |
| Primary entrypoint | `electrumx_server` |

Required environment:

```bash
export COIN=<coin-class-name>
export DB_DIRECTORY=/var/lib/electrumx
export DAEMON_URL=http://user:pass@127.0.0.1:<node-rpc-port>/
export SERVICES=tcp://0.0.0.0:50001
```

`COIN` must match the configured coin class name exposed by your deployment.

## Operator Paths

Start service:

```bash
electrumx_server
```

Available utilities:

| Command | Purpose |
| --- | --- |
| `electrumx_rpc` | Server RPC operations |
| `electrumx_compact_history` | History compaction |

## Implementation Notes

- Documentation set: `docs/`
- Test coverage entry: `tests/`
- Dependency base: `aiorpcX`, `attrs`, `plyvel`, `aiohttp`
- Service behavior is controlled through environment variables, not CLI flags

## License Reference

MIT. See `LICENCE`.
