---
namespace-identifier: xrpl
title: XRP Ledger Namespace
author: Anton Dalgren (@antondalgren)
discussions-to: https://github.com/ChainAgnostic/namespaces/pull/57/
status: Draft
type: Informational
created: 2023-02-23
updated: 2026-09-28
requires: ["CAIP-2", "CAIP-10", "CAIP-122"]
---

# Namespace for XRP Ledger

This document defines the applicability of CAIP schemes to the blockchains of
the XRP Ledger ecosystem.

## Syntax

The namespace `xrpl` refers to blockchains that use the XRP Ledger protocol,
including public, test, development, sidechain, and private networks.

In addition to the XRP Ledger networks, this namespace includes Xahau.
Xahau is an XRPL protocol sidechain powered by the `xahaud` server, a fork of
`rippled` that adds Hooks smart contracts and uses XAH as its native asset.

## References

- [XRP Ledger documentation](https://xrpl.org/docs.html)
- [Xahau documentation](https://xahau.network/docs/)
- [Xahau server implementation](https://github.com/Xahau/xahaud)
- [CAIP-2](https://github.com/ChainAgnostic/CAIPs/blob/master/CAIPs/caip-2.md)
- [CAIP-10](https://github.com/ChainAgnostic/CAIPs/blob/master/CAIPs/caip-10.md)
- [CAIP-122](https://github.com/ChainAgnostic/CAIPs/blob/master/CAIPs/caip-122.md)

## Rights

Copyright and related rights waived via CC0.
