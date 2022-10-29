# Architecture

## Contracts
### Overview
KNS is implemented as 3 smart contracts: Registry, Registrar, and Auctions.

- Registry: store of records.
- Registrar: [CW721](https://github.com/cosmwasm/cw-nfts) NFT contract.
- Auctions: handles [domain auctions](/auctions).

### Registry
The Registry contract manages two types of data: Resolvers and Records.
A Resolver maps a domain root (e.g. `kuji`) to an admin address that is
authorized to create, update, and delete Records matching that root. Resolvers
also have a list of allowed RecordKind types.

### Registrar
The Registrar contract is an extended CW721 NFT contract with expiring tokens and a
configurable fee split for minting funds. A Registrar tracks ownership for a single
domain root and is intended to be set as the Resolver admin for that root.

### Auctions
The Auctions contract manages domain auctions and is responsible for minting
Registrar NFTs to the winners. It is intended to be set as the Registrar admin.
Auctions uses the Registrar `domain_info` query to determine if a domain is available
and get base prices.

## Metadata
Metadata is served from the [KNS API server](https://github.com/mintthemoon/kns-api-js)
at api.kujira.domains. Data is generated on-demand by querying the chain and cached for
a short time.
