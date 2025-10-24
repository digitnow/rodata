┌─────────────────────────────────────────────────────────────────┐
│                         Client Layer                             │
│                    (Web, Mobile, API Clients)                    │
└────────────────────────────┬────────────────────────────────────┘
                             │ HTTPS
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│                    Nginx Reverse Proxy                           │
│              (SSL Termination, Load Balancing)                   │
└────────────────────────────┬────────────────────────────────────┘
                             │
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│                   Gunicorn Process Manager                       │
│                  (Multiple Uvicorn Workers)                      │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐       │
│  │ Uvicorn  │  │ Uvicorn  │  │ Uvicorn  │  │ Uvicorn  │       │
│  │ Worker 1 │  │ Worker 2 │  │ Worker 3 │  │ Worker N │       │
│  └────┬─────┘  └────┬─────┘  └────┬─────┘  └────┬─────┘       │
└───────┼─────────────┼─────────────┼─────────────┼──────────────┘
        │             │             │             │
        └─────────────┴─────────────┴─────────────┘
                             │
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│                     FastAPI Application                          │
│  ┌────────────────────────────────────────────────────────┐    │
│  │  API Endpoints (GET/POST)                               │    │
│  │  - Authentication endpoints (/login, /register)         │    │
│  │  - User management (/users/*)                           │    │
│  │  - Calculation submission (/calculate)                  │    │
│  │  - Results retrieval (/results/*)                       │    │
│  └────────────────────────────────────────────────────────┘    │
│  ┌────────────────────────────────────────────────────────┐    │
│  │  Business Logic Layer                                   │    │
│  │  - Request validation (Pydantic models)                 │    │
│  │  - Authentication/Authorization (JWT, OAuth2)           │    │
│  │  - Task orchestration (Celery task dispatch)            │    │
│  └────────────────────────────────────────────────────────┘    │
└────────────┬───────────────────┬───────────────────┬───────────┘
             │                   │                   │
             ▼                   ▼                   ▼
┌──────────────────┐  ┌──────────────────┐  ┌─────────────────┐
│   PostgreSQL     │  │     MongoDB      │  │      Redis      │
│  (Relational)    │  │     (NoSQL)      │  │    (Cache)      │
│                  │  │                  │  │                 │
│ - User accounts  │  │ - Unstructured   │  │ - Session data  │
│ - Calculations   │  │   data           │  │ - API cache     │
│ - Transactions   │  │ - Logs           │  │ - Rate limiting │
│ - Relationships  │  │ - Documents      │  │                 │
└──────────────────┘  └──────────────────┘  └────────┬────────┘
                                                      │
                                                      │ (Broker)
                                                      ▼
┌─────────────────────────────────────────────────────────────────┐
│                    Celery Task Queue                             │
│  ┌────────────────────────────────────────────────────────┐    │
│  │  Celery Beat (Scheduler)                                │    │
│  │  - Periodic tasks                                       │    │
│  │  - Scheduled calculations                               │    │
│  └────────────────────────────────────────────────────────┘    │
│  ┌────────────────────────────────────────────────────────┐    │
│  │  Celery Workers (Multiple Processes)                    │    │
│  │  ┌──────────┐  ┌──────────┐  ┌──────────┐             │    │
│  │  │ Worker 1 │  │ Worker 2 │  │ Worker N │             │    │
│  │  │          │  │          │  │          │             │    │
│  │  │ Intensive│  │ Intensive│  │ Intensive│             │    │
│  │  │ Calc     │  │ Calc     │  │ Calc     │             │    │
│  │  └──────────┘  └──────────┘  └──────────┘             │    │
│  └────────────────────────────────────────────────────────┘    │
└─────────────────────────────────────────────────────────────────┘
                             │
                             │ (Results)
                             ▼
                    ┌─────────────────┐
                    │   PostgreSQL    │
                    │   or MongoDB    │
                    │ (Store Results) │
                    └─────────────────┘
