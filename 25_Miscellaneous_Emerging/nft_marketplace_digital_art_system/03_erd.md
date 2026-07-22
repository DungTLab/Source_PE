# Conceptual ERD — NFT Marketplace & Digital Art System

## Mermaid Code

```mermaid
erDiagram
    DIGITAL_ARTIST {
        int artist_id PK
        string artist_name
        string handle
        string bio_summary
        string primary_wallet_address
        string verification_status
    }

    WALLET_ACCOUNT {
        int wallet_id PK
        int artist_id FK
        string wallet_address
        string blockchain_network
        boolean is_primary
    }

    ART_COLLECTION {
        int collection_id PK
        int artist_id FK
        string collection_name
        string contract_address
        string token_standard
        int total_supply
    }

    NFT_ARTWORK {
        int artwork_id PK
        int collection_id FK
        int artist_id FK
        string token_id
        string title
        string media_type
        string current_owner_wallet
        string status
    }

    IPFS_METADATA {
        int metadata_id PK
        int artwork_id FK
        string ipfs_media_uri
        string ipfs_json_uri
        string content_hash
        decimal file_size_mb
    }

    COLLECTOR_PROFILE {
        int collector_id PK
        string wallet_address
        string username
        string email
        datetime joined_date
    }

    AUCTION_LISTING {
        int auction_id PK
        int artwork_id FK
        string auction_type
        decimal reserve_price_crypto
        datetime start_time
        datetime end_time
        string status
    }

    BID_OFFER {
        int bid_id PK
        int auction_id FK
        int bidder_collector_id FK
        decimal bid_amount_crypto
        string tx_hash
        datetime bid_time
    }

    NFT_TRANSACTION {
        int transaction_id PK
        int artwork_id FK
        int seller_collector_id FK
        int buyer_collector_id FK
        decimal sale_price_crypto
        decimal usd_equivalent
        string transaction_hash
        datetime transaction_date
    }

    ROYALTY_RULE {
        int royalty_id PK
        int artwork_id FK
        int artist_id FK
        decimal royalty_percentage
        string payout_wallet_address
        decimal cumulative_royalties_earned
    }

    CURATED_EXHIBITION {
        int exhibition_id PK
        string exhibition_title
        string curator_name
        datetime start_date
        datetime end_date
        string status
    }

    EXHIBITION_ARTWORK {
        int exhibition_id PK, FK
        int artwork_id PK, FK
        int display_order
    }

    DIGITAL_ARTIST ||--o{ WALLET_ACCOUNT : "owns"
    DIGITAL_ARTIST ||--o{ ART_COLLECTION : "creates"
    DIGITAL_ARTIST ||--o{ NFT_ARTWORK : "mints"
    ART_COLLECTION ||--o{ NFT_ARTWORK : "contains"
    NFT_ARTWORK ||--|| IPFS_METADATA : "linked_to"
    NFT_ARTWORK ||--o{ AUCTION_LISTING : "offered_in"
    AUCTION_LISTING ||--o{ BID_OFFER : "receives"
    COLLECTOR_PROFILE ||--o{ BID_OFFER : "places"
    NFT_ARTWORK ||--o{ NFT_TRANSACTION : "sold_in"
    COLLECTOR_PROFILE ||--o{ NFT_TRANSACTION : "buys_or_sells"
    NFT_ARTWORK ||--|| ROYALTY_RULE : "enforces"
    DIGITAL_ARTIST ||--o{ ROYALTY_RULE : "receives_yield"
    CURATED_EXHIBITION ||--o{ EXHIBITION_ARTWORK : "features"
    NFT_ARTWORK ||--o{ EXHIBITION_ARTWORK : "displayed_in"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|-------------------|
| 1 | DIGITAL_ARTIST | Tác giả Nghệ thuật Số | Digital artist, animator, or 3D creator minting and selling NFT artworks. | artist_id (PK), artist_name, handle, primary_wallet_address, verification_status | Owns Wallet Accounts, creates Collections, mints Artworks, receives Royalties |
| 2 | WALLET_ACCOUNT | Tài khoản Ví Web3 | Non-custodial Web3 crypto wallet address (0x...) linked to an artist or collector profile. | wallet_id (PK), artist_id (FK), wallet_address, blockchain_network | Belongs to Digital Artist |
| 3 | ART_COLLECTION | Bộ sưu tập NFT | Smart contract collection grouping individual NFT artworks under a common contract address. | collection_id (PK), artist_id (FK), collection_name, contract_address, token_standard | Created by Digital Artist, contains NFT Artworks |
| 4 | NFT_ARTWORK | Tác phẩm Nghệ thuật NFT | Individual digital artwork tokenized as an ERC-721/1155 NFT on the blockchain. | artwork_id (PK), collection_id (FK), artist_id (FK), token_id, title, current_owner_wallet | Belongs to Collection & Artist, linked to IPFS Metadata, offered in Auctions, sold in Transactions |
| 5 | IPFS_METADATA | Metadata Đã Pin IPFS | Decentralized IPFS storage hashes hosting original high-res media files and JSON metadata URIs. | metadata_id (PK), artwork_id (FK), ipfs_media_uri, ipfs_json_uri, content_hash | Linked to NFT Artwork |
| 6 | COLLECTOR_PROFILE | Hồ sơ Nhà Sưu tập | Profile of an NFT buyer or secondary trader holding crypto assets and managing collections. | collector_id (PK), wallet_address, username, email | Places Bid Offers, buys/sells in NFT Transactions |
| 7 | AUCTION_LISTING | Niêm yết Đấu giá | Timed English or Dutch auction listing specifying reserve price, duration, and bidding status. | auction_id (PK), artwork_id (FK), auction_type, reserve_price_crypto, start_time, status | Offers NFT Artwork, receives Bid Offers |
| 8 | BID_OFFER | Lượt Đặt giá Bid | Competitive crypto bid placed by a collector on an active auction listing. | bid_id (PK), auction_id (FK), bidder_collector_id (FK), bid_amount_crypto, tx_hash | Placed by Collector Profile, placed on Auction Listing |
| 9 | NFT_TRANSACTION | Giao dịch Mua bán NFT | On-chain settlement transaction recording primary sale or secondary resale of an NFT. | transaction_id (PK), artwork_id (FK), seller_collector_id (FK), buyer_collector_id (FK), sale_price_crypto, transaction_hash | Records sale of NFT Artwork, involves Collector Profiles |
| 10 | ROYALTY_RULE | Quy tắc Nhuận bút (EIP-2981) | Creator royalty configuration percentage and payout wallet address enforced on secondary sales. | royalty_id (PK), artwork_id (FK), artist_id (FK), royalty_percentage, payout_wallet_address | Enforced on NFT Artwork, pays Digital Artist |
| 11 | CURATED_EXHIBITION | Triển lãm Nghệ thuật Số | Curated virtual gallery exhibition highlighting selected thematic NFT artworks and artist drops. | exhibition_id (PK), exhibition_title, curator_name, start_date, end_date | Features NFT Artworks (via EXHIBITION_ARTWORK) |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | DIGITAL_ARTIST | one-to-many | WALLET_ACCOUNT | owns | A Digital Artist owns one or more Web3 Wallet Accounts. |
| 2 | DIGITAL_ARTIST | one-to-many | ART_COLLECTION | creates | A Digital Artist creates multiple Art Collections. |
| 3 | DIGITAL_ARTIST | one-to-many | NFT_ARTWORK | mints | A Digital Artist mints multiple NFT Artworks. |
| 4 | ART_COLLECTION | one-to-many | NFT_ARTWORK | contains | An Art Collection contains multiple individual NFT Artworks. |
| 5 | NFT_ARTWORK | one-to-one | IPFS_METADATA | linked_to | An NFT Artwork is linked to a unique IPFS Metadata URI. |
| 6 | NFT_ARTWORK | one-to-many | AUCTION_LISTING | offered_in | An NFT Artwork can be offered in multiple timed Auction Listings over time. |
| 7 | AUCTION_LISTING | one-to-many | BID_OFFER | receives | An Auction Listing receives multiple competitive Bid Offers. |
| 8 | COLLECTOR_PROFILE | one-to-many | BID_OFFER | places | A Collector Profile places multiple Bid Offers. |
| 9 | NFT_ARTWORK | one-to-many | NFT_TRANSACTION | sold_in | An NFT Artwork is sold across multiple primary/secondary NFT Transactions. |
| 10 | COLLECTOR_PROFILE | one-to-many | NFT_TRANSACTION | buys_or_sells | A Collector Profile buys or sells in multiple NFT Transactions. |
| 11 | NFT_ARTWORK | one-to-one | ROYALTY_RULE | enforces | An NFT Artwork enforces an EIP-2981 Royalty Rule. |
| 12 | DIGITAL_ARTIST | one-to-many | ROYALTY_RULE | receives_yield | A Digital Artist receives secondary royalty yield from Royalty Rules. |
| 13 | CURATED_EXHIBITION | many-to-many | NFT_ARTWORK | features | Curated Exhibitions feature multiple NFT Artworks (via EXHIBITION_ARTWORK). |
