---
namespace-identifier: xrpl-caip2
title: XRP Ledger Namespace - Chains
author: Anton Dalgren (@antondalgren)
discussions-to: https://github.com/ChainAgnostic/namespaces/pull/57/
status: Draft
type: Standard
created: 2023-02-23
updated: 2026-09-28
requires: ["CAIP-2"]
---

# CAIP-2.

*For context, see the [CAIP-2][] specification.*

## Rationale

The namespace `xrpl` refers to the XRP Ledger ecosystem, including its
alternative testing and development networks.

The XRP Ledger ecosystem consists of several different blockchains.
The XRP Ledger has a production network called `livenet`, a testing network
called `testnet` for stable releases, and a development network called `devnet`
for beta releases.
There are also preview networks for particularly large network changes and
XRPL protocol sidechains such as Xahau.
The networks are identified by a numerical `network_id`.

An identifier for an XRPL chain consists of the `xrpl` namespace prefix followed
by the chain's unique `network_id`, an unsigned integer, i.e.
`xrpl:{network_id}`.

## Syntax

A network id in the XRP Ledger ecosystem is defined as an unsigned integer
ranging from 0 to 4294967295.

### Resolution Method

To resolve a network reference for a XRPL network, POST a RPC request to the
XRPL node with endpoint `/` for example:

```jsonc
// Request
curl --location --request POST "https://xrplcluster.com/" \
--header 'Content-Type: application/json' \
--data-raw '{
    "method": "server_info",
    "params": [ ]
}'
// Response
{
    "result": {
        "info": {
            "build_version": "1.9.4",
            "complete_ledgers": "32570-77992447",
            "hostid": "LEST",
            "initial_sync_duration_us": "328508164",
            "io_latency_ms": 1,
            "jq_trans_overflow": "9048",
            "last_close": {
                "converge_time_s": 3.001,
                "proposers": 34
            },
            "load_factor": 1,
            "network_id": 0,
            "peer_disconnects": "29",
            "peer_disconnects_resources": "0",
            "peers": 23,
            "pubkey_node": "n9KQK8yvTDcZdGyhu2EGdDnFPEBSsY5wEgpU5GgpygTgLFsjQyPt",
            "server_state": "full",
            "server_state_duration_us": "35758622131",
            "state_accounting": {"..."},
            "time": "2023-Feb-23 13:24:41.285216 UTC",
            "uptime": 700794,
            "validated_ledger": {"..."},
            "validation_quorum": 28
        },
        "status": "success"
    }
}
```
The response will return a JSON object which will include server information.

The network reference can be retrieved from the field
`response.result.info.network_id` in the response of the `server_info` RPC
request.

For Xahau, the public HTTPS endpoints are `https://xahau.network` for Mainnet
and `https://xahau-test.net` for Testnet.
The Xahau documentation identifies these networks as `21337` and `21338`,
respectively.

Xahau transactions must include their network ID in the `NetworkID` field.
This follows the XRPL protocol rule that networks with an ID greater than 1024
use the field for cross-network replay protection.

### Backwards Compatibility

Not applicable

## Test Cases

This is a list of manually composed examples

```
# Livenet
xrpl:0

# Testnet
xrpl:1

# Devnet
xrpl:2

# AMM - Devnet
xrpl:25

# Xahau Mainnet
xrpl:21337

# Xahau Testnet
xrpl:21338
```

## References

- [XRPL Documentation][]
- [XRPL Networks][] - Description of the different XRPL networks.
- [XRPL Public Nodes][] - Public nodes for the different XRPL networks.
- [XRPL Server Info Request][] - RPC request to get the `network_id`.
- [XRPL Network ID][] - The definition of the `network_id` value.
- [Xahau Network Endpoints][] - Public endpoints and network IDs for Xahau Mainnet and Testnet.
- [Xahau Transaction Common Fields][] - `NetworkID` requirements and replay protection for Xahau transactions.
- [CAIP-2][]

[CAIP-2]: https://chainAgnostic.org/CAIPS/caip-2
[XRPL Documentation]: https://xrpl.org/docs.html
[XRPL Networks]: https://xrpl.org/parallel-networks.html 
[XRPL Network ID]: https://github.com/XRPLF/rippled/blob/8f514937a41eba90d98fb99daf938925527f0c44/cfg/rippled-example.cfg#L818-L820
[XRPL Public Nodes]: https://xrpl.org/public-servers.html 
[XRPL Server Info Request]: https://xrpl.org/server_info.html
[Xahau Network Endpoints]: https://xahau.network/docs/infrastructure/installing-xahaud/
[Xahau Transaction Common Fields]: https://xahau.network/docs/protocol-reference/transactions/transaction-common-fields/


## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
