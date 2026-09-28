---
namespace-identifier: xahau
title: Xahau Ecosystem
author: Ekiserrepé (@Ekiserrepe)
discussions-to: https://github.com/ChainAgnostic/namespaces/discussions
status: Draft
type: Informational
created: 2026-09-28
requires: ["CAIP-2"]
---

# Namespace for Xahau Chains

Xahau is a decentralized Layer 1 blockchain derived from the XRP Ledger
protocol.
It is powered by the open-source `xahaud` server and uses XAH as its native
asset.

Xahau extends the XRP Ledger protocol with Hooks, which are small WebAssembly
programs attached to accounts.
Hooks can inspect and control transactions, maintain state, and emit new
transactions.
Xahau also provides network-specific transaction types, ledger objects, and
server definitions for applications that serialize and sign transactions.

## Rationale

The `xahau` namespace distinguishes Xahau chains from other networks based on
the XRP Ledger protocol.
Although Xahau shares its consensus ancestry, address encoding, and much of its
API with the XRP Ledger, its Hooks execution environment, native asset,
transaction types, ledger objects, governance, and dynamically published server
definitions form a distinct application and tooling ecosystem.

Each Xahau chain is identified by the numeric network ID returned by its
`server_info` API response.
The network ID is also included in signed Xahau transactions for replay
protection.

## Governance

The Xahau protocol is implemented in the open-source `xahaud` repository.
Protocol amendments are activated through validator voting, while the Genesis
Hook provides on-ledger governance for network-level responsibilities defined
by the Xahau protocol.

## References

- [Xahau Documentation][] - Official developer and protocol documentation.
- [Xahau Whitepaper][] - Architecture, Hooks, tokenomics, and governance.
- [xahaud][] - Open-source server implementation for the Xahau network.

[Xahau Documentation]: https://xahau.network/docs/
[Xahau Whitepaper]: https://xahau.network/docs/resources/whitepaper/
[xahaud]: https://github.com/Xahau/xahaud

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
