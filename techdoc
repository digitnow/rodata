# Utviklingsprosess
Må skaffe seg grunnleggende kunnskap om alle verktøyene.

Eksempel på en "flow"
```
┌──────────────────────────────────────────────────────────────┐
│                     DATA SOURCES                              │
│  regatta.roing.no  │  RegattaCentral  │  CrewTimer  │  Excel │
└────────────┬─────────────────┬──────────────┬────────────┬───┘
             │                 │              │            │
             ▼                 ▼              ▼            ▼
┌──────────────────────────────────────────────────────────────┐
│                      SCRAPERS / PARSERS                       │
│  (Collect and structure data - NO database access)            │
│                                                                │
│  norwegian_rowing_scraper.py                                  │
│  regattacentral_client.py                                     │
│  crewtimer_pdf_parser_v2.py                                   │
│  excel_importer_v2.py                                         │
└────────────┬─────────────────┬──────────────┬────────────────┘
             │                 │              │
             ▼                 ▼              ▼
┌──────────────────────────────────────────────────────────────┐
│              CELERY TASKS (Integration Layer)                 │
│  ⭐ THIS IS WHERE DATA GETS INSERTED INTO DATABASES ⭐       │
│                                                                │
│  ingestion_tasks.py:                                          │
│    Line 102: INSERT INTO regattas                             │
│    Line 121: INSERT INTO events                               │
│    Line 132: INSERT INTO races                                │
│    Line 145: INSERT INTO clubs                                │
│    Line 152: INSERT INTO crews                                │
│    Line 156: INSERT INTO persons                              │
│    Line 162: INSERT INTO crew_members                         │
│    Line 169: INSERT INTO race_entries                         │
│    Line 176: INSERT INTO results (MongoDB)                    │
│    Line 439: INSERT INTO test_results (MongoDB)               │
└────────────┬─────────────────┬──────────────────────────────┘
             │                 │
             ▼                 ▼
┌─────────────────────┐  ┌──────────────────────┐
│  DATABASE HANDLERS  │  │  DATABASE HANDLERS   │
│  postgres_handler.py│  │  mongodb_handler.py  │
│  (Execute SQL)      │  │  (Execute MongoDB)   │
└──────────┬──────────┘  └──────────┬───────────┘
           │                        │
           ▼                        ▼
┌─────────────────────┐  ┌──────────────────────┐
│    PostgreSQL       │  │      MongoDB         │
│  (9 tables)         │  │  (2 collections)     │
│  - regattas         │  │  - results           │
│  - events           │  │  - test_results      │
│  - races            │  │                      │
│  - clubs            │  │                      │
│  - persons          │  │                      │
│  - crews            │  │                      │
│  - crew_members     │  │                      │
│  - race_entries     │  │                      │
│  - coaches          │  │                      │
└─────────────────────┘  └──────────────────────┘
```

## Mongodb (using CLI)
**mongo** er byttet ut med **mongosh**

Ved å skrive mongosh får man en mongodb-shell. 

- <pre>use databasenavn</pre> fungerer men det ser ut at man kan bruke hva som helst som <pre>databasenavn</pre>, dvs. det trenger ikke å være en database med det navnet i DBHS.
- db.listCommands() returnerer en meget lang liste av alle tilgjengelige kommandoer i den kjørende MongoDB instansen
- show dbs viser alle definerte databaser
- med påfølgende bruk av use eneksisterendedatabase for man shell til den konkrete datbasen
- show collections da vil vise alle "dokumenter" (tabeller) i den valgte databasen
