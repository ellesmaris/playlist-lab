# Playlist Lab

A music playlist analysis and generation platform for exploring listening patterns, discovering tracks, and creating playlists from configurable criteria.

## Overview

Playlist Lab focuses on the data and logic behind music discovery rather than simply storing music.

Users will be able to import or maintain a music collection, analyze its characteristics, define playlist criteria, generate playlists, and explore statistics about their music.

The project is designed to progressively introduce data processing, background jobs, filtering, aggregation, and scalable application architecture.

## Core Capabilities

* Music and playlist collection management
* Playlist import and export
* Artist, album, genre, and release-year analysis
* Track filtering and search
* Configurable playlist generation
* Playlist statistics
* Listening-pattern analysis
* Background processing for larger operations
* Caching for frequently requested data
* API documentation
* Automated testing
* Containerized development

## Architecture

Playlist Lab will follow a layered architecture:

```text
                    ┌──────────────────────┐
                    │      API Layer       │
                    │   FastAPI / REST     │
                    └──────────┬───────────┘
                               │
                    ┌──────────▼───────────┐
                    │   Service Layer      │
                    │ Business Logic       │
                    └──────────┬───────────┘
                               │
              ┌────────────────┼────────────────┐
              │                │                │
      ┌───────▼───────┐ ┌──────▼──────┐ ┌──────▼──────┐
      │  Data Layer   │ │   Cache     │ │ Background  │
      │ SQLAlchemy    │ │   Redis     │ │    Jobs     │
      └───────┬───────┘ └─────────────┘ └──────┬──────┘
              │                                │
      ┌───────▼───────┐                ┌───────▼───────┐
      │  PostgreSQL   │                │     Worker     │
      └───────────────┘                └────────────────┘
```

The API layer handles HTTP requests, the service layer contains application logic, the data layer manages persistence, Redis provides caching and job support, and background workers handle operations that do not need to block API requests.

## Project Structure

```text
playlist-lab/
├── app/
│   ├── api/
│   │   ├── routes/
│   │   │   ├── tracks.py
│   │   │   ├── playlists.py
│   │   │   ├── analysis.py
│   │   │   └── generation.py
│   │   └── dependencies.py
│   │
│   ├── core/
│   │   ├── config.py
│   │   ├── database.py
│   │   ├── logging.py
│   │   └── security.py
│   │
│   ├── models/
│   │   ├── track.py
│   │   ├── artist.py
│   │   ├── album.py
│   │   ├── genre.py
│   │   ├── playlist.py
│   │   └── listening_event.py
│   │
│   ├── schemas/
│   │   ├── track.py
│   │   ├── playlist.py
│   │   ├── analysis.py
│   │   └── generation.py
│   │
│   ├── services/
│   │   ├── playlist_service.py
│   │   ├── analysis_service.py
│   │   ├── generation_service.py
│   │   └── import_service.py
│   │
│   ├── repositories/
│   │   ├── track_repository.py
│   │   ├── playlist_repository.py
│   │   └── listening_repository.py
│   │
│   ├── workers/
│   │   ├── tasks.py
│   │   └── worker.py
│   │
│   └── main.py
│
├── tests/
│   ├── unit/
│   ├── integration/
│   └── api/
│
├── migrations/
│
├── scripts/
│
├── docs/
│   ├── architecture.md
│   └── api.md
│
├── .env.example
├── .gitignore
├── Dockerfile
├── docker-compose.yml
├── pyproject.toml
├── README.md
└── LICENSE
```

## Technology Direction

The initial implementation is expected to use:

* Python
* FastAPI
* PostgreSQL
* SQLAlchemy
* Redis
* Background worker system
* Pytest
* Docker

The technology stack may evolve as the architecture develops.

## Development Roadmap

### Stage 1 — Foundation

Application structure, configuration, database connection, Docker environment, health endpoint, and initial tests.

### Stage 2 — Music Data

Tracks, artists, albums, genres, and database relationships.

### Stage 3 — Playlist Management

Playlist creation, modification, track ordering, and playlist retrieval.

### Stage 4 — Analysis

Library statistics, genre distribution, artist statistics, release-year analysis, and listening patterns.

### Stage 5 — Playlist Generation

Rule-based playlist generation using configurable criteria.

### Stage 6 — Import & Export

Import music collections and playlists and provide structured export functionality.

### Stage 7 — Background Processing

Move expensive analysis and generation operations into background jobs.

### Stage 8 — Caching

Introduce Redis caching for frequently requested analysis and playlist data.

### Stage 9 — Testing & Production Readiness

Expand test coverage, improve error handling, documentation, security, observability, and deployment preparation.

## Project Status

**Planning**

The repository currently contains the project definition and architectural direction. Implementation will begin with Stage 1.

## Engineering Goals

Playlist Lab is intended to demonstrate practical software engineering through a music-focused project.

The emphasis is on clear architecture, maintainable code, testing, data processing, and incremental development rather than building every possible music feature at once.

## License

MIT
