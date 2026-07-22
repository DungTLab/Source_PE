# Swimlane Diagram — NFT Marketplace & Digital Art System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Digital Artist"]
        A1["Upload Digital Art & Royalty Terms"]
        A2["Sign On-Chain Minting Voucher"]
        A3["Collect Secondary Sale Royalty Payout"]
    end

    subgraph Lane2["System"]
        S1["Pin Artwork Media to IPFS Storage"]
        S2["Verify Artist Identity & Copyright"]
        S3{"Auction vs Instant Buy?"}
        S4["Lock Bid Crypto in Escrow Contract"]
        S5["Execute Token Transfer & Royalty Split"]
    end

    subgraph Lane3["NFT Collector"]
        C1["Connect Web3 Wallet & Browse Art"]
        C2["Place Escrow Bid or Instant Buy"]
        C3["Receive NFT Token in Wallet"]
    end

    subgraph Lane4["Blockchain Network"]
        B1["Mint ERC-721 Token on-Chain"]
        B2["Settle Smart Contract Escrow Payouts"]
    end

    Finish(["End"])

    Start --> A1 --> S1 --> S2 --> A2 --> B1 --> S3
    S3 -->|"Instant Buy"| C1 --> C2 --> S5
    S3 -->|"Auction"| C1 --> C2 --> S4 --> S5
    S5 --> B2 --> C3 --> A3 --> Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Digital Artist | Uploads digital artwork files, configures EIP-2981 creator royalty percentages, signs minting vouchers, and collects secondary sales royalties. |
| 2 | System | Pins media and metadata to IPFS storage, runs copyright verification checks, manages auction vs fixed-price routes, locks escrow funds, and routes payments. |
| 3 | NFT Collector | Connects non-custodial Web3 crypto wallet, browses curated marketplace, places escrow bids or instant buys, and receives NFT tokens. |
| 4 | Blockchain Network | Executes on-chain ERC-721/1155 token minting contracts, enforces EIP-2981 royalty splits, and settles atomic token swaps. |
