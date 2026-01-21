# OOP-Team-B_Youtube-lite
A lightweight YouTube-style application built as an OOP team project.

## System Architecture
```mermaid
flowchart TB

  subgraph C[Clients]
    V[Viewer Browser]
    CR[Creator Browser]
    A[Admin Browser]
  end

  subgraph W[Web Layer]
    R[Web Router and Reverse Proxy]
    UI[Web User Interface]
  end

  subgraph B[Backend Application]
    AUTH[Authentication and RBAC]
    VIDEO[Video Management]
    SOCIAL[Social Features]
    ADMIN[Admin Moderation]
    SEARCH[Search Service]
    SVC[Service Layer]
    DAO[Data Access Layer]
  end

  subgraph D[Data Layer]
    DB[(Relational Database)]
    FS[(Video File Storage)]
    TH[(Thumbnail Storage)]
  end

  subgraph O[Operations]
    LOG[Application Logs]
    MET[System Metrics]
  end

  V --> R
  CR --> R
  A --> R

  R --> UI
  R --> B

  UI --> B

  B --> AUTH
  B --> VIDEO
  B --> SOCIAL
  B --> ADMIN
  B --> SEARCH

  AUTH --> SVC
  VIDEO --> SVC
  SOCIAL --> SVC
  ADMIN --> SVC
  SEARCH --> SVC

  SVC --> DAO
  DAO --> DB

  VIDEO --> FS
  VIDEO --> TH

  B --> LOG
  R --> LOG
  LOG --> MET
```
## Recomended File Structure
```text
youtube-lite/
├── README.md              # Project overview and setup instructions
├── .gitignore             # Git ignored files
├── .env                   # Environment variable template
├── requirements.txt       # Python dependencies
│
├── src/
│   └── app/
│       ├── __init__.py    # Application factory
│       ├── config.py      # Application configuration
│       ├── extensions.py  # Flask extensions (DB, auth, etc.)
│       │
│       ├── models/        # Database entities
│       │   └── __init__.py
│       │
│       ├── services/      # Business logic layer
│       │   └── __init__.py
│       │
│       ├── routes/        # Controllers / web endpoints
│       │   └── __init__.py
│       │
│       ├── templates/     # HTML templates
│       │   └── base.html
│       │
│       ├── static/        # CSS, JavaScript, images
│       │   └── style.css
│       │
│       └── utils/         # Helper utilities (RBAC, decorators)
│           └── __init__.py
│
├── tests/
│   └── test_smoke.py      # Basic application startup test
│
└── run.py                 # Application entry point
```
