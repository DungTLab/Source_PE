# Conceptual ERD — Metaverse Real Estate Management System

## Mermaid Code

```mermaid
erDiagram
    METAVERSE_WORLD {
        int world_id PK
        string world_name
        string blockchain_network
        string native_token_symbol
        int total_land_parcels
    }

    PARCEL_OWNER {
        int owner_id PK
        string owner_name
        string primary_wallet_address
        string email
        datetime registered_at
    }

    WALLET_KEY {
        int wallet_id PK
        int owner_id FK
        string wallet_address
        string wallet_type
        boolean is_primary
    }

    LAND_PARCEL_NFT {
        int parcel_id PK
        int world_id FK
        int owner_id FK
        string token_id
        string smart_contract_address
        int grid_coord_x
        int grid_coord_y
        string district_name
        string status
    }

    VIRTUAL_TENANT {
        int tenant_id PK
        string tenant_name
        string tenant_wallet_address
        string business_category
        string email
    }

    LEASE_SMART_CONTRACT {
        int lease_id PK
        int parcel_id FK
        int tenant_id FK
        string contract_address
        decimal monthly_rent_crypto
        string crypto_currency
        datetime lease_start
        datetime lease_end
        string lease_status
    }

    STRUCTURE_ASSET_3D {
        int structure_id PK
        int parcel_id FK
        string structure_name
        string ipfs_content_uri
        int polygon_count
        decimal file_size_mb
        datetime deployed_at
    }

    RENTAL_TRANSACTION {
        int transaction_id PK
        int lease_id FK
        string tx_hash
        decimal amount_crypto
        decimal amount_usd_equivalent
        datetime payment_date
    }

    EVENT_BOOKING {
        int event_id PK
        int parcel_id FK
        int tenant_id FK
        string event_name
        datetime start_time
        datetime end_time
        int peak_avatar_count
    }

    PARCEL_VALUATION {
        int valuation_id PK
        int parcel_id FK
        decimal estimated_value_eth
        decimal estimated_value_usd
        int traffic_rank_score
        datetime valuation_date
    }

    BROKER_LISTING {
        int listing_id PK
        int parcel_id FK
        string listing_type
        decimal asking_price_crypto
        decimal commission_rate
        datetime listed_at
    }

    METAVERSE_WORLD ||--o{ LAND_PARCEL_NFT : "contains"
    PARCEL_OWNER ||--o{ WALLET_KEY : "owns"
    PARCEL_OWNER ||--o{ LAND_PARCEL_NFT : "holds_deed"
    LAND_PARCEL_NFT ||--o{ LEASE_SMART_CONTRACT : "leased_in"
    VIRTUAL_TENANT ||--o{ LEASE_SMART_CONTRACT : "signs_lease"
    LAND_PARCEL_NFT ||--o{ STRUCTURE_ASSET_3D : "renders"
    LEASE_SMART_CONTRACT ||--o{ RENTAL_TRANSACTION : "generates"
    LAND_PARCEL_NFT ||--o{ EVENT_BOOKING : "hosts"
    VIRTUAL_TENANT ||--o{ EVENT_BOOKING : "organizes"
    LAND_PARCEL_NFT ||--o{ PARCEL_VALUATION : "appraised_in"
    LAND_PARCEL_NFT ||--o{ BROKER_LISTING : "offered_in"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|-------------------|
| 1 | METAVERSE_WORLD | Thế giới Metaverse | Represents a 3D virtual world ecosystem (Decentraland, Sandbox, Somnium Space). | world_id (PK), world_name, blockchain_network, native_token_symbol | Contains Land Parcel NFTs |
| 2 | PARCEL_OWNER | Chủ sở hữu Bất động sản | Virtual land investor or Web3 fund holding land parcel NFT deeds. | owner_id (PK), owner_name, primary_wallet_address, email | Owns Wallet Keys, holds deed for Land Parcel NFTs |
| 3 | WALLET_KEY | Ví Crypto Web3 | Non-custodial Web3 crypto wallet address (0x...) associated with a parcel owner. | wallet_id (PK), owner_id (FK), wallet_address, wallet_type | Belongs to Parcel Owner |
| 4 | LAND_PARCEL_NFT | NFT Đất Virtual | Tokenized virtual land parcel NFT (ERC-721/1155) with spatial grid coordinates. | parcel_id (PK), world_id (FK), owner_id (FK), token_id, grid_coord_x, grid_coord_y, status | Belongs to World & Owner, leased in Smart Contracts, renders 3D Structures, appraised in Valuations |
| 5 | VIRTUAL_TENANT | Thẻ Người Thuê Virtual | Brand, creator, or company renting virtual land to host 3D venues or events. | tenant_id (PK), tenant_name, tenant_wallet_address, business_category | Signs Lease Contracts, organizes Event Bookings |
| 6 | LEASE_SMART_CONTRACT | Hợp đồng Thông minh Thuê | On-chain smart contract locking land NFT escrow and enforcing monthly crypto rent. | lease_id (PK), parcel_id (FK), tenant_id (FK), contract_address, monthly_rent_crypto, lease_status | Leases Land Parcel NFT, signed by Virtual Tenant, generates Rental Transactions |
| 7 | STRUCTURE_ASSET_3D | Công trình 3D Virtual | Deployed 3D architectural model file (.gltf) rendered on a virtual land parcel. | structure_id (PK), parcel_id (FK), structure_name, ipfs_content_uri, polygon_count | Renders on Land Parcel NFT |
| 8 | RENTAL_TRANSACTION | Giao dịch Tiền thuê Crypto | On-chain monthly rental payment execution, tracking transaction hash and crypto amount. | transaction_id (PK), lease_id (FK), tx_hash, amount_crypto, amount_usd_equivalent | Generated by Lease Smart Contract |
| 9 | EVENT_BOOKING | Sự kiện Virtual | Concert, exhibition, or brand product launch hosted on a virtual land parcel. | event_id (PK), parcel_id (FK), tenant_id (FK), event_name, start_time, peak_avatar_count | Hosted on Land Parcel NFT, organized by Virtual Tenant |
| 10 | PARCEL_VALUATION | Định giá Đất Virtual | Automated market valuation appraisal based on floor prices, location, and avatar traffic. | valuation_id (PK), parcel_id (FK), estimated_value_eth, estimated_value_usd, traffic_rank_score | Appraises Land Parcel NFT |
| 11 | BROKER_LISTING | Niêm yết Môi giới | Marketplace sales or lease listing managed by virtual real estate brokers. | listing_id (PK), parcel_id (FK), listing_type, asking_price_crypto, commission_rate | Offers Land Parcel NFT |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | METAVERSE_WORLD | one-to-many | LAND_PARCEL_NFT | contains | A Metaverse World contains multiple Land Parcel NFTs. |
| 2 | PARCEL_OWNER | one-to-many | WALLET_KEY | owns | A Parcel Owner owns one or multiple Web3 Wallet Keys. |
| 3 | PARCEL_OWNER | one-to-many | LAND_PARCEL_NFT | holds_deed | A Parcel Owner holds deeds for multiple Land Parcel NFTs. |
| 4 | LAND_PARCEL_NFT | one-to-many | LEASE_SMART_CONTRACT | leased_in | A Land Parcel NFT can be leased in multiple Lease Smart Contracts over time. |
| 5 | VIRTUAL_TENANT | one-to-many | LEASE_SMART_CONTRACT | signs_lease | A Virtual Tenant signs multiple Lease Smart Contracts. |
| 6 | LAND_PARCEL_NFT | one-to-many | STRUCTURE_ASSET_3D | renders | A Land Parcel NFT renders one active or historical 3D Structure Assets. |
| 7 | LEASE_SMART_CONTRACT | one-to-many | RENTAL_TRANSACTION | generates | A Lease Smart Contract generates monthly crypto Rental Transactions. |
| 8 | LAND_PARCEL_NFT | one-to-many | EVENT_BOOKING | hosts | A Land Parcel NFT hosts multiple Virtual Event Bookings over time. |
| 9 | VIRTUAL_TENANT | one-to-many | EVENT_BOOKING | organizes | A Virtual Tenant organizes multiple Event Bookings. |
| 10 | LAND_PARCEL_NFT | one-to-many | PARCEL_VALUATION | appraised_in | A Land Parcel NFT is appraised across multiple historical Parcel Valuations. |
| 11 | LAND_PARCEL_NFT | one-to-many | BROKER_LISTING | offered_in | A Land Parcel NFT is offered in multiple Broker Listings over time. |
