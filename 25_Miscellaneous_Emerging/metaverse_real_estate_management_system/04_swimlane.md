# Swimlane Diagram — Metaverse Real Estate Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Virtual Land Investor"]
        O1["Connect Web3 Wallet & Verify NFT"]
        O2["List Land Parcel NFT & Set Rent Terms"]
        O3["Approve NFT Operator Escrow Access"]
        O4["Collect Monthly Crypto Rent Yield"]
    end

    subgraph Lane2["System"]
        S1["Verify On-Chain NFT Ownership"]
        S2["Deploy Lease Escrow Smart Contract"]
        S3{"Tenant Wallet Balance Sufficient?"}
        S4["Grant 3D Build Rights to Tenant"]
        S5["Dispatch Automated Yield to Owner Wallet"]
    end

    subgraph Lane3["Virtual Tenant"]
        T1["Search Available Virtual Land Parcels"]
        T2["Sign Smart Contract & Deposit Rent"]
        T3["Deploy 3D Virtual Structure Asset"]
    end

    subgraph Lane4["Blockchain Network"]
        B1["Execute On-Chain Ownership Query"]
        B2["Lock NFT Escrow & Confirm Transaction"]
        B3["Distribute Crypto Tokens On-Chain"]
    end

    Finish(["End"])

    Start --> O1 --> S1 --> B1 --> O2 --> S2 --> T1 --> T2 --> S3
    S3 -->|"Yes"| O3 --> B2 --> S4 --> T3 --> S5 --> B3 --> O4 --> Finish
    S3 -->|"No"| T2
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Virtual Land Investor | Connects Web3 crypto wallet, verifies land NFT deeds, configures lease pricing terms, approves escrow permissions, and collects rental yield. |
| 2 | System | Automates on-chain NFT ownership checks, deploys escrow smart contracts, checks tenant crypto balances, grants 3D build permissions, and triggers yield payouts. |
| 3 | Virtual Tenant | Searches virtual land listings, signs smart contract lease agreements, funds crypto deposits, and deploys 3D architectural building models. |
| 4 | Blockchain Network | Verifies ERC-721/1155 NFT deeds, locks smart contract escrows on-chain, and executes immutable token transfers (ETH/USDC). |
