# Speek — Personal Audiobook & Reader PWA
### Technical Brief · Christian Egwuogu · August 2026

Most reading apps treat the library and the player as separate problems. Speek is one application that manages a personal document library and reads it aloud with synchronized text — built from concept to daily-use product.

## Architecture

- **Next.js (TypeScript) PWA** — app-router application with a full REST API surface: document ingestion, chapter splitting, per-chapter audio generation, bookmarks, continue-listening, cover extraction, offline packaging. Every API route ships with its own route tests.
- **Self-hosted TTS engine** — a Python FastAPI service wrapping the Kokoro-82M ONNX speech model, running locally. No cloud TTS dependency: voice synthesis is an owned local service, with a curated 8-voice catalog and health/voice endpoints. The interface reserves word-level timestamp fields for a future forced-alignment upgrade — designed for read-along highlighting, not just playback.
- **Offline-first** — per-document offline packaging endpoints; service-worker caching makes the app installable and usable without a network.
- **Monorepo tooling** — pnpm workspace, Vitest test runner with setup harness, scripted ops.

## Engineering signals

- **436 automated tests** across API routes, handlers, and the TTS service
- TypeScript throughout the app; Python service tested separately, with its own test suite
- ~670K lines of TypeScript in the application — a full product, not a weekend demo

## Position

A daily-use personal product built with production discipline: local-first infrastructure, tested API surface, and a self-hosted ML model instead of a third-party API key. Same engineering standards as the security and pipeline systems, applied to consumer software.

Source is private. Full technical walkthrough available on request.

---
*Christian Egwuogu — Founder, DeployLabs.*
