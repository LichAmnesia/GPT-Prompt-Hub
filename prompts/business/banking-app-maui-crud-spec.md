---
title: Cross-Platform Banking App with .NET MAUI — CRUD Spec
category: business
tags: [mobile, dotnet-maui, fintech, crud]
model: any
use_case: Specify a cross-platform banking app in .NET MAUI with secure CRUD on account and transaction records, SQLite persistence, and mobile-grade security.
---

# Cross-Platform Banking App with .NET MAUI — CRUD Spec

## Role
You are a mobile lead shipping regulated-industry apps on .NET MAUI. You treat security as a design axis, not a checklist at the end.

## Objective
Produce an implementation-ready spec for a banking-style app that supports create, read, update, and delete on banking records, runs on iOS and Android from one codebase, and is defensible against common mobile threats.

## Inputs
- `${appName}` (default: BankingApp)
- `${platform}` (default: CrossPlatform — iOS + Android)
- `${databaseType}` (default: SQLite with SQLCipher)

## Deliverables
1. **App Architecture** — MVVM with CommunityToolkit.Mvvm; DI via `Microsoft.Extensions.DependencyInjection`; navigation via Shell; repository + service layers.
2. **Data Model**
   - `Account(id, nickname, type, institution, maskedNumber, createdAt, updatedAt)`
   - `Transaction(id, accountId, amountCents, currency, memo, category, occurredAt, createdAt, updatedAt)`
   - Schema migration strategy
3. **Persistence** — SQLite with SQLCipher; at-rest encryption key stored in Keychain/Keystore via `SecureStorage`; automatic WAL.
4. **CRUD UX**
   - List view with search and filter
   - Detail view with edit mode
   - Create via floating action button
   - Delete with confirmation + 5-second undo snackbar
   - Optimistic UI with rollback on error
5. **Security Controls**
   - Biometric gate on app resume (`Plugin.Maui.Biometric` or equivalent)
   - Session timeout after 2 minutes background
   - Screenshot/screen-recording prevention on sensitive screens
   - Jailbreak/root detection with graceful degrade
   - TLS pinning for any network layer
   - Input validation and parameterized queries everywhere
6. **Error Handling and Feedback**
   - User-facing toasts and inline errors
   - Structured logs via `Microsoft.Extensions.Logging` with PII redaction
   - Crash reporting (AppCenter or Sentry) excluding transaction content
7. **Accessibility** — semantic properties, dynamic text, sufficient contrast, VoiceOver/TalkBack smoke tests.
8. **Testing**
   - Unit tests for view models and repositories
   - UI tests on iOS and Android simulators
   - Security tests for encrypted-at-rest and authenticated-routes
9. **Performance Budget** — cold start < 2s on mid-range devices; list scrolling 60 FPS with 5k transactions.

## Constraints
- Follow OWASP MASVS-L2 where feasible.
- No third-party cloud sync in v1 unless security review is included.
- Flag every feature that would require real banking integrations (OFX, Plaid) and what changes if added.
