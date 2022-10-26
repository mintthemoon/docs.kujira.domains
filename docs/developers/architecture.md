# Architecture

## Contracts
KNS is implemented as 3 smart contracts: Registry, Registrar, and Auctions.

- Registry: store of records.
- Registrar: [CW721](https://github.com/cosmwasm/cw-nfts) NFT contract.
- Auctions: handles [domain auctions](/auctions).

## Registry
### Overview
The Registry contract manages two types of data: Resolvers and Records.
A Resolver maps a domain root (e.g. `kuji`) to an `admin` address that is
authorized to create, update, and delete Records matching that root. Resolvers
also have a list of allowed `RecordKind` types.

### Internal resolver
On instantiation, an internal resolver is created with the contract's own address
as its admin. This resolver is used for reverse records and can be queried directly
but the helper queries like `kujira_addr` should be preferred for convenience.

## Registrar
### Overview
The Registrar contract is an extended CW721 NFT contract with expiring tokens and a
configurable fee split for minting funds. A Registrar tracks ownership for a single
domain root and is intended to be set as the Resolver admin for that root.

### Minting
The Registrar has an authorized `minter` who can mint any domain. Each mint call
must include a minimum amount of funds determined by the configured price tiers.
Funds will be distributed according to the configured `default_funds_split`.

### Expiration
Tokens will be minted with a starting expiration of the mint time plus the configured
`base_duration`. A token can be extended by the owner before it expires at multiples
of the `base_duration`. The `grace_duration` is the number of seconds after a token has
expired when it cannot be used to register but is still valid and can be extended.
An expired token can be minted again and the existing token will be burned.

### Registration
Domain owners will be authorized to call the `register` function for their domain.
This will call the Registry contract to configure a Record for the domain using
the values they provide.

## Auctions
### Overview
The Auctions contract manages domain auctions and is responsible for minting
Registrar NFTs to the winners. It is intended to be set as the Registrar admin.
Auctions uses the Registrar `domain_info` query to determine if a domain is available
and get base prices.
