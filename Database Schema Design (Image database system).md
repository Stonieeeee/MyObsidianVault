
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
        int process_id PK
        string process_name
        string process_type
        string description
        datetime created_at
    }

    SOURCE_LOCATION {
        int source_id PK
        string source_name
        string source_type
        string source_path
        string machine_name
        boolean enabled
        datetime created_at
    }

    IMAGE_FILE {
        int image_id PK
        int process_id FK
        int source_id FK
        string file_name
        string original_name
        string file_extension
        bigint file_size
        string file_hash
        datetime generated_at
        datetime collected_at
        string status
    }

    STORAGE_LOCATION {
        int storage_id PK
        string storage_name
        string storage_type
        string storage_path
        boolean enabled
        datetime created_at
    }

    TRANSFER_HISTORY {
        int transfer_id PK
        int image_id FK
        int storage_id FK
        datetime started_at
        datetime completed_at
        string status
        string error_message
        int retry_count
    }

    APPLICATION_LOG {
        int log_id PK
        int image_id FK
        string log_level
        string event_type
        string message
        string machine_name
        datetime created_at
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