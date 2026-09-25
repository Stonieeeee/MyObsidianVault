
# TABLE STRUCTURE

**PPCS_IMG_INFO**



**PQC1_IMG_INFO**

| COLUMN      | DATA TYPE      |
| ----------- | -------------- |
| IMG_ID      | INT            |
| IMG_LABEL   | VARCHAR2(50)   |
| IMG_PATH    | VARCHAR2(150)  |
| IMG_SIZE    | DECIMAL(10, 2) |
| IMG_UP_TIME | DATE           |
| IMG_DL_TIME | DATE           |
| USER_ID     | VARCHAR2(15)   |


**PQC2_IMG_INFO**

| COLUMN      | DATA TYPE      |
| ----------- | -------------- |
| IMG_ID      | INT            |
| IMG_LABEL   | VARCHAR2(50)   |
| IMG_PATH    | VARCHAR2(150)  |
| IMG_SIZE    | DECIMAL(10, 2) |
| IMG_UP_TIME | DATE           |
| IMG_DL_TIME | DATE           |
| USER_ID     | VARCHAR2(15)   |
| Area        | VARCHAR2(7)    |

**Entity-Relation Diagram for the SP Image File Collector/Uploader**
```mermaid
erDiagram

    PROCESS ||--o{ IMAGE_FILE : generates
    SOURCE_LOCATION ||--o{ IMAGE_FILE : provides
    IMAGE_FILE ||--o{ TRANSFER_HISTORY : has
    STORAGE_LOCATION ||--o{ TRANSFER_HISTORY : receives
    IMAGE_FILE ||--o{ APPLICATION_LOG : generates

    PROCESS {
        NUMBER process_id PK
        STRING process_name
        STRING process_type
        STRING description
        DATE created_at
    }

    SOURCE_LOCATION {
        NUMBER source_id PK
        STRING source_name
        STRING source_type
        STRING source_path
        STRING machine_name
        BOOLEAN enabled
        DATE created_at
    }

    IMAGE_FILE {
        NUMBER image_id PK
        NUMBER process_id FK
        NUMBER source_id FK
        STRING file_name
        STRING original_name
        STRING file_extension
        bigNUMBER file_size
        STRING file_hash
        DATE generated_at
        DATE collected_at
        STRING status
    }

    STORAGE_LOCATION {
        NUMBER storage_id PK
        STRING storage_name
        STRING storage_type
        STRING storage_path
        BOOLEAN enabled
        DATE created_at
    }

    TRANSFER_HISTORY {
        NUMBER transfer_id PK
        NUMBER image_id FK
        NUMBER storage_id FK
        DATE started_at
        DATE completed_at
        STRING status
        STRING error_message
        NUMBER retry_count
    }

    APPLICATION_LOG {
        NUMBER log_id PK
        NUMBER image_id FK
        STRING log_level
        STRING event_type
        STRING message
        STRING machine_name
        DATE created_at
    }


    %% =========================
    %% CUSTOM ENTITY COLORS
    %% =========================

    classDef process fill:#D1FAE5,stroke:#16A34A,color:#14532D,stroke-width:2px
    classDef image fill:#DBEAFE,stroke:#2563EB,color:#1E3A8A,stroke-width:3px
    classDef source fill:#EDE9FE,stroke:#7C3AED,color:#4C1D95,stroke-width:2px
    classDef storage fill:#CCFBF1,stroke:#0D9488,color:#134E4A,stroke-width:2px
    classDef transfer fill:#FFEDD5,stroke:#EA580C,color:#7C2D12,stroke-width:2px
    classDef log fill:#FCE7F3,stroke:#DB2777,color:#831843,stroke-width:2px

    class PROCESS process
    class IMAGE_FILE image
    class SOURCE_LOCATION source
    class STORAGE_LOCATION storage
    class TRANSFER_HISTORY transfer
    class APPLICATION_LOG log
```