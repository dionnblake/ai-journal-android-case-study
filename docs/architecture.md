# Architecture Notes

This document describes the private Android app at a system-design level without exposing source code.

## System overview

The app is a local-first Android journaling system with AI-assisted reflection. It combines a Compose UI, a ViewModel-centered state layer, Room persistence, DataStore preferences, background workers, export utilities, media utilities, and LLM API clients.

```text
User
  ↓
Jetpack Compose UI
  ↓
Navigation + screen state
  ↓
Journal ViewModel
  ↓                         ↓
Repository / Room / DAO     AI + media + export utilities
  ↓                         ↓
Local database + prefs      LLM APIs / Android services
```

## UI layer

Major screens:

- Journal home / calendar / entries
- Create and edit entry
- Entry detail
- Insights
- Ask AI
- Stats
- Settings and API settings
- Trash / recovery flow

The main app shell uses a tabbed navigation model for top-level areas, with detail routes outside the main pager for create/edit, entry detail, API settings, and trash.

## State and business logic

The ViewModel coordinates:

- entry creation and updates
- search, filter, and date selection state
- stats calculation paths
- AI request orchestration
- voice note handling
- export actions
- backup and restore flows
- UI state transitions

This keeps UI screens mostly declarative while centralizing app behavior.

## Persistence

The private app uses:

- Room database for journal entries and structured local records
- DAO queries for entry retrieval, filtering, updates, deletion, and cleanup
- Repository layer between ViewModel and database
- DataStore for settings, preferences, lock configuration, and API key state

## AI integration

The private implementation supports LLM-backed features such as Ask AI, summaries, and transcription-related workflows. Public docs intentionally avoid exposing prompt templates, orchestration logic, model-routing strategy, or proprietary product behavior.

At a safe level, the architecture includes:

- user-managed API key settings
- network clients for AI providers
- ViewModel-level orchestration
- UI flows for requesting and displaying AI output

## Background jobs

WorkManager supports durable Android background tasks, including reminders and cleanup flows. This is more reliable than manual timers because Android can manage scheduling across app restarts and device state changes.

## Security and privacy model

- Journal entries are local-first.
- API keys are not committed to source control.
- User can configure keys inside app settings.
- Biometric/app-lock flow protects local access.
- Public case study excludes source code, private prompts, and real journal data.

## Recruiter-relevant tradeoffs

- Public code would make the project easier to inspect but easier to copy.
- Private code plus strong case study protects the product while still showing skill.
- Screen-share code walkthrough is safer than temporary GitHub collaborator access.
- A separate sanitized sample repo can prove code style without exposing proprietary logic.
