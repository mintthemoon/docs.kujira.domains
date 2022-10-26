# Kujira Name System (KNS)
Connecting the Cosmos one link at a time. 🚀🪐🌍

- Get your own personalized .kuji domain!
- Domains can link to a wallet address for readable identifiers.
- Domains can serve content just like a traditional web address.

Get ready, you don't want to miss this!

## More than a name
KNS aims to be a fully-featured on-chain domain name system providing much more functionality than a map from domains to wallet addresses. Decentralized finance needs decentralized infrastructure, and reliance on traditional DNS is an underappreciated problem without easy answers.

The long-term goal of this project is to provide some of those answers, and in the short-term the initial offering improves on many existing services.

## Fair price discovery with domain auctions
How do you decide on a price for a domain? Historically DNS and its alternatives have been plagued by issues like squatting, where someone will buy domains they never intend to use at a low base price and immediately relist them for much more without taking on much risk. This situation (along with most traditional NFT mints) encourages a flood of transactions all at once as buyers race to lock in domains, which can impact other operations on the chain.

The KNS Auctions contract is our solution. Users can place bids for any domain with a base price determined by length, and a limited number of auctions with the highest bid totals can be opened. Once opened existing bids are locked and cannot be withdrawn, only increased, until the end of the open period when the auction will be closed and a winner chosen. The limits and durations are configurable via governance so they can be adjusted as capacity and demand evolve over time.

### Pricing
Final prices will be determined by auction with the following base prices:

| Length   | Min. Bid |
| -------- | -------- |
| 5+ chars | 20 $USK  |
| 4 chars  | 100 $USK |
| 3 chars  | 500 $USK |

## Creating value for stakers
Here's the best part: a full 80% of all auction proceeds will be sent directly to $KUJI stakers! The remaining 20% will be kept as payment for development and continued support of the protocol. This project has huge potential for revenue generation which we hope will boost that APR and strengthen the whole ecosystem. KNS will use $USK for bids to help drive demand for our favorite stablecoin. 

## Roadmap
### Planned Feature: KNS Gateway
KNS is not just for wallets! Your KNS record can point at content hosted with IPFS, or link to the traditional internet with an IP or DNS name. These records are already supported on-chain and the KNS Gateway will serve them at [yourdomain.kujira.link](https://kujira.link) in addition to being queryable on Kujira.

### Planned Feature: ICS721 Support
The ICS721 standard for cross-chain NFT transfers is under active development and we intend to support it as it becomes available. This will enable you to transfer KNS domain NFTs off Kujira and list them for sale on Stargaze or whichever Cosmos marketplace you prefer.

### Planned Feature: Owner Auctions
The auction system provides an excellent price discovery mechanism for newly minted tokens, and the end goal is to make this functionality available to holders as well. The owner auctions feature will enable bidding for all tokens, including those that are already owned. Token holders can view bids for their domains and at any time choose to initiate an auction.
